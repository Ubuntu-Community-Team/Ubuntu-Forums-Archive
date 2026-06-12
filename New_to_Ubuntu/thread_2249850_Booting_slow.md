---
title: "Booting slow"
date: 2014-10-25
forum: New to Ubuntu
---

### Post by rahul25 on 2014-10-25
[SOLVED] When I start my laptop the system takes about 15 minutes to load and when it loads the aspect ratio is very low so the icons are very large I am currently having ubuntu 14.04.my processor is core 2 duo and is having 2 gb ram and I don't know the graphics

---

### Post by Bucky Ball on 2014-10-25
Do you get to a menu screen where you can choose which kernel to boot when you start the machine? If not, hit shift after the manufacturers splash screen and it should come up.

Highlight the kernel you want to use and press 'e'. Find the line that ends in 'quiet splash' or any one or combination of those two words. 

At the end of that line, after 'quiet splash' and a space, add 'nomodeset'. I think it is then control+x to continue. The instructions are at the bottom of the screen. You want to save the changes and boot. 

Any different?

When posting please provide as much info as you can. What machine are you using? How much RAM? When it's loading is it a black screen?

The other thing to try is selecting the recovery kernel from the grub menu at boot. That will show you where it is stopping and hopefully why. Take note of where it stops all the way to when it gets to the desktop then report back. That will give more clues if 'nomodeset' doesn't work.

---

### Post by rahul25 on 2014-10-25
I did try pressing shift after the manufacturer logo but no luck, as for the second(aspect ratio)  problem  is solved by using xdiagonse

---

### Post by Bucky Ball on 2014-10-25
So, still 15 minutes to boot but the desktop looks ok when you get there? 

When you get to the Ubuntu desktop, open a terminal and:

```
 sudo nano /etc/default/grub
```

Find this line:

```

GRUB_TIMEOUT=0
```

... and change it to:

```

GRUB_TIMEOUT=10
```

Hit control+x, 'y', then, back in the terminal:

```

sudo update-grub
```

When finished, reboot and select the recovery kernel at the boot menu. 

PS: Please use [code] tags when posting code. Neater and easier to read. ;) (See last link in my signature for how.)

---

### Post by rahul25 on 2014-10-25
The desktop looks perfectly fine and when I ran the codes you gave it was showing that it is already 10

---

### Post by Bucky Ball on 2014-10-25
Do these lines look like this? If not, make it so:

```
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
```

Make sure there is a # at the beginning of the line 'GRUB_HIDDEN_TIMEOUT=0'.

---

### Post by vasa1 on 2014-10-25
What is the brand and model number of your laptop?

---

### Post by rahul25 on 2014-10-25
I don't know about the # but rest are the same but it will take me at least 15 minutes to do so, thank you for your help

---

### Post by Bucky Ball on 2014-10-25
That line I mentioned should be commented out with a # at the beginning of the line. That is probably what is hiding the grub menu.

---

### Post by rahul25 on 2014-10-25
It's wipro 7B1630

---

### Post by rahul25 on 2014-10-25
It is not having #,  should the one with 10 also have #????and how to save changes

---

### Post by Bucky Ball on 2014-10-25
No. Just make them look exactly like this:
```

GRUB_DEFAULT=0
**#** GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
```

Then control+x to exit and 'y' to save. The instructions for saving and exiting are at the bottom of the terminal screen.

GRUB_TIMEOUT=10 means the grub menu will stay up for 10 seconds at boot unless you change the selection. DON'T put a hash tag # in front of that line.

---

### Post by rahul25 on 2014-10-25
When I boot the screen with an _ remains for 15 minutes and I did edit the code even then I get no boot menu or such,  after time some codes come written quickly and the system loads

---

### Post by rahul25 on 2014-10-25
I have sorted out the 15 minute issue but the system is still slow as hell

---

### Post by oldfred on 2014-10-25
Are you running full Unity?

My old laptop with 1.5GB of RAM and an Intel chip from about 2006 just does not have enought horsepower for Unity. I do install Ubuntu, then then install fallback/flashback/gnome-panel which is a lot more lightweight. Other lighter weight options are Xubuntu or Lubuntu, but I prefer the Ubuntu set of applications. Plus I want laptop configured like Desktop which can run Unity but I do not.

       sudo apt-get install gnome-panel
On login screen click on logo/cog-wheel/star and choose 
[http://www.psychocats.net/ubuntu/classicgnome](http://www.psychocats.net/ubuntu/classicgnome)
12.04 LTS / Precise Classic (No effects) Tweaks and tricks kansasnoob & cortman
[https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)
[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370) 
[http://ubuntuforums.org/showthread.php?t=2090021](http://ubuntuforums.org/showthread.php?t=2090021)
[http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed](http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed)

---

