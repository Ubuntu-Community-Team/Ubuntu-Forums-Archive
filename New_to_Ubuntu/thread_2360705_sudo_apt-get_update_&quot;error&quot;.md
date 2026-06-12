---
title: "sudo apt-get update &quot;error&quot;"
date: 2017-05-07
forum: New to Ubuntu
---

### Post by gravity1988 on 2017-05-07
Hi,
         I am facing with an error when I use the command sudo apt-get update. When I do this, the following error is found. Unfortunately, nothing is installed in my laptop. Previously I could install everything and there were no problems with update. It has been a very serious problem to me since I cannot install anything including my recent HP printer. 
I will be really grateful if someone helps me out of this situation. 

Bests,

Supriya

Please see the following. 

```
Err:1 [http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu](http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu) xenial InRelease
  Could not connect to 172.21.30.124:8080 (172.21.30.124). - connect (111: Connection refused)
Err:2 [http://ppa.launchpad.net/ubuntu-toolchain-r/test/ubuntu](http://ppa.launchpad.net/ubuntu-toolchain-r/test/ubuntu) xenial InRelease
  Unable to connect to 172.21.30.124:8080:
Err:3 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease
  Could not connect to 172.21.30.124:8080 (172.21.30.124). - connect (111: Connection refused)
Err:4 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial InRelease
  Could not connect to 172.21.30.124:8080 (172.21.30.124). - connect (111: Connection refused)
Err:5 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease
  Could not connect to 172.21.30.124:8080 (172.21.30.124). - connect (111: Connection refused)
Err:6 [http://dl.google.com/linux/talkplugin/deb](http://dl.google.com/linux/talkplugin/deb) stable InRelease
  Unable to connect to 172.21.30.124:8080:
Err:7 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial InRelease
  Could not connect to 172.21.30.124:8080 (172.21.30.124). - connect (111: Connection refused)
Err:8 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates InRelease
  Unable to connect to 172.21.30.124:8080:
Err:9 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports InRelease
  Unable to connect to 172.21.30.124:8080:
Reading package lists... Done
W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/xenial/InRelease](http://archive.canonical.com/ubuntu/dists/xenial/InRelease)  Could not connect to 172.21.30.124:8080 (172.21.30.124). - connect (111: Connection refused)
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/xenial/InRelease](http://archive.ubuntu.com/ubuntu/dists/xenial/InRelease)  Could not connect to 172.21.30.124:8080 (172.21.30.124). - connect (111: Connection refused)
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/xenial-security/InRelease](http://security.ubuntu.com/ubuntu/dists/xenial-security/InRelease)  Could not connect to 172.21.30.124:8080 (172.21.30.124). - connect (111: Connection refused)
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/xenial-updates/InRelease](http://archive.ubuntu.com/ubuntu/dists/xenial-updates/InRelease)  Unable to connect to 172.21.30.124:8080:
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/xenial-backports/InRelease](http://archive.ubuntu.com/ubuntu/dists/xenial-backports/InRelease)  Unable to connect to 172.21.30.124:8080:
W: Failed to fetch [http://dl.google.com/linux/chrome/deb/dists/stable/InRelease](http://dl.google.com/linux/chrome/deb/dists/stable/InRelease)  Could not connect to 172.21.30.124:8080 (172.21.30.124). - connect (111: Connection refused)
W: Failed to fetch [http://dl.google.com/linux/talkplugin/deb/dists/stable/InRelease](http://dl.google.com/linux/talkplugin/deb/dists/stable/InRelease)  Unable to connect to 172.21.30.124:8080:
W: Failed to fetch [http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu/dists/xenial/InRelease](http://ppa.launchpad.net/i-nex-development-team/stable/ubuntu/dists/xenial/InRelease)  Could not connect to 172.21.30.124:8080 (172.21.30.124). - connect (111: Connection refused)
W: Failed to fetch [http://ppa.launchpad.net/ubuntu-toolchain-r/test/ubuntu/dists/xenial/InRelease](http://ppa.launchpad.net/ubuntu-toolchain-r/test/ubuntu/dists/xenial/InRelease)  Unable to connect to 172.21.30.124:8080:
W: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by deadflowr on 2017-05-07
Do you have any internet connection from that system?

---

### Post by gravity1988 on 2017-05-07
Yes, I am using internet in that system. Just couple of weeks back, it was perfectly alright. Suddenly, I encountered with such problem.

---

### Post by deadflowr on 2017-05-07
Are you running through a proxy setup?
As that error seems to be related to proxy:
[https://askubuntu.com/questions/678285/111-connection-refused]("https://askubuntu.com/questions/678285/111-connection-refused")

---

### Post by RobGoss on 2017-05-07
Hello and welcome to the forum, have you tried changing your download source?

---

### Post by gravity1988 on 2017-05-08
Hideadflowr, 
Yes, I am using the internet through a proxy setup. I followed exactly the same approach suggested by you [https://askubuntu.com/questions/678285/111-connection-refused](https://askubuntu.com/questions/678285/111-connection-refused)
Now, I found that sudo apt-get works fine. But, it is strange to me that now firefox is working (which did not work until yesterday), chrome is not working (with there is something wrong the proxy or the internet connection[CENTER][COLOR=#8F8F8F][FONT=sans][/FONT][/COLOR][/CENTER]). I used both few weeks ago. Currently I am in a new place and I suspect it happened when I took a new LAN connection and the survice providers did something wrong with it. I am not an expert on these things. 

Would be nice if both the browsers work fine ! 

Bests,
[**[COLOR=#C61919][B]**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=1276577")

---

### Post by gravity1988 on 2017-05-08
Hi RobGoss,
                     Thank you very much. Yes, I did it following the link [https://askubuntu.com/questions/678285/111-connection-refused](https://askubuntu.com/questions/678285/111-connection-refused) suggested by deadflowr ! 
But, now firefox is working, chrome is not. Previously the converse was true. Now there is no problem with sudo apt-get update or install. It is working fine now. 
When I open the chrome browser, it shows that there is something wrong with the proxy setting or the internet connection. I do not understand what is happening! it seems that 
one of them will work. 

Bests,

---

### Post by deadflowr on 2017-05-08
Per chrome not working anymore, --check the network setting in chrome.
(Open settings, go down, click advanced, go to Network click on Change Proxy Settings)

---

### Post by gravity1988 on 2017-05-08
Hi,
Thank you very much. It was solved using the following approach.
Network ---> Network Proxy ---->Method (None)----> Apply system wide....and I found that both firefox and chrome are working now...

Thank you very much for the help.

---

