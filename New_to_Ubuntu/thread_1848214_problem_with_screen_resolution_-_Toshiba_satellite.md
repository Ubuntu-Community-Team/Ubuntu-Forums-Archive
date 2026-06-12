---
title: "problem with screen resolution - Toshiba satellite"
date: 2011-09-22
forum: New to Ubuntu
---

### Post by Journeyman1962 on 2011-09-22
Hi all,

New poster here.

I desperately need help. I have been trying to sort out the screen resolution on a ten year old toshiba laptop for about a year (on and off). Ubuntu 10.04 will only allow 800x600.

I have tried the xrandr and xorg.conf solutions after trawling through all the forums that exist on earth, and nothing works. Computer always returns "maximum resolution is 800x600" - or words to that effect. Or "failed to configure CRTC 0".

I can add a new modeline to the GUI monitor resolution facility, but computer still refuses to allow it.

I tried out Puppy Linux the other day, and the set up program just asked me what resolution the screen was - and, bang, it worked! I can't work out why it's so (seemingly) complicated in Ubuntu.

Any help gratefully received. Please let me know what specs/info you need.

Best
Tim

---

### Post by P05TMAN on 2011-09-22
Check out this thread. You may need to customize etc/X11/xorg.conf

[http://ubuntuforums.org/showthread.php?t=1847685](http://ubuntuforums.org/showthread.php?t=1847685)

---

### Post by roger_1960 on 2011-09-22
Hi

What laptop model is it.  I found a solution for a S1800-514 which is a 2001 model 13" screen which now runs at 1024x768 as it should.  If that may be it let me know (post back here) and i'll search out the info.

Edit:  found it - see post #12 in this thread
[http://ubuntuforums.org/showthread.php?t=806835&page=2](http://ubuntuforums.org/showthread.php?t=806835&page=2)

Roger

---

### Post by Journeyman1962 on 2011-09-22
Hi Roger,

It's Toshiba satellite, S1400 - 103, Model No. PS140E-03CSQ-IT.

Bought around the beginning of 2002 in Italy - if that's relevant (probably not....)

Cheers
Tim

---

### Post by Journeyman1962 on 2011-09-22
> **P05TMAN said:**
> Check out this thread. You may need to customize etc/X11/xorg.conf

[http://ubuntuforums.org/showthread.php?t=1847685](http://ubuntuforums.org/showthread.php?t=1847685)

Thanks for that, Po5tman.
I'm collecting the amassed wisdom at the moment :)
Tim

---

### Post by roger_1960 on 2011-09-22
Hi

I would try pasting the code giving in my link above into your xorg.conf.  My post #19 (in the link above explains how)  If your graphics card is a Trident Cyberblade Ai1 it should work

You can check what Graphic Controller by using the following command in a  terminal window
> sudo lshw

---

### Post by P05TMAN on 2011-09-22
> **Journeyman1962 said:**
> Hi Roger,

It's Toshiba satellite, S1400 - 103, Model No. PS140E-03CSQ-IT.

Bought around the beginning of 2002 in Italy - if that's relevant (probably not....)

Cheers
Tim
If you go to System>Administration>Additional Drivers, you can check for any propritetary drivers that you may need. If I'm not mistaken, that model of Toshiba has an older ATI  graffics card. I had an older Toshiba S1217 & to get the proper drivers, I just clicked on that 'Additional Drivers' icon.

---

### Post by Journeyman1962 on 2011-09-22
Roger and Po5tman,

Used the xorg script from post 12 of the linked thread. It worked!!!!

Thanks a million!

Tim

---

### Post by Journeyman1962 on 2011-09-22
PS:

Trying to avoid posting a question and not waste everyone's time, and trawling through the forums is good practice - but it's got its limits :D

Tim

---

### Post by P05TMAN on 2011-09-22
> **Journeyman1962 said:**
> PS:

Trying to avoid posting a question and not waste everyone's time, and trawling through the forums is good practice - but it's got its limits :D

Tim
Glad you got it sorted out, but what do you mean by the above statement? If you mean that to search for your answers on this forum is a waste of time, then I'm sorry but I believe that it is a better learning experience. Not to mention, you were pointed to relevant threads that were hyper-linked. As far as asking for more detail about your issue....well, I think that only goes to better assist you.

---

### Post by Journeyman1962 on 2011-09-22
No mate. You misunderstood me. I agree with you completely. In fact, everything I've had to sort out with the system, I've managed to do by looking through the forums - EXCEPT THIS ONE! And, I might add, learnt a lot of other stuff along the way.

I was, in fact, being critical of myself and my inability to find the correct answer unaided. All I needed, on this occasion, was to ask the specific question, and two people instantly pointed me in exactly the right direction.

That's what I like about this community. Everybody's got time for you and no one treats you like an idiot.

Best
Tim

---

### Post by P05TMAN on 2011-09-22
> **Journeyman1962 said:**
> No mate. You misunderstood me. I agree with you completely. In fact, everything I've had to sort out with the system, I've managed to do by looking through the forums - EXCEPT THIS ONE! And, I might add, learnt a lot of other stuff along the way.

I was, in fact, being critical of myself and my inability to find the correct answer unaided. All I needed, on this occasion, was to ask the specific question, and two people instantly pointed me in exactly the right direction.

That's what I like about this community. Everybody's got time for you and no one treats you like an idiot.

Best
Tim
I apologize for my misunderstanding, Tim; thanks for clearing that up! I'm glad you are a part of the community here

---

