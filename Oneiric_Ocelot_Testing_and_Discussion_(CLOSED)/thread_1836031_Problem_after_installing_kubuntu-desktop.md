---
title: "Problem after installing kubuntu-desktop"
date: 2011-08-30
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by carltonh on 2011-08-30
My PC no longer boots all the way to the login manager (lightdm) after installing the kubuntu-desktop package within a standard oneiric ubuntu installation.

I have a way around the problem. I choose "recovery mode" on Grub2 menu, then "resume" normal boot up.  This brings me to a login prompt without X11. Then login and type "sudo lightdm" and am back to normal, but after every shutdown I have to repeat this process through recovery mode every time.

Is this a standard problem with a known fix, or I assume there is a log file or such that I can use to diagnose the problem?

---

### Post by lucazade on 2011-08-30
> **carltonh said:**
> My PC no longer boots all the way to the login manager (lightdm) after installing the kubuntu-desktop package within a standard oneiric ubuntu installation.

I have a way around the problem. I choose "recovery mode" on Grub2 menu, then "resume" normal boot up.  This brings me to a login prompt without X11. Then login and type "sudo lightdm" and am back to normal, but after every shutdown I have to repeat this process through recovery mode every time.

Is this a standard problem with a known fix, or I assume there is a log file or such that I can use to diagnose the problem?

Today i've installed kubuntu-desktop on a standard oneiric installation, just to check kde state.
During installation of metapackage I was asked to choose lightdm or kdm as default login manager and I kept lightdm as default.
Everything worked correctly so I think you should enable back lightdm as default.
try with:

sudo dpkg-reconfigure lightdm
or just remove kdm

---

### Post by carltonh on 2011-08-30
I tried in stages to see what might actually fix it.

1st sudo apt-get remove kdm
Reboot...still doesn't work.

2nd sudo dpkg-reconfigure lightdm
Rebbot...still doesn't work.

3rd sudo apt-get remove gdm
Reboot...still doesn't work.

The last step also removed gdm-guest-sessions, but I don't think that matters.

Any more ideas?

---

### Post by lucazade on 2011-08-30
sudo update-rc.d lightdm enable
?

---

### Post by carltonh on 2011-08-30
That gives this message:
```
update-rc.d: warning: /etc/init.d/lightdm missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
 System start/stop links for /etc/init.d/lightdm do not exist.
```

---

### Post by buzzmandt on 2011-08-30
hmmmm, how about
```
sudo apt-get install lightdm --reinstall
```

---

### Post by carltonh on 2011-08-30
No, that didn't work.  Maybe one or some of the LSB packages need to be reinstalled?

---

### Post by carltonh on 2011-08-30
Tried sudo apt-get install lsb lsb-base lsb-desktop --reinstall

Did not work either.

---

### Post by lucazade on 2011-08-30
> **carltonh said:**
> That gives this message:
```
update-rc.d: warning: /etc/init.d/lightdm missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
 System start/stop links for /etc/init.d/lightdm do not exist.
```

oh right, lightdm service is not init.d based so only way to interact with it is via:
```
sudo service lightdm start
```
anyway dunno if this really help your situation..

---

### Post by carltonh on 2011-08-30
No that just starts lightdm same as running "sudo lightdm" if X11 is not already running.  It doesn't make it the boot up process complete to get to lightdm or a prompt.

The last thing the screen shows when attempting to boot up normally is "checking battery state  .... [ok]"  I can hit ALT+F1 and log in, but sudo lightdm does not work or get to X that way.  I still can only get to X by going through the "recovery mode" on the Grub2 menu.

---

### Post by xebian on 2011-08-31
Try installing lxdm (lxde-core).  It's a good recovery tool for X not behaving properly.  Just select your session - gnome, etc.

---

### Post by carltonh on 2011-08-31
I tried sudo apt-get install lxde-core --reinstall because I already had the lubuntu-desktop installed too. (And xubuntu-desktop and enlightenment and gnome shell.)  That didn't fix the problem or allow bootup process to complete.

Since installing the kubuntu-desktop changed the grub2 background to blue (no other *-desktop package did) I tried sudo apt-get install grub2 grub2-common grub2-splashimages --reinstall.  I didn't realize only grub2-common of those was installed, but it didn't matter. It didn't change the background back to Ubuntu default black, nor allow bootup to complete.

---

### Post by carltonh on 2011-08-31
Is there a log file that might help? I've copied the one from /var/log/boot.log

Note that when I try to boot normally from the first Grub2 menu item, the screen displays the 2nd to last line about checking battery state ...[ok]. It does not show or state the next line about stopping SysV  runlevel compatibility.

```
fsck from util-linux 2.19.1

/dev/sda5: clean, 354808/3039232 files, 7269378/12141056 blocks

modem-manager[804]: <info>  ModemManager (version 0.5) starting...




Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox

 * Starting AppArmor profiles       [80G 
[74G[ OK ]

 * Setting sensors limits       [80G 
[74G[ OK ]

 * Starting Kernel Oops catching service kerneloops       [80G 
 * Stopping System V initialisation compatibility[74G[ OK ]

[74G[ OK ]

 * Starting System V runlevel compatibility[74G[ OK ]

 * Starting automatic crash report generation[74G[ OK ]

 * Starting eCryptfs[74G[ OK ]

speech-dispatcher disabled; edit /etc/default/speech-dispatcher

 * Starting ACPI daemon[74G[ OK ]

 * Starting CPU interrupts balancing daemon[74G[ OK ]

 * Starting save kernel messages[74G[ OK ]

 * Starting anac(h)ronistic cron[74G[ OK ]

 * Stopping eCryptfs[74G[ OK ]

 * Starting regular background program processing daemon[74G[ OK ]

 * Starting deferred execution scheduler[74G[ OK ]

 * Stopping save kernel messages[74G[ OK ]

 * Stopping anac(h)ronistic cron[74G[ OK ]

 * Starting the Winbind daemon winbind       [80G 
[74G[ OK ]

 * Starting bluetooth       [80G 
[74G[ OK ]

 [33m*[39;49m PulseAudio configured for per-user sessions

saned disabled; edit /etc/default/saned

 * Starting anac(h)ronistic cron[74G[ OK ]

 * Stopping anac(h)ronistic cron[74G[ OK ]

 * Checking battery state...       [80G 
[74G[ OK ]

 * Stopping System V runlevel compatibility[74G[ OK ]
```

---

### Post by carltonh on 2011-09-02
I gave up and installed the 11.10 beta 1 over it without reformating.  I'm not sure if I should mark the thread solved, because there is a real problem here that wasn't solved, just bypassed by over-writing. I think I'll avoid reinstalling the kubuntu-desktop package until someone knows it is fixed.

Any opinion on if it might be safe to just install kde without the kubuntu-desktop meta-package?

---

