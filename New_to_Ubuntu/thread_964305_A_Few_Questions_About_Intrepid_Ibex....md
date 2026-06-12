---
title: "A Few Questions About Intrepid Ibex..."
date: 2008-10-30
forum: New to Ubuntu
---

### Post by skaldicpoet9 on 2008-10-30
Now that the new release is out I figure I'd give Ubuntu another spin. I've tried a few times to use Gutsy and Hardy with mixed results. My main problem has always been that I can't seem to figure out how to get my wireless working using Ubuntu. I've only been successful once and then never again. So, I was wondering if the wireless support for Intrepid is better then Hardy's or if there was an easy way for me to get my wireless up and running. My wireless card is a Broadcom 4310 if that helps. I also wanted to know if I should go with the 32bit or 64bit version. I have an AMD Turion 64 X2 running at 2.0ghz and 3.2gb of ram. Last time I used the 64bit version of Hardy and I kept wondering if it was really necessary and what the advantages/disadvantages of using the 64bit version is. Lastly, I was curious to know what the main difference between installing Ubuntu on Windows or creating a partition was (speed issues, inability to do certain tasks etc...). Anyways, I hope that someone can help me out so I can start enjoying Ubuntu :)

---

### Post by skaldicpoet9 on 2008-10-30
Now that the new release is out I figure I'd give Ubuntu another spin. I've tried a few times to use Gutsy and Hardy with mixed results. My main problem has always been that I can't seem to figure out how to get my wireless working using Ubuntu. I've only been successful once and then never again. So, I was wondering if the wireless support for Intrepid is better then Hardy's or if there was an easy way for me to get my wireless up and running. My wireless card is a Broadcom 4310 if that helps. I also wanted to know if I should go with the 32bit or 64bit version. I have an AMD Turion 64 X2 running at 2.0ghz and 3.2gb of ram. Last time I used the 64bit version of Hardy and I kept wondering if it was really necessary and what the advantages/disadvantages of using the 64bit version is. Lastly, I was curious to know what the main difference between installing Ubuntu on Windows or creating a partition was (speed issues, inability to do certain tasks etc...). Anyways, I hope that someone can help me out so I can start enjoying Ubuntu :)

---

### Post by nhasian on 2008-10-30
the new Ubuntu 8.10 has a lot more drivers for wireless devices.  I believe that includes some broadcom models.  Boot off the LiveCD and give it a whirl.  if it doesnt get set up automatically usually we can get it working with a bit of tweaking.

---

### Post by Crafty Kisses on 2008-10-30
From what I've read the wireless support is more widespread with Intrepid is a good thing. Intrepid is using a newer kernel and everything, so give your wireless card a shot.

---

### Post by lisati on 2008-10-30
One advantage of installing "within" Windows is that if something goes wrong and you need to re-install Ubuntu, the broken installation is fairly easily removed via Windows "add/remove programs" menu.

The advantage of the 64-bit version is that it can make better use of the capabilities of the processor. The catch is that it sometimes takes a little more work to find suitable drivers and plugins and then get them working.

One advantage of using the 32-bit version is that it works on 64-bit-capable machines.

---

### Post by eolson on 2008-10-30
Intrepid supports my laptop wireless with the restricted drivers with no problem.   It has some version of Broadcomm, but don't remember exactly which one.   On the desktop now so can't check.

---

### Post by logos34 on 2008-10-30
> **skaldicpoet9 said:**
>  what the advantages/disadvantages of using the 64bit version is. Lastly, I was curious to know what the main difference between installing Ubuntu on Windows or creating a partition was (speed issues, inability to do certain tasks etc...).

re x64, see [sticky in 64-bit forum]("http://ubuntuforums.org/showthread.php?t=765428")

Here's from the wubi wiki page:
> **Limitations** 
[LIST]
[*]Hibernation is not supported. [[1]]("http://en.wikipedia.org/wiki/Wubi_%28Ubuntu%29#cite_note-WubiFAQ-0")
[*]Wubi filesystem is more vulnerable to hard reboots (unplugging the power) than a normal filesystem.[[1]]("http://en.wikipedia.org/wiki/Wubi_%28Ubuntu%29#cite_note-WubiFAQ-0")
[*]Since Wubi installs Ubuntu on the same file partition as Windows, Ubuntu may see a slight degradation in performance over time due to [FAT32]("http://en.wikipedia.org/wiki/FAT32")/[NTFS]("http://en.wikipedia.org/wiki/NTFS") file [fragmentation]("http://en.wikipedia.org/wiki/Fragmentation"), which could be alleviated via [defragging]("http://en.wikipedia.org/wiki/Defragging") the disk.
[/LIST]


and links [here]("http://wubi-installer.org/")

---

### Post by eolson on 2008-10-30
For starters,  I'd use the 32 bit version.   A whole lot less gotchas.   When you are comfortable move to the 64 bit version.   That's one of the many  beauties of Linux,  Trying various versions doesn't cost you a thing.

---

### Post by overdrank on 2008-10-30
Threads merged :)

---

