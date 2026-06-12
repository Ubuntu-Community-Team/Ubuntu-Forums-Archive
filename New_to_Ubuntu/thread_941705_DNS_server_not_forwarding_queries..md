---
title: "DNS server not forwarding queries."
date: 2008-10-08
forum: New to Ubuntu
---

### Post by chronopiccolo74 on 2008-10-08
Hopefully I am just missing something simple. I'm trying to set up an ubuntu 8.04 server to be a dns server for my entire network. The problem is when I point client machines, say an XP box, to the server for DNS queries, it rejects them. I get errors in the daemon.log saying things like 

"client 10.0.231.13#1045: query (cache) 'google.com/A/IN' denied" 

When I configure specific zones for the server to be authoritvie for, it responds only to queries directed for that domain.

I went in the /etc/bind/named.conf.options and uncommented the forwarders line so that it looks like this:

options {
        directory "/var/cache/bind";

        // If there is a firewall between you and nameservers you want
        // to talk to, you might need to uncomment the query-source
        // directive below.  Previous versions of BIND always asked
        // questions using port 53, but BIND 8.1 and later use an unprivileged
        // port by default.

         query-source address * port 53;

        // If your ISP provided one or more IP addresses for stable
        // nameservers, you probably want to use them as forwarders.
        // Uncomment the following block, and insert the addresses replacing
        // the all-0's placeholder.

         forwarders {
                4.2.2.2;
         };

        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };
};
 
According to the official docs that should be all I need to do to make the forwarding work, but obviously it's not... So, can anyone help me?!

---

### Post by chronopiccolo74 on 2008-10-08
Ok, so I found where the issue was. The requests were coming from a different subnet from the one the dns server was sitting on. So after adding the "allow-queries {ip_range_for_valid_clients}" it started accepting them.

---

