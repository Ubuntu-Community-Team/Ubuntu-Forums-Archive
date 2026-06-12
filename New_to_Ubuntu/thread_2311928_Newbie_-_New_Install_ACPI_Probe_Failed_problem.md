---
title: "Newbie - New Install ACPI Probe Failed problem"
date: 2016-01-31
forum: New to Ubuntu
---

### Post by spanner3 on 2016-01-31
I am a brand new Ubuntu user, I am trying to do an install to the hard drive.  I am using a USB stick, PC completes POST, states on screen that "loading operating system" then I get an error "ACPI Probe Failed" followed by a blank screen.  I googled the message and it seems that the issue relates to the graphics card. Resolutions I have seen state to set "acpi=off" or "noacpi" under f6; I have tried all 4 combinations of these options and I still get the same error message.  I read a different post which said to turn off "nomodeset", again I get the same error message.

I have tried 2 different PC's, 1 Intel and the other AMD, get the same error on both.  Both machines are about 3 years old and have been running windows fine so I don't believe this is a hardware issue on either box.

This is the first time I have ever attempted to install Ubuntu so I have zero experience to try to trouble shoot this issue from so any help or ideas to resolve this would be greatly appreciated.

---

### Post by grahammechanical on 2016-01-31
Do not get distracted by the ACPI Probe Failed message. It is just a message. It is not indicating the source of the problem that you are having. I run the development version of each release of Ubuntu during its 26 week development period. I started seeing that message during the development period of 15.04, if I remember correctly. It never stopped my installation from loading to a working desktop. So, we ask, what is stopping your system from getting to a login screen?

First, is this happening after Ubuntu has been installed? Or is it happening to the live session? I am not clear as to the actual situation.
Second, how did the live session run?

The difference between the live session and an installed Ubuntu is the live session uses the open source video driver. When we install and tick the box "install third party software" we get some proprietary audio & video codecs & a proprietary video driver. So, if the live session worked well but after installing Ubuntu and restarting we get a blackscreen, then it could be a conflict with a proprietary video driver.

What we can try is to select the Advanced options for Ubuntu sub-menu at the Grub boot menu. Then we select a recovery mode kernel. And at the recovery menu we select Resume. If that gets us to a working desktop, and it might, we go to System Settings>Software & Updates>Additional Drivers tab and change video drivers.

We need to be connected to the internet and allow time for the utility to find the drivers. You might want to try using the open source video driver. After a few re-starts that get you to a working desktop with the open source video driver, then you can experiment with the offered proprietary video drivers.

Are you aware that you have not informed us of the version of Ubuntu that you are installing? Neither have you given us the hardware specification of the machine. That can be useful information. If you are installing Ubuntu 15.04 then you should be aware that it is about to reach end of life.

Regards.

---

### Post by spanner3 on 2016-01-31
Thanks for the reply.

To answer your questions the message appears when I first attempt to start the install of ubuntu on a blank hard drive so from your description this is the live session.  The screen will show the message ACPI Probe Failed problem for 2-3 seconds then the screen will go black and after another 5-10 seconds my display will tell me "no video available".  I have left the machine in this state for 10 minutes and there is no change.

The version of ubuntu is 14.04.3-desktop-amd64, I used rufus to build a flash drive install.  My mother board is a Gigabyte GA-M52LT-D3.  I have just tried the install with a (this is a different model of graphics card) ASUS EN210 SILENT/D1/1GD3V2(LP) and I still get the same message and black screen.

Just googled the versions and will download Ubuntu 15.10 and see if this resolves the issue.  Expect this will take an hour or so to download and test so will post results.

Thanks.

---

### Post by Vladlenin5000 on 2016-01-31
Forget about the ACPI message, it has nothing to do with anything.
You need *nomodeset* in order to have generic video with such NVIDIA cards you're using, so you can install the OS, then reboot - *nomodeset* again -, install the proprietary graphics drivers, reboot, *remove *nomodeset** and off you go...

---

### Post by spanner3 on 2016-02-01
I downloaded  Ubuntu 15.10 and it installed perfectly.

Issue is resolved.  Thanks for all your help.

---

### Post by Vladlenin5000 on 2016-02-01
You're welcome.

Please use the thread tools and select "Solved".

---

