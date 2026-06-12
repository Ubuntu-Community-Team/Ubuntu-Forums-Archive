---
title: "Lubuntu 13.04 &amp; Nexus 4. Files to copy to with their filenames intact."
date: 2013-08-04
forum: New to Ubuntu
---

### Post by Troy Barbas on 2013-08-04
[COLOR=#000000][FONT=Arial]I'm running Lubuntu 13.04 and the MTP device in question is a Google/LG Nexus 4.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]My computer is finding the phone with no problem and asks me what to do when I plug it in. I can browse the phone's storage and everything's there. However, if I drag files from it to my filesystem, the copied files and directories are all named with numbers instead of the names (I'm guessing these are the files' StorageIDs?), whereas the files are being rendered in Pcmanfm with their filenames.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Does anyone know of a way to get these files to copy to my filesystem with their filenames intact?[/FONT][/COLOR]

---

### Post by TheFu on 2013-08-04
Interesting.  I'm using a Nexus4 and Ubuntu 12.04 (actually server + LXDE) without that issue at all.  Are there any errors in log files?
Yep, just tested it again with pcmanfm; no funny file names going in either direction.  Perhaps a reinstall of the MTP driver or Pcmanfm is needed?

---

### Post by meilin on 2013-08-04
Ubuntu 13.04 and Nexus 4 works like a charm

---

### Post by Troy Barbas on 2013-08-04
I'm still facing this problem...any advice beside letting me know that it is working with your system.

Thanks.

---

### Post by TheFu on 2013-08-04
> **Troy Barbas said:**
> I'm still facing this problem...any advice beside letting me know that it is working with your system.

Thanks.

Pretty certain that I asked a question and made a suggestion. How did those turn out? Did you do them?

---

### Post by Troy Barbas on 2013-08-04
Sorry The Flu and thank you, yes I did follow your instruction and re-install libmtp-common, libmtp-runtime, libmtp9 & pcmanfm, without any success. Still transfer files from nexus as numbers, instead of filenames.

---

### Post by TheFu on 2013-08-05
> **Troy Barbas said:**
> Sorry The Flu and thank you, yes I did follow your instruction and re-install libmtp-common, libmtp-runtime, libmtp9 & pcmanfm, without any success. Still transfer files from nexus as numbers, instead of filenames.

Have you tried a different cable?  Sorry - that's the best idea I have ... besides installing 12.04 LTS.

---

### Post by Troy Barbas on 2013-08-06
@The Flu, I have tired it with another cable, and tested it with Lubuntu 13.04 live to see if it display the above issue, this it does. So I tried it with the 13.10 live and which copy the file name over properly.

I have installed the 13.10, but after installing the updates, the wifi icon disappeared from the panel bar...

---

### Post by TheFu on 2013-08-07
> **Troy Barbas said:**
> @The Flu, I have tired it with another cable, and tested it with Lubuntu 13.04 live to see if it display the above issue, this it does. So I tried it with the 13.10 live and which copy the file name over properly.

I have installed the 13.10, but after installing the updates, the wifi icon disappeared from the panel bar...

For all practical purposes, 13.04 is beta code and 13.10 is less than alpha level.  12.04?  I know that 12.04 works here - there is a PPA that must be added to get MTP working. 
Add these to your APT sources setup under 12.04:
```
deb http://ppa.launchpad.net/langdalepl/gvfs-mtp/ubuntu precise main
deb-src http://ppa.launchpad.net/langdalepl/gvfs-mtp/ubuntu precise main

```
Should work under a liveCD.

---

