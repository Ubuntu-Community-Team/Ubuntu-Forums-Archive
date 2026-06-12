---
title: "lubuntu 12.04 install problem"
date: 2012-08-03
forum: New to Ubuntu
---

### Post by linuxdude123 on 2012-08-03
ill give the background first..this is a 2003 compaq presario 2710us lap top...w/ 1.1ghz cpu.....1gb ram [maxed]...a netgear wpn511 wireless adapter....
ok ...ive tried puppy linux and it worked well from cd...but could not get the wi-fi working with it
so i heard lubuntu can support netgear stuff through a broadcom b43 driver and thats why im trying this
well in "trying out" mode i tried the install and it just wont connect....so i decided to fully install in case thats the issue
but heres how that went
1. language ..english
2.install window....continue
3.preparing install.....3 green checks....ive tried this with the boxes checked and unchecked and it still gets stuck after the next steps
4.type of install...ive tried along side other stuff and erase and install....still no difference
5.ive left the partition at 14gb-9gb....and on advanced it wanted the full 40gb hard drive..and gave it that......still gets stuck
6.english options again
7.name and passwords...tried auto and login options with no difference
8. after all that ...i get the desktop and the loading circle thing and thats where it stays for hrs on end...pls help...thanks

---

### Post by papibe on 2012-08-03
Hi linuxdude123.

I'm running Lubuntu on a similar machine: P3 with 256Mb of RAM.

A few thoughts:
[LIST]
[*]Since it is an old machine I would start by testing the RAM using Memtest86.
[*]My machine runs fine, but the installer uses more resources that OS itself, so I used the alternative CD for the installation.
[*]It is always a good idea to test if the CD was burned correctly (one of options on the main menu).
[/LIST]
Regards.

---

### Post by Rodney9 on 2012-08-03
Check MD5SUM for your CD/DVD

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Burn the discs at the slowest speed you can.

Try a different brand of cd.



For How-To's and Information on Lubuntu

[https://wiki.ubuntu.com/Lubuntu](https://wiki.ubuntu.com/Lubuntu)

For  Screen-Casts on Lubuntu

[http://blip.tv/rss/bookmarks/206798](http://blip.tv/rss/bookmarks/206798)

Rodney

---

### Post by linuxdude123 on 2012-08-03
i did the cd check thing and it came up good.....wheres memtest86...i tried it on RUN at the start menu....i cant see in system that i have 1gb ram..

---

### Post by papibe on 2012-08-03
You need a few tricks to get to 'Test Memory'. Read Solution #2 [here]("http://brainstorm.ubuntu.com/idea/25534/").

Regards.

---

### Post by ajgreeny on 2012-08-03
After booting the live CD/USB run the terminal command ```
sudo apt-get remove ubiquity-slideshow-lubuntu
```and then, still in the live system, try installing again.

There seems to be a bug in the slideshow that can make certain hardware crash and not continue with the installation.  Remove the slideshow from the live system and it may install fine. If that still does not work try using the Alternate-install-CD which uses a text installer; still very easy to use.

---

### Post by linuxdude123 on 2012-08-06
how do i get to terminal command?....at what point do i try this....BIOS on this machine is very skimpy...thanks

---

### Post by linuxdude123 on 2012-08-06
i found the test memory...it was right there under try and check cd ...etc....just clicked it on and its in blue screen testing away...ill tell you what it finds....

---

### Post by linuxdude123 on 2012-08-08
ok.....memtest86 passed with flying colors....

---

### Post by linuxdude123 on 2012-08-08
i tried the terminal command thing.....but it didnt recognize the "sudu" part.....any ideas?

---

### Post by ubudog on 2012-08-08
> **linuxdude123 said:**
> i tried the terminal command thing.....but it didnt recognize the "sudu" part.....any ideas?

Hi linuxdude123, be sure you are typing "sudo" and not "sudu".

Best,
ubudog

---

### Post by linuxdude123 on 2012-08-08
should i let it decide the partition or should i choose a custom?

---

### Post by linuxdude123 on 2012-08-08
sorry ...i meant sudo.....thats what i entered

---

### Post by linuxdude123 on 2012-08-08
well it took it this time...maybe i did screw it up.....ill reboot and see if it takes this time

---

### Post by edfast on 2012-10-30
> **ajgreeny said:**
> After booting the live CD/USB run the terminal command ```
sudo apt-get remove ubiquity-slideshow-lubuntu
```and then, still in the live system, try installing again.

There seems to be a bug in the slideshow that can make certain hardware crash and not continue with the installation.  Remove the slideshow from the live system and it may install fine. If that still does not work try using the Alternate-install-CD which uses a text installer; still very easy to use.@ajgreeny; I have been running lubuntu 10.04 successfully on a vintage Compaq Presario, and tried to upgrade to 12.04 in the past week-end. I tried just about every method and cheat and trick that I could come up with, but the install kept failing about one third in, or so it seemed. Only on reading your post did I realise that it always bombed at the beginning of the slideshow (why bother with a slideshow?) just as the second image was about to come up - proof again that we often cannot see the forest for all the trees. Now, thanks to ajgreeny, my computer is up and running like a charm. Kudos, thanks!

Happy Halloween!
H.

---

