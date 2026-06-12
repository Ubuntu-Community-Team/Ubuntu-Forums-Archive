---
title: "A novice's questions on xbuntu and partitioning harddisk"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by ambercomm on 2008-04-29
Hi All,

I have an old IBM computer with the following specs:

Processor: AMD-K6 3D processor 450 MHz, L2 cache, 512K; RAM Memory: 256 M RAM; Main board: SiS-530; Video Card: SiS-530; Hard Disk: 80G, partitioned into C: and D:
MS Window98 and the associated application programs reside in drive C:. Drive D: was originally intended for data storage, but now empty. 

My questions are:

1) Is such as a system suitable for Xbuntu 8.04? I burned the Xbuntu iso on a CD disk last night and tried it out on this computer without installing. Xbuntu recognized all the hardware flawlessly. However, the start-ups and running speeds of Firefox 3 and Thunderbird 2 were excruciatingly slow. Can I expect more acceptable running speeds once the Xbuntu packages are installed on the hard disk?

2)I briefly looked through the software packages in the the Synaptic Package Manager. I could not find Seamonkey, Opera or Skype. Are these packages stored in a different location in Xbuntu?

3) I tried installing Xbuntu on my D: drive this afternoon. When I reached Step 4 where partitioning of the Hard disk was required, I chose Manual mode, hoping to install Xbuntu in Drive D:. The screen showed 2 choices:
sda1 fat32 33814MB 
sda5 fat32 48529MB

I highlighted sda5 and click "Next". A dialog box popped up to say that: "no drive chosen". I wonder where I went wrong?

4) If I were to install Xbuntu as a dual-boot system on this computer, presumably with a front-end selection for either Window98 or Xbuntu at start up, what do I need to do to restore the computer to its original state, i.e.how do I remove Xbuntu _and_ the front-end selection, if Xbuntu proves to be too slow on this computer?  

5) I understand that there is a WUBI system where I can install Xbuntu under MS-Windows for evaluation before permanent installation. How do I go about that? Would Xubuntu's running speed be closer to that of a dual-boot system? 

Grateful for any help given.

Many thanks!

---

### Post by hyper_ch on 2008-04-29
> **ambercomm said:**
> 1)Xbuntu recognized all the hardware flawlessly. However, the start-ups and running speeds of Firefox 3 and Thunderbird 2 were excruciatingly slow. Can I expect more acceptable running speeds once the Xbuntu packages are installed on the hard disk?
It will be faster, but still FF3 and TB3 are big appz... you have 250mb ram which is good.. it won't be super fast but should be ok.

> **ambercomm said:**
> 2)I briefly looked through the software packages in the the Synaptic Package Manager. I could not find Seamonkey, Opera or Skype. Are these packages stored in a different location in Xbuntu?
Opera and Skype are not included in the default repos. You'll have to add others (medibuntu for skype [and maybe even for opera] or opera has its own... not sure)... no clue about seamonkey...

> **ambercomm said:**
> 3) I tried installing Xbuntu on my D: drive this afternoon. When I reached Step 4 where partitioning of the Hard disk was required, I chose Manual mode, hoping to install Xbuntu in Drive D:. The screen showed 2 choices:
sda1 fat32 33814MB 
sda5 fat32 48529MB
Naming partitions and give them a letter is a windows things... if you want sda5 to be used for Xubuntu, then delete that partition... or from windows just delete the d: partition... when it's unpartitioned you can then just select "use largest continuous empty space"

> **ambercomm said:**
> 
4) If I were to install Xbuntu as a dual-boot system on this computer, presumably with a front-end selection for either Window98 or Xbuntu at start up, what do I need to do to restore the computer to its original state, i.e.how do I remove Xbuntu _and_ the front-end selection, if Xbuntu proves to be too slow on this computer?
you first have to run /fixmbr from the dos command prompt (after booting windows) and then you can formate the partitions used by Xubuntu to fat32 again...

---

### Post by Sjovan on 2008-04-29
You have to download a *.deb file from operas home page. Note: stable install got flash issues, download the beta.

---

### Post by ambercomm on 2008-04-29
Hi hyper_ch,

Thank you for your prompt reply. 

I am afraid my knowledge of the computer is limited to clicking icons and choosing from the menu under ms-window. Therefore I have follow-up questions on your reply:

1)Deleting drive D:
> **hyper_ch said:**
> 
Naming partitions and give them a letter is a windows things... if you want sda5 to be used for Xubuntu, then delete that partition... or from windows just delete the d: partition... when it's unpartitioned you can then just select "use largest continuous empty space"

How do I go about "deleting the D: partition" from window? I would appreciate a step-by-step instructions please. Can I take it that this procedure will not affect my data and programs in Drive C: ?

As a matter of interest, what would happen to the data in Drive D: if these data were present prior to the deletion?

2) Installing from WUBI
I have been reading some of the articles on WUBI on the Ubuntu  website, WUBI blogs and Wikipedia. Nowhere did they explicitly mention that one can install Xbuntu under ms-window using WUBI. Can this be done? How do one go about this? As you know, I already have a CD with Xbuntu 8.04 iso image.

Many thanks.

Hi Sjovan, 

Thanks for your advice. I shall give your suggestions a go if FF3 proves to be too much for my hardware. 

Cheers!

---

### Post by hyper_ch on 2008-04-29
> **ambercomm said:**
> As a matter of interest, what would happen to the data in Drive D: if these data were present prior to the deletion?


Just delete that partition with a partitioning tool... all data on it will be deleted.

---

### Post by ambercomm on 2008-04-29
Hi hyper_ch,

Thank you for your reply and advice. 

> **hyper_ch said:**
> Just delete that partition with a partitioning tool... all data on it will be deleted.

While I have a general idea what a partitioning tool does, I do not know how or where to invoke this utility (Does this utility reside within the ms-DOS system?)... A computer-savvy neighbor helped me to re-install and partition the hard drive a few years ago when the original hard disk broke-down. Unfortunately he has since moved. 

As I have indicated in my previous post, my knowledge of computer softwares is limited. So I would very much appreciate a step by step instruction on where, how to get and use the appropriate partitioning tool. Any pointer from anyone in this direction will be much appreciated. 

Still on the topic of Wubi, can anyone in the forum advice on how to install Xbuntu 8.04 using Wubi please? I think this is a great idea.... installing Linux under the familiar ms-window system to try out and if satisfied, make Linux the sole operating system. 

Where can I find an iso package with Xbuntu and Wubi included? Alternatively, how do I identify the Xbuntu iso package with Wubi included if this is already available on the Ubuntu website?

Many thanks for any help rendered.

---

### Post by hyper_ch on 2008-04-30
there's a dos program called fdisk that can take care of partitioning... inside Windows I don't know any graphical tool that comes included... with VISTA you have a gui partitioning tool...

But probably the simplest way would be to get the GParted LiveCD.

---

### Post by ambercomm on 2008-04-30
Hi hyper_ch,

Thank you for coming to my aid once again. 

Last night, I had a quick look through the Gparted manual and some  articles on the filing structure on a PC hard disk. It would appear  that the mechanics involved in modifying hard-disk partitions are quite tedious, fraud with pitfalls for the uninitiated. Maybe I should give Wubi a try first. 

In any case, thank you for all your help hyper-ch. It is much appreciated 

kind regards!

---

