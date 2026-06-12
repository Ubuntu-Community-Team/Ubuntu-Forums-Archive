---
title: "Ubuntu is slow even after i installed video card drivers"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by pankirk on 2008-08-20
I'll start with my computer's specs, since everyone always asks that.
CPU speed: 3.1 ghzs (amd)
videocard: nvidia 8800 gt
ram: 2gb's

So basically, I installed ubuntu 8.04 and it was SUPER laggy. even after using restricted drivers technique mentioned by various users. I decided to install KDE 4.1 because i'm a bit more used to KDE rather than gnome. So, after seeing it still lags in Gnome (i knew it would probably be even worse) i tried to use envy to install the real drivers(i guess?) and so once i did that it said it worked and i reset my PC. And it's still very laggy for me like i hadent installed any video drivers. Is there any way to check what's going on? It's quite frustrating the *buntu 8.04's are. I never had a problem with kubuntu 7.10 =/. Anyway, thanks a lot in advance for your help guys!

---

### Post by Gregmond on 2008-08-20
Sounds like it hasn't set your hardware up correctly.
Under "System -> Administration -> System Monitor" does it list your hardware correctly ?
Correct amount of RAM ? CPU Speed ?
What's using the CPU ?
Is your HDD being used all the time ?
May not be relevant but, did you use i386 or AMD64 OS ?

---

### Post by pankirk on 2008-08-20
Yes everything is listed correctly. That's the part that got me. I used a regular install of i386 because i didnt have much luck with the 64bit version (my cpu is able to use 64bit os's though) and as for my harddrive its an older 80gb IDE drive, not sata. But the drive can run windows vista easily with not nearly as much lag as this. It also ran Ubuntu 7.10 easily no lag at all.

---

### Post by nicedude on 2008-08-20
Try running top and see if anything is hogging the CPU etc.

And did you say you installed a new Nvidia driver if so which one and how, as the video driver still might be involved in the equation.

Oops I see now that you stated you used Envy to install, You could try the newest driver direct from Nvidia's linux driver page as that is what I do and I find it worked the best by far for my 8400M gpu chipset.

---

### Post by dustman on 2008-08-20
i also had trouble with Hardy, the cursor movement was very laggy (had to put "irqpoll" as a kernel boot parameter for the mouse to work at all - i think that this is causing the laggy cursor, cause if i removed it, the cursor was moving fine, but the mouse stopped working after 5-20 minutes). So now i'm back to Feisty, cause everything works there :D; looking forward to Ubuntu 8.10 though

---

### Post by Gregmond on 2008-08-20
As suggested, TOP might well tell you something.

Hmm have you got twinview set up ? might pay to kill it.
May be caused by Compiz, try turning that off.

Found this in another posting:
                                  ***Re: Hardy runs extremely slow..help!***             
                                                                [I]After updating my amd64 system to Hardy, everything started being slow as hell... my box was constantly doing swap.

I added the following boot options to my boot image at /boot/grub/menu.lst :
fb=false noapic nolapic

Now everything seems to be fine again.
[http://ph.ubuntuforums.com/showthread.php?t=782096&page=2](http://ph.ubuntuforums.com/showthread.php?t=782096&page=2)
[/I]  

I know I have had to use the noapic previously.

How did it run under a Live CD ? They are always a little slower, but if it was alright under the live CD I would definitly think its something in your install.

Goodluck

---

### Post by pankirk on 2008-08-20
The live CD was actually much faster. It also freezes a lot as well and I don't think it's my video card drivers because i'm sure that thy are the newest ones. I\'m going to try to 
> 
I added the following boot options to my boot image at /boot/grub/menu.lst :
fb=false noapic nolapic
 

I really hope that fixes it because I have a problem where I NEED the newest OV version and 7.10 isn't going to cut it for me (:):))
Also, thanks a lot for your help so far guys! Lots of great answers for me to try out.

---

