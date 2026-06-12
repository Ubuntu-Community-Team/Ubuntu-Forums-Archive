---
title: "External sound output doesn't work on Lenovo thinkpad"
date: 2012-03-08
forum: New to Ubuntu
---

### Post by neojamin on 2012-03-08
Hi everyone,

I just installed ubuntu 10.04 on my Lenovo thinkpadedge laptop, I had the 11.04 version before and just downgraded. Everything works fine beside the fact that headphones or external speakers don't work. I connect them and the sound keep coming out of the internal speakers.

I check with the alsa project and they give me this link:
[http://www.alsa-project.org/db/?f=9b0f201536366d8e438ae3e9867562940d575a2b](http://www.alsa-project.org/db/?f=9b0f201536366d8e438ae3e9867562940d575a2b)

I don't really understand it and don't know what I could or should do.

Thanks a lot for you help in advance!

Ben

---

### Post by Jon Monreal on 2012-03-08
I've actually experienced a similar problem before.

Firstly, could you try opening a terminal and typing "alsamixer" and pressing enter, and seeing what it says for items such as "Headphone"? If it says "MM," that means that the device is muted (which presents a problem, because even if you unmute it it would likely still play from the internal speakers). If it doesn't appear at all, then there are other problems.

Thanks.

---

### Post by neojamin on 2012-03-09
Hi, thanks for replying so quick! I did Alsamixer and there are nothing about headphones, only pcm and master which have a colorful bar and S/PDIF defaut and 1 that have 00.

Do you have any idea waht it could be!?

Thanks a lot!

---

### Post by Jon Monreal on 2012-03-09
Can you give me a more detailed model number for your laptop? That could help me identify what hardware you have and attempt to come up with a solution.

Thanks.

---

### Post by neojamin on 2012-03-09
HI, its a thinkpad edge 13"...Id on't really know how to find more info in ubuntu, I just runned Sysinfo and got some info:
Intel(R) Core(TM) i3 CPU       U 380  @ 1.33GHz
 SOundcard:Intel corporation 5 series/3400 series Chipset High Definition Audio (rev06)
Subsystem:lenovo Device 21 c8

need anything else? thanks

---

### Post by Jon Monreal on 2012-03-09
Try opening a terminal and typing: sudo gedit /etc/modprobe.conf/alsa-base.conf

Add (copy and paste) the following on a new line at the end: options snd-hda-intel model="olpc-xo-1_5"

Then, save and restart, and test the headphone jack.

---

### Post by neojamin on 2012-03-09
I put the first line and a blank document opens...is it meant to be blank?

---

### Post by Jon Monreal on 2012-03-09
That's fine.

---

### Post by neojamin on 2012-03-09
I can't save the file, it says: Could not find the file /etc/modprobe.conf/alsa-base.conf.
Please check that you typed the location correctly and try again.

---

### Post by Jon Monreal on 2012-03-09
Sorry I'm facepalming right now.

It should be: sudo gedit /etc/modprobe.d/alsa-base.conf

---

### Post by neojamin on 2012-03-09
Great!!! It's working! That was amazing, thank you so much, you made my day!
Have a good one!

---

### Post by Jon Monreal on 2012-03-09
It's no problem.

If you get a chance, could you mark the thread as solved under "Thread Tools" at the top of the page?

Thanks.

---

### Post by neojamin on 2012-03-09
Yes...and one other thing :) the internal mic is not working either with skype...any idea what it could be? Is it related?

---

### Post by Jon Monreal on 2012-03-09
Try the same as above, but replace it with this: options snd-hda-intel model=thinkpad

---

### Post by neojamin on 2012-03-09
Hi again...I try what you told me...and if I do that the external headphones don't work, there is like a conflict.
Everything was so working fine with 11.10, it is really weird. 

If you have another suggestion, thanks for helping, if not I might just live without mic! :)

have a great day!

---

### Post by Jon Monreal on 2012-03-09
Interesting, have you tried the mic in any program other than Skype? Could it maybe be Skype itself that's the problem?

Also, you might want to try opening a terminal, typing "alsamixer" minus the quotes again, and when the mixer comes up press F4to switch to capture devices. You should be able to check the internal mic's level there.

---

### Post by neojamin on 2012-03-09
It is not only skype, the voice recorder of ubuntu doesn't work either. When I check the asamixer in the terminal there is only one capture now, the bar seem full green, white and red.

---

### Post by Jon Monreal on 2012-03-09
I'm afraid I don't have anything other than that. That's kind of weird that you can only have one or the other though.

---

### Post by neojamin on 2012-03-09
It might be a driver problem or something, I will try an external mic as soon as I find one and it will be fine! I am too happy anyway that I can now here my music from my speakers...it makes a big difference!!!
thanks again for your time and patience!
Have a good one,

---

