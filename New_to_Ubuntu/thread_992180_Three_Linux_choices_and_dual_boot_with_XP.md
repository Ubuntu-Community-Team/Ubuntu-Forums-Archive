---
title: "Three Linux choices and dual boot with XP"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by monkpoirot on 2008-11-24
My previous experience is limited to a few weeks use of Kubuntu Alternate in a very old notebook.
Now i'd like to make more experiments by installing in a P3,1000MHZ,256MB RAM machine with a light edition XPHome 5GB partition (of 20 total) one of the following distros I had previously downloaded :

VectorLinux 5.9GOLD
Kubuntu alternate (for < 256 MB RAM)
Puppy  Linux version 4.1.1

Which one is better for such a weak machine and small partition?
What should i do in order to install a Linux in the H-partition and keep XP in C and dual boot?

Thanks in advance,i hope somebody replies in spite of not being a strict Ubuntu question,
monkpoirot

---

### Post by MinstrelBoy on 2008-11-24
I installed Puppy 4.1 on an old laptop, 300Mhz and 192mb and it works Ok, so it should fly along on you machine. Puppy is great !

---

### Post by Bölvaður on 2008-11-24
> **monkpoirot said:**
> 
Kubuntu alternate (for < 256 MB RAM)

This is alternate cd, but still a full installation, which means that you shouldn't expect it to be anything else than causing you problems... and have 100% load on your RAM at all times.

What you need is something smaller like the one you got there, puppy. And try debian with openbox instead of kde, gnome or what ever (you need to install it your self.)

---

### Post by snowpine on 2008-11-24
I suggest you burn Live CDs for a few different distros and experiment to find which YOU like best. Puppy Linux is a great option for older hardware. I also like SliTaz, Debian+LXDE, or even Sidux (with Xfce or LXDE, not KDE) if you are feeling very adventurous.

---

### Post by Titan8990 on 2008-11-24
If you don't mind doing a lot of tweaking you can install Ubuntu or Debian and then install jwm. This will give you a lightweight desktop like Puppy Linux but will also have features such as Debian package management.


Edit: XFCE used to be my desktop of choice for lightweight on older hardware. In the end, I found it to be too bulky and am now a big fan of jwm.

---

### Post by CJ56 on 2008-11-24
Have you thought of Zenwalk?

It runs on my wheezy old Celeron laptop with 256Mb RAM and does a nice job with Xfce. Easy to install, too, and not a bad package management system once you get used to it...

---

### Post by monkpoirot on 2008-11-25
Sorry for the delay,also due to time zone.
Thanks everybody for replying to my question.
@MinstrelBoy, I take notice and i'll definetely try Puppy first.

@Bölvaður, yes Kubuntu alternate gave me some problems,but i ascribed them to the machine. I'll try puppy.

@Titan 8990,with jwm  are you referring to Joes Window Manager as
outlined at  [http://en.wikipedia.org/wiki/JWM](http://en.wikipedia.org/wiki/JWM)  ?

At first sight it gives me the (possibly wrong) idea of being less easy for a newbie than puppy, but i'll investigate further.

@CJ56, thanks for pointing me to Zenwalk, it seems ok for my needs i only need some time to try it.

As i am now going to install Puppy in the 5GB partition and there's XP Home in the other 15GB one, is there anything i should know or do before installing Puppy to later be able to dual boot with both OSs?

---

### Post by wizard10000 on 2008-11-25
Given the choice I prefer Vector Linux - ran an older version on an old 300MHz IBM Thinkpad and all the hardware just worked - and I tried about eight distributions on that laptop before I got one that just ran.

I heart Puppy but don't like Puppy's security model - I get that Puppy is supposed to be a light, fast single-user system but there are other distributions that are just as fast that have a better security model.

I'd take a hard look at Vector.

---

### Post by wizard10000 on 2008-11-25
> **monkpoirot said:**
> What should i do in order to install a Linux in the H-partition and keep XP in C and dual boot?

I'm gonna swim upstream here and recommend that a machine that has Windows installed needs to boot from a Windows bootloader  ;)

The reason for this is that a Windows install (or reinstall) is *always* gonna overwrite the boot sector and install its own bootloader so I tend to just let Windows have the boot sector, install grub on the first Linux partition and use Windows to call grub instead of the other way around.

Check out bootpart -

[http://www.winimage.com/bootpart.htm](http://www.winimage.com/bootpart.htm)

good luck!

---

### Post by monkpoirot on 2008-11-26
wizard10000,thanks for Bootpart, i wonder if it works for non english machines as well.

I didnt know about Puppy's security shortcomings,a matter to be thoroughly investigated.

---

### Post by gn2 on 2008-11-26
Some other choices to consider:

[Sam Linux]("http://sam.hipsurfer.com/index.php?page=downloads")

[Linux Mint 5 Xfce Edition]("http://www.linuxmint.com/rel_elyssa_xfce.php")

[Debian Xfce]("http://cdimage.debian.org/cdimage/lenny_di_rc1/i386/iso-cd/debian-testing-i386-xfce-CD-1.iso")

---

### Post by monkpoirot on 2008-11-26
For some strange quirk of my eyes or the browser I didnt see 
snowpine
post before. Thanks for his advice, i will digest and comply.

---

### Post by monkpoirot on 2008-11-26
@gn2 :  what a fantastic mass of info about all the topics i need you provided with the herman link and the other info,too!
an invaluable help really,thanks a lot!
I need some time to study it all now,but you saved me a lot of fuss.

---

### Post by zvacet on 2008-11-26
All suggestion are very well,but having Kubuntu alternate CD did you try just switch desktop and having Xubuntu?I mean you have it on your CD and all you have to do is described [here.]("http://psychocats.s465.sureserver.com/ubuntu/purexfce") Read under **Remove Kubuntu**.

---

### Post by monkpoirot on 2008-11-27
@zvacet,i'm overwhelmed by the expertise and the will to help in this forum.
I didnt know you could do that sort of 'downgrade' in Kubuntu, but i must warn you that i have the CD ,but no longer the install,which died with the machine it hosted it, so my three choices are on a par now.
Thanks to you,too. I got enough info to be happy through christmas holidays and beyond....

---

### Post by Th3Professor on 2008-11-27
> **monkpoirot said:**
> My previous experience is limited to a few weeks use of Kubuntu Alternate in a very old notebook.
Now i'd like to make more experiments by installing in a P3,1000MHZ,256MB RAM machine with a light edition XPHome 5GB partition (of 20 total) one of the following distros I had previously downloaded :

VectorLinux 5.9GOLD
Kubuntu alternate (for < 256 MB RAM)
Puppy  Linux version 4.1.1

Which one is better for such a weak machine and small partition?
What should i do in order to install a Linux in the H-partition and keep XP in C and dual boot?

Thanks in advance,i hope somebody replies in spite of not being a strict Ubuntu question,
monkpoirot
If you're looking for an opinion, there are many ;) ...mine would be to go for Vector... but I'm also a Slacker (Slackware user), and I advocate use of Slackware or Slack-based systems/set-ups. Though, not entirely. There are lots of excellent options available. You could go Debian-based or RH-based... or any of many others. Even Unix, my personal favorite, generally speaking, including BSD & SysV. But all of that's just a matter of opinion.

You might find that you prefer a system that installs everything for you.
You might find that you prefer a system that you install everything yourself.

Different *nix systems have different package managers (ways of installing, deinstalling, etc.-changes, all of your programs/applications).

All *nix systems let you use "source", they say "compile from source", for example, in which case you would manually install the program or programs in the command line, which includes maximum control over exactly how it is installed. That's where you see the famous commands "./configure", "make", "make install", and many more.

You might also like the idea of installing a system that handles everything automatically for you, then install a virtual machine or otherwise emulate an install of another *nix within that *nix, during which you could safely experiment with learning how to manually install everything without the worry of messing up anything important. ;)

Ultimately, you will have maximum control of the computer if you either install and set up everything manually or at least if you are aware of what's going on with the automatic processes.

> **monkpoirot said:**
> Which one is better for such a weak machine and small partition?"

From scratch (mostly) is perhaps the least opinion-based option.

> **monkpoirot said:**
> What should i do in order to install a Linux in the H-partition and keep XP in C and dual boot?

I'm not sure if someone else already answered this but several Linux "meta-packages", or similar, come with programs like "gparted" or similar partition editors, which are capable of detecting the partition that you'd like to install on (while not interfering with your Windows install).

---

