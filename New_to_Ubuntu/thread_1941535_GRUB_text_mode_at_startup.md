---
title: "GRUB text mode at startup"
date: 2012-03-15
forum: New to Ubuntu
---

### Post by stdare on 2012-03-15
Greetings all,
My Ubuntu 10.10 system suddenly stopped booting the other day.
I was working on a media mounting issue, but not from the drive ubuntu boots from.
It hung on startup a couple of times, at which I had to force a power down.
Now I am getting GRUB in text mode when I startup.

Could someone fill me in on:
1. Why this may have occurred?
2. Steps to fix?
3. If I get as far as startup, where I might look to solve the non-booting issue.

Might I need to reinstall Ubuntu?

Many thanks!

---

### Post by Jon Monreal on 2012-03-17
Try the following commands:

```
kernel /boot/vmlinuz
boot
```

Hopefully that will allow you to boot, and then we can work on fixing the problem.

---

### Post by oldfred on 2012-03-17
You may need to run a e2fsck. Any abnormal shutdown can cause issues.

#From liveCD so everything is unmounted,swap off if necessary, change example with sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors:
sudo e2fsck -f -y -v /dev/sdb1

How did you shut down?

Best way to shutdown:
Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)
Another
sudo init 0

Generally pressing and holding Ctrl+Alt and
then PrintScr, R, E, I, S, U, B (Raising Elephants Is So Utterly Boring)
should do a clean reboot.
R gives back control of the keyboard, S issues a sync, E sends all processes but init the term singal, I sends all processes but init the kill signal, U mounts all filesystem ro to prevent a fsck at reboot, B reboots the system

---

### Post by stdare on 2012-03-17
> **oldfred said:**
> You may need to run a e2fsck. Any abnormal shutdown can cause issues.

#From liveCD so everything is unmounted,swap off if necessary, change example with sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors:
sudo e2fsck -f -y -v /dev/sdb1

How did you shut down?

Best way to shutdown:
Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)
Another
sudo init 0

Generally pressing and holding Ctrl+Alt and
then PrintScr, R, E, I, S, U, B (Raising Elephants Is So Utterly Boring)
should do a clean reboot.
R gives back control of the keyboard, S issues a sync, E sends all processes but init the term singal, I sends all processes but init the kill signal, U mounts all filesystem ro to prevent a fsck at reboot, B reboots the system
I shutdown by holding the power button, as it was hung on startup.  
Thanks for the proper shutdown tips!

---

### Post by stdare on 2012-03-17
> **Jon Monreal said:**
> Try the following commands:

```
kernel /boot/vmlinuz
boot
```

Hopefully that will allow you to boot, and then we can work on fixing the problem.
OK, but how do I get to a command terminal from grub?
Taa

---

### Post by chipbuster on 2012-03-17
The lines there go into the GRUB prompt, not a  linux one. If you can't get to the GRUB prompt, try escape or Ctrl+x

---

### Post by oldfred on 2012-03-17
If you are getting grub> or system rescue you may be able to manually boot otherwise it may be better just to use Boot-Repair.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)

---

### Post by stdare on 2012-03-18
Thanks for your suggestions folks.
Not much time to play with my machine at the mo. Will give things another whirl in a day or so. 
Have a great week!
D

---

### Post by stdare on 2012-03-23
Hello all.  I have some time to work on this problem this weekend, so will be giving your suggestions a try.
Many thanks to those who have responded so far.
Dan

---

### Post by stdare on 2012-03-23
> **Jon Monreal said:**
> Try the following commands:

```
kernel /boot/vmlinuz
boot
```

Hopefully that will allow you to boot, and then we can work on fixing the problem.
Gave this a whirl with no joy.
Getting unknown command 'kernel' error.
Thanks

---

### Post by stdare on 2012-03-23
> **oldfred said:**
> If you are getting grub> or system rescue you may be able to manually boot otherwise it may be better just to use Boot-Repair.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)
I gather that liveCD is a bootable install disk?
On this assumption I returned to the USB I installed my system from. Next problem is that the machine doesn't seem to want to recognise it as the boot source....
Having not much luck here!

---

### Post by stdare on 2012-03-23
OK - let's get serious.

Here is [a screenshot]("http://www.box.com/s/5f15c8c435e46ce0419e") of the grub screen I get on boot.

Here is [what it shows]("http://www.box.com/s/6ce949f406c48fd96cf7") when I hit 'e' to edit boot command.

Hopefully this helps to shed some light on what is going wrong.

Thanks contributors.

Dan

---

### Post by oldfred on 2012-03-23
Those look normal. You can upload screenshots (or small size photos) with the paper clip icon in the edit panel at the top of you message.

That you get the menu says grub has loaded and is ready to boot kernel. If you then have issues it often requires a boot parameter and most often is video related recently.

On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by dolphin194 on 2012-03-23
GRUB, GRUB, GRUB...Oh what fun.

Well I have a solution that almost always works. I have suggested this to multiple people.

You will use a Live CD and install Boot Repair on it.
[I]
Grab your Live CD, you're gonna need it![/I] Your Live CD is your Ubuntu Intallation CD
*It can also be done with a flash drive media.*

***1) Boot from your Live CD and type the following commands in the Terminal***
```
sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update
``````
sudo apt-get install -y boot-repair && boot-repair
```[B][I]2) Open Boot Repair and click the "Recommended Repair'
[/I][/B][I][IMG]http://pix.toile-libre.org/upload/original/1322150524.png[/IMG]

[B]This should fix any issues with the GRUB and everything should go back to normal.

[/B]Source: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
[/I]

---

### Post by stdare on 2012-03-23
Thanks for replies folks. 
Will investigate further and let you know how I get on.
D

---

### Post by stdare on 2012-03-26
Thanks Oldfred for your ongoing assistance!!
I tried your suggestion and ctrl+X launched a boot.  
The last messages I see are saying "Failed to spawn network interface (lo) pre-start process :unable to execute : Permission denied...
Also '/lib/udev/udisks-part-id' failed a few lines above that.

Thanks
D

---

### Post by stdare on 2012-03-26
> **dolphin194 said:**
> GRUB, GRUB, GRUB...Oh what fun.

Well I have a solution that almost always works. I have suggested this to multiple people.

You will use a Live CD and install Boot Repair on it.
[I]
Grab your Live CD, you're gonna need it![/I] Your Live CD is your Ubuntu Intallation CD
*It can also be done with a flash drive media.*

***1) Boot from your Live CD and type the following commands in the Terminal***
```
sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update
``````
sudo apt-get install -y boot-repair && boot-repair
```[B][I]2) Open Boot Repair and click the "Recommended Repair'
[/I][/B][I][IMG]http://pix.toile-libre.org/upload/original/1322150524.png[/IMG]

[B]This should fix any issues with the GRUB and everything should go back to normal.

[/B]Source: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
[/I]
**Thanks for this tip.**  
I finally got my liveCD (on usb) to boot the system, which meant I could get in and try the boot repair. This worked, and I now find myself where i was 2 weeks ago, with a system that says its booting but never actually starts up. 
At least now I can get into the file structure, backup anything i wish to, then reinstall Ubuntu.

I won't click solved yet, as someone may be able to help me with the issue of my system hanging on startup.

Thanks so much for your input!

---

### Post by oldfred on 2012-03-26
The last errors your see may indicate something, but you should look at the log files and look for any entry with long times between entries or one that repeats, trying to load something.

System -> Administration->Log File Viewer 
Look for repeated entries or long times between entries
or:
egrep -e fatal /var/log/dmesg
egrep -e modules /var/log/syslog

I also look in messages.

Edit, It could be that system needs another boot parameter to recognize system correctly. We often add nomodeset for video issues but their are many other parameters.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by stdare on 2012-03-31
So all fixed.

Using my boot USB I was able to startup the system and backup files off my drive where Ubuntu was installed. (Won't be partitioning to use some space on that drive for user files again - will keep things simpler.)

I was then able to do a reinstall of Ubuntu.
System now boots and shuts down no probs.
Some fun ahead reinstating all the settings I once had, like samba and mounted drives, but this was always going to be a 'project machine.'

Thanks to all who contributed, particularly Old Fred and Dolphin192.

Marking as solved  8-)

---

