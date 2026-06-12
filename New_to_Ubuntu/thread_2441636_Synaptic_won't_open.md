---
title: "Synaptic won't open"
date: 2020-04-25
forum: New to Ubuntu
---

### Post by eipapp on 2020-04-25
I'm currently running Ubuntu 20.04. I installed WPS office but kept getting a message to upgrade which I did through the WPS download page.
Now I'm getting the message " E: wps-office needs to be reinstalled, but I can't find an archive for it"
when I try to open Synaptic package manager I keep getting this message and Synaptic won't open for me to do a complete removal of WPS.
What can I do to get my Synaptic back ?

Thanks,
Bruce

---

### Post by speartip on 2020-04-25
WPS is downloaded as a .deb package. It seems that it's not fully installed or removed. Try
```
sudo apt remove wps*
```
followed by:
```
sudo apt autoremove
```
If it throws out any errors, post them back here.

ps. You can't upgrade a program you have downloaded from the internet. You need to uninstall the old one & install the new one.

---

### Post by eipapp on 2020-04-25
Hopefully I grabbed the correct image.

---

### Post by speartip on 2020-04-25
OK. Try reinstalling WPS this way.
First of all install gdebi-core in a terminal.
Then go into the directory where your WPS .deb is. Open a terminal within that directory and run:
```
sudo gdebi wps-office*
```
That should reinstall it. Again if any issues, post back the errors.

---

### Post by eipapp on 2020-04-25
Sorry but I couldn't get gdebi-core to work. 
It apparently is looking for a destination file ???
This is read out from terminal:
**install: missing destination file operand after 'gdebi-core'**
**Try 'install --help' for more information.**

---

### Post by speartip on 2020-04-25
You have updated your apt cache after installation i assume. What does the following do:
```
sudo apt update && sudo apt install gdebi-core
```

---

### Post by eipapp on 2020-04-25
This is the out put from command line you sent me.

Get:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal InRelease [265 kB]
Hit:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security InRelease               
Hit:3 [https://deb.trendtechcn.com](https://deb.trendtechcn.com) stable InRelease                             
Get:4 [https://mega.nz/linux/MEGAsync/xUbuntu_19.10](https://mega.nz/linux/MEGAsync/xUbuntu_19.10) ./ InRelease [2,468 B]      
Get:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-updates InRelease [89.1 kB]
Hit:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-backports InRelease
Get:7 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-updates/main amd64 Packages [2,004 B]
Get:8 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-updates/main i386 Packages [648 B]
Fetched 359 kB in 2s (198 kB/s) 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
1 package can be upgraded. Run 'apt list --upgradable' to see it.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package wps-office needs to be reinstalled, but I can't find an archive for it.

---

### Post by CelticWarrior on 2020-04-25
@speartip

Apparently you don't know as much as you think you do. Your suggestions are mostly wrong and ineffective. Namely:

[LIST]
[*]The suggestion for removing and reinstalling WPS is OK although I suspect there's a lot more to it (I'll comment about that later on) but the command 'sudo apt remove wps*' doesn't work. APT doesn't support wildcards so we need to use the "old" 'apt-get' for that -> ```
sudo apt-get remove --purge wps*
```
[*]Why suggest 'apt autoremove'? it does nothing in this case.
[*]No need to install (another one) APT frontend - GDebi -. You may like it but in this case suggesting the installation of additional software can only increase the problem. When APT has issues that need to be solved by reinstalling some package, one uses DPKG!
[/LIST]

@eipapp

Considering the above comments I strongly suggest you ignore those suggestions altogether for the moment.
Now, first of all, please understand that WPS can be installed in several different ways - snap, flatpak or deb - and we need to know HOW did you install it the first time. The typical way now is via snap. If you downloaded and tried to install the .deb file from wps-community then I'm afraid you've made a nasty mess.

Assuming you downloaded the latest deb from wps-community you should have the 'wps-office_11.1.0.9505.XA_amd64.deb' file. If not then please download it again. Then cd into the directory where that file is and run (assuming it's in the Downloads directory, change as appropriate):
```
cd Downloads
sudo dpkg -i wps-office_11.1.0.9505.XA_amd64.deb
```
and post the full error messages, if any, by copying from the terminal (mouse select > right-click > Copy) and paste it here in code tags (Go advanced > click "#" and paste inside), do NOT post screenshots of commands, please.

If it installs successfully then do: ```
sudo apt update && sudo apt full-upgrade
```
again noting down any eventual error messages. If everything goes according to the plan, the worse case scenario will be having a duplicated WPS, two different versions, one snap and one "apt". You can later uninstall one if you want.

If any other problem meanwhile, we troubleshoot from there.

---

### Post by eipapp on 2020-04-25
Initially I downloaded from the software center, WPS office suite which I believe was version 10.x
Every time I ran it though, I kept getting a message to install the latest version.
Believing that it was not available in the software center, I then went to the WPS web to install version 11.x

Below is out put from sudo apt-get remove --purge wps*

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package wps-office needs to be reinstalled, but I can't find an archive for it.

I didn't go beyond this as it seemed futile.

---

### Post by CelticWarrior on 2020-04-25
> **eipapp said:**
> Initially I downloaded from the software center, WPS office suite which I believe was version 10.x
Every time I ran it though, I kept getting a message to install the latest version.
Believing that it was not available in the software center, I then went to the WPS web to install version 11.x

Below is out put from sudo apt-get remove --purge wps*

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package wps-office needs to be reinstalled, but I can't find an archive for it.

I didn't go beyond this as it seemed futile.


The corrected command was mainly for educating the other user, it is NOT what I'd do in your situation.
Please try what I recommended and keep us posted. And, again, **please use code tags**, thank you.

---

### Post by eipapp on 2020-04-25
OK, that did it, problem solved.
Thank You,

Bruce

---

### Post by CelticWarrior on 2020-04-25
> **eipapp said:**
> OK, that did it, problem solved.
Thank You,

Bruce

Nice :D

Please use the thread tool to mark it solved. Thank you.

---

