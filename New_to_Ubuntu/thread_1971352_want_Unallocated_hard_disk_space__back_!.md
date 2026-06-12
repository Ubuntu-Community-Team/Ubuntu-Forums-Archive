---
title: "want Unallocated hard disk space  back !"
date: 2012-05-02
forum: New to Ubuntu
---

### Post by kaling on 2012-05-02
Hi Guys ! 
I heard so much about Ubuntu 12.04  that i finally installed it in my PC after two attempts ( the second attempt was succesful ) During the first ( unsuccessful ) installation , I had (mindlessly) chose the site of installation as my 1 terabyte WD external hard disk drive. During the installation process , I ( again mindlessly) allocated 119 GB for ubuntu .While the process was going on , it got interrupted abruptly due to a power failure ( common in this part of the world, India ). When the power resumed , I again ran the installation from the USB ( Ubuntu prompted me to uninstall the previous faulty installation and to reinstall , which I did , but this time on C: drive ). This installation was a success but for loss of my 119 GB of precious space in my 1 TB Ext. HDD . How do I get it back ? Any help is appreciated ! i am attaching a screenshot .

---

### Post by dankdave on 2012-05-02
If I understand correctly, you have two hard drives.  An internal hard drive, and an external hard drive.

If you installed ubuntu onto your external hard drive, then the only way to get that space back is to reformat that section, and have a program resize it for you.  If you boot into the live CD, and run gparted, that has the capability of doing that for you.

---

### Post by oldfred on 2012-05-02
Welcome to the forums.

With gparted, you normally need to use liveCD/USB, but if only working on another drive you can unmount all the partitions and edit from your install. While gparted is on the liveCD, it is not normally installed as you cannot easily use it in an install, so you have to add it. 

sudo apt-get install gparted

You then should be able to delete the swap, assuming you have swap on you same drive as your install, and then reformat the unallcated to NTFS. You could expand the Windows NTFS if you want.

I normally suggest a shared NTFS partition for any data you may want to use in both systems and make any Windows install read-only to avoid Windows issues. Windows does not like other systems writing into it, but sometimes you have to to make repairs. :) You should not hibernate Windows either as than can cause issue.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by kaling on 2012-05-02
> **dankdave said:**
> If I understand correctly, you have two hard drives.  An internal hard drive, and an external hard drive.

If you installed ubuntu onto your external hard drive, then the only way to get that space back is to reformat that section, and have a program resize it for you.  If you boot into the live CD, and run gparted, that has the capability of doing that for you.

Thanks for the prompt reply dankdave  \m/- You got it right . I have two hard drives and also I am a complete newbie :D Did you see the Screenshot ?

How do I reformat "that section "?

How do I boot into a liveCD ( I don't think I have one) ? I installed Ubuntu using a pendrive linux

I installed gparted but I hardly know how to use it ( I opened it and it only shows what I already know ie allocated space , extended partition etc etc ) 

Is there a simpler way ?

Thanks already :D

P.S.- How do I add a new user ? I couldn't find any "buttons" to do that !

---

### Post by kaling on 2012-05-02
> **oldfred said:**
> Welcome to the forums.

With gparted, you normally need to use liveCD/USB, but if only working on another drive you can unmount all the partitions and edit from your install. While gparted is on the liveCD, it is not normally installed as you cannot easily use it in an install, so you have to add it. 

sudo apt-get install gparted

You then should be able to delete the swap, assuming you have swap on you same drive as your install, and then reformat the unallcated to NTFS. You could expand the Windows NTFS if you want.

I normally suggest a shared NTFS partition for any data you may want to use in both systems and make any Windows install read-only to avoid Windows issues. Windows does not like other systems writing into it, but sometimes you have to to make repairs. :) You should not hibernate Windows either as than can cause issue.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

Hey Oldfred ! Thanks for the prompt reply .

How should I use the USB to use the Gparted for getting my space back ?

Correct me wherever and whenever I am wrong .

i plug in the USB .
Then I restart the PC . Press f12 and choose the USB as the boot device . The boot menu comes up and 
Now I am stuck .
How do I proceed from the boot menu ?

Any help is appreciated .

Thanks already !

---

### Post by oldfred on 2012-05-02
USB should have two choices, one is an installer and the other is use it to test or the "liveCD". Gparted is one of the programs built in.

I am not as familiar with Unity as I use fall-back, but I think you click on the icon top left and type in gparted. Click on icon & It should then run.

See links above for details on using gparted. Upper right is combo box to choose drive. Little key symbols mean a partition is mounted and any mounted partition in an extended partition mounts the extended also. I only do one major change at a time. You have to click on check mark to actually run the changes.

---

### Post by Baldrick_NZ on 2012-05-02
"Is there a simpler way ?"

Short answer, no.

But if you follow the instructions given one step at a time (and rechecking each step before actioning), you shouldn't go wrong.

1/ reboot your PC into your USB drive
2/ choose "Try Ubuntu" when asked
3/ from dash, choose "gparted'
4/ once gparted has loaded, take a screenshot, and repost here so we can see what we're dealing with more clearly.

---

### Post by kaling on 2012-05-03
> **Baldrick_NZ said:**
> "Is there a simpler way ?"

Short answer, no.

But if you follow the instructions given one step at a time (and rechecking each step before actioning), you shouldn't go wrong.
1/ reboot your PC into your USB drive
2/ choose "Try Ubuntu" when asked
3/ from dash, choose "gparted'
4/ once gparted has loaded, take a screenshot, and repost here so we can see what we're dealing with more clearly.

hey guys , Thanks for your enthusiasm ! \m/- 

I plugged in the USB .

I Chose " Run from USB "

I got to gparted and selected the External hard drive in question .

And here's the screen shot ( Please see attachment )

Now as you can see  there is unallocated 108 gb which I want back  ! 

Thanks already !

---

### Post by oldfred on 2012-05-03
A couple of choices, you can just delete swap also and let the automatic installer use all of the unallocated space to put a new install in.

Or you can create your own partitions. Then you have some control of size and can create a separate /home if you want. But then you have to use Something else or manual install and choose which partition is / (root) which is /home and swap. You also choose ext4 (or ext3) for / & /home. Then next time you install, you have all your user setting in /home so you can reinstall and reuse your /home WITHOUT reformating to preseve you settings. Backups are still important.

Difference in versions for installer is minor.
Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)
Install 11.10 with screenshots of Unity, gnome3, & gnome fallback - Not everything is necessary, but shows how to do many things
[http://*********************.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](http://*********************.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

---

### Post by kaling on 2012-05-03
This is the latest screenshot . I deleted the linux swap and now it looks like what it is :D

How do I claim my space back ?

Thanks already !

---

### Post by oldfred on 2012-05-03
I do not know if the automatic installer will recreate the extended partition. I did just test using the liveCD in automatic mode and it found I had 40GB of unallocated on my sdc drive and just used it.

If you just want to delete the extended you can.

You have to click on the check mark to run the pending operations. I prefer to run each and not create a queue.

---

### Post by kaling on 2012-05-03
hey Oldfred ! What's up ? Thanks for all your help .

Umm.. I am a bit confused here . As I already mentioned before , I had a failed installation once ( in my external HDD) . now i have a proper installation already in C:/ . 
Using Gparted, I deleted the swap  and I guess that swap space got merged with the unallocated space in the extended partition as you can  see from the screenshot .
This is where I am stuck now . I want my /dev/sdc1 to show 931.15 GB ( I mean all of it ) but it's showing only 820.68 gb and 110.83 as unallocated space .

Thanks for putting up with me ! I am getting there slowly ! 

 Thanks already !

---

### Post by kaling on 2012-05-03
Yey! I got it back ! 

I just deleted the extended partition and resized ! 

Thanks oldfred , Dankdave and Baldrick_Nz ! \m/

I just hope that the data isn't lost as I hadn't backed it up :D

I 'll be back \m/

---

