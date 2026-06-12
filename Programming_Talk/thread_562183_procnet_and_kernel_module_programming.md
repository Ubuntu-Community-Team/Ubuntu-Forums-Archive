---
title: "/proc/net and kernel module programming"
date: 2007-09-28
forum: Programming Talk
---

### Post by edfredcoder on 2007-09-28
Hello. I am learning how to write linux kernel modules, so please excuse my noobyness. :)

I have some code at the beginning of my module to iterate over /proc/net, printing out the get_info pointer for each one. So the code I have this:
```

struct proc_dir_entry *p;
for(p=proc_net->subdir;p;p=p->next)
{
     printk("%s->get_info=%u\n",p->name,p->get_info);
}

```
I checked the results with dmesg | tail, and its almost all NULL!
```

ip6_flowlabel->get_info=0
rt6_stats->get_info=0
ipv6_route->get_info=4176800394
if_inet6->get_info=0
anycast6->get_info=0
sockstat6->get_info=0
dev_snmp6->get_info=0
snmp6->get_info=0
udplite6->get_info=0
udp6->get_info=0
tcp6->get_info=0
raw6->get_info=0
mcfilter6->get_info=0
igmp6->get_info=0
irda->get_info=0
packet->get_info=0
unix->get_info=0
tr_rif->get_info=0
sockstat->get_info=0
snmp->get_info=0
netstat->get_info=0
route->get_info=0
udp->get_info=0
tcp->get_info=0
raw->get_info=0
ip_mr_cache->get_info=0
ip_mr_vif->get_info=0
udplite->get_info=0
mcfilter->get_info=0
igmp->get_info=0
rt_acct->get_info=0
rt_cache->get_info=0
arp->get_info=0
atm->get_info=0
psched->get_info=0
dev_mcast->get_info=0
wireless->get_info=0
softnet_stat->get_info=0
dev->get_info=0
protocols->get_info=0
netlink->get_info=0
netfilter->get_info=0
stat->get_info=0

```
This doesn't make any sense, because many of these (such as /proc/net/dev) you can read from, so they should have a non-null get_info field.

Can someone please explain this to me? I'm very confused.

-Kevin

---

