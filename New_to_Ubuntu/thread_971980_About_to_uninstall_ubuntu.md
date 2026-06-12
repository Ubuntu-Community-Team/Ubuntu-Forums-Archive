---
title: "About to uninstall ubuntu"
date: 2008-11-05
forum: New to Ubuntu
---

### Post by hfp on 2008-11-05
Hey, everyone.  I'm about to uninstall ubuntu, if I can figure out how to do it without destroying my computer, because of the following reason.  Maybe one of you can help me with my problem with Ubuntu.  I like Ubuntu but the disk partition is killing me.  I have a 500 gigabyte harddrive and ubuntu is using around 450 gb, leaving windows with around 20gb.  So I have very little space on windows vista, and I like Windows Vista because I can play games on it.  Does anyone know how to change the disk partitions easily or does it almost always require a very risky procedure?  Thanks a lot.

---

### Post by logos34 on 2008-11-05
normally Gparted can handle just about any partitioning task.

Post the output of

** sudo fdisk -l**

To resize/shrink the 450 gb's with ubuntu and expand the vista partition you'll have to work from the ubuntu live cd (/ cannot be mounted during the operation).

Boot into the live cd desktop.  System>admin>Partition Editor (gparted)

shrink ubuuntu and then grow windows into the empty space.  Reboot into windows--error check/chkdsk should run automatically

---

### Post by hfp on 2008-11-05
Thanks, logos34, but I think I just want to get rid of Ubuntu completely.  All of this disk partition stuff seems to risky.  Where's the easy uninstall function that Ubuntu advertised?  Ugh, this looks like a headache.  Ubuntu should make it clear that once you install it, it's going to be hard to get rid of it should you ever want to.

---

### Post by chrisod on 2008-11-05
Have you ever tried to uninstall Windows? Complaining about Ubuntu because you haven't made the effort to understand it is not productive.

If you format the Ubuntu partition from the Windows partition manager it will be gone, then you can give it a new drive letter and use it as a data drive. I think that is all possible from within Windows without worrying about live CDs and without resizing partitions.

---

### Post by hfp on 2008-11-05
> **chrisod said:**
> Have you ever tried to uninstall Windows? Complaining about Ubuntu because you haven't made the effort to understand it is not productive.

If you format the Ubuntu partition from the Windows partition manager it will be gone, then you can give it a new drive letter and use it as a data drive. I think that is all possible from within Windows without worrying about live CDs and without resizing partitions.

I haven't tried to uninstall Windows because I like Windows. :D

How can I use the Windows partition manager to completely get rid of Ubuntu?

---

### Post by LowSky on 2008-11-05
> **hfp said:**
> How can I use the Windows partition manager to completely get rid of Ubuntu?

Maybe you should ask that on a Windows Help  Forum...  :lolflag:

Right click on my computer, go to manage, then go to disk management, clcik on partition you want to mess with, choose format

to get rid of GRUB you will need your windows recovery CD

---

### Post by CatKiller on 2008-11-05
> **hfp said:**
> I like Ubuntu but the disk partition is killing me... Does anyone know how to change the disk partitions easily or does it almost always require a very risky procedure?  Thanks a lot.

Technically, disk partitioning is ever-so-slightly risky. This will be true whether you resize your Ubuntu partition or delete it entirely.

Since you've said that you like Ubuntu aside from the partition mis-configuration, it's probably worth persevering. It's straightforward to fix.

Boot from your Ubuntu cd (since you can't use a program on a partition to fiddle around with that partition). Select whichever is the first option - the one that lets you try Ubuntu and gives you the Ubuntu Desktop. Go to System -> Partition Editor.

After a while - it needs to read the drive layout - you'll be presented with a graphical image of your hard drive. Drag the right end of the Ubuntu partition to make it smaller. Drag the Ubuntu partition to the right. Make the Vista partition larger, again by dragging the right end. Hit Apply. Wait while it does its stuff. Reboot. Problem solved.

---

### Post by raydeen on 2008-11-05
If you really want to get rid of Ubuntu, follow the steps above using the Live CD. You could delete all the Ubuntu partitions ('/' and '/swap'), resize the Windows partition and reboot. You'll still have the Grub menu and be able to access Windows through that. If you want to get rid of Grub completely, follow the instructions from the link below. You'll need your original Windows CD in order to do this. You'll run a program called fixmbr to get rid of Grub and replace it with the Windows bootloader.

[http://askbobrankin.com/fix_mbr.html](http://askbobrankin.com/fix_mbr.html)

As for Ubuntu being easy to uninstall, that really only applies if you used the wubi installer to basically put it in your Windows partition.

---

### Post by bodhi.zazen on 2008-11-05
You can remove Ubuntu, basically you just delete or reformat the Ubuntu partitions any way you wish.

Your computer will then not boot windows :twisted:

To fix that you need to restore the windows boot loader.

See this thread : [http://ubuntuforums.org/showthread.php?t=508927](http://ubuntuforums.org/showthread.php?t=508927)

---

### Post by hfp on 2008-11-05
Ok, I used gparted live to try to shrink ubuntu's harddrive space and expand vista's, but I was only able to shrink ubuntu's space.  It would never let me expand vista's space.  In other words, I can't drag the bar to give myself more space for vista.  It's as if the drive for Ubuntu has all the memory and that memory can't be placed anywhere else.  It can only be shrunk, but this doesn't do me any benefit since vista is still unchangeable.

---

### Post by Paqman on 2008-11-05
> **hfp said:**
> Where's the easy uninstall function that Ubuntu advertised?

To use it you would have had to install using an installer called Wubi.

Wubi works by creating a virtual hard drive on your Windows partition and installing Ubuntu onto it. If you don't like partitioning then you'll probably like Wubi.

To use it, just boot into WIndows and pop your LiveCD in the drive. Wubi is seriously easy to use, you could be installed and ready to go in 20 mins on a decent machine.

---

### Post by hfp on 2008-11-05
It seems like I am going to have to learn to partition my hard drives if I want to solve this problem.  The thing is, when I try to extend the space available for vista, it won't let me, even if I shrink the size of vista's hard drive.  Why is this?  What should I do?  I really appreciate your help.

---

### Post by ad_267 on 2008-11-05
Can you post the output of "sudo fdisk -l" or a screenshot from gparted so we can see what your partitions are like. It should let you expand the vista partition.

---

### Post by hfp on 2008-11-06
> **ad_267 said:**
> Can you post the output of "sudo fdisk -l" or a screenshot from gparted so we can see what your partitions are like. It should let you expand the vista partition.

I'm sorry.  I haven't used Ubuntu much lately.  How do I post the output of "sudo fdisk -l"?  And what do you mean by "sudo fdisk -l"?  Where do I type that?

---

### Post by achase79 on 2008-11-06
> **hfp said:**
> I'm sorry.  I haven't used Ubuntu much lately.  How do I post the output of "sudo fdisk -l"?  And what do you mean by "sudo fdisk -l"?  Where do I type that?

You type it into the terminal

---

### Post by bodhi.zazen on 2008-11-06
> **ad_267 said:**
> Can you post the output of "sudo fdisk -l" or a screenshot from gparted so we can see what your partitions are like. It should let you expand the vista partition.

You typically need to do this in two steps. Shrink or delete a partition -> apply changes

Then expand Vista -> apply changes.

If that is not working either post a screen shot from gparted or the output of 

```
sudo fdisk -l
```

---

### Post by hfp on 2008-11-06
> **achase79 said:**
> You type it into the terminal

When I type that in the terminal it asks for my password and then will not accept my password.

---

### Post by bodhi.zazen on 2008-11-06
You need to resize your partitions from a live CD.

On the Ubuntu live CD you will not be asked for a password when you use sudo.

---

### Post by hfp on 2008-11-06
But why won't it accept my password?

---

### Post by JohnFH on 2008-11-06
> **hfp said:**
> It seems like I am going to have to learn to partition my hard drives if I want to solve this problem.  The thing is, when I try to extend the space available for vista, it won't let me, even if I shrink the size of vista's hard drive.  Why is this?  What should I do?  I really appreciate your help.

What program are you using?  Did you unmount the Windows partition first?  Do you know how to post a screenshot?

---

### Post by bodhi.zazen on 2008-11-06
> **hfp said:**
> But why won't it accept my password?

When you enter your password, nothing appears on the screen. Just type it in and hit enter.

If it is not accepting your PW the 2 most common issues are caps lock is on and you are typing the wrong password.

Beyond that there was another similar thread but I do not recall any answer to the other thread.

---

### Post by hfp on 2008-11-06
> **JohnFH said:**
> What program are you using?  Did you unmount the Windows partition first?  Do you know how to post a screenshot?

I am using gparted.  I did not unmount the Windows partition first and I do not know how to post a screenshot. Please help. :)

---

### Post by nothingspecial on 2008-11-06
Non windows user alert !
Open a terminal by going in to your menus.

Aplictions > accessories > terminal

Then copy and paste 
```

sudo fdisk -l
```

---

### Post by nothingspecial on 2008-11-06
Then accessories > take screenshot

---

### Post by peakshysteria on 2008-11-06
To remove Ubuntu completely why don't you just put your Vista disc into the drive and choose [**clean install**]("http://support.microsoft.com/kb/918884")?

If you then choose to install Ubuntu afterwords you can better control the size of it :) You just have to clean some room for it in your Vista partition and then afterwards install Ubuntu onto that space.

Good luck

---

### Post by ugm6hr on 2008-11-06
I realise there are plenty of people trying to help here, which can be confusing.

However, I would like to offer the following advice:

Decide whether you want to keep Ubuntu at all, or just wipe it.  

If you want to wipe it completely - look here: [http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm) (look at the EasyBCD option for Step 1)

If you want to shrink Ubuntu:
It appears that you have discovered how to shrink Ubuntu, but can't expand Vista with GParted.  Why not just shrink Ubuntu, reboot into Vista, and then use Vista's own partition manager to enlarge the Vista partition?

Hope that helps.

---

### Post by bobbob1016 on 2008-11-06
> **hfp said:**
> I am using gparted.  I did not unmount the Windows partition first and I do not know how to post a screenshot. Please help. :)

You are getting help.  Please, be patient, they are helping you, and they are patient.  The links they gave you will help.  Go to those sites, and print the page.  Did you shut down windows normally?  It could be that gparted can't touch the Vista partition without it being shut down normally.

An OS is not usually something that can be "uninstalled", Wubi is the exception.  An OS is like the engine in your car, putting it in, or taking it out aren't too easy, and are big jobs.  Installing a program,  or part, is usually easy, as in I just changed my wiper blades, "uninstalling" the old ones and "installing" the new ones was easy.

---

### Post by hfp on 2008-11-06
> **ugm6hr said:**
> 
If you want to shrink Ubuntu:
It appears that you have discovered how to shrink Ubuntu, but can't expand Vista with GParted.  Why not just shrink Ubuntu, reboot into Vista, and then use Vista's own partition manager to enlarge the Vista partition?

Hope that helps.

Because Windows won't let me adjust the amount of space available for Vista.  With gparted I shrunk the hard drive that Ubuntu was using, but I just ended up with a bunch of unallocated space.  That unallocated space cannot be applied to Vista, or at least if it can, I haven't figured out how to do it.

---

### Post by ugm6hr on 2008-11-06
> **hfp said:**
> Because Windows won't let me adjust the amount of space available for Vista.  With gparted I shrunk the hard drive that Ubuntu was using, but I just ended up with a bunch of unallocated space.  That unallocated space cannot be applied to Vista, or at least if it can, I haven't figured out how to do it.

What happens when you use Vista's partition manager?  And make sure you have created the unallocated space with GParted first.

I've only ever used it once (to shrink Vista's partition), and it worked great.

---

### Post by hfp on 2008-11-06
> **ugm6hr said:**
> What happens when you use Vista's partition manager?  And make sure you have created the unallocated space with GParted first.

I've only ever used it once (to shrink Vista's partition), and it worked great.

When I use Vista's partition manager I am only allowed to shrink Vista's space.  I am not able to extend it, even though it even shows that there is free space, which is the free space I created in gparted by shrinking the space available for Ubuntu.

---

### Post by bobbob1016 on 2008-11-06
> **hfp said:**
> When I use Vista's partition manager I am only allowed to shrink Vista's space.  I am not able to extend it, even though it even shows that there is free space, which is the free space I created in gparted by shrinking the space available for Ubuntu.

Shrink (or if you want to, remove) Ubuntu's partition from gparted on the LiveCD.  Then make sure you click Apply.  Then boot into Vista, and you should be able to resize it now.  You can also just go into the Vista partitioner and remove all partitions that ARE NOT your Vista ones.  The Vista ones should say a drive letter on them.  Then you can resize the C: partition to fit the drive.

---

### Post by hfp on 2008-11-06
> **nothingspecial said:**
> Then accessories > take screenshot

Thanks for your help, nothingspecial.  I was able to type in my password, invisibly, and it did work, and I was able to take a screenshot, but how do I place that screenshot in a post?

Thanks for helping, everyone.  I know these are a bunch of newbie questions and I apologize.

---

### Post by bobbob1016 on 2008-11-06
> **hfp said:**
> Thanks for your help, nothingspecial.  I was able to type in my password, invisibly, and it did work, and I was able to take a screenshot, but how do I place that screenshot in a post?

Thanks for helping, everyone.  I know these are a bunch of newbie questions and I apologize.

No problem, so long as they are asked nicely, and patiently.  You could post them as attachments to your posts.  At the bottom of the reply screen, under Additional Options, is Manage Attachments, just post them like that.

---

### Post by bodhi.zazen on 2008-11-06
> **hfp said:**
> I am using gparted.  I did not unmount the Windows partition first and I do not know how to post a screenshot. Please help. :)

Well, you are going about it all wrong and if you persist in doing so you will either not succeed or damage your Ubuntu and/or windows installation.

When you manage a partition it should be unmounted and again is best done from a live CD.

It sounds as if you are trying to manage your partitions while running from your hard drive and, as you can see, this will cause problems. They only get worse from where you are now.

Please start by booting the Ubuntu CD and unmounting all your partitions. Then proceed with gparted.

If you follow directions it is quite easy.

See this link for general information.

[Gparted Documentation](http://gparted.sourceforge.net/documentation.php)

---

### Post by CatKiller on 2008-11-06
> **hfp said:**
> Ok, I used gparted live to try to shrink ubuntu's harddrive space and expand vista's, but I was only able to shrink ubuntu's space.  It would never let me expand vista's space.  In other words, I can't drag the bar to give myself more space for vista.  It's as if the drive for Ubuntu has all the memory and that memory can't be placed anywhere else.  It can only be shrunk, but this doesn't do me any benefit since vista is still unchangeable.

Is there a box around the free space and Ubuntu partitions? This would represent an [Extended Partition]("http://en.wikipedia.org/wiki/Extended_partition") which should be re-sized to the right so that it only encompasses your Ubuntu partitions.

---

### Post by hfp on 2008-11-06
I have booted up the computer using gparted live on a cd and all drives are unmounted, but I can only shrink the Ubuntu partition and then that space is just unallocated.  I can't extend vista.  There is a box around Ubuntu and the unallocated partitions, but Vista just has 24 gigabytes to use.

---

### Post by bodhi.zazen on 2008-11-06
As Catkiller said, you need to shrink the box around the unallocated space. 

The box is an extended partition, probably sda5

---

### Post by Viranh on 2008-11-06
If you're still having trouble extending the Vista drive after you remove the extended partition, I would simply format the unallocated space NTFS but leave it separate from the Vista partition. Vista will be able to use it and you can use the space to install games and programs. I usually recommend a setup like this because if you have problems with your operating system (which are inevitable over time) then program data, and anything else on this separate drive, is saved when the operating system is reinstalled.

---

### Post by hfp on 2008-11-06
> **Viranh said:**
> If you're still having trouble extending the Vista drive after you remove the extended partition, I would simply format the unallocated space NTFS but leave it separate from the Vista partition. Vista will be able to use it and you can use the space to install games and programs. I usually recommend a setup like this because if you have problems with your operating system (which are inevitable over time) then program data, and anything else on this separate drive, is saved when the operating system is reinstalled.

Thanks Viranh, your method worked.  I formatted the unallocated space to NTFS and I was able to access it in Vista.  So that's good, well, very good.  For some reason I still can't change the amount of space available on drive c: , which is the drive I have been talking about in this thread.  I've tried to change it in gparted as you all have said, but to no avail.  It's as if gparted won't let me extend the amount of space available for drive c no matter what I do.

---

### Post by B34ST1Y on 2008-11-06
> **hfp said:**
> Hey, everyone.  I'm about to uninstall ubuntu, if I can figure out how to do it without destroying my computer, because of the following reason.  Maybe one of you can help me with my problem with Ubuntu.  I like Ubuntu but the disk partition is killing me.  I have a 500 gigabyte harddrive and ubuntu is using around 450 gb, leaving windows with around 20gb.  So I have very little space on windows vista, and I like Windows Vista because I can play games on it.  Does anyone know how to change the disk partitions easily or does it almost always require a very risky procedure?  Thanks a lot.

should be pretty straight forward, with respect to a few points. If you're going to run with Vista, you can reclaim the ubuntu partition space, simply by running the windows command "compmgmt.msc" and navigating to the Disk Management tab. You can easily resize your partition via Windows in there.

Another definite thing to give attention to...is once you get rid of ubuntu, that means getting rid of GRUB typically as well. If you dont remake your MBR / boot.ini file, you will NOT be able to boot into windows! The Ultimate Boot CD has some awesome boot managers. Just one of them should do the trick for rebuilding it. :) 


happy trails

---

### Post by kansasnoob on 2008-11-07
> **ugm6hr said:**
> I realise there are plenty of people trying to help here, which can be confusing.

However, I would like to offer the following advice:

Decide whether you want to keep Ubuntu at all, or just wipe it.  

If you want to wipe it completely - look here: [http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm) (look at the EasyBCD option for Step 1)

If you want to shrink Ubuntu:
It appears that you have discovered how to shrink Ubuntu, but can't expand Vista with GParted.  Why not just shrink Ubuntu, reboot into Vista, and then use Vista's own partition manager to enlarge the Vista partition?

Hope that helps.

+1

Best advice I've read!

---

### Post by ugm6hr on 2008-11-07
> **hfp said:**
> Thanks Viranh, your method worked.  I formatted the unallocated space to NTFS and I was able to access it in Vista.  So that's good, well, very good.  For some reason I still can't change the amount of space available on drive c: , which is the drive I have been talking about in this thread.  I've tried to change it in gparted as you all have said, but to no avail.  It's as if gparted won't let me extend the amount of space available for drive c no matter what I do.

I think you need to read more about partitions (specifically extended partitions) in order to extend Vista.  It is clear that the problem is that your previously unallocated space remains within "sda5" which is an extended partition (depsite being unallocated).  The "C" drive cannot be extended over the top of sda5, until sda5 has been shrunk to the same size as the Ubuntu+swap partitions.

Unfortunately, partitioning can be a confusing topic, and is probably not something those unfamiliar with installing an OS should be recommended to do.

---

### Post by chrisod on 2008-11-07
Now that the unallocated space is available - simply use the Vista disk tools to assign a new drive letter to the free space. Whether you have 50 GB on drive C or 24 on drive C and 26 on Drive Z doesn't really matter. As mentioned earlier, there are a lot of advantages to storing your data on a seperate logical drive from the OS. If you need to reinstall the OS in the future, you don't lose your pictures. music, etc in the process.

---

### Post by schmickey on 2008-11-07
I've uninstalled Ubuntu many times.  It's easy: boot into Vista and download EasyBCD (Google is your friend) which is a free program.  EasyBCD allows you to rewrite the MBR to restore boot control to Vista. After doing that, just start > run > diskmgmt.msc and you can delete the Ubuntu partitions and expand the windows partition to fill the disk if you want.

Instead of EasyBCD, you can use mbrfix.exe (another freebie). To use it, go to a command prompt and type:
"mbrfix /drive 0 fixmbr /vista /y"
This also will restore boot control to Vista's bootloader and pre-empt GRUB.  Only after restoring boot control to Vista should you delete the Ubuntu partitions.

---

