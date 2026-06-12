---
title: "ubuntu login Problem!!! ---SOS---"
date: 2008-10-10
forum: New to Ubuntu
---

### Post by jackgu1988 on 2008-10-10
i have the beta version of ubuntu 8.10 and i tried setting up compiz (following a tutorial i found on the internet) by going to the system-->preferences-->sessions and adding the command emerald --replace and since then i can't move the mouse and the keyboard when i log in and the only thing i can use is a virtual terminal! i also have a live cd of ubuntu 8.04.1 if this can help... please help me fix this because i am in panic!:(:(:(:(:(:(:(:( tnx!

---

### Post by hyper_ch on 2008-10-10
It is advised to use a descriptive topic title; that means use a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have notices, just about everyone posting in here has some kind of a problem or issue or question

Just imagine what these forums would look like if everybody would just post "Help" or "Noob here". What do you think how many people will still look at such threads?

Furthermore, for unrelated questions it's also adviced to open a seperate thread for each one, so that each problem can be addressed (and eventually marked as solved) individually.

---

### Post by jackgu1988 on 2008-10-10
sorry but i couldn't think of anything better... i changed it and now looks better but this is still not the exact problem...

---

### Post by darrenm on 2008-10-10
It's this [http://ubuntuforums.org/showthread.php?t=943370&page=2](http://ubuntuforums.org/showthread.php?t=943370&page=2) 

Thats the problems that come with running beta's! Its caught me out too.

---

### Post by Orange_and_Green on 2008-10-10
Hi. have you tried booting in safe graphics mode? (The second option you are given in the GRUB menu).

From there you can:

1)Resume bot normally
or
2)Go from a text-based login,

whichever works for you.

In any of these cases, you need to locate a directory called /home/YOUR_LOGIN/.config/autostart.
That is where the session shortcuts are located. Just delete the one you created for emerald, then reboot.

Examples:
case 1) Places->Computer; double-click /home; double-click the folder that corresponds to your name; CTRL+H to show hidden files; double-click .config; double-click autostart; delete the link you want to remove from autostart.
case 2)```
cd /home/INSERT_YOUR_LOGIN_HERE/.config/autostart
ls
.....
rm emerald.desktop
```
(Instead of "emerald.desktop", type the file that ls gives you)

AFAIK emerald is a discontinued project (after being merged with compiz) and you activate the effects by:
1)Installing a video driver that supports hardware acceleration
2)System->Appearance->Effects.


Good luck

---

### Post by jackgu1988 on 2008-10-10
thank you all!

---

### Post by jackgu1988 on 2008-10-10
actually i am still from a live cd... maybe i need some updates...

---

### Post by Orange_and_Green on 2008-10-10
Ok. Please post the output of
```
sudo fdisk -l
```

---

### Post by Orange_and_Green on 2008-10-10
Sorry, gotta go now... I'll give you the instructions in a nutshell.

sudo fdisk -l will give you a list of your disk's partitions. They should be entries like /dev/sda1, /dev/sda2, /dev/sdb1 etc.

You need to make sure which one corresponds to the partition of your home directory. To do this, you must mount them from the live cd and inspect their contents. So, for every entry you get from fdisk, do:

```
mkdir partition1
sudo mount /dev/sda1 partition1
ls partiton1
```

And see if you get an entry called "/home". If you do, then sda1 is your "home" partition. if not, try with /dev/sda2 and so on.

Suppose you get the "home" entry after three steps (that is, after mounting /dev/sda3 on "partition3").

Now do:
```
cd partition3
cd home/YOUR_LOGIN/.config/autostart
ls
```

and delete the emerald entry like I explained above.
The others will surely help you from here on. I wish you the very very best of luck :KS

---

### Post by jackgu1988 on 2008-10-10
tnx again!

---

