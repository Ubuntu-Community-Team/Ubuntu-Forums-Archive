---
title: "Okay, got a new hard drive"
date: 2008-08-27
forum: New to Ubuntu
---

### Post by anotherconfused1 on 2008-08-27
Ok, Got a new Hard Drive, I copied the old hard drive to the new hard drive, the new hard drive is meant for XP only, and the old Hard drive for Ubuntu. How would I do this? If possible, can I do it in XP, so I don't have to burn another Live CD. 
edit: fixed grammar errors and whatnot.

---

### Post by louieb on 2008-08-27
Not a big fan of wubi but thats one way to install inside of xp. 
Dual booting with two hard drives is pretty easy - easier that dual booting with 1 hard drive. Heres the classic how to :  [Dualboot Two Hard Drives - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=179902") 

Although  you can install without burning a CD IMHO thats by far the easiest way.

Take a look [HOWTO Boot from any .iso file without needing a working CD-ROM]("http://ubuntuforums.org/showthread.php?t=666267")

---

### Post by markbuntu on 2008-08-27
Put in the first hard drive and load XP on it. Then plug in the other drive as the master and make the xp drive the slave and load ubuntu onto the master drive. 

If you have SATA drives it is even easier. Plug the Xp drive into plug 2 and load xp then plug the Ubuntu drive into plug 1 and load Ubuntu.

Either way XP will never know Ubuntu or the drive is there and ubuntu wont mess with the xp drive at all.

---

### Post by caljohnsmith on 2008-08-28
> **anotherconfused1 said:**
> Ok, Got a new Hard Drive, I copied the old hard drive to the new hard drive, the new hard drive is meant for XP only, and the old Hard drive for Ubuntu. How would I do this? If possible, can I do it in XP, so I don't have to burn another Live CD. 
edit: fixed grammar errors and whatnot.
So you want the new HDD Win to be XP only, and the old HDD to have Ubuntu, correct? Wubi will allow you to install Ubuntu within Windows, but I don't think that is what you want, right? Because if so, I think you need to have a Live CD so you can install Ubuntu to your old HDD. Or if you want to jump through alot of hoops, I think there are ways you can download the Ubuntu ISO in Windows, and then create a virtual environment where you can boot that Ubuntu ISO; but you'll need VirtualBox or similar. So why not just spend the 25 cents and burn a Live CD? :)

---

### Post by egalvan on 2008-08-28
I'm having a hard time following the line of thought here.


> **anotherconfused1 said:**
> Ok, Got a new Hard Drive, I copied the old hard drive to the new hard drive, the new hard drive is meant for XP only,

Have you successfully moved XP to the new drive?
In other words, is XP now booting OK?

 > and the old Hard drive for Ubuntu.

Have you loaded Ubuntu on the second drive?
Is Ubuntu booting OK as a first drive or second drive?


 > How would I do this? If possible, can I do it in XP, 

Do what? What have you done already?


[QOUTE]so I don't have to burn another Live CD. 
edit: fixed grammar errors and whatnot.[/QUOTE]


What LiveCD do you have now?


Do you want to keep Ubuntu & XP from seeing each other? 
If so, why?
Unless you explicitly load special drivers, XP will never see the Ubuntu drives.
And under Linux, it's possible to tell it to ignore (not mount) specific drives.

A little more info can better help us help you.

ErnestG

:popcorn:

---

### Post by anotherconfused1 on 2008-08-28
> **egalvan said:**
> I'm having a hard time following the line of thought here.




Have you successfully moved XP to the new drive?
In other words, is XP now booting OK?

 

Have you loaded Ubuntu on the second drive?
Is Ubuntu booting OK as a first drive or second drive?


  

Do what? What have you done already?


[QOUTE]so I don't have to burn another Live CD. 
edit: fixed grammar errors and whatnot.


What LiveCD do you have now?


Do you want to keep Ubuntu & XP from seeing each other? 
If so, why?
Unless you explicitly load special drivers, XP will never see the Ubuntu drives.
And under Linux, it's possible to tell it to ignore (not mount) specific drives.

A little more info can better help us help you.

ErnestG

:popcorn:[/QUOTE]

1. Yes XP boots okay.
2. No, I can't get Ubuntu to install on the second HDD
3. I have misplaced my Live CD, and am currently out of blank CD-RW's. All my others have backups on them.
4. No, XP and Ubuntu can see each other, I prefer they do.
Is that better?

---

### Post by egalvan on 2008-08-29
> **anotherconfused1 said:**
> 

1. Yes xp boots okay.
2. No, i can't get ubuntu to install on the second hdd
3. I have misplaced my live cd, and am currently out of blank cd-rw's. All my others have backups on them.
4. No, xp and ubuntu can see each other, i prefer they do.
Is that better?

Yes, thanks, don't mean to sound mean, but sometimes information gets lost in the written word. You know what you mean, but it doesn't always come through..

Point 3, CD-RW are not required, one can use CD-R, these are much cheaper. (I bought 200 blanks at Staples last month for $30, and they had a "free" 256m thumb drive in each package)

But maybe buying them right now is not an option.

It IS possible to do a "network" install, but unless you have a reasonably fast Internet (at least DSL-type) it will take a long while.

This involves downloading a small (floppy-sized) "boot-image" that sets up your computer and network. The boot image then starts pulling all the software it needs off the Internet (more specifically, whatever network you set up).

Practically, it will be a smaller download than a full install ISO, since the boot installer only downloads what you decide to install, but it will still be a long process.


But try this page, and see if any of the options sounds OK to you. 

**[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)**


There are installs from Windows, and there is also the Wubi option.
Wubi is an installer which "installs" Ubuntu inside windows.
You can then 'move' the install to it's own partition, just like a 'real' install.

In sum, most of these options are a lot of work, and/or time-consuming. A few can hose your Windows if you make a mistake. Be prepared. Read all the options, and when you decide on the route to take, **read the instructions completely before actually starting.** This can save you much grief.

---

