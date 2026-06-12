---
title: "How to make sure my pc will detect both Windows and Ubuntu after installing Ubuntu"
date: 2015-10-01
forum: New to Ubuntu
---

### Post by JCAPER on 2015-10-01
Hi guys, sorry if this is in the wrong category.

So, a few months ago, I made 2 partitions while installing Windows 7 after formatting my pc. A few weeks later, I installed Ubuntu 64 bit in the second partition. Everything went well and it installed just fine. But then when I booted my pc, it would go directly to Ubuntu without asking which OS I wanted to use. Since I didn't have internet at the time, I was dumb enough to format Ubuntu's partition, hoping that the pc would then automatically go to the Windows 7. But sadly, it didn't and I was forced to reinstall the Windows.

Now I find myself in the same situation, except now I have Windows 10 instead of 7. I have a second partition ready and I want to install the latest Ubuntu 64 bit version there, but I am afraid that the same thing will happen again.

I talked to a person who told me that I probably didn't have grub. I googled for a while but I found myself more confused than anything else. I understand what grub is, but I am unsure what's the best way to install it. One website said that I could install grub from Ubuntu after installing Ubuntu, but I am afraid that it will not detect the Windows then or that it will not install successfully (maybe I am being paranoid, but I really don't have the luxury to lose everything and reinstall all my programs and games).

So, is there any way to install the grub before installing Ubuntu? Or make sure that I can install grub without problems? Or is there any good tutorial that explains everything I should do from installing grub to installing Ubuntu?

Thanks in advance! Any help would be appreciated.

PS: My pc is an Asus N56V laptop. It has one single 500 HDD and the partition I want to use has around 20 gb.

---

### Post by yancek on 2015-10-01
> Since I didn't have internet at the time, I was dumb enough to format Ubuntu's partition

A standard install of Ubuntu will install part of the Grub code in the master boot record pointing to the other Grub files which are needed to boot and are on the Ubuntu system partition.   You deleted that partition so that's why it didn't boot.  There should have been an entry in the Grub menu when you booted for windows, it almost always detects that and creates an entry.  If it doesn't, the user would boot Ubuntu and run:  sudo update-grub which should then detect and create an entry for windows.

> I talked to a person who told me that I probably didn't have grub.

If you didn't have Grub installed Ubuntu would not boot.

Now that you have windows 10, you have added another complicating factor which is UEFI.  If you install windows 10 using UEFI/GPT, you need to do the same when you install Ubuntu.  If you don't, you will have problems booting one of the systems.  The first link below is a very detailed tutorial on installing Ubuntu although it doesn't have any info on UEFI it does have a lot of useful information at the beginning of the page.  The second link explains UEFI installs with Ubuntu.  Since you haven't posted what you are using, I can only point you to the tutorials.

[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by JCAPER on 2015-10-01
> **yancek said:**
> A standard install of Ubuntu will install part of the Grub code in the master boot record pointing to the other Grub files which are needed to boot and are on the Ubuntu system partition.   You deleted that partition so that's why it didn't boot.  There should have been an entry in the Grub menu when you booted for windows, it almost always detects that and creates an entry.  If it doesn't, the user would boot Ubuntu and run:  sudo update-grub which should then detect and create an entry for windows.



If you didn't have Grub installed Ubuntu would not boot.

Now that you have windows 10, you have added another complicating factor which is UEFI.  If you install windows 10 using UEFI/GPT, you need to do the same when you install Ubuntu.  If you don't, you will have problems booting one of the systems.  The first link below is a very detailed tutorial on installing Ubuntu although it doesn't have any info on UEFI it does have a lot of useful information at the beginning of the page.  The second link explains UEFI installs with Ubuntu.  Since you haven't posted what you are using, I can only point you to the tutorials.

[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Thanks for the reply and for the help.

Happy to report that already installed Ubuntu and grub is working just fine. I can select between Windows 10 and Ubuntu no problems. Thanks again!

---

### Post by mastablasta on 2015-10-02
just a couple of things to mention, since this is not a private thread...

> **JCAPER said:**
>  But sadly, it didn't and I was forced to reinstall the Windows.


you could have solved the issue by restoring windows boot loader (MBR) which si very easy to do following instructions on MS website.

> 
(maybe I am being paranoid, but I really don't have the luxury to lose everything and reinstall all my programs and games).


which is why you should always make backup before doing any major OS changes or partitioning. for example creating an image on external drive (tools: redobackup, clonezilla) would make it very easy and very fast to restore the previous state.

> 
PS: My pc is an Asus N56V laptop. It has one single 500 HDD and the partition I want to use has around 20 gb.
small partition. but anyway if you have the OS just to fiddle around with it it is easier, faster to install it for example in virtualbox: [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)
- no need for reboots to get to the other OS
- you can work with windows at the same time as with Ubuntu
- you can create a system snapshot, mess up the OS, then restore it all within a minute or two
- excellent for testing - various premade virtual images are available online that are ready to be deployed (no install needed) such as TurnKey Linux (debian based) or Bitnami stack (Ubuntu based)

---

### Post by JCAPER on 2015-10-02
Thanks for the reply, but the problem has already been solved. I'm really sorry, I forgot to change the title to [SOLVED].

> **mastablasta said:**
> you could have solved the issue by restoring windows boot loader (MBR) which si very easy to do following instructions on MS website.
Yeah, but at the time I wasn't aware of the boot loaders existence. I thought that the BIOS automatically detected the OS installed in the HDD and asked to which one I wanted to go.


> which is why you should always make backup before doing any major OS changes or partitioning. for example creating an image on external drive (tools: redobackup, clonezilla) would make it very easy and very fast to restore the previous state.
Oh, I did. I didn't lose my things, but I had to reinstall them. At the time it was fine, I was on vacation. But this weekend I am busy so I didn't have time to sit down a whole afternoon to reinstall and copy everything back into the pc again.

> small partition. but anyway if you have the OS just to fiddle around with it it is easier, faster to install it for example in virtualbox: [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)
- no need for reboots to get to the other OS
- you can work with windows at the same time as with Ubuntu
- you can create a system snapshot, mess up the OS, then restore it all within a minute or two
- excellent for testing - various premade virtual images are available online that are ready to be deployed (no install needed) such as TurnKey Linux (debian based) or Bitnami stack (Ubuntu based)
Yeah, I am aware of that software, but thanks for the suggestion anyway. I prefer to have it alongside windows. It will be mostly for work and for college so I don't need much space. (it was 30 gb after all)

---

