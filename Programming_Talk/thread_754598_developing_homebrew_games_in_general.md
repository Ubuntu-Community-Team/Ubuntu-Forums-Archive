---
title: "developing homebrew games in general"
date: 2008-04-13
forum: Programming Talk
---

### Post by zizzdude on 2008-04-13
hey guys, I learned a bit about homebrew, and it seemed pretty cool to do on a wii or nintendo DS. but, I'm wandering if I actually have to mod it to make games, or just have the machine read the game on a disk or game card. 

I'm also looking for a wii homebrew development library for c++ too. :)

thanks guys.

---

### Post by sq377 on 2008-04-14
Homebrew on the Wii right now is still taking baby steps.  They just recently got code execution, so I wouldn't jump right into that.  Also, you wont likely be able to make your own game disks/cartridges without nintendo's help. 
[http://en.wikipedia.org/wiki/Nintendo_DS_homebrew#Programming](http://en.wikipedia.org/wiki/Nintendo_DS_homebrew#Programming)

Good luck

---

### Post by gny on 2008-04-14
Hello,

To be able to run Homebrew on the DS you need a card like the "R4" or similar,
just search google "ds R4". It's a card with a flash memory which you can download stuff to and just plug in to the DS.

It's easy too set up a toolchain for developing on the DS, compile and run examples.

A good start should be:

[http://en.wikipedia.org/wiki/Nintendo_DS_homebrew](http://en.wikipedia.org/wiki/Nintendo_DS_homebrew)

and

[http://www.palib.info/wiki/doku.php](http://www.palib.info/wiki/doku.php)
[http://www.devkitpro.org/](http://www.devkitpro.org/)

Regards,

---

### Post by louman on 2008-05-15
<plug>
For those interested in DS development, check out my HOWTO on setting up devkitPRO and some other libraries here:
[http://ubuntuforums.org/showthread.php?t=750050](http://ubuntuforums.org/showthread.php?t=750050)
</plug>

---

### Post by Can+~ on 2008-05-15
I've never developed things for homebrew systems, but my psp it completely hackable.

---

### Post by nhandler on 2008-05-15
> **Can+~ said:**
> I've never developed things for homebrew systems, but my psp it completely hackable.

For homebrew on the PSP, you don't need to do any hardware modifications. You either need to downgrade the firmware or upgrade to a custom firmware. Once you do that, you will be able to run homebrew off of the memorystick.

---

### Post by soapytheclown on 2008-05-16
> **zizzdude said:**
> hey guys, I learned a bit about homebrew, and it seemed pretty cool to do on a wii or nintendo DS. but, I'm wandering if I actually have to mod it to make games, or just have the machine read the game on a disk or game card. 

I'm also looking for a wii homebrew development library for c++ too. :)

thanks guys.

im not really developing games but aiming to set my wii remote up as a controller for my laptop hooked up to my tv, ive just started out and am using a library called wiiuse, its written in C and theres a Java implementation of it, i dont know anything about C++ but ive seen atleast one person use it in one of there projects so maybe it might be of help to you, heres the link :) [http://wiiuse.net]("http://wiiuse.net")

---

### Post by Twintop on 2008-05-26
As gny said, devkitPro/devkitARM (specifically) and PALib is a very good combination. I used PALib for an Embedded Games Development class (followed by some independant study credit) where I go to school and it has been very good to me. There are instructions in PALib's Wiki on how to get a development environment setup in Linux or Windows (I went with Visual Studio 2005 for simplicity).

One thing I will say is that if you are going to use PALib, it does not like to work with newer releases of devkitARM! You'll need to use PALib 070715 and devkitARM r20 (they're up to a community PALib release from this past February and r23 for devkitARM now, but they aren't compatible). I have a setup guide I put together for my professor to use in future classes to get the environment setup in Visual Studio 2005 or Visual C++ Express Edition 2005 if you'd like me to post it.

---

