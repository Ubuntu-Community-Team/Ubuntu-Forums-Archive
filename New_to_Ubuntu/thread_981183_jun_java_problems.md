---
title: "jun java problems"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by fantasia on 2008-11-13
I'm a complete newbie so i need big help. Every time I try to run pkg. manager or synoptic I get this message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

---

### Post by kernelhaxor on 2008-11-13
Did you try running that command? If so what did it say then?

---

### Post by fantasia on 2008-11-13
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)

now and download.  The file should be owned by root.root and be copied
to /tmp.

---

### Post by igknighted on 2008-11-13
You need to accept the license, running the command it says (prepend it with sudo, it needs root privileges) should bring up the dialog to accept the license.

---

### Post by fantasia on 2008-11-13
I tried that and I got the same message:

---

### Post by igknighted on 2008-11-13
Can you copy/paste the entire terminal output (the command you entered and what it spit back) so we can see it?

---

### Post by fantasia on 2008-11-13
angie@angie-desktop:~$ sudo dpkg --configure -a
Setting up sun-java6-doc (6-10-0ubuntu2) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort]

---

### Post by porchrat on 2008-11-13
> **fantasia said:**
> angie@angie-desktop:~$ sudo dpkg --configure -a
Setting up sun-java6-doc (6-10-0ubuntu2) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort]

It is trying to run a dpkg build for java documentation.  Why would it do that?

All you were doing is trying to use "synaptic" and "add/remove programs"?  Nothing else?

---

### Post by fantasia on 2008-11-13
no I get the same message for update manager too

---

### Post by igknighted on 2008-11-13
What are you using java for?  You installed the JDK, which is for writing programs in Java.  And even then, I don't think you need the javadoc.  Can you 'sudo apt-get remove --purge sun-java6-doc'?

edit: oh, just type 'no' then enter to abort.  You (almost certainly) don't need javadoc

---

### Post by fantasia on 2008-11-13
angie@angie-desktop:~$ sudo apt-get remove --purge sun-java6-doc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  sun-java6-doc*
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
2 not fully installed or removed.
After this operation, 168kB disk space will be freed.
Do you want to continue [Y/n]?

---

### Post by igknighted on 2008-11-13
Yes, thats what it should say.  Hit 'Y' or 'enter' to continue with the removal

---

### Post by porchrat on 2008-11-13
Unless you're a developer working with java, and you want to know the definitions for all the foundations classes you don't really need javadocs.  It isn't required for the jdk to function.  So it shouldn't matter if you remove it.

You might also want to try doing a "sudo apt-get autoremove" just to clean out whatever other unused junk is hanging around your system.

---

### Post by fantasia on 2008-11-13
This is the message I get when I enter yes:

angie@angie-desktop:~$ sudo apt-get remove --purge sun-java6-doc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  sun-java6-doc*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 168kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 227682 files and directories currently installed.)
Removing sun-java6-doc ...
Processing triggers for doc-base ...
Processing 1 removed doc-base file(s)...
Registering documents with scrollkeeper...
Setting up sun-java5-doc (1.5.0-16-3) ...
This package is an installer package, it does not actually contain the
J2SDK documentation.  You will need to go download one of the
archives:

    jdk-1_5_0-doc.zip jdk-1_5_0-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/j2se/1.5.0/download.html](http://java.sun.com/j2se/1.5.0/download.html)

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort]

---

### Post by igknighted on 2008-11-13
same thing... remove that one too (sudo apt-get remove --purge sun-java5-doc)

---

### Post by fantasia on 2008-11-13
I tried that and I get this message

angie@angie-desktop:~$ sudo apt-get autoremove
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
angie@angie-desktop:~$ 

I have no other processes running??

---

### Post by fantasia on 2008-11-13
tried and got this message again

angie@angie-desktop:~$ sudo apt-get remove --purge sun-java5-doc
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by igknighted on 2008-11-13
> **fantasia said:**
> tried and got this message again

angie@angie-desktop:~$ sudo apt-get remove --purge sun-java5-doc
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

sudo dpkg --configure -a

then answer no to abort

---

### Post by fantasia on 2008-11-13
then I get this message

angie@angie-desktop:~$ sudo dpkg --configure -a
dpkg: status database area is locked by another process
angie@angie-desktop:~$

---

### Post by igknighted on 2008-11-13
> **fantasia said:**
> then I get this message

angie@angie-desktop:~$ sudo dpkg --configure -a
dpkg: status database area is locked by another process
angie@angie-desktop:~$

Do you have another terminal open with that dpkg command waiting for an answer?  Or synaptic?  Or update manager?

---

### Post by fantasia on 2008-11-13
no other processes are up or waiting

---

### Post by igknighted on 2008-11-13
> **fantasia said:**
> no other processes are up or waiting

Can you run the command 'top' and see if there is one running in the background?  If you don't see one, it might be that the lockfile wasn't removed... but check top first

---

### Post by porchrat on 2008-11-13
Just because you can't see it in the GUI doesn't mean it isn't still running in the background.

Please post the ouput of this command so that we can see if apt-get or something similar is stuck running in the background locking everything.

```
sudo ps -e
```

EDIT: igknighted's top command will work too

---

### Post by fantasia on 2008-11-13
top - 12:48:35 up  1:49,  2 users,  load average: 0.29, 0.33, 0.36
Tasks: 112 total,   2 running, 110 sleeping,   0 stopped,   0 zombie

---

### Post by igknighted on 2008-11-13
> **fantasia said:**
> top - 12:48:35 up  1:49,  2 users,  load average: 0.29, 0.33, 0.36
Tasks: 112 total,   2 running, 110 sleeping,   0 stopped,   0 zombie

It should have had an ever-changing list of running apps/processes... anything resembling dpkg there?

---

### Post by fantasia on 2008-11-13
this is the response i get

angie@angie-desktop:~$ sudo ps -e
  PID TTY          TIME CMD
    1 ?        00:00:02 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 migration/0
    4 ?        00:00:00 ksoftirqd/0
    5 ?        00:00:00 watchdog/0
    6 ?        00:00:00 events/0
    7 ?        00:00:00 khelper
   46 ?        00:00:00 kintegrityd/0
   48 ?        00:00:00 kblockd/0
   50 ?        00:00:00 kacpid
   51 ?        00:00:00 kacpi_notify
  113 ?        00:00:00 cqueue
  117 ?        00:00:00 kseriod
  154 ?        00:00:00 pdflush
  155 ?        00:00:00 pdflush
  156 ?        00:00:00 kswapd0
  200 ?        00:00:00 aio/0
 1129 ?        00:00:00 ksuspend_usbd
 1133 ?        00:00:00 khubd
 1155 ?        00:00:01 ata/0
 1157 ?        00:00:00 ata_aux
 1398 ?        00:00:00 scsi_eh_0
 1400 ?        00:00:02 scsi_eh_1
 2073 ?        00:00:01 kjournald
 2257 ?        00:00:01 udevd
 4043 tty4     00:00:00 getty
 4044 tty5     00:00:00 getty
 4050 tty2     00:00:00 getty
 4055 tty3     00:00:00 getty
 4059 tty6     00:00:00 getty
 4214 ?        00:00:00 acpid
 4251 ?        00:00:00 kondemand/0
 4330 ?        00:00:00 syslogd
 4377 ?        00:00:00 dd
 4379 ?        00:00:00 klogd
 4400 ?        00:00:00 dbus-daemon
 4420 ?        00:00:00 avahi-daemon
 4421 ?        00:00:00 avahi-daemon
 4458 ?        00:00:00 cupsd
 4520 ?        00:00:00 winbindd
 4534 ?        00:00:00 winbindd
 4537 ?        00:00:00 dhcdbd
 4557 ?        00:00:01 hald
 4560 ?        00:00:00 console-kit-dae
 4623 ?        00:00:00 hald-runner
 4643 ?        00:00:00 hald-addon-inpu
 4650 ?        00:00:00 hald-addon-acpi
 4654 ?        00:00:03 hald-addon-stor
 4692 ?        00:00:00 bluetoothd
 4697 ?        00:00:00 btaddconn
 4699 ?        00:00:00 btdelconn
 4711 ?        00:00:00 krfcommd
 4743 ?        00:00:00 NetworkManager
 4748 ?        00:00:00 wpa_supplicant
 4751 ?        00:00:00 nm-system-setti
 4767 ?        00:00:00 gdm
 4771 ?        00:00:00 gdm
 4776 tty7     00:07:40 Xorg
 4789 ?        00:00:00 system-tools-ba
 4824 ?        00:00:00 atd
 4852 ?        00:00:00 cron
 4931 tty1     00:00:00 getty
 4949 ?        00:00:00 dhclient
 5024 ?        00:00:00 bonobo-activati
 5076 ?        00:00:00 dbus-launch
 5077 ?        00:00:00 dbus-daemon
 5127 ?        00:00:00 gnome-keyring-d
 5137 ?        00:00:00 x-session-manag
 5195 ?        00:00:00 dbus-launch
 5196 ?        00:00:00 dbus-daemon
 5199 ?        00:00:01 pulseaudio
 5202 ?        00:00:00 gconf-helper
 5204 ?        00:00:04 gconfd-2
 5210 ?        00:00:00 seahorse-agent
 5214 ?        00:00:00 gvfsd
 5219 ?        00:00:00 gnome-keyring-d
 5220 ?        00:00:04 gnome-settings-
 5222 ?        00:00:28 metacity
 5232 ?        00:00:00 gvfs-fuse-daemo
 5238 ?        00:00:49 gnome-panel
 5241 ?        00:00:04 nautilus
 5244 ?        00:00:00 bonobo-activati
 5256 ?        00:00:00 gvfs-hal-volume
 5258 ?        00:00:00 gvfs-gphoto2-vo
 5266 ?        00:00:21 gnome-screensav
 5269 ?        00:00:00 trashapplet
 5273 ?        00:00:00 gvfsd-burn
 5276 ?        00:00:01 gvfsd-trash
 5283 ?        00:00:04 tomboy
 5286 ?        00:00:00 gweather-applet
 5289 ?        00:00:00 stickynotes_app
 5292 ?        00:00:40 geyes_applet2
 5299 ?        00:00:00 fast-user-switc
 5302 ?        00:00:00 mixer_applet2
 5306 ?        00:00:00 tracker-applet
 5308 ?        00:00:00 python
 5312 ?        00:00:02 update-notifier
 5316 ?        00:00:01 nm-applet
 5317 ?        00:00:00 bluetooth-apple
 5321 ?        00:00:00 evolution-alarm
 5324 ?        00:00:00 trackerd
 5326 ?        00:00:00 gnome-power-man
 5333 ?        00:00:00 evolution-excha
 5337 ?        00:00:00 evolution-data-
 5500 ?        00:12:46 firefox
 7784 ?        00:00:04 apt-get
 7800 pts/1    00:00:00 dpkg
 7801 pts/1    00:00:00 sun-java5-doc.p
 8493 ?        00:00:01 gnome-terminal
 8496 ?        00:00:00 gnome-pty-helpe
 8497 pts/2    00:00:00 bash
 8517 pts/2    00:00:00 ps
angie@angie-desktop:~$

---

### Post by porchrat on 2008-11-13
> **fantasia said:**
> top - 12:48:35 up  1:49,  2 users,  load average: 0.29, 0.33, 0.36
Tasks: 112 total,   2 running, 110 sleeping,   0 stopped,   0 zombie

rather post "sudo ps -e"

will give us a list of all the processes currently running on your system.

---

### Post by igknighted on 2008-11-13
> **fantasia said:**
> this is the response i get

angie@angie-desktop:~$ sudo ps -e
  PID TTY          TIME CMD
    1 ?        00:00:02 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 migration/0
    4 ?        00:00:00 ksoftirqd/0
    5 ?        00:00:00 watchdog/0
    6 ?        00:00:00 events/0
    7 ?        00:00:00 khelper
   46 ?        00:00:00 kintegrityd/0
   48 ?        00:00:00 kblockd/0
   50 ?        00:00:00 kacpid
   51 ?        00:00:00 kacpi_notify
  113 ?        00:00:00 cqueue
  117 ?        00:00:00 kseriod
  154 ?        00:00:00 pdflush
  155 ?        00:00:00 pdflush
  156 ?        00:00:00 kswapd0
  200 ?        00:00:00 aio/0
 1129 ?        00:00:00 ksuspend_usbd
 1133 ?        00:00:00 khubd
 1155 ?        00:00:01 ata/0
 1157 ?        00:00:00 ata_aux
 1398 ?        00:00:00 scsi_eh_0
 1400 ?        00:00:02 scsi_eh_1
 2073 ?        00:00:01 kjournald
 2257 ?        00:00:01 udevd
 4043 tty4     00:00:00 getty
 4044 tty5     00:00:00 getty
 4050 tty2     00:00:00 getty
 4055 tty3     00:00:00 getty
 4059 tty6     00:00:00 getty
 4214 ?        00:00:00 acpid
 4251 ?        00:00:00 kondemand/0
 4330 ?        00:00:00 syslogd
 4377 ?        00:00:00 dd
 4379 ?        00:00:00 klogd
 4400 ?        00:00:00 dbus-daemon
 4420 ?        00:00:00 avahi-daemon
 4421 ?        00:00:00 avahi-daemon
 4458 ?        00:00:00 cupsd
 4520 ?        00:00:00 winbindd
 4534 ?        00:00:00 winbindd
 4537 ?        00:00:00 dhcdbd
 4557 ?        00:00:01 hald
 4560 ?        00:00:00 console-kit-dae
 4623 ?        00:00:00 hald-runner
 4643 ?        00:00:00 hald-addon-inpu
 4650 ?        00:00:00 hald-addon-acpi
 4654 ?        00:00:03 hald-addon-stor
 4692 ?        00:00:00 bluetoothd
 4697 ?        00:00:00 btaddconn
 4699 ?        00:00:00 btdelconn
 4711 ?        00:00:00 krfcommd
 4743 ?        00:00:00 NetworkManager
 4748 ?        00:00:00 wpa_supplicant
 4751 ?        00:00:00 nm-system-setti
 4767 ?        00:00:00 gdm
 4771 ?        00:00:00 gdm
 4776 tty7     00:07:40 Xorg
 4789 ?        00:00:00 system-tools-ba
 4824 ?        00:00:00 atd
 4852 ?        00:00:00 cron
 4931 tty1     00:00:00 getty
 4949 ?        00:00:00 dhclient
 5024 ?        00:00:00 bonobo-activati
 5076 ?        00:00:00 dbus-launch
 5077 ?        00:00:00 dbus-daemon
 5127 ?        00:00:00 gnome-keyring-d
 5137 ?        00:00:00 x-session-manag
 5195 ?        00:00:00 dbus-launch
 5196 ?        00:00:00 dbus-daemon
 5199 ?        00:00:01 pulseaudio
 5202 ?        00:00:00 gconf-helper
 5204 ?        00:00:04 gconfd-2
 5210 ?        00:00:00 seahorse-agent
 5214 ?        00:00:00 gvfsd
 5219 ?        00:00:00 gnome-keyring-d
 5220 ?        00:00:04 gnome-settings-
 5222 ?        00:00:28 metacity
 5232 ?        00:00:00 gvfs-fuse-daemo
 5238 ?        00:00:49 gnome-panel
 5241 ?        00:00:04 nautilus
 5244 ?        00:00:00 bonobo-activati
 5256 ?        00:00:00 gvfs-hal-volume
 5258 ?        00:00:00 gvfs-gphoto2-vo
 5266 ?        00:00:21 gnome-screensav
 5269 ?        00:00:00 trashapplet
 5273 ?        00:00:00 gvfsd-burn
 5276 ?        00:00:01 gvfsd-trash
 5283 ?        00:00:04 tomboy
 5286 ?        00:00:00 gweather-applet
 5289 ?        00:00:00 stickynotes_app
 5292 ?        00:00:40 geyes_applet2
 5299 ?        00:00:00 fast-user-switc
 5302 ?        00:00:00 mixer_applet2
 5306 ?        00:00:00 tracker-applet
 5308 ?        00:00:00 python
 5312 ?        00:00:02 update-notifier
 5316 ?        00:00:01 nm-applet
 5317 ?        00:00:00 bluetooth-apple
 5321 ?        00:00:00 evolution-alarm
 5324 ?        00:00:00 trackerd
 5326 ?        00:00:00 gnome-power-man
 5333 ?        00:00:00 evolution-excha
 5337 ?        00:00:00 evolution-data-
 5500 ?        00:12:46 firefox
[B] 7784 ?        00:00:04 apt-get
 7800 pts/1    00:00:00 dpkg
 7801 pts/1    00:00:00 sun-java5-doc.p[/B]
 8493 ?        00:00:01 gnome-terminal
 8496 ?        00:00:00 gnome-pty-helpe
 8497 pts/2    00:00:00 bash
 8517 pts/2    00:00:00 ps
angie@angie-desktop:~$

It is running... type top, then while top is running hit 'k' to kill processes, then type in the PID's from above (7784, 7800, and 7801) to kill them.

---

### Post by porchrat on 2008-11-13
There is also another alternative.

You can remove the files that synaptic uses to lock by using this command:

```
sudo rm /var/lock/aptitude
```

You can remove the file dpkg uses to lock by using this command:

```
sudo rm /var/lib/dpkg/lock
```

---

### Post by porchrat on 2008-11-13
> **igknighted said:**
> It is running... type top, then while top is running hit 'k' to kill processes, then type in the PID's from above (7784, 7800, and 7801) to kill them.

another command is to use 

```
sudo kill -9 7784
sudo kill -9 7800
sudo kill -9 7801
```

---

### Post by igknighted on 2008-11-13
> **porchrat said:**
> There is also another alternative.

You can remove the files that synaptic uses to lock by using this command:

```
sudo rm /var/lock/aptitude
```

You can remove the file dpkg uses to lock by using this command:

```
sudo rm /var/lib/dpkg/lock
```

Don't do this while dpkg/apt are running though!

---

### Post by igknighted on 2008-11-13
> **porchrat said:**
> another command is to use 

```
sudo kill -9 7784
sudo kill -9 7800
sudo kill -9 7801
```

Thanks, I'm not on a linux box ATM and I can never remember what the command to kill a process by PID is.

---

### Post by fantasia on 2008-11-13
ok I did that then I tried sudo dpkg --configure -a and I got the same message as before

angie@angie-desktop:~$ sudo apt-get remove --purge sun-java6-doc
[sudo] password for angie: 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
angie@angie-desktop:~$ sudo dpkg --configure -a
Setting up sun-java5-doc (1.5.0-16-3) ...
This package is an installer package, it does not actually contain the
J2SDK documentation.  You will need to go download one of the
archives:

    jdk-1_5_0-doc.zip jdk-1_5_0-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/j2se/1.5.0/download.html](http://java.sun.com/j2se/1.5.0/download.html)

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort]

---

### Post by porchrat on 2008-11-13
which ones did you try?

Suppose we shouldn't have given you all the ideas at once

---

### Post by igknighted on 2008-11-13
well, i guess you'll just have to download the file it wants from the link it gives and get through it.  I'd remove all the sun-java5 stuff though when you clean that mess up and use sun-java6 instead (it is the latest java).  You only need to install the sun-java6-jre and sun-java6-plugin packages in order to use java as an end user.  If you are writing java software also include the sun-java6-jdk as well.

---

### Post by porchrat on 2008-11-13
There is another thing you could try...and that is to reinstall apt-get.  Of course I've just realised you can't do that as you can't run dpkg...hmmmm this is a strange one.  I'm sorry friend but I'm out of suggestions.  Did you try removing the lock files?

---

### Post by igknighted on 2008-11-13
> **porchrat said:**
> There is another thing you could try...and that is to reinstall apt-get.  Of course I've just realised you can't do that as you can't run dpkg...hmmmm this is a strange one.  I'm sorry friend but I'm out of suggestions.  Did you try removing the lock files?

He/she could try clearing the apt cache, but the message that is coming up isn't an error per se.  Its simple enough to just give it the file it wants (it even gives you the link), I just thought it would be easier to delete it rather than configure it.  Apparently it wont let you do that though, hence the need to just give it what it wants.

---

### Post by fantasia on 2008-11-13
I tried all of the suggestions so now i'm at the java website trying to download the upgrade,  crossing my fingers that it works.. I'll keep you posted for the results, thanks for your help

---

### Post by porchrat on 2008-11-13
> **igknighted said:**
> He/she could try clearing the apt cache, but the message that is coming up isn't an error per se.  Its simple enough to just give it the file it wants (it even gives you the link), I just thought it would be easier to delete it rather than configure it.  Apparently it wont let you do that though, hence the need to just give it what it wants.

Good point.  I agree that is probably the best course of action right now.  Anyway it is getting late and I have work in the morning so I'm heading to bed, I hope you get this sorted out.  Good luck!

---

### Post by igknighted on 2008-11-13
> **fantasia said:**
> I tried all of the suggestions so now i'm at the java website trying to download the upgrade,  crossing my fingers that it works.. I'll keep you posted for the results, thanks for your help

*YOU ONLY WANT THE JAVADOC FILE INDICATED (and the full install, not the upgrade)*

Do not install the whole JRE.  You already have that, and installing the one from sun could break both.  Simply put the .zip file in /tmp (you will need sudo) and run the dpkg --configure -a command again.  You need to finish that package install before it will let you install more with apt/synaptic.

---

