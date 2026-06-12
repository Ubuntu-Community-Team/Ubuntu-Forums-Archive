---
title: "Apache2 install defaults to local host only connection"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by ejpyle on 2008-05-11
i just did a fresh install of LAMP and I see the "it works" test page and all.
I have made a new site and and everything works, however, I am only able to connect using a localhost and I can only connect from the PC that is running Apache2. 

What changes need to be made? I have already set up port forwarding to port 80 on my router.

---

### Post by freebeer on 2008-05-11
are you trying to access the web pages from another machine within the LAN?  It's not exactly clear what your set up is and what, exactly, you're trying to do.

---

### Post by ejpyle on 2008-05-11
Thanks for the reply....let me elaborate for you.

I have a router with port forwarding setup to send all HTTP traffic through port 80 to the static internal IP address I have set up on the web server which is 192.168.1.3

When I go to 192.168.1.3 on the local PC I can pull up the website though it resolves to the local host 127.0.0.1.

I try to access it from another PC within the network and I get connection refused. It acts as if the site is there though it just wont load.

Question is what am I supposed to do so that I can access the website from another computer within the network as well as outside the network?

---

### Post by freebeer on 2008-05-11
Don't do the above!  I think he's suggesting you reformat your hard drive.  I've seen this post from him before, so I'm suspecting a malicious intent.

More later... must post this quick.

---

### Post by ejpyle on 2008-05-11
> **I_love_p_quarles said:**
> This happens a lot with ext filesystem.  You can repair it by typing:
```

<snip>

```

and apache should run just fine.  Good luck!

Does this have anything to do with the way Linux mounts external drives/partitions? I noticed that the command you provided me gives several different options. Does this have anything to do with the way I have the drive entered in my FSTAB?

/dev/sda1	/media/disk	ext3	defaults	0	0

The directory that it is trying to access is on another hard drive.

---

### Post by HotShotDJ on 2008-05-11
> **I_love_p_quarles said:**
> This happens a lot with ext filesystem.  You can repair it by typing:
```

<snip>

```

and apache should run just fine.  Good luck!This command may do damage to your system.  Ignore this person's posts.

---

### Post by ejpyle on 2008-05-11
> **HotShotDJ said:**
> This command may do damage to your system.  Ignore this person's posts.

LMFAO....!!!!

Sat night, I am drunk as heck, and I have people messing with me....Alcohol and Ubuntu don't mix.....


I reported him.

---

### Post by freebeer on 2008-05-11
I'm not sure why you might be getting a "connection refused" error unless you've got some kind of security/authentication set up and it's not getting the authentication that it needs.

Laying aside the refused error for the moment, do you have a domain set up for the server?  (This is strictly not necessary, but it can be helpful.)

---

### Post by ejpyle on 2008-05-11
> **freebeer said:**
> Don't do the above!  I think he's suggesting you reformat your hard drive.  I've seen this post from him before, so I'm suspecting a malicious intent.

More later... must post this quick.

I bet it's Bill Gates playing pranks in his "I Love Linux" underwear.

---

### Post by ejpyle on 2008-05-11
> **freebeer said:**
> I'm not sure why you might be getting a "connection refused" error unless you've got some kind of security/authentication set up and it's not getting the authentication that it needs.

Laying aside the refused error for the moment, do you have a domain set up for the server?  (This is strictly not necessary, but it can be helpful.)

No I don't have a domain set up...I was just looking to have people type in my public ip to the router in their browser and be forwarded to my internal LAN IP that Apache2 is running on (192.168.1.3)

---

### Post by Monicker on 2008-05-11
> **ejpyle said:**
> Thanks for the reply....let me elaborate for you.

I have a router with port forwarding setup to send all HTTP traffic through port 80 to the static internal IP address I have set up on the web server which is 192.168.1.3

When I go to 192.168.1.3 on the local PC I can pull up the website though it resolves to the local host 127.0.0.1.

I try to access it from another PC within the network and I get connection refused. It acts as if the site is there though it just wont load.

Question is what am I supposed to do so that I can access the website from another computer within the network as well as outside the network?

By default Apache listens on all ip addresses and not just localhost.  To restrict that you would have to change the configuration.  Are you doing any firewalling on the apache server?

What is the output of the following command?
```

sudo netstat -anltp|grep apache
```

---

### Post by ejpyle on 2008-05-11
> **Monicker said:**
> By default Apache listens on all ip addresses and not just localhost.  To restrict that you would have to change the configuration.  Are you doing any firewalling on the apache server?

What is the output of the following command?
```

sudo netstat -anltp|grep apache
```


tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      10565/apache2


I dont know about firewalling....This was a fresh installed...Ran updates and installed LAMP

---

### Post by Monicker on 2008-05-11
Okay.  Its definitely listening on port 80 for all ip addresses.  That is that 0.0.0.0:80 means.  0.0.0.0 is all addresses, and of course the default http port of 80.

Something else seems to be preventing the connection from being made from externally.


Do you have any firewall rules in place?

---

### Post by ejpyle on 2008-05-11
> **Monicker said:**
> Okay.  Its definitely listening on port 80 for all ip addresses.  That is that 0.0.0.0:80 means.  0.0.0.0 is all addresses, and of course the default http port of 80.

Something else seems to be preventing the connection from being made from externally.


Do you have any firewall rules in place?


I would not be certain on that one Monicker. Is there a way to check?
As I stated before, this was from a fresh install....I have been scratching my head on this one for 2 days....

---

### Post by ejpyle on 2008-05-11
BTW, if I am on the computer with apache and I type in the internal ip assigned to it i get to the site though it resolves to [http://127.0.1.1/index.php](http://127.0.1.1/index.php)

---

### Post by Monicker on 2008-05-11
> **ejpyle said:**
> I would not be certain on that one Monicker. Is there a way to check?
As I stated before, this was from a fresh install....I have been scratching my head on this one for 2 days....

A fresh install would not have any restrictive firewall rules in places.  You can verify by running the following:

```
sudo iptables -n -L
```

You could also check /var/log/apache2/access.log, to see if the incoming connections are even being shown there.

---

### Post by ejpyle on 2008-05-11
> **Monicker said:**
> A fresh install would not have any restrictive firewall rules in places.  You can verify by running the following:

```
sudo iptables -n -L
```

You could also check /var/log/apache2/access.log, to see if the incoming connections are even being shown there.

The log file shows this

127.0.1.1 - - [11/May/2008:01:30:55 -0500] "GET /myPh3.core.php HTTP/1.1" 200 1219 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9b5) Gecko/2008050509 Firefox/3.0b5"

---

### Post by ejpyle on 2008-05-11
with regard to apache being open to everyone at default.....

....could this mean that the issue is with my network configuration....?

---

### Post by Monicker on 2008-05-11
> **ejpyle said:**
> with regard to apache being open to everyone at default.....

....could this mean that the issue is with my network configuration....?

Possibly, though at first glance it seems like a pretty basic setup.

Can you even ping the web server from a different machine?  Can the web server ping other machines on the network?

If you run the iptables command I gave earlier you should see the following if no firewalling was put in place:

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```

---

### Post by ejpyle on 2008-05-11
No firewalling....

check this out...I came down stairs and got on another computer within my network...

I can ping the Apache2 PC (192.168.1.3) though when I type that address into the address bar I get the message

Failed To cOnnect
Firefox can't establish a connection to the server at 127.0.1.1.

now in the address bar the 192.168.1.3 changes to [http://127.0.1.1/myPh3.core.php...which](http://127.0.1.1/myPh3.core.php...which) is the address of localhost pointing to my website.

---

### Post by Monicker on 2008-05-11
You need to provide a lot more information.  So far you have still left out some of what has been requested.


Lets say Computer A is the apache server, and Computer B is a client which can't reach the web server on A.

What is the ip address and netmask of both computers?
What does "netstat -rn" from each computer show?
What is in the hosts file for each computer?

What is the actual output when you ping A from B?
What is the actual output when you ping B from A?

Is computer B also a linux machine?  If not, what operating system is it?

---

### Post by spiderbatdad on 2008-05-11
> **ejpyle said:**
> No firewalling....

check this out...I came down stairs and got on another computer within my network...

I can ping the Apache2 PC (192.168.1.3) though when I type that address into the address bar I get the message

Failed To cOnnect
Firefox can't establish a connection to the server at 127.0.1.1.

now in the address bar the 192.168.1.3 changes to [http://127.0.1.1/myPh3.core.php...which](http://127.0.1.1/myPh3.core.php...which) is the address of localhost pointing to my website.

It looks like you need to add another ServerName <yourip> in httpd.conf  where <yourip> is the actual ip address provided by your isp. Checkout: [www.whatismyip.com](www.whatismyip.com)

```
ServerName localhost
ServerName spiderbatdad.podzone.org
<Directory /xxxx/xxxx/xxxx />
AllowOverride All
</Directory>

<Files ~ "^\.ht">
    Order allow,deny
    Deny from all
</Files>
```

---

### Post by ejpyle on 2008-05-13
well guys it turned out to be a permissions issue on my web folders...
i ran a CHOWN from root to me and then I CHMOD.... now everything works...
sorry it took so long to post.....i have been going web site crazy.....

.....not to mention i am addicted to that game "Urban Terror"

thank you all.

---

