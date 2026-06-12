---
title: "Could not download all repository indexes"
date: 2006-07-03
forum: Repositories &amp; Backports
---

### Post by Malakia on 2006-07-03
Here is the error I keep getting when I am trying to add repositories. 

[http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg:](http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

What can I do to fix this so I can add new software. The internet itself works fine and its running off of a D-Link wireless router. 

Any help would be appreciated considering I am newbie.

---

### Post by stonefeet on 2006-07-04
try pinging or do a lookup on archive.ubuntu.com

then try to update

i had the same problem and searched all over and the work around for this problem was fairly simple

---

### Post by Malakia on 2006-07-04
I pinged it and it brought up a totally different ip address so how do I change it to the one that is correct instead of the localhost.:confused:

---

### Post by adwait on 2006-07-04
You seem to have setup a proxy or something, because the IP address there points to your own computer @ port 4001. Check your resolv.conf....If nothing else, replace the URLS with the IP addresses that you get when you ping the site. That way the resolution step is skipped.....but this is just a stopgap solution.

---

### Post by Malakia on 2006-07-04
My resolv.conf is fine its pointing to the right place so what else can I check?

---

### Post by Malakia on 2006-07-04
I recently installed postfix could that be the problem

---

### Post by villavicencio on 2006-07-08
I had the same problem and I fixed it with the following command:

unset http_proxy

It appears that I had some kind of proxy set up that I didn't know about.  Good luck.

---

### Post by thomas997 on 2006-07-10
I'm having a similar problem:
> Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
  Connection failed
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg
  Connection failed [IP: 85.133.25.8 80]
Err [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg
  Connection failed
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg
  Connection failed [IP: 85.133.25.8 80]

pinging the address works, opening it in firefox works as well. I tried adding the resolved IP to the hosts and resolv.conf file but that doesnt seem to help. The attempted connection DOES show up in the router log, so I assume its getting sent out?:
> Mon, 2006-07-10 02:39:30 - TCP packet - Source: 192.168.0.4 - Destination: 82.211.81.151 - [Service access request successful Src 41789 Dst 80 from CORP n/w]

The odd thing is that I just had 5.10 installed and updates would work fine, then I formatted and installed 6.06 and it fails..


**edit:** ok google could find this thread but didnt seem to find the one that is on page 2 or 3 ([http://ubuntuforums.org/showthread.php?t=197046)?](http://ubuntuforums.org/showthread.php?t=197046)?) Anyway his solution was to uncheck keyword blocking in router settings.

Even though I had nothing being blocked, and even though it worked FINE with 5.10, I unchecked keyword, hit apply, and it WORKS. How is this possible? I have no damn idea :)

---

### Post by HecticPoodle on 2007-07-13
I have a problem with downloading repository indexes aswell:


[I][http://gb.archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg:](http://gb.archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg:) Could not connect to gb.archive.ubuntu.com:80 (194.169.254.10). - connect (111 Connection refused)
[http://gb.archive.ubuntu.com/ubuntu/dists/feisty/main/i18n/Translation-en_GB.bz2:](http://gb.archive.ubuntu.com/ubuntu/dists/feisty/main/i18n/Translation-en_GB.bz2:) Could not connect to gb.archive.ubuntu.com:80 (194.169.254.10). - connect (111 Connection refused)
[http://gb.archive.ubuntu.com/ubuntu/dists/feisty/restricted/i18n/Translation-en_GB.bz2:](http://gb.archive.ubuntu.com/ubuntu/dists/feisty/restricted/i18n/Translation-en_GB.bz2:) Could not connect to gb.archive.ubuntu.com:80 (194.169.254.10). - connect (111 Connection refused)
[http://gb.archive.ubuntu.com/ubuntu/dists/feisty/universe/i18n/Translation-en_GB.bz2:](http://gb.archive.ubuntu.com/ubuntu/dists/feisty/universe/i18n/Translation-en_GB.bz2:) Could not connect to gb.archive.ubuntu.com:80 (194.169.254.10). - connect (111 Connection refused)
[http://gb.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/i18n/Translation-en_GB.bz2:](http://gb.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/i18n/Translation-en_GB.bz2:) Could not connect to gb.archive.ubuntu.com:80 (194.169.254.10). - connect (111 Connection refused)
[http://gb.archive.ubuntu.com/ubuntu/dists/feisty-updates/Release.gpg:](http://gb.archive.ubuntu.com/ubuntu/dists/feisty-updates/Release.gpg:) Could not connect to gb.archive.ubuntu.com:80 (194.169.254.10). - connect (111 Connection refused)
[http://gb.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/i18n/Translation-en_GB.bz2:](http://gb.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/i18n/Translation-en_GB.bz2:) Could not connect to gb.archive.ubuntu.com:80 (194.169.254.10). - connect (111 Connection refused)
[http://gb.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/i18n/Translation-en_GB.bz2:](http://gb.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/i18n/Translation-en_GB.bz2:) Could not connect to gb.archive.ubuntu.com:80 (194.169.254.10). - connect (111 Connection refused)
[http://security.ubuntu.com/ubuntu/dists/feisty-security/Release.gpg:](http://security.ubuntu.com/ubuntu/dists/feisty-security/Release.gpg:) Could not connect to security.ubuntu.com:80 (91.189.88.31). - connect (111 Connection refused) [IP: 91.189.88.31 80]
[http://security.ubuntu.com/ubuntu/dists/feisty-security/main/i18n/Translation-en_GB.bz2:](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/i18n/Translation-en_GB.bz2:) Could not connect to security.ubuntu.com:80 (91.189.88.31). - connect (111 Connection refused) [IP: 91.189.88.31 80]
[http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/i18n/Translation-en_GB.bz2:](http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/i18n/Translation-en_GB.bz2:) Could not connect to security.ubuntu.com:80 (91.189.88.31). - connect (111 Connection refused) [IP: 91.189.88.31 80]
[http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/i18n/Translation-en_GB.bz2:](http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/i18n/Translation-en_GB.bz2:) Could not connect to security.ubuntu.com:80 (91.189.88.31). - connect (111 Connection refused) [IP: 91.189.88.31 80]
[http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/i18n/Translation-en_GB.bz2:](http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/i18n/Translation-en_GB.bz2:) Could not connect to security.ubuntu.com:80 (91.189.88.31). - connect (111 Connection refused) [IP: 91.189.88.31 80]
[http://ubuntu.beryl-project.org/dists/feisty/Release.gpg:](http://ubuntu.beryl-project.org/dists/feisty/Release.gpg:) Could not connect to ubuntu.beryl-project.org:80 (82.140.42.54). - connect (111 Connection refused) [IP: 82.140.42.54 80]
[http://ubuntu.beryl-project.org/dists/feisty/main/i18n/Translation-en_GB.bz2:](http://ubuntu.beryl-project.org/dists/feisty/main/i18n/Translation-en_GB.bz2:) Could not connect to ubuntu.beryl-project.org:80 (82.140.42.54). - connect (111 Connection refused) [IP: 82.140.42.54 80][/I]


The only way i can connect to the internet is through an 'Automatic proxy configuration URL'. Is there any way of setting this in 'Synaptic Package Manager'?

Also I can't ping in a terminal, I only have a connection through firefox!

---

