---
title: "Using WUBI versus virtualization software"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by LewisR on 2008-04-26
Good evening,

I am anxious to try Hardy.

Is there any benefit to using commercial virtualization software (e.g. vmware, parallels) versus using WUBI, to run Hardy within a Vista environment? 

Thanks in advance,
Lewis

---

### Post by pytheas22 on 2008-04-26
You can't really make a comparison, because wubi and virtualization are not the same things.  wubi, which has nothing to do with virtualization, is just a way to install Ubuntu from within Windows, not to run Ubuntu inside Windows...in other words, if you install via wubi, you need to reboot into Ubuntu in order to use it; you will have a dual-boot set up.  If you install Ubuntu inside a virtual machine, you will be running Ubuntu inside Windows.

Virtualization of course wastes resources, you probably won't be able to use hardware acceleration and so on.  So if you want to get the full experience of Ubuntu, you should install it using wubi (or the live CD using the normal method, which will give you almost the same set up as wubi would).  If you are just trying to tinker a little bit with Ubuntu and want to see what it looks like, a virtual machine would probably be more convenient, since you wouldn't have to reboot from Vista in order to access it.

---

### Post by LewisR on 2008-04-26
Pytheas22,

Thank you for taking the time to respond to my question. After doing some research, I quickly discovered my gaffe and apologize for not first doing my research!! :)

Here's hopefully a more-informed question: I am currently running SuSE Linux Enterprise Desktop and Vista dual-boot. If I install Hardy via WuBI, I know it likes to add the Ubuntu option to the Windows bootloader. But I am currently on the GRUB bootloader (and like it like that) - what will the outcome be?

Also, I downloaded the .iso before I knew that WuBI did that - will I need to download once again through WuBI?

Again, thank you. This community is great and is a very strong attraction to Ubuntu.

---

### Post by sdennie on 2008-04-26
I think the way grub treats Windows means that it will pass on the bootloading sequence to Windows if you select Windows at boot time.  So, if you've installed Ubuntu via Wubi and select Windows via grub, I believe it will "do the right thing".  However, I've not actually tried that so, I could be wrong.

---

### Post by pytheas22 on 2008-04-26
> Also, I downloaded the .iso before I knew that WuBI did that - will I need to download once again through WuBI?

I think I remember there being an option in wubi to copy the needed files from an iso image instead of downloading them, but I could be wrong.  Try looking around the settings.

As for the other question regarding the boot-loader, I agree with the previous poster's conclusion that it would probably do what you want, but I have also never done this myself so I can't make any promises.

If you can afford the space, you could always just do an install on a real partition instead of using wubi; this would definitely set up grub correctly, and Ubuntu is faster if it's on a real partition anyway.

---

### Post by LewisR on 2008-04-26
> **vor said:**
> I think the way grub treats Windows means that it will pass on the bootloading sequence to Windows if you select Windows at boot time.  So, if you've installed Ubuntu via Wubi and select Windows via grub, I believe it will "do the right thing".  However, I've not actually tried that so, I could be wrong.

Thanks for your thoughts. I'm trying it now, so I'll let you know how it plays out, unless anyone else is able to chime in sooner. 

Best,
Lewis

---

### Post by LewisR on 2008-04-26
> **pytheas22 said:**
> 
If you can afford the space, you could always just do an install on a real partition instead of using wubi; this would definitely set up grub correctly, and Ubuntu is faster if it's on a real partition anyway.

Hi,

I'd *love* to do this, but I don't know how to do so properly. In order to install SuSE, I used windows disk manager to shrink and create a nice size partition. SuSE installation performed beautifully.

I tried to shrink again and this time it only offered me 14MB - hardly enough for much. I simply am not sure how to set up another partition for Ubuntu without royally breaking stuff.

Thanks again,
Lewis

---

### Post by sdennie on 2008-04-26
I'm not an expert on NTFS but, you could try to defragment your Windows partition and see if it then gives you more space for the resize.

---

### Post by marine63 on 2008-04-26
one for virtual wubi just screws up my computer 
also vmware can install ubuntu on physical drive and can dual boot it

---

### Post by LewisR on 2008-04-26
Wow, really impressive. I am typing this reply in Hardy, by way of WuBI.

1) The behavior vis-a-vis bootloader was as you predicted - I select "Windows" in GRUB and then Ubuntu in the Windows bootloader. No big deal.

2) I'd love to say everything is wonderful but Ubuntu is crashing for me at reboot/shutdown. Rather than rebooting or shutting down, it hangs at the Cylon screen, no orange back-and-forth, just empty Cylon bar.

Any thoughts on a fix, or should I attempt to re-install via a new partition (somehow?) and see if that helps?

Thanks in advance-  this is really amazing stuff.

best,
Lewis

---

### Post by LewisR on 2008-04-26
> **marine63 said:**
> 
also vmware can install ubuntu on physical drive and can dual boot it

Hi -thanks for your reply - would you mind explaining the above? (or pointing me towards an explanation?) Thanks again!

---

### Post by pytheas22 on 2008-04-26
To troubleshoot this, select shutdown/reboot and then immediately press control-alt-f1.  You should be dumped to a screen displaying messages about what the system is doing as it shuts down.  Do you see any error messages as it goes down, or is it hanging at a certain step?  If not there are ways to look deeper, but hopefully this will tell us what's wrong.

and control-alt-f7 of course brings you back to the graphical screen, just so you know.

---

### Post by LewisR on 2008-04-26
Thank you again for your help. I decided to install "for real" in the space now formerly held by SuSE.

I've made it as far as the Partitioner in the live-cd. However, I am afraid to commit without having a better sense of which options I should select.

I successfully created some "free space" in Vista and indeed want to use that. So I selected it and hit New Partition.

Type: Primary or Logical?
New Partition Size: My choice, right?
Location: Beginning or End?
Use as: Ext3 journaling file system (or a slew of other options) ?
Mount point?

I would greatly appreciate some guidance on the above. Again, thank you - you are wonderful!

best,
Lewis

---

### Post by LewisR on 2008-04-26
Or am I safe simply doing "use largest continuous free space?" I freed up about 60GB as "unallocated space" in Vista - will it capture that?

Thanks,
Lewis

---

### Post by LewisR on 2008-04-26
Phew. Using that option indeed preserved my Vista install seemingly just fine. My hands are still shaking however. :)

Booting into Ubuntu now and hoping for the best... and hoping the reboot/shut down issue has resolved. Will report back shortly.

Best!

---

### Post by LewisR on 2008-04-26
Darn. Unfortunately, I still get hung at the blank cylon screen (all the orange goes away, then it hangs.) Attempting a ^-ALT-F1 does not respond, nor do my keyboard lights (e.g. num lock, caps lock, etc.) and I am forced to a hard shut down.

Any thoughts?

Thank you,
Lewis

---

### Post by pytheas22 on 2008-04-27
> Darn. Unfortunately, I still get hung at the blank cylon screen (all the orange goes away, then it hangs.) Attempting a ^-ALT-F1 does not respond, nor do my keyboard lights (e.g. num lock, caps lock, etc.) and I am forced to a hard shut down.

Sorry to hear about this problem and sorry the control-alt-f1 thing isn't working (make sure you are pressing this combination immediately after you click the shut down button).

It could be that the system is going through the shutdown sequence properly, but for some reason is not issuing the very last command, which cuts power to the machine (or reboots).  In this case it's not a really big deal; beyond the inconvenience of having to manually power it off, you're not risking damage to your disks or anything as long as they're unmounted properly as shutdown occurs.  On the other hand, there could be some kind of worse problem.

One thing to try is to issue the command:
```

sudo shutdown -h now
```

and see if it shuts down properly there.  That command specifically tells the system to shut off; I'm not sure which commands the gnome shutdown button issues but if it's different, this could be the problem.

If that doesn't work, the next thing to do is look at the system log (System>Administration>System Log).  Look especially at "messages,"  "syslog" and "kern.log."  Look at the timestamps that pertain to when the system was shutting down, and see if there are any error messages.

Also, what kind of hardware do you have?  And did you ever have similar problems running suse?

---

### Post by LewisR on 2008-04-27
Thank you for your response. I did some digging on these forums, and apparently what I am seeing is very similar to (or the exact same thing as) what others have seen in previous distros of Ubunto - lots of "Network Manager" messages followed by the empty cylon screen, forcing a hard shut-down. I tried three of the solutions I saw proposed:

- adding reboot=b to the GRUB config file
- doing a network.stop before rebooting
- logging off of gnome before rebooting 

Unfortunately, none has worked. I am on a Dell XPS 410 and I did not have this problem with SUSE. My next attempt will be to try "sudo shutdown -h now" and I will report back.

I do not hear any drive movement on that screen (and the keyboard becomes totally unresponsive) - are the chances OK that I'm not doing any HDD damage with my hard resets?

Thanks again and have a good night,
Lewis

---

### Post by marine63 on 2008-04-27
[http://ubuntuforums.org/showpost.php?p=4789240&postcount=6](http://ubuntuforums.org/showpost.php?p=4789240&postcount=6)

---

### Post by pytheas22 on 2008-04-27
> I do not hear any drive movement on that screen (and the keyboard becomes totally unresponsive) - are the chances OK that I'm not doing any HDD damage with my hard resets?


Yes, probably (but I emphasize probably).  Also if you were causing problems to the hard drive you would most likely be told during the next reboot that fsck is fixing them (at least, that always happened for me on 7.10 whenever my reiserfs file system was not unmounted properly before shutdown).  But try the shutdown -h command (or shutdown -r to make it reboot instead of shutdown) and see if that helps.  I'll be back sometime tomorrow.

---

### Post by LewisR on 2008-04-27
> **pytheas22 said:**
> Yes, probably (but I emphasize probably).  Also if you were causing problems to the hard drive you would most likely be told during the next reboot that fsck is fixing them (at least, that always happened for me on 7.10 whenever my reiserfs file system was not unmounted properly before shutdown).  But try the shutdown -h command (or shutdown -r to make it reboot instead of shutdown) and see if that helps.  I'll be back sometime tomorrow.

Good morning,

Thanks for the tip .... unfortunately it yields the same result... throws a bunch of NetworkManager errors, followed the deadish ubuntu screen and unresponsive keyboard, forcing  hard shutdown.

Will keep digging around... this would be much easier if I weren't a Linux newbie.... I feel as if I'm trying to fly through bad weather, except I don't know how to fly :)

Best,
Lewis

ETA: I think it is [this bug]("http://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/183568") but I am not 100% sure as this does not refer to 8.04.

---

### Post by pytheas22 on 2008-04-27
If you have an ATI video card, it could be that bug.  You could try installing wicd as someone suggests in that bug report and see if it helps.

I also found another bug at [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/42160](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/42160) that suggests it's a problem with different kinds of BIOS and certain versions of the kernel.  Unfortunately, there's no work around.

Also, what happens if you press control-alt-f2, login at that terminal, and type "sudo shutdown -h now" there?  This would help isolate problems related to X/graphics drivers.

---

### Post by LewisR on 2008-04-27
Thank you for sticking with me on this during your weekend!

By turning off "roaming mode" in Network manager, I am now able to shutdown nicely (via the GUI and via the command you provided me with). However, rebooting remains unchanged. I guess that's less-awful, but would still love to come up with a more elegant fix.

Thank you again,
Lewis

P.S. Although shutting down works and rebooting still does not, shutting down still throws the Network manager errors previously described. It just happens to turn off afterwards now though.

---

### Post by pytheas22 on 2008-04-27
I'm glad you seemed to have tracked down the source of the problem and found a workable solution.

> By turning off "roaming mode" in Network manager, I am now able to shutdown nicely (via the GUI and via the command you provided me with). However, rebooting remains unchanged. I guess that's less-awful, but would still love to come up with a more elegant fix.

In light of this, it definitely sounds like NM is causing the problem.  You could try installing wicd, [http://wicd.sourceforge.net](http://wicd.sourceforge.net).  Personally, I like wicd better anyway; NM seems to be the cause of a lot of problems for a lot of people.

Another solution would be to write a custom shutdown script that would kill NM before powering down.  It could look something like:
```

if ps -e | grep NetworkManager
then kill $(ps -e | grep NetworkManager)
fi
if ps -e | grep NetworkManager
then kill -9 $(ps -e | grep NetworkManager) #to make sure it's really dead; sometimes NM likes to not close with the normal kill command
fi
shutdown -h now
```

this is brute-forced and it's been a while since I've written bash scripts, so don't assume these commands would definitely work.

If you use this approach, you could create a button in Gnome to launch the script (using gksudo) to make it easy and elegant.

---

### Post by LewisR on 2008-04-27
Pytheas22, 

Thank you again for your response. At the risk of asking two dumb questions:

1) If I uninstall Network Manager, how will I download and install WICD (as I will no longer have a network connection?

2) When situations call for a reboot (e.g. install new software, etc.) would it  be sufficient to simply log out and then back in as opposed to rebooting my machine? Or does that not do what a reboot needs done?

Best,
Lewis

---

### Post by pytheas22 on 2008-04-27
> At the risk of asking two dumb questions:


there are no dumb questions; how else would you learn about Linux?

1. you can download the debian package for wicd from the website and install it.  It will force you to uninstall Network Manager at that time, but it's ok because wicd will be immediately installed in its place.  So you won't be left without a connection manager.  But that doesn't matter anyway because once Network Manager has gotten you connected after your computer boots, it doesn't need to do anything (it does do things, but none of them are necessary to keep your connection alive), so you'd still have a connection till the next reboot.  You could also always connect via the command line (there are guides on this forum; it's not as hard as you might think) as a last resort.  And beyond all that, Network Manager can be installed from the Ubuntu CD, so you don't need to be online to get it back if wicd fails.

2. in Linux, the only time you really need to reboot is if you upgrade the kernel.  Everything else is designed to be modular so that you can restart just that one piece of your system.  There are probably exceptions to this, and sometimes it's just easier to reboot instead of figure out which part of the system to restart, but in general you should never have to reboot unless you're explicitly told to do so (I believe that a little bubble will pop up in Ubuntu to tell you if you need to, although unlike the Windows bubbles, it is kind enough to take no for an answer the first time and lets you keep working until you're ready to reboot).  So I'm wondering, which software are you installing that you're thinking calls for a reboot?

---

### Post by LewisR on 2008-04-29
> **pytheas22 said:**
> 

2. in Linux, the only time you really need to reboot is if you upgrade the kernel.  Everything else is designed to be modular so that you can restart just that one piece of your system.  There are probably exceptions to this, and sometimes it's just easier to reboot instead of figure out which part of the system to restart, but in general you should never have to reboot unless you're explicitly told to do so (I believe that a little bubble will pop up in Ubuntu to tell you if you need to, although unlike the Windows bubbles, it is kind enough to take no for an answer the first time and lets you keep working until you're ready to reboot).  So I'm wondering, which software are you installing that you're thinking calls for a reboot?

Sorry for the delay in getting back to you. The reason I ask about rebooting versus logout/back in is because I am trying to mitigate against the reboot issue I am having - but to your point, I have not encountered anything yet (save for the ATI drivers) that asked me specifically to reboot.

Thank you again,
Lewis

---

