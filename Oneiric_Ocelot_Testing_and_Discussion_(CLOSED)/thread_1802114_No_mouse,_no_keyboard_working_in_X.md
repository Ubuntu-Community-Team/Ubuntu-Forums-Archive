---
title: "No mouse, no keyboard working in X"
date: 2011-07-11
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Quackers on 2011-07-11
I don't often try the daily builds as I have never had one install fully before.
Sadly the builds for the 10th and 11th both fail at 18% of "selecting and installing software". The base system installs fine but I can't get past 18% of the software install process whatever I try.
The md5sums of both iso's are correct and the dvd has been checked for defects in each case.
Is this a common place for the install to fail or is it just my system they object to?
Thanks

---

### Post by collisionystm on 2011-07-11
Have you tried to run in virtualbox?

---

### Post by Quackers on 2011-07-11
No, I prefer to install everything on partitions. Thanks.

---

### Post by rbrick49 on 2011-07-11
i get that problem when I burn with Brasero if I use k3b they work ok and it just says something like software installer failed

---

### Post by Quackers on 2011-07-11
Brasero has failed me occasionally in the past too, but both these dvd's were burned with k3b and they've both been checked for errors.
I honestly can't remember a single daily build that installed properly here, on either release I've tested. Maybe there's a knack to it that I just don't possess :-)
But in fairness, I have probably only ever tried 5 or 6 of them in total.
It sure is a waste of bandwidth though!

---

### Post by donniezazen on 2011-07-11
> **quackers said:**
> i don't often try the daily builds as i have never had one install fully before.
Sadly the builds for the 10th and 11th both fail at 18% of "selecting and installing software". The base system installs fine but i can't get past 18% of the software install process whatever i try.
The md5sums of both iso's are correct and the dvd has been checked for defects in each case.
Is this a common place for the install to fail or is it just my system they object to?
Thanks

+1

EDIT:- Mine worked. I used 07/10 alternate-amd64.iso burned a live usb using unetbootin on win 7. The one made using startup-disk-creator failed as you describe above.

---

### Post by Quackers on 2011-07-11
A recap and an update.
I suffered a breakage in my alpha2 install after running current updates. This breakage results in no keyboard input or pointer movement. If I unplug then re-plug the usb mouse it will work ok, but, as this is a laptop unplugging and re-plugging the keyboard isn't really an option.

I then tried the 10th daily build, which wouldn't fully install, as described earlier.
I then tried the 11th daily build with the same results.
I have since re-installed Natty and upgraded to OO again.
After updates the same keyboard/mouse problems exist. It was ok before the updates were run.
Therefore, it must be one of the recent updates that is causing this problem but I have scoured them and found no likely candidate.

I'd do a bug report but I don't know if that's possible without a keyboard in the affected system.

Can anybody make any suggestions please? 
Thanks all :-)

---

### Post by Harry33 on 2011-07-11
> **Quackers said:**
> A recap and an update.
I suffered a breakage in my alpha2 install after running current updates. This breakage results in no keyboard input or pointer movement. If I unplug then re-plug the usb mouse it will work ok, but, as this is a laptop unplugging and re-plugging the keyboard isn't really an option.

I then tried the 10th daily build, which wouldn't fully install, as described earlier.
I then tried the 11th daily build with the same results.
I have since re-installed Natty and upgraded to OO again.
After updates the same keyboard/mouse problems exist. It was ok before the updates were run.
Therefore, it must be one of the recent updates that is causing this problem but I have scoured them and found no likely candidate.

I'd do a bug report but I don't know if that's possible without a keyboard in the affected system.

Can anybody make any suggestions please? 
Thanks all :-)

It is the latest udev (172-0ubuntu1) that is causing the input death during booting process. I only installed the new udev and after reboot => no mouse, no keyboard.

And yes unplugging USB devices (mouse and keyboard) and replugging them solves the issue, but only until next reboot.

---

### Post by Quackers on 2011-07-11
Ah, thanks Harry. Sadly taking my laptop apart isn't really an option for me.
I'll await an update then, hopefully :-)

---

### Post by Harry33 on 2011-07-11
> **Quackers said:**
> Ah, thanks Harry. Sadly taking my laptop apart isn't really an option for me.
I'll await an update then, hopefully :-)

Well try to downgrade to the previous version 171-0ubuntu4.

---

### Post by Quackers on 2011-07-11
I can try it via chroot perhaps.

---

### Post by Harry33 on 2011-07-11
> **Quackers said:**
> I can try it via chroot perhaps.

Recovery mode works also.
The wget the previous version and downgrade with dpkg.

---

### Post by Quackers on 2011-07-11
Thanks I'll try that. I forgot I now have the recovery option as I have had it disabled for some time :-)

---

### Post by Harry33 on 2011-07-11
Hmm, this is a bit more difficult.
Downgrading udev did not help.

---

### Post by Quackers on 2011-07-11
Oh no! I've not got you in trouble have I?

---

### Post by Harry33 on 2011-07-11
> **Quackers said:**
> Oh no! I've not got you in trouble have I?

No not you.
This bug appeared right after I upgraded udev.

---

### Post by Quackers on 2011-07-11
To be honest I looked for updates that were possible causes and I didn't even see a udev update. Maybe I should go to the optician again :-)

---

### Post by Harry33 on 2011-07-11
There is a bug report (807306) of this "Keyboard & mouse not working in X":

[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/807306](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/807306)

I made a new thread about his.

---

### Post by Harry33 on 2011-07-11
Today I was hit by this bug.
After each boot, I have no mouse and no keyboard detected in LightDm.
Of course I cannot login now.

If I unplug and replug mouse & keyboard they work again.

This is the original bug report (807306) about this issue:

[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/807306](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/807306)

There are several duplicates also: 807291, 807538, 808599, 808890.

---

### Post by Quackers on 2011-07-11
Thanks. I've me too'd the bug.

---

### Post by Quackers on 2011-07-11
Me too, me too :wink:

---

### Post by Harry33 on 2011-07-11
So the bug report suggests that this is really a difficult issue with new udev.
Some users report this will help:

mv /run/udev /run/udev.old

---

### Post by Quackers on 2011-07-11
I'm back in! Using the 
mv /run/udev /run/udev.old

I'm not sure whether that will last though. But at least I can type again in OO :-)

---

### Post by Harry33 on 2011-07-11
I think the directory /run/udev is problematic after the lates base-files and udev upgrades.

You can also delete the directory I think. Renaming it simply does the same to the udev.

---

### Post by lucazade on 2011-07-11
> **Quackers said:**
> I'm back in! Using the 
mv /run/udev /run/udev.old

I'm not sure whether that will last though. But at least I can type again in OO :-)

solves here as well!
ohhhh my precious!

---

### Post by Quackers on 2011-07-11
Isn't that the cause of the silly message at boot for the last few weeks?

---

### Post by Harry33 on 2011-07-11
> **Quackers said:**
> Isn't that the cause of the silly message at boot for the last few weeks?

That is actually another bug, but it is somehow related.
At least the existence of the directory /run/udev.
I deleted this directory and all is well now.

---

### Post by Quackers on 2011-07-11
Thanks Harry33 :-)

---

### Post by JRV on 2011-07-11
> **Harry33 said:**
> So the bug report suggests that this is really a difficult issue with new udev.
Some users report this will help:

mv /run/udev /run/udev.old

It worked for me, many thanks Harry33.

---

### Post by arpanaut on 2011-07-11
WOW that fix also restored my sound -indicator & session-indicator in the panel, and allowed me to log in to Unity 3d for the first time since todays updates were applied.

TYVM

---

### Post by linuxman94 on 2011-07-11
Installed today's updates and rebooted, and when i got to the login screen, my mouse and keyboard didn't work!  This is the second time this has happened during the testing period.  Last time it was pre-alpha 1.  I'm using a Logitech ex110 cordless desktop with the receiver connected using USB.

EDIT: Just saw the other thread about this :lolflag:

---

### Post by jerrylamos on 2011-07-11
> **Harry33 said:**
> So the bug report suggests that this is really a difficult issue with new udev.
Some users report this will help:

mv /run/udev /run/udev.old


Well there wasn't any /run/udev so mv /run/udev /run/udev.old didn't work.

So I booted in recovery mode and did:

mkdir /run/udev
mv /run/udev /run/udev.old

That worked.  Go figure...

Jerry

---

### Post by cariboo on 2011-07-11
Merged 3 threads about keyboard problems.

---

### Post by rbrick49 on 2011-07-11
Quackers I have found also with the live cd or dvd if I dont use the install option at boot instead I run the live disc the install from install icon on top left of screen thats what works for me on this amd system

---

### Post by iClouseau88 on 2011-07-11
> **jerrylamos said:**
> Well there wasn't any /run/udev so mv /run/udev /run/udev.old didn't work.

So I booted in recovery mode and did:

mkdir /run/udev
mv /run/udev /run/udev.old

That worked.  Go figure...

Jerry

Hi Jerry,

Just updated Ubuntu 11.10 and deleted obsolete packages linux-image-3.0-3-generic, linux-headers-3.0-3 and linux-headers-3.0-3-generic.  Then after reboot, I booted into ubuntu session and encountered the "no mouse" problem. I did not see the recovery mode and I don't know how to get to a terminal.  Can you help me solve these 2 problems?

Thanks a lot for your help.

:(

---

### Post by cariboo on 2011-07-12
To get to recovery mode, hold down the shift key during post.

If your keyboard works press Ctrl-Alt-F1 to get to a console.

---

### Post by Harry33 on 2011-07-12
Here is Martin Pitt's explanation to this bug

> 
Nothing to do with udev, it just causes the initramfs to be rebuilt.

What happens is that apparently due to the recently uploaded base-files there is now a /run directory, which might get partially populated during runtime. Apparently during initramfs time, udev uses /dev/.udev, but then when then initramfs is done, udev gets stopped, and restarted in the "real" system again, at which point it uses /run/udev/. But the latter does not have any of the previously detected properties like ID_INPUT_*, and thus stuff fails all over the place.

As you already figured out, "sudo rm /run/*" will temporarily fix the problem again.

We need to make up our mind here if we want to complete the base-files upload for /run, and adjust initramfs-tools etc. accordingly, or revert it, to avoid having more people fall into this trap.


---

### Post by iClouseau88 on 2011-07-12
> **cariboo907 said:**
> To get to recovery mode, hold down the shift key during post.

If your keyboard works press Ctrl-Alt-F1 to get to a console.

Hello cariboo907 my fellow BC pal,

Thanks for your reply.  I am not sure if your suggestion works in my case.  I have a multiboot system with Win 7, openSUSE (default boot) and a few other Fedora's and Ubuntu's.  

When I boot from Ubuntu 11.10, I see "Input not supported" because I use nvidia-current driver.  After the screen shows Ubuntu 11.10 and the changing dots, the lights are still on the keyboard and the mouse.  Then screen shows "disk drive for / is not ready or not present". After that, the login screen appears but the mouse cursor just sits there.  The mouse light is ON but the keyboard light is OFF. I cannot move the mouse cursor or use the keyboard after this.  

On the GRUB menu, there's a window to allow (kernel)boot options, e.g. "acpi=off", or "nomodeset", etc.  Because the keyboard and mouse are still functioning at this stage of GRUB booting, what should be the boot options/parameters for Oneiric, such that I can get to a terminal? In openSUSE just typing "3" as boot option gets me to runlevel 3, thence to the terminal.

Any other suggestions?  Thanks again!

:confused:

---

### Post by cariboo on 2011-07-12
> **iClouseau88 said:**
> Hello cariboo907 my fellow BC pal,

Thanks for your reply.  I am not sure if your suggestion works in my case.  I have a multiboot system with Win 7, openSUSE (default boot) and a few other Fedora's and Ubuntu's.  

When I boot from Ubuntu 11.10, I see "Input not supported" because I use nvidia-current driver.  After the screen shows Ubuntu 11.10 and the changing dots, the lights are still on the keyboard and the mouse.  Then screen shows "disk drive for / is not ready or not present". After that, the login screen appears but the mouse cursor just sits there.  The mouse light is ON but the keyboard light is OFF. I cannot move the mouse cursor or use the keyboard after this.  

On the GRUB menu, there's a window to allow (kernel)boot options, e.g. "acpi=off", or "nomodeset", etc.  Because the keyboard and mouse are still functioning at this stage of GRUB booting, what should be the boot options/parameters for Oneiric, such that I can get to a terminal? In openSUSE just typing "3" as boot option gets me to runlevel 3, thence to the terminal.

Any other suggestions?  Thanks again!

:confused:

Just select recovery mode from the grub menu, then once at the menu select drop to netroot, then run the following command:

```
mv /run/udev /run /udev.old
```

If that doesn't work, you could use a live cd and chroot your Oneiric / partition, open a terminal and type the following commands:

```
sudo mount /dev/sdX /mnt
sudo mount -o bind /sys /mnt/sys
sudo mount -o bind /dev /mnt/dev
sudo mount -o bind /proc /mnt/proc
sudo chroot /mnt
```

then run the move command above.

**Note:** /dev/sdX = your Oneiric partition.

---

### Post by Quackers on 2011-07-12
iClouseau88, unplugging and re-plugging your mouse and keyboard after booting may allow you to use the keyboard to run the mv command.

---

### Post by Harry33 on 2011-07-12
The latest udev (172-0ubuntu2) + initramfs-tools (0.99ubuntu1) have fixed this bug for now.

Also the warning message ( error: runtime directory '/run/udev' not writeable, for now falling back dev/.udev) is gone.

Booting is a bit prettier. :guitar:

---

### Post by Quackers on 2011-07-12
Yes it is now fixed.
No /run/udev error is a bonus :-)

---

### Post by iClouseau88 on 2011-07-12
> **Quackers said:**
> iClouseau88, unplugging and re-plugging your mouse and keyboard after booting may allow you to use the keyboard to run the mv command.

Quackers, 

Thank you thank you a zillion times!  I am in Oneiric now, but I cannot find "/run/udev" because the search tool fails to find it.

Now what should I do to fix the problem for good?  I will not do any more update until the problem is solved for my PC.

---

### Post by Harry33 on 2011-07-12
> **iClouseau88 said:**
> Quackers, 

Thank you thank you a zillion times!  I am in Oneiric now, but I cannot find "/run/udev" because the search tool fails to find it.

Now what should I do to fix the problem for good?  I will not do any more update until the problem is solved for my PC.

You can do it with nautilus (root)

```
gksu nautilus
```

---

### Post by iClouseau88 on 2011-07-12
Hello Harry33,

Thanks for your reply.  This is the first time I know how to use nautilus!  Anyway, I used a different approach: become root and search for /run/udev in the filesystem.  Found it. Then I renamed it as follows:

```

mv /run/udev /run/udev.old

```

Is this just a temporary fix, or do I need to update Oneiric in order to have a permanent solution?  I am wary and reluctant to update Oneiric!

---

### Post by Quackers on 2011-07-12
The change seems to have worked ok for me and I've rebooted several times :wink:
The new udev version seems to fix it permanently.

---

### Post by iClouseau88 on 2011-07-12
> **Quackers said:**
> The change seems to have worked ok for me and I've rebooted several times :wink:
The new udev version seems to fix it permanently.

Hello Quackers,

My celebration is short-lived, since somehow I borked Oneiric once again!  Via Synaptic I upgraded initramfs-tools to version 0.99ubuntu1, then I was thinking perhaps I should do the same for udev to udev172-0ubuntu2.  Because I saw an exclamation mark to the left of udev172-0ubuntu1, I thought I should rename /run/udev.old to /run/udev before upgrading.

```

mv /run/udev.old /run/udev

```

What a fatal mistake!  After reboot, I cannot load the following sessions: gnome, ubuntu, ubuntu2d, user-defined session (=gnome).  The only session that loads is "Recovery Console", which boots into a black terminal session over a reddish-purple desktop.

Now, which commands lead me back to the normal ubuntu session where everything was fine 1-2 days ago? 

Any suggestions?

---

### Post by jerrylamos on 2011-07-12
> **iClouseau88 said:**
> Hello Quackers,

My celebration is short-lived, since somehow I borked Oneiric once again!  Via Synaptic I upgraded initramfs-tools to version 0.99ubuntu1, then I was thinking perhaps I should do the same for udev to udev172-0ubuntu2.  Because I saw an exclamation mark to the left of udev172-0ubuntu1, I thought I should rename /run/udev.old to /run/udev before upgrading.

```

mv /run/udev.old /run/udev

```

What a fatal mistake!  After reboot, I cannot load the following sessions: gnome, ubuntu, ubuntu2d, user-defined session (=gnome).  The only session that loads is "Recovery Console", which boots into a black terminal session over a reddish-purple desktop.

Now, which commands lead me back to the normal ubuntu session where everything was fine 1-2 days ago? 

Any suggestions?

Boot in recovery mode, at menu go down off the bottom to get root terminal.  Do:
mv /run/udev /run/udev.old

Good luck,

Jerry

---

### Post by iClouseau88 on 2011-07-12
Hi Jerry,

I booted into the only choice = Recovery Console

```

mv /run/udev /run/udev.old

```

After reboot, still couldn't boot into sessions other than Recovery Console.  Recovery Console session brings up a small black terminal on top of a large reddish-purple desktop screen.

```

sudo su
pwd:

#gksu nautilus

```

Found /run has 3 folders: initramfs, mount, udev

(whereas previously /run has 2 folders: udev, motd)

1. Is this content of /run "normal", or something is wrong?
2. Obviously udev has not changed its name to udev.old

Somehow the desktop interface (i.e., gnome, ubuntu, ubuntu2d) is not brought up after signing in.

Any suggestions, anyone?

:(

---

### Post by seeker5528 on 2011-07-13
> **iClouseau88 said:**
> 1. Is this content of /run "normal", or something is wrong?

I think current situation is wrong, in my Debian installation '/var/run/' is a symlink to '/run/', currently in Ubuntu '/run/' and '/var/run/' are both real directories. Doesn't seem to be causing a problem, but I did see in the responses to one of the bug reports an indication that one of these should be a symlink to the other. 

Later, Seeker

---

