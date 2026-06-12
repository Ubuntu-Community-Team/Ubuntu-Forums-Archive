---
title: "Help to remove Ubuntu 11.10,install Windows &amp; then install Ubuntu 13.04 in dual mode"
date: 2013-04-25
forum: New to Ubuntu
---

### Post by ask_ on 2013-04-25
Hello ,

I have only Lubuntu 11.10 running as of now on my Desktop PC. I have realised I may need Windows for some applications in the future. So I aim to install Lubuntu and Windows in a dual mode.

Now I have nothing important saved in Lubuntu 11.10  , everything is backed up , and I wish to completely remove it. Following which I will be installing Windows XP and after that I wish to install the latest version of Lubuntu - 13.04. 

I am confused over how to remove Lubuntu 11.10. Had it been a dual mode , I would have simply formatted the Ubuntu drive from my Windows XP . But as of now there is only Lubuntu 11.10 on my PC. I do not know how to format in such a case.

Should I simply just insert Windows XP installation CD and proceed with installation ,will it simply replace the Lubuntu OS ?

After that I will do the dual mode installation with which I am familiar. But I need help with previous step.


Thanks.
:)

P.S :- Ubuntu 13.04 seems to be released , is Lubuntu 13.04 released too ? The website says Beta 2 version is available. When will final be available ?

---

### Post by Mark Phelps on 2013-04-25
Since XP is so old, it's likely the XP installer will be confused by the Linux partitions on the drive.

What you need to do is to  boot from an Ubuntu LiveCD, select Try Ubuntu, and then select GParted using the Dash.  That is the Gnome Partition Editor.  When that opens, you can use it to remove the partitions.

You can also use it to create an NTFS partition for installing XP -- that way, it won't take up your entire drive.

Then, when you boot from the XP CD, you should have no trouble installing.

---

### Post by ask_ on 2013-04-25
Can't I create a NTFS partition from my current version of Lubuntu ?

---

### Post by pfeiffep on 2013-04-25
You certainly can, however you won't be able to achieve the other part of your goal to remove 11.10. You're going to need an install media for Lubuntu anyway, just download it and use the live dvd as Mark suggested!

---

### Post by ask_ on 2013-04-25
Hi. Thanks for the replies.

I definitely want to upgrade to 13.04 so am downloading the installation.

Let me chalk out the steps , as a confirmation that I have understood the process  ,and also point out queries I have in those steps.

1) Insert Live CD of Lubuntu 13.04. (does Lubuntu have Gparted in it ? )

2) Remove Older partitions of Lubuntu while using Lubuntu 13.04 from Live CD in 'Try' mode.

3) Create an NTFS partition.

4) Insert Windows XP cd and install it in NTFS drive , which it will hopefully detect.

5) proceed with dual boot install of 13.04 using Live CD.

Another query is  :- after removal of the partitions of Older Lubuntu from Live CD of 13.04 , the drive will be clean ? 
And if so , once I create an NTFS partition what should I do with other free space should I leave it as RAW?


Alternately , since I am unsure if gparted is there in Live CD of Lubuntu , I could partition the drive by installing gparted in Lubuntu 11.10. Create NTFS. Install Windows XP , format the Lubuntu drives from Windows XP computer management, and then use Live CD to install Lubuntu 13.04 in free space of RAW drives. Is there a hitch in this alternate process ?

Thanks again for replying to my beginner questions. 

:)

---

### Post by pfeiffep on 2013-04-25
> [COLOR=#000000]Another query is :- after removal of the partitions of Older Lubuntu from Live CD of 13.04 , the drive will be clean ? [/COLOR]
[COLOR=#000000]And if so , once I create an NTFS partition what should I do with other free space should I leave it as RAW?[/COLOR]

If you know the partitioning scheme that you wish to use you CAN create it during Live, other wise you can let it remain unallocated.

> [COLOR=#000000]Alternately , since I am unsure if gparted is there in Live CD of Lubuntu , I could partition the drive by installing gparted in Lubuntu 11.10. Create NTFS. Install Windows XP , format the Lubuntu drives from Windows XP computer management, and then use Live CD to install Lubuntu 13.04 in free space of RAW drives. Is there a hitch in this alternate process ?[/COLOR]

Even if gparted is not part of Lubuntu live you can install it once you've fully booted the live session and choosen "TRY" and not install. 

Installing gparted in Lubuntu 11.1 will not enable you to manipulate the Lubuntu 11.10 partitions! Formatting the 'lubuntu drives' from within Win is a waste of time - Linux needs to be installed on ext partitions and I'm pretty certain Win doesn't partition or format ext.

I suggest installing Win after partitoning using live installation, and then installing Lubuntu 13.04. In this manner grub2 will be installed on the windows partition and you will be able to choose which OS to boot. If you install Lubuntu 13.04 first than Win - the grub2 install will be overwritten by Win boot loader (requiring you to manually fix the grub2 install)

---

### Post by ask_ on 2013-04-27
Thanks for all the help provided. Issue resolved.

:)

---

