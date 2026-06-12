---
title: "[SOLVED] Question About Clean Install"
date: 2008-10-04
forum: New to Ubuntu
---

### Post by nkri on 2008-10-04
Hey everyone...

I'm thinking about doing a clean install when the official release of Intrepid comes out, but am not exactly sure how to do it on a dual boot machine and don't know what it could do to the machine.

When you run the LiveCD, which option would you select at the partitioning stage (guided, manual, etc.)?

Would it seriously change anything (such as Windows or the hard drive itself)?

Since I don't have a /home partition, could I make a copy of my home folder before installation in order to replace it after installation?  If I do this, would all of my settings stay the same?

Also, which do you think is safer on a dual boot machine: upgrade from within Ubuntu, or clean install?

Thanks!
-nkri

---

### Post by linuxisfree on 2008-10-04
> **nkri said:**
> Hey everyone...

I'm thinking about doing a clean install when the official release of Intrepid comes out, but am not exactly sure how to do it on a dual boot machine and don't know what it could do to the machine.

When you run the LiveCD, which option would you select at the partitioning stage (guided, manual, etc.)?

Would it seriously change anything (such as Windows or the hard drive itself)?

Since I don't have a /home partition, could I make a copy of my home folder before installation in order to replace it after installation?  If I do this, would all of my settings stay the same?

Also, which do you think is safer on a dual boot machine: upgrade from within Ubuntu, or clean install?

Thanks!
-nkri

Normally, for a clean install, i use manual... i see my drives from there and just select what partition to install the OS at.

Not sure if it'll change anything, though (as i'm a single OS guy - don't dual boot). It would also probably be safer to upgrade from Ubuntu, as opposed to a clean install (for a dual boot machine, anyway.) Sure hope that'll help.

---

### Post by iansane on 2008-10-04
If your certain you know what partition to use for ubuntu you can choose that one under guided. Manual is unnecesary unless your making seperate partition for home directory which will solve the home directory issue next time.

It will do everything automatically and grub will detect windows on the other partition giving you the menu to choose which os to boot.

You can definately save files by copying the home directory but I'm not sure if there are settings in there for applications that won't be present in the fresh install and might cause problems

yeah like linuxisfree said, just do an upgrade It would be safer.

---

### Post by nkri on 2008-10-04
> **linuxisfree said:**
> Normally, for a clean install, i use manual... i see my drives from there and just select what partition to install the OS at.

So it writes over only the partition you specify if you use manual?

---

### Post by Sef on 2008-10-04
> . It would also probably be safer to upgrade from Ubuntu, as opposed to a clean install (for a dual boot machine, anyway.)

Actually it is safer to do a clean install.

> 
When you run the LiveCD, which option would you select at the partitioning stage (guided, manual, etc.)?

Select manual.

>  Would it seriously change anything (such as Windows or the hard drive itself)?

Not if all went well.

> Since I don't have a /home partition, could I make a copy of my home folder before installation in order to replace it after installation? If I do this, would all of my settings stay the same?
a)** Back up** your data before upgrading or doing a clean install.  

b) If you did a clean install, you would lose all of your settings.

---

### Post by Sef on 2008-10-04
> So it writes over only the partition you specify if you use manual?

Yes it does.  It will also reformat your swap automatically.

A short version of what to do:  You will delete that partition, then reformat it.

---

### Post by statikeffeck on 2008-10-04
> **nkri said:**
> Hey everyone...

I'm thinking about doing a clean install when the official release of Intrepid comes out, but am not exactly sure how to do it on a dual boot machine and don't know what it could do to the machine.

When you run the LiveCD, which option would you select at the partitioning stage (guided, manual, etc.)?

Would it seriously change anything (such as Windows or the hard drive itself)?

Since I don't have a /home partition, could I make a copy of my home folder before installation in order to replace it after installation?  If I do this, would all of my settings stay the same?

Also, which do you think is safer on a dual boot machine: upgrade from within Ubuntu, or clean install?

Thanks!
-nkri

If you do a network upgrade, you won't lose any documents or settings, but you might have some hardware & driver troubles. However, if you do a fresh install from the new version CD, you risk losing things from /home directory. 
I was just discussing this with some other members at:
[http://ubuntuforums.org/showpost.php?p=5842286](http://ubuntuforums.org/showpost.php?p=5842286)

As others have said, you should back up your /home/yourname directory to DVD or USB disk before trying anything; that way you can always just copy it back.

---

### Post by nkri on 2008-10-04
> **Sef said:**
> A short version of what to do:  You will delete that partition, then reformat it.

But it won't change my partition table at all, right?  And GRUB should still show Ubuntu and Windows side-by-side every time I boot?  If both of these are true, I'm definitely gonna do a clean install:D

---

### Post by Sef on 2008-10-04
> But it won't change my partition table at all, right? And GRUB should still show Ubuntu and Windows side-by-side every time I boot? If both of these are true, I'm definitely gonna do a clean install

If you do it right and all goes well, then your partition table will be the same, and GRUB will boot both Ubuntu and Windows.  Use the Live CD for a while to make sure that there are not any glitches with your hardware.  If there are not, then more than likely the install will be fine.  You will lose all your settings though.

---

### Post by Paqman on 2008-10-04
> **nkri said:**
> 
Since I don't have a /home partition, could I make a copy of my home folder before installation in order to replace it after installation?  If I do this, would all of my settings stay the same?


Yes.

One thing to watch out for is file ownership. If the file ownership and permissions of each users /home folder aren't right, they won't be able to log in.

Besides their name, each user account has an ID number. By default, these numbers are issued sequentially when new users are created. When you set up the fresh system, make sure you set them up in the same order as you originally did (or else manually set their user number to be the same as the old system)

Alternatively, after you copy in the /home holder, execute a chown command to ensure they have ownership of all the files.

---

### Post by nkri on 2008-10-04
> **Paqman said:**
> Yes.

One thing to watch out for is file ownership. If the file ownership and permissions of each users /home folder aren't right, they won't be able to log in.

Besides their name, each user account has an ID number. By default, these numbers are issued sequentially when new users are created. When you set up the fresh system, make sure you set them up in the same order as you originally did (or else manually set their user number to be the same as the old system)

Alternatively, after you copy in the /home holder, execute a chown command to ensure they have ownership of all the files.

OK, so I've decided to put the windows hard disk recovery partition (5GB) on DVDs and then use the partition as /home to make the upgrade process easier:)  In so doing, I wouldn't have to worry about the permissions issue Paqman brought up, right?

And on a side-note: does anyone who is testing the Intrepid beta happen to use a Tablet PC with a Wacom digitizer?  If so, does it even work?

Thanks!
-nkri

---

### Post by Paqman on 2008-10-05
> **nkri said:**
> In so doing, I wouldn't have to worry about the permissions issue Paqman brought up, right?


You shouldn't, because Intrepid's installer should detect the user's home folders and set up the users on the fresh install to match. You would only have to enforce the ownership yourself if that went wonky.

If you only have one user on the machine it'll never be an issue, btw.

---

### Post by nkri on 2008-10-05
> **Paqman said:**
> You shouldn't, because Intrepid's installer should detect the user's home folders and set up the users on the fresh install to match. You would only have to enforce the ownership yourself if that went wonky.

If you only have one user on the machine it'll never be an issue, btw.

Ah, ok, thanks for clearing that up...and yep, I only have one user:)

Oh, and *one* last question: a clean install will keep GRUB intact, i.e., it will still show Ubuntu and Windows side-by-side every time I boot, correct?

Thanks!
-nkri

---

### Post by Paqman on 2008-10-05
> **nkri said:**
> 
Oh, and *one* last question: a clean install will keep GRUB intact, i.e., it will still show Ubuntu and Windows side-by-side every time I boot, correct?


It will actually *reinstall* GRUB, but yes, it will spot Windows and add it to the list.

---

### Post by nkri on 2008-10-05
> **Paqman said:**
> It will actually *reinstall* GRUB, but yes, it will spot Windows and add it to the list.

Well, I guess that'll do it!  Thanks for helping me on all of this, man, it made it a lot less scary;-)
-nkri

---

### Post by Idefix82 on 2008-10-05
One more thing: when you use an existing partition as /home and there is already data there, don't forget to uncheck the "format" option for this partition when doing a clean install, otherwise all the data will be lost.

---

### Post by nkri on 2008-10-05
> **Idefix82 said:**
> One more thing: when you use an existing partition as /home and there is already data there, don't forget to uncheck the "format" option for this partition when doing a clean install, otherwise all the data will be lost.

Good point...but I should keep it checked for my / and swap, right?

Thanks!
-nkri

---

### Post by Idefix82 on 2008-10-05
Yes. In fact SWAP will be formatted anyway.
You may also want to have a look at this post of mine with a couple of thoughts on why to create more than just one or two partitions for Linux:
[http://ubuntuforums.org/showthread.php?p=5852443#post5852443]("http://ubuntuforums.org/showthread.php?p=5852443#post5852443")

---

### Post by nkri on 2008-10-06
> **Idefix82 said:**
> Yes. In fact SWAP will be formatted anyway.
You may also want to have a look at this post of mine with a couple of thoughts on why to create more than just one or two partitions for Linux:
[http://ubuntuforums.org/showthread.php?p=5852443#post5852443]("http://ubuntuforums.org/showthread.php?p=5852443#post5852443")

Sounds good, but how necessary do you think it is to have /boot?  I always keep at least two extra kernels on which to fall back, and if I really screw something up in /, would a /boot partition really make a difference if I have to reinstall?  I guess I'm not too worried about it since I plan on doing clean installs every six months if this one goes well and don't really want partitioning trouble right now.  Still, any input and reasoning is much appreciated:)

Thanks!
-nkri

---

