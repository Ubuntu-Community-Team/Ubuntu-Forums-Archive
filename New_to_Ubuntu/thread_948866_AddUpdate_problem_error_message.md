---
title: "Add/Update problem error message"
date: 2008-10-15
forum: New to Ubuntu
---

### Post by NoL618 on 2008-10-15
I'm trying to add/update programs and I'm getting this error message:

"Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'."

What does this mean? And what do I have to do??

Thanks!:KS

---

### Post by Nxion on 2008-10-15
> **NoL618 said:**
> I'm trying to add/update programs and I'm getting this error message:

"Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'."

What does this mean? And what do I have to do??

Thanks!:KS

What are the commands you are running when you receive this error message?

---

### Post by NoL618 on 2008-10-15
I'm sorry, I'm new...what do you mean by "commands I am running"?
:(

---

### Post by Ryadt on 2008-10-15
Try ```
sudo apt-get install -f
``````
sudo apt-get update
```

Post back the error messages you might get.

---

### Post by Nxion on 2008-10-15
> **NoL618 said:**
> I'm sorry, I'm new...what do you mean by "commands I am running"?
:(

Sorry about that :)

I meant how are you trying to update your machine? From a terminal? From the Update Manager?

As for installing a application, how are you doing that? Are you installing from a terminal? Are you using a .deb file? Or are you doing that another way?

Also...

Can you post your sources.list file. This file contains the server lists that have all the software for Ubuntu. Run this and please post it:

```
sudo cat /etc/apt/sources.list
```Thanks :)

---

### Post by NoL618 on 2008-10-27
here is the scouces list file:  
Sorry, I was away for a bit...

#deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release amd64 (20080702.1)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse


what does all this mean?

---

### Post by NoL618 on 2008-10-27
> **Ryadt said:**
> Try ```
sudo apt-get install -f
``````
sudo apt-get update
```

Post back the error messages you might get.


I got this error message

noelle@sunshine:~$ sudo apt-get install -f
Reading package lists... Error!
E: Unable to write mmap - msync (28 No space left on device)
E: The package lists or status file could not be parsed or opened.

---

### Post by porteclefs on 2008-10-27
those are a list of sources that apt-get checks to download / upgrade from. apt-get is a way of installing software on your ubuntu machine in an easy way. when you run the command 

$ sudo apt-get update

your computer checks all of the websites in that source list for updates. if you edit that source list to include some piece of software that isn't part of the default source list, then you have to make sure that the syntax is right so that apt-get can successfully check that new address for updates. once you run the above command, ubuntu knows what is there in your sourcelist that you don't have installed and then you can run commands like:

sudo apt-get install (some program name)

---

### Post by porteclefs on 2008-10-27
you might want to check to make sure you have room on your harddiskdrive.

what are the specs on your machine?

---

### Post by Elfy on 2008-10-27
Hi - can you open aterminal, run this command and then paste the output here please

```
df -h
```

Can you also use code tags - either the # button on the text box toolbar with New Reply - or if you quick reply type [noparse]```
[/noparse] before the paste and [noparse]
```[/noparse] after the paste

[http://ubuntuforums.org/misc.php?do=bbcode](http://ubuntuforums.org/misc.php?do=bbcode) - shows the different codes which can be used

---

### Post by NoL618 on 2008-10-27
Here is what I got:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             2.7G  2.7G     0 100% /
varrun               1007M  104K 1007M   1% /var/run
varlock              1007M     0 1007M   0% /var/lock
udev                 1007M   64K 1007M   1% /dev
devshm               1007M   24K 1007M   1% /dev/shm
lrm                  1007M   44M  963M   5% /lib/modules/2.6.24-19-generic/volatile
overflow              1.0M   36K  988K   4% /tmp
gvfs-fuse-daemon      2.7G  2.7G     0 100% /home/noelle/.gvfs

How do I get more space?  Why would I not have any space left?  I just downloaded Ubuntu about a month ago, only really use it for school work and surfing the net?

---

### Post by Elfy on 2008-10-27
It was a very small drive to start with by the look of it, you can clean the apt cache to get some room

```
sudo apt-get clean
```

That will remove downloaded deb files and allow you to use the system, but I would look at resizing to get a bit more room.

---

### Post by NoL618 on 2008-10-27
> **forestpixie said:**
> It was a very small drive to start with by the look of it, you can clean the apt cache to get some room

```
sudo apt-get clean
```

That will remove downloaded deb files and allow you to use the system, but I would look at resizing to get a bit more room.

I tried the command, and nothing happened....
:(

---

### Post by Elfy on 2008-10-27
The command shouldn't show anything does df -h gives the same result now?

If it doesn't then return to your other thread nad deal with that.

Once you can use the system I would think about resizing to get a bit more space - 4Gb is the recommended minimum.

---

### Post by NoL618 on 2008-10-27
holy hell!
It worked!!  THANKS SOOO MUCH!!


so now how do I upgrade? I have an external hard drive.....?:popcorn:

---

### Post by Elfy on 2008-10-27
Do these -

```
sudo apt-get update
sudo apt-get install -f
sudo apt-get upgrade
```

But before you start do you have enough room to do so? If you're not sure post df -h
here.

---

### Post by NoL618 on 2008-10-28
this is what I got after df-h

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             2.7G  2.6G   27M  99% /
varrun               1007M  104K 1007M   1% /var/run
varlock              1007M     0 1007M   0% /var/lock
udev                 1007M   64K 1007M   1% /dev
devshm               1007M   24K 1007M   1% /dev/shm
lrm                  1007M   44M  963M   5% /lib/modules/2.6.24-19-generic/volatile
gvfs-fuse-daemon      2.7G  2.6G   27M  99% /home/noelle/.gvfs


do I have enough room to do the other codes?

---

### Post by SunnyRabbiera on 2008-10-28
2.7 GB for your main partition?
You need at least 4.
How big is your hard drive?
How did you partition?

---

### Post by Elfy on 2008-10-28
nol618 - you have enough room to just about keep it going - you do not have enough room to do an upgrade.

You need to resize.

---

### Post by Elfy on 2008-10-28
<snip> double post courtesy of the forum

---

### Post by NoL618 on 2008-10-28
How do I resize?

---

### Post by Elfy on 2008-10-28
You can do so from the livecd there is a partition editor on there. Make sure you have backups of anything you can't afford to lose.

You might need to resize an extended partition to accomplish it - can you run 

```
sudo fdisk -l
``` and post result here

How much spare space do you have avilable in windows?

---

### Post by NoL618 on 2008-10-28
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18706   150255913+   6  FAT16
/dev/sda2           18707       19457     6032407+   5  Extended
/dev/sda5           18707       19081     3012156   82  Linux swap / Solaris
/dev/sda6           19082       19433     2827408+  83  Linux
/dev/sda7           19434       19457      192748+  82  Linux swap / Solaris


im not sure how much space I have left on windows.....:confused:

---

### Post by Elfy on 2008-10-28
Well you have 2 swaps so that's a start in gaining some room I would guess.

You need to have some idea of how much room you have available to resize the partition before you start.

Can you post the results of 
```
free -m
cat /etc/fstab
```

---

### Post by NoL618 on 2008-10-28
here are the results:


 total       used       free     shared    buffers     cached
Mem:          2013        559       1454          0         12        260
-/+ buffers/cache:        286       1727
Swap:          188          0        188
noelle@sunshine:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=b9ab2b13-8c2f-4147-bfb5-22c7c6490c4e /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=f91cfc86-5706-41ea-aef5-35e05ff94907 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


i restarted and went into the boot menu, it said i have 2046mb available....

---

### Post by Elfy on 2008-10-28
Ok so you can remove sda5

not sure what you mean by > i restarted and went into the boot menu,it said i have 2046mb available.... is that your memory or do you really only have 2Gb left from your 160Gb hard drive

---

### Post by NoL618 on 2008-10-28
lol...that was my memory.....

how do i get rid of sda5? and what is it?

---

### Post by Elfy on 2008-10-28
It's one of two swaps but its' not mounting.

Using the livecd - run the partition editor in system admin menu, you need to do it in this order

turn off swap sda5 and 7 - right click on partition - unmount
reduce sda1
grow sda2
grow sda6

---

### Post by NoL618 on 2008-10-28
ok...when I inserted the livecd and restarted I get 4 options:

Ubuntu generic
Ubuntu recovery mode
other operating systems
Dell Utility Partition

When I choose dell utility partition, nothing happens...its like the computer freezes and I have to reboot.

Am I going about this the right way?

---

### Post by Elfy on 2008-10-28
do you not actually have any other os but ubuntu installed on your pc? you don't have any windows at all installed?

---

### Post by NoL618 on 2008-10-28
I don't think so, is that bad? :(

---

### Post by Elfy on 2008-10-28
Not as such :) seems perfectly normal to me lol

Can you run the livecd - open the partition editor and then do a screenshot - screenshot is in accessories menu.

You appear to have an absolutely enormous recovery partition, they are normally about 7Gb - it seems it is about 150Gb

---

### Post by BlackS3th on 2008-10-28
Well ... i have a problem .. maybe its easy though ... ok here it comes all ready:lolflag: now my update manager isnt working or smt ... im new so excouse me "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report." so .. i report ... now whats going on people?:confused:? ...{noob here}

---

### Post by NoL618 on 2008-10-28
im not sure I know where the partition editor is then...:confused:
do I need to resart? 

I've inserted the livecd....heres the screen shot...

---

### Post by Elfy on 2008-10-28
it's in the system admin menu - I need a screenshot of the editor window - I know what the livecd looks like :)

---

### Post by zakirs on 2008-10-28
partition editor is in ... system>administration> partition editior

---

### Post by Elfy on 2008-10-28
@BlackS3th - open a terminal in accessories - run this command ```
sudo dpkg --configure -a
```

It will ask for password - use your's - it will be invisible that is normal.

---

### Post by NoL618 on 2008-10-28
hehee....sorry...

I went to system>admin>
and I do not have the option of partition editior...

here is another screen shot of my system/admin menu

---

### Post by Elfy on 2008-10-28
You have to be running the livecd not running your installation.

Boot the livecd - once that has booted - you will find the partition editor in the sys admin menu.

---

### Post by NoL618 on 2008-10-28
this is probably an abundance of stupid questions...im sorry...

when i put the cd in, it shows on the desktop, thats it...im not sure what to open to boot it.  

When i restart with the cd in the drive, nothing is different...i have the same options as before...

---

### Post by Elfy on 2008-10-28
It's ok take a deep breath - leave the cd in the tray and reboot - the pc should start with the livecd :D

When it has started you can do what I have asked for. WE need to be in the livecd environment so that we can do the resizing - I can stay around for another couple of hours if you need it :)

Have you ever used irc? once you have the livecd booted we can use irc to talk while you are doing the job if you want. 

If you've not then we can set it up easily enough ok :)

or you can use pidgin to get on the right channel

---

### Post by NoL618 on 2008-10-28
ok. ::breathing::
the livecd is not booting, nothing is changing, its all going as normal, like the cd isnt even there.  I still get the same four options when I boot up and I get my normal setup...no livecd environment....

I have not used an irc...not exactly sure what it is...lol
I do have pidgin...:)

thanks for your help!

---

### Post by Elfy on 2008-10-28
mmm - we need to boot the livecd - at some point you must have had it set up to boot from cd - either by changing an option in the bios or if you have a newer type sometimes there is an option to choose boot options.

When you first installed ubuntu how did you do it?

irc - internet relay chat - you can use pidgin 

protocol - irc

server - irc.freenode.net

/join ##beginners-help

I'm in there anyway os if you see me you've got to the right place:)

---

### Post by NoL618 on 2008-10-28
WOW! all that irc stuff....i have noooo idea.....lmao

I originally booted from the livecd, tried it out for about a week and then did the install from there.  Everything worked great for a while, until I tried to figure out my sound issue which is still not working...and then the update thing with broken packages....

I will be leaving for a few hours...bbs! we will reconnect!

---

### Post by BlackS3th on 2008-10-28
Damn ... HoW u do this guys ??? it worked..:) LOOOOOOOOVE ya u r :KS

---

### Post by Elfy on 2008-10-28
ok - I'll be gone then I expect - if you get the livecd booted - post the screenshot - if no-on else looks I'm subscribed to this thread and will look in morning - I'm on the irc channel most of the day so if you go there I'm sure it'll be fine

Once you actually can get the livecd booted then it won't take very long to do what's needed to resize your drive and you'll be able to carry on :)

---

### Post by BlackS3th on 2008-10-28
1 more think ...:(... it says ... that it found one broken package ... "must be the limewire package i tryied to download but the power went off when i was trying to download it ..." and it also says to use the broken package filter to find it ... where is that?

---

### Post by Elfy on 2008-10-28
in syanptic - system admin menu, edit - fix broken packages

once it's fixed you can get frostwire - which is limewire without the ads

[http://www.frostwire.com/](http://www.frostwire.com/)

download and double click the file

---

### Post by BlackS3th on 2008-10-28
U r the man .. U rock:guitar:... Thnx a lot man ...2 thanks to ur courage of keep going helping!!!

---

### Post by NoL618 on 2008-10-28
Thanks...
I added the account to pidgin, but cannot figure out how to work the thing...lol

I've also tried to boot the livecd as well....no luck, still going to the my settings.......

Thanks again!  :KS

---

### Post by Elfy on 2008-10-29
it's not really any differnt than any other afaik - as long as you are joined to the right channel you should show up, once you are connected to freenode then use the /join command I gave

on way or the other you are going to need to boot a livecd - if not the buntu one then a partition editor - if you're pc/laptop is new it could well have a 'boot from' option - esc, del, f1 it should show on the screen as it boots

---

### Post by NoL618 on 2008-11-12
Hi Forest!
so...i finally got up enough ambition to tackle this again...and I guess with less stress I figured it out...

I booted the live cd, and got rid of sda5, not sure what to do next...
I also figured out the IRC thing....

Here is my screen shot of the partition editior...:)

---

### Post by Elfy on 2008-11-12
Well I have to say that I have no idea what os you're running - I assume that you can still get into it? Can you?

At the moment it appears that you don't have any linux file systems - or were you orioginally running wubi?

Can you confirm please.

---

### Post by NoL618 on 2008-11-12
I was running windows vista...and then I installed ubuntu about two months ago...

just those two...

---

### Post by Elfy on 2008-11-12
> I assume that you can still get into it? Can you?

Umm - do they work?

It appears to em that you have use less than 5Mb of your drives :)

---

