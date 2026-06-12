---
title: "Hardwarey Graphics Problems"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by ThePerm on 2008-07-01
I hope people don't mind me asking this here as it's more related to my hardware than specifically about Ubuntu but I don't really know any online communities as attractive for computing help as this one.

Also I've been using Ubuntu for a little while now so I have some basic experience of it but I still consider myself a major noob with it all so lamens terms would be appreciated.

So I've just ordered a brand new swanky computer to do swanky things on, I didn't have it come with an operating system already installed as they only offered Windows installations and I decided that I'd like Ubuntu on it.

Basically what happens is I turn on the computer, comes up with some text, fine, comes up with the ASUS or whatever it says flashy graphic logo thing while it's running it's POST checks BUT the graphic is all weird and gnarled, and then after that it shows a bunch of other text like it should but the text is all weird and with odd characters all over it, it's almost totally illegible. Though these weird graphics problems seem to be kinda situational 'cause sometimes I power it up and it's fine and everything looks tidy and other times it's not. And upon a time when the graphics were fine I went ahead and installed Ubuntu and everything was fine and dandy and even when the graphics are garbled I can still usually boot to Ubuntu (though with the occasional random error or XServer crash or sumpthin') and it's like the computer is running fine it's just what I see pretty much (though not totally, I know it's not my monitor 'cause of how there sometimes seems to be various booting problems) so I assume it's sumpthin' to do with the graphics card and I don't even know where to start and I don't wanna send it back to where I got it from 'cause I waited 2-3 weeks for it to get here in the first place and my alternative computer is Intel 500Mhz. >_>

Oh and while I'm at it I might as well add a couple Ubuntuish related questions.
If I was to try and make my computer dual-boot Windows and Ubuntu could I simply install Windows on a separate drive and GRUB would handle the rest or would Windows overwrite GRUB? Could I use SuperGRUB simply to fix that if it does?

And even simpler question, does Windows understand ext3?
If not is there software you can use with Windows to help it use a ext3 formatted drive?

My hardware is:

Processor - Intel Core2 Quad Q6600 (4 X 2.40GHz)
Memory - 8GB CORSAIR DOMINATOR (4x2GB)
Motherboard - ASUS P5K SE
Graphics - 1024MB GEFORCE 8800GT
Sound - Sound Blaster Audigy SE with 7.1 Surround Sound
DVD-ROM - 20x Dual Layer LightScribe DVD Writer ±R/±RW/RAM
HDDs - 1 SATA 80Gb HDD and 2 SATA 250Gb HDDs

Thanks in advance.

---

### Post by ET! on 2008-07-01
windows will not detect ext3 partition.... but you can make windows detect it by installing a software whose name i dont remember (google it)

---

### Post by alienexplorers on 2008-07-01
The program you need to read a ext3 partition from windows is called:
> ext2ifs
You can google that name to get the latest version which I think is 1.11....

Try going to this page for ext2ifs:
[http://www.fs-driver.org/]("http://www.fs-driver.org/")

---

### Post by ThePerm on 2008-07-01
Hrmmmm, well that's all well and good I guess but I still dunno why my graphics are being so buggy.

This is actually getting me down quite a bit, I'm a student so this was a BIG purchase for me. =(

---

### Post by markbuntu on 2008-07-01
Have you tried reseating the video card. Sometimes they come a bit loose in shipping and act really glitchy. We had this problem all the time in Alaska.

Turn off the computer, take the card completely out of the slot and put it firmly back in. Rest your arms on the case when you do this to prevent static electrical problem. Also, while you have the cover off, look for loose wires etc that may be touching something they should not be and check that everything else is plugged tightly in.

---

