---
title: "What version for a laptop, celeron processor 1GB  memory"
date: 2013-06-20
forum: New to Ubuntu
---

### Post by mr best buy on 2013-06-20
What version for a laptop, celeron processor 1 mb memory

So many versions to choose from

---

### Post by acimi66 on 2013-06-20
My vote would be for** Lubuntu**.

---

### Post by Iowan on 2013-06-20
> **mr best buy said:**
> What version for a laptop, celeron processor [COLOR="#FF0000"]1 mb[/COLOR] memory
Meg or gig?

---

### Post by ahallubuntu on 2013-06-20
~

---

### Post by VinDSL on 2013-06-20
> **acimi66 said:**
> My vote would be for** Lubuntu**.

Me, too (in the Canonical family).

Better yet, Peppermint OS (Lubuntu fork).

---

### Post by mr best buy on 2013-06-21
I installed it. It is fast.  I have a broadcom wireless on this computetr. Acer extensa 4620z.  
I tried the following command that worked for me in the past but it can not find the package now:
sudo apt-get update
sudo apt-get install firmware b43-install
It said it cannot find the package
I  am using a dynex  usb wireless  now, but I want the built in wireless to work like it did with  ubunutu.  Amy I forgetting something??

---

### Post by AndyOpie150 on 2013-06-21
Try asking wireless Question in the Networking and wireless sub-forum. There really good about getting broadcom wireless interfaces to work in Ubuntu distros.

PS: I have tried over 25 linux distros. Xubuntu is highly underated and the best overall for looks, and for low RAM machines like yours (mine started out with only 512MB, upgraded to the max possible for my processor: 1GB). Give it a look see. You can download onto a CD-RW (I use these so I can reuse them just by wiping with the Brasero utility). Move mouse to bottom of screen for the hidden app bar to appear.
The round clock and smaller round system monitors are called Conky Lua. This is is something I added to the desktop. If you like I can send you the files with an explanation of how to get working and how to edit all the colors.

---

### Post by Rob Sayer on 2013-06-22
When you went from ubuntu to lubuntu did you also install a newer ubuntu  version?  I went from kubuntu 12.04 to 13.04 on the netbook I'm typing  into here and the method I used to get the wireless working properly was  different.

Ditto on asking a wireless question in the wireless  section.  While I'm no expert, it would probably help to post the result  of this command in the terminal:

lspci -nnd 14e4:

... wrapping it in the code tags.  It'll say exactly what type of wireless adapter you have.  With this one it's a broadcom 4313 but there are actually several versions of it, which can be confusing.  That command will clear that up.

Actually I had far worse wireless problems on this machine in 12.04 than 13.04.

---

### Post by AndyOpie150 on 2013-06-22
One of the reasons I'm sticking to my 12.04 LTS. It seems all the 12.10's and 13.04's have issues. My 12.04 LTS just keeps rocking.

---

### Post by Rob Sayer on 2013-06-23
I have 12.04 on my bigger laptop, 13.04 on this netbook I'm using not.  12.04 did not work properly on it because the drivers for the video weren't properly integrated into the kernel in 12.04 or 12.10.

I also had a lot more problems on this machine with the wireless prior to 13.04.

Whether the lts works better than newer versions depends upon the individual case.  If the lts works fine on your hardware by all means use it.  But you won't get newer packages.  That can be a disadvantage.

---

