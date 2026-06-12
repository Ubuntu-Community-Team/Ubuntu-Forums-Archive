---
title: "Installing Ubuntu from a USB stick Problems"
date: 2013-01-26
forum: New to Ubuntu
---

### Post by jraymond14 on 2013-01-26
I have tried to boot from a USB drive using three different programs, LinuxLive USB creator, Universal USB creator, and UNetBootin. I am using a Dell Latitude E5410 running Windows 7.

Each time I select boot from USB device, I get to a menu with options to try Ubuntu without installing, boot into Ubuntu, and install on Hard Disk, etc. No matter which option I choose lines of text scroll up the screen, the screen goes black then turn almost back and I have to take out my battery to restart it.

I was wondering if there might be a problem with my USB stick(Sandisk Cruzer 8GB). I tried using the "check drive for errors" option from My Computer -> Removable Disk (F: ) -> Properties -> Tools but it said no error found. I also tried a different USB stick and had the same problem.

I tried
    -hit tab when you get to the menu that comes up when you boot from it
    -look for the end of the string, before --
    -remove the "quiet" and "splash" parameters and add "nomodeset xforcevesa" and press enter
    -If it's getting stuck somewhere, you'll see where and then you can post the error message.
but the result remained the same.

It was suggested to me that this might be a problem with my video card. My video card is an Intel(R) Graphics Media Accelerator HD(Core i5). When I looked up compatibility, it said that my GPU was supported.

Any suggestions would be greatly appreciated.

---

### Post by The Cog on 2013-01-26
Do you have a nvidia card? Sounds like you do.
Try this: When you see the icons of a keyboard and a man, press the enter key to get a menu. One of the F keys (F6 maybe) is for more options. Enable the **nomodeset** option and then escape back to your normal boot procedure.

---

### Post by grahammechanical on 2013-01-26
It is F6. We usually have to press Enter twice to get to the Try - Install screen and then press F6.

You can try those different options in the menu that comes up when we press F6. Select one and then press Enter then Esc.

At this point we can still edit the boot parameters which we see at the bottom of the Try - Install screen. Just move the left arrow key An option that I learnt about the other day was

> irqpoll

Put it before 'quite splash.' At this point F10 will boot those parameters.

I had a different problem to you but sometimes we have to try everything. I do agree with try 'nomodeset' on its own. The Live session will run without setting a video mode.

I know that the error messages scroll past very fast but is there anything on the screen that can indicate where the loading process has stopped?

Is there a flashing cursor? You may be getting to a Linux command line.

Regards.

---

### Post by jraymond14 on 2013-01-27
> **The Cog said:**
> Do you have a nvidia card? Sounds like you do.
Try this: When you see the icons of a keyboard and a man, press the enter key to get a menu. One of the F keys (F6 maybe) is for more options. Enable the **nomodeset** option and then escape back to your normal boot procedure.
Thank you very much! This worked :)

---

