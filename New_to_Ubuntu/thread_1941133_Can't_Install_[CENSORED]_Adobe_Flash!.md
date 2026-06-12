---
title: "Can't Install [CENSORED] Adobe Flash!"
date: 2012-03-15
forum: New to Ubuntu
---

### Post by gremlinkurst on 2012-03-15
i have an rpm downloaded from adobe that SUPPOSEDLY is supposed to install flash.  it doesn't.  the instructions are NOT all that god-[CENSORED] clear; the proper installation location is NOT detailed, and it just gets worse after that.  the only thing i could do was UNPACK the accursed thing and stare dumbly at the disembowelled archive, having already attempted the obvious, merging the usr directory with the one that already exists.  i have been informed that i am denied permision DESPITE the fact i was never even ASKED for a root password.  i can't believe i can't even watch a [CENSORED] video on the [CENSORED] [CENSORED] [CENSORED] internet, can't believe adobe doesn't have an actual INSTALLER for linux machines.

---

### Post by Perfect Storm on 2012-03-15
You don't need in most cases to hunt down application for Ubuntu. You'll find them in the Ubuntu Software Center.

Simple open Ubuntu Software center and search for **ubuntu-restricted-extras**.
This will install Flash, Openjava and some codecs.

---

### Post by winh8r on 2012-03-15
Try using Flash Aid to sort out your flash problem.

Click on the "Help with Flash" link in my sig below and install flash aid and run the wizard then restart firefox.

---

### Post by TBABill on 2012-03-15
Most of the problem you are encountering is probably because you downloaded an rpm for a deb OS. Although it is possible to use an RPM, it is neither encouraged nor guaranteed to work well. Easiest way to get flash and all the codecs is just ```
sudo apt-get install ubuntu-restricted-extras
``` Or you can install Flash Aid extension in Firefox and it'll get Flash from Adobe, extract and install it all for you plus keep your version updated.

---

