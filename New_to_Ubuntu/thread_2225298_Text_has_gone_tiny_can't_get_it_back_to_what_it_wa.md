---
title: "Text has gone tiny can't get it back to what it was"
date: 2014-05-20
forum: New to Ubuntu
---

### Post by paulravin on 2014-05-20
Hi, I have a growing list of problems with Ubuntu 14.04 on a HP split and a growing list of problems that are not consistent, sometimes they happen sometimes not.
 The latest is the headings / text on everything on the desktop are 1mm high. I have changed screen resolution with no change to the text size. Any idea how to fix this latest frustration?

---

### Post by paulravin on 2014-05-20
So I have found a text size increase option under System settings, universal access, large text on.
So any text in the operating system is now grandpa size, better than 1mm but it would be great the text back to where it was.
Any ideas?

---

### Post by deadflowr on 2014-05-20
What do you have the text scale factor set at now?
For the record, normal is 1.0.

---

### Post by sethj3 on 2014-05-20
There wasn't an Ubuntu 4.04. I'm guessing you mean 14.04?

What is the output of:  

```
gsettings get org.gnome.desktop.interface text-scaling-factor
```

---

### Post by paulravin on 2014-05-21
Yes 14.04

scaling-factor 1.25

Where can I change the size of the font?

---

### Post by grumblebum2 on 2014-05-21
Open system settings > screen display
and check the scale value for titlebar and menu.
Install unity-tweak-tool where you have a restore button for most customizations. Search "tweak" in the software centre.
or
install via terminal...
```
sudo apt-get install unity-tweak-tool
```

---

### Post by paulravin on 2014-05-29
Follow up on my multiple posts with all of the issues with this machine. I had about 6 problems with the HP pavilion split, 2 were solved, then the keyboard stopped working and HP refunded my cash. Go HP for customer support, they did not support using Ubuntu and also did not use it as an excuse for a keyboard that would not even work in Bios.  
 

 I have now bought an Acer Aspire V7-582p, it is listed as compatible with ubuntu, runs on live CD no problem. Loaded it up and no screen. So am now a week into trying to solve it via forums with no success, am now looking for tech support for it or lap top shop with pre loaded Ubuntu in Australia that is not double the cost. Sound easy? Try it. It is getting to the point of back to windows, never had issues like this in 4 years of using Ubuntu, 14.04 compatibility with laptops seems to have gone down hill big time!
 

 Motto of my experience:
 

 * Running live cd does not mean it will work on that machine after install. You are taking on a complete gamble.
 * Forum post that a machine works with Ubuntu does not mean it will for me. (I am not stupid with computers but I am not a programmer)
 * Finding payed help with Ubuntu is near non existent.
 * Buying a new Ubuntu pre loaded laptop is near non existent in Australia, I found one shop with computers at 2 x the price. Maybe that just is the price of something that works?

Follow up for posterity.
 

 Everything on this Acer V7 now works. It took me 1 week of half days, communication with _5 different tech support / linux savy people_, lots of trawling the web, posting messages etc to get the screen working.  
 

 Fixed now (by installing on Legacy not UEFI, see other post) just so releaved to not have to go back to the continual headache that is windows. Thank you Acer tech support, credit where credit is due, the guys at Acer 'out of scope' technical support (From Australia 1800 144 519) worked out why my screen would not work and how to fix it in 10 min. They charge $75 and it was worth every cent.  
 

 When trying to fix a HP I also found the best and fastest way to solve problems was HP tech support threats of warranty voiding bla bla but they fixed my computer issues where no one else could.

---

