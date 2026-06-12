---
title: "AGYP Video card doesn't display anything"
date: 2014-02-17
forum: New to Ubuntu
---

### Post by david164 on 2014-02-17
Hello,

I recently bought a video card from a local computer store known as AGYP, I installed the video card correctly- I think, yet when I attempt to boot into Ubuntu, I just get greeted by a black screen, I think this card I got from AGYP may be defected, or not compatible with Ubuntu, How can I find out?

Thanks!

---

### Post by jp734 on 2014-02-17
Type **lspci -k** and post back result.

---

### Post by Vladlenin5000 on 2014-02-17
If we were to believe *acritically *(I know, an invented word but I fell it's missing in English language) in everything a Google search tells us you're the only one in this world using such card... I would expect at least some references to stores selling it and hopefully the manufacturer itself. However, I found nothing except your post here and at Tom's Hardware.
Please run the command suggested above in order for us to check what hardware you really have and for graphic cards what really matters is the GPU, the chipset, whatever. The manufacturer (ASUS, Gigabyte, Zoltac, Colorful, Club 3D, etc. etc.) is hardly relevant but knowing the brand/model one can easily find what chip it has inside. Again, AGYP doesn't register.

---

### Post by david164 on 2014-02-17
Hello, 

Where exactly am I to type that command? I don't have access to the terminal for I cannot even boot into Ubuntu.

---

### Post by Vladlenin5000 on 2014-02-17
> **david164 said:**
> Hello, 

Where exactly am I to type that command? I don't have access to the terminal for I cannot even boot into Ubuntu.


Good point indeed. Let's try a different approach, shall we?
Please inform the better you're able to the specifications of 1. Your computer and 2. That new graphics card (check the package for any other info like model number, etc.)

---

### Post by Bashing-om on 2014-02-17
Vladlenin5000; Hi !

Let's work on getting you booted to a terminal so we can do some trouble shooting.

Boot up your ubuntu install; as soon as the bios screen clears depress and hold the right shift key -> grub boot menu;
Look through the boot options and find a "recovery" kernel;
With that line highlighted, press the enter key -> recovery console -> "resume normal boot".
Do you now boot to the GUI login ? 
If so go ahead and enter your pass word -> Desktop ?(degraded graphics is OK at this point)
Key combo ctl+alt+t yields a terminal interface.

Else: will try and boot you to a text login terminal (TTY1); or other things.

[INDENT]it is ubuntu
[INDENT][INDENT]all things are possible
[/INDENT][/INDENT][/INDENT]

---

### Post by ibjsb4 on 2014-02-17
Hi Bashing

His post in the Gentoo forum indicates he has this AGYP working.

---

### Post by Vladlenin5000 on 2014-02-17
> **ibjsb4 said:**
> His post in the Gentoo forum indicates he has this AGYP working.

Good for him but would anyone be so kind as to enlighten me/us about what that freaking card really is? Thank you.

---

### Post by Bashing-om on 2014-02-17
@ ibjsb4 Good deal;

Appreciate ya letting us know, not to direct any additional resources to this thread.

Hopefully the OP will return and advise the steps he did for resolution.

[INDENT]it is ubuntu
[INDENT][INDENT]all for 1 and one for all
[/INDENT][/INDENT][/INDENT]

---

