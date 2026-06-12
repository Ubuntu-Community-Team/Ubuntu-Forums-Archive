---
title: "could I have the same ubuntu on vbox and harddisk?"
date: 2011-09-18
forum: New to Ubuntu
---

### Post by shevin on 2011-09-18
guys I wonder if it is practical,
 I want to install ubuntu on my laptop as dualboot ,
and the times that I am in windows, I wanna be able to have the same ubuntu in virtualbox, (I mean the same data and hard disk) could I make virtualbox to use a reall partition instead of VDI file ? is this idea practial or I better forget it .

---

### Post by Lisiano on 2011-09-18
Technically it is possible. Practically I don't think you should try this as you can seriously mess up your hard drive.

---

### Post by anewguy on 2011-09-18
I know you can do the opposite - you can have Linux running as the host and the virtualbox Windows as a guest using an existing Windows installation.  It's not recommended.  I can't state that strong enough.  I've done it, and it creates a whole bunch of virtual devices, so Windows thinks it's on new hardware and makes you re-register.  And don't think about going back to boot just Windows after having done so.  Some might say "I did it" - well, so have I, and I'm telling you don't.

Since Windows will be virtualizing devices to a Linux guest in what you want to do, I can't help but see problems down the road.  So my suggestion here again is don't do it.

I can understand why you might want to do this, but I think you are just looking for some really big headaches not too far down the road.

Dave ;)

---

### Post by Lisiano on 2011-09-18
Lets just say. I ran my Ubuntu installation as both my Guest and Host (Yes, I actually did it. Still regret it). Next time I rebooted, I got greeted by a nasty FSCK error stating I can't continue untill I manually FSCK it.
Running a Linux guest is no problem at all, Linux has all drivers you will need for both actual hardware and virtual hardware (I booted off my old Ubuntu install on a PC I was lent to restore my files). The problem lies in that if Linux mounts your Windows drive, say goodbye to Windows.

---

### Post by anewguy on 2011-09-19
If you mean a Linux host and a Windows guest, then yep - that's what I was saying.  It just totally ruined my Windows installation.  At some point "something" happened - never was able to trace it - that caused the partition with Windows on it to no longer even attempt to boot.  Reinstalling Windows was the only option, but since I had more than 1 CPU and more than enough other resources, I just ran Linux as the host and my Windows was all in a VM.  Made life easier! ;)

Hope you get a chance to get caught up on your school work.  It's so easy sometimes to just get kind of "glued" to the forum, but always remember a good education comes first!  ;)

Later -

dave ;)

---

### Post by Lisiano on 2011-09-19
Well I ran my Ubuntu install which was BOTH my Guest AND Host. Was fun. They both were independent and worked flawlessly until I powered down the VM then rebooted my host, rest you know. And meh at school. Boring here. Arithmetic progressions. If only we had something like LUA scripting or SH scripting. I could at least waste my time more effectively.

Okay. Going offtopic. In short. ***_[COLOR="Red"][SIZE="4"]Do. Not. Run. Your. Ubuntu. Physical. Install. In. A. VM.[/SIZE][/COLOR]_***
Kay. Should be good enough.

---

### Post by haqking on 2011-09-19
yes it can be done, i usually clone my real partition and have it running in a VM but if you want it to reflect the changes made either side then yes it can be done, however not a great idea.

[http://en.gentoo-wiki.com/wiki/Running_a_VirtualBox_Guest_from_a_Real_Partition](http://en.gentoo-wiki.com/wiki/Running_a_VirtualBox_Guest_from_a_Real_Partition)

this is gentoo based but same things apply.

and this is windows but again same rules apply pretty much.

[http://forums.virtualbox.org/viewtopic.php?t=9697](http://forums.virtualbox.org/viewtopic.php?t=9697)

I am sure there is a Ubuntu specific guide out there somewhere, it is not too difficult but you do risk losing some data so make sure you have a complete backup and preferably a clone of your sytem to revert back to normal in the event something goes wrong.

and a few more

[http://blog.amhill.net/2010/01/27/linux-ftw-using-virtualbox-with-an-existing-windows-partition/](http://blog.amhill.net/2010/01/27/linux-ftw-using-virtualbox-with-an-existing-windows-partition/)

[http://ubuntuforums.org/showthread.php?t=664692](http://ubuntuforums.org/showthread.php?t=664692)

---

