---
title: "Radtest for Freeradius on Ubuntu12.04"
date: 2012-10-04
forum: New to Ubuntu
---

### Post by cway00 on 2012-10-04
After a successful installation of free radius I decided to run it on a debug mode with the following code 

```

sudo su 

```then 
```

radiusd -X

```The above code makes radius run in a debug mode 
This is what I got when I output the result in a file 

```

FreeRADIUS Version 2.2.0, for host i686-pc-linux-gnu, built on Oct  2 2012 at 09:47:42
Copyright (C) 1999-2012 The FreeRADIUS server project and contributors. 
There is NO warranty; not even for MERCHANTABILITY or FITNESS FOR A 
PARTICULAR PURPOSE. 
You may redistribute copies of FreeRADIUS under the terms of the 
GNU General Public License v2. 
Starting - reading configuration files ...
including configuration file /usr/local/etc/raddb/radiusd.conf
including configuration file /usr/local/etc/raddb/proxy.conf
including configuration file /usr/local/etc/raddb/clients.conf
including files in directory /usr/local/etc/raddb/modules/
including configuration file /usr/local/etc/raddb/modules/echo
including configuration file /usr/local/etc/raddb/modules/radutmp
including configuration file /usr/local/etc/raddb/modules/pam
including configuration file /usr/local/etc/raddb/modules/passwd
including configuration file /usr/local/etc/raddb/modules/mac2vlan
including configuration file /usr/local/etc/raddb/modules/wimax
including configuration file /usr/local/etc/raddb/modules/mac2ip
including configuration file /usr/local/etc/raddb/modules/redis
including configuration file /usr/local/etc/raddb/modules/krb5
including configuration file /usr/local/etc/raddb/modules/acct_unique
including configuration file /usr/local/etc/raddb/modules/perl
including configuration file /usr/local/etc/raddb/modules/cache
including configuration file /usr/local/etc/raddb/modules/checkval
including configuration file /usr/local/etc/raddb/modules/cui
including configuration file /usr/local/etc/raddb/modules/chap
including configuration file /usr/local/etc/raddb/modules/exec
including configuration file /usr/local/etc/raddb/modules/opendirectory
including configuration file /usr/local/etc/raddb/modules/ldap
including configuration file /usr/local/etc/raddb/modules/realm
including configuration file /usr/local/etc/raddb/modules/expiration
including configuration file /usr/local/etc/raddb/modules/files
including configuration file /usr/local/etc/raddb/modules/detail.example.com
including configuration file /usr/local/etc/raddb/modules/digest
including configuration file /usr/local/etc/raddb/modules/detail.log
including configuration file /usr/local/etc/raddb/modules/pap
including configuration file /usr/local/etc/raddb/modules/counter
including configuration file /usr/local/etc/raddb/modules/sqlcounter_expire_on_login
including configuration file /usr/local/etc/raddb/modules/etc_group
including configuration file /usr/local/etc/raddb/modules/sql_log
including configuration file /usr/local/etc/raddb/modules/preprocess
including configuration file /usr/local/etc/raddb/modules/dynamic_clients
including configuration file /usr/local/etc/raddb/modules/linelog
including configuration file /usr/local/etc/raddb/modules/attr_filter
including configuration file /usr/local/etc/raddb/modules/soh
including configuration file /usr/local/etc/raddb/modules/radrelay
including configuration file /usr/local/etc/raddb/modules/ntlm_auth
including configuration file /usr/local/etc/raddb/modules/rediswho
including configuration file /usr/local/etc/raddb/modules/sradutmp
including configuration file /usr/local/etc/raddb/modules/detail
including configuration file /usr/local/etc/raddb/modules/unix
including configuration file /usr/local/etc/raddb/modules/mschap
including configuration file /usr/local/etc/raddb/modules/smbpasswd
including configuration file /usr/local/etc/raddb/modules/dhcp_sqlippool
including configuration file /usr/local/etc/raddb/sql/mysql/ippool-dhcp.conf
including configuration file /usr/local/etc/raddb/modules/ippool
including configuration file /usr/local/etc/raddb/modules/replicate
including configuration file /usr/local/etc/raddb/modules/otp
including configuration file /usr/local/etc/raddb/modules/logintime
including configuration file /usr/local/etc/raddb/modules/policy
including configuration file /usr/local/etc/raddb/modules/attr_rewrite
including configuration file /usr/local/etc/raddb/modules/expr
including configuration file /usr/local/etc/raddb/modules/smsotp
including configuration file /usr/local/etc/raddb/modules/always
including configuration file /usr/local/etc/raddb/modules/inner-eap
including configuration file /usr/local/etc/raddb/eap.conf
including configuration file /usr/local/etc/raddb/policy.conf
including files in directory /usr/local/etc/raddb/sites-enabled/
including configuration file /usr/local/etc/raddb/sites-enabled/default
including configuration file /usr/local/etc/raddb/sites-enabled/inner-tunnel
including configuration file /usr/local/etc/raddb/sites-enabled/control-socket
main {
    allow_core_dumps = no
}
including dictionary file /usr/local/etc/raddb/dictionary
main {
    name = "radiusd"
    prefix = "/usr/local"
    localstatedir = "/usr/local/var"
    sbindir = "/usr/local/sbin"
    logdir = "/usr/local/var/log/radius"
    run_dir = "/usr/local/var/run/radiusd"
    libdir = "/usr/local/lib"
    radacctdir = "/usr/local/var/log/radius/radacct"
    hostname_lookups = no
    max_request_time = 30
    cleanup_delay = 5
    max_requests = 1024
    pidfile = "/usr/local/var/run/radiusd/radiusd.pid"
    checkrad = "/usr/local/sbin/checkrad"
    debug_level = 0
    proxy_requests = yes
 log {
    stripped_names = no
    auth = no
    auth_badpass = no
    auth_goodpass = no
 }
 security {
    max_attributes = 200
    reject_delay = 1
    status_server = yes
 }
}
radiusd: #### Loading Realms and Home Servers ####
 proxy server {
    retry_delay = 5
    retry_count = 3
    default_fallback = no
    dead_time = 120
    wake_all_if_all_dead = no
 }
 home_server localhost {
    ipaddr = 127.0.0.1
    port = 1812
    type = "auth"
    secret = "testing123"
    response_window = 20
    max_outstanding = 65536
    require_message_authenticator = yes
    zombie_period = 40
    status_check = "status-server"
    ping_interval = 30
    check_interval = 30
    num_answers_to_alive = 3
    num_pings_to_alive = 3
    revive_interval = 120
    status_check_timeout = 4
  coa {
    irt = 2
    mrt = 16
    mrc = 5
    mrd = 30
  }
 }
 home_server_pool my_auth_failover {
    type = fail-over
    home_server = localhost
 }
 realm example.com {
    auth_pool = my_auth_failover
 }
 realm LOCAL {
 }
radiusd: #### Loading Clients ####
 client localhost {
    ipaddr = 127.0.0.1
    require_message_authenticator = no
    secret = "testing123"
    nastype = "other"
 }
radiusd: #### Instantiating modules ####
 instantiate {
 Module: Linked to module rlm_exec
 Module: Instantiating module "exec" from file /usr/local/etc/raddb/modules/exec
  exec {
    wait = no
    input_pairs = "request"
    shell_escape = yes
  }
 Module: Linked to module rlm_expr
 Module: Instantiating module "expr" from file /usr/local/etc/raddb/modules/expr
 Module: Linked to module rlm_expiration
 Module: Instantiating module "expiration" from file /usr/local/etc/raddb/modules/expiration
  expiration {
    reply-message = "Password Has Expired  "
  }
 Module: Linked to module rlm_logintime
 Module: Instantiating module "logintime" from file /usr/local/etc/raddb/modules/logintime
  logintime {
    reply-message = "You are calling outside your allowed timespan  "
    minimum-timeout = 60
  }
 }
radiusd: #### Loading Virtual Servers ####
server { # from file /usr/local/etc/raddb/radiusd.conf
 modules {
  Module: Creating Auth-Type = digest
  Module: Creating Post-Auth-Type = REJECT
 Module: Checking authenticate {...} for more modules to load
 Module: Linked to module rlm_pap
 Module: Instantiating module "pap" from file /usr/local/etc/raddb/modules/pap
  pap {
    encryption_scheme = "auto"
    auto_header = no
  }
 Module: Linked to module rlm_chap
 Module: Instantiating module "chap" from file /usr/local/etc/raddb/modules/chap
 Module: Linked to module rlm_mschap
 Module: Instantiating module "mschap" from file /usr/local/etc/raddb/modules/mschap
  mschap {
    use_mppe = yes
    require_encryption = no
    require_strong = no
    with_ntdomain_hack = no
    allow_retry = yes
  }
 Module: Linked to module rlm_digest
 Module: Instantiating module "digest" from file /usr/local/etc/raddb/modules/digest
 Module: Linked to module rlm_unix
 Module: Instantiating module "unix" from file /usr/local/etc/raddb/modules/unix
  unix {
    radwtmp = "/usr/local/var/log/radius/radwtmp"
  }
 Module: Linked to module rlm_eap
 Module: Instantiating module "eap" from file /usr/local/etc/raddb/eap.conf
  eap {
    default_eap_type = "md5"
    timer_expire = 60
    ignore_unknown_eap_types = no
    cisco_accounting_username_bug = no
    max_sessions = 4096
  }
 Module: Linked to sub-module rlm_eap_md5
 Module: Instantiating eap-md5
 Module: Linked to sub-module rlm_eap_leap
 Module: Instantiating eap-leap
 Module: Linked to sub-module rlm_eap_gtc
 Module: Instantiating eap-gtc
   gtc {
    challenge = "Password: "
    auth_type = "PAP"
   }
Ignoring EAP-Type/tls because we do not have OpenSSL support.
Ignoring EAP-Type/ttls because we do not have OpenSSL support.
Ignoring EAP-Type/peap because we do not have OpenSSL support.
 Module: Linked to sub-module rlm_eap_mschapv2
 Module: Instantiating eap-mschapv2
   mschapv2 {
    with_ntdomain_hack = no
    send_error = no
   }
 Module: Checking authorize {...} for more modules to load
 Module: Linked to module rlm_preprocess
 Module: Instantiating module "preprocess" from file /usr/local/etc/raddb/modules/preprocess
  preprocess {
    huntgroups = "/usr/local/etc/raddb/huntgroups"
    hints = "/usr/local/etc/raddb/hints"
    with_ascend_hack = no
    ascend_channels_per_line = 23
    with_ntdomain_hack = no
    with_specialix_jetstream_hack = no
    with_cisco_vsa_hack = no
    with_alvarion_vsa_hack = no
  }
reading pairlist file /usr/local/etc/raddb/huntgroups
reading pairlist file /usr/local/etc/raddb/hints
 Module: Linked to module rlm_realm
 Module: Instantiating module "suffix" from file /usr/local/etc/raddb/modules/realm
  realm suffix {
    format = "suffix"
    delimiter = "@"
    ignore_default = no
    ignore_null = no
  }
 Module: Linked to module rlm_files
 Module: Instantiating module "files" from file /usr/local/etc/raddb/modules/files
  files {
    usersfile = "/usr/local/etc/raddb/users"
    acctusersfile = "/usr/local/etc/raddb/acct_users"
    preproxy_usersfile = "/usr/local/etc/raddb/preproxy_users"
    compat = "no"
  }
reading pairlist file /usr/local/etc/raddb/users
reading pairlist file /usr/local/etc/raddb/acct_users
reading pairlist file /usr/local/etc/raddb/preproxy_users
 Module: Checking preacct {...} for more modules to load
 Module: Linked to module rlm_acct_unique
 Module: Instantiating module "acct_unique" from file /usr/local/etc/raddb/modules/acct_unique
  acct_unique {
    key = "User-Name, Acct-Session-Id, NAS-IP-Address, NAS-Identifier, NAS-Port"
  }
 Module: Checking accounting {...} for more modules to load
 Module: Linked to module rlm_detail
 Module: Instantiating module "detail" from file /usr/local/etc/raddb/modules/detail
  detail {
    detailfile = "/usr/local/var/log/radius/radacct/%{%{Packet-Src-IP-Address}:-%{Packet-Src-IPv6-Address}}/detail-%Y%m%d"
    header = "%t"
    detailperm = 384
    dirperm = 493
    locking = no
    log_packet_header = no
  }
 Module: Linked to module rlm_attr_filter
 Module: Instantiating module "attr_filter.accounting_response" from file /usr/local/etc/raddb/modules/attr_filter
  attr_filter attr_filter.accounting_response {
    attrsfile = "/usr/local/etc/raddb/attrs.accounting_response"
    key = "%{User-Name}"
    relaxed = no
  }
reading pairlist file /usr/local/etc/raddb/attrs.accounting_response
 Module: Checking session {...} for more modules to load
 Module: Linked to module rlm_radutmp
 Module: Instantiating module "radutmp" from file /usr/local/etc/raddb/modules/radutmp
  radutmp {
    filename = "/usr/local/var/log/radius/radutmp"
    username = "%{User-Name}"
    case_sensitive = yes
    check_with_nas = yes
    perm = 384
    callerid = yes
  }
 Module: Checking post-proxy {...} for more modules to load
 Module: Checking post-auth {...} for more modules to load
 Module: Instantiating module "attr_filter.access_reject" from file /usr/local/etc/raddb/modules/attr_filter
  attr_filter attr_filter.access_reject {
    attrsfile = "/usr/local/etc/raddb/attrs.access_reject"
    key = "%{User-Name}"
    relaxed = no
  }
reading pairlist file /usr/local/etc/raddb/attrs.access_reject
 } # modules
} # server
server inner-tunnel { # from file /usr/local/etc/raddb/sites-enabled/inner-tunnel
 modules {
 Module: Checking authenticate {...} for more modules to load
 Module: Checking authorize {...} for more modules to load
 Module: Checking session {...} for more modules to load
 Module: Checking post-proxy {...} for more modules to load
 Module: Checking post-auth {...} for more modules to load
 } # modules
} # server
radiusd: #### Opening IP addresses and Ports ####
listen {
    type = "auth"
    ipaddr = *
    port = 0
}
listen {
    type = "acct"
    ipaddr = *
    port = 0
}
listen {
    type = "control"
 listen {
    socket = "/usr/local/var/run/radiusd/radiusd.sock"
 }
}
listen {
    type = "auth"
    ipaddr = 127.0.0.1
    port = 18120
}
 ... adding new socket proxy address * port 42259
Listening on authentication address * port 1812
Listening on accounting address * port 1813
Listening on command file /usr/local/var/run/radiusd/radiusd.sock
Listening on authentication address 127.0.0.1 port 18120 as server inner-tunnel
Listening on proxy address * port 1814
Ready to process requests.

```Showing that installation and editing was successful..

But when I do a test run on the radius server with the following code :

```

radtest guest guest 127.0.0.1 0 radpassword

```radpassword is my secret key that the server and the clients

error.. I get the error that my shared key is incorrect ..after following alot of working setup of freeradius..

any help will be appreciated

---

### Post by rai4shu2 on 2012-10-04
Actually, your shared key is not correct:

```
radiusd: #### Loading Clients ####
 client localhost {
    ipaddr = 127.0.0.1
    require_message_authenticator = no
    secret = "testing123"
    nastype = "other"
 }
```

---

### Post by cway00 on 2012-10-04
Thanks for the great clue.. it was allthis while looking at me nd was bz ](*,) ..thanks . I really appreciate

---

