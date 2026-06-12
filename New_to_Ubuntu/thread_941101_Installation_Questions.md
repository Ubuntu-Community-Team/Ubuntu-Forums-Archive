---
title: "Installation Questions"
date: 2008-10-07
forum: New to Ubuntu
---

### Post by BitCrusher on 2008-10-07
Hello:

This is my first post in a new thread. Thank you to Ubuntu for providing this fantastic software. Of course, my current problem is in overcoming problems getting it installed, but I am so impressed with it's look and feel, and common sense approach.

Here is my situation. I use a Core Duo (E6850) 3 Ghz processor, Windows Vista Home Premium,4 GByte Memory, 32 Bit setup and would like to install Ubuntu on my External Hard Drive as a 64 Bit setup. Sounds simple enough, but obviously not so simple for me.

During my installation attempts, When I get to Partition, Ubuntu provides a default option of hd0, but I was concerned that this would mess up my Windows MBR and chose to have Ubuntu set up on /dev/sdc which is my External Drive. However, Ubuntu won't allow me to set it up this way so I doing something wrong. This is the first question in a long line of them them.

My second question is how to get the Internet Network set up. I know my:

IP address and subnet mask,
DNS Server and physical address,
SSID,
iPV4 DNS Server,

but don't know what the following are or how to find out what they are: 

Gateway IP Address,
DHCP server,
VPI/VCI,
MTU
Encapsulation Type
DHCP Setting
POP server
Connection Type

Maybe there is a simple way to set up a network conncetion, and if so, I need help with a tutorial on what to do.

Thanks,

BitCrusher

---

### Post by JoshuaRL on 2008-10-07
First off, welcome to Ubuntu!

Next, get used to ripping up the Windows MBR.  That takes the whole master boot record and is really greedy.  The bootloader that Ubuntu uses is called GRUB.  That stands for GRand Unified Bootloader.  It should detect and load almost all operating systems.  So really, it's better than the Windows MBR.  If you have it install somewhere else, you wont be able to boot into Windows without that external drive attached.  So somewhat problematic.  Windows is still there, don't worry.  But you can't get to it because GRUB is pointing weird.

Now for networking.  For wired ethernet networking, you shouldn't need that stuff.  It should automatically detect and work.  Are you trying to use wireless or are you having problems connecting?

---

### Post by BitCrusher on 2008-10-07
Hi Joshua. I am using wireless. I use a Trendnet wireless PCI adapter (108 mBPS 802.11 G) My desktop is in my basement and my Linksys router is upstairs. I cannot use an Ethernet cable.

Just to clarify. In your opinion, If I leave the default installation from the LIVECD install in hd0, it will install GRUB there, but Ubuntu will still be installed on my External Drive.

Thanks for taking the time to help.

BitCrusher

---

### Post by JoshuaRL on 2008-10-07
Not a problem man.  No, if you install to your first harddrive, it will install the whole thing there.  But if you install GRUB to the MBR, it should still be able to boot into Windows without the external plugged in.  

What I think would be the best and easiest idea for you is to put a 10-20GB partition on your main harddrive for the / (root) partition.  That will hold all the system data, and should be enough for you.  Then set up your /home partition on your external harddrive.  That way you have plenty of space for that, where most of your media and other personal files will live.

Another option is available if you have a motherboard that can boot off of that USB harddrive.  If so, you can install the complete OS to that drive.  Then just choose which you boot to at startup.  And when you install you can mount the Windows harddrive in your Ubuntu system.  (Something like /media/WindowsHD would be fine.  Follow your own naming conventions of course.)  Then you would have access to all your files, plus read/write ability too.  But that all depends on whether your motherboard supports that.

---

### Post by BitCrusher on 2008-10-09
Hi Joshua:

Need your help again. I freed up about 130G on one of my hard drives and loaded Ubuntu there. So far so good. After loading, Ubuntu asks you to restart the computer which I did..The problem is I get Error 17 when the computer tries to restatrt and I cannot use the computer at all...to either run Windows or Ubuntu. Can you provide me with advice on how to fix this. According to the LIVECD, Ubuntu as to provide me with a screen that alloed me to select either OS. I think my MBR is totally screwed up.

Thanks,

Joe

---

### Post by oldos2er on 2008-10-09
[http://users.bigpond.net.au/hermanzone/p15.htm#17](http://users.bigpond.net.au/hermanzone/p15.htm#17)

---

### Post by hyper_ch on 2008-10-09
It is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;) 

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

---

### Post by JoshuaRL on 2008-10-09
> **BitCrusher said:**
> Hi Joshua:

Need your help again. I freed up about 130G on one of my hard drives and loaded Ubuntu there. So far so good. After loading, Ubuntu asks you to restart the computer which I did..The problem is I get Error 17 when the computer tries to restatrt and I cannot use the computer at all...to either run Windows or Ubuntu. Can you provide me with advice on how to fix this. According to the LIVECD, Ubuntu as to provide me with a screen that alloed me to select either OS. I think my MBR is totally screwed up.

Thanks,

Joe

No problem man.  I have a feeling that everything is there, just GRUB isn't pointing to the OSs right.  In the LIVECD, could you go to the terminal (Applications->Accessories->Terminal) and put this command in?  Please post it back here.
```

sudo fdisk -l

```
and that arguement is a lowercase L, not a 1.

When you post back here, put the output in code tags.  Like this:

[noparse]```
stuff from output of command
```[/noparse]

---

### Post by drowner on 2008-10-09
> **BitCrusher said:**
> Hi Joshua:

Need your help again. I freed up about 130G on one of my hard drives and loaded Ubuntu there. So far so good. After loading, Ubuntu asks you to restart the computer which I did..The problem is I get Error 17 when the computer tries to restatrt and I cannot use the computer at all...to either run Windows or Ubuntu. Can you provide me with advice on how to fix this. According to the LIVECD, Ubuntu as to provide me with a screen that alloed me to select either OS. I think my MBR is totally screwed up.

Thanks,

Joe


Did you end up installing it on an internal or external hard drive? How many hard drives do you have?

---

### Post by BitCrusher on 2008-10-09
I have placed Ubuntu on an internal hard disk. I haven't used the external HD.

I will try what Joshua advised and get back to you. Thanks.

---

### Post by BitCrusher on 2008-10-09
Almost forgot...Thank You Ann for the webpage on Error 17 and GRUB. I'm working my way thru it slowly.

Joe

---

### Post by BitCrusher on 2008-10-09
Jason: Here's what the computer came back with. Thanks for letting me know what to do next.

Joe
-------------------------------------------------------------
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9ea8ebd6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       27489   220798964    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a19ac

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       18662   149902483+  83  Linux
/dev/sdb2           18663       19457     6385837+   5  Extended
/dev/sdb5           18663       19457     6385806   82  Linux swap / Solaris

Disk /dev/sdc: 41.1 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf6eb810a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        4795    38515806   83  Linux
/dev/sdc2            4796        5005     1686825    5  Extended
/dev/sdc5            4796        5005     1686793+  82  Linux swap / Solaris

Disk /dev/sdd: 4102 MB, 4102887936 bytes
255 heads, 63 sectors/track, 498 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1         497     3992135+   7  HPFS/NTFS

Disk /dev/sde: 1043 MB, 1043333120 bytes
64 heads, 32 sectors/track, 995 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Disk identifier: 0xd33bbeb3

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1         995     1018863+   6  FAT16
Partition 1 has different physical/logical endings:
     phys=(993, 63, 32) logical=(994, 63, 31)
ubuntu@ubuntu:~$

---

### Post by BitCrusher on 2008-10-09
Jason: I'm resending this. I couldn't find my earlier post of this information. Thanks for your help.

Joe

-------------------------------------------------------------

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9ea8ebd6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       27489   220798964    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a19ac

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       18662   149902483+  83  Linux
/dev/sdb2           18663       19457     6385837+   5  Extended
/dev/sdb5           18663       19457     6385806   82  Linux swap / Solaris

Disk /dev/sdc: 41.1 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf6eb810a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        4795    38515806   83  Linux
/dev/sdc2            4796        5005     1686825    5  Extended
/dev/sdc5            4796        5005     1686793+  82  Linux swap / Solaris

Disk /dev/sdd: 4102 MB, 4102887936 bytes
255 heads, 63 sectors/track, 498 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1         497     3992135+   7  HPFS/NTFS

Disk /dev/sde: 1043 MB, 1043333120 bytes
64 heads, 32 sectors/track, 995 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Disk identifier: 0xd33bbeb3

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1         995     1018863+   6  FAT16
Partition 1 has different physical/logical endings:
     phys=(993, 63, 32) logical=(994, 63, 31)
ubuntu@ubuntu:~$

---

### Post by JoshuaRL on 2008-10-09
Man, how many hard drives do you have?  I count three, a memory stick, and something else with 4GB on it.  Is that right?

---

### Post by BitCrusher on 2008-10-09
I have 2 hard drives, 1 external hard drive, and one USB 4MB stick which I used as backup RAM when Windows needed to swap memory.

Hope that helps..

Thanks,

Joe

---

### Post by JoshuaRL on 2008-10-10
First of all, does your motherboard and BIOS allow you to boot from either the Windows or Linux harddrive?

If so, did you try to boot from the Linux harddrive?  If so, that may be because GRUB is on the Windows harddrive.  Or vice versa.  If you can boot from either, the best idea would be to set up GRUB on the Linux harddrive and repair the Windows MBR.

If not, we just need to reinstall GRUB so it reads your system right.  So let me know which it is and I'll walk you through how to do it from the Live CD.

---

### Post by BitCrusher on 2008-10-10
I can only boot from my CD Drive. When I restatrt my system, the system begins to boot, then it says something like Stage 1.5, then Error 17.

---

### Post by BitCrusher on 2008-10-10
just a follow up to my post #15. My cmputer has 2 hard drives. Windows is on Drive 0, Ubuntu is on Drive 1. I have one external drive (not used for anything but storage), one stick drive (4GB). The other 4GB must be my computer RAM. That's the only thing I am aware of. Thanks again for your help.

---

### Post by JoshuaRL on 2008-10-10
> **BitCrusher said:**
> I can only boot from my CD Drive. When I restatrt my system, the system begins to boot, then it says something like Stage 1.5, then Error 17.

Okay.  Sorry, I meant the ability to boot, not a successful boot up.  When you go into BIOS, does it let you boot from the two internal harddrives?  What options does it give you for booting?

---

### Post by lisati on 2008-10-10
> **BitCrusher said:**
> Jason: I'm resending this. I couldn't find my earlier post of this information. Thanks for your help.

Joe


Sometimes posts don't always show up right away for the person who sent them.... be patient. You can always click on "Search"->"Find all your posts" (see picture).

---

### Post by BitCrusher on 2008-10-11
Hi, while the Bios (Details) shows 2 internal hard drives, the Bios shows then as one huge hard drive. There is no option to pick which hard drive to boot up seperately. I think this is because of the way the RAID was set up or the way Windows configured them. I don't know which. So while the Bios shows me two hard drives in the Details section of my Bios, the BIOS shows them as one huge internal hard drive. The BIOS gives me an option to Delete the huge partition (I guess that's what it is), but I'm not going there without some guidance. Thanks for for your continuing efforts.

Joe

---

### Post by BitCrusher on 2008-10-11
Almost forgot. It could be that Ubuntu set up GRUB on hd0, since BIOS shows the 2 hard drives as one huge drive? However, during installation it somehow has corrupted the Windows MBR. Windows is stored on \dev\sda which should be hd0, while Ubuntu is stored on \dev\sdb which I beleive is hd1. So I think we need to figure out how to gt GRUB installed to the first partition in hd1, and the Windows MBR reinstalled to hd0. At least that my current theory on what needs to happen. Thanks again.

Joe

---

### Post by ugm6hr on 2008-10-11
> **BitCrusher said:**
> I freed up about 130G on one of my hard drives and loaded Ubuntu there. So far so good. After loading, Ubuntu asks you to restart the computer which I did..The problem is I get Error 17 when the computer tries to restatrt and I cannot use the computer at all...to either run Windows or Ubuntu.

Do you get an option to choose which OS to boot - i.e. a text list of options, or perhaps a press Escape within 3 secs to access boot list?

If yes - the problem is with your menu.lst file.

Confirm that this is the issue - and I'll advise from there (you can use the "e" key to edit from this menu).

---

### Post by BitCrusher on 2008-10-11
Unfortunately the Error 17 showed before I was given the option to choose. Error 17 shows up right after the a restart. The computer says something with Stage 1.5, then Error 17. Thanks.

Joe

---

### Post by BitCrusher on 2008-10-11
I reread your post and I'm not certain I am answering your question. After Ubuntu was loaded, it advised me to restart the computer (probably so the OS could set itself up on the hard drive). I wasn't aware of other options at that point. Let me know if you think I need to reload everything, what issues I should be aware, or anything you think might be helpful. Regards.

Joe

---

### Post by JoshuaRL on 2008-10-12
Alright, it seems like GRUB isn't set up quite right.  And yes, since you have those two drive set up in a RAID array, it will and should read as a single drive.  After all, that's the idea of RAID:  Redundant Arrays of Independant Disks.  So let's try reinstalling GRUB from the Live CD and see if that fixes the issue.

First, boot into the Live CD.  Then open the terminal.  (Applications->Accessories->Terminal)  Then let's do a little work from the GRUB command line.  To open that within the Terminal, put in this command:
```

sudo grub

```
Then we will be at the GRUB prompt.  It should look like this:
```

grub>

```
Next we want to locate the GRUB install in your system.  Do this to find that:
```

find /boot/grub/stage1

```
and that is this time a number 1, not a lowercase L.  This finds the GRUB files.  Only a small part of GRUB sits in the MBR, and the rest is on the Linux partition.  So this finds where the rest is.  You'll want to use the location you find from the output of that command in the next two.  What we're doing on the next step is focusing GRUB here for installation, telling it where those files are:
```

root (hdx.y)

```
Now, x and y refer to the harddrive and partition that it should point to.  Again, you'll get that from the command above the last one.  Next, installation:
```

setup (hdx,y)

```
Now, we have hopefully installed GRUB correctly, and you'll want to quit the GRUB command line.
```

quit

```

Now try to reboot and see if that helps.  If not, we'll talk more about your RAID array and how it was set up.

---

### Post by hyper_ch on 2008-10-12
It is advised to use a descriptive topic title; that means use a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;) 

Just imagine what these forums would look like if everybody would just post "Help" or "Noob here". What do you think how many people will still look at such threads?

Furthermore, for unrelated questions it's also adviced to open a seperate thread for each one, so that each problem can be addressed (and eventually marked as solved) individually.

---

### Post by jonandrews on 2008-10-12
I have put a step-by-step guide to networking between Ubuntu & Windows on a website:

[http://www.europe.eclipse.co.uk/Ubuntu](http://www.europe.eclipse.co.uk/Ubuntu)

That should help you with that part of your project

---

### Post by JoshuaRL on 2008-10-12
> **hyper_ch said:**
> It is advised to use a descriptive topic title; that means use a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;) 

Just imagine what these forums would look like if everybody would just post "Help" or "Noob here". What do you think how many people will still look at such threads?

Furthermore, for unrelated questions it's also adviced to open a seperate thread for each one, so that each problem can be addressed (and eventually marked as solved) individually.

Man, I first of all want to say that I respect you and the help you provide here on the forums.  Seriously, much love.

But you already said this to the OP.  Post #7 on the first page.  And as far as I'm concerned, this is all the same issue:  Dual booting Ubuntu and Windows.  I and others are trying to determine the underlying issue and help him with what he really needs.

And while I agree that a descriptive title is very important, I both think that we need to have some understanding that not everyone knows exactly what the problem really is, and that the OP really did point out the issue he was having.

But that's just my opinion.

---

### Post by collinp on 2008-10-12
Just dropping in for a few seconds:
hyper_ch: I really believe that the repost of what you already stated on the first page is unnecessary, and i believe the OP has received the point of your first post on here.
JoshuaRL: I believe that he has just installed GRUB onto the wrong partition or something of that sorts, it happened to me once.

---

### Post by BitCrusher on 2008-10-12
Hello:

First, my continued thanks to all of you for your help. I have now changed the title of this post. I hope this is closer to what is expected. 

Now, for our continuing saga. 

I went to Live CD, loaded ubuntu, went to Terminal. Once there I entered:

sudo grub... and was taken to grub>, so far so good...

then I typed in find/boot/grub/stage1...

and received Error 27 unrecognized command..

So, it's time to check back in for some additional help..

Thanks,

Joe

---

### Post by BitCrusher on 2008-10-12
John:

Thank you for your post and helpful notes. Once I get past the problems of getting my pc back to where it will boot again, I plan to use your guide to establish internet connectivity. Again..thanks to all.

Joe

---

### Post by JoshuaRL on 2008-10-13
Alright.  So could you elaborate some on the RAID array you have set up?  Is it via a RAID card, or did you set it up with Windows?

---

### Post by BitCrusher on 2008-10-13
Joshua: I have decided to start from scratch. I reinstalled my Windows MBR and backed up my entire Windows setup last night (6 DVD's). The RAID setup is controlled by the BIOS. I am now considering the following activities:

1. Eliminate the RAID setup in BIOS.
2. Reset up Windows on Partition 0.
3. Set up Ubuntu on Partition 1.

My question is this: Will Ubuntu set itself on Partition 1 in a way that doesn't corrupt the Windows MBR? Is it possible to set up my system so that both systems are operable, and I get to choose which OS to boot? 

Thanks,

Joe

---

### Post by Keen101 on 2008-10-14
> ust a follow up to my post #15. My cmputer has 2 hard drives. Windows is on Drive 0, Ubuntu is on Drive 1. I have one external drive (not used for anything but storage), one stick drive (4GB). The other 4GB must be my computer RAM. That's the only thing I am aware of. Thanks again for your help.

Okay, I think i know what happened. Ubuntu is on hard drive two, but overwrote the MBR on hard drive 1. But, you have fixed the MBR for windows.

Ok, here is the easiest way to set up your system:

1. switch the dard drive pins (and maybe cables), so that the ubuntu hard drive is the PRIMARY one. Set it up so that the windows drive is the SLAVE.

2.restore grub with the SUPER GRUB DISK (live-CD)..... or just reinstall ubuntu. (restoring grub is easier, but whatever floats your boat)

3. Now the bootloaders should be fine, and you should be able to boot both operating systems, unless GRUB thinks Windows is on the wrong drive, in which case other people on these forums know how to fix that.

---

### Post by BitCrusher on 2008-10-14
Hi, I can still use some clarification...My situation is now a bit different from what Keen addressed..Here is where I am..

I have reformatted both hard disks and they are currently free and clear of everything. I have gone into BIOS and eliminated the RAID setup.

So..Now I am at a new beginning. So, what is the procedure to establish a dual boot setup. I do not care whether Ubuntu is on Partition 0 or 1, just as long as I can also load Windows Vista and use it on the other hard drive. Your thoughts are appreciated. I definitely need GRUB to be set up in a way that allows both OS's be to operational. Thanks.

Joe

---

### Post by Keen101 on 2008-10-14
Well, i still recommend basically the same thing.

Install windows first onto whichever hard drive is the SLAVE.

then install ubuntu onto whichever one is free and the PRIMARY drive and use "largest continous free space".

This should in effect install Grub on the ubuntu drive which is the primary one, and detect windows MBR and set a link to it in grub automatically.

since grub is on the PRIMARY hard drive the BIOS will boot grub.

---

### Post by BitCrusher on 2008-10-14
Thanks Keen, and to all who have perserved with me through the process. I am hopeful for success.

Later,

Joe

---

### Post by JoshuaRL on 2008-10-14
> **Keen101 said:**
> Well, i still recommend basically the same thing.

Install windows first onto whichever hard drive is the SLAVE.

then install ubuntu onto whichever one is free and the PRIMARY drive and use "largest continous free space".

This should in effect install Grub on the ubuntu drive which is the primary one, and detect windows MBR and set a link to it in grub automatically.

since grub is on the PRIMARY hard drive the BIOS will boot grub.

Agreed.  If you've formatted both drives and taken off the RAID array, then that should work just fine.  Please post back here if you have any more issues.

---

