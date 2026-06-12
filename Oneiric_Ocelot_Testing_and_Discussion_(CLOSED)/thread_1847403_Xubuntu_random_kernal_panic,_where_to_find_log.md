---
title: "Xubuntu: random kernal panic, where to find log?"
date: 2011-09-20
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by keithpeter on 2011-09-20
Hello All

Beta 1 Xubuntu installed, updated and dist-upgraded to kernel 3.0.0.11 on an EeePC 1000 with 8Gb ssd for operating system and 30Gb home, I deleted the dotfiles from the home partition from the previous 10.04 installation. All going fine, a few crash notifications on startup. Installed xubuntu-restricted-extras and I'm running the dropbox daemon.

Had a kernel panic and left with a text screen with frozen mouse over the top. I was moving the mouse over a rather busy web page, powertop was running in a terminal.

If this happens again, where would I be able to find any logs &c? Not reproducible in an obvious way.

Any other Xubuntu issues that I can reproduce in the final stages of testing?

---

### Post by decoherence on 2011-09-20
If it was able to sync the disk before dying, you might find something in /var/log/messages

here's a fine blog post about kernel panics, why they often happen and what can be done about them. the post is a few years old but i don't think things have changed much in that time....

[http://rhcelinuxguide.wordpress.com/2006/06/01/linux-kernel-panic-prevent-cardiac-arrest/](http://rhcelinuxguide.wordpress.com/2006/06/01/linux-kernel-panic-prevent-cardiac-arrest/)

---

### Post by keithpeter on 2011-09-21
Hello decoherence

OK, It's a hard panic, and seems to be associated with scrolling in Firefox when a long web page with lots of objects is loaded. 

/var/logs does not contain a file or directory called messages, so I guess it could not synch the drive on the way down. The logs I do have are below;

```
keith@EeePC:~$ ls /var/log
alternatives.log  dist-upgrade	  fsck		    samba
apport.log	  dmesg		  installer	    speech-dispatcher
apt		  dmesg.0	  jockey.log	    syslog
auth.log	  dmesg.1.gz	  kern.log	    udev
boot		  dmesg.2.gz	  lastlog	    ufw.log
boot.log	  dmesg.3.gz	  lightdm	    unattended-upgrades
bootstrap.log	  dmesg.4.gz	  mail.err	    wtmp
btmp		  dpkg.log	  mail.log	    Xorg.0.log
ConsoleKit	  faillog	  news		    Xorg.0.log.old
cups		  fontconfig.log  pm-powersave.log
```

The text printed to screen (which I will photograph next time) mentions a return to text console, so I'll investigate the X logs. 

Its only happened twice so far, Firefox, long web page, plenty of flash ads and doodads, so I'll try to reproduce it consistently.

Thanks

---

### Post by keithpeter on 2011-09-27
Hello All

Hoping this is for historical interest as 3.0.0.12 kernel has just arrived as an update. These two photos of the completely frozen screen show part of the kernel dump (3.0.0.11 kernel). Any ideas?

---

### Post by keithpeter on 2011-09-27
Kernel panic again with 3.0.0.12 as today's update. Just like the first thumbnail.

Anyone else seeing these?

Could the hardware be playing up?

Haven't had this with any other linux distribution

---

### Post by jmacak on 2011-09-27
Hi

I've had two panics the last couple of weeks running kubuntu.

I have an asus 1000he.

I have not captured any of the screens of death.  If I get another, I will see if mine looks like yours.

-j

---

