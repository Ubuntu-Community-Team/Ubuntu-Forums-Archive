---
title: "Enable custom bind9 logging"
date: 2016-11-03
forum: Programming Talk
---

### Post by dam034 on 2016-11-03
Dear users,

I have a mini-pc with OS ubuntu server. This mini-pc is the DNS server of my office.

It works fine, but my headoffice has appointed me to enable bind9 logging to see all DNS queries.

Particularly, I need:
[LIST]
[*]this log format: ip address of client, dns name requested to resolve, date, time;
[*]enable logs for all ips, except for those specified by me (ip of headoffice pc);
[*]write logs in .txt or .log files per day (es: 2016-11-03.log) in the folder specified by me (es: /var/log/bind);
[/LIST]

Or if possible, to save the log in a table of a mysql database.


How can I do?


Thanks,
dam034

---

### Post by spjackson on 2016-11-03
I think that bind9's query logging will provide you with the basic information you need. See the Logging section here: [https://help.ubuntu.com/community/BIND9ServerHowto](https://help.ubuntu.com/community/BIND9ServerHowto)

As for excluding specific IPs and formatting to your requirements, whether a text file or database, I think you will need to write your own custom script for that.

---

### Post by dam034 on 2016-11-07
> **spjackson said:**
> I think that bind9's query logging will provide you with the basic information you need. See the Logging section here: [https://help.ubuntu.com/community/BIND9ServerHowto](https://help.ubuntu.com/community/BIND9ServerHowto)
I have read the section, but I don't understand where I have to write the code.

> **spjackson said:**
> As for excluding specific IPs and formatting to your requirements, whether a text file or database, I think you will need to write your own custom script for that.
I'm not able to enable simple logs, imagine my own script!



Thanks,
dam034

---

### Post by SeijiSensei on 2016-11-07
[https://help.ubuntu.com/community/BIND9ServerHowto#Channel_Option](https://help.ubuntu.com/community/BIND9ServerHowto#Channel_Option)

As it says explicitly, you need to add these lines to /etc/bind/named.conf.local.  They should not be inside another "{}" container, but stand on their own before the zone files are defined.

```

options {
        various stuff
};

logging {
    channel query.log {
        file "/var/lib/bind/query.log";
        // Set the severity to dynamic to see all the debug messages.
        severity debug 3;
    };

    category queries { query.log; };
};

zone ...

```

---

### Post by dam034 on 2016-11-28
I did so:

/etc/bind/named.conf.options
```
options {
        directory "/var/cache/bind";

        // If there is a firewall between you and nameservers you want
        // to talk to, you may need to fix the firewall to allow multiple
        // ports to talk.  See http://www.kb.cert.org/vuls/id/800113

        // If your ISP provided one or more IP addresses for stable
        // nameservers, you probably want to use them as forwarders.
        // Uncomment the following block, and insert the addresses replacing
        // the all-0's placeholder.

        // forwarders {
        //      0.0.0.0;
        // };

        //=====================================================================$
        // If BIND logs error messages about the root key being expired,
        // you will need to update your keys.  See https://www.isc.org/bind-keys
        //=====================================================================$
        dnssec-validation auto;

        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };
};

logging {
    channel query.log {
        file "/etc/bind/richieste.log";
        // Set the severity to dynamic to see all the debug messages.
        severity debug 3;
    };

    category queries { query.log; };
};
```
I didn't edit options{ }

I executed these commands:
```
root@srvesp:/etc/bind# touch richieste.log
root@srvesp:/etc/bind# ls -ahl
totale 60K
drwxr-sr-x  2 root bind 4,0K nov 28 13:14 .
drwxr-xr-x 90 root root 4,0K nov 28 09:08 ..
-rw-r--r--  1 root root 2,4K mar 24  2014 bind.keys
-rw-r--r--  1 root root  237 mar 24  2014 db.0
-rw-r--r--  1 root root  271 mar 24  2014 db.127
-rw-r--r--  1 root root  237 mar 24  2014 db.255
-rw-r--r--  1 root root  353 mar 24  2014 db.empty
-rw-r--r--  1 root root  270 mar 24  2014 db.local
-rw-r--r--  1 root root 3,0K mar 24  2014 db.root
-rw-r--r--  1 root bind  463 mar 24  2014 named.conf
-rw-r--r--  1 root bind  490 mar 24  2014 named.conf.default-zones
-rw-r--r--  1 root bind  165 mar 24  2014 named.conf.local
-rw-r--r--  1 root bind 1,1K nov 28 13:15 named.conf.options
-rw-r--r--  1 root bind    0 nov 28 13:14 richieste.log
-rw-r-----  1 bind bind   77 nov 28 08:56 rndc.key
-rw-r--r--  1 root root 1,3K mar 24  2014 zones.rfc1918
root@srvesp:/etc/bind# service bind9 start
 * Starting domain name service... bind9                                 [fail]
```

Why does bind9 fail?


Thanks,
dam034

---

### Post by SeijiSensei on 2016-11-28
What do you see in /var/log/syslog?

I'm not entirely sure how Ubuntu BIND is configured (I use CentOS on servers), but it may be a permissions problem.  If the syslog error isn't obvious, try using "sudo chown bind:bind /etc/bind/richieste.log" and see if that helps.

---

