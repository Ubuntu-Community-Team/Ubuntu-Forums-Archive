---
title: "Installing teamviewer on Ubuntu 12.04 LTS 64bit"
date: 2013-06-15
forum: New to Ubuntu
---

### Post by sadiqkhoja on 2013-06-15
Environment: Ubuntu 12.04 LTS 64bit
Problem: Unable to install teamviewer; error: cannot install lib32asound2

Tried: sudo get-apt install lib32asound2
lib32asound2 : Depends: libc6-i386 (>= 2.7) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

then tried: sudo get-apt install libc6-i386
libc6-i386 : Depends: libc6 (= 2.15-0ubuntu10.2) but 2.15-0ubuntu10.3 is to be installed
E: Unable to correct problems, you have held broken packages.

then tried: sudo get-apt install libc6
libc6 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

what to do know? it driving me crazy. please help

---

### Post by zombifier25 on 2013-06-15
Run these commands one at a time and see if the problem is fixed:
```
sudo apt-get install -f
sudo dpkg --configure -a
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by NikTh on 2013-06-15
[FONT=tahoma][SIZE=3][You have to know that teamviewer is not FOSS]("http://en.wikipedia.org/wiki/Free_and_open-source_software")
[/SIZE][/FONT]
Remove any existing instance of teamviewer from your PC. 

Then download teamviewer 8 (newest version) from [here]("http://www.teamviewer.com/en/download/linux.aspx")

Download the appropriate architecture (64bit) .deb package. 

Connect to Downloads folder and install it with dpkg 

```
cd Downloads 
sudo dpkg -i teamviewer_linux_x64.deb
``` 

Probably it will throw a bunch of errors, then run 
```
sudo apt-get install -f
``` to correct these errors. 

If not succeed, post back full results of above commands. 

Thanks

---

### Post by sadiqkhoja on 2013-06-15
same issue:

sadiq@sadiq-linux:/Data1/Software$ sudo dpkg --force-depends -i teamviewer_linux_x64.deb
Selecting previously unselected package teamviewer.
(Reading database ... 175552 files and directories currently installed.)
Unpacking teamviewer (from teamviewer_linux_x64.deb) ...
dpkg: teamviewer: dependency problems, but configuring anyway as you requested:
 teamviewer depends on libc6-i386 (>= 2.4); however:
  Package libc6-i386 is not installed.
 teamviewer depends on lib32asound2; however:
  Package lib32asound2 is not installed.
 teamviewer depends on lib32z1; however:
  Package lib32z1 is not installed.
 teamviewer depends on ia32-libs; however:
  Package ia32-libs is not installed.
Setting up teamviewer (8.0.17147) ...
initctl: Job failed to start

---

### Post by NikTh on 2013-06-16
Have you ran after dpkg , the ```
sudo apt-get install -f
``` command ? 

I recently installed this tool in 12.04.2 LTS and I've had the same problems, but above command correct them. A bunch of :i386 packages will be installed in your system, but that's the way. 

First be sure that you have completely removed the old-corrupted teamviewer installation

```
sudo dpkg -P [COLOR=#000000]teamviewer_linux_x64.deb
``` [/COLOR]

Thanks

---

### Post by superduper2 on 2013-10-22
I understand that this thread is now a couple of months old however it always helps if the OP responds as to whether or not the information given by the respondant solved the issue in question.

Thankyou very much NikTH - I was looking for this information in Google and came across your posts in regard to this matter - worked perfectly for me by following your instructions - cheers.

Tested and working on Wubi install of Ubuntu 12.04 LTS w/ Windows 7 Home Premium 64 bit using Teamviewer deb v8.0.20931 downloaded through the link provided in post #3

Note: Run commands exactly how NikTH has provided them - I typed a lower case d for Dowloads and therefore as Linux is           specific with Directory naming I got the error about no such directory - I then used upper case D for cd 
          (change directory) Downloads without issue.

          Also NikTH is correct in saying that Teamviewer is not open source however it IS free for non commercial users. I         am sure that there are better/ faster tools out there to accomplish the same task but IMO Teamviewer's ease of
          use is a winner - ie: bypass Firewall restrictions etc etc..... 

Thanks very much for the install info again NikTH.

---

### Post by msilahi.82 on 2013-11-27
Hi,

I have Ubuntu 13.10

When I try to install dependencies after typing sudo apt-get install -f, it just uninstalls teamviewer.

here is the output

dpkg -i teamviewer_linux_x64.deb 
Selecting previously unselected package teamviewer.
(Reading database ... 197918 files and directories currently installed.)
Unpacking teamviewer (from teamviewer_linux_x64.deb) ...
dpkg: dependency problems prevent configuration of teamviewer:
 teamviewer depends on lib32asound2; however:
  Package lib32asound2 is not installed.
 teamviewer depends on lib32z1; however:
  Package lib32z1 is not installed.
 teamviewer depends on ia32-libs; however:
  Package ia32-libs is not installed.

dpkg: error processing teamviewer (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 teamviewer



apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libc6-i386 linux-image-generic
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  teamviewer
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 81.9 MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 198146 files and directories currently installed.)
Removing teamviewer ...


I have also added Wine package

What am I doing wrong?





Regards,
Sheharyar

---

### Post by erazor84 on 2013-11-27
I got the same error on my 64bit Ubuntu 13.10. But i managed to install TeamViewer as 32Bit Version! The only function, that will not work is the autostart. But with the 32bit .deb package, it will install perfectly. sorry about my bad english ;)

---

### Post by monkeybrain20122 on 2013-11-27
[http://askubuntu.com/questions/362951/teamviewer-dependends-of-lib32asound2](http://askubuntu.com/questions/362951/teamviewer-dependends-of-lib32asound2)

---

### Post by monkeybrain20122 on 2013-11-27
There is a Chrome addon which does similarly things.
[http://www.tejasbarot.com/2013/08/15/howtolinux-desktop-sharing-with-google-chrome-browser/](http://www.tejasbarot.com/2013/08/15/howtolinux-desktop-sharing-with-google-chrome-browser/)

---

### Post by msilahi.82 on 2013-12-06
> **monkeybrain20122 said:**
> [http://askubuntu.com/questions/362951/teamviewer-dependends-of-lib32asound2](http://askubuntu.com/questions/362951/teamviewer-dependends-of-lib32asound2)


I am still getting the same error which I pasted earlier :)

Now I am using teamviewer on Wine

---

### Post by howefield on 2013-12-06
> **msilahi.82 said:**
> What am I doing wrong?

Use the 32-Bit / Multiarch version.

---

### Post by msilahi.82 on 2013-12-10
ah, 32-bit worked. 

Thanks again.

---

