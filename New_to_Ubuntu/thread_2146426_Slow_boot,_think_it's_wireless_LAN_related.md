---
title: "Slow boot, think it's wireless LAN related"
date: 2013-05-18
forum: New to Ubuntu
---

### Post by jonnymopar on 2013-05-18
I wiped my extra laptop clean, then installed Ubuntu 12.04 with Cinnamon over it.  Its running great... after it boots up.  It's taking over 2 minutes to completely boot.  Most of the time is at the empty black screen.  There seems to be no hard drive activity during this period.  All of a sudden, the hard drive light comes back on, and into Cinnamon we go.

The reason that I think it may be something to do with the wireless (or network managment in general) is because when Cinnamon first appears, there is no network connectivity at all, wireless or hard-wired.  Going into Network properties, it gives me an error "not compatible with this version".  If you wait at the desktop for about another minute, all of a sudden the wireless starts working and all is well.  Once the wireless starts working, there is no error message going into Network properties (although it defaults to Airplane Mode every time, which I've never seen before).

I'm sure there's some kind of log file that I can rifle through trying to find where it's stopping.  Can anybody help me out as far as where that might be?

Thanks.

---

### Post by fantab on 2013-05-18
You can disable Ubuntu splash at boot and it will show you all the text that goes on behind that purple screen; here's how:

sudo gedit /etc/default/grub

In the file that opens search for, GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" and remove "quite splash" just leave "" after =. Save the file and,

sudo update-grub

Reboot. Follow the text and see what goes on. Later you can add "quiet splash" to get back the Purple Ubuntu splash.

As for Log files check /etc/var/log there will be log files which could give you pointers.

---

### Post by jonnymopar on 2013-05-21
Got fed up, wiped it out completely and started fresh.  No problems now.  The only difference is when I installed it this time, I used the wireless as my internet connection during installation.  It might be a coincidence, but when I was having problems, I had use hardwired ethernet during installation.  Again, could be coincidence.  Still very much learning about this stuff.

As a random note: either Cinnamon doesn't like gdm, or gdm doesn't like me.  I ran into problems twice in a row using gdm with Cinnamon.  lighdm to the rescue!

---

### Post by fantab on 2013-05-22
Ubuntu has 'lightdm' as its default display manager. How did you end up with GDM?

---

### Post by Bucky Ball on 2013-05-22
> **fantab said:**
> You can disable Ubuntu splash at boot and it will show you all the text that goes on behind that purple screen; here's how:

sudo gedit /etc/default/grub

In the file that opens search for, GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" and remove "quite splash" just leave "" after =. Save the file and,

sudo update-grub

Reboot. Follow the text and see what goes on. Later you can add "quiet splash" to get back the Purple Ubuntu splash.

As for Log files check /etc/var/log there will be log files which could give you pointers.

Long way around. ;) Booting to the recovery kernel (second on the list) will give you the messages and a chance to fix the problem. Also, immediately after booting and getting to the desktop, open a terminal and:

```
dmesg
``` 

Look for anything suspicious in there.

---

### Post by Tjkhan on 2013-05-22
If u have time, can u reinstall the OS?

---

### Post by Bucky Ball on 2013-05-22
> **Tjkhan said:**
> If u have time, can u reinstall the OS?

ALWAYS last resort and no point going there ... yet. Why would you when the machine is working fine apart from a slow boot? If you have the time, don't waste it. Check the recovery boot and dmesg first. Your machine is actually working fine when you get to the desktop so the issue is in the boot process somewhere. A matter of finding it. A reinstall would probably replicate this same problem if you are installing identical software to what you have now. 

Save some time and try fix this issue. ;)

* This may be specific to your hardware configuration and something you should know about anyway to avoid future and present issues, which you won't unless you track it down. ;)

---

### Post by the8thstar on 2013-05-22
> **Bucky Ball said:**
> Long way around. ;) Booting to the recovery kernel (second on the list) will give you the messages and a chance to fix the problem. Also, immediately after booting and getting to the desktop, open a terminal and:

```
dmesg
``` 

Look for anything suspicious in there.

+1 on this. It's the easiest way to diagnose what's going on with your system.

---

