---
title: "fn brightness keys doesn't work - Nvidia driver"
date: 2012-12-23
forum: New to Ubuntu
---

### Post by morphyrichards on 2012-12-23
Hi there,

I just installed most recent version of nvidia drivers 304.64 which (probably) caused my brightness fn keys to stop working.
Other fn keys are fine. I have did some searching but none of proposed solutions worked for me.

I'm using S Vaio vgn-fz31z, system version is 12.10. The fn keys are "communicating with the system" so nothing is broken.

Thanks in advance!

---

### Post by Pjotr123 on 2012-12-23
You could use the terminal:
[https://sites.google.com/site/easylinuxtipsproject/display#TOC-Brightness-of-the-display-is-wrong-and-not-adjustable](https://sites.google.com/site/easylinuxtipsproject/display#TOC-Brightness-of-the-display-is-wrong-and-not-adjustable)
(item 2.5, right column)

---

### Post by morphyrichards on 2012-12-23
I just tried that: entered everything in console, however with no response: I can get the BUS id but I cannot change the brightness.

---

### Post by NikTh on 2012-12-23
Hi ,
lets try some parameters. 

Open a terminal and apply this command ```
gksudo gedit /etc/default/grub
```

Scroll down and find the line 
> GRUB_CMDLINE_LINUX_DEFAULT= "quiet splash"
now modify the line and add the parameter **acpi_osi=** 
The line now should be exactly like this > **GRUB_CMDLINE_LINUX_DEFAULT= "quiet splash acpi_osi="**
Save the document and now run in terminal ```
sudo update-grub
``` 
Reboot your system and check again the Fn (for brightness) keys.

Thanks

---

### Post by morphyrichards on 2012-12-23
NikTh: You, sir, are awesome! Thank you for that!

I have previously tried various changes within the same file but only this one proved successful.

I'll just take advantage of an open post and ask one quick question:
When I start the system, once it is fully booted (desktop visible, etc.) it takes an awful long time to start up Thunar 1.4.0 (about 40 seconds from the keystroke), afterwards everything opens smoothly. How can I fix that?

---

### Post by NikTh on 2012-12-23
> **morphyrichards said:**
> 

I'll just take advantage of an open post and ask one quick question:
When I start the system, once it is fully booted (desktop visible, etc.) it takes an awful long time to start up Thunar 1.4.0 (about 40 seconds from the keystroke), afterwards everything opens smoothly. How can I fix that?

Try this workaround 

Open this file ```
gksudo gedit /usr/share/gvfs/mounts/network.mount
```and change the > AutoMount=true to > AutoMount=**false**See now if Thunar opens faster.

**Be aware that this is not a solution , is just a workaround. The delay now will show up when you click the "Network" tab on the left sidebar . But if you not using the "Network" tab, this workaround can be a good standing.**

Thanks

---

### Post by morphyrichards on 2012-12-24
It worked again! Now Thunar opens instantaneous. 

Thank you sir.

---

### Post by ucracker on 2013-01-05
Worked like a charm on Asus K55VM with Linux Mint 14 Cinnamon.


By the way, for those who are searching for a solution for the FN keys to work on K55V's, take the risk to change to Linux Mint 14 Cinnamon.
You won't regret it ;)

---

### Post by rafaelhsn on 2013-01-24
> **NikTh said:**
> Hi ,
lets try some parameters. 

Open a terminal and apply this command ```
gksudo gedit /etc/default/grub
```

Scroll down and find the line 

now modify the line and add the parameter **acpi_osi=** 
The line now should be exactly like this 
Save the document and now run in terminal ```
sudo update-grub
``` 
Reboot your system and check again the Fn (for brightness) keys.

Thanks

Hi! Thanks a lot, it worked with the tips above, but with this change I have a little bug here, after reboot the browser chromium starts with a very small size and cannot be maximized (just on first open) , it stay like that, i have to close it and open again then it restore to normal size.

like that: [https://www.dropbox.com/s/v0dy33kc1f54slt/screen.png](https://www.dropbox.com/s/v0dy33kc1f54slt/screen.png)

Do you or someone have an idea what could be that?

Thanks!

---

### Post by ucracker on 2013-01-24
instead of using chromium, try using chrome ;)

---

### Post by rafaelhsn on 2013-01-25
> **ucracker said:**
> instead of using chromium, try using chrome ;)

Hi

I Just fixed it using the command -start-maximized on shortcut =)

Thaks a lot for your help!

---

### Post by asadullah on 2013-02-07
Thanks the first post worked on a  		 					        					 						 						 						 						**NV57H50u **

---

### Post by gatuki on 2013-05-03
Hi, I've got the same problem with my ASUS S200E running Linux Mint 14,  everything works except for the Brightness function keys F5 and F6. When  I type "sudo gedit /etc/default/grub" into the Terminal an empty window  opens with "grub (/etc/default) - gedit" written at the top. There's _no_  text to edit whatsoever.
Do you know whether there's something I need to install first?
I'm grateful for any help!

---

### Post by Toz on 2013-05-03
> **gatuki said:**
> Hi, I've got the same problem with my ASUS S200E running Linux Mint 14,  everything works except for the Brightness function keys F5 and F6. When  I type "sudo gedit /etc/default/grub" into the Terminal an empty window  opens with "grub (/etc/default) - gedit" written at the top. There's _no_  text to edit whatsoever.
Do you know whether there's something I need to install first?
I'm grateful for any help!

Thats interesting. What does the following return:
```
ls -l /etc/default
```
Since gedit is a graphical app, you should also probably use **gksu** instead of sudo, so:
```
gksu gedit /etc/default/grub
```

Of interest would also be the video card that you have:
```
sudo lspci -vnn | grep -A12 VGA
```

What version of ubuntu is Linux Mint 14 based on?

---

### Post by gatuki on 2013-05-24
Thanks for your reply Toz, I've only just noticed it. Been too busy moving house over the last few weeks....

I'm  an absolute newbee to linux and when I first posted here I didn't even  notice that I should be a different forum i.e. linux mint forum.
As far as I've found out Linux Mint 14 is based on Ubuntu 12.10
It  doesn't bother me too much that the brightness function keys don't  work, because I've installed the brightness applet on my taskbar. It  would just be nice if it worked 

So   "ls -l /etc/default" gives me the following: 

total 140
-rw-r--r-- 1 root root  346 Jun  7  2012 acpid
-rw-r--r-- 1 root root 4922 Oct  9  2012 acpi-support
-rw-r--r-- 1 root root  160 Feb  2  2007 add-apt-key
-rw-r--r-- 1 root root  638 May 24 02:45 alsa
-rw-r--r-- 1 root root  290 May  1  2012 anacron
-rw-r--r-- 1 root root  219 Jun  4  2012 avahi-daemon
-rw-r--r-- 1 root root   47 Jul 21  2012 bootlogd
-rw-r--r-- 1 root root  608 Sep 10  2012 brltty
-rw-r--r-- 1 root root  222 May 22  2012 bsdmainutils
-rw------- 1 root root  384 Jul 30  2012 cacerts
-rw-r--r-- 1 root root 2025 Oct 17  2012 console-setup
-rw-r--r-- 1 root root  549 Jan 24  2012 crda
-rw-r--r-- 1 root root  183 Jun 14  2012 cron
-rw-r--r-- 1 root root  122 Jul 28  2012 cups
-rw-r--r-- 1 root root  297 Jul 23  2012 dbus
-rw-r--r-- 1 root root   92 Jul 21  2012 devpts
-rw-r--r-- 1 root root   86 Jul 21  2012 halt
-rw-r--r-- 1 root root 1226 Oct 18  2012 hddtemp
-rw-r--r-- 1 root root  126 Oct 17  2012 irqbalance
-rw-r--r-- 1 root root   84 Jul 20  2012 kerneloops
-rw-r--r-- 1 root root  559 May 24 01:21 keyboard
-rw-r--r-- 1 root root  250 May 24 01:49 locale
-rw-r--r-- 1 root root 1756 Oct  4  2012 nss
-rw-r--r-- 1 root root   48 Oct 17  2012 ntfs-3g
-rw-r--r-- 1 root root  456 Oct 26  2011 ntpdate
-rw-r--r-- 1 root root   64 Oct  4  2012 pulseaudio
-rw-r--r-- 1 root root  685 May 24 01:24 rcS
-rw-r--r-- 1 root root 1768 Jul 20  2012 rsync
-rw-r--r-- 1 root root  321 Mar 30  2012 rsyslog
-rw-r--r-- 1 root root  258 Nov  4  2012 samba
-rw-r--r-- 1 root root  146 Oct 17  2012 saned
-rw-r--r-- 1 root root  132 Jun 19  2012 speech-dispatcher
-rw-r--r-- 1 root root 1754 Sep 24  2012 ufw
-rw-r--r-- 1 root root 1118 Sep  6  2012 useradd



"gksu gedit /etc/default/grub" just opens the same blank page.

And "sudo lspci -vnn | grep -A12 VGA" shows the following video card:


00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09) (prog-if 00 [VGA controller])
    Subsystem: ASUSTeK Computer Inc. Device [1043:108d]
    Flags: bus master, fast devsel, latency 0, IRQ 43
    Memory at f7800000 (64-bit, non-prefetchable) [size=4M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at f000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [d0] Power Management version 2
    Capabilities: [a4] PCI Advanced Features
    Kernel driver in use: i915
    Kernel modules: i915


If you have any idea of what I could try I'd give it a go, but as I said, I can live without it.
And I don't want to be a bother to anyone, especially since I'm in the wrong forum!
I shall give Ubuntu a try one of these days, maybe It will work there...

---

### Post by gatuki on 2013-05-24
I've just found out that there's a newer version of Mint and I want to try Ubuntu as well, so I'm not going to mess around with the (tiny) problem any more. 
I'll see if it all works and otherwise come back to this post.
Thanks anyway!!

---

