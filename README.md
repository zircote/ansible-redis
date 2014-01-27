# Ansible Roles for redis

Provides roles supporting:
 - redis
 - redis-server
 - redis-sentinel

An example of a master
```yaml
---
- hosts: redis
  roles:
   - { role: redis-server,
       redis_port: 6380,
       redis_requirepass: "fushyou",
       redis_save: none,
       redis_maxmemory_policy: volatile-ttl,
       redis_hz: 100,
       redis_appendfsync: "no",
       redis_rename_command:
         - FLUSH ""
         - FLUSHALL ""
       }

```

An example of a slave
```yaml
---
- hosts: redis
  roles:
   - { role: redis-server,
       redis_port: 6380,
       redis_slaveof: "127.0.0.1 6381",
       redis_save: none,
       redis_maxmemory_policy: volatile-ttl,
       redis_hz: 100,
       redis_appendfsync: "no"
       }

```

Options Available:

```yaml
################################ GENERAL  #####################################
redis_config_file
redis_daemonize
redis_port
redis_pidfile 
redis_bind
redis_unixsocket
redis_unixsocketperm
redis_timeout
redis_tcp_keepalive
redis_loglevel
redis_log_dir
redis_logfile
redis_syslog_enabled
redis_syslog_ident
redis_syslog_facility
redis_databases

################################ SNAPSHOTTING  ################################
redis_save
redis_stop_writes_on_bgsave_error
redis_rdbcompression
redis_rdbchecksum
redis_dbfilename
redis_dir
redis_slaveof
redis_masterauth
redis_slave_serve_stale_data
redis_slave_read_only
redis_repl_ping_slave_period
redis_repl_timeout
redis_repl_disable_tcp_nodelay
redis_repl_backlog_size
redis_repl_backlog_ttl
redis_slave_priority
redis_min_slaves_to_write
redis_min_slaves_max_lag

################################## SECURITY ###################################
redis_requirepass
redis_rename_command

################################### LIMITS ####################################
redis_maxclients
redis_maxmemory
redis_maxmemory_policy
redis_maxmemory_samples

############################## APPEND ONLY MODE ###############################
redis_appendonly
redis_appendfilename
appendfsync
redis_appendfsync
redis_appendfsync
redis_no_appendfsync_on_rewrite
redis_auto_aof_rewrite_percentage
redis_auto_aof_rewrite_min_size

################################ LUA SCRIPTING  ###############################
redis_lua_time_limit

################################## SLOW LOG ###################################
redis_slowlog_log_slower_than
redis_slowlog_max_len

############################# Event notification ##############################
redis_notify_keyspace_events

############################### ADVANCED CONFIG ###############################
redis_hash_max_ziplist_entries
redis_hash_max_ziplist_value
redis_list_max_ziplist_entries
redis_list_max_ziplist_value
redis_set_max_intset_entries
redis_zset_max_ziplist_entries
redis_zset_max_ziplist_value
redis_activerehashing
redis_client_output_buffer_limit 
redis_hz
redis_aof_rewrite_incremental_fsync


