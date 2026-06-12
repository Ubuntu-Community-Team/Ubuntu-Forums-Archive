---
title: "Mandriva One (2007)"
date: 2007-04-15
forum: Other OS Talk
---

### Post by Platinum J on 2007-04-15
I just tried it. I thought it was quite good. Seemed to recognize everything more or less. I was wondering what was  other user's experiences. 

thanks, 

The Platinum One

---

### Post by rufius on 2007-04-16
I actually kind of bounce back and forth between Mandriva and Ubuntu. The first Linux distribution I ever used was Mandrake, I forget what version, but I have fond memories with it. My problem with Mandriva is one release will be absolutely stunning, works great, and everything. Then the next release will be absolute rubbish and barely work. I think they did a good job with 2007 though, though not quite as well as Ubuntu has done with 7.04.

---

### Post by Platinum J on 2007-04-16
WOW! I really hope Feisty is all that I dream it will be because Mandriva was pretty nice. Although, I did run into some wireless issues.

The Platinum One

---

### Post by igknighted on 2007-04-16
Mandirva hates my mobo which all other distro's use no problem... any kind of networking fails (even though it sees my LAN cards) and the sound isn't recognized.  So, when other distro's have no issues, Mandriva just isn't worth the effort.  Hopefully it will be fixed by 2007.1 (which should be out any day, yes?).

---

### Post by tommcd on 2007-04-16
> **Platinum J said:**
> I just tried it. I thought it was quite good. Seemed to recognize everything more or less. I was wondering what was  other user's experiences. 

thanks, 

The Platinum One

Did you install it? And did the install go ok? I tried an older version of mandriva one and although it booted up fine from the live session, it hung during the install and would not go further. After looking around the mandriva forums I found this was pretty common at the time.

---

### Post by igknighted on 2007-04-16
> **tommcd said:**
> Did you install it? And did the install go ok? I tried an older version of mandriva one and although it booted up fine from the live session, it hung during the install and would not go further. After looking around the mandriva forums I found this was pretty common at the time.

Yeah, I had it do this too.  Then I reinstalled Ubuntu's grub and it added Mandriva automatically, and it booted fine... go figure.  There was something really screwy going on there.

EDIT: Sorry, mine hung during boot.  Then reinstalling Ubuntu's grub fixed it.  Weird.

---

### Post by 3rdalbum on 2007-04-16
Mandriva One 2006 worked fine on my hardware. The 2007 version was *extremely* slow on my computer; probablly something to do with Metisse.

I tried Metisse as standalone on Ubuntu, and although it's interesting I don't see the features as being very useful.

---

### Post by jctweb on 2007-09-23
I'm resurrecting this thread to avoid a new one :)

I've got a coupon from Mandriva to get the powerpack download edition for about $30.  Is it worth it?

I've been using Kubuntu Feisty for about a week and I'm getting frustrated with it - 100% of my problems are wireless and video card related and the Mandriva live CD didn't have any issues when I tried it out.

Most distros are basically the same yet I, too, have fond memories of using Mandrake in the past - it just 'worked' for me.

Any thoughts?  Should I give feisty another week or spend the $30 and go from there?

Thanks

---

### Post by igknighted on 2007-09-24
> **jctweb said:**
> I'm resurrecting this thread to avoid a new one :)

I've got a coupon from Mandriva to get the powerpack download edition for about $30.  Is it worth it?

I've been using Kubuntu Feisty for about a week and I'm getting frustrated with it - 100% of my problems are wireless and video card related and the Mandriva live CD didn't have any issues when I tried it out.

Most distros are basically the same yet I, too, have fond memories of using Mandrake in the past - it just 'worked' for me.

Any thoughts?  Should I give feisty another week or spend the $30 and go from there?

Thanks

There really isn't much in the power pack that isn't in the free version (just a couple proprietary apps, and also I think a Cedega license).  So if you think the extra stuff is worth the $30 go for it (Cedega is $15 by itself).

As for trying Mandriva, I would strongly recommend trying it whether you use the free version or buy the power-pack, its a fabulous distro.

---

### Post by Shazaam on 2007-09-24
I initially liked it until I tried to update it. The version I used was the livecd version of Spring 2007. A million "unsatisfied make" errors later (would NOT let me update the kernel or other critical files) I have given up. According to the Mandriva forums the version I downloaded was seriously flawed. Its a nice OS, recognised all of my hardware (except a Conexant Winmodem), but the dependancy problem is a mess. And yes, I have all of the recommended mirrors enabled and I have checked the md5 on the disk (burned at 2x).
I hope they do better with 2008.

---

### Post by igknighted on 2007-09-24
> **Shazaam said:**
> I initially liked it until I tried to update it. The version I used was the livecd version of Spring 2007. A million "unsatisfied make" errors later (would NOT let me update the kernel or other critical files) I have given up. According to the Mandriva forums the version I downloaded was seriously flawed. Its a nice OS, recognised all of my hardware (except a Conexant Winmodem), but the dependancy problem is a mess. And yes, I have all of the recommended mirrors enabled and I have checked the md5 on the disk (burned at 2x).
I hope they do better with 2008.

The issue is, when Mandriva comes on the "one" live CD, it comes with kernel modules built for the kernel provided.  But if you just upgrade that, it will upgrade the kernel.  It won't remove the old modules, and it will try to use DKMS to install new ones.  But somewhere in the switching from pre-built modules to DKMS, urpmi is getting confused.  The easy answer is to (a) never update your kernel, or (b) install a version with no pre-built modules (no non-free stuff), and then install and upgrade the kernel before you do install them.  Mandriva 2008 should be out this week, hopefully this issue will be fixed by then.

EDIT: Yes, this is a rather serious design flaw.  I am really surprised that they let this one slip through and didn't even release an update to fix it.  That said, hopefully in 2008 this won't be an issue.

---

### Post by jctweb on 2007-09-24
I'm going to give the liveCD a shot this weekend and see what happens.  I know how to get Kubuntu to work, so I can recover pretty quickly if I don't like it.  I have to wait until the weekend because I've got work to do :)

---

### Post by igknighted on 2007-09-24
> **jctweb said:**
> I'm going to give the liveCD a shot this weekend and see what happens.  I know how to get Kubuntu to work, so I can recover pretty quickly if I don't like it.  I have to wait until the weekend because I've got work to do :)

The 2008 version should be out by this weekend... I would recommend you try that one instead

[QUOTE=www.distrowatch.com]2007-09-27: Mandriva Linux 2008 (see release schedule) [/QUOTE]

---

### Post by AdamWill on 2007-09-27
it won't be out this weekend. most likely next week.

---

### Post by igknighted on 2007-09-27
> **AdamWill said:**
> it won't be out this weekend. most likely next week.

:( I'm really excited about 2008... I think Mandriva is gonna wow us with this one.

---

### Post by jctweb on 2007-09-27
We'll see what happens.  I'm looking forward to some of the eye candy.  I'm currently messing with the Beta 1 release of Gutsy - I must say Mandriva is taking second place ;)

---

