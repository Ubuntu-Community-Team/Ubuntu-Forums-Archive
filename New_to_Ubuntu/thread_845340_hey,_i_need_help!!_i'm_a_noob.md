---
title: "hey, i need help!! i'm a noob"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by geovanni_1 on 2008-06-30
heey people!!!! I just downloaded ubuntu hardy heron, but I have 2 questions...

1) I installed it from windows, and when I rebooted my system, windows vista doesnt appear on the GRUB menu.........
2) how do I enable, or configure desktop effects? I can't see the option in system ---> preferences

---

### Post by Canis familiaris on 2008-06-30
(1) Please post the output of:
gedit /boot/GRUB/menu.lst

(2) System->Preferences->Appearance and choose Visual Effects

---

### Post by sayakb on 2008-06-30
2. Open a terminal and type:
```
sudo apt-get install compizconfig-settings-manager
```
Now goto System->Preferences->Advanced desktop effects settings

---

### Post by pete-the-meat on 2008-06-30
If this is a WUBI install then surely it'll be a problem with the boot.ini file?

---

### Post by kansasnoob on 2008-06-30
> **pete-the-meat said:**
> If this is a WUBI install then surely it'll be a problem with the boot.ini file?

I tried a Wubi install when 8.04 was just an RC and I don't think ,if I recall correctly, that the Grub menu even shows up when you start/restart the computer.

I wonder if a more complete command (cut-n-paste version) would be helpful to see the op's menu lst. I'm reluctant to post code because I suck at it. I'm a gui guy!

But I wonder if I could get someone else to post the full command beginning with "sudo"?

I fear that the op may have let Gparted resize the Vista partition and I've had VERY, VERY bad luck doing that! It's much safer to use Vista's own partitioning tools to resize the Vista partition.

---

### Post by billgoldberg on 2008-06-30
I'm not familiar with WUBI.

For the second question, click the link call "ultimate guide to customizing ubuntu". It might come in handy, and covers the compiz fusion question.

--

If you need help, it could be a good idea to work with the people.

--

If you read this, make sure to post the outcome of the command in post 2.

---

### Post by hyper_ch on 2008-06-30
it is also adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

a generic topic title like "noob here" or "need help" does not help at all. As you may have notices, just about everyone posting in here has some kind of a problem or issue or question ;) 

and it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

---

### Post by pete-the-meat on 2008-06-30
Well as far as the boot-issue is concerned... Am I right in thinking that you installed Ubuntu from within Windows using the live CD (i.e. did you install it like other Windows software, so that it shows up on the list of installed programs)? Or did you have windows installed first? Either way you'll be using the Microsoft boot loader, unless you have changed to GRUB since. This, I guess, is the first piece of vital information to find.

---

