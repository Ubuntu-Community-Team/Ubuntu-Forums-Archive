---
title: "MFC 7420 scanner &quot;failed to open device&quot;"
date: 2013-04-08
forum: New to Ubuntu
---

### Post by jtsnsc on 2013-04-08
Hello,

First off I'm not sure if this is the correct forum to post to. If not please let me know. I just installed v12.04 and can not get my scanner to connect. I get the following error  - Failed to open device 'Brother2:bus4;dev1' invalid argument.
I have followed every possible instruction I can find and everything is set as they say it should be. Can someone tell me why this error is occuring? Shouldn't the scanner be seeing bus 1 dev 5 not bus 4 dev 1. If so how do I change it to the correct location? The printer prints as it should. I am using 64 bit drivers.

Any help would be appreciated

Bus 001 Device 002: ID 0409:0059 NEC Corp. HighSpeed Hub
Bus 002 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 003 Device 002: ID 04f2:0760 Chicony Electronics Co., Ltd Acer KU-0760 Keyboard
Bus 004 Device 002: ID 046d:c054 Logitech, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 043d:0139 Lexmark International, Inc. 
Bus 001 Device 005: ID 04f9:0180 Brother Industries, Ltd MFC-7420

---

### Post by kurt18947 on 2013-04-09
Have you look at the FAQs?
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html#f00106](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html#f00106)

There is an installer flaw with 64 bit drivers.  The 4th item in the FAQ list addresses it.  If you're using a USB connection you'll need to edit a file to be able to use the scanner as a non-SUDO(normal) user.  That is addressed in the FAQ toward the bottom of the list.  If you make these changes, you'll probably need to restart for them to take effect.  These items make my Brother scanner functional.  I hope you're able to get your machine working properly.

---

### Post by jtsnsc on 2013-04-09
> **kurt18947 said:**
> Have you look at the FAQs?
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html#f00106](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html#f00106)

There is an installer flaw with 64 bit drivers.  The 4th item in the FAQ list addresses it.  If you're using a USB connection you'll need to edit a file to be able to use the scanner as a non-SUDO(normal) user.  That is addressed in the FAQ toward the bottom of the list.  If you make these changes, you'll probably need to restart for them to take effect.  These items make my Brother scanner functional.  I hope you're able to get your machine working properly.


Thank you.... This corrected the error. I've been struggling with this for days.

---

### Post by kurt18947 on 2013-04-09
You're welcome.  I've seen the putting files in the wrong folder error with other manufacturers as well.  I recall reading about the problem and it seems to be a problem with Alien.  Alien is a program that converts .rpm packages into .deb packages.  It seems somewhat common among hardware manufacturers to package drivers as .rpm packages and convert with Alien rather than repackage.   I am nowhere near knowledgeable enough to understand the whats and whys but Brother obviously knows about the problem.

---

