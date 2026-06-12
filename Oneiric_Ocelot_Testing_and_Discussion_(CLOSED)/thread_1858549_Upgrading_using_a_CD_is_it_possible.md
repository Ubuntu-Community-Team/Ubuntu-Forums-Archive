---
title: "Upgrading using a CD is it possible"
date: 2011-10-12
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by 23dornot23d on 2011-10-12
Quote:
                                                                      Originally Posted by **23dornot23d**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=11334442#post11334442")                 
                 [I]All sounds good in theory .... 

Easy is good ...... for the majority ...... me included .....

What you propose there is

1 ..... download the latest ISO

2 ..... mount it so it can be used to upgrade from

3 ..... upgrade from CD without a chance of losing it through a lost INTERNET connection

Sounds good to me ...... :smile:[/I]
                                 
But I'm sure there are a zillion little steps in between! Like  will it be necessary to edit the sources list and replace natty with  oneiric???

> BTW, congrats on 2K beans!Cheers for the nice remark ......

and to Charles A .... derailing a thread ..... we would quite happily move to a new thread if it was not relevant.

Updates and Uograding were the subject ..... 

[http://ubuntuforums.org/showthread.php?t=1856403](http://ubuntuforums.org/showthread.php?t=1856403)

 there was absolutely no need to close it ..... everything will be closed tonight anyway,

This Oneiric Testing Area may get closed tonight ........ so will have to create a Fresh Thread .....
[URL="http://ubuntuforums.org/showthread.php?p=11334068#post11334068"][COLOR=Red][B]
LINK TO PROBLEMS WITH UPGRADES[/B][/COLOR][/URL] - add what are relevant here 		                   		  		  		 		 			 				__________________

---

### Post by seeker5528 on 2011-10-12
> [I]All sounds good in theory .... 

Easy is good ...... for the majority ...... me included .....

What you propose there is

1 ..... download the latest ISO

2 ..... mount it so it can be used to upgrade from

3 ..... upgrade from CD without a chance of losing it through a lost INTERNET connection

Sounds good to me ...... :smile:[/I]
                                 
But I'm sure there are a zillion little steps in between! Like  will it be necessary to edit the sources list and replace natty with  oneiric???


The CD has an upgrade option, which will try to keep some amount of currently installed packages installed. What the end results are may vary depending on what additional packages are installed and if you are connected to the internet.

The CD doesn't have packages on it so mounting it and attempting to use it to upgrade won't work.

The DVD does have packages on it, but looks like they are not (at least currently) putting all of main on there like the did in previous releases. 

These are the file lists for the natty and oneric DVDs for comparison....

[http://cdimage.ubuntu.com/releases/natty/release/ubuntu-11.04-dvd-i386.list](http://cdimage.ubuntu.com/releases/natty/release/ubuntu-11.04-dvd-i386.list)

[http://cdimage.ubuntu.com/releases/oneiric/beta-2/ubuntu-11.10-beta2-dvd-i386.list](http://cdimage.ubuntu.com/releases/oneiric/beta-2/ubuntu-11.10-beta2-dvd-i386.list)

The alternate CD has packages on it, so it may be possible to use that by mounting/loop mounting, but if you have installed extra stuff, you would probably have to get rid of some of it when upgrading to resolve conflicts.

Here are a couple of links on how to get/create DVDs of the repositories, which in theory could be used to upgrade.

[http://blog.mypapit.net/2006/08/get-ubuntu-repositories-on-dvd.html](http://blog.mypapit.net/2006/08/get-ubuntu-repositories-on-dvd.html)

[http://www.howtoforge.com/dvd_images_of_ubuntu_repositories](http://www.howtoforge.com/dvd_images_of_ubuntu_repositories)

Don't know how that would work out for loop mounting as opposed to actually having a DVD drive.

If you have a large enough flash drive, you could mirror the repositories there, which might work out better.

EDIT: Looks like you could use debmirror to get the files you want, but there may be better ways to limit the number of files you have to download. There is a dpkg-scanpackages command that can be used to index a directory of downloaded .debs, so you can use apt-get to install them.

[https://help.ubuntu.com/community/Debmirror](https://help.ubuntu.com/community/Debmirror)
[http://www.debian.org/doc/manuals/apt-howto/ch-basico.en.html#s-dpkg-scanpackages](http://www.debian.org/doc/manuals/apt-howto/ch-basico.en.html#s-dpkg-scanpackages)

Might take some trial and error to sort it out exactly.

Later, Seeker

---

### Post by effenberg0x0 on 2011-10-12
Good info.

I guess we can all agree that, considering CD/DVD burning (and read) low speed, and the fact that almost everyone has a chip gift USB stick somewhere, many users will follow the Download ISO / Create Live USB instructions on Ubuntu.com download page. The instruction on how to do that are well documented, with screenshots, etc.
[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

Regards,
Effenberg

---

### Post by 23dornot23d on 2011-10-12
Great information ...... will have a look through it all tonight ..... but what effenberg0x0

proposes may be the better solution ...... we were just throwing around some ideas

to make it less of a problem for slow internet users ..... the USB stick is the best way 

I think.

---

### Post by seeker5528 on 2011-10-12
Some thoughts about signs warning of 'slow children' come to my mind, but.... biting my tongue. :p

Later, Seeker

---

### Post by 23dornot23d on 2011-10-12
Yep I should have written slow internet connections ..... like dial-up ...... :D

slow users is another thing .... like me the older I get  .... :rolleyes:

---

### Post by 3rdalbum on 2011-10-13
Er...

You can do a dist-upgrade from the Alternate CD. Mount the CD or the ISO and run the "cdrom-upgrade" script in the top directory of the CD/ISO.

This will run an upgrade of the base system using the packages on the Alternate CD. Your existing non-standard programs will be upgraded from the Internet, unless you are not connected (in which case they will still be preserved in their original state).

Note: This doesn't work with the Desktop CD because it doesn't contain packages, per-se.

---

### Post by vasa1 on 2011-10-13
23dornot23d,
Thanks for starting this thread.
[CENTER]+++++++++++[/CENTER]
Difficulties for some may not be for others.
> Some thoughts about signs warning of 'slow children' come to my mind, but.... biting my tongue.

So what does that mean?

Is it that people who want to learn how to use Ubuntu and how to update/upgrade successfully should be especially qualified?

Is that how lay people are treated? I don't understand and feel quite hurt.

---

### Post by 23dornot23d on 2011-10-13
I have never tried to do a upgrade just using a CD or DVD

But taking the fact that it can fail when all the files are available over the net

The chances of a upgrade succeeding when either CD or DVD alone is used seems
to me from what I have read above to leave the system lacking .....

Alternate CD ..... although this will work as explained above it will  leave some packages at the older versions .... no good if they are  Gnome2 and we have moved to Gnome 3
something is going to fail.

DVD ..... although this has a lot of packages on it ...... its been  reduced from previous versions and as Seeker says the main does not seem  to be complete.

> The DVD does have packages on it, but looks like they are not (at least  currently) putting all of main on there like the did in previous  releases. So again this does not seem as if it should work ....... but may be worth trying out ,,,,,
a slow connection and downloading a DVD may be ok as it can be re-started if the 
connection is lost.

Any other method that needs to install while connected to the NET ...... is still 
going to render the install corrupt if the Network is lost while setting up the system

Therefore ...... a slow or interupted network connection that some people may 
experience ........ possible problems can best be avoided by downloading the DVD version and using that
to install/upgrade from ......... but its not known that this will work without testing it first,

So once the DVD is available ..... [**out now**]("http://ubuntuforums.org/showthread.php?t=1858902") .....

[http://cdimage.ubuntu.com/releases/11.10/release/](http://cdimage.ubuntu.com/releases/11.10/release/)

already got 386 CD
Now the 64 Bit DVD


I will download it and try to upgrade one of my systems from it - disconnecting the internet connection for the try out  .......

I will now download the Alternate CD and try the to do the same with that .......

Well I enjoy trying things out ........ and no doubt with UBUNTU ..... UNITY ...... 

The two words mean so much ...... 

Ubuntu: "I am what I am because of who we all are." 

Unity:  "oneness of mind, feeling, etc., as among a number of persons; concord, harmony, or agreement. "

The one word that it also needs is one that defines a true way forward breaking down
any class and education barriers that we may have ........

That way we truly do become one force to be reconed with ........ and all strive to obtain
a better system ...... wether it be a computer system or a communal one .......... ;)

---

