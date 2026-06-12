---
title: "opinions on BSD and other free/open unix OS's"
date: 2008-12-03
forum: Other OS Talk
---

### Post by WinterMadness on 2008-12-03
i dont really know anything about the bsd operating systems, but i was interested in getting a linux users perspective on these.

i know that if i were to use the terminal, the commands would be slightly different but other than that i dunno.

give philosophical reasons and technical ones

---

### Post by jimi_hendrix on 2008-12-03
i just installed PCBSD...it looks very similar to linux but i cant get my wifi working yet so i will tell you after i get it to work

---

### Post by cardinals_fan on 2008-12-03
I like NetBSD very much, and DragonFlyBSD & DesktopBSD a bit less.  I couldn't quite bring myself to like OpenBSD.  OpenSolaris is also fun.

---

### Post by jimi_hendrix on 2008-12-03
> **cardinals_fan said:**
> I like NetBSD very much, and DragonFlyBSD & DesktopBSD a bit less.  I couldn't quite bring myself to like OpenBSD.  OpenSolaris is also fun.

if i get bored...what should i install?

</othyjack>

---

### Post by perlluver on 2008-12-03
I installed FreeBSD, with the three CD's, after that, I had to download the Nvidia drivers, which took me a while to get to work, because I had to manually create an Xorg configuration.  All good after that for a minute.

Now on to the second part of my journey: Adobe Flash really does not work on FreeBSD, other than trough the Linux Binary Compatibles, I couldn't figure out how to get that to work.  

So then, I figure what the heck, give up with that, and add my nfs shares to fstab.  Oops on my part, I did not know that when you set up an nfs share on BSD, that you can not add defaults, like on Linux.  

Needless to say that took me about an hour to fix.  So after all that fun, I am back to Intrepid.

---

### Post by ddnev45 on 2008-12-03
Solaris 10 is good -- never crashed or froze on me for the year I used it. Hopefully OpenSolaris keeps moving forward.

---

### Post by jimi_hendrix on 2008-12-03
OpenSolaris == Solaris 10?

---

### Post by cardinals_fan on 2008-12-03
> **jimi_hendrix said:**
> OpenSolaris == Solaris 10?
No.  Solaris 10 is an enterprise-grade semi-proprietary OS currently offered by Sun.  OpenSolaris is the successor to 10, is fully open source, and is not necessarily ready for rock-solid deployments.  Future versions of Solaris will be based on OpenSolaris.

As for your earlier question, I would recommend NetBSD or DragonFlyBSD.  Both can be very fun to play with, if you're in the right frame of mind.

---

### Post by Grant A. on 2008-12-03
> **cardinals_fan said:**
> No.  Solaris 10 is an enterprise-grade semi-proprietary OS currently offered by Sun.  OpenSolaris is the successor to 10, is fully open source, and is not necessarily ready for rock-solid deployments.  Future versions of Solaris will be based on OpenSolaris.

As for your earlier question, I would recommend NetBSD or DragonFlyBSD.  Both can be very fun to play with, if you're in the right frame of mind.

Does Sun plan on releasing Solaris 11 for free as they did with Solaris 9 & 10? Btw, pretty amazing they managed to open source what is essentially a UNIX distribution. Thank God that Novell got that UNIX IP!

---

### Post by cardinals_fan on 2008-12-03
> **Grant A. said:**
> Does Sun plan on releasing Solaris 11 for free as they did with Solaris 9 & 10? Btw, pretty amazing they managed to open source what is essentially a UNIX distribution. Thank God that Novell got that UNIX IP!
*shrugs*

I would guess so, since most of their customers pay for support over the software itself.

---

### Post by yabbadabbadont on 2008-12-03
> **perlluver said:**
> ...

Now on to the second part of my journey: Adobe Flash really does not work on FreeBSD ...

That is a *feature*, not a problem.  ;)

---

### Post by Grant A. on 2008-12-03
> **yabbadabbadont said:**
> That is a *feature*, not a problem.  ;)

We are talking about BSD/UNIX, not Windows.

---

### Post by perlluver on 2008-12-03
Gnash apparently works, but if you have used Gnash, you know how well that works.  Yes flash not working could be a feature, but since I help my father-in-law with video and DJ services, I kind of use flash everyday.  So that feature didn't work for me.  Anyway it was pretty nice, but I can get the same thing from Gentoo, or Arch almost with flash.  So I will stick to the *nix for now. ;)

---

### Post by WinterMadness on 2008-12-03
whats the problem with flash?

---

### Post by perlluver on 2008-12-03
> **WinterMadness said:**
> whats the problem with flash?

It only works through Linux Binary Compatibles, and after reading how to do that for about a half an hour, my head kinda hurt.  Flash does not work natively in FreeBSD.

---

### Post by WinterMadness on 2008-12-03
> **perlluver said:**
> It only works through Linux Binary Compatibles, and after reading how to do that for about a half an hour, my head kinda hurt.  Flash does not work natively in FreeBSD.


well i meant how people are saying "its a feature, not a problem" it implies they dont want flash. I wonder why, outside of the fact its proprietary. Is it malicious in some way im not aware of?

---

### Post by perlluver on 2008-12-03
For most people, it is just a pain and a waste of bandwidth.  For me it is a form of pleasure to have.  To each there own I guess.

---

### Post by kk0sse54 on 2008-12-03
The *BSD operating systems are really fantastic with NetBSD in my opinion being my favorite. Unfortunately they tend to lag behind linux when it comes to things like hardware support and they often frustratingly lack certain features such as flash mentioned before.

OpenSolaris and it's derivatives are also really fun to use and they just released a new OpenSolaris which I have yet to try (the cd is sitting around here somewhere...). Nexenta is also an interesting project 
> Nexenta Operating System is a free and open source operating system combining the OpenSolaris kernel with GNU application userland

---

### Post by Rokurosv on 2008-12-04
I tried DesktopBSD but I didn't like it much, although I did get Flash to work, can't remember how. I was a little curious about OpenSolaris might try that later on.

---

### Post by Sorivenul on 2008-12-04
You had to bring this up, didn't you?  
Just kidding. I love these systems.  

FreeBSD is my favorite to use, and I run it specifically for mission critical work.  NetBSD and DragonFlyBSD are my favorites to tinker with. The other *BSDs are a proverbial grab-bag, especially when it comes to hardware support.  I am currently looking into some of the lesser BSD systems (MidnightBSD and MirOS).    

OpenSolaris is a good system, but needs your help to test it, use it, and make it better.

Also worth mentioning would be MINIX and Plan 9.

---

### Post by zmjjmz on 2008-12-04
I've honestly only tried BelenIX, which is a little OpenSolaris distro when it was in beta (.7 to be exact).
I probably have to get an update to it, the copy I have is undoubtedly very old. It was a cool system (really fast in my experience), but since I could never get it to do the flash drive install I didn't get to do much with it.


Philosophically, more open source operating systems can only be good.


(Now this isn't UNIX, but I have used Syllable. It is awesome. So ridiculously awesome.)

---

### Post by cardinals_fan on 2008-12-04
> **Sorivenul said:**
> 
Also worth mentioning would be MINIX and Plan 9.
Plan 9 is always worth mentioning, but not worth trying :P

Then again, with Glendix out there...

---

### Post by cmay on 2008-12-04
> **jimi_hendrix said:**
> if i get bored...what should i install?

</othyjack>
minix the book version. that will keep you amused for some hours at least.

---

### Post by cmay on 2008-12-04
i love most of the other systems that i have tried.  i install linux on  many older computers and i use the debian set up on most of them.  but i have for myself some older computers that i use for testing and i use them for trying the other systems that are not exactly linux. so far i have a pretty well configured FreeDos partion and i have a old computer running minix. which i have to write a keyboard driver for my self if i ever want a danish keyboard layout. i been wanting to learn bsd but i have only tried pc-bsd which i did not like that much and i tried free bsd . then desktop bsd. which i like. i have also tried gnu solaris nexenta and gnewsence but these two could not get installed and boot for some reason. i have tried to install plan 9 but had to give up. i have a usb stick running belenix which is a open-solaris based distribution that has  a script that makes it so easy to install to usb stick that i could not resist trying iot out and i think its great. so i use it as a alternative to using live cd. i also use open-solaris and i love it. i use it as office computer and its the system i use for internet.

---

### Post by jimi_hendrix on 2008-12-04
> **cmay said:**
> minix the book version. that will keep you amused for some hours at least.

isnt minix ugly though?

---

### Post by cmay on 2008-12-04
> **jimi_hendrix said:**
> isnt minix ugly though?
no its kinda cute. if you like a terminal only. i have not mangaged to install desktop since my network card is not supported. and i have a keyboard layout that is not exactly danish but  can work around it. i have the book version and i think its great fun to play with but i am amazed that it can look so great as it does on the screenshots on their website. minix is going to be a great hobby of mine if i can figure out how to get internet and keyboard working.

---

### Post by jimi_hendrix on 2008-12-04
wait...its kinda cute if i like terminal only? thats like saying DOS is awesome looking

---

### Post by cmay on 2008-12-04
> **jimi_hendrix said:**
> wait...its kinda cute if i like terminal only? thats like saying DOS is awesome looking
  my Free-Dos installation looks pretty awesome. i have also modified it a "bit" :)

---

### Post by ibutho on 2008-12-04
I've used FreeBSD since the release of version 5 and also tinkered with NetBSD. Flash 7 will work fine using linuxpluginwrapper. Flash 9 crashes a lot and I guess its due to the fact that its heavily dependent on ALSA (which is not used on other Unix like OSes). Personally I like FreeBSD and NetBSD and they make a good replacement for Linux if you are willing to learn (just like switching from Windows to Linux).

---

### Post by cardinals_fan on 2008-12-04
> **jimi_hendrix said:**
> isnt minix ugly though?
That would depend on your tastes.  You won't find much of a GUI with MINIX.

---

### Post by zmjjmz on 2008-12-04
> **cmay said:**
> my Free-Dos installation looks pretty awesome. i have also modified it a "bit" :)

OpenGEM?

---

### Post by cardinals_fan on 2008-12-04
> **zmjjmz said:**
> OpenGEM?
I had almost forgotten OpenGEM!  Happy memories...

---

### Post by cmay on 2008-12-05
> **zmjjmz said:**
> OpenGEM?
nope. i did more than one thing. first the boot manager i change the tittle from freedos to cmayOS and then i changed the colors in the start up menu to blue and then i took the freebasic example and compiled with a change in the text so it said welcome to cmay OS instead of welcome to freebasic and made this start up as the first thing. i wrote a little start up script that makes the default dir one gets into a home folder and i changed all the folders names also so no one can see it is in fact free dos. but i do have open gem installed i just do not use it since i have no mouse for the old computer.  but i have the turbo pascal 5.5 installed from, borland antique software and i have free pascal which is why i have dos in the first place.

---

### Post by zmjjmz on 2008-12-05
> **cardinals_fan said:**
> I had almost forgotten OpenGEM!  Happy memories...

I just tried it (ver. 5) in DOSBox, it's pretty good.

---

### Post by em4r1z on 2008-12-05
Why the author also asked for 'philosophical' reasons to use or avoid the different Unix-like OS's, so...
While I'm not a hardcore open source fan, I like the idea behind the General Public License. I like that individuals enjoy a project which can distribute and modify as long as they keep these guarantees intact. For me, it's to acknowledge that your work/joy would be impossible without the work that many others gave you. Like retribution.
This is the main reason I prefer GNU/Linux over, say, FreeBSD.

---

### Post by kk0sse54 on 2008-12-05
> **em4r1z said:**
> Why the author also asked for 'philosophical' reasons to use or avoid the different Unix-like OS's, so...
While I'm not a hardcore open source fan, I like the idea behind the General Public License. I like that individuals enjoy a project which can distribute and modify as long as they keep these guarantees intact. For me, it's to acknowledge that your work/joy would be impossible without the work that many others gave you. Like retribution.
This is the main reason I prefer GNU/Linux over, say, FreeBSD.

Do you even understand the BSD licenses?

---

### Post by em4r1z on 2008-12-06
> **C!oud said:**
> Do you even understand the BSD licenses?
The right to do whatever you want with a project as long as you keep a note differs from what I stated. You inherit more than what you're entitled to produce.

---

### Post by handy on 2008-12-06
I used PCBSD about 18 months - 2 years ago, it was nice, it was the cleanest KDE I had ever used at the time, the forum was helpful, only tiny by comparison with this one of course.

I left it because I couldn't run Cedega/Guild Wars on it.

---

### Post by MisfitI38 on 2008-12-06
An opinion:
Philosophically, BSD is the 'right way'.
Kernel and all userspace apps developed together in one repository. No mish-mash of chaotic pieces arbitrarily collected together to form a 'distribution'.

The BSD license too, is done the right way; it protects the coder above the code, in contrast to the GPL, which is unruly and out of balance, weighing in favor of 'sourcecode, sourcecode, sourcecode'.

In practice, however, GNU/Linux generally offers more support for hardware, which is an advantage. Package management tools on GNU/Linux distributions tend to be pretty easy to use too; arguably a bit easier and more diverse than most BSD flavors.
Coming from a GNU/Linux background, I find BSD's very nice, but somewhat awkward to use as a desktop system.

---

### Post by init1 on 2008-12-06
> **jimi_hendrix said:**
> wait...its kinda cute if i like terminal only? thats like saying DOS is awesome looking
I would consider DOS to be very awesome looking ;)

> **cardinals_fan said:**
> That would depend on your tastes.  You won't find much of a GUI with MINIX.
There is a port of X11 for Minix, but for some reason, I can't get it to work with either of my laptops. It works in QEMU, though. Not many applications for it in any case.

---

### Post by cardinals_fan on 2008-12-07
> **init1 said:**
> 
There is a port of X11 for Minix, but for some reason, I can't get it to work with either of my laptops. It works in QEMU, though. Not many applications for it in any case.
As I see it, running X on MINIX is rather like adding a coffee grinder to a tea strainer ;)

---

