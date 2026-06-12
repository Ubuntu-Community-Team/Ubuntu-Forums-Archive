---
title: "(Install) Re-assure me please..."
date: 2008-08-02
forum: New to Ubuntu
---

### Post by doublewitt on 2008-08-02
OK, this is my first go at Linux (Ubuntu) - looks good and simple but I still need some re-assurance on the "how to install". My computer has 2 drives C: and D: and ofcourse, Windows is on the C: drive. I want to install Ubuntu on the D: drive and so I read that all information will be wiped out during installation. I figure that means the D: drive and not the C: drive - correct? Nothing will happen to the C: drive I presume. Is there something I misunderstand? Is there something else I should know before making the step? I have the installation CD and want to install now. Is this process smooth and worry free?! Technically, installing to the D: drive shouldn't affect the C: drive in any way - I guess. Any commentaries before I hit the "GO" button?!

---

### Post by Diabolis on 2008-08-02
Yeah hit it!

Don't worry, nothing will happen to C. It will only wipe the disks marked with the label "reformat"(or somethign like that).

---

### Post by ScaredNoob on 2008-08-02
you might want to use windows to tell you and take note of the exact capacity of each drive because the Ubuntu installer will have a different label for them than c: and d: that could possibly confuse you.

---

### Post by GreenN00b on 2008-08-02
If D: is a partition:
You will have to delete the D: partition from windows or the installer, ubuntu creates it's own partitions and will not touch existing one if not instructed to do so during the install process ...
Safest way here is to delete the D: partition from windows before staring the installer ...

---

### Post by northern lights on 2008-08-02
If it's indeed two drives (are you sure it's not just partitioned?), then nothing will happen to your Windows install. Choose the correct drive, of course.

You might want to check [http://www.psychocats.net/ubuntu/installing]("http://www.psychocats.net/ubuntu/installing")

As an aside: Linux does not employ the concept of drive letters.

---

### Post by freebeer on 2008-08-02
You might want to have a look at this: [http://www.psychocats.net/ubuntu/installing]("http://www.psychocats.net/ubuntu/installing")

---

### Post by alzie on 2008-08-02
You really should back up anything of importance on your Windows drive.  Its not likely that you will have an issue but sometimes you click the wrong thing (I do anyway).

Besides,  Its good practice to make backup on a regular basis right?

Welcome to Ubuntu!

---

### Post by doublewitt on 2008-08-02
Thanks for the tips! I'll check out those recommended sites and figure (confirm) whether I'm dealing with partitions or drives...

---

### Post by GreenN00b on 2008-08-02
You can see if you have partition or drives from Computer Manager in windows ... at Storage\Disk management. You can delete the D: partition from there if this is the case ...

---

### Post by doublewitt on 2008-08-02
OK, it's 2 partitions...

---

### Post by jeremy1138 on 2008-08-02
Go for it.  No worries...  Even I managed to get it right.  Ubuntu is great!

---

### Post by northern lights on 2008-08-02
> **doublewitt said:**
> OK, it's 2 separate drives... in that case, then, after reading the suggested page above, the installation won't ask me to partition if there is nothing on the D: drive - correct?Not quite. First off, the filesystem can't be ntfs as it most likely is now. So you want to format data partitions as 'ext3'.

Further, do you know what the pagefile is in Windows? Virtual memory in Linux is in a separate partition called the swap
space. Make /swap around a gig. Unless you want to let the comp hibernate, then you might need a bit more.

It's optional to partition further. I like the idea of a separate /home since it saves you from backing up in fear of a shot OS. If you don't trust your hardware of course, backups are still necessary.

---

### Post by doublewitt on 2008-08-02
My previous post was wrong! I'm sorry... I replied too quickly. I realize that I'm dealing with partitions and not separate drives.

---

### Post by doublewitt on 2008-08-02
OK, will do a quick backup of my necessary files and hit the GO button!

---

### Post by northern lights on 2008-08-02
> **doublewitt said:**
> My previous post was wrong! I'm sorry... I replied too quickly. I realize that I'm dealing with partitions and not separate drives.

Doesn't change much.

Delete the non-Windows one. Since you're dealing with partitions though, you have the option of resizing the Windows one also. A word of caution: The process will take significantly longer and, even though still unlikely, increases the chances of Windows getting screwed also.

After deletion (and possibly resizing) create two (or three if you want a separate /home - that's where the user's (your) files will be stored) new partitions in the unallocated space - a one gig swap and the rest as ext3.

---

### Post by doublewitt on 2008-08-02
> **northern lights said:**
> Doesn't change much.

Delete the non-Windows one. Since you're dealing with partitions though, you have the option of resizing the Windows one also. A word of caution: The process will take significantly longer and, even though still unlikely, increases the chances of Windows getting screwed also.

After deletion (and possibly resizing) create two (or three if you want a separate /home - that's where the user's (your) files will be stored) new partitions in the unallocated space - a one gig swap and the rest as ext3.
OK, that sounds good... thanks.

---

### Post by Macintosh Sauce on 2008-08-02
> **alzie said:**
> You really should back up anything of importance on your Windows drive.  Its not likely that you will have an issue but sometimes you click the wrong thing (I do anyway).

Besides,  Its good practice to make backup on a regular basis right?

Welcome to Ubuntu!

I definitely agree with that. Back up any crucial data first then go crazy. :)

---

### Post by doublewitt on 2008-08-02
One more question before installing...

I noticed the option to "Install Inside Windows" and also the option to perform the full installation from within the demo. What's the most recommended approach?

---

### Post by Boelcke on 2008-08-02
Ah, couldn't say.  I've never done that, "install from within Windows" thing.

I will say this, and maybe I'm getting too far ahead of myself.  You've got Windows installed in the partition you're calling C:.  There's also something in the very front of your harddrive space, not a partition, called an MBR.  Master Boot Record.  Or something like that.  It's the little boot loader that tells the thing to boot Windows.

When you install Ubuntu onto the other partition(s), you'll also be asked about loading GRUB, a different bootloader than what you have now.  When you're done, it'll give you the choice of which thing to boot into, Windows or Ubuntu.  I've never had a problem with it.

There's also some odd way to still use the Windows booter, but I've never done it.  Never had a problem with GRUB.

---

### Post by Koselara on 2008-08-03
I installed from DVD with a similar configuration just a few weeks ago for the first time, and I was anxious as all get-out too.  :)  It went pretty smoothly, though...even let me conserve part of drive D in NTFS format where my old My Documents folder has always been. 

One tip I do have from my experience: if anything weird happens, just search the forum since someone else probably already went through & fixed it. I panicked because a vaguely-worded error made me think my drive was dying, only to find on the forums that I merely needed to defrag it... :rolleyes:

Good luck!

---

### Post by Jason80513 on 2008-08-03
Instead of committing your whole D: drive, consider installing using WUBI.

[http://wubi-installer.org/]("http://wubi-installer.org/")

I am running in WUBI-installed Ubuntu right now.  It's my first go at it, and WUBI is an incredible starter drug for Ubuntu, since it requires no commitment and can be removed from the machine by uninstalling from Windows.  It's a much better option than trying in VMWare, because you don't have to use hardware emulation (so my 3-D card works the way it should).

Basically, WUBI is a dual boot option that runs Ubuntu in a virtual disk stored on one of your hard drives as a file.  But it isn't virtualized any other way, so you get pretty much all the benefits and drawbacks of a full Ubuntu install, but with an option to uninstall the whole thing and start over.

On the other hand, I have been using Ubuntu for two days and have moved my entire family off of Vista Home and onto Ubuntu accounts. If everything works well for the next month or so, Vista may be coming off my machine entirely.  :-)

---

### Post by doublewitt on 2008-08-03
I made the full install...!! Wow! - this is nice! Everything went fine. The installation process worked smoothly without any problems... I'm really starting to enjoy this. This operating system looks very impressive...***Thanks for Ubuntu!*** If all continues to go well, Windows will go bye-bye relatively soon...

---

### Post by ScaredNoob on 2008-08-03
glad you're satisfied.  If you are like me, you probably wil want to begin fine-tuning everything to the way you want.  A biggie for me is the grub bootloader.  I use a program installable through Synaptic Package Manager called startupmanager.  (After you install it it ends up right next to where you found Synaptic).  This let me set the screen that first comes up with all those options.  My grub boot screen now only has two choices (Ubuntu or Windows), I took out the memory test and recovery mode choices, and I set the default timeout to 2 seconds (instead of 10), with ubuntu being the default.  
      Also, if you want to set Ubuntu to autologin to your desktop/wireless, the answers are out there, but can be a little tricky/guilttrip laden to find them on these forums.  If you are interested, I would be willing to walk you through later this day.  Keep on keeping on.

---

