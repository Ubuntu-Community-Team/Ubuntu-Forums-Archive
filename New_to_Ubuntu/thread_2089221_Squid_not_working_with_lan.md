---
title: "Squid not working with lan"
date: 2012-11-28
forum: New to Ubuntu
---

### Post by kanjah on 2012-11-28
am using squid 2.7stable9 on ubuntu 12 server, with two NIC cards, one for WAN i.p 81.25.128.35, LAN 198.168.1.37 and gadmin for management,  my squid isn't responding to lan NIC connections, any advice? squid.conf is as follows
http_port 192.168.1.34:3128 transparent
visible_hostname [EMAIL="cache@sdn.so"]cache@sdn.so[/EMAIL]
mail_from [EMAIL="tech@sdn.so"]tech@sdn.so[/EMAIL]
client_netmask 255.255.255.0
snmp_incoming_address 0.0.0.0
snmp_outgoing_address 255.255.255.255
udp_incoming_address 0.0.0.0
udp_outgoing_address 255.255.255.255
icp_port 3130 proxy-only
cache_replacement_policy lru
memory_replacement_policy lru
cache_dir ufs /var/spool/squid 100 16 256
hierarchy_stoplist cgi-bin ?
access_log /var/log/squid/access.log squid
cache_log /var/log/squid/cache.log
cache_store_log /var/log/squid/store.log
pid_filename /var/run/squid.pid
hosts_file /etc/hosts
icon_directory /usr/share/squid/icons
error_directory /usr/share/squid/errors/en
diskd_program /usr/lib/squid/diskd-daemon
unlinkd_program /usr/lib/squid/unlinkd
debug_options ALL,1
ftp_user Squid@
uri_whitespace strip
cache_effective_user squid
cache_effective_group squid
cache_mgr root
mail_program mail
umask 027
announce_host tracker.ircache.net
as_whois_server whois.ra.net
wccp_address 0.0.0.0
wccp2_address 0.0.0.0
wccp_router 0.0.0.0
store_dir_select_algorithm least-load
coredump_dir /var/spool/squid
icp_query_timeout 0
maximum_icp_query_timeout 2000
mcast_icp_query_timeout 2000
dead_peer_timeout 10 seconds
forward_timeout 4 minutes
connect_timeout 1 minutes
peer_connect_timeout 30 seconds
read_timeout 15 minutes
request_timeout 5 minutes
persistent_request_timeout 1 minutes
pconn_timeout 120 seconds
ident_timeout 10 seconds
dns_timeout 2 minutes
dns_retransmit_interval 5 seconds
snmp_port 0
cache_mem 8 MB
cache_swap_low 90
cache_swap_high 95
maximum_object_size 4096 KB
minimum_object_size 0 KB
maximum_object_size_in_memory 8 KB
ipcache_size 1024
ipcache_low 90
ipcache_high 95
fqdncache_size 1024
ftp_list_width 32
memory_pools_limit 5 MB
request_header_max_size 20 KB
request_body_max_size 0 KB
quick_abort_min 16 KB
quick_abort_max 16 KB
quick_abort_pct 95
read_ahead_gap 16 KB
negative_ttl 5 minutes
positive_dns_ttl 6 seconds
negative_dns_ttl 1 seconds
range_offset_limit 0 KB
client_lifetime 1 day
shutdown_lifetime 30 seconds
reply_header_max_size 20 KB
announce_period 50 seconds
announce_port 3131
logfile_rotate 0
tcp_recv_bufsize 0 bytes
minimum_direct_hops 4
minimum_direct_rtt 400
store_avg_object_size 13 KB
store_objects_per_bucket 20
netdb_low 900
netdb_high 1000
netdb_ping_period 5 minutes
maximum_single_addr_tries 1
wccp_version 4
wccp2_forwarding_method 1
wccp2_return_method 1
wccp2_assignment_method 1
wccp2_service standard 0
wccp2_weight 10000
max_open_disk_fds 0
digest_bits_per_entry 5
digest_rebuild_period 1 seconds
digest_rewrite_period 1 seconds
digest_swapout_chunk_size 4096 bytes
digest_rebuild_chunk_percentage 10
high_response_time_warning 0
high_page_fault_warning 0
high_memory_warning 60 MB
sleep_after_fork 0
minimum_expiry_time 60 seconds
authenticate_cache_garbage_interval 1 seconds
authenticate_ttl 1 seconds
authenticate_ip_ttl 20 seconds
check_hostnames on
dns_defnames off
emulate_httpd_log off
log_ip_on_direct on
log_mime_hdrs off
log_fqdn off
ftp_passive on
ftp_sanitycheck on
ftp_telnet_protocol on
allow_underscore on
memory_pools on
half_closed_clients on
httpd_suppress_version_string off
via on
forwarded_for on
log_icp_queries on
client_db on
icp_hit_stale off
query_icmp off
test_reachability off
buffered_logs off
reload_into_ims off
global_internal_static on
short_icon_urls off
offline_mode off
nonhierarchical_direct on
prefer_direct off
strip_query_terms on
redirector_bypass off
ignore_unknown_nameservers on
client_persistent_connections on
server_persistent_connections on
persistent_connection_after_error off
detect_broken_pconn off
balance_on_multiple_ip on
pipeline_prefetch off
request_entities off
ie_refresh off
vary_ignore_expire off
relaxed_header_parser on
retry_on_error off
wccp2_rebuild_wait on
digest_generation on

acl our_networks src 192.168.0.0/24 192.168.1.0/24 10.8.0.0/32
acl localhost src 127.0.0.1/32
acl to_localhost dst 127.0.0.0/8
acl manager proto cache_object
acl QUERY urlpath_regex cgi-bin \?
acl apache rep_header Server ^Apache
acl SSL_ports port 443
acl Safe_ports port 80        # http
acl Safe_ports port 21        # ftp
acl Safe_ports port 443        # https
acl Safe_ports port 70        # gopher
acl Safe_ports port 210        # wais
acl Safe_ports port 1025-65535    # unregistered ports
acl Safe_ports port 280        # http-mgmt
acl Safe_ports port 488        # gss-http
acl Safe_ports port 591        # filemaker
acl Safe_ports port 777        # multiling http
acl CONNECT method CONNECT

http_access allow our_networks
http_reply_access allow all
icp_access allow all
miss_access allow all
http_access allow !Safe_ports
cache allow QUERY
http_access deny CONNECT !SSL_ports
http_access deny to_localhost
ident_lookup_access deny all
http_access allow all
snmp_access deny all

thanks

---

### Post by newbie-user on 2012-11-28
```
http_port 192.168.1.34:3128 transparent
```

That line is causing the problem. It should just be

```
http_port 3128 transparent
```

Also, have you set up your iptables to reroute lan traffic from port 80 to 3128?

And one more thing, your LAN IP of 198.168.1.37 is using a routable address. You need to change it to a nonroutable address for your internal network. Looks like you're using 192.168.0.0/24 and 192.168.0.1/24 for your internal network. Change your lan IP to match.

---

### Post by SeijiSensei on 2012-11-28
You need to use iptables to route all outbound requests for port 80 to go through the proxy like this:

```
sudo /sbin/iptables -A PREROUTING -s your.internal.network.0/mask -p tcp -m tcp --dport 80 -j REDIRECT --to-ports 3128 
```

replacing your.internal.network.0/mask with the network and mask of the LAN, e.g., 192.168.1.0/24.  If both 192.168.0.0/24 and 192.168.1.0/24 are accessing the proxy, use 192.168.0.0/16 in the iptables rule to encompass the entire range of legitimate addresses.

If this fixes your problem, either add it to your current iptables ruleset, or place the command in /etc/rc.local (without the initial sudo) so it will be run at boot.

---

### Post by kanjah on 2012-12-01
> **newbie-user said:**
> ```
http_port 192.168.1.34:3128 transparent
```That line is causing the problem. It should just be

```
http_port 3128 transparent
```Also, have you set up your iptables to reroute lan traffic from port 80 to 3128?

And one more thing, your LAN IP of 198.168.1.37 is using a routable address. You need to change it to a nonroutable address for your internal network. Looks like you're using 192.168.0.0/24 and 192.168.0.1/24 for your internal network. Change your lan IP to match.
hi, thanks for the help, ave setup my iptables, still can't connect, changed my lan i.p to 192.168.0.34

---

### Post by kanjah on 2012-12-01
> **SeijiSensei said:**
> You need to use iptables to route all outbound requests for port 80 to go through the proxy like this:

```
sudo /sbin/iptables -A PREROUTING -s your.internal.network.0/mask -p tcp -m tcp --dport 80 -j REDIRECT --to-ports 3128 
```replacing your.internal.network.0/mask with the network and mask of the LAN, e.g., 192.168.1.0/24.  If both 192.168.0.0/24 and 192.168.1.0/24 are accessing the proxy, use 192.168.0.0/16 in the iptables rule to encompass the entire range of legitimate addresses.

If this fixes your problem, either add it to your current iptables ruleset, or place the command in /etc/rc.local (without the initial sudo) so it will be run at boot.
  

thanks men,  yur a lifesaver

---

### Post by kanjah on 2012-12-01
hi there, am using mikrotik router board 1100,  did a restore on one of my backup files, now all my clients complain of not sending mail via outlook though they can recieve, i dnt host their mails only provide internet, what rule should i use on the firewall to allow stmp
thanks

---

### Post by SeijiSensei on 2012-12-01
Are they using the Outlook client or Outlook Web Access?

Did this happen after adding the rule I gave you above?  It should not have affected anything having to do with SMTP.

Does your iptables ruleset have a rule to masquerade outbound traffic?

Post your iptables rules inside of [noparse]```

```[/noparse] tags.

---

### Post by kanjah on 2012-12-11
hi sensei, thanks alot, my system worked well though with low speed than i expected.......thank agen, sorry for not posting this earlier

---

