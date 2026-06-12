---
title: "[SOLVED] Sensible to fall back to Gutsy?"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by Nebelhom on 2008-05-06
Hi all,

I recently installed hardy heron on my PC in a dual boot. I'm a complete and utter newbie and straight away ran into some issues with my graphics card drivers that up to now after one week of constant trying I haven't resolved. (I basically always had to start in vesa mode without drivers or failsafe mode with installed drivers)
(if interested see thread: [http://ubuntuforums.org/showthread.php?p=4885303#post4885303](http://ubuntuforums.org/showthread.php?p=4885303#post4885303) )

Although I got plenty of help and advice on the way, I am really stuck with it. I really like the idea of ubuntu, so I was wondering whether it is a good idea to fall back to gutsy which is a tested and tried OS and learn a bit more about ubuntu in general, rather than trying to learn the hard way in a newly released system that "may" still have bugs.

you guys reckon that's wise or will I most likely run into the same problems in gutsy as well?

Thanks for the feedback,

Nebelhom

---

### Post by c4v3m4n on 2008-05-06
I don't think it's a bad idea at all.  I haven't even upgraded from gutsy yet because there just seems to be too many problems with hardy still.  Whatever works for you man.

---

### Post by Dougie187 on 2008-05-06
I think its totally fine. If you have to use gutsy its better than nothing. Though getting Hardy to work would probably be a better idea.

---

### Post by Oldsoldier2003 on 2008-05-06
> **Nebelhom said:**
> Hi all,

I recently installed hardy heron on my PC in a dual boot. I'm a complete and utter newbie and straight away ran into some issues with my graphics card drivers that up to now after one week of constant trying I haven't resolved. (I basically always had to start in vesa mode without drivers or failsafe mode with installed drivers)
(if interested see thread: [http://ubuntuforums.org/showthread.php?p=4885303#post4885303](http://ubuntuforums.org/showthread.php?p=4885303#post4885303) )

Although I got plenty of help and advice on the way, I am really stuck with it. I really like the idea of ubuntu, so I was wondering whether it is a good idea to fall back to gutsy which is a tested and tried OS and learn a bit more about ubuntu in general, rather than trying to learn the hard way in a newly released system that "may" still have bugs.

you guys reckon that's wise or will I most likely run into the same problems in gutsy as well?

Thanks for the feedback,

Nebelhom

I think its worth a shot to try gutsy and revisit hardy again at a later date. I fisrt started playing with Ubuntu back when breezy was out and left to use opensuse, which I turned out not liking. Another alternative might be to try Debian Etch. Since Ubuntu is a descendant of Debian switching between the two adds very little learning curve.

---

### Post by Nebelhom on 2008-05-06
just a quick question. I got


Intel Core2 CPU
6420 @ 2.13GHz
2.00 GB RAM

Onboard Sound
GeForce 7600 GS

is it AMD64 or the standard x86 version.

in hardy they say intel for AMD (Which is the one I chose there) and in gutsy they mention "most intels" for x86. which one?!

---

### Post by kansasnoob on 2008-05-06
If Gutsy worked well for you before, why not?

It's still supported for many months!

I only changed because I was in the middle of a build about one week before the release candidate came out, so I gave the Beta a test drive and all worked well for me.

But ........ I run very basic hardware, nothing fancy, and everything's dual booted with Windows just in case.

But I'm running out of reasons to even own a Windows OS.

---

### Post by Dougie187 on 2008-05-06
AMD64 would be for a 64 bit computer. I am not completely sure, but I dont think an intel core 2 duo is 64 bit, so I would use this one.

[http://mirror.ox.ac.uk/sites/releases.ubuntu.com/releases/8.04/ubuntu-8.04-desktop-i386.iso](http://mirror.ox.ac.uk/sites/releases.ubuntu.com/releases/8.04/ubuntu-8.04-desktop-i386.iso)

---

### Post by Grishka on 2008-05-06
> **Dougie187 said:**
> AMD64 would be for a 64 bit computer. I am not completely sure, but I dont think an intel core 2 duo is 64 bit, so I would use this one.

[http://mirror.ox.ac.uk/sites/releases.ubuntu.com/releases/8.04/ubuntu-8.04-desktop-i386.iso](http://mirror.ox.ac.uk/sites/releases.ubuntu.com/releases/8.04/ubuntu-8.04-desktop-i386.iso)

Intel Core 2 are 64-bit processors.

---

### Post by Nebelhom on 2008-05-06
oh oh, I hope I didn't kick off a discussion here :popcorn:

sorry, guys, this is a bit embarrassing. I'm talking about going "down" to gutsy etc. but I actually don't reeeeally know how to. I thought it would just be a quick deinstall of hardy and re-install of gutsy in the newly empty partition.

looks like I was yet again wrong. is there an easy to follow Howto guide somewhere or an easy way to switch between distros?

thanks for the patience. I really am that incompetent ;(

Nebelhom

---

### Post by Grishka on 2008-05-06
> **Nebelhom said:**
> oh oh, I hope I didn't kick off a discussion here :popcorn:

sorry, guys, this is a bit embarrassing. I'm talking about going "down" to gutsy etc. but I actually don't reeeeally know how to. I thought it would just be a quick deinstall of hardy and re-install of gutsy in the newly empty partition.

looks like I was yet again wrong. is there an easy to follow Howto guide somewhere or an easy way to switch between distros?

thanks for the patience. I really am that incompetent ;(

Nebelhom

there's no easy way to downgrade, as far as I know. reformatting your system partition for Gutsy seems to be the easiest way. unless you installed with Wubi?

---

### Post by Nebelhom on 2008-05-06
ok, thanks all of you for the quick replies.

I'll try to delete the linux partition via windows XP installer and then cancel.

will it be a problem if I leave Grub on? I am assuming that the linux installation will notice if grub is already installed and skip that bit.

Thanks again.

---

### Post by Grishka on 2008-05-06
> **Nebelhom said:**
> ok, thanks all of you for the quick replies.

I'll try to delete the linux partition via windows XP installer and then cancel.

will it be a problem if I leave Grub on? I am assuming that the linux installation will notice if grub is already installed and skip that bit.

Thanks again.

you don't have to use windows for that. you can delete and partition your hard drive from Gutsy live CD. the installer will update Grub accordingly, there's probably no need to mess with it.

---

### Post by Nebelhom on 2008-05-06
Phew. I think this is the first time I am glad downloads take long ;).
I was mentally preparing for a digital waterloo with me being the french :).
cheers

I'll try that

Nebelhom

---

### Post by louieb on 2008-05-06
When you install Gutsy - at the partitioning step choose manual partitioning. 
Just select the Hardy partition for / (root), check the format box  and rock on. 
The installer will then overlay Hardy with a fresh install of Gutsy. 

No need to delete Hardy's partition - just reuse it.  And the Gutsy grub install should   set up to dual boot just like the Hardy install did.

---

