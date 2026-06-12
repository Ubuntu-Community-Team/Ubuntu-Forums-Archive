---
title: "Widescreen Resolution Problems"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by sadpony on 2008-10-29
I am really new to Linux and I was wondering how to get a widescreen resolution option for my monitor. Here are my specs:

Monitor: Samsung Sync Master 226 BW
Video Adapter: Nvidia Geforce 9800 GTX+

I am running 64bit also. 

I have read some things that tell you to edit the /etc/x11/xorg.conf file but if I got to edit it, I cannot save the changes. Is there something I am doing wrong? Currently the file has only generic info, not specific devices.

---

### Post by SteveLefty on 2008-10-29
If you're going to edit the xorg.conf file, you need root access.  Open a terminal and type:
"sudo gedit /etc/x11/xorg.conf"

It will ask for your password, which you type in and hit return.  You will then be able to edit this file under gedit.  HOWEVER!!  I highly suggest backing this file up before making any changes to it.  You can do this by:

"sudo cp /etc/x11/xorg.conf ~/xorg.conf.backup"

This will copy the file to your home directory as "xorg.conf.backup".  In case you run into any issues and aren't able to boot, you can just copy this backup the same way except this time from your home directory and replace the original in /etc/x11/

---

### Post by sadpony on 2008-10-29
got it working, thank you

---

