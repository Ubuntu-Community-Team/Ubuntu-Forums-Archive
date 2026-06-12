---
title: "wont boot. (neither will previous versions)"
date: 2013-01-24
forum: New to Ubuntu
---

### Post by milkweed701 on 2013-01-24
so, my laptop was 'out of order' due to keyboard issues for some time. i came back to 89 updates barking at me. after those updates, ubuntu will not boot. (unfortunately, but) luckily, the hard drive also has a vista partition, that i am using now. the last time something close to this happened, i was able to get a previous version to boot, and a friend reinstalled the kernel. this time, no previous versions will boot. what do i do?

>power up
>see "boot options press f12" screen
> see box that allows me to boot:
-ubuntu
-ubuntu (recovery)
-previous versions
-memtest
-another memtest option
-vista
>ubuntu(any version) seems to be hung up on some MIDI application.

please help, i miss ubuntu

---

### Post by mansonfan78 on 2013-01-24
Can you load Ubuntu recovery?  In the menu that comes up after loading that there is an option to repair broken packages, I would give that a try first.

---

### Post by milkweed701 on 2013-01-24
i tried that, with a few other "recovery" options. they all say that the "last mounted time" for something important-looking "is in the future", but its by less than a day, and its probably due to a hardware clock being incorrectly set, and that its been fixed. it goes no further. - i wish i could copy and paste the text.

---

### Post by Bashing-om on 2013-01-25
milkweed701; Hi !

Probing to see what shape your ubuntu is in:
Boot up the liveCD at the purple splash screen press any key ->language screen; escape to accept the default-> boot options;
Choose "boot from first hard drive".

Do you boot into your operating system ?

[INDENT][INDENT]just try'n to help

[/INDENT][/INDENT]

---

### Post by milkweed701 on 2013-01-25
i have no live cd. and the only splash screens i see are the 'toshiba' & "tell me what you want me to boot [ubuntu, recovery, previous versions, a couple 'memtest' options, and windows vista]"
im trying to boot "ubuntu, with linux 3.2.0-36-generic"
when i select that, i get to this black "cmd line"-looking screen that tells me:
> wont write bytes: broken pipe
> starting pyscrabble
> speech dispatcher disabled
> saned disabled
> starting TiMidity++ ALSA Midi Emulator 
that last one, is where it stops

---

### Post by Bashing-om on 2013-01-25
milkweed701;

With no liveCd, another approach is:
Boot up and choose a "recovery" kernel mode ->recovery menu-> choose "fsck" let it run the check/and try to repair the file system; When completed ->"resume normal boot" option -> degraded graphics is OK at this point. Booting to the desktop.
Reboot the system.

Do you now boot up ubuntu ?

[INDENT][INDENT]try'n to help

[/INDENT][/INDENT]

---

### Post by milkweed701 on 2013-01-25
fsck results:

it tells me that (something important looking) will be remounted in read/write mode and asked if i wanted to continue. i selected 'yes'

then, at the bottom, i saw:
fsck from util-linux 2.20.1
/dev/sda3: 601280/11075584 files (1.8% non-contagious) {then something about blocks}

after this, the activity light goes out, and nothing changes.

---

### Post by Bashing-om on 2013-01-25
milkweed701;

Do you get any kind of a command line interface ?

---

### Post by milkweed701 on 2013-01-25
unfortunately, no sir/ma'am, i did not.

---

### Post by Bashing-om on 2013-01-25
milkweed701;

With no command line, we have exhausted all resources at out disposal to effect a repair.

At this time a liveCD is required (or USB) to look at your system.

Do you need guidance to make a medium ?

[INDENT][INDENT]try'n to help

[/INDENT][/INDENT]

---

### Post by Sarcastic Cows on 2013-01-25
If you've not got any important documents on your Ubuntu partition, it may just be easier to reinstall Ubuntu, unfortunately :(

But there might be a solution if there are things important, just stick around and you might find a solution ;)

---

### Post by milkweed701 on 2013-01-26
Thank you for your assistance. I tried one last time to get it to boot into the current Ubuntu version. It again got stuck. So, in a fit of rage, I randomly pressed (too many) buttons. I somehow managed to get the laptop to want my Ubuntu login information....

I am pleased to announce that I am now at a command line (and using a different machine to stay active in this thread!).

---

### Post by Bashing-om on 2013-01-26
milkweed701;

Good news indeed !

I still suggest you run that sequence of commands from the last post in this normal CLI. In the case of the "normal" CLI precede each command with "sudo" in order to gain root's authority. Carefully !
example:
```
sudo apt-get update
```[INDENT]best regards
 
[/INDENT]

---

### Post by milkweed701 on 2013-01-26
:( 

Command run.

Process complete.

Machine restarted.

Same stopping point. (Midi emulation)

---

### Post by frank604 on 2013-01-26
Without the exact error message that is being displayed, it is a bit hard to take a stab at a solution.  I am making an assumtion that it is similar to another thread and going to summarize some possible solutions.  Please read the thread I linked below.

[http://ubuntuforums.org/showthread.php?t=1859536](http://ubuntuforums.org/showthread.php?t=1859536)

Theory 1: It is a problem with the login manager.

```
sudo dpkg-reconfigure gdm 
```

Theory 2: Need to tidy up packages

```
sudo apt-get autoremove
sudo apt-get autoclean
sudo apt-get update
sudo apt-get upgrade
```

Theory 3: Remove timidity

```
sudo apt-get purge timidity
```

---

### Post by milkweed701 on 2013-01-26
More bad news, guys.

1) for the :gdm: command, I get told that "gdm" is not installed
2) for every other command that was run (all that were listed), I get back:
"
W: Not using locking for read only lock file {specific path}
E: Unable to write to {specific path}
E: The package lists or status file could not be parsed or opened
"

This is from:
root@lappy:~#

---

### Post by frank604 on 2013-01-26
Are you connected to the internet?

Edit: Also, it would be easier to reinstall from a liveusb if you could.  Not the best of answers but it is an option.

Edit2: Just realized you are using Xubuntu and it has changed from GDM to lightdm

---

### Post by milkweed701 on 2013-01-26
I cannot guarantee that it is connected. The wifi light is lit up, the wireless light on the router blinks. I have no reason to believe it is not connected. 

:( Will the usb option wipe out what is already on the Ubuntu partition?

---

### Post by linuxsyst on 2013-01-26
first type ```
mount -o rw,remount /
``` type it in exactly like that. Then try those commands again.
Oh and btw. Its > sudo dpkg-reconfigure lightdm

---

### Post by milkweed701 on 2013-01-26
Every listed command retried.

Every listed command now returned individual results.

Apt-get update returned a lot of "failed to fetch" errors.

Reconfigure lightdm merely took me to the command line

Not sure what to do now.

---

### Post by frank604 on 2013-01-26
Thanks for the updated code for lightdm linuxsyst.

Yes, creating a usb installer will overwrite your xubuntu partition.  Or you can create another alongside it (a second xubuntu partition).  Move everything over to the new and delete the old partition.

I would really try to get those commands working, especially the dpkg-reconfigure and the remove timidity.  Those two commands don't need internet.

The other codes for apt-get are to clean out and update your packages.  Keep us posted.

Edit: restart and try it out

---

### Post by linuxsyst on 2013-01-26
If it says its unable to write that means its locked so you have to mount it so it can write so what error didn```
mount -o rw,remount
``` return?

---

### Post by Bashing-om on 2013-01-26
recon the partition is being mounted "read only" to protect the file system ?

nevermind ,linuxsyst beat me to it.

---

### Post by milkweed701 on 2013-01-26
Thank you, all of you, for trying to help. After lthe remounting, all the other commands worked, with the exception of the one that returned a bunch of :failed to fetch: errors. The partition was/is full, so I wasn't expecting that to work.... However, I am pleased to announce that I am now logged in to a very dearly missed graphical version of Ubuntu, and will be labeling this thread as solved as soon as I can.

Thanks again!!!!!!!!!!!!!!!!

---

### Post by frank604 on 2013-01-26
The collective mind always finds solutions.  Happy that it worked for you :)  Happy Ubuntu-ing

---

