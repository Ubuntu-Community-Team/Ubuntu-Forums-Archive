---
title: "Black screen at boot and wireless problem"
date: 2012-05-14
forum: New to Ubuntu
---

### Post by BazzaR on 2012-05-14
Hi All, new to the forum and Ubuntu. I am really battling at the moment, not just with the installation but also finding the correct way to fix the problems I am having.
So let me apologise now for the following questions, cause they probably been asked before but I can seem to find the right solution.
I have a dell inspiron mini 10 netbook and trying to install 12.04
The first time I tried to install it from a flash drive the screen was all screwed up and wouldn't install unless i quit the installer and installed it from the 'try ubuntu desktop'
After that installation it would not boot up at all, just showed a purple screen and then blank screen.
So I burned a dvd and installed it from there. First reboot did the same as above and after ctl+alt+del it booted up successfully.
An error also showed saying missing wireless firmware. And checking after the re-boot, the wireless is in fact not working.

So how can I sort these issues out? The whole boot up problem and the wireless problem?

Sorry again if this has been asked, and  appreciate the help.
Cheers
And now it wont boot up at all!!!! so frustrating

---

### Post by Rodney9 on 2012-05-14
Welcome.

I'm sorry I have very limited knowledge on this, but a little research turned up these - 

[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)

It seems the graphic card in these notebooks is the problem, Intel don't offer any support.

[http://ubuntuforums.org/showthread.php?t=1874552](http://ubuntuforums.org/showthread.php?t=1874552)

The Freezy Linux may work better for you, worth giving it a go.

Good Luck

Rodney

---

### Post by BazzaR on 2012-05-15
Thanks for the info, will give it a try.
I also tried to install Mint 12 and that didnt work either. It starts and then just goes to a @mint command prompt.
I am getting really frustrated, thought this was going to be easy and work like a charm but it seems to be a bit more involved than that.

---

### Post by roelforg on 2012-05-15
> **BazzaR said:**
> Thanks for the info, will give it a try.
I also tried to install Mint 12 and that didnt work either. It starts and then just goes to a @mint command prompt.
I am getting really frustrated, thought this was going to be easy and work like a charm but it seems to be a bit more involved than that.

Try nomodeset ([http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)).
My laptop needed it until i installed the ati/amd drivers for the card.

---

### Post by BazzaR on 2012-05-15
How and where do I get the netbook remix?
And does anyone know why Mint wont install?

---

### Post by xedi on 2012-05-15
Mint is based on Ubuntu, so if Ubuntu does not run, chances are that Mint won't, too, because at its core it's Ubuntu.

---

### Post by nothingspecial on 2012-05-15
Title changed to reflect the problems

---

### Post by BazzaR on 2012-05-15
So freeze does not work either...............
Going to try and re-install straight ubuntu and see what happens.
I have read all the fixes for the screen/graphics card but I cant understand them and when I try the fix nothing happens. If I type in the command prompt always asks for a password??????

---

### Post by xedi on 2012-05-16
> **BazzaR said:**
> So freeze does not work either...............
Going to try and re-install straight ubuntu and see what happens.
I have read all the fixes for the screen/graphics card but I cant understand them and when I try the fix nothing happens. If I type in the command prompt always asks for a password??????

If the command starts with sudo, then that is normal because you are declaring that this command needs full control over the system, which requires your password for security reasons.

---

### Post by BazzaR on 2012-05-17
Okay, I have sorted out the problem I have 12.04 running perfectly on my Dell Mini 10.
Wireless is working and boots up quickly and without a hiccup.
Thanks for the link, Rodney9. It helped and finally figured out how to boot properly. 
used the link below to figure out the wireless problem
[http://ubuntuforums.org/showthread.php?t=1974006&highlight=broadcom+wireless](http://ubuntuforums.org/showthread.php?t=1974006&highlight=broadcom+wireless)

Thanks again

---

