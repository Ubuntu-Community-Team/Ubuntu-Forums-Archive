---
title: "Dual boot Hardy/Hardy?"
date: 2008-10-17
forum: New to Ubuntu
---

### Post by ranch hand on 2008-10-17
Here's the deal.  I have now, in 3 days, done 2 clean reinstalls of Hardy.

Why?, you may ask.  Because I am having way too much fun.

The problem is I do need tho use the computer and one of these days I would like to store some files I want to, or need to keep.

I am new to Ubuntu, new to Linux, basically new to a computer you can have some control over.  I love it.

I break it and do not have the knowledge to fix it.

Can I dual boot Hardy with Hardy?

I have known me for 56 years and know I will continue to push buttons to find out what they do.  Kind of like sticking your finger in the light socket and turning on the switch to see what happens and then being suprised when it does.

This is a Dell xps 420, 320Gb HDD, 3 Gb ram, quad core 240GHz.  I may have enough resources to dual boot.

I would just like some way that I can USE Ubuntu and at the same time bust the heck out of it.

---

### Post by OutOfReach on 2008-10-17
Sure! I don't see a problem with dualbooting Hardy with Hardy.

P.S. Welcome to Ubuntu :)

---

### Post by Bakon Jarser on 2008-10-17
You may also want to look into remastersys.

[http://www.remastersys.klikit-linux.com/](http://www.remastersys.klikit-linux.com/)

---

### Post by bumanie on 2008-10-17
You can dual boot hardy and hardy, but why not setup with a separate /home partition in the first place? If you destroy the / filesystem, you will only have to reinstall to / and all your data in /home is safe. You can do this at the partitioning stage of the installation process or [follow this]("http://www.psychocats.net/ubuntu/separatehome") to get a separate /home on an existing installation.

---

### Post by ranch hand on 2008-10-17
bumanie; This does look like a good idea even if I decide to dual boot.  I do have plenty of room and this would make life on the box safer.

There is a problem though.  I am on dial up so I ordered a live DVD and installed.  When I try to run off the DVD I have never been able to configure the modem, and I just gave it a try to see about this process, gparted comes up but all but about 2 entries in the menu are greyed out.

Am I right if assuming that I need to make my own live DVD and that will connect me and allow me to use gparted?  I also did install gparted.

---

### Post by LowSky on 2008-10-17
Gparted is availible from the Regular Ubuntu LiveCD (just called Paritition Editor under System> Admin)

---

### Post by ranch hand on 2008-10-17
Yes it is there.  It will not work.  It comes up but you can't do anything except look at it.

---

### Post by celticbhoy on 2008-10-17
As you are playing about with things, why not set up your hardy, and then use VirtualBox to play with Virtual PC's containing another Hardy, and any other kind of distro you might want to look at. That way your original install stays safe ?

---

### Post by Orange_and_Green on 2008-10-17
Hello :)

Are you by chance trying to resize mounted partitions? You need to unmount them before you can do that from gparted (so if you want to resize your root partition, you'll have to do that from a live).

BTW, care to check out the link in my signature? If you like to reinstall a lot, I wonder if you might find it useful... :)

Glad there are other people in the world who love playing around with Ubuntu just as much as I do :KS:)
Have a nice day,
Orange and Green

---

### Post by ranch hand on 2008-10-17
> **celticbhoy said:**
> As you are playing about with things, why not set up your hardy, and then use VirtualBox to play with Virtual PC's containing another Hardy, and any other kind of distro you might want to look at. That way your original install stays safe ?

This is another good idea.  I will have to look into it, it is one of the many things I have heard of but know nothing more about.

---

### Post by ranch hand on 2008-10-17
> **Orange_and_Green said:**
> Hello :)

Are you by chance trying to resize mounted partitions? You need to unmount them before you can do that from gparted (so if you want to resize your root partition, you'll have to do that from a live).

I am aware of this, it will not work from my DVD.  I think I need to make one, not sure how to do this but the info is out there I am sure.

Thanks for the link.  This sounds real good too.  Where is this stored so that it isn't wiped?

---

### Post by Orange_and_Green on 2008-10-18
Thank you for your interest in my program.

Just download it and extract it to any place on your hard disk, then run the binary called "aptautosave". From that moment on, it will run automatically every time you log in, and manage a history of system restores in a directory called "aptautosave" in your home.
Documentation and source files are included in the package :)

Yes, you are right, there is much information on the net about making bootable live CDs. There is a fantastic article on these forums too:

[http://ubuntuforums.org/showthread.php?t=688872](http://ubuntuforums.org/showthread.php?t=688872)

Enjoy enjoy enjoy:KS

---

### Post by ranch hand on 2008-10-27
Well, busy week.

Shipped our calves, helped ship calves for two neighbors.  Studied this thread.

Here is what I did.

I decided to dual boot.  Had trouble with the live CD getting gparted to work.  That was, for me, a tough problem.  Turns out that it helps if the CD is clean.  Surprising what you can do with a soft cloth.

I know have Ubuntu on another partition, about 50 gig.  I can screw with that as much as I want.

Now I have a new problem.  I want to try Ubuntu Studio.

I resized my main partition down to 138 gig.  Installed Hardy on another 50.  This leaves the other partition I made at about 70 gig.

Is there some reason that I can't triple boot?

Thanks

---

