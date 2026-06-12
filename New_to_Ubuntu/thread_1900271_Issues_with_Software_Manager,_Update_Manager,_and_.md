---
title: "Issues with Software Manager, Update Manager, and Ipod setup to Ubuntu :("
date: 2011-12-25
forum: New to Ubuntu
---

### Post by dyoungsays on 2011-12-25
I just joined, so hey everyone ):P

Anyways, I have a toshiba satellite laptop with Ubuntu linux installed. I just bought an ipod touch, and I can't download the needed wine software to get itunes to work because....
1) Update manager does not work? It pops up this message saying could not initialize....

'E: encountered a section with no package: header, E: Problem with MergeList/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages, E: The package lists or status file could not be parsed or opened.'

2) Ubuntu Software Center will not let me download anything. It pops up the first page, but won't let me search anything. It sits there with a swirly thing.

Please pardon my stupidity, I am good for Pontiac cars, not computers lol.

---

### Post by jtarin on 2011-12-25
Do you have a working internet connection? What is the specific package name? You might try a different server to download from if you have a working connection.

---

### Post by wildmanne39 on 2011-12-25
Hi, this should fix your software problem.
```
sudo rm /var/lib/apt/lists/* -vf
```
The first command will remove the damaged list and when you run the second command it will replace it with a new list.
```
sudo apt-get update
```
Thanks

---

### Post by dyoungsays on 2011-12-25
It can't be my connection because it has been working fine all night, it spotted out once or twice but quickly came back. It still isn't loading either of them. The update manager scares me the most because it wont even open.

---

### Post by Learning Linux 2011 on 2011-12-26
Open a terminal (Ctrl + Alt + T) or "Applications -> Accessories -> Terminal" and type:
```

sudo apt-get install wine

```Does that work?

---

### Post by dyoungsays on 2011-12-26
It keeps saying [sudo] password for young: but I keep trying to type my login security password and it isn't even typing it in.

---

### Post by oldos2er on 2011-12-26
Just type your password and press Enter, it's normal that nothing's echoed to the screen.

---

### Post by dyoungsays on 2011-12-26
YOu guys are great, thank you so much. It is doing its thing right now, I can't believe I didn't try actually typing it in! Thank you! Will update you when it is finished!:)

---

### Post by dyoungsays on 2011-12-26
It is updating, adding 284MB of updates! I really didn't want to pay $70 to get it looked at by the local computer guy. I can finally use my ipod once I download wine beta release and itunes for windows! I cant thank you enough!

---

### Post by oldos2er on 2011-12-26
Glad you got it going. Would you please mark the thread as 'Solved' (under Thread Tools) ? Thanks.

---

### Post by wildmanne39 on 2011-12-26
Hi, great to hear it worked.
Enjoy

---

### Post by dyoungsays on 2011-12-26
Everything worked out that they told me to do flawlessly, but it was a fault on my part somewhere I guess...

My ipod touch won't recognize the computer or itunes 10.5 for windows xp I installed using playonlinux. And when I tried to download wine (beta release) it said i must uninstall the wine program that my laptop came with when it was converted to Ubuntu. So I figured, hey I already have wine? Cool.

Tried it out, even has the wine glass logo saying itunes, and it is a white and black screwy version of itunes.

I give up, deleting all my itunes attempts. Just waiting until tax income money to buy a new laptop. This Toshiba is falling to pieces anyway lol. Guess my ipod will have to sit in its box until February, great... :/

---

### Post by wildmanne39 on 2011-12-26
Hi, if your computer has enough resources and you have a windows disk you can install windows in virtualbox in ubuntu and use itunes that way, here is a link so you can read about virtualbox.
[https://www.virtualbox.org/](https://www.virtualbox.org/)
Thanks

---

### Post by dyoungsays on 2011-12-26
I don't have a windows disc :( That's why we switched to Ubuntu when it crashed, plus linux can't really get viruses!

---

### Post by wildmanne39 on 2011-12-26
Hi, here is a thread that talks about all the options and if you scroll down far enough it talks about a linux replacement that works.
[http://www.psychocats.net/ubuntu/itunes](http://www.psychocats.net/ubuntu/itunes)
Thanks

---

### Post by dyoungsays on 2011-12-26
> **wildmanne39 said:**
> Hi, here is a thread that talks about all the options and if you scroll down far enough it talks about a linux replacement that works.
[http://www.psychocats.net/ubuntu/itunes](http://www.psychocats.net/ubuntu/itunes)
Thanks

I just give up. This ipod will need to be set up on the computer. Thanks for all your help though, I just don't understand this. 

Thank you.

---

### Post by wildmanne39 on 2011-12-26
Hi, your welcome!

---

### Post by calabashhh on 2011-12-28
I had the same problem and this seems to have worked. Thanks!

---

