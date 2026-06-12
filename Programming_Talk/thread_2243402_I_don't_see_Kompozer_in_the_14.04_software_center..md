---
title: "I don't see Kompozer in the 14.04 software center.  Is it still available?"
date: 2014-09-08
forum: Programming Talk
---

### Post by Tom_Carr on 2014-09-08
I don't see Kompozer in the 14.04 software center.  Is it still available?  How can I install it?
Kompozer is a great html editor.  Has something better replaced it?

---

### Post by nerdtron on 2014-09-08
It is not on the software center. Not familiar with any replacements though. But try this to install it.
[https://help.ubuntu.com/community/InstallKompozer](https://help.ubuntu.com/community/InstallKompozer)

---

### Post by Tom_Carr on 2014-09-08
Kompozer is no longer in the repos,  although you can install it.   Is there something better now avaliable?

---

### Post by slickymaster on 2014-09-08
Threads merged.

Please do not create duplicate threads, it dilutes community effort.

---

### Post by Tom_Carr on 2014-09-08
> [COLOR=#000000]Please do not create duplicate threads, it dilutes community effort.[/COLOR]

Thanks for pointing that out.  I won't do it again.  Where will the merged thread show up now, in both forums of just one?

---

### Post by slickymaster on 2014-09-08
> **Tom_Carr said:**
> Thanks for pointing that out.  I won't do it again.  Where will the merged thread show up now, in both forums of just one?

Just in this one. I merged the other one from the General Help sub-forum into this one.

---

### Post by Tom_Carr on 2014-09-08
I followed the instructions above and successfully installed Kompozer.  I don't really understand why it is no longer in the software ceneter, but I am glad it is still available.

One final question though - Is there something else better?   I tried Blue Fish but  it is not WYSIWYG.  I am not a professional.  I just manage a few simple web sites.  Is Kompozer still the best tool for me?

---

### Post by nerdtron on 2014-09-08
Not sure why it was removed from the software center. I'm not a web developer so I may not be familiar with other programs but I think Kompozer is the best among other WYSIWYG editors. It get's the job done for static web pages.

---

### Post by Tom_Carr on 2014-09-08
Thanks.  I'll close the thread now.

---

### Post by jbig1959 on 2014-09-26
Your help link worked for me. After upgrade to 14.04 I lost Kompozer, I used Synaptic package manager to find and try to install but It would crash whenever I used the program. I have to start Kompozer from teminal but that's fine because it is working. Thankx.

---

### Post by Tom_Carr on 2014-10-25
I just reopened this thread because I am having trouble installing kompozer.
I installed it successfully on another install of 14.04 using these instructions

[https://help.ubuntu.com/community/InstallKompozer](https://help.ubuntu.com/community/InstallKompozer)

but I just tried to install it again and the process hung
This is what is in the terminal -




tom@tom-Veriton-X275:~$ uname -a
Linux tom-Veriton-X275 3.13.0-37-generic #64-Ubuntu SMP Mon Sep 22 21:28:38 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
tom@tom-Veriton-X275:~$ sudo apt-get install libatk1.0-0 libc6 libcairo2 libfontconfig1 libfreetype6 libgdk-pixbuf2.0-0 libglib2.0-0 libgtk2.0-0  libidl0 libnspr4 libnss3 libpango1.0-0 libpng12-0 libstdc++6 libx11-6 libxft2 libxinerama1 libxrender1 libxt6 zlib1g
[sudo] password for tom: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libatk1.0-0 is already the newest version.
libcairo2 is already the newest version.
libgdk-pixbuf2.0-0 is already the newest version.
libglib2.0-0 is already the newest version.
libpng12-0 is already the newest version.
libstdc++6 is already the newest version.
libx11-6 is already the newest version.
libxft2 is already the newest version.
libxinerama1 is already the newest version.
libxrender1 is already the newest version.
libxt6 is already the newest version.
zlib1g is already the newest version.
libc6 is already the newest version.
libfontconfig1 is already the newest version.
libfreetype6 is already the newest version.
libgtk2.0-0 is already the newest version.
libnspr4 is already the newest version.
libnss3 is already the newest version.
libpango1.0-0 is already the newest version.
The following extra packages will be installed:
  libidl-common
The following NEW packages will be installed:
  libidl-common libidl0
0 upgraded, 2 newly installed, 0 to remove and 1 not upgraded.
Need to get 74.1 kB of archives.
After this operation, 337 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty/main libidl-common all 0.8.14-0.2ubuntu4 [8,196 B]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty/main libidl0 amd64 0.8.14-0.2ubuntu4 [65.9 kB]
Fetched 74.1 kB in 0s (141 kB/s)   
Selecting previously unselected package libidl-common.
(Reading database ... 195345 files and directories currently installed.)
Preparing to unpack .../libidl-common_0.8.14-0.2ubuntu4_all.deb ...
Unpacking libidl-common (0.8.14-0.2ubuntu4) ...
Selecting previously unselected package libidl0:amd64.
Preparing to unpack .../libidl0_0.8.14-0.2ubuntu4_amd64.deb ...
Unpacking libidl0:amd64 (0.8.14-0.2ubuntu4) ...
Setting up libidl-common (0.8.14-0.2ubuntu4) ...
Setting up libidl0:amd64 (0.8.14-0.2ubuntu4) ...
Processing triggers for libc-bin (2.19-0ubuntu6.3) ...
tom@tom-Veriton-X275:~$ wget [https://launchpad.net/ubuntu/+archive/primary/+files/kompozer-data_0.8%7Eb3.dfsg.1-0.1ubuntu2_all.deb](https://launchpad.net/ubuntu/+archive/primary/+files/kompozer-data_0.8%7Eb3.dfsg.1-0.1ubuntu2_all.deb)
--2014-10-25 11:11:26--  [https://launchpad.net/ubuntu/+archive/primary/+files/kompozer-data_0.8%7Eb3.dfsg.1-0.1ubuntu2_all.deb](https://launchpad.net/ubuntu/+archive/primary/+files/kompozer-data_0.8%7Eb3.dfsg.1-0.1ubuntu2_all.deb)
Resolving launchpad.net (launchpad.net)... 91.189.89.222, 91.189.89.223
Connecting to launchpad.net (launchpad.net)|91.189.89.222|:443... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: [https://launchpadlibrarian.net/102977237/kompozer-data_0.8%7Eb3.dfsg.1-0.1ubuntu2_all.deb](https://launchpadlibrarian.net/102977237/kompozer-data_0.8%7Eb3.dfsg.1-0.1ubuntu2_all.deb) [following]
--2014-10-25 11:11:27--  [https://launchpadlibrarian.net/102977237/kompozer-data_0.8%7Eb3.dfsg.1-0.1ubuntu2_all.deb](https://launchpadlibrarian.net/102977237/kompozer-data_0.8%7Eb3.dfsg.1-0.1ubuntu2_all.deb)
Resolving launchpadlibrarian.net (launchpadlibrarian.net)... 91.189.89.228, 91.189.89.229
Connecting to launchpadlibrarian.net (launchpadlibrarian.net)|91.189.89.228|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2145516 (2.0M) [application/x-debian-package]
Saving to: &#8216;kompozer-data_0.8~b3.dfsg.1-0.1ubuntu2_all.deb&#8217;


100%[======================================>] 2,145,516    603KB/s   in 3.8s   


2014-10-25 11:11:31 (548 KB/s) - &#8216;kompozer-data_0.8~b3.dfsg.1-0.1ubuntu2_all.deb&#8217; saved [2145516/2145516]


tom@tom-Veriton-X275:~$ wget [https://launchpad.net/ubuntu/+archive/primary/+files/kompozer_0.8%7Eb3.dfsg.1-0.1ubuntu2_amd64.deb](https://launchpad.net/ubuntu/+archive/primary/+files/kompozer_0.8%7Eb3.dfsg.1-0.1ubuntu2_amd64.deb)
--2014-10-25 11:11:31--  [https://launchpad.net/ubuntu/+archive/primary/+files/kompozer_0.8%7Eb3.dfsg.1-0.1ubuntu2_amd64.deb](https://launchpad.net/ubuntu/+archive/primary/+files/kompozer_0.8%7Eb3.dfsg.1-0.1ubuntu2_amd64.deb)
Resolving launchpad.net (launchpad.net)... 91.189.89.223, 91.189.89.222
Connecting to launchpad.net (launchpad.net)|91.189.89.223|:443... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: [https://launchpadlibrarian.net/102976096/kompozer_0.8%7Eb3.dfsg.1-0.1ubuntu2_amd64.deb](https://launchpadlibrarian.net/102976096/kompozer_0.8%7Eb3.dfsg.1-0.1ubuntu2_amd64.deb) [following]
--2014-10-25 11:11:32--  [https://launchpadlibrarian.net/102976096/kompozer_0.8%7Eb3.dfsg.1-0.1ubuntu2_amd64.deb](https://launchpadlibrarian.net/102976096/kompozer_0.8%7Eb3.dfsg.1-0.1ubuntu2_amd64.deb)
Resolving launchpadlibrarian.net (launchpadlibrarian.net)... 91.189.89.228, 91.189.89.229
Connecting to launchpadlibrarian.net (launchpadlibrarian.net)|91.189.89.228|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 7858708 (7.5M) [application/x-debian-package]
Saving to: &#8216;kompozer_0.8~b3.dfsg.1-0.1ubuntu2_amd64.deb&#8217;


100%[======================================>] 7,858,708   1.30MB/s   in 6.9s   


2014-10-25 11:11:39 (1.08 MB/s) - &#8216;kompozer_0.8~b3.dfsg.1-0.1ubuntu2_amd64.deb&#8217; saved [7858708/7858708]


tom@tom-Veriton-X275:~$ sudo dpkg -i kompozer-data_0.8~b3.dfsg.1-0.1ubuntu2_all.deb
Selecting previously unselected package kompozer-data.
(Reading database ... 195361 files and directories currently installed.)
Preparing to unpack kompozer-data_0.8~b3.dfsg.1-0.1ubuntu2_all.deb ...
Unpacking kompozer-data (1:0.8~b3.dfsg.1-0.1ubuntu2) ...
Setting up kompozer-data (1:0.8~b3.dfsg.1-0.1ubuntu2) ...
tom@tom-Veriton-X275:~$ sudo dpkg -i kompozer-data_0.8~b3.dfsg.1-0.1ubuntu2_all.deb

---

### Post by Tom_Carr on 2014-10-27
I tried it again and it worked, so no problem now.

---

### Post by Scunizi on 2015-02-24
If it doesn't load like my instlall didn't, you may still need to get kompozer-data.. a different .deb.  [It's available here]("https://packages.debian.org/squeeze/all/kompozer-data/download").  One other tid-bit missed is after downloading the .deb's for install you must add permissions for executing the file with dpkg.  sudo chmod +x [filename.deb]

---

