---
title: "HOWTO: Get Your iPod to work with GTKPod"
date: 2005-05-24
forum: Outdated Tutorials &amp; Tips
---

### Post by Merc248 on 2005-05-24
I personally had a lot of problems trying to get my iPod to work correctly with GTKPod.  It seems that GTKPod always made the vfat filesystem on the iPod read only every time I wanted to do an operation on it.  However, I finally found out how to make it work correctly. :p  Keep in mind that you will need an iPod already formatted in Windows through iTunes before you can proceed with this HOWTO.

First, I will explain how to get GTKPod up and running first, then I will go over the distinct problem that I was talking about.

If you want AAC support for GTKPod, type the following command in in the terminal:

```
sudo apt-get install gtkpod-aac
```

You'll need to make sure that you have the Hoary Backports repositories added to /etc/apt/sources.list in order to use the gtkpod-aac package.  Check [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) for more information.

Otherwise, type this in:

```
sudo apt-get install gtkpod
```

Keep in mind that you cannot have both packages installed at the same time, so I advise you to just use the AAC package.

You can likewise search for "gtkpod" in Synaptic and install it through there.

Next, in order for it to properly appear in the menu, type in:

```
killall gnome-panel
```

I'm assuming that GNOME or KDE will automatically create a mount point for your iPod under the /media/ directory.  If not, edit fstab, and add a new entry into it.  Here's what I personally added at the bottom of fstab:

```
sudo gedit /etc/fstab

...

/dev/sdc2	/media/MERCPOD  vfat	nosuid,noauto,nodev,rw,umask=077,gid=1000,uid=1000,user,defaults,noatime,iocharset=utf8	0	0
```

That should be enough to get your iPod up and running.

When you go into GTKPod, go to Edit > Preferences, Input/Output tab.  I personally didn't get the auto mount/unmount thing working, so I left it unchecked.

However, the most important field in that entire preferences window is the iPod Mount Point field in the Input/Output tab.  Fill in the mount point field with the appropriate folder that GNOME/KDE created (or that you yourself created) for your iPod.  With GNOME, it automatically created the folder /media/MERCPOD, MERCPOD being the name of my iPod that I entered in when I had it set up in Windows.

Restart the program.  It will automatically fill the GTKPod database with all of the songs and playlists that you have stored on your iPod prior to setting up GTKPod.

However, here is the rub: GTKPod seems to work randomly for different people.  It will work on one synchronization, yet it will stop working for subsequent synchronizations.  Others will find that it will not work, period.  There's a simple solution to that, actually; just type the following command in into your console app:

```
sudo dosfsck -a /dev/sdc2
```

sdc2 being the partition where your iPod data resides.  Be sure to check out /etc/mtab with gedit in order to confirm which /dev/ node is being used for your iPod.

The above command will execute dosfsck, and automatically fix any errors encountered in the vfat partition.

After that, GTKPod should work flawlessly without your system automatically mounting your iPod as read only.

---

### Post by poofyhairguy on 2005-05-24
Good and needed how to. Thanks.

One thing, please make some kind of note that the gtkpod-aac is only in the backport repo.

---

### Post by Merc248 on 2005-05-24
Whoops... didn't know. :p  I added the backport repositories right after I installed Ubuntu, so I had no clue... I'll be sure to add that note, though.

---

### Post by Sionide on 2005-05-24
Reckon this will only work for iPods or any mp3player? I'm having trouble getting anything out of my Rio... Anyone got any links for Rio software which might work on Ubuntu?

---

### Post by poofyhairguy on 2005-05-24
[QUOTE=Sionide]Reckon this will only work for iPods or any mp3player??[/QUOTE]

just iPods. Any iPod.

---

### Post by bored2k on 2005-05-24
[QUOTE=poofyhairguy]just iPods. Any iPod.[/QUOTE]
 I soo wish I had one..

---

### Post by RastaMahata on 2005-05-24
[QUOTE=bored2k]I soo wish I had one..[/QUOTE]
 I NEED one! and I need Angelina Jolie too, but, well, at least I can afford the iPod :P

---

### Post by bored2k on 2005-05-24
[QUOTE=RastaMahata]I NEED one! and I need Angelina Jolie too, but, well, at least I can afford the iPod :P[/QUOTE]
 Tomb Raider for PS1 is cheaper than the iPOD.

---

### Post by andlinux21 on 2005-05-26
my laptop doesnt have firewire anyone know if this card would work with Ubuntu (Compaq's PCMCIA cardbus offers 2 FireWire ports ). I would like to get it so that i can use my laptop with my iPod.

---

### Post by ganatronic on 2005-05-26
Thanks for the write-up. 

Remarkably, I had almost no problems getting my ipod to make sweet love to this program. My gripe, however, is that I can't get my newly added playlists to alphabetise. They show up in the gtkpod playlist list in correct alpha order, but they don't sync that way.

I wish this program had more sorting commands. The general library list is in an unknown order - it makes it difficult to locate certain artists.

So, anyone have alphabetising and sorting advice? I could be missing something.

---

### Post by MicroChris on 2005-05-26
[QUOTE=RastaMahata]I NEED one! and I need Angelina Jolie too, but, well, at least I can afford the iPod :P[/QUOTE]

Do freeipods.com...

I completed mine in two days, and after checking my DHL tracking #, itll be here today!! Yay!

Thanks for the tutorial. This will ocme in handy for sure.

-Chris

---

### Post by Merc248 on 2005-05-27
[QUOTE=ganatronic]Thanks for the write-up. 

Remarkably, I had almost no problems getting my ipod to make sweet love to this program. My gripe, however, is that I can't get my newly added playlists to alphabetise. They show up in the gtkpod playlist list in correct alpha order, but they don't sync that way.

I wish this program had more sorting commands. The general library list is in an unknown order - it makes it difficult to locate certain artists.

So, anyone have alphabetising and sorting advice? I could be missing something.[/QUOTE]
 That's odd... yeah, usually it comes out alphabetically sorted when I sort it as such in GTKPod.  However, the problem I had was that it would sort only when I explicitly told it to sort by changing the sort order from "ascending" to "none" back to "ascending" again.

I don't know, maybe that will work in your case as well?

Oh yeah, thanks for the compliments guys.  I didn't want people to go through the same hell that I went through when I tried to get GTKPod to work properly. ;p

---

### Post by Merc248 on 2005-05-27
Sorry, spoke too soon... the last few stuff I added to my iPod were all unsorted.  I'll look a bit more into this when I get time to...

---

### Post by RastaMahata on 2005-05-27
[QUOTE=MicroChris]Do freeipods.com...

I completed mine in two days, and after checking my DHL tracking #, itll be here today!! Yay!

Thanks for the tutorial. This will ocme in handy for sure.

-Chris[/QUOTE]
 what's that? :o

I want one! I will need help!

---

### Post by andlinux21 on 2005-05-27
[FONT=Comic Sans MS][SIZE=2][COLOR=Navy]I have the 10Gig iPod with Firewire is anyone using a docking station or USB or anything other than firewire I can't seem to get mine to work[/COLOR].[/SIZE] ](*,) [/FONT]

---

### Post by Dethread on 2005-05-27
Works for the Shuffle, too.  :-P

---

### Post by ganatronic on 2005-05-28
[QUOTE=Merc248]Sorry, spoke too soon... the last few stuff I added to my iPod were all unsorted.  I'll look a bit more into this when I get time to...[/QUOTE]


I can't even find sort options. I wonder if I have an old version. "about" says I have 0.88.1. But I only got it a few months ago.

---

### Post by rjs on 2005-05-29
Trying to import AACs into gtkpod gives me this >  Import of '/home/quijote/Desktop/music/2-03 Barbedwired Baby_s Dre.m4a' failed: m4a/m4p/m4b not supported without the mp4v2 library. You must compile the gtkpod source together with the mp4v2 library.

now my understanding of that error message is - "You are using Gtkpod not gtkpod-aac stupid, now go uninstall gtkpod and install gtkpod-aac if you want to be a slave to apples stupid format" So i went to do this, but... aptitude tells me i AM using gtkpod-aac...

Any ideas what to do now?

paz y amor,
-rjs.

**update:** i uninstalled it and reinstalled it, and it didnt change anything, also what is interesting is that it seems to have no problem with the AACs which are already on my iPod (shuffle), just AACs that are in my library that i want to put onto my iPod. Strange.

---

### Post by matthewrevell on 2005-06-05
[QUOTE=Merc248]
```
sudo dosfsck -a /dev/sdc2
```
[/QUOTE]

Why is life never simple?

I'm having the same problem of a previously perfectly functioning iPod suddenly becoming read-only. So, I tried the command above and I'm told:

```
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
Currently, only 1 or 2 FATs are supported, not 123.
```

Any thoughts anyone?

---

### Post by mtenorio on 2005-06-09
Problem. Gtkpod updates my ipod fine. I can see all my music, I can play it and update it. BUT when I unmount the ipod from ubuntu I can't use it! It has a blank screen with the words Charged scribbled on top of a line and that's it. It doesn't respond to buttons or anything else. If I reconect it to the computer it still mounts and works fine but I'd like to have my ipod on the go as I used to.

Any ideas?

Working with ubuntu AMD64
iPod 3G windows formated
GtkPod 0.88

---

### Post by salmazen on 2005-06-24
isn't there any other software that allows to manage the ipod, without formatting it on ITunes on windows?

---

### Post by recover82 on 2005-07-01
I did your steps as described in this post and it was working....but it seems after the dosfsck command when I plug in my iPod it just starts taking charge from the firewire port.

Any ideas?

---

### Post by wunderbread on 2005-07-11
[QUOTE=rjs]Trying to import AACs into gtkpod gives me this 

now my understanding of that error message is - "You are using Gtkpod not gtkpod-aac stupid, now go uninstall gtkpod and install gtkpod-aac if you want to be a slave to apples stupid format" So i went to do this, but... aptitude tells me i AM using gtkpod-aac...

Any ideas what to do now?

paz y amor,
-rjs.

**update:** i uninstalled it and reinstalled it, and it didnt change anything, also what is interesting is that it seems to have no problem with the AACs which are already on my iPod (shuffle), just AACs that are in my library that i want to put onto my iPod. Strange.[/QUOTE]

I had the same exact problem.  If you compile from source, it works.  I'm not sure why, but it does.

---

### Post by debian_n00b on 2005-07-16
Thanks for the writeup. But I think you should revise it for newbies. As an example, your manual fstab entry to mount the ipod would not work for everyone. Please document what it is you are doing and how users can edit your example to suit their specific setup.

---

### Post by atf487 on 2005-07-18
[QUOTE=debian_n00b]Thanks for the writeup. But I think you should revise it for newbies. As an example, your manual fstab entry to mount the ipod would not work for everyone. Please document what it is you are doing and how users can edit your example to suit their specific setup.[/QUOTE]
 i've got a question for anyone who uses the ipod shuffle: will it charge in linux? i dont want to have to boot into windows or buy a stupid docking thing just to be able to always use it in linux.

---

### Post by rjs on 2005-07-20
There is no prob with it charging under linux. It should automatically mount (just like any other usb mass storage device), however gtkpod still doesnt manage it properly. I have never got it to work correctly, my brother did, but somehow managed to fry it, and ive heard stories from my clug that other people have had  trouble using gtkpod with it. If you are using it as a normal mass storage device, rather than an ipod, however, it works great with no probs. But if you have a copy of mac os X or windows, it might be an idea to use that to update the songs on it.

If you do decide to play with gtkpod, remember that shuffles live in a different place to normal ipods, and you have to change the defualt place that gtkpod looks before you can start playing.

paz y amor,
-rjs.

---

### Post by crane on 2005-08-18
I have had absolutly no lusk at all with mine. I've had an Ipod mini for 2 day and have yet to hear one freaking song. When I go to about on my ipod (mini) it tell me I ave a capacity of 3.7 gig and 1.3 availible and yet I can find no files on it.
This is very frustrating. I just wanna enjoy my ipod and yet it looks like I will be returning it for somethong else
 :-|

I tried the fstab entry but it did not seem to work. Do I need to mount -a to have it working. I did try this an was told that, line 13, (the line I added was wrong. Any ideas?

---

### Post by crane on 2005-08-19
Crazy stuff man.
I guess sometimes one has to drop back and punt. I didn't add the fstab line but cleaned everything off and started over and now I sitting here enjoying the sounds of A Perfect Circle on my ipod!!!

---

### Post by Zelut on 2005-08-20
When I connect my ipod dmesg shows a connection fine but I have no mount point, no listing of songs or access anywhere.  If anyone could give me some tips I'd appreciate it...

---

### Post by Trin on 2005-09-12
Hey Guys

First, thanks a lot for this how to! but stupid as I am, i gave my iPod a name with blanks.. so the created folder's name is: /media/IPOD VON TR
i tried to edit fstab, but.. :

df: `/media/IPOD': No such file or directory
df: `VON': No such file or directory
df: `TR': No such file or directory

So has anyone any idea how to change the name of my iPod? Or is there any other way to just change the foldername my iPod creates?

Thanks a lot for ur help!

---

### Post by wallstquant on 2005-09-14
just a guess but try putting an \ character before the spaces: /media/IPOD\ VON\ TR

---

### Post by Velox Letum on 2005-09-15
\ escapes the spaces, so that'll work. Also I just created a mounting/unmounting script which I use to mount my iPod, then I run gtkpod.

[php]
# iPod Mount/Unmount
# Written by Xorlev (Velox) 2005

DEVICE=/dev/sdb # iPod Device, usually 
MOUNT_POINT=/mnt/ipod # Where the iPod's files are mounted
PARTITION=2 # Only needed if using a custom partition table

case "$1" in
  mount)
	echo -n "Mounting iPod at" $MOUNT_POINT"..."
        modprobe uhci_hcd
	modprobe sbp2
	(sleep 1 && mount -t vfat -o rw,uid=1000,gid=1000 $DEVICE""$PARTITION $MOUNT_POINT) &
	echo "iPod mounted."
        ;;
  umount)
        echo -n "Unmounting iPod at" $MOUNT_POINT"..."
	
	umount $MOUNT_POINT

	echo "iPod unmounted"
        ;;
  *)
        echo "Usage: ipod {mount|umount}"
        exit 1
esac

exit 0
[/php]

---

### Post by Trin on 2005-09-15
Hi guys

thanks for the replies.. when i try to write \ instead of a single space it doesnt work either.. gtkpod isnt able to find the mounted iPod..

but never mind, i'll rename it ander windows and then i hope i wont have any more problems ;)

have a nice day!

---

### Post by [pl]ice on 2005-09-15
bit of warning :D)
just used windows itunes , formatem my ipod, after using with gtkpod, then when after that i used gtkpod, gtk uploaded songs, and they actually didn't play :) cleaning the fat32 helped :)

there is another program for ipod (with wine....)   :
[http://www.cs.duke.edu/~geha/ipod/](http://www.cs.duke.edu/~geha/ipod/)

enjoy :)

EDIT:

had to format/restore under windows my ipod, then it worked w/o problems with gtkpod, bloody iTunes formated it to hfs+ (i think what is called) FS, and nothing else could wirte correctly to it!!!

---

### Post by kleeman on 2005-09-17
[QUOTE=Trin]Hi guys

thanks for the replies.. when i try to write \ instead of a single space it doesnt work either.. gtkpod isnt able to find the mounted iPod..

but never mind, i'll rename it ander windows and then i hope i wont have any more problems ;)

have a nice day![/QUOTE]

Yeah that is an annoying problem. I solved it today as follows:
My daughter called her ipod SOPHIE'S IPOD so it mounts at /media/SOPHIE'S IPOD
I just went
sudo ln -s /media/SOPH* /media/ipod

which created a new linked mountpoint called /media/ipod. Use this one in gtkpod. Worked for me...

---

### Post by schermozzel on 2005-09-30
How do i disconnect it safely? The "do not disconnect" message won't go away

---

### Post by aysiu on 2005-09-30
[QUOTE=schermozzel]How do i disconnect it safely? The "do not disconnect" message won't go away[/QUOTE] Read [this thread](http://ubuntuforums.org/showthread.php?p=376734#post376734)

---

### Post by [pl]ice on 2005-09-30
hm, i don't give a damn about disconnected or not, apple saind in the man that if the drive is unmounted then it's ok :/ i think the most important part is when program updated ipod's d.base , at the end of transfer.... :D
 
  do you guys use gnupod ??  i stil have problems with gtkpod, wont update my database and files are there w/o any dbase ....

---

### Post by 23meg on 2005-09-30
i'm having a weird problem with the latest GTKPod in Breezy (the old version in Hoary backports didn't have this): when i try to recursively add directories (with spaces in their names) it reports that "the file or folders are missing" and just won't upload them. anyone having this?

---

### Post by Zelut on 2005-10-09
I've added the 'official' backports to my repositories list but I can't seem to find the gtkpod-aac file.  Can anyone give me some tips?  I've got a user that is sold assuming I can get her iPod to work...

---

### Post by atf487 on 2005-10-09
Build GTKPod yourself from source, I could never get the gtkpod-aac binaries to actually accept aac files.

---

### Post by shanghaipi on 2005-10-20
i can't get gtkpod to work in breezy either, sucks that i'm using windows for it....

---

### Post by cagljevic on 2005-10-27
i need help getting my ipod shuffle to work.  i have tried various usb ports on my computer, none of which detect the ipod, at least i can't see any indication of it.  the ipod worked without issue in xp and the device was named 'clarence' within itunes.  i did a search for 'clarence' incase it was mounted somewhere i wasn't aware of, but not such luck.

ubuntu 5.10 w/ 2.6.12-9-686
intel d875pbz motherboard
1gb ipod shuffle

any help with this would be great.

**i checked in the device manager and did find reference to the device, but there were not /dev/ locations for it, so i'm not sure what i am supposed to do with it...**

-mark

---

### Post by [pl]ice on 2005-10-27
hey, i just burned my ipod mini :/  
any ideas? i rebooted it, after it jammed, then played ok, then froze, no reboot worked, just the screen lightened up and stayed like that, ipod hot hell hot, and ... that's it. when i plugged it to pc, the hd sounded like on v.high revs ... :/ sux

---

### Post by braynyac on 2005-11-03
cagljevic,

I had some issues getting my iPod detected with that kernel...I looked in my dmesg, and the computer was seeing it, but would not mount it.  So I reverted back to 2.6.12-9-386, and everything is working peachy again.

~braynyac

---

### Post by Dustismo on 2005-11-04
I can't seem to get gtkpod-aac from the repository.  I added the backports:

```
deb http://archive.ubuntu.com/ubuntu hoary-backports main universe multiverse restricted
```

and I update 

```
$ sudo apt-get update
$ sudo apt-get install gtkpod-aac
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gtkpod-aac
```

Any help?
-Dustin

---

### Post by mrzud on 2005-11-04
I had to build gtkpod from source to be able to get aac support. After installing all those damned dependencies also I had trouble with it recognizing the command gtkpod from the terminal so I created a link from the default directory it was installed in (which was /usr/local/bin) to I guess where it should have been installed to which i dont know where that is right now, but whatever.  Then it complained about the mp4 libraries not existing so I created symbolic links to them in the "correct location"  I think I could have just either corrected my PATH variable for the kernel (correct?) or changed something in the config or make file... i dunno.

Also mine isnt /dev/sdb its /dev/sda... had to use fdisk to find that out.

And I'm still trying to work out problems. :P
  Having the whole random read only problem and now a problem where my folders are turning into files... great stuff.

Just my experience.

---

### Post by Ubuntu Joe on 2007-01-07
great work guys!

---

### Post by Ubuntu Joe on 2007-01-08
Guys . . .

Help!

I ALWAYS get this . . .

Could not open "iTunesDB.ext" for reading extended info.
Extended info will not be used.

 . . . whenever I try to read my perfectly mounted iPod's iTunesDB . . .

WWHHHYYYY!?!?!??!?

---

### Post by whiteman on 2009-06-08
Why am I showing 2 Ipods? Also I am trying to copy an mp3 file from an audioboook The entire book consists of two  mp3s. I can get one or the other but not both. If I get #1 i cant get # 2 and vice versa. I get a wierd error message --Conversion of 'The Unnecessary War' failed: '"-x" (null)' did not return filename extension as expected. Thats the name of the book..Unneccesary War. MAybe I should change the title of files?

---

