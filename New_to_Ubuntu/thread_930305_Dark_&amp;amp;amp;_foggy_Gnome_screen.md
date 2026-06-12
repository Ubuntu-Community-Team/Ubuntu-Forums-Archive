---
title: "Dark &amp;amp;amp; foggy Gnome screen"
date: 2008-09-25
forum: New to Ubuntu
---

### Post by iClouseau88 on 2008-09-25
Hello everyone,

Please help me.  I am using a Toshiba Satellite pro 4600 laptop dual-boot XP Pro-Ubuntu Hardy 8.04 with Gnome 2.22.3 and linux kernel 2.6.24-19 generic.  The Windows display is normal, but Gnome display is unusual in the following sense:

The Welcome screen has blue and green colour instead of the usual orange-brown colour

The screen is quite dark and foggy.  It has always been bright and readable until now.

I am running this laptop on household current, not on battery.

Could you show me how to get my Gnome display back to normal as before?

Thank you kindly for your help.

:confused:

---

### Post by iClouseau88 on 2008-09-25
Hello again,

Some progress: Restarted and chose Recovery module of 2.6.24-19 kernel.  Then selected Repair Xserver, then Resume normal booting.

Now I got everything almost back to what I used to have, except that the screen resolution is only 800x600 (i.e., smaller bright display on a dark background).  

How should I get screen resolution back to 1024x768?  I can't do it using System > Preferences > Appearance.

iClouseau88

---

### Post by NullHead on 2008-09-26
Make sure your video driver is installed.

---

### Post by iClouseau88 on 2008-09-26
PROBLEM SOLVED:

sudo displayconfig-gtk

Select generic VESA driver, OK

Log out.  Log back in: sudo displayconfig-gtk

Screen tab: Model LCD Panel 1024x768

Resolution button: 1024x768

Log out and log back in.

It appears that the problem is due to Bug #185440 in xserver-xorg which is in kernel 2.6.24-19.  Has this been resolved in newer kernel?  Although I update Ubuntu routinely, it appears I still have to put up with this kernel.

---

### Post by NullHead on 2008-09-26
I believe theres a *.21 kernel you can use instead of the *.19 one. 

> jon@jon-laptop:~$ uname -r
2.6.24-21-generic
jon@jon-laptop:~$

---

### Post by iClouseau88 on 2008-09-27
Hi,

I found that linux-image 2.6.24-21 has not been installed even though linux-headers was, so I installed the former.  Now, when i rebooted there's no sound at all!  There's a red X next to the speaker icon and the error message is: "No volume control GStreamer plugin and/or devices found".

Here's the ouput of my terminal:

$ lshw -C sound
WARNING: you should run this program as super-user.
  *-multimedia UNCLAIMED  
       description: Multimedia audio controller
       product: 82801BA/BAM AC'97 Audio Controller
       vendor: Intel Corporation
       physical id: 1f.5
       bus info: pci@0000:00:1f.5
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: latency=0

What should I do to get sound back?

---

### Post by iClouseau88 on 2008-09-27
Update:

I tried "sudo apt-get install linux-backports-modules-generic".  Backport modules not detected, so installed and rebooted but still no sound.

So, I went back to 2.6.24-19 generic and got the soundback.

I am still interested in a long term solution but this will do for now, perhaps until Ubuntu 8.10!

---

