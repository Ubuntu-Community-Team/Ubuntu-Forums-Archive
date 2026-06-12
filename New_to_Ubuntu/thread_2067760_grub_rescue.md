---
title: "grub rescue"
date: 2012-10-07
forum: New to Ubuntu
---

### Post by eslam elbyaly on 2012-10-07
hi,
i had xp sp two and kubuntu 
i deleted kubuntu partition from xp

when i restarted , i got the prompt    grub rescue

-what i have now in my hand is xp sp3 cd and ubuntu live cd
-i tried to boot from xp cd , and i failed , it did not boot ,i just saw the grub rescue prompt again 

-then i tried to boot from ubuntu live cd , it booted with just two options ,either try it or install it .

- when i tried it , i did not see any partions when i explored the home folder.

- i tried also to install it , but when getting the partitionning window , it just see the whole disk as one mass , dev/sda , as i remember , there were no other partitions .
-Iam afraid of data loss.

Notice: i have no network connection , but i have mobinil usb modem .

Please be direct because i am using mobile for writing this thread .

---

### Post by Bashing-om on 2012-10-07
eslam elbyaly; Hi ! Welcome to the forum.

Did you have kubuntu installed inside of windows as a "wubi" install ?
else, when you deleted the kubuntu's install partition, you lost the system bootloader; as grub had chainloaded widows bootloader.

To see your system configuration using GParted:
boot the live cd ->try ubuntu ->dash (top icon) ->search box -> enter the term "Gparted" (without the quotes)-> click on GParted icon that appears below the search box.
The disk devices (sda, sdb, sdc and so on) are listed in the upper right, select the one you are currently interested in. Be careful in GParted, nothing wrong in looking, but be sure of what you are doing, a slip of the fingers can have disastrous results.

This link will provide instruction to install ubuntu as dual boot with windows:
[http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/](http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/)
and:
[https://help.ubuntu.com/community/DualBoot/Windows](https://help.ubuntu.com/community/DualBoot/Windows)

Post back with any additional assistance required.
[INDENT]kind regards <==BDQ

[/INDENT]

---

### Post by houseworkshy on 2012-10-07
This application may be helpful
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
There is also a live cd with it on.  [http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)

And there is UbuntuSecureRemix which is designed especially to make duel booting with other systems easy  [https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)
I'm not sure if one can get a version with KDE, the graphic user interphase in Kubuntu, but KDE can be installed afterwards.

If you backed out from installing before formating you should still have the data so things should be mendable.  Though I don't understand why the live cd can't see anything.  The "try" option from booting up with Ubuntu is the "live session" which is how you can get to gparted which is on the disk.

If gparted won't do it then try boot-repair first.  Secure remix is really more to avoid the same problem if you have to start fresh, though it does have boot-repair inside it.  With the rest of the operating system it is twice as big but if that isn't a problem you could think along the lines of two birds with one stone.  

Either way that means downloading.
For the download you may need to borrow someone elses pc.  
If you can't, and you have enough ram,  you could try a live session  and download to your desktop then burn to cd, 
or download to a stick and boot from that ( if your pc is one that can) 
or burn a cd from the iso on the stick.  
Obviously you want to avoid writing to your hard drive at the moment.
boot-repair is a grapic tool which is fairly clear and easy to use.
Good luck and welcome to the forums.

---

### Post by eslam elbyaly on 2012-10-10
please follow this link , if you can help me , i really am in a bad need of help , 
[http://ubuntuforums.org/showthread.php?t=2067771&page=3](http://ubuntuforums.org/showthread.php?t=2067771&page=3)

thanks in advance

---

### Post by houseworkshy on 2012-10-11
I've read the thread and agree with Darkod that it's is a messed up FAT,  file allocation table.  I also looked at some of your earlier posts  trying to find out what kind of install it was, if you are on the same  set up as you were a few months ago, it's a wubi install.  That means  you installed inside windows rather than alongside windows.  I know very  little about those as I haven't used windows for yonks and preferred to  have Linux more separate, partly to have more boot options, even when I  did.  This issue may have something to do with deleting the Kubuntu  partition from the xp manager instead of uninstalling it, as when it  Kubuntu was installed it will have altered your boot as well as making a  partition.
 

 The following paragraph is mostly invalid now, because your xp disk  won't boot, but knowing that you are mostly offline I'll put the info  here anyway for when it does.  As it happens xp was the last windows  system I used much so, if I remember rightly ( double check as my memory  may be hazy ).  To fix a borked FAT in windows xp.  From 'Disk  Management'>right click on the damaged partition to open the  properties window, choose tools, tick check now, tick automatically fix  file system errors and then 'start'.  That's for later of course, at the  moment even fixmbr type advice is redundant.
 

 I think that you are in data recovery and file system repair mode  first, and mostly offline so I'd use the online time to get a  comprehensive tool.  Windows won't boot nor can it read exe4,  so get a  Linux based rescue distro, preferably a well documented one.  Ideally  one which can run from RAM and has cd/dvd burning software, that way you  can free up the cd drive and copy your files off the exe4 partition,  when you can get at it.  Not knowing how much RAM or knowledge you have I  don't know what to recommend but one of these should fit the bill [http://distrowatch.com/search.php?category=Rescue](http://distrowatch.com/search.php?category=Rescue)
 This brief article may be worth looking at first so you know the names  of some tools to look for in the distro before making your choice [http://www.brighthub.com/computing/linux/articles/104277.aspx](http://www.brighthub.com/computing/linux/articles/104277.aspx)  Some of it is fairly deepend stuff, maybe grab some wikis and manuals  just in case the documents on the cd aren't comprehensive enough.
 

 Another thing to bear in mind is that there is a 4g limit on file size  with FAT32 so if you get to the stage of copying things off the exe4  which might be bigger and you are using an external hd or stick, which  will usually be FAT32,  to get them over you'll need to split them.   This command is in most Linux distro's so &#8220;man split&#8221; in the terminal  for details.  When you get to the stage of having your files safe and  reinstalling windows I'd recommend going with the NTFS file system.   Also if you duel boot again I'd recommend alongside rather than inside.
 

 I'm no expert on this so sorry I can't give better advice.  I know what  it feels like when windows has a wobble fit, the worst is when  irreplaceable work or data is threatened or lost.  I'd used MS operating  systems from the days of 286's and  Dos right through to xp service  pack 3 but bailed out a few months into Vista,  the ratio of time spent  between fixing the tool and actually using it was just getting silly.   Partly my own fault as I was a freeware, which is not the same as open  source, addict. 
Another choice, once your data is safe, would be  going all out Unix, Mac or Linux and installing wine for app's that are  windows only or, as xp is hardly supported at all now, upgrading to  windows7 or 8.  I've used it elsewhere and the GUI is good enough and  gets one round, sysinternals is still available to fill some gaps and cmd is still there.  I'm told by people who've installed it on their own  machines where they can dig into it that windows7 is the best since  xp.
I suspect the people in the thread you pointed at know more than I do about the tools you'll find in whichever distro you get.  Not being an expert on forensics and file system repair all I can offer is a viable road map.  Expect to spend a some time reading up and learning before you get to the few seconds you spend actually typing in the quick fix.  

In the very short term, as your machine isn't broken,  live disto and stick can be used for office type tasks, emails, browsing, media playing, etc.  When it was me with severe software problems on the hd, an unreadable display, I used Knoppix to keep working, meet deadlines and stay in touch.  It's the best of the designed to be run live ones full of stuff including drivers so offline doesn't matter so much, it has some recovery tools too but I can't remember which ones. It does have to stay in the drive though. [http://www.knoppix.org/](http://www.knoppix.org/)  It was using this curiousity of a cover disk to recover data and as an emergancy system when windows blew it's top that got me into linux, I realised I preferred it to what was on the hard drive.  You could use Ubuntu as a live stop gap too but it's less good offline as it doesn't have non-free codex drivers flash etc etc.

Puppy linux is also very good for it's size with the added plus that it's so small it can be loaded to ram and it's disk ejected so one can use the cd/dvd drive. There are many varieties of Puppy and may be a rescue flavour one.[http://www.puppylinux.com/](http://www.puppylinux.com/)  and [http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm]("http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm")

Edit. There is I've just browsed and found [http://www.murga-linux.com/puppy/viewtopic.php?t=69651](http://www.murga-linux.com/puppy/viewtopic.php?t=69651)   Could be useful, seems to have many of the tools you may need, no idea  what it's like yet but am taking a look at it.  ... Which I've just  done.  Well it's not so good for general purpose, though it has a few  things and a decent gui. The standard Puppy linux, or some other pupplet  like Fatdog, would be better for daily tasks but if you are ok with  command line tools, because most of the bit's you'd need to fix things  with are, not bad.
  
Sorry so much of the advice involves downloads, the idea is that if you  get this sort of thing you can try to fix it offline and, meanwhile,  continue to use your machine despite the hard drive.  If you are  borrowing a connection, the person whose it is might torrent a distro as  a background task when they are online anyway.  The reason for  suggesting a whole distro is to grab the lot, with documentation, in one  internet session instead of in bits, might be socially better too if  you are depending on a friends kindness.
  
Linux Puppyies are small downloads anyway and it would be worth trying  for the files with one.  If you are lucky it may get them, once they're  out and safe on some external media, and with puppies that can be cd's  or dvd's, then the problem would be reduced to a simple format and  reinstall. Unless you are a video editor the really important stuff is  probably quite small, the replaceable and reinstallable doesn't matter  so don't bother with it.

Good luck.

---

### Post by eslam elbyaly on 2012-10-14
thanks all , i used boot-repair gui , and it is solved

---

### Post by YannBuntu on 2012-10-15
good job! please could you use the Thread Tools in order to mark the thread [SOLVED] ?

---

