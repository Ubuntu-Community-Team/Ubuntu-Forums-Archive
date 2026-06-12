---
title: "Request feedback on my implementation of a DNS server"
date: 2011-06-25
forum: Programming Talk
---

### Post by WitchCraft on 2011-06-25
Hi,
 
I recently wanted to setup a DNS server, wich uses a database, and write a web frontend so I could move my DNS entries from EveryDNS.net to my own server.
 
The intention is that I wouldn't have to migrate all my website's DNS entries in the future, if a free DNS service, such as EveryDNS suddenly decides it wants to charge, which means I need to move all those entries elsewhere if I continue to want my DNS entries to be FREE OF (impudent) CHARGES.
 
Unfortunately, there were some issues:
1. bind9 requires recompilation for use with MySQL and PostGre SQL. This means that I won't be having security updates.
2. Bind pestered about dns-sec keys, and just wouldn't work without it. When I generated a pair, it said they were invalid. (Before, the key generator crashed when I wanted to create a 4096 bit DH key, so I had to go for the standard 256 bit crap which then failed, too).
3. It doesn't support anything else than MySQL and PostGre (I'd like to use FireBird !)
4. There doesn't exist a real alternative to bind9.
5. All things C and Java tend not to offer interfaces for C#
 
In short, after spending three hours trying to configure bind9 yesterday evening, I got so mad at whoever wrote and documented this crap, that I decided it was easier and faster to write my very own DNS server.
 
It's a very basic DNS server, just implementing lookup and nothing more. Request arrives, database is searched, if match, a valid response is returned, else the response is server error.
 
Since a DNS server is a pretty dangerous thing...
I wanted to ask for a third opinion on the code I wrote.
 
Would you put this thing online, or would you not ?
Does it lack a feature that would lead to my site being inaccessible to others ?
And most importantly, anybody spots a security bug ?
 
 
Programming language: C#
Required .NET Framwork version: 4.0
Required mono-version: 2.10.2
Operating system: Windows + Linux (+works everywhere where there is mono 2.10.2 and a libc.so in path + firebird server installed)
Database: MS-SQL + FireBird, very easily extensible, creates database + tables automagically. 
 
Database configuration resides yet in 
EasyDNS\EasyDNS\DAL\cDatabaseConfiguration.cs
 
I still have to add the ability to use a XML configuration file.
At the moment, the configuration compiled into it is:
 
```

Database: FireBird (2.5)
server: localhost
port: 3050
user: sysdba
password: masterkey

```
 
**(Don't worry, I changed the default password on my server)**

---

### Post by v8YKxgHe on 2011-06-25
I don't have any feedback on your actual code & program per se, however:

> 1. bind9 requires recompilation for use with MySQL and PostGre SQL. This means that I won't be having security updates.
Nor will your own custom program. Subscribing to their mailing list is a hell of a lot easier than doing what you're doing.

Also, have you looked at PowerDNS? It supports a multiple of backends, including MySQL, PostgreSQL, SQLite and many more. 

Tbh, running your own DNS server is not wise because you don't have any redundancy. What happens if your own server goes down? Where do you host your website? I run with Linode, which apart from offering a great VPS service, also offers me 5 DNS servers in 5 different locations at no extra cost.

I don't mean for this to be a negative post, just making sure you're aware of what you're letting your self into.

---

### Post by WitchCraft on 2011-06-25
> **AlexC_ said:**
> 
I don't have any feedback on your actual code & program per se, however:
 
 
Nor will your own custom program. 
Subscribing to their mailing list is a hell of a lot easier than doing what you're doing.

I just proved that writing my own DNS server was faster than figuring out how to configure bind9.
 
 
> **AlexC_ said:**
> 
Also, have you looked at PowerDNS? It supports a multiple of backends, including MySQL, PostgreSQL, SQLite and many more. 

 
The documentation is unusable!
I have to search with google to find something useful ! Again ?
And then they document v3, but have thus far only releases 2.92 ?
And Firebird is not among the backends.
The server is multithreaded, supports SQlite, only that SQlite isn't threadsafe...
It's a major DNS server, and doesn't yet support dns-sec ?
 
The admin tool requires PHP ? 
> 
apt-get install apache2 libapache2-mod-php5 php5 php5-common php5-curl php5-dev php5-gd php-pear php5-imap php5-mcrypt php5-mhash php5-ming php5-mysql php5-xmlrpc gettext 

...
Pear & RPC & IMAP & Curl too ? 
Not to mention PHP for the administration of a DNS-server ?
WTF, made by a madman or what? ... 
 
OK, burry last one, it also has a Java tool, but that's what happens when you have to look somewhere else...
 
Then, I have to google to find out the DB schema ?
[http://www.howtoforge.com/installing-powerdns-with-mysql-backend-and-poweradmin-on-ubuntu-8.10](http://www.howtoforge.com/installing-powerdns-with-mysql-backend-and-poweradmin-on-ubuntu-8.10)
 
OMG, now I've again waisted already 10 minutes.
 
Products - what is that supposed to mean ?
 
And I have to subscribe to the mailing list to find out how to finally configure this thing or what ? 
Resulting in my set-up-for-spam mail account, which already almost exceeds it's quota, finally exceeding it ?
This is even worse than bind9...
 
So far my first impression of it, and that's also gonna be my last one.
 
> **AlexC_ said:**
> 
I run with Linode, which apart from offering a great VPS service, also offers me 5 DNS servers in 5 different locations at no extra cost.

20 $ a month the cheapest solution ? That's 240$ a year.
Hell, I can buy my own server, at only 200$, get 4 GB of RAM, 500 GB diskspace, nobody that can take a look in my data, and it's still cheaper than that.
And I also won't have any serverfarms and cloud problems, such as disappearing sessions.
 
 
> **AlexC_ said:**
> 
Tbh, running your own DNS server is not wise because you don't have any redundancy. What happens if your own server goes down? Where do you host your website? 
I don't mean for this to be a negative post, just making sure you're aware of what you're letting your self into.
 
It's simple: 
My website runs on my own server. 
So whether the reason is hardware failure or DOS attack, if the DNS server is down, it means the website is down as well.
Because if the dns server crashes or zombies, or uses unusually much memory, it's killed and restarted.

---

### Post by SeijiSensei on 2011-06-25
If you're going to build your own DNS server, you need to make sure you've read all the relevant RFCs concerning the Domain Name Service. [Here's a good starting point]("http://www.bind9.net/rfc").

Remember that even if you have one DNS server, you still need a second backup server to conform to the requirements of [RFC 2182]("http://tools.ietf.org/html/rfc2182").

---

### Post by v8YKxgHe on 2011-06-25
removed

---

### Post by WitchCraft on 2011-06-25
> **AlexC_ said:**
> 
Then either your DNS server is lacking regarding standards, or you're incredibly slow are reading man pages :P
 
There's another possibility:
I just used an existing DNS protocol library, and basically wrote the database backend.
For MS-SQL and Firebird. That's possible in 3 to 4 hours...
 
Plus the only man pages I usually read are the manpages for C and C++ stdlib functions, because most other manpages are not worth the effort.
A quick google search usually yields better documentation, not to mention that it's nicer to read something in the webbrowser than on gnome-terminal.
For some reason, this isn't the case for C/C++ functions.
 
> **AlexC_ said:**
>  
You're right, having to Google to find out something is just unheard of these days...
 
 
The documentation is clear and is all relevant to the latest versions.
 
 
Ok, your reading of man pages & documentation is lacking and is probably the result of all this. PowerDNS supports OpenDBX which in turn supports Firebird...
 
 
 
See, that's exactly what I mean by bad documentation.
I've now looked at this for 15 minutes (www & doc [.powerdns.com/]("http://doc.powerdns.com/")), and I never came across any mentioning of OpenDBX, and even if OpenDBX supports 
Firebird, I wouldn't have know that, I would have assumed OpenDBX is some esotheric database engine or standard, and wouldn't even have looked it up on wikipedia. 
 
Extremely unstructured, less diplomatic said one ugly giant hell of a chaos.
It cannot be that I have to read 1'000 pages of documentation just to find the relevant half a page information that I actually need.
 
So far the only things I know for certain is that it supports MySQL (and how to configure it), and that there are schemas findable via google (to whatever version of the software they belong) for Oracle and PostGre, actually on their doc website, but you wouldn't even find that without google.
 
Furthermore, even when OpenDBX supports Firebird, one still does need the DB schema for Firebird. 
Of course I can do that myself, but WTF ? 
Isn't that just what I did by writing my own server ?
Well, actually I'd guess that my abstraction layer is better.
And BTW, I haven't yet installed it, so I have NO man page.
And the man page also never turned up in a google search.
 
Of course, if you now go and search man PowerDNS, or more acurately man ...pdns_server...
It actually turns out the only content worth mentioning is: pdns_control - The PowerDNS nameserver 
 
 
> **AlexC_ said:**
> 
Yes it is, [http://www.sqlite.org/faq.html#q6](http://www.sqlite.org/faq.html#q6)
 
No it isn't.
[http://stackoverflow.com/questions/355327/does-thread-safety-of-sqlite3-mean-different-threads-can-modify-the-same-table-of](http://stackoverflow.com/questions/355327/does-thread-safety-of-sqlite3-mean-different-threads-can-modify-the-same-table-of)
It just locks and blocks, that's not real multithreading.
But I guess it's a question of how you define thread-safe.
To me, for a database, that means allowing multiple concurrent write access.
Which obviously is very difficult to achive.
In an internet environment, you have asynchronous ajax lookups and writes, which unfortunately have a timeout. 
Same thing goes for DNS lookups.
Of course, you can now argue that one can just switch the timeout higher, which is true, but that means it becomes virtually unusable if there is a bit more traffic. 
 
Which means it near-deadlocks the webserver or the dns-server threads.
Which means it's not really thread-safe. 
Although the implementation for itselfs may be thread-safe.
But you never have the implementation for itselfs, as in a unit test.
You always have the implementation in the environment, which is a very different thing.
 
 
> **AlexC_ said:**
>  
A quick Google suggests that it does have this feature, potentially in the form of PowerDNSSEC.
 
And my look at their website suggested it's part of the UPCOMING v3.0 release, and the only release available as .deb so far is 2.92 or whatever it was. 
 
 
> **AlexC_ said:**
>  
No, you administer it in what ever way you want. Including your own interface if you want to write one. And of course, PHP is obviously inherently insecure ... get over your self :) Crappy developers write crappy code in any language. PHP done correctly is fine.
 
True. But one wouldn't need to put the admin tool at the very bottom of the page.
And a quick screenshot wouldn't have hurt either, so one could see whether it was worth the effort of downloading it. 
However, last thing is a shortcoming of the admin tool guy.
Since that is a pretty elementary shortcoming, it pretty much tells us everything we need to know about that admin tool...
 
 
> **AlexC_ said:**
>  
Or you could just go to their website, view documentation, search in your browser for MySQL and oh my god, an example MySQL schema! The horror! [http://doc.powerdns.com/configuring-db-connection.html#configuring-mysql](http://doc.powerdns.com/configuring-db-connection.html#configuring-mysql)
 
The only way to find anything in their documentation quickly is doing a custom search on google, limiting by site:doc.powerdns.com - myself ... 
 
 
> **AlexC_ said:**
>  
This is full of so many things I can nit-pick at due to the incorrectness of it all, that I just wont bother.
 
Either way, if you want people to critic your code the best thing to actually to do is link them to your code.
 
 
OMG, I was so enraged, I completely forgot to upload it.
See attachment.

---

### Post by WitchCraft on 2011-06-25
Oh, and you'll also need this attachment below.

It contains the actual implementation of the DNS protocol & server itselfs.

Originally, it's from 
[http://arsofttoolsnet.codeplex.com/](http://arsofttoolsnet.codeplex.com/)

But since the mono UPD implementation is not thread safe, although it claims it is (with unit tests), just like SQlite, it actually is not.

So below my modified version of it, in order to circumvent the bugs in the mono UPD implementation, in order to actually, and not just theorethically, make it work on Linux.

---

### Post by slavik on 2011-06-26
you can't figure out how to configure bind9?! really?

[http://www.youtube.com/watch?v=h-XgvHPt1cg](http://www.youtube.com/watch?v=h-XgvHPt1cg)

---

### Post by v8YKxgHe on 2011-06-26
removed

---

### Post by WitchCraft on 2011-06-26
> **AlexC_ said:**
> 
Or by going to doc.powerdns.com and using your browsers search feature. 

If you do this, you will realize it's to no avail since they have splitted all the sites up. Browser search won't get you anywhere.
 
> 
Seriously, get over your self and put your ego away. Don't expect things to be given to you without reading and at least having the decency to RTFM. It takes a very short amount of time (read, not 15 minutes) to find everything you needed to know.

Normally, you'd be finished in 15 minutes, since all you need to do is:
1. Read the quickstart section
2. Downloading and install the executable, preferably with apt-get
3. Change a few config files
4. Login to the database
5. Create the database
6. Adapt and run the schema-create scripts
7. Generate an asymmetric key
8. Start the service/daemon. 

A good program prompts you for 4 and 5, then does 4, 5 and 6 automagically, or has a postinstallation script.

But with that kind of chaos, it takes you at least 4 times as long - unnecessarely one might add.
Not to mention that afterwards, you still have to setup the administration tool, whatever one chooses to use.
Having a unit-test to make sure that everything is fine wouldn't be a luxury either.

---

### Post by WitchCraft on 2011-06-26
> **slavik said:**
> you can't figure out how to configure bind9?! really?

[http://www.youtube.com/watch?v=h-XgvHPt1cg](http://www.youtube.com/watch?v=h-XgvHPt1cg)

Hahaha. Nice video.

Bind works out of the box, that's not the problem.
Configuring the recompiled version of bind to work with pgsql, that's the problem. 
It seems that the compiled version in the repository is not quite the same as the one that is in the src repository.

You better change your attitude right now.
Because as I read more and more threads on how to configure bind with a database, I find plenty of people who complain about it, having wasted hours for what should have taken minutes.

It's now 18:10, and I'll now try to finish getting bind9 to work.
I'll let you know WHEN I am finished.

And in the mean time, I suggest you do something productive, like actually criticing my code, as it was the original purpose of this thread.

Or posting a working bind config file for pgsql.
Since you both say it's that simple, I challenge the both of you to put your 'money' where your mouth is.

---

### Post by v8YKxgHe on 2011-06-26
removed

---

### Post by Dangertux on 2011-06-26
I might be wrong but I am assuming this is what you are trying to do.  

[http://bind-dlz.sourceforge.net/postgresql_driver.html](http://bind-dlz.sourceforge.net/postgresql_driver.html)

---

### Post by WitchCraft on 2011-06-26
> **Dangertux said:**
> I might be wrong but I am assuming this is what you are trying to do.  

[http://bind-dlz.sourceforge.net/postgresql_driver.html](http://bind-dlz.sourceforge.net/postgresql_driver.html)
Yes, this is what I try to do.

It's now 19:26, and I give up.

Here's what I did so far:


First, find the db-schema.

Found this tutorial, but it's for MySQL.
[http://diaryproducts.net/about/operating_systems/unix/installing_bind9_with_dlz_and_mysql_backend_on_ubuntu_jaunty_9_04](http://diaryproducts.net/about/operating_systems/unix/installing_bind9_with_dlz_and_mysql_backend_on_ubuntu_jaunty_9_04)

Looking for the PG schema, I found this here, where there are actual table create scripts, as opposed to the schema definition on the dlz.
[http://narthollis.net/blog/2010/06/Bind9_DLZ_-_PostgreSQL_style/](http://narthollis.net/blog/2010/06/Bind9_DLZ_-_PostgreSQL_style/)


Created the table on the postgre db.

Then first apt-get install bind9
then apt-get remove bind9

for that you have the bind9 config and startup file...
Then recompile bind9 with support for pg and mysql.

Afterwards add
```

dlz "Postgres Zone" {
       database "postgres 2
       {host=127.0.0.1 port=5432 dbname=bind user=postgres}
       {SELECT zone FROM dns_record WHERE zone = '%zone%'}
       {SELECT ttl, type, mx_priority, case when lower(type)='txt' then '\"' || data || '\"' else data end AS data FROM dns_record WHERE zone = '%zone%' AND host = '%record%' AND type <> 'SOA' AND type <> 'NS'}
       {SELECT ttl, type, data, resp_contact, serial, refresh, retry, expire, minimum FROM dns_record WHERE zone = '%zone%' AND (type = 'SOA' OR type='NS')}
       {SELECT ttl, type, host, mx_priority, case when lower(type)='txt' then '\"' || data || '\"' else data end AS data, resp_contact, serial, refresh, retry, expire, minimum FROM dns_record WHERE zone = '%zone%' AND type <> 'SOA' AND type <> 'NS'}
       {SELECT zone FROM dns_xfr where zone='%zone%' AND client = '%client%'}";
};

```
to named.conf

So now run /etc/init.d/bind9 restart and you'll get:
> 
rndc: neither /etc/bind/rndc.conf nor /etc/bind/rndc.key was found

server start failed


So... what is rndc ?
Answer: the administration tool
[http://www.centos.org/docs/5/html/Deployment_Guide-en-US/s1-bind-rndc.html](http://www.centos.org/docs/5/html/Deployment_Guide-en-US/s1-bind-rndc.html)

Why does the server not start because of this ?
Unknown.


OK, obviously we need a rndc.key file.
So we need to get one.

Google leads to this one:
[http://linuxzoo.net/page/tut_named.html](http://linuxzoo.net/page/tut_named.html)
```

rndc-confgen -a -b 512  -r keyboard

```
which falsely claims it does the configuration for you.
It actually only creates a rndc.key in /etc/
You still have to copy it manually to /etc/bind9


Then read 
[http://www.centos.org/docs/5/html/5.2/Deployment_Guide/s2-bind-rndc-configuration-rndcconf.html](http://www.centos.org/docs/5/html/5.2/Deployment_Guide/s2-bind-rndc-configuration-rndcconf.html)
to get a bit more information


Or you can just generate the key manually, according to 
[http://codesnippets.joyent.com/posts/show/1064](http://codesnippets.joyent.com/posts/show/1064)
you can run
```

dnssec-keygen -a hmac-md5 -b 256 -n HOST mybrandnewkey

```
Read the man page of dnssec-keygen
And then just don't try to replace hmac-md5 with DH and 256 with 4096. It won't work.
It will run forever, and never generate a key.
Just use the the entire verbatim command from that website:
```

dnssec-keygen -a hmac-md5 -b 256 -n HOST mybrandnewkey

```

Try /etc/init.d/bind9 restart, it still fails with the same msg.

Read:
[http://www.centos.org/docs/5/html/5.2/Deployment_Guide/s2-bind-rndc-configuration-rndcconf.html](http://www.centos.org/docs/5/html/5.2/Deployment_Guide/s2-bind-rndc-configuration-rndcconf.html)

And find out you actually have to have a bit more in named.conf

This is unusable, so searching for a example via google yields
[http://ubuntuforums.org/showthread.php?t=281393](http://ubuntuforums.org/showthread.php?t=281393)
and this one
[http://linux-sxs.org/internet_serving/bind9.html](http://linux-sxs.org/internet_serving/bind9.html)

For what it actually means, refer to:
[http://www.centos.org/docs/5/html/Deployment_Guide-en-US/s1-bind-namedconf.html](http://www.centos.org/docs/5/html/Deployment_Guide-en-US/s1-bind-namedconf.html)



Now I have this named.conf
```

// This is the primary configuration file for the BIND DNS server named.
//
// Please read /usr/share/doc/bind9/README.Debian.gz for information on the 
// structure of BIND configuration files in Debian, *BEFORE* you customize 
// this configuration file.
//
// If you are just adding zones, please do that in /etc/bind/named.conf.local

include "/etc/bind/named.conf.options";
include "/etc/bind/named.conf.local";
include "/etc/bind/named.conf.default-zones";


key "rndc-key" {
            // how was key encoded
            algorithm hmac-md5;
            // what is the pass-phrase for the key
            secret "TcZMT2dK8Vgz1+do+TC4PA47QZcFvaIor6kc+z97SASiH2l9NQMzsIPxCE+VlQ1LHvJpis0Ut4yDCQh+KKaIrQ==" ;
             };


options {
default-key "rndc-key";
default-server 127.0.0.1;
default-port 953;
};

controls {
inet * port 953 allow { any; } keys { "rndc-key"; };
};


dlz "Postgres Zone" {
       database "postgres 2
       {host=127.0.0.1 port=5432 dbname=bind user=postgres}
       {SELECT zone FROM dns_record WHERE zone = '%zone%'}
       {SELECT ttl, type, mx_priority, case when lower(type)='txt' then '\"' || data || '\"' else data end AS data FROM dns_record WHERE zone = '%zone%' AND host = '%record%' AND type <> 'SOA' AND type <> 'NS'}
       {SELECT ttl, type, data, resp_contact, serial, refresh, retry, expire, minimum FROM dns_record WHERE zone = '%zone%' AND (type = 'SOA' OR type='NS')}
       {SELECT ttl, type, host, mx_priority, case when lower(type)='txt' then '\"' || data || '\"' else data end AS data, resp_contact, serial, refresh, retry, expire, minimum FROM dns_record WHERE zone = '%zone%' AND type <> 'SOA' AND type <> 'NS'}
       {SELECT zone FROM dns_xfr where zone='%zone%' AND client = '%client%'}";
};

```



and this rndc.key
```

key "rndc-key" {
	algorithm hmac-md5;
	secret "TcZMT2dK8Vgz1+do+TC4PA47QZcFvaIor6kc+z97SASiH2l9NQMzsIPxCE+VlQ1LHvJpis0Ut4yDCQh+KKaIrQ==";
};

```


now i do
```

/etc/init.d/bind9 restart

```

And all I get is
> 
 * Stopping domain name service... bind9                                        rndc: connect failed: 127.0.0.1#953: connection refused
                                                                         [ OK ]
 * Starting domain name service... bind9                                 [fail] 


Programming my own server, didn't I read the DNS port was 53 ?
So changing ports in named.conf to 53 instead of 953, and I still get the same message.

Changing back to 953
and adding a 
```

server localhost {
key "rndc-key";
};

```
to my named.conf

Searching google for the error message, i get 
 8,540 results
and no solution.

I'm now fed up, I'm going to run my own server.
And if it doesn't work for some people, they can send their complaints to me@/dev/null or the bind9 mailing list. 
I for sure won't be subscribing there.

Since setting up bind9 is easy, at least according to slavik, if you can point out what I did wrong, it would be very much appreciated.

As far as I can tell, it's gonna be easier to finish implementing dnssec in this library than to get a bind9 dlz configuration up and running.

---

### Post by WitchCraft on 2011-06-26
Hmm, now I gave it a last try and see there, i got a bit further:

In a last desperate attempt to find out what the problem is, i found this:
[http://www.computerhope.com/forum/index.php?topic=82446.0](http://www.computerhope.com/forum/index.php?topic=82446.0)

Whose only worth mentioning part is that statement below, which tells us to let the bind9 executable, called "named", run in debug mode:
```

named -d 9 -g 

```

Which, when default error handling is so bad, would be the first thing I would mention in any documentation.

It turns out while the config file for the bind from the compiled repository is in /etc/bind/named.conf,
the config file for the bind from source (apt-get source bind9 !!!) is actually located at:
```

/etc/named.conf 

```
...

So it can't find the config file and terminates, WITHOUT AN ERROR MESSAGE, or rather with the 'incorrect' one from the previous post, which would have seemed to be a result of a different port or a firewall or a wrong IP or key.

Grrrrrrrrrrrrrrrrrrrrrrrrrrrrrr
Somebody lend me some ammo for my gun.

I've now copied named.conf to /etc/

and now this happens:

> 
root@IS1300-1:/etc# named -d 9 -g
26-Jun-2011 22:21:17.409 starting BIND 9.7.1-P2 -d 9 -g
26-Jun-2011 22:21:17.409 built with '--with-dlz-mysql=yes' '--with-dlz-postgres=yes'
26-Jun-2011 22:21:17.409 using up to 4096 sockets
26-Jun-2011 22:21:17.409 Registering DLZ postgres driver.
26-Jun-2011 22:21:17.409 Registering SDLZ driver 'postgres'
26-Jun-2011 22:21:17.409 Registering DLZ driver 'postgres'
26-Jun-2011 22:21:17.409 Registering DLZ mysql driver.
26-Jun-2011 22:21:17.409 Registering SDLZ driver 'mysql'
26-Jun-2011 22:21:17.409 Registering DLZ driver 'mysql'
26-Jun-2011 22:21:17.420 loading configuration from '/etc/named.conf'
26-Jun-2011 22:21:17.420 reading built-in trusted keys from file '/etc/bind.keys'
26-Jun-2011 22:21:17.420 set maximum stack size to 4294967295: success
26-Jun-2011 22:21:17.420 set maximum data size to 4294967295: success
26-Jun-2011 22:21:17.420 set maximum core size to 4294967295: success
26-Jun-2011 22:21:17.420 set maximum open files to 18446744073709551615: success
26-Jun-2011 22:21:17.421 using default UDP/IPv4 port range: [1024, 65535]
26-Jun-2011 22:21:17.421 using default UDP/IPv6 port range: [1024, 65535]
26-Jun-2011 22:21:17.424 listening on IPv6 interfaces, port 53
26-Jun-2011 22:21:17.424 clientmgr @0xb77a2428: create
26-Jun-2011 22:21:17.424 clientmgr @0xb77a2428: createclients
26-Jun-2011 22:21:17.424 clientmgr @0xb77a2428: create new
26-Jun-2011 22:21:17.424 client @0xb77d0008: create
26-Jun-2011 22:21:17.424 clientmgr @0xb77a2428: createclients
26-Jun-2011 22:21:17.424 clientmgr @0xb77a2428: create new
26-Jun-2011 22:21:17.424 client @0xb77d03e0: create
26-Jun-2011 22:21:17.425 listening on IPv4 interface lo, 127.0.0.1#53
26-Jun-2011 22:21:17.425 clientmgr @0xb77a2398: create
26-Jun-2011 22:21:17.425 clientmgr @0xb77a2398: createclients
26-Jun-2011 22:21:17.425 clientmgr @0xb77a2398: create new
26-Jun-2011 22:21:17.425 client @0xb77d07b8: create
26-Jun-2011 22:21:17.425 clientmgr @0xb77a2398: createclients
26-Jun-2011 22:21:17.425 clientmgr @0xb77a2398: create new
26-Jun-2011 22:21:17.425 client @0xb77d0b90: create
26-Jun-2011 22:21:17.425 listening on IPv4 interface wlan0, 192.168.1.8#53
26-Jun-2011 22:21:17.425 clientmgr @0xb77a25a8: create
26-Jun-2011 22:21:17.425 clientmgr @0xb77a25a8: createclients
26-Jun-2011 22:21:17.425 clientmgr @0xb77a25a8: create new
26-Jun-2011 22:21:17.425 client @0xb77d5008: create
26-Jun-2011 22:21:17.425 clientmgr @0xb77a25a8: createclients
26-Jun-2011 22:21:17.425 clientmgr @0xb77a25a8: create new
26-Jun-2011 22:21:17.425 client @0xb77d53e0: create
26-Jun-2011 22:21:17.425 generating session key for dynamic DNS
26-Jun-2011 22:21:17.427 Loading 'Postgres Zone' using driver postgres
26-Jun-2011 22:21:17.427 Loading SDLZ driver.
26-Jun-2011 22:21:17.427 Postgres driver running single threaded
26-Jun-2011 22:21:17.427 Required token $zone$ not found.
26-Jun-2011 22:21:17.427 Could not build all nodes query list
26-Jun-2011 22:21:17.427 Postgres driver could not create database instance object.
26-Jun-2011 22:21:17.427 SDLZ driver failed to load.
26-Jun-2011 22:21:17.427 DLZ driver failed to load.
26-Jun-2011 22:21:17.427 load_configuration: failure
26-Jun-2011 22:21:17.427 loading configuration: failure
26-Jun-2011 22:21:17.427 exiting (due to fatal error)


Notice this:
> 
Required token $zone$ not found.


But I think I know what this is:

While searching for previous information, I found somebody complaining that someone changed %zone% to $zone$ and did not update the documentation, and that it cost him hours to find that out.

Well, some more ammo for my gun please.


Oh wait, that ain't all, it's still not running... Now I get this:
> 

root@IS1300-1:/etc# named -d 9 -g
26-Jun-2011 22:54:28.872 starting BIND 9.7.1-P2 -d 9 -g
26-Jun-2011 22:54:28.872 built with '--with-dlz-mysql=yes' '--with-dlz-postgres=yes'
26-Jun-2011 22:54:28.872 using up to 4096 sockets
26-Jun-2011 22:54:28.872 Registering DLZ postgres driver.
26-Jun-2011 22:54:28.872 Registering SDLZ driver 'postgres'
26-Jun-2011 22:54:28.872 Registering DLZ driver 'postgres'
26-Jun-2011 22:54:28.872 Registering DLZ mysql driver.
26-Jun-2011 22:54:28.872 Registering SDLZ driver 'mysql'
26-Jun-2011 22:54:28.872 Registering DLZ driver 'mysql'
26-Jun-2011 22:54:28.879 loading configuration from '/etc/named.conf'
26-Jun-2011 22:54:28.880 reading built-in trusted keys from file '/etc/bind.keys'
26-Jun-2011 22:54:28.880 set maximum stack size to 4294967295: success
26-Jun-2011 22:54:28.880 set maximum data size to 4294967295: success
26-Jun-2011 22:54:28.880 set maximum core size to 4294967295: success
26-Jun-2011 22:54:28.880 set maximum open files to 18446744073709551615: success
26-Jun-2011 22:54:28.880 using default UDP/IPv4 port range: [1024, 65535]
26-Jun-2011 22:54:28.881 using default UDP/IPv6 port range: [1024, 65535]
26-Jun-2011 22:54:28.885 listening on IPv6 interfaces, port 53
26-Jun-2011 22:54:28.885 clientmgr @0xb7817428: create
26-Jun-2011 22:54:28.885 clientmgr @0xb7817428: createclients
26-Jun-2011 22:54:28.885 clientmgr @0xb7817428: create new
26-Jun-2011 22:54:28.885 client @0xb7845008: create
26-Jun-2011 22:54:28.885 clientmgr @0xb7817428: createclients
26-Jun-2011 22:54:28.885 clientmgr @0xb7817428: create new
26-Jun-2011 22:54:28.885 client @0xb78453e0: create
26-Jun-2011 22:54:28.885 listening on IPv4 interface lo, 127.0.0.1#53
26-Jun-2011 22:54:28.885 clientmgr @0xb7817398: create
26-Jun-2011 22:54:28.885 clientmgr @0xb7817398: createclients
26-Jun-2011 22:54:28.885 clientmgr @0xb7817398: create new
26-Jun-2011 22:54:28.885 client @0xb78457b8: create
26-Jun-2011 22:54:28.885 clientmgr @0xb7817398: createclients
26-Jun-2011 22:54:28.885 clientmgr @0xb7817398: create new
26-Jun-2011 22:54:28.885 client @0xb7845b90: create
26-Jun-2011 22:54:28.885 listening on IPv4 interface wlan0, 192.168.1.8#53
26-Jun-2011 22:54:28.886 clientmgr @0xb78175a8: create
26-Jun-2011 22:54:28.886 clientmgr @0xb78175a8: createclients
26-Jun-2011 22:54:28.886 clientmgr @0xb78175a8: create new
26-Jun-2011 22:54:28.886 client @0xb784a008: create
26-Jun-2011 22:54:28.886 clientmgr @0xb78175a8: createclients
26-Jun-2011 22:54:28.886 clientmgr @0xb78175a8: create new
26-Jun-2011 22:54:28.886 client @0xb784a3e0: create
26-Jun-2011 22:54:28.886 generating session key for dynamic DNS
26-Jun-2011 22:54:28.887 Loading 'Postgres Zone' using driver postgres
26-Jun-2011 22:54:28.887 Loading SDLZ driver.
26-Jun-2011 22:54:28.887 Postgres driver running single threaded
26-Jun-2011 22:54:28.887 Postgres driver created database instance object.
26-Jun-2011 22:54:28.965 Postgres driver failed to create database connection after 4 attempts
26-Jun-2011 22:54:28.965 SDLZ driver failed to load.
26-Jun-2011 22:54:28.965 DLZ driver failed to load.
26-Jun-2011 22:54:28.966 load_configuration: failure
26-Jun-2011 22:54:28.966 loading configuration: failure
26-Jun-2011 22:54:28.966 exiting (due to fatal error)


Now the guessing game begins again.

I suppose this line
> 
26-Jun-2011 22:54:28.965 Postgres driver failed to create database connection after 4 attempts

is an attempt to tell me that the password for the postgre user has not yet been specified anywhere.
Which is another thing I found odd.


It doesn't say where to put the password, but actually, when you take a closer look at
```

{host=127.0.0.1 port=5432 dbname=bind user=YOUR_DB_USER 

```

, you realize this is a connection string.
The only problem seems to be that the parameters are not called with the standard names they should be called.

A correct postgre connection string looks like THIS, and the parameters are called like THIS, and NOT something else...
```

User ID=root;Password=myPassword;Host=localhost;Port=5432;Database=myDataBase; Pooling=true;Min Pool Size=0;Max Pool Size=100;Connection Lifetime=0;

```

But I guess this is what's necessary when somebody is too stupid to parse tokens when not every parameter is separated by a whitespace from the next one...
But who cares, it's not too difficult to guess (and hope) that the password parameter is called password in this case.

So replacing the second to last statement with this one:
```

{host=127.0.0.1 port=5432 dbname=bind user=YOUR_DB_USER password=YOUR_SQL_USER_PASSWORD}

```
and it starts to work.


YES, that's true, it's finally up and running, I hope fine.
Finished at 23:14:43

23:14 - 18:10 = 5h 4 min

+ 3 h from before yesterday

Sums up to 8h 4 min to get bind9 working.
Ridiculous. 
And all because of the *ing config file.
And even that could only happen because the documentation is f*ed up.
Else, it would take less than 15 minutes.
Well, that is, supposed one wouldn't need to recompile bind9 because the Ubuntu team has ingeniously put the executable with disabled SQL drivers into the repositories.
That's certainly good for security - I mean when all those servers running SQL databases (=those who really serve a hughe amount of data, the important ones) need to patch all security holes themselves.
After all, what's writing to files on the filesystem for a security risk when compared to connecting to a database that actually is designed to do these things in a multithreading environment, and whose bugs and security holes have been fixed over and over again, resulting in something pretty solid...
A "coup de main" of Ubuntu engineering, so to say.


Look at it, doesn't this look nice:
> 

root@IS1300-1:/etc# named -d 9 -g
26-Jun-2011 23:19:58.234 starting BIND 9.7.1-P2 -d 9 -g
26-Jun-2011 23:19:58.234 built with '--with-dlz-mysql=yes' '--with-dlz-postgres=yes'
26-Jun-2011 23:19:58.234 using up to 4096 sockets
26-Jun-2011 23:19:58.234 Registering DLZ postgres driver.
26-Jun-2011 23:19:58.234 Registering SDLZ driver 'postgres'
26-Jun-2011 23:19:58.234 Registering DLZ driver 'postgres'
26-Jun-2011 23:19:58.234 Registering DLZ mysql driver.
26-Jun-2011 23:19:58.234 Registering SDLZ driver 'mysql'
26-Jun-2011 23:19:58.234 Registering DLZ driver 'mysql'
26-Jun-2011 23:19:58.244 loading configuration from '/etc/named.conf'
26-Jun-2011 23:19:58.245 reading built-in trusted keys from file '/etc/bind.keys'
26-Jun-2011 23:19:58.245 set maximum stack size to 4294967295: success
26-Jun-2011 23:19:58.245 set maximum data size to 4294967295: success
26-Jun-2011 23:19:58.245 set maximum core size to 4294967295: success
26-Jun-2011 23:19:58.245 set maximum open files to 18446744073709551615: success
26-Jun-2011 23:19:58.245 using default UDP/IPv4 port range: [1024, 65535]
26-Jun-2011 23:19:58.246 using default UDP/IPv6 port range: [1024, 65535]
26-Jun-2011 23:19:58.248 listening on IPv6 interfaces, port 53
26-Jun-2011 23:19:58.248 clientmgr @0xb779d428: create
26-Jun-2011 23:19:58.248 clientmgr @0xb779d428: createclients
26-Jun-2011 23:19:58.248 clientmgr @0xb779d428: create new
26-Jun-2011 23:19:58.249 client @0xb77cc008: create
26-Jun-2011 23:19:58.249 clientmgr @0xb779d428: createclients
26-Jun-2011 23:19:58.249 clientmgr @0xb779d428: create new
26-Jun-2011 23:19:58.249 client @0xb77cc3e0: create
26-Jun-2011 23:19:58.249 listening on IPv4 interface lo, 127.0.0.1#53
26-Jun-2011 23:19:58.249 clientmgr @0xb779d398: create
26-Jun-2011 23:19:58.249 clientmgr @0xb779d398: createclients
26-Jun-2011 23:19:58.249 clientmgr @0xb779d398: create new
26-Jun-2011 23:19:58.249 client @0xb77cc7b8: create
26-Jun-2011 23:19:58.249 clientmgr @0xb779d398: createclients
26-Jun-2011 23:19:58.249 clientmgr @0xb779d398: create new
26-Jun-2011 23:19:58.249 client @0xb77ccb90: create
26-Jun-2011 23:19:58.249 listening on IPv4 interface wlan0, 192.168.1.8#53
26-Jun-2011 23:19:58.249 clientmgr @0xb779d5a8: create
26-Jun-2011 23:19:58.249 clientmgr @0xb779d5a8: createclients
26-Jun-2011 23:19:58.249 clientmgr @0xb779d5a8: create new
26-Jun-2011 23:19:58.249 client @0xb77d1008: create
26-Jun-2011 23:19:58.249 clientmgr @0xb779d5a8: createclients
26-Jun-2011 23:19:58.249 clientmgr @0xb779d5a8: create new
26-Jun-2011 23:19:58.249 client @0xb77d13e0: create
26-Jun-2011 23:19:58.249 generating session key for dynamic DNS
26-Jun-2011 23:19:58.255 Loading 'Postgres Zone' using driver postgres
26-Jun-2011 23:19:58.255 Loading SDLZ driver.
26-Jun-2011 23:19:58.255 Postgres driver running single threaded
26-Jun-2011 23:19:58.255 Postgres driver created database instance object.
26-Jun-2011 23:19:58.326 SDLZ driver loaded successfully.
26-Jun-2011 23:19:58.326 DLZ driver loaded successfully.
26-Jun-2011 23:19:58.326 res 0xb77d9008: create
26-Jun-2011 23:19:58.327 dns_requestmgr_create
26-Jun-2011 23:19:58.327 dns_requestmgr_create: 0xb77db4e8
26-Jun-2011 23:19:58.327 dns_requestmgr_whenshutdown
26-Jun-2011 23:19:58.328 set up managed keys zone for view _default, file 'managed-keys.bind'
26-Jun-2011 23:19:58.328 automatic empty zone: 254.169.IN-ADDR.ARPA
26-Jun-2011 23:19:58.328 automatic empty zone: 2.0.192.IN-ADDR.ARPA
26-Jun-2011 23:19:58.328 automatic empty zone: 100.51.198.IN-ADDR.ARPA
26-Jun-2011 23:19:58.328 automatic empty zone: 113.0.203.IN-ADDR.ARPA
26-Jun-2011 23:19:58.328 automatic empty zone: 255.255.255.255.IN-ADDR.ARPA
26-Jun-2011 23:19:58.328 automatic empty zone: 0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA
26-Jun-2011 23:19:58.328 automatic empty zone: 1.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA
26-Jun-2011 23:19:58.328 automatic empty zone: D.F.IP6.ARPA
26-Jun-2011 23:19:58.328 automatic empty zone: 8.E.F.IP6.ARPA
26-Jun-2011 23:19:58.328 automatic empty zone: 9.E.F.IP6.ARPA
26-Jun-2011 23:19:58.328 automatic empty zone: A.E.F.IP6.ARPA
26-Jun-2011 23:19:58.328 automatic empty zone: B.E.F.IP6.ARPA
26-Jun-2011 23:19:58.328 automatic empty zone: 8.B.D.0.1.0.0.2.IP6.ARPA
26-Jun-2011 23:19:58.328 automatic empty zone: 0.1.1.0.0.2.IP6.ARPA
26-Jun-2011 23:19:58.330 res 0xb77d90b8: create
26-Jun-2011 23:19:58.331 dns_requestmgr_create
26-Jun-2011 23:19:58.331 dns_requestmgr_create: 0xb76e0308
26-Jun-2011 23:19:58.331 dns_requestmgr_whenshutdown
26-Jun-2011 23:19:58.331 none:0: open: /etc/rndc.key: file not found
26-Jun-2011 23:19:58.331 couldn't add command channel 127.0.0.1#953: file not found
26-Jun-2011 23:19:58.331 none:0: open: /etc/rndc.key: file not found
26-Jun-2011 23:19:58.331 couldn't add command channel ::1#953: file not found
26-Jun-2011 23:19:58.331 ignoring config file logging statement due to -g option
26-Jun-2011 23:19:58.331 load_configuration: success
26-Jun-2011 23:19:58.331 zone 0.in-addr.arpa/IN: starting load
26-Jun-2011 23:19:58.332 zone 0.in-addr.arpa/IN: number of nodes in database: 1
26-Jun-2011 23:19:58.332 no journal file, but that's OK
26-Jun-2011 23:19:58.332 zone 0.in-addr.arpa/IN: journal rollforward completed successfully: no journal
26-Jun-2011 23:19:58.332 zone 0.in-addr.arpa/IN: loaded
26-Jun-2011 23:19:58.332 zone_settimer: zone 0.in-addr.arpa/IN: enter
26-Jun-2011 23:19:58.332 zone 0.in-addr.arpa/IN: loaded serial 1
26-Jun-2011 23:19:58.332 zone 127.in-addr.arpa/IN: starting load
26-Jun-2011 23:19:58.333 zone 127.in-addr.arpa/IN: number of nodes in database: 2
26-Jun-2011 23:19:58.333 no journal file, but that's OK
26-Jun-2011 23:19:58.333 zone 127.in-addr.arpa/IN: journal rollforward completed successfully: no journal
26-Jun-2011 23:19:58.333 zone 127.in-addr.arpa/IN: loaded
26-Jun-2011 23:19:58.333 zone_settimer: zone 127.in-addr.arpa/IN: enter
26-Jun-2011 23:19:58.333 zone 127.in-addr.arpa/IN: loaded serial 1
26-Jun-2011 23:19:58.333 zone 254.169.IN-ADDR.ARPA/IN: starting load
26-Jun-2011 23:19:58.333 zone 254.169.IN-ADDR.ARPA/IN: number of nodes in database: 0
26-Jun-2011 23:19:58.333 zone 254.169.IN-ADDR.ARPA/IN: loaded
26-Jun-2011 23:19:58.333 zone_settimer: zone 254.169.IN-ADDR.ARPA/IN: enter
26-Jun-2011 23:19:58.333 zone 2.0.192.IN-ADDR.ARPA/IN: starting load
26-Jun-2011 23:19:58.333 zone 2.0.192.IN-ADDR.ARPA/IN: number of nodes in database: 0
26-Jun-2011 23:19:58.333 zone 2.0.192.IN-ADDR.ARPA/IN: loaded
26-Jun-2011 23:19:58.333 zone_settimer: zone 2.0.192.IN-ADDR.ARPA/IN: enter
26-Jun-2011 23:19:58.333 zone 100.51.198.IN-ADDR.ARPA/IN: starting load
26-Jun-2011 23:19:58.333 zone 100.51.198.IN-ADDR.ARPA/IN: number of nodes in database: 0
26-Jun-2011 23:19:58.333 zone 100.51.198.IN-ADDR.ARPA/IN: loaded
26-Jun-2011 23:19:58.333 zone_settimer: zone 100.51.198.IN-ADDR.ARPA/IN: enter
26-Jun-2011 23:19:58.333 zone 113.0.203.IN-ADDR.ARPA/IN: starting load
26-Jun-2011 23:19:58.333 zone 113.0.203.IN-ADDR.ARPA/IN: number of nodes in database: 0
26-Jun-2011 23:19:58.333 zone 113.0.203.IN-ADDR.ARPA/IN: loaded
26-Jun-2011 23:19:58.333 zone_settimer: zone 113.0.203.IN-ADDR.ARPA/IN: enter
26-Jun-2011 23:19:58.334 zone 255.in-addr.arpa/IN: starting load
26-Jun-2011 23:19:58.334 zone 255.in-addr.arpa/IN: number of nodes in database: 1
26-Jun-2011 23:19:58.334 no journal file, but that's OK
26-Jun-2011 23:19:58.334 zone 255.in-addr.arpa/IN: journal rollforward completed successfully: no journal
26-Jun-2011 23:19:58.334 zone 255.in-addr.arpa/IN: loaded
26-Jun-2011 23:19:58.334 zone_settimer: zone 255.in-addr.arpa/IN: enter
26-Jun-2011 23:19:58.334 zone 255.in-addr.arpa/IN: loaded serial 1
26-Jun-2011 23:19:58.334 zone 255.255.255.255.IN-ADDR.ARPA/IN: starting load
26-Jun-2011 23:19:58.334 zone 255.255.255.255.IN-ADDR.ARPA/IN: number of nodes in database: 0
26-Jun-2011 23:19:58.334 zone 255.255.255.255.IN-ADDR.ARPA/IN: loaded
26-Jun-2011 23:19:58.334 zone_settimer: zone 255.255.255.255.IN-ADDR.ARPA/IN: enter
26-Jun-2011 23:19:58.334 zone 0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA/IN: starting load
26-Jun-2011 23:19:58.334 zone 0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA/IN: number of nodes in database: 0
26-Jun-2011 23:19:58.334 zone 0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA/IN: loaded
26-Jun-2011 23:19:58.334 zone_settimer: zone 0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA/IN: enter
26-Jun-2011 23:19:58.334 zone 1.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA/IN: starting load
26-Jun-2011 23:19:58.334 zone 1.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA/IN: number of nodes in database: 0
26-Jun-2011 23:19:58.334 zone 1.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA/IN: loaded
26-Jun-2011 23:19:58.334 zone_settimer: zone 1.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA/IN: enter
26-Jun-2011 23:19:58.334 zone 8.B.D.0.1.0.0.2.IP6.ARPA/IN: starting load
26-Jun-2011 23:19:58.335 zone 8.B.D.0.1.0.0.2.IP6.ARPA/IN: number of nodes in database: 0
26-Jun-2011 23:19:58.335 zone 8.B.D.0.1.0.0.2.IP6.ARPA/IN: loaded
26-Jun-2011 23:19:58.335 zone_settimer: zone 8.B.D.0.1.0.0.2.IP6.ARPA/IN: enter
26-Jun-2011 23:19:58.335 zone 0.1.1.0.0.2.IP6.ARPA/IN: starting load
26-Jun-2011 23:19:58.335 zone 0.1.1.0.0.2.IP6.ARPA/IN: number of nodes in database: 0
26-Jun-2011 23:19:58.335 zone 0.1.1.0.0.2.IP6.ARPA/IN: loaded
26-Jun-2011 23:19:58.335 zone_settimer: zone 0.1.1.0.0.2.IP6.ARPA/IN: enter
26-Jun-2011 23:19:58.335 zone D.F.IP6.ARPA/IN: starting load
26-Jun-2011 23:19:58.335 zone D.F.IP6.ARPA/IN: number of nodes in database: 0
26-Jun-2011 23:19:58.335 zone D.F.IP6.ARPA/IN: loaded
26-Jun-2011 23:19:58.335 zone_settimer: zone D.F.IP6.ARPA/IN: enter
26-Jun-2011 23:19:58.335 zone 8.E.F.IP6.ARPA/IN: starting load
26-Jun-2011 23:19:58.335 zone 8.E.F.IP6.ARPA/IN: number of nodes in database: 0
26-Jun-2011 23:19:58.335 zone 8.E.F.IP6.ARPA/IN: loaded
26-Jun-2011 23:19:58.335 zone_settimer: zone 8.E.F.IP6.ARPA/IN: enter
26-Jun-2011 23:19:58.335 zone 9.E.F.IP6.ARPA/IN: starting load
26-Jun-2011 23:19:58.335 zone 9.E.F.IP6.ARPA/IN: number of nodes in database: 0
26-Jun-2011 23:19:58.335 zone 9.E.F.IP6.ARPA/IN: loaded
26-Jun-2011 23:19:58.335 zone_settimer: zone 9.E.F.IP6.ARPA/IN: enter
26-Jun-2011 23:19:58.335 zone A.E.F.IP6.ARPA/IN: starting load
26-Jun-2011 23:19:58.335 zone A.E.F.IP6.ARPA/IN: number of nodes in database: 0
26-Jun-2011 23:19:58.335 zone A.E.F.IP6.ARPA/IN: loaded
26-Jun-2011 23:19:58.335 zone_settimer: zone A.E.F.IP6.ARPA/IN: enter
26-Jun-2011 23:19:58.335 zone B.E.F.IP6.ARPA/IN: starting load
26-Jun-2011 23:19:58.335 zone B.E.F.IP6.ARPA/IN: number of nodes in database: 0
26-Jun-2011 23:19:58.335 zone B.E.F.IP6.ARPA/IN: loaded
26-Jun-2011 23:19:58.335 zone_settimer: zone B.E.F.IP6.ARPA/IN: enter
26-Jun-2011 23:19:58.336 zone localhost/IN: starting load
26-Jun-2011 23:19:58.336 zone localhost/IN: number of nodes in database: 1
26-Jun-2011 23:19:58.336 no journal file, but that's OK
26-Jun-2011 23:19:58.336 zone localhost/IN: journal rollforward completed successfully: no journal
26-Jun-2011 23:19:58.336 zone localhost/IN: loaded
26-Jun-2011 23:19:58.336 zone_settimer: zone localhost/IN: enter
26-Jun-2011 23:19:58.336 zone localhost/IN: loaded serial 2
26-Jun-2011 23:19:58.336 managed-keys-zone ./IN: starting load
26-Jun-2011 23:19:58.336 managed-keys-zone ./IN: loading from master file managed-keys.bind failed: file not found
26-Jun-2011 23:19:58.336 managed-keys-zone ./IN: number of nodes in database: 1
26-Jun-2011 23:19:58.336 managed-keys-zone ./IN: creating SOA
26-Jun-2011 23:19:58.336 no journal file, but that's OK
26-Jun-2011 23:19:58.336 managed-keys-zone ./IN: journal rollforward completed successfully: no journal
26-Jun-2011 23:19:58.336 managed-keys-zone ./IN: loaded
26-Jun-2011 23:19:58.336 managed-keys-zone ./IN: synchronizing trusted keys
26-Jun-2011 23:19:58.336 zone_settimer: managed-keys-zone ./IN: enter
26-Jun-2011 23:19:58.336 managed-keys-zone ./IN: loaded serial 0
26-Jun-2011 23:19:58.336 zone authors.bind/CH: starting load
26-Jun-2011 23:19:58.336 zone authors.bind/CH: number of nodes in database: 0
26-Jun-2011 23:19:58.336 zone authors.bind/CH: loaded
26-Jun-2011 23:19:58.336 zone_settimer: zone authors.bind/CH: enter
26-Jun-2011 23:19:58.336 zone hostname.bind/CH: starting load
26-Jun-2011 23:19:58.336 zone hostname.bind/CH: number of nodes in database: 0
26-Jun-2011 23:19:58.336 zone hostname.bind/CH: loaded
26-Jun-2011 23:19:58.336 zone_settimer: zone hostname.bind/CH: enter
26-Jun-2011 23:19:58.337 zone version.bind/CH: starting load
26-Jun-2011 23:19:58.337 zone version.bind/CH: number of nodes in database: 0
26-Jun-2011 23:19:58.337 zone version.bind/CH: loaded
26-Jun-2011 23:19:58.337 zone_settimer: zone version.bind/CH: enter
26-Jun-2011 23:19:58.337 zone id.server/CH: starting load
26-Jun-2011 23:19:58.337 zone id.server/CH: number of nodes in database: 0
26-Jun-2011 23:19:58.337 zone id.server/CH: loaded
26-Jun-2011 23:19:58.337 zone_settimer: zone id.server/CH: enter
26-Jun-2011 23:19:58.337 dns_zone_maintenance: zone localhost/IN: enter
26-Jun-2011 23:19:58.337 zone_settimer: zone localhost/IN: enter
26-Jun-2011 23:19:58.337 dns_zone_maintenance: zone 127.in-addr.arpa/IN: enter
26-Jun-2011 23:19:58.337 zone_settimer: zone 127.in-addr.arpa/IN: enter
26-Jun-2011 23:19:58.337 dns_zone_maintenance: zone 0.in-addr.arpa/IN: enter
26-Jun-2011 23:19:58.337 zone_settimer: zone 0.in-addr.arpa/IN: enter
26-Jun-2011 23:19:58.337 dns_zone_maintenance: zone 255.in-addr.arpa/IN: enter
26-Jun-2011 23:19:58.337 zone_settimer: zone 255.in-addr.arpa/IN: enter
26-Jun-2011 23:19:58.337 dns_zone_maintenance: managed-keys-zone ./IN: enter
26-Jun-2011 23:19:58.337 zone_settimer: managed-keys-zone ./IN: enter
26-Jun-2011 23:19:58.344 dns_zone_maintenance: zone 254.169.IN-ADDR.ARPA/IN: enter
26-Jun-2011 23:19:58.344 zone_settimer: zone 254.169.IN-ADDR.ARPA/IN: enter
26-Jun-2011 23:19:58.344 dns_zone_maintenance: zone 2.0.192.IN-ADDR.ARPA/IN: enter
26-Jun-2011 23:19:58.344 zone_settimer: zone 2.0.192.IN-ADDR.ARPA/IN: enter
26-Jun-2011 23:19:58.344 dns_zone_maintenance: zone 100.51.198.IN-ADDR.ARPA/IN: enter
26-Jun-2011 23:19:58.344 zone_settimer: zone 100.51.198.IN-ADDR.ARPA/IN: enter
26-Jun-2011 23:19:58.344 dns_zone_maintenance: zone 113.0.203.IN-ADDR.ARPA/IN: enter
26-Jun-2011 23:19:58.344 zone_settimer: zone 113.0.203.IN-ADDR.ARPA/IN: enter
26-Jun-2011 23:19:58.344 dns_zone_maintenance: zone 255.255.255.255.IN-ADDR.ARPA/IN: enter
26-Jun-2011 23:19:58.344 zone_settimer: zone 255.255.255.255.IN-ADDR.ARPA/IN: enter
26-Jun-2011 23:19:58.344 dns_zone_maintenance: zone 0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA/IN: enter
26-Jun-2011 23:19:58.344 zone_settimer: zone 0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA/IN: enter
26-Jun-2011 23:19:58.344 dns_zone_maintenance: zone 1.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA/IN: enter
26-Jun-2011 23:19:58.344 zone_settimer: zone 1.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA/IN: enter
26-Jun-2011 23:19:58.344 dns_zone_maintenance: zone D.F.IP6.ARPA/IN: enter
26-Jun-2011 23:19:58.344 zone_settimer: zone D.F.IP6.ARPA/IN: enter
26-Jun-2011 23:19:58.344 dns_zone_maintenance: zone 8.E.F.IP6.ARPA/IN: enter
26-Jun-2011 23:19:58.344 zone_settimer: zone 8.E.F.IP6.ARPA/IN: enter
26-Jun-2011 23:19:58.344 dns_zone_maintenance: zone 9.E.F.IP6.ARPA/IN: enter
26-Jun-2011 23:19:58.344 zone_settimer: zone 9.E.F.IP6.ARPA/IN: enter
26-Jun-2011 23:19:58.344 dns_zone_maintenance: zone A.E.F.IP6.ARPA/IN: enter
26-Jun-2011 23:19:58.344 zone_settimer: zone A.E.F.IP6.ARPA/IN: enter
26-Jun-2011 23:19:58.344 dns_zone_maintenance: zone B.E.F.IP6.ARPA/IN: enter
26-Jun-2011 23:19:58.344 zone_settimer: zone B.E.F.IP6.ARPA/IN: enter
26-Jun-2011 23:19:58.344 dns_zone_maintenance: zone 8.B.D.0.1.0.0.2.IP6.ARPA/IN: enter
26-Jun-2011 23:19:58.344 zone_settimer: zone 8.B.D.0.1.0.0.2.IP6.ARPA/IN: enter
26-Jun-2011 23:19:58.344 dns_zone_maintenance: zone 0.1.1.0.0.2.IP6.ARPA/IN: enter
26-Jun-2011 23:19:58.344 zone_settimer: zone 0.1.1.0.0.2.IP6.ARPA/IN: enter
26-Jun-2011 23:19:58.344 dns_zone_maintenance: zone version.bind/CH: enter
26-Jun-2011 23:19:58.344 zone_settimer: zone version.bind/CH: enter
26-Jun-2011 23:19:58.344 dns_zone_maintenance: zone hostname.bind/CH: enter
26-Jun-2011 23:19:58.344 zone_settimer: zone hostname.bind/CH: enter
26-Jun-2011 23:19:58.344 dns_zone_maintenance: zone authors.bind/CH: enter
26-Jun-2011 23:19:58.344 zone_settimer: zone authors.bind/CH: enter
26-Jun-2011 23:19:58.344 dns_zone_maintenance: zone id.server/CH: enter
26-Jun-2011 23:19:58.344 zone_settimer: zone id.server/CH: enter
26-Jun-2011 23:19:58.344 running
26-Jun-2011 23:19:58.344 client @0xb77cc008: udprecv
26-Jun-2011 23:19:58.344 client @0xb77cc3e0: accept
26-Jun-2011 23:19:58.345 client @0xb77cc7b8: udprecv
26-Jun-2011 23:19:58.345 client @0xb77ccb90: accept
26-Jun-2011 23:19:58.345 client @0xb77d1008: udprecv
26-Jun-2011 23:19:58.345 client @0xb77d13e0: accept
26-Jun-2011 23:19:58.345 zone_timer: zone localhost/IN: enter
26-Jun-2011 23:19:58.345 zone_maintenance: zone localhost/IN: enter
26-Jun-2011 23:19:58.345 zone_settimer: zone localhost/IN: enter
26-Jun-2011 23:19:58.345 zone_timer: zone 127.in-addr.arpa/IN: enter
26-Jun-2011 23:19:58.345 zone_maintenance: zone 127.in-addr.arpa/IN: enter
26-Jun-2011 23:19:58.345 zone_settimer: zone 127.in-addr.arpa/IN: enter
26-Jun-2011 23:19:58.345 zone_timer: zone 0.in-addr.arpa/IN: enter
26-Jun-2011 23:19:58.345 zone_maintenance: zone 0.in-addr.arpa/IN: enter
26-Jun-2011 23:19:58.345 zone_settimer: zone 0.in-addr.arpa/IN: enter
26-Jun-2011 23:19:58.345 zone_timer: zone 254.169.IN-ADDR.ARPA/IN: enter
26-Jun-2011 23:19:58.345 zone_maintenance: zone 254.169.IN-ADDR.ARPA/IN: enter
26-Jun-2011 23:19:58.345 zone_settimer: zone 254.169.IN-ADDR.ARPA/IN: enter
26-Jun-2011 23:19:58.345 zone_timer: zone 255.in-addr.arpa/IN: enter
26-Jun-2011 23:19:58.345 zone_maintenance: zone 255.in-addr.arpa/IN: enter
26-Jun-2011 23:19:58.345 zone_settimer: zone 255.in-addr.arpa/IN: enter
26-Jun-2011 23:19:58.345 zone_timer: zone 255.255.255.255.IN-ADDR.ARPA/IN: enter
26-Jun-2011 23:19:58.345 zone_maintenance: zone 255.255.255.255.IN-ADDR.ARPA/IN: enter
26-Jun-2011 23:19:58.345 zone_settimer: zone 255.255.255.255.IN-ADDR.ARPA/IN: enter
26-Jun-2011 23:19:58.345 zone_timer: zone 2.0.192.IN-ADDR.ARPA/IN: enter
26-Jun-2011 23:19:58.345 zone_maintenance: zone 2.0.192.IN-ADDR.ARPA/IN: enter
26-Jun-2011 23:19:58.345 zone_settimer: zone 2.0.192.IN-ADDR.ARPA/IN: enter
26-Jun-2011 23:19:58.345 zone_timer: zone 113.0.203.IN-ADDR.ARPA/IN: enter
26-Jun-2011 23:19:58.345 zone_maintenance: zone 113.0.203.IN-ADDR.ARPA/IN: enter
26-Jun-2011 23:19:58.345 zone_settimer: zone 113.0.203.IN-ADDR.ARPA/IN: enter
26-Jun-2011 23:19:58.345 zone_timer: zone 100.51.198.IN-ADDR.ARPA/IN: enter
26-Jun-2011 23:19:58.345 zone_maintenance: zone 100.51.198.IN-ADDR.ARPA/IN: enter
26-Jun-2011 23:19:58.345 zone_settimer: zone 100.51.198.IN-ADDR.ARPA/IN: enter
26-Jun-2011 23:19:58.345 zone_timer: zone 0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA/IN: enter
26-Jun-2011 23:19:58.345 zone_maintenance: zone 0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA/IN: enter
26-Jun-2011 23:19:58.345 zone_settimer: zone 0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA/IN: enter
26-Jun-2011 23:19:58.345 zone_timer: zone 8.E.F.IP6.ARPA/IN: enter
26-Jun-2011 23:19:58.345 zone_maintenance: zone 8.E.F.IP6.ARPA/IN: enter
26-Jun-2011 23:19:58.345 zone_settimer: zone 8.E.F.IP6.ARPA/IN: enter
26-Jun-2011 23:19:58.345 zone_timer: zone D.F.IP6.ARPA/IN: enter
26-Jun-2011 23:19:58.345 zone_maintenance: zone D.F.IP6.ARPA/IN: enter
26-Jun-2011 23:19:58.345 zone_settimer: zone D.F.IP6.ARPA/IN: enter
26-Jun-2011 23:19:58.345 zone_timer: zone version.bind/CH: enter
26-Jun-2011 23:19:58.345 zone_maintenance: zone version.bind/CH: enter
26-Jun-2011 23:19:58.345 zone_settimer: zone version.bind/CH: enter
26-Jun-2011 23:19:58.345 zone_timer: zone B.E.F.IP6.ARPA/IN: enter
26-Jun-2011 23:19:58.345 zone_maintenance: zone B.E.F.IP6.ARPA/IN: enter
26-Jun-2011 23:19:58.348 zone_settimer: zone B.E.F.IP6.ARPA/IN: enter
26-Jun-2011 23:19:58.348 zone_timer: zone 0.1.1.0.0.2.IP6.ARPA/IN: enter
26-Jun-2011 23:19:58.348 zone_maintenance: zone 0.1.1.0.0.2.IP6.ARPA/IN: enter
26-Jun-2011 23:19:58.351 zone_settimer: zone 0.1.1.0.0.2.IP6.ARPA/IN: enter
26-Jun-2011 23:19:58.351 zone_timer: zone id.server/CH: enter
26-Jun-2011 23:19:58.351 zone_maintenance: zone id.server/CH: enter
26-Jun-2011 23:19:58.351 zone_settimer: zone id.server/CH: enter
26-Jun-2011 23:19:58.351 zone_timer: zone 1.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA/IN: enter
26-Jun-2011 23:19:58.351 zone_maintenance: zone 1.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA/IN: enter
26-Jun-2011 23:19:58.352 zone_settimer: zone 1.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA/IN: enter
26-Jun-2011 23:19:58.352 zone_timer: zone 9.E.F.IP6.ARPA/IN: enter
26-Jun-2011 23:19:58.352 zone_maintenance: zone 9.E.F.IP6.ARPA/IN: enter
26-Jun-2011 23:19:58.352 zone_settimer: zone 9.E.F.IP6.ARPA/IN: enter
26-Jun-2011 23:19:58.352 zone_timer: zone hostname.bind/CH: enter
26-Jun-2011 23:19:58.352 zone_maintenance: zone hostname.bind/CH: enter
26-Jun-2011 23:19:58.352 zone_settimer: zone hostname.bind/CH: enter
26-Jun-2011 23:19:58.352 zone_timer: zone authors.bind/CH: enter
26-Jun-2011 23:19:58.352 zone_maintenance: zone authors.bind/CH: enter
26-Jun-2011 23:19:58.352 zone_settimer: zone authors.bind/CH: enter
26-Jun-2011 23:19:58.352 zone_timer: zone A.E.F.IP6.ARPA/IN: enter
26-Jun-2011 23:19:58.352 zone_maintenance: zone A.E.F.IP6.ARPA/IN: enter
26-Jun-2011 23:19:58.352 zone_settimer: zone A.E.F.IP6.ARPA/IN: enter
26-Jun-2011 23:19:58.352 zone_timer: zone 8.B.D.0.1.0.0.2.IP6.ARPA/IN: enter
26-Jun-2011 23:19:58.352 zone_maintenance: zone 8.B.D.0.1.0.0.2.IP6.ARPA/IN: enter
26-Jun-2011 23:19:58.352 zone_settimer: zone 8.B.D.0.1.0.0.2.IP6.ARPA/IN: enter


So, now I still have to replace the keys because I posted them here.




Seems for using tsig, some more work is necessary:
[http://www.cyberciti.biz/faq/unix-linux-bind-named-configuring-tsig/](http://www.cyberciti.biz/faq/unix-linux-bind-named-configuring-tsig/)

Thinking about it, I should be able to get Firebird to work via ODBC.

And looks like copy pasting from these 4
[http://ubuntuforums.org/showthread.php?t=823578](http://ubuntuforums.org/showthread.php?t=823578)
[https://sites.google.com/a/devel.ws/iptables-stuff/bind-dlz-mysql](https://sites.google.com/a/devel.ws/iptables-stuff/bind-dlz-mysql)
[http://forums.gentoo.org/viewtopic-t-346739-start-0.html](http://forums.gentoo.org/viewtopic-t-346739-start-0.html)
[http://ubuntuforums.org/showthread.php?p=9160045](http://ubuntuforums.org/showthread.php?p=9160045)


in comparison to this:
[http://bind-dlz.sourceforge.net/mysql_example.html](http://bind-dlz.sourceforge.net/mysql_example.html)

One can also create the MySQL table create scripts.

Now looking for how to add entries. 
I guess this is gonna be real fun, too.

---

### Post by WitchCraft on 2011-06-28
Here the proper MySQL tables, just in case anybody needs them:
```

CREATE TABLE `dns_records` (
  `id` int(10) unsigned NOT NULL AUTO_INCREMENT,
  `zone` varchar(255) NOT NULL,
  `host` varchar(255) NOT NULL DEFAULT '@',
  `type` varchar(255) NOT NULL,
  `data` text,
  `ttl` int(11) NOT NULL DEFAULT '86400',
  `mx_priority` int(11) DEFAULT NULL,
  `refresh` int(11) DEFAULT NULL,
  `retry` int(11) DEFAULT NULL,
  `expire` int(11) DEFAULT NULL,
  `minimum` int(11) DEFAULT NULL,
  `serial` bigint(20) DEFAULT NULL,
  `resp_person` varchar(255) DEFAULT NULL,
  `primary_ns` varchar(255) DEFAULT NULL,
  PRIMARY KEY (`id`),
  KEY `type` (`type`),
  KEY `host` (`host`),
  KEY `zone` (`zone`),
  KEY `zone_host_index` (`zone`(30),`host`(30)),
  KEY `type_index` (`type`(8))
) ENGINE=InnoDB DEFAULT CHARSET=utf8
 

```
 
```

CREATE TABLE `xfr_table` (
  `zone` varchar(255) NOT NULL,
  `client` varchar(255) NOT NULL,
  KEY `zone` (`zone`),
  KEY `client` (`client`),
  KEY `zone_client_index` (`zone`(30),`client`(30))
) ENGINE=InnoDB DEFAULT CHARSET=utf8
 

```

---

### Post by WitchCraft on 2011-09-04
And the next best thing:
The pg scripts have gone offline.

Here a backup, courtesy of web.archive.org @ the University of Alexandria

```

CREATE TABLE dns_record (     id integer NOT NULL,     zone character varying(255) NOT NULL,     ttl integer NOT NULL,     type character varying(255) NOT NULL,     host character varying(255) DEFAULT '@'::character varying NOT NULL,     mx_priority integer,     data text,     primary_ns character varying(255),     resp_contact character varying(255),     serial bigint,     refresh integer,     retry integer,     expire integer,     minimum integer );

``````

CREATE SEQUENCE dns_record_id_seq     START WITH 1     INCREMENT BY 1     NO MAXVALUE     NO MINVALUE     CACHE 1;

``````

CREATE SEQUENCE dns_record_id_seq     START WITH 1     INCREMENT BY 1     NO MAXVALUE     NO MINVALUE     CACHE 1;  ALTER TABLE dns_record ALTER COLUMN id SET DEFAULT nextval('dns_record_id_seq'::regclass);
```

And the rest, for whatever reason, ubuntuforums destroys the source layout...
```

CREATE TABLE dns_xfr (     zone character varying(255) NOT NULL,     client character varying(255) NOT NULL );  CREATE INDEX dns_xfr_client_idx ON dns_xfr USING btree (client); CREATE INDEX dns_xfr_zone_idx ON dns_xfr USING btree (zone); 

```


```

dlz "Postgres Zone" {        database "postgres 2        {host=127.0.0.1 port=5432 dbname=bind user=bind}        {SELECT zone FROM dns_record WHERE zone = '%zone%'}        {SELECT ttl, type, mx_priority, case when lower(type)='txt' then '\"' || data || '\"' else data end AS data FROM dns_record WHERE zone = '%zone%' AND host = '%record%' AND type <> 'SOA' AND type <> 'NS'}        {SELECT ttl, type, data, resp_contact, serial, refresh, retry, expire, minimum FROM dns_record WHERE zone = '%zone%' AND (type = 'SOA' OR type='NS')}        {SELECT ttl, type, host, mx_priority, case when lower(type)='txt' then '\"' || data || '\"' else data end AS data, resp_contact, serial, refresh, retry, expire, minimum FROM dns_record WHERE zone = '%zone%' AND type <> 'SOA' AND type <> 'NS'}        {SELECT zone FROM dns_xfr where zone='%zone%' AND client = '%client%'}"; }; 

```



and with zone transfer

```

dlz "Postgres Zone" {         database "postgres 2         {host=127.0.0.1 port=5432 dbname=bind user=bind}         {SELECT zone FROM dns_record WHERE zone = '%zone%'}         {SELECT ttl, type, mx_priority, CASE WHEN LOWER(type)='txt' THEN '\"' || data || '\"' WHEN LOWER(type)='soa' THEN data || ' ' || resp_contact || ' ' || serial || ' ' || refresh || ' ' || retry || ' ' || expire || ' ' || minimum else data end from dns_record where zone = '%zone%' and host = '%record%'}         {}         {select ttl, type, host, mx_priority, case when lower(type)='txt' then '\"' || data || '\"' else data end, resp_contact, serial, refresh, retry, expire, minimum from dns_record where zone = '%zone%'}         {SELECT zone FROM dns_xfr where zone='%zone%' AND client = '%client%'}"; }; 

```

---

### Post by WitchCraft on 2011-09-04
Ah, damn, the boot order:

bind9 now starts before MySQL/pgSQL


[http://diaryproducts.net/about/operating_systems/unix/installing_bind9_with_dlz_and_mysql_backend_on_ubuntu_jaunty_9_04](http://diaryproducts.net/about/operating_systems/unix/installing_bind9_with_dlz_and_mysql_backend_on_ubuntu_jaunty_9_04)

---

### Post by WitchCraft on 2011-09-06
On 11.04, there are new gotchas:

#1:
```

mkdir /var/cache/bind

```Because
```

/etc/bind/named.conf.options

```specifies
```

directory "/var/cache/bind";

```But this directory doesn't exist.


#2: comment out:
```

#options {
#default-key "rndc-key";
#default-server 127.0.0.1;
#default-port 953;
#};

```

---

### Post by WitchCraft on 2011-09-06
What's the name of the gremlin playing around in the ubuntu source repository ?

Formerly, after I recompiled bind9 for DLZ support, named -d 9 -g used to output 
> 
26-Jun-2011 22:21:17.409 starting BIND 9.7.1-P2 -d 9 -g
26-Jun-2011 22:21:17.409 built with '--with-dlz-mysql=yes' '--with-dlz-postgres=yes'


Now, on 11.04, after rebuild from source with DLZ support, I get:
> 
06-Sep-2011 23:10:11.551 starting BIND 9.7.3 -d 9 -g
06-Sep-2011 23:10:11.551 built with defaults



And it seems to completely ignore the DLZ settings, let alone a wrong password or db...
Is there something overwriting the rules file, deleting my --with flags ?

Did this breake in the transition from 10.10 to 11.04 ?

---

### Post by WitchCraft on 2011-09-06
> **AlexC_ said:**
> Excuse me? We're not your slaves. I've given you plenty of information but your lack of willingness to actually put a little bit of effort in is down right rude.

As I said before, get over your self and put your ego away. Once you've done that, people will help you.

I'll be unsubscribing from this thread that's for sure. Good luck.

8 hours is NOT a 'little' effort.

---

### Post by WitchCraft on 2011-09-06
Just wanted to say that the repository version is f*ed up.
[http://itsecureadmin.com/2010/09/bind-dlz-with-mysql/](http://itsecureadmin.com/2010/09/bind-dlz-with-mysql/)
has a nice tutorial

Download the latest stable source from: [http://www.isc.org/downloads](http://www.isc.org/downloads)

Then install the dependencies
```

apt-get install libmysqlclient15-dev (with-dlz-mysql)
apt-get install libpq-dev (with-dlz-postgres,  postgresql-devel RPM)
apt-get install libdb4.6-dev (with-dlz-bdb)

```
or for Fedora-fans:
```

yum install openssl-devel mysql-devel openldap-devel unixODBC-devel gcc

```


and then start the build
```

./configure --prefix=/usr --sysconfdir=/etc/bind --localstatedir=/var 
--enable-threads --enable-largefile --with-libtool --enable-shared --enable-static 
--with-openssl=/usr --with-gssapi=/usr --with-gnu-ld 
--with-dlz-postgres=yes --with-dlz-mysql=yes 
--with-dlz-filesystem=yes --with-dlz-stub=yes --with-geoip=/usr --enable-ipv6 
--with-dlz-bdb=yes 

```


Do NOT include
```

--with-dlz-ldap=yes 

```
or you will get a unresolved symbol error.
It probably lacks -lresolv somewhere...

---

### Post by WitchCraft on 2011-09-06
Aferwards, you still need to check whether bind9 now works

```

dig @127.0.0.1 www.domaininsertedindatabase.com

```

[http://linuxconfig.org/linux-dns-server-bind-configuration](http://linuxconfig.org/linux-dns-server-bind-configuration)
contains some nice infos.


And finaly, another problem resolved:
Compiling the ubuntu sources from source created named files in /usr/local/sbin, and this folder is prefered over /usr/sbin...

So one has to delete the old installation first, then everything works, and also, the config files are in the /etc/bind folder...

Now dig resolves my fictional entries correctly.

I still have to figure out, why the logging, setup according to 
[https://help.ubuntu.com/community/BIND9ServerHowto](https://help.ubuntu.com/community/BIND9ServerHowto)
throws access denied errors on writing to the config file, although I did touch and chown.

---

