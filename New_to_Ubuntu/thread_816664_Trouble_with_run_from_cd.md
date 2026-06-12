---
title: "Trouble with run from cd"
date: 2008-06-02
forum: New to Ubuntu
---

### Post by Padje Dog on 2008-06-02
Hi

I downloaded Ubuntu 7.10 (the "Gutsy" one) and unzipped it, burned it to CD and restarted my computer, first going into the BIOS to disallow booting from the hard drive but allowing booting from the DVD drive, and it says that there is no way to boot an OS. I ran the diagnostic that seems to be an inherant part of my computer (as it suggested as an option) and it passed everything.

When putting the cd in while using Windows the autoplay works fine, gives me options to install Firefox along with two other programs.

Can anyone help me to determine why it won't run from the CD?

I have a Dell Inspiron 6400 Laptop
1Gb Ram
T2400 @ 1.83 GHz

I'm not a computer simpleton but also not a genius, any help would be appreciated.

Cheers

*edit* I just wish to try the "run from CD" option first, not install :)

---

### Post by jualin on 2008-06-02
Do you have any other choice in the BIOS appart from "DVD", sometimes you need to try another choice like "Cdrom". If not you can use the Wubi Installer that comes with Ubuntu Hardy Heron 8.04.

*edit* Using the Wubi installer would allow you to boot from the CD without having to change anything in the BIOS. Plus based on your computer's specs you should be better off with 8.04.

---

### Post by Padje Dog on 2008-06-02
I heard version 8.x was sorta developmental stage, so I thought it best to go the tried and true one. 

Ok I'll try 8.04 and see what happens. 

Cheers

---

### Post by Padje Dog on 2008-06-02
One more question:

Which download do I need?

Intel x86 or 64bit PC?

I think I have the dual core chip, but not 100%, only 90%

---

### Post by jualin on 2008-06-02
do you have a 64 bit processor? If you do in some place in the outside of your computer you should have something that says it. Having a Dual Core PC doesn't mean that you have a 64-bit PC, I have a Pentium Dual Core which is 32bits. Basically if your computer doesnt say anything about 64 bits it should be a 32 bit computer and therefore you need to download the Intel x86 version. 
Also, maybe in the BIOS you can check if the computer is 64 or 32 bits.

*edit* And about the "developmental stage" is actually the opposite, 8.04 (Hardy Heron) supports more hardware by default and is supposed to be more stable than 7.10. The only software that you might consider in the developmental stage is Firefox 3 Beta 5 which 8.04 includes by default versus Firefox 2 in 7.10. However many people argue that Firefox 3 Beta 5 is more stable than Firefox 2.

Good Luck!

---

### Post by jualin on 2008-06-02
I just noticed something from what you did that may have influence in your computer not being able to boot from the CD. You said "I downloaded Ubuntu 7.10 (the "Gutsy" one) and **unzipped** it". When you download any .iso Image, Windows or WinRar usually treats it as a "zipped" file and therefore you might think that unzipping it and then just putting the files in a CD will make the CD ready for an installation. However this is wrong, you dont have to unzip anything, instead you are supposed to use the "Burn Image" option from your favorite CD/DVD Burning Software such as Nero or Roxio. So maybe thats why the CD did not boot up correctly, because you burned it in an incorrect way.

---

### Post by Padje Dog on 2008-06-02
Thanks for the help!

---

### Post by jualin on 2008-06-02
No problem dude, any time!

---

