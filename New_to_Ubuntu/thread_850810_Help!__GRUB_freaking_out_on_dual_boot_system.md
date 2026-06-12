---
title: "Help!  GRUB freaking out on dual boot system"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by The Rocker on 2008-07-06
I just installed Ubuntu yesterday on my HP Pavilion laptop, and made it dual boot with Vista which had previously been installed.  Everything worked perfectly, I was able to boot to either OS just fine, Ubuntu detected all my hardware correctly, etc.  I was very happy... so I thought.

I'd been working in Ubuntu all day today, then I booted to Vista, which worked fine, and I certainly didn't do anything out of the ordinary while in Vista.  Then I went to reboot back to Ubuntu, and now, all of a sudden I get "GRUB loading stage 1.5" for a second, then it just restarts again and I get the HP screen.  Then "GRUB loading stage 1.5" again for a second, then the HP screen again... well you get the idea.  It doesn't stop.  Just keeps endlessly restarting the computer and I never get the bootloader screen at all, so I can't boot to anything!

Help!  How do I fix this and why did it happen?

---

### Post by Sef on 2008-07-06
Does it give you an error message too?  If so, what number is it?

---

### Post by The Rocker on 2008-07-06
No, it doesn't give any error message.  It says "GRUB Loading Stage 1.5" for a few seconds, then the screen goes black for a few seconds, then it restarts.  Keeps doing that till I power down completely.

I can still boot from the live Ubuntu CD and I can still see all of the partitions from there.

---

### Post by bumanie on 2008-07-06
Boot live cd and go into terminal and post output of > sudo grub  > find /boot/grub/stage1

---

### Post by The Rocker on 2008-07-06
It says (hd0,4)

---

### Post by toucher5 on 2008-07-06
The best thing I have found that helps when having problems with GRUB is the Super Grub boot disk. It doesn't require really any knowledge of GRUB. Just burn the ISO to a cd and choose the autoconfigure grub option.

Hope this helps.
Josh @ digitalvaldosta.com
:guitar:

---

### Post by bumanie on 2008-07-06
You can try super grub disc, it often works well. If not from live cd post output of > sudo fdisk -l (that's a lower case L)

---

### Post by The Rocker on 2008-07-06
Here is the output...

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x13882b5f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9362    75194416    7  HPFS/NTFS
/dev/sda2           18593       19457     6948112+   7  HPFS/NTFS
/dev/sda3            9363       18592    74139975    5  Extended
/dev/sda5            9363       18210    71071528+  83  Linux
/dev/sda6           18211       18592     3068383+  82  Linux swap / Solaris

Partition table entries are not in disk order
-----------

I'll try that Super Grub Disk, I found it online actually and was going to ask if anyone had had good experiences with it.

---

### Post by bumanie on 2008-07-06
Try super grub disc first if you like - it is a good tool that often sorts grub problems out. Even if it doesn't fix grub it will often be able to boot the windows and/or ubuntu partition and once inside the OS, it is easier to track down problems. Post back if sgd doesn't work and we'll go on from there.

---

### Post by The Rocker on 2008-07-06
OK, thanks all... I'm going to bed now but I'll give SGD a go in the morning.

---

### Post by rsaavedra on 2008-07-06
Did you install any update in Vista right before that loop happened?

I ask because it is known that Service Pack 3 for Windows XP does cause a booting loop with some Compaq machines, on its own, without any dual boot configuration required.  I understand it's a problem with the BIOS in those Compaq machines it seems.  Since yours it's an HP (which purchased Compaq,) I wonder if there might be something similar happening here.

---

### Post by akarmenia on 2008-07-06
If you would like to install XP and Ubuntu on the same computer, you can try my tutorial wiki at:

[http://aramk.wikispaces.com/Ubuntu+XP+Dual+Boot]("http://aramk.wikispaces.com/Ubuntu+XP+Dual+Boot")

I have step-by-step instructions and screenshots. Hope it helps!

Also, if you only need Ubunutu, then you can ignore the XP steps.

---

### Post by The Rocker on 2008-07-06
> **rsaavedra said:**
> Did you install any update in Vista right before that loop happened?

I ask because it is known that Service Pack 3 for Windows XP does cause a booting loop with some Compaq machines, on its own, without any dual boot configuration required.  I understand it's a problem with the BIOS in those Compaq machines it seems.  Since yours it's an HP (which purchased Compaq,) I wonder if there might be something similar happening here.

I did install SP1 for Vista right before I installed Ubuntu.  However as mentioned, everything worked fine when I first installed Ubuntu and I could boot either OS just fine.

I've just burned the Super Grub Disk so will let you know how that works...

---

### Post by The Rocker on 2008-07-06
OK, I ran the Super Grub Disk.  It didn't seem to give me any options for fixing the dual-boot grub, only for one OS or the other.  I chose Windows, and it successfully fixed the MBR and GRUB so that the machine now boots only to Windows.  But it least it boots!

So now what?  How do I get it to dual boot again?

---

### Post by The Rocker on 2008-07-06
Aha!  I told SGD to fix the MBR and restore GRUB in Linux, and that did it! It brought back my dual boot menu.  Yay!  Thanks for the recommendation!

Now I'd like to consider this problem solved, except that I have no clue what caused it to happen, which of course makes me nervous because I'm afraid it could happen again at any time, for no apparent reason.  Anyone have any clue?  I will keep an eye on it, and keep my Super Grub Disk very handy meanwhile.

---

### Post by caljohnsmith on 2008-07-06
I agree with the previous posters, I think that your Vista update is most likely the culprit.

---

### Post by bumanie on 2008-07-06
I'm glad super grub disc worked. Was it the vista upgrade to sp1? Maybe. Was it somehting else? Maybe. Sometimes *ubuntu kernel wreak havoc on some users systems. It's sometimes hard to tell, but if sp1 wrote anything to the mbr - look no further.

---

### Post by The Rocker on 2008-07-06
But, to be clear - I had never had Ubuntu installed on this machine or tried to set up dual boot until *after* I'd done the SP1 update on Vista.  And it did work right away, it just failed inexplicably after one day.  If SP1 was going to write anything to the MBR it would have done so when I first updated (prior to ever messing with GRUB or Ubuntu), wouldn't it?

Not that I'm not perfectly willing to blame Vista - I hate it. :D  It took me 3 hours to do the SP1 update because I had to fix my registry and assign admin permissions to my whole filesystem before it would install... of course one shouldn't need "God" permissions to install the patch and if one does need admin permissions for anything, it should just ask for the admin password like any self respecting OS. ;)

In fact I'd been wanting to install Ubuntu for some time because Vista sucks so bad, and my "upgrade" fiasco was what finally sent me over the edge. :)

---

### Post by bumanie on 2008-07-06
You are certainly correct - if sp1 was installed prior to ubuntu even going on the computer, there is no way sp1 could have caused it - it may have been a kernel update or some other conflict within ubuntu. Mind you a friend of mine had their vista mbr corrupt for no obvious reason, so if that happened, that would upset grub's pointer within the mbr and cause grub to malfunction. 
Just be happy :) that's it's all fixed. If it happens again, you have super grub disc and if that fails, post to the forum. There will be someone who can help.

---

### Post by The Rocker on 2008-07-06
Yes, I think I'll run chkdsk and a defrag on the Vista partition, just to minimize any potential problems there.  And then I'll stay out of Vista as much as possible. ;)

Thanks guys.

---

### Post by The Rocker on 2008-07-09
Ack!

I thought this was solved, but it seems now that although I can reboot as many times as I like in Ubuntu, any time I boot to Vista, the problem returns on my next reboot, and I have to use Super Grub Disk to fix it again.

WTF?  :confused: Is Vista somehow messing with the MBR every time it starts?

---

### Post by ubume2 on 2008-07-09
Can you boot into Windows with Super Grub Disk?

Your problem is the one of the reasons I have avoided Vista.  I avoid my XP as much as possible as it takes 3-4 minutes after boot before it is usable.  Spend 95% of my time in Ubuntu or Linux Puppy.

Good luck.

---

### Post by The Rocker on 2008-07-09
Yes, once I fix the GRUB bootloader in Linux with SGD, I can boot to either Ubuntu or Windows just fine.  However, once I boot to Windows, if I then restart again I have the problem again.  Whereas I can boot to Ubuntu over and over with no problem.

And yes, I wish I could avoid Vista altogether, which I mostly have since installing Ubuntu... that's why this problem didn't come up again for several days. :D

---

### Post by ubume2 on 2008-07-10
Well, not that I would be any help, but maybe some expert would know the solution if you posted menu.lst from Ubuntu. It may be barking up the wrong tree, though. The problem is most likely in Vista itself. Maybe boot.ini.

Edit: but first, try this:
```
$sudo grub
>find /boot/grub/stage1   ##I think you've already done this
>root (hd0,4)
>quit
```

Then try to reboot in Windows.  If that doesn't solve the problem, then proceed with this:

```
$ gedit /boot/grub/menu.lst         note:not sudo gedit
```  

I ran across this in:

[http://ubuntuforums.org/showthread.php?t=789120&page=2](http://ubuntuforums.org/showthread.php?t=789120&page=2)

> **Pumalite said:**
> When you use Vista; you have to allocate free space for Ubuntu with the Vista partitioner. You cannot partition with the Ubuntu CD. Give thanks to Microsoft.

The poster's problem was slightly different, but points to Vista's unfriendliness to other OS's

I searched Ubuntu's sites and couldn't find any howto's or posts on how to dual boot Vista and Ubuntu.  There are probably lots of folks who have Vista and are double booting from the same HD.

Here are three urls that might help you.

[http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm](http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm)

[http://port25.technet.com/archive/2006/10/13/Using-Vista_2700_s-Boot-Manager-to-Boot-Linux-and-Dual-Booting-with-BitLocker-Protection-with-TPM-Support.aspx](http://port25.technet.com/archive/2006/10/13/Using-Vista_2700_s-Boot-Manager-to-Boot-Linux-and-Dual-Booting-with-BitLocker-Protection-with-TPM-Support.aspx)

[http://www.pronetworks.org/forum/about78184.html](http://www.pronetworks.org/forum/about78184.html)

Also, I think there is a way you can boot directly into Vista by using Super Grub Disk without changing grub. 

If you choose Language & help in the menu choose windows >>boot windows
else !WIN!  That boots windows for me (at least for XP)

---

### Post by kansasnoob on 2008-07-10
Look at page #4 of the following tutorial for an alternative option to using GRUB:

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

I'd rather find a way to keep GRUB but if the problem simply persists Ad-nauseam and you can't find a better way, using the Vista Boot-Loader would be an alternative.

---

### Post by acrosome99 on 2008-07-23
I just had the exact same problem with an XP dual boot with Hardy on my wife's laptop.  It started when my wife was in XP and Phoenix cME told her there was a problem that needed to be fixed, so she told it to fix it.  Apparently it wiped out the MBR or whatever.  (Of course, she blamed me rather than Microsoft or herself.)  I burned a Super GRUB Disk ISO on my desktop and popped it in, and told it to fix the MBR to boot Linux.  Now GRUB works normally, and both Ubuntu (several kernels) and XP are selectable at boot as expected.  I have disabled Phoenix.

Does Vista have something like Phoenix cME that works automatically?  If so, then I can see why Rocker has the problem after every Vista reboot.

This is EXACTLY why Linux doesn't allow everyone superuser privileges by default...

Anyway, I figured out how to fix this problem by reading this thread.  So thanks, everyone!

---

### Post by The Rocker on 2008-07-23
Well I'm glad my thread helped somebody. :D  I guess that works for XP but not Vista.  I tell Super Grub Disk the same thing as you do, and it works so long as I don't boot to Vista and then try to boot again. :D  It must be that Vista has something that automatically messes with the MBR.

I haven't solved the problem yet, because I haven't had time to mess with it any further.  Luckily I haven't needed to boot to Vista very often.  But one of these days I will mess with it some more, and if anyone else comes up with any bright ideas meanwhile, I'd appreciate it.

---

### Post by philinux on 2008-07-23
Well thus looks promising.

Needs a good read.

[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm?page=5](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm?page=5)

---

### Post by The Rocker on 2008-07-23
AHA!  So Vista SP1 DOES hose the bootloader! :mad:

Well, I'll have to try that.  Thanks for posting!

Windows is so lame, it manages to hose up your machine even when you're not running it. :mad:

---

### Post by Sigma on 2009-04-11
The Rocker, did you eventually get this problem fixed?  I'm having the EXACT same issue.  I'm dual-booting Windows Vista and Ubuntu, and EVERY time I use Vista, it wipes out my MBR, and I need to use SGD or a live CD to restore grub.

---

### Post by meierfra. on 2009-04-12
Sigma:  You need to install Grub without the stage1.5 files:

[http://www.supergrubdisk.org/wiki/WindowsErasesGrub](http://www.supergrubdisk.org/wiki/WindowsErasesGrub)

---

### Post by nandemonai on 2009-04-12
Thanks for the info guys, I'm sure this will come in handy one day.

Wish MS would get with the program and realise that even though they may have majority market share that does not mean everyone wants one operating system on their machine.

Rude Bill.. Just Rude. -.-

---

### Post by The Rocker on 2009-04-13
> **Sigma said:**
> The Rocker, did you eventually get this problem fixed?  I'm having the EXACT same issue.  I'm dual-booting Windows Vista and Ubuntu, and EVERY time I use Vista, it wipes out my MBR, and I need to use SGD or a live CD to restore grub.

No, I never did get it fixed.  Well, I haven't really tried that hard, because I hardly ever boot to Vista anyway.  Those few times that I do, I just use Super Grub Disk to boot again.  Somewhat of a pain, but to this point I haven't thought it worth the time to keep messing with it.

If anyone else comes up with a good solution, I hope they post it!

---

### Post by meierfra. on 2009-04-13
The Rocker: Did you try my suggestion from post 31?

---

### Post by The Rocker on 2009-04-13
> **meierfra. said:**
> The Rocker: Did you try my suggestion from post 31?

No, but it definitely looks like it's worth trying.  Now if I can only find the time and inclination to mess with it. :D

Thanks much for the post though.

---

### Post by meierfra. on 2009-04-14
> Now if I can only find the time and inclination to mess with it

It should only take a few minutes and you will make me very happy.

---

### Post by Sigma on 2009-04-30
Thanks, meierfra.  I didn't try your approach because I actually (seemingly) got it working another way.  To be honest, I'm not sure whether what I did is a good approach and whether it'll work for everyone, so proceed with caution.

I noticed in my /boot/grub/menu.lst file that the "makeactive" flag was set under the Windows Vista boot info, so I commented it out.

Here's a snippet from my old /boot/grub/menu.lst:

```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows Vista/Longhorn (loader)
root            (hd0,1)
savedefault
makeactive
chainloader     +1

```

Here's what I modified that snippet to:

```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows Vista/Longhorn (loader)
root            (hd0,1)
savedefault
#makeactive
chainloader     +1

```

I have been using this configuration for several weeks, switching between Ubuntu and Vista numerous times (even having performed several Vista upgrades) and everything seems to be working fine.  But again, I'm not 100% sure about what the makeactive flag does, so be careful.

---

### Post by meierfra. on 2009-05-01
> I noticed in my /boot/grub/menu.lst file that the "makeactive" flag was set under the Windows Vista boot info, so I commented it out.
Removing "makeactive" is fine. But since that  cured your problem, I think that your case must be different from The Rocker's

Did you have the same symptoms as The Rocker?
Or did  just boot straight into Vista each time after you booted into Vista from the Grub menu?

Just so that I can  give  other  people  with the same problem better help, could you boot into  Ubuntu and  download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post (use the code tags)

Thanks.

---

