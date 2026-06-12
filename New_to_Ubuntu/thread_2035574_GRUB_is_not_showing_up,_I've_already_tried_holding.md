---
title: "GRUB is not showing up, I've already tried holding shift"
date: 2012-07-30
forum: New to Ubuntu
---

### Post by SL61 on 2012-07-30
I installed Ubuntu 12.04 today along with Windows 7. I can no longer boot into Windows 7 because GRUB doesn't show up at startup. I've already tried holding shift and editing the GRUB config files as suggested by someone in an archived post.

---

### Post by levlaz on 2012-07-30
> **SL61 said:**
> I installed Ubuntu 12.04 today along with Windows 7. I can no longer boot into Windows 7 because GRUB doesn't show up at startup. I've already tried holding shift and editing the GRUB config files as suggested by someone in an archived post.

So what happens when you boot the computer does it go straight into Ubuntu?

---

### Post by SL61 on 2012-07-30
It sits at a magenta-ish screen for about 1 second, then it starts Ubuntu.

---

### Post by levlaz on 2012-07-30
Try to [reinstall grub. ]("http://www.av8n.com/computer/htm/grub-reinstall.htm")

Hopefully that will work. Are you sure you installed ubuntu side by side with Windows 7?

typically in my own experience when there are two OS's and no grub nothing happens -- the fact that it boots into ubuntu is troubling.

---

### Post by SL61 on 2012-07-30
I know Windows 7 is still there because I can see the files from Nautilis (that's what it's called, right?) [http://i.imgur.com/2CmoQ.png](http://i.imgur.com/2CmoQ.png)

Now I'm off to reinstall GRUB, I'll post the results when I'm done.

---

### Post by levlaz on 2012-07-30
I am glad to hear that you can see the files and they are still there. :) 

Yes the file manage is Nautilus. 

Hope it works! 

Best, 

Lev

---

### Post by SL61 on 2012-07-30
How do I define $partition and $device?

---

### Post by levlaz on 2012-07-30
I am assuming you are asking about step 4 of the tutorial. 

If you run the commands in a terminal it should tell you which partition has the linux distribution on it. 

I believe "defining" simply means setting something "equal" ... i.e. in the example they gave they defined the parition using variables. 

$parition=/dev/sda6

$parition and $device are nothing more than shell variables that hold information -- the reason why you are defining them is to make it easier in later steps to use the commands to accomplish your goal. 

You just need to ensure that the sda is the correct one. 

Hope that makes sense?

---

### Post by SL61 on 2012-07-30
Somehow GRUB loaded when I restarted to boot to the Live USB, but Windows doesn't show up in the list. It has Ubuntu, Ubuntu recovery mode, memtest, and some other memtest thing.

---

### Post by levlaz on 2012-07-30
Just from googling I found[ this]("http://askubuntu.com/questions/133073/windows-7-entry-missing-from-grub-after-12-04-installation"), it does not match your situation exaclty but perhaps you could try to login to ubuntu and run sudo update-grub.

---

### Post by SL61 on 2012-07-30
That was one of the things I tried before I made this thread.

---

### Post by levlaz on 2012-07-30
> **SL61 said:**
> That was one of the things I tried before I made this thread.

Gotcha. 

When you first installed ubuntu did you make the partition in windows first? Or did you use the tools on the live CD to resize the partition?

---

### Post by SL61 on 2012-07-30
I used an empty partition that I made a long time ago in the Live CD. I didn't create or resize anything today.

There was also about 200MB of free space that I made into a swap partition. I know it's not much, but I figured it couldn't hurt. Was that a mistake?

---

### Post by levlaz on 2012-07-30
> **SL61 said:**
> I used an empty partition that I made a long time ago in the Live CD. I didn't create or resize anything today.

There was also about 200MB of free space that I made into a swap partition. I know it's not much, but I figured it couldn't hurt. Was that a mistake?

The swap space was a good call.. the more the better. I don't think that's the issue. 

Did you have a look at [this guide? ]("https://help.ubuntu.com/community/WindowsDualBoot")

I am no expert, but have had my fair share of grub issues in the past. I think the best thing to do at this point would be to try to re-install Ubuntu all together. We may have done more harm than good by messing with the grub. When you are installing make sure you replace the current version of ubuntu and make sure that the windows is not written over... as in install them "side by side". 

If that does not work -- you may have to [recover the windows partition]("http://www.sevenforums.com/backup-restore/62209-remove-grub-restore-windows-7-a.html") (assuming you have the recovery CD from Microsoft) and then try this again from the top.

---

### Post by SL61 on 2012-07-30
I did a complete system backup in Windows 5 days ago. I think I'll restore that, and try Ubuntu another day.

---

### Post by levlaz on 2012-07-30
> **SL61 said:**
> I did a complete system backup in Windows 5 days ago. I think I'll restore that, and try Ubuntu another day.

Good call on the backup. 

Just make sure when you try this again that grub is installed on the top of all the partitions and not just on the linux/windows partition. 

I think if you follow the guide from my previous post you should have better luck! 

Sorry I couldn't be more help. 

Best, 

Lev

---

### Post by oldfred on 2012-07-30
You can install this gui tool into your Ubuntu install or liveCD/USB. It can repair many issues and those it cannot repair, will let you create a report BootInfo that you can post a link to, for us to suggest other corrections.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.

---

### Post by Bashing-om on 2012-07-30
hey, do not give up on ubuntu. I admit it is a steep learning curve coming from a windows environment; However the effort is well worth it. Great system and even greater (friendlier) support is all I can say. With this operating system the only limitation is your own imagination! 

          kind regards;

---

### Post by techvish81 on 2012-07-30
are you sure the 200 mb partition you used for swap wasn't the boot partition for win7?

windows 7 creates 2 partition while installed, one is 100-200 mb for boot and the other is for the whole OS?

---

