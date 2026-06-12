---
title: "Ubunutu and APUs"
date: 2014-05-29
forum: New to Ubuntu
---

### Post by fbaerkir on 2014-05-29
Hi! I've been away from Linux for quite a while, and was never more than a beginner, really. But now I'm wanting to make a machine to handle home NAS duties, backups, potential for tinkering with PHP and server stuff, and, perhaps most importantly, to act as a client for the new Steam streaming feature from my more powerful Windows PC.
I ran a LAMP server, and it was great, but that was about eight years ago. At that time, Linux was very fiddly with graphics cards. For this new box, I'm considering one of those AMD CPU/GPU chips, specifically the AMD A8-5600K Trinity 3.6GHz. Largely because the machine is going to have a rang of duties that may evolve in the future.
So my question is, does Ubuntu play nicely with these chips, or does it have the same problems Linux used to (and may still, I really don't know) have with GPUs?
Thanks all.

---

### Post by Vladlenin5000 on 2014-05-29
It depends on what you really want it to do. For a general purpose server any current Ubuntu version supports that graphics card acceptably. There are also proprietary drivers that should work but I'm not really sure because I don't use ATI stuff...

---

### Post by zemega on 2014-05-30
I'm not sure if this helps you. But I have an ASUS 1225B, that use APU (I assume from the sticker at the laptop and the Asus Spec Page), it run 14.04 just fine. Multple monitors works fine.Usually, the recent guide is, if the parts you want to purchase are newer or released later than the kernel the OS is using, you might have problem getting it to run. If it was released before the kernel was released, it should work just fine. And newer parts are more Linux friendly this days.

---

### Post by mastablasta on 2014-05-30
server with GPU? strange...

still i think A8 is supported. but since it's an APU and you can't just replace the graphics card wouldn't it be better to use intel instead? the intel drivers are opensource. AMD though it's helping wiht opensource drivers they are not really as good as their closed source ones (this may change in the future). anyway as it is now if closed sourced driver support is dropped then you get stuck with opensource whic might not be that good.

---

### Post by fbaerkir on 2014-05-30
Excellent! Thanks all.
Yeah, it's an odd choice for a server part, but again, the machine's duties may change in the future, and one of its jobs will be for me to experiment with. Those chips are, in the grand scheme of things, pretty cheap, and certainly more so than having to buy a whole new chip if things do change. The bit about the drivers makes sense, and I can look into that now. I do remember drivers being one of the complications a few years ago.
One of the things that attracted me to the AMD part was that the mobo has an HDMI port that will let me stream games to the TV. But that's surely not the only option with that port, I just haven't looked farther yet.

---

### Post by fbaerkir on 2014-05-30
Oh, and also, thanks for noting that at least some of those AMD APUs do work! I'm not one of those guys who hates Intel, but given the choice I do like going with the underdog.

---

### Post by rahul4557 on 2014-05-31
Check this..
[http://www.phoronix.com/scan.php?page=article&item=amd_r9hawaii_linwin&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_r9hawaii_linwin&num=1)

AMD Catalyst Drivers has improved a lot now.
I am also not one of the guys who hates intel, but when it comes to Graphics i'd choose APU anytime(12 Computing Cores- 4 CPU & 8 GPU)..

---

### Post by zemega on 2014-06-01
HDMI?, thats good and common in connecting to TV. DisplayPort is better in chaining displays together. How about you consider DisplayLink monitors? Those monitors only need USB 3.0 for both power supply and data transfer (Or you can use USB 2.0 Y cable, the other end goes into pered USB hub). Either use your USB3.0 slot or get a PCI USB 3.0 card. And they have their own card/chip inside the monitor that will handle the processing.

---

