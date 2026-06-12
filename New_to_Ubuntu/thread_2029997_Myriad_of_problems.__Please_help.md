---
title: "Myriad of problems.  Please help"
date: 2012-07-20
forum: New to Ubuntu
---

### Post by yakinikku on 2012-07-20
Hi guys,

I finally got around to reinstalling ubuntu 12.04 (x86) on my computer and am having a whole slew of issues.  Here are the main issues I am having in order of severity.

1) Random GTK (GUI?) crashes.  Basically the screen suddenly goes black and I am brought back to the lock screen and have to log in again.  So far this seems to happen more when I am doing something and the computer is not sitting idle, but I wager if I left it idle long enough it would do the same thing.

2) Cannot resume from suspend.  I am using a laptop and when I close the lid and open it again the screen turns on, but its all black.  The only way for me to get back to doing anything is to restart the computer.

3) Plymouth is using VGA resolution.  Not the most severe of the issues, but something that still bugs me.  I would like to get the random crashing solved first if possible.  

At the moment, this is pretty much a fresh install.  I have installed some applications, I installed gnome-tweak-tool, but read somewhere that that was causing a problem for someone so I deleted it.

My computer is an Alienware M15x.  It has an nvidia graphics card and I have a feeling that is causing some of these problems.  Instead of using the 'additional drivers' tool in ubuntu, I followed these steps

[http://askubuntu.com/questions/104527/how-do-i-install-the-latest-nvidia-drivers-via-the-additional-drivers-tool](http://askubuntu.com/questions/104527/how-do-i-install-the-latest-nvidia-drivers-via-the-additional-drivers-tool)

to install the latest nvidia driver.

Please help me guys!  TIA!:guitar:

---

### Post by yakinikku on 2012-07-20
Doh!  Using Ubuntu not lubuntu

---

### Post by coffeecat on 2012-07-20
> **yakinikku said:**
> Doh!  Using Ubuntu not lubuntu

Fixed that for you! :wink:

---

### Post by yakinikku on 2012-07-20
> **coffeecat said:**
> Fixed that for you! :wink:

Much obliged my good sir or Madame

---

### Post by thatguruguy on 2012-07-20
> **yakinikku said:**
> 

3) Plymouth is using VGA resolution.  Not the most severe of the issues, but something that still bugs me.
I don't know of a way to fix that with the NVIDIA hardware. Fortunately, it's only on-screen for ~10 seconds, or so.


> **yakinikku said:**
> Instead of using the 'additional drivers' tool in ubuntu, I followed these steps

[http://askubuntu.com/questions/104527/how-do-i-install-the-latest-nvidia-drivers-via-the-additional-drivers-tool](http://askubuntu.com/questions/104527/how-do-i-install-the-latest-nvidia-drivers-via-the-additional-drivers-tool)

to install the latest nvidia driver.
You would have been better off if you had followed the instructions [here]("http://askubuntu.com/questions/36930/how-well-do-laptops-with-nvidia-optimus-work/36936#36936"). The issue is that you have Optimus on your laptop, which NVIDIA isn't supporting on Linux. There are two projects out there to deal with hybrid graphics for Linux, Bumbleebee and Ironhide. Both projects have been discussed at length in various threads in the forums. Take your pick.

---

### Post by yakinikku on 2012-07-20
> **thatguruguy said:**
> I don't know of a way to fix that with the NVIDIA hardware. Fortunately, it's only on-screen for ~10 seconds, or so.



You would have been better off if you had followed the instructions [here]("http://askubuntu.com/questions/36930/how-well-do-laptops-with-nvidia-optimus-work/36936#36936"). The issue is that you have Optimus on your laptop, which NVIDIA isn't supporting on Linux. There are two projects out there to deal with hybrid graphics for Linux, Bumbleebee and Ironhide. Both projects have been discussed at length in various threads in the forums. Take your pick.

My computer does not use Optimus at all.  My card is a gt260m.

---

### Post by thatguruguy on 2012-07-20
> **yakinikku said:**
> My computer does not use Optimus at all.  My card is a gt260m.

I stand corrected.

Did you try it with the suggestions in [this thread]("http://ubuntuforums.org/showthread.php?t=1762126")?

---

### Post by yakinikku on 2012-07-21
> **thatguruguy said:**
> I stand corrected.

Did you try it with the suggestions in [this thread]("http://ubuntuforums.org/showthread.php?t=1762126")?

I hope I didn't come off as too abrupt in my last response to you.  If so, I am sorry.  That was not my intention.  I appreciate the help!  I will give what you have linked me to a shot when I get home and report back.  It sounds like what is being described in that thread is exactly what is happening to me.  I hope that fixes the random crash so I can tackle these other problems.  :guitar:

EDIT: I applied the fix from that link.  I hope it works :).  I know my machine wasn't running in stealth mode, but I double checked that too.  Since it happens completely at random I will have to toy around in ubuntu some more trying to get it to crash.

Are there any log files that I should post that could help with the troubleshooting?

EDIT 2: No dice, just had another crash.

---

