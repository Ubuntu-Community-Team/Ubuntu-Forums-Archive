---
title: "Problems Connecting to software updater"
date: 2018-06-18
forum: New to Ubuntu
---

### Post by mattcrust on 2018-06-18
Hi, I'm not a complete novice but my linux understanding is limited to the basics. I am currently using 16.10 LTS and I am having an issue with the Software installer as I keep getting an apt error (no connection). When i try to do this in a terminal either
"sudo apt update" or "wget   [http://ftp.gb.debian.org/debian/pool/main/n/netselect/netselect_0.3.ds1-26_amd64.deb](http://ftp.gb.debian.org/debian/pool/main/n/netselect/netselect_0.3.ds1-26_amd64.deb) " I get "Could not connect to 130.159.183.75:9100 (130.159.183.75), connection timed out"

thanks in advance for any help or ideas

Matt

---

### Post by &amp;KyT$0P# on 2018-06-18
16.10 was not a LTS.  It has been unsupported for nearly a year now.  Please install 16.04 or 18.04 for your own safety.

---

### Post by deadflowr on 2018-06-18
For what it's worth when I copied the wget link and ran as a search I got results for ]http://ftp.**uk**.debian.org/debian/pool/main/n/netselect/
And not ]http://ftp.**gb**.debian.org/debian/pool/main/n/netselect/

I scoured [this listing]("https://www.debian.org/mirror/list") and did not find any mirror for the gb.debian particular name scheme.

That said, are you positive you're on 16.10, as already posted about?
i give the benefit of the doubt and assume it's a typo, and it's actually 16.04.
Which happens here all the time.

post back the results from the *sudo apt update* command.
That can clarify things all around.

Some random thoughts by me

---

### Post by mattcrust on 2018-06-18
OK thanks 
It is 16.04 my mistake soz- getting confused due to my desktop running 17.10
so when i run "sudo apt update" I get


```
Err:1 [http://repo.entroware.com/ubuntu](http://repo.entroware.com/ubuntu) xenial InRelease                        
  Could not connect to 130.159.183.75:9100 (130.159.183.75), connection timed out
Err:2 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial InRelease                     
  Could not connect to 130.159.183.75:9100 (130.159.183.75), connection timed out
Err:3 [http://ftp.ticklers.org/archive.ubuntu.org/ubuntu](http://ftp.ticklers.org/archive.ubuntu.org/ubuntu) xenial InRelease       
  Could not connect to 130.159.183.75:9100 (130.159.183.75), connection timed out
Err:4 [http://ftp.ticklers.org/archive.ubuntu.org/ubuntu](http://ftp.ticklers.org/archive.ubuntu.org/ubuntu) xenial-updates InRelease
  Unable to connect to 130.159.183.75:9100:
Err:5 [http://ftp.ticklers.org/archive.ubuntu.org/ubuntu](http://ftp.ticklers.org/archive.ubuntu.org/ubuntu) xenial-backports InRelease
  Unable to connect to 130.159.183.75:9100:
Err:6 [http://ftp.ticklers.org/archive.ubuntu.org/ubuntu](http://ftp.ticklers.org/archive.ubuntu.org/ubuntu) xenial-security InRelease
  Unable to connect to 130.159.183.75:9100:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up-to-date.
W: Target Packages (partner/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Packages (partner/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Packages (partner/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Translations (partner/i18n/Translation-en_GB) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Translations (partner/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target DEP-11 (partner/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target DEP-11-icons (partner/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Failed to fetch [http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/dists/xenial/InRelease](http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/dists/xenial/InRelease)  Could not connect to 130.159.183.75:9100 (130.159.183.75), connection timed out
W: Failed to fetch [http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/dists/xenial-updates/InRelease](http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/dists/xenial-updates/InRelease)  Unable to connect to 130.159.183.75:9100:
W: Failed to fetch [http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/dists/xenial-backports/InRelease](http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/dists/xenial-backports/InRelease)  Unable to connect to 130.159.183.75:9100:
W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/xenial/InRelease](http://archive.canonical.com/ubuntu/dists/xenial/InRelease)  Could not connect to 130.159.183.75:9100 (130.159.183.75), connection timed out
W: Failed to fetch [http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/dists/xenial-security/InRelease](http://ftp.ticklers.org/archive.ubuntu.org/ubuntu/dists/xenial-security/InRelease)  Unable to connect to 130.159.183.75:9100:
W: Failed to fetch [http://repo.entroware.com/ubuntu/dists/xenial/InRelease](http://repo.entroware.com/ubuntu/dists/xenial/InRelease)  Could not connect to 130.159.183.75:9100 (130.159.183.75), connection timed out
W: Some index files failed to download. They have been ignored, or old ones used instead.
W: Target Packages (partner/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Packages (partner/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Packages (partner/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Translations (partner/i18n/Translation-en_GB) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Translations (partner/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target DEP-11 (partner/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target DEP-11-icons (partner/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list.d/xenial-partner.list:4
```

Thanx

Matt

---

### Post by deadflowr on 2018-06-18
port 9100 seems weird to me.
Is this using a proxy, or something?

---

### Post by mattcrust on 2018-06-19
I Knaa, I think it maybe a printer port. I'm not sure why its trying to call up that port instead of whatever port the apt sits on.

---

### Post by mattcrust on 2018-06-19
Ok this is really weird whatever mirror address imanually try to get - using wget it still trys to connect to 130.159.183.75

---

### Post by mattcrust on 2018-06-19
So I discovered a file in /etc/apt/ directory called apt-conf which had text saying update to the proxy 130.etc etc. Should I remove this or just change the proxy address to the one I want to go to.

thx

Matt

---

### Post by mattcrust on 2018-06-19
Ok so I got it sorted as well as the apt-conf file which needed removed There was a line in /etc/environment.txt calling for proxy address which also neebded to be removed. Thanks for listening t my pish.

Matt

---

