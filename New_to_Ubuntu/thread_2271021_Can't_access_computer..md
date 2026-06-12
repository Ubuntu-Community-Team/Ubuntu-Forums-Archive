---
title: "Can't access computer."
date: 2015-03-27
forum: New to Ubuntu
---

### Post by Sonofhellrazorliv on 2015-03-27
I bought 2 gaming computers running ubuntu 14.04 from an auction and  they seem to be password protected. I have no clue how to bypass this as  i didn't receive any login info for them. I've never used ubuntu and it  is very intimidating.

My biggest problem is that when i go to advanced options and then select  recovery mode nothing happens. text scrolls and then nothing, just a  black screen. Any ideas?

---

### Post by mastablasta on 2015-03-27
well you can reinstall the OS (if you plan on using windows install windows instead). 

or you can reset the password: [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

you could try to enter console with text mode. [http://ubuntuhandbook.org/index.php/2014/01/boot-into-text-console-ubuntu-linux-14-04/](http://ubuntuhandbook.org/index.php/2014/01/boot-into-text-console-ubuntu-linux-14-04/)

do you have any hardware specs known?

---

### Post by Sonofhellrazorliv on 2015-03-27
Not sure what motherboard, looks to be an Asus. P4 processor (3 ghz I believe), 2gb RAM ddr3 at least. And a Radion x800 pro graphics card.

The other one I haven't started up but it has 4gb or RAM and a geforce 8800 pro. Looks like two hard drives but the paperwork only listed one.

---

### Post by Bucky Ball on 2015-03-27
You may need something lighter weight for the P4, perhaps Xubuntu or Lubuntu, but you could try Ubuntu on the 4Gb machine. Depends on the processor. 

To find details, I suggest you download some ISOs, burn install media (USB or disk), boot from that and 'Try *buntu'. This will get you to a desktop. Once there, open a terminal and write or paste this:

```
lspci
```

... then hit return. Post the result back here between [code] tags (see the last link in my signature for how). 

Get [Xubuntu]("http://xubuntu.org/getxubuntu/") (lighter).
Get [Ubuntu]("http://www.ubuntu.com/download/desktop"). 

Xubuntu 14.04 LTS has three years support, Ubuntu five.

---

### Post by kerry_s on 2015-03-27
i think you need to wipe them, which should have been done before they went to auction.
this is very bad for the previous owner of those computers. i hope your a good person.

---

### Post by yancek on 2015-03-27
It could also be bad for the OP as the person who sold the computers may have left some back door or malware on them.  I think either scenarios is unlikely but also feel you would be better off with a new install as they could be cluttered up with all kinds of software and/or perso al data.

---

### Post by Sonofhellrazorliv on 2015-03-27
The previous owner was the videogame company 38studios. 
Is there an easy way to wipe the drives? Because I can't even get recovery mode to run..

---

### Post by Sonofhellrazorliv on 2015-03-27
I like to think of myself as a good person. If I were to access the drives and they really didn't wipe them they could have some leftover pieces of the unfinished kingdoms of amular MMO, not too sure if I'd be able to keep myself from that, haha.

---

### Post by Sonofhellrazorliv on 2015-03-27
I forgot to mention. The password reset link you gave me was actually the exact process I was trying to do all last night but like i said, everytime I select recovery mode it either just goes to a black screen or back to a login screen

---

### Post by Bucky Ball on 2015-03-27
> **Sonofhellrazorliv said:**
> 
Is there an easy way to wipe the drives? 

Yes. [See post #4]("http://ubuntuforums.org/showthread.php?t=2271021&p=13253521&viewfull=1#post13253521"). Create a Ubuntu installer (USB or disk)>boot from it>select 'Try *buntu' when you get to the options screen>once at a desktop launch Gparted>right click and delete each partition until there is nothing but unallocated space on the drive. Done. ;)

---

### Post by The Cog on 2015-03-27
You might be able to get a visible console in recovery mode if you choose nomodeset in the bootloader advanced options, but I am inclined to agree with the others that you are better off just installing from scratch. It's nothing like as hard as installing windows.

---

### Post by Sonofhellrazorliv on 2015-03-27
Really? I've never had any trouble installing windows. This is my first time even looking at a Linux OS. To me this computer is like something out of those 80's Hacker movies

---

### Post by Sonofhellrazorliv on 2015-03-27
So i have a windows 8 disc in the dvd drive, but i cant get it to do anything with it.

---

### Post by Vladlenin5000 on 2015-03-27
> **Sonofhellrazorliv said:**
> So i have a windows 8 disc in the dvd drive, but i cant get it to do anything with it.

What do you want to do with it? If it's to install then you must boot from that installation media. How you select it to boot from the DVD has nothing to do with either the installed OS or the one you intend to install, it's BIOS setup.

---

