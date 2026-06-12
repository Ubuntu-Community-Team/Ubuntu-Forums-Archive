---
title: "Cannot enter recovery mode"
date: 2013-02-24
forum: New to Ubuntu
---

### Post by jerrynewt on 2013-02-24
My daughter-in-law was given a laptop by her son that has 11.04 installed, but the power cord was bad. It has been setting for the last 2 years and she finally dug it out and got a good cord for it. Now they can't seem to remember the password. I tried to walk her thru the recovery mode but when she boots into recovery and selects the root line item it asks for the root password before she can get into the shell promtp.  She doesn't have a live CD and isn't very comp savvy, but she is trying to learn. Any ideas what we can do to get her up and running? She can boot into normal desktop but can't perform any admin functions without the password.

---

### Post by Bashing-om on 2013-02-24
jerrynewt; Hi !

Here are easy instructions to reset your password in Ubuntu:
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)
[INDENT][INDENT][INDENT][INDENT]hth

[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by jerrynewt on 2013-02-24
We tried that but it keeps asking for a root password before she can get to the shell.

---

### Post by Impavidus on 2013-02-25
Having a live cd/dvd/usb would be a good idea because it can help you solve many problems. Furthermore, 11.04 is end of live. There are no more security updates for that version. She hasn't used the computer in over a year, so there can't be much important on it. Therefore I suggest a clean start. Download the installation iso for 12.04 LTS (or 12.10 if you wish) and install. This should take about half an hour, bring the computer in a default state and prevent surprises in the future.

---

### Post by audiomick on 2013-02-25
> **jerrynewt said:**
> We tried that but it keeps asking for a root password before she can get to the shell.

Hmm, that's a showstopper, I think. 

I'm inclined to agree with Impavidus that a fresh install might be the simplest thing.

You say that you can boot into the computer. If there is anything useful on there that you want to save, you shouldn't have a problem moving it off onto an external drive or a USB stick.

You can also use the computer to get your installer, and creat the install medium. I would suggest 12.04 LTS. This is the current long term support version of Ubuntu.

When you have the installer, boot into the "try ubuntu" option to see if the computer is happy with the OS.

You will almost certainly have to add proprietary drivers to get the WiFi going, and might need proprietary drivers to get the graphics working properly. This is generally not a great problem. If the computer is connected to the internet on a cable, the additional drivers utility should pop up and offer you the drivers. You can install them in the live environment (booted into "try Ubuntu") to see if they work well, but that wont stick. You will need to install them again when you do the install for real.

---

