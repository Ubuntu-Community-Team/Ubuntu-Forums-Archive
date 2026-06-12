---
title: "Sound issue with new 12.04 install?"
date: 2012-07-26
forum: New to Ubuntu
---

### Post by Homeroast on 2012-07-26
Hello all,

I've tried researching this but couldn't find a solution ...

I've recently installed Ubuntu 12.04 LTS on a basic entry level Lenovo G570 laptop (I wiped away Windows).  Everything is running very nicely except for one thing.  

When headphones are plugged in, volume only comes out of one side (left side).  The sound settings (in system settings) is fine and works as it should.

My question is, do I have a problem with Ubuntu or a problem with the soundcard (or both)?

Also, is there a snipping tool equivalent on Ubuntu that I could use to take pictures of something on my screen?

Thanks,

H

---

### Post by vexorian on 2012-07-26
If you try the headphones in another device, does it still happen?

If you use the Live CD, does it still happen?

If only you had Linux, it would be easier to know it is a sound card problem or not. But if your sound was working fine before you installed ubuntu, then it is most likely a problem with ubuntu.

--
Yes, there are tools to capture screenshots. Try to go to the software center and search for the word capture and/or screenshot. You will find some.

---

### Post by Homeroast on 2012-07-26
Thanks Vexorian.  

The headphones work great in other devices.

I'm not sure how to use the live CD after a full install on this machine.  I guess I could try (I'm still a newbie here) ... 

Also, I'm not  sure how the audio worked on this machine originally.  The first thing I did when I got it was to install Ubuntu.  :)

Thanks again for the helpful post.  I'll look for a screenshot application now ...

---

### Post by BlackWolfe on 2012-07-26
> **Homeroast said:**
> Thanks Vexorian.  

The headphones work great in other devices.

I'm not sure how to use the live CD after a full install on this machine.  I guess I could try (I'm still a newbie here) ... 

Also, I'm not  sure how the audio worked on this machine originally.  The first thing I did when I got it was to install Ubuntu.  :)

Thanks again for the helpful post.  I'll look for a screenshot application now ...

Whenever your computer reboots, do you know how to get into your BIOS? (Usually it's the DEL key). If you know how to get into your BIOS:

Look in  your BIOS for a BOOT ORDER section. There you can set it up where your computer will boot from your CD/DVD drive FIRST, and then any internal/external HDs that you have Ubuntu installed on. Once it boots up the LiveCD, it will once again give you the option to "check Ubuntu out" or "install Ubuntu". Use the first option, and it will boot up off of the LiveCD again, while usually mounting your hard-drive so you have access to it.  Once you do that,  you might follow the advice above about checking out your headphones to see if the problem lies within your install on your HD (if they work off the LiveCD) or something else.

Just thought I'd throw-in on how to boot from the LiveCD once you have it installed.

Best of luck!

---

### Post by Homeroast on 2012-07-27
Thanks BlackWolfe!

That is very helpful (and an oversight on my part).  I wasn't sure I could go back and make the BIOS read from the CD.  Makes sense though.

Thanks for getting me pointed in the right direction!  

I'll try that soon ...

---

### Post by mastablasta on 2012-07-27
also post specification of your sound card.
and run ```
alsamixer
``` (from terminal) to see if volumes and such are propperly set.
 
to get specificaitons of your card use this command in terminal:
```
 
lshw

```
 
then find the card in it, copy the text and post result here (should be under multimedia) using code tags (this icon: #)
 
also copy&paste and run this command in terminal:
```

 aplay -l
```
and then post the results here.

---

### Post by reinisvs on 2012-07-27
To get a basic screen shot, press the "Prt-Sc" located in the top right-hand section of you keyboard. You should get a small pop-up that lists four courses of action with your new screenshot.

---

### Post by Homeroast on 2012-07-27
Thanks everyone.  After running the LiveCD and rebooting the machine it works fine.  I guess all it needed was a good reboot.  :)  Thanks again for all the helpful suggestions.

---

