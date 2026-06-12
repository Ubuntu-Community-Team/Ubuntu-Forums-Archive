---
title: "Help Setting up BIND"
date: 2012-09-19
forum: New to Ubuntu
---

### Post by ewellb on 2012-09-19
Ok I am having some difficulty in trying to get BIND9 working, I used a common tutorial and thought that I have done everything correctly, but I keep getting the following error  

rndc: connect failed: 127.0.0.1#953: connection refused

root@ubuntu:/# /usr/sbin/named -g
19-Sep-2012 08:14:48.248 starting BIND 9.8.1-P1 -g
19-Sep-2012 08:14:48.250 built with '--prefix=/usr' '--mandir=/usr/share/man' '--infodir=/usr/share/info' '--sysconfdir=/etc/bind' '--localstatedir=/var' '--enable-threads' '--enable-largefile' '--with-libtool' '--enable-shared' '--enable-static' '--with-openssl=/usr' '--with-gssapi=/usr' '--with-gnu-ld' '--with-geoip=/usr' '--enable-ipv6' 'CFLAGS=-fno-strict-aliasing -DDIG_SIGCHASE -O2' 'LDFLAGS=-Wl,-Bsymbolic-functions -Wl,-z,relro' 'CPPFLAGS=-D_FORTIFY_SOURCE=2'
19-Sep-2012 08:14:48.251 adjusted limit on open files from 4096 to 1048576
19-Sep-2012 08:14:48.252 found 2 CPUs, using 2 worker threads
19-Sep-2012 08:14:48.254 using up to 4096 sockets
19-Sep-2012 08:14:48.418 loading configuration from '/etc/bind/named.conf'
19-Sep-2012 08:14:48.428 /etc/bind/named.conf:23: expected quoted string near '/'
19-Sep-2012 08:14:48.430 loading configuration: unexpected token
19-Sep-2012 08:14:48.430 exiting (due to fatal error)

Before I was getting a permissions error on several folders so I change the permissions and that fixed those errors, but I am still getting a fatal error here. 

Not sure what I am missing. 

Any help would be appropriated

---

### Post by termvrl on 2012-09-19
it maybe a permission issue.
i found this link. [http://www.linuxquestions.org/questions/linux-networking-3/dns-rndc-service-errror-229950/](http://www.linuxquestions.org/questions/linux-networking-3/dns-rndc-service-errror-229950/)

hope help you.

---

### Post by ewellb on 2012-09-19
Thank you but I read that post also, with no help, I am not even sure what is erroring out, I have checked my firewall ( turned off ) I confirmed that the port forwarding is working, not sure where to find the problem.

---

### Post by cmont899 on 2012-09-19
what does your named.conf look like? Specifically around line 23:

```
 19-Sep-2012 08:14:48.428 /etc/bind/named.conf:23: expected quoted string near '/'
```

---

### Post by ewellb on 2012-09-19
> **cmont899 said:**
> what does your named.conf look like? Specifically around line 23:

```
 19-Sep-2012 08:14:48.428 /etc/bind/named.conf:23: expected quoted string near '/'
```

//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
include "/etc/bind/rndc.key";

controls {
inet 127.0.0.1 port 953
allow {127.0.0.1;} keys { "rndc-key"; };
};

# This is the zone definition. replace example.com with your domain name
zone testserver1.mytestingaccount.com {
        type master;
        file "/etc/bind/zones/testserver1.mytestingaccount.com.db";
        };

# This is the zone definition for reverse DNS. replace 0.1.168.192 with your network a$
zone "63.1.168.192.in-addr.arpa" {
     type master;
     file /etc/bind/zones/rev.63.1.168.192.in-addr.arpa;
};

---

### Post by cmont899 on 2012-09-19
add quotes around your file path:

Change:
```
# This is the zone definition for reverse DNS. replace 0.1.168.192 with your network a$
zone "63.1.168.192.in-addr.arpa" {
     type master;
     file /etc/bind/zones/rev.63.1.168.192.in-addr.arpa;
};
```to:
```
# This is the zone definition for reverse DNS. replace 0.1.168.192 with your network a$
zone "63.1.168.192.in-addr.arpa" {
     type master;
     file "/etc/bind/zones/rev.63.1.168.192.in-addr.arpa";
};
```

---

### Post by ewellb on 2012-09-19
> **cmont899 said:**
> add quotes around your file path:

Change:
```
# This is the zone definition for reverse DNS. replace 0.1.168.192 with your network a$
zone "63.1.168.192.in-addr.arpa" {
     type master;
     file /etc/bind/zones/rev.63.1.168.192.in-addr.arpa;
};
```to:
```
# This is the zone definition for reverse DNS. replace 0.1.168.192 with your network a$
zone "63.1.168.192.in-addr.arpa" {
     type master;
     file "/etc/bind/zones/rev.63.1.168.192.in-addr.arpa";
};
```


root@ubuntu:/etc/bind# /etc/init.d/bind9 restart
 * Stopping domain name service... bind9                                               waiting for pid 11261 to die
                                                                                [ OK ]
 * Starting domain name service... bind9                                        [ OK ]
root@ubuntu:/etc/bind#


THAT DID THE TRICK !!  

THANK YOU

---

