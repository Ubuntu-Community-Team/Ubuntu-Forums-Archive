---
title: "Wrong Keyboard Layout"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by skymera on 2008-06-20
Hi

I've selected United Kingdom and Dell keyboard from the keyboard options yet it's still not the right layout. or not workign right.

All the keys are jumbled up, any idea how to fix?

---

### Post by Qrikko on 2008-06-20
$> gnome-keyboard-properties

should give you the interface to set up your keyboard :)

check if it is correct when you do, I for example had to use Finnish keyboard (I am Swedish) for a long while before it was "correct" so easiest I think is to use that and find something that work better :)

Hope it can help you.

---

### Post by skymera on 2008-06-20
I used that, United Kingdom is selected which is correct but all symbols are mixed around.

---

### Post by skymera on 2008-06-22
Reconfigured Xorg and selected GB, selected UK as my layout and still not right :(

---

### Post by Troll_the_Great on 2008-06-22
What do you mean "Don't feed the trolls!" Do you have something against trolls?Are you a troll hater?:lolflag::lolflag::lolflag:

---

### Post by rockerphil on 2008-06-22
i'm a bit more command line oriented, so this is what i'd do. in terminal run this:


sudo dpkg-reconfigure xserver-xorg

it'll have an option to select your keyboard layout, but it should auto-detect it. hope it helps

---

### Post by skymera on 2008-06-22
> **Troll_the_Great said:**
> What do you mean "Don't feed the trolls!" Do you have something against trolls?Are you a troll hater?:lolflag::lolflag::lolflag:

I was called a troll for saying i liked Dream Linux.

---

### Post by Troll_the_Great on 2008-06-22
Why?What is dream linux?By the way, my nickname comes form the Norse mythology, I'm not an internet troll.

---

### Post by skymera on 2008-06-23
Ok Dream Linux is just another distro based on Debian.

Anyone know about the keyboard solution?

---

### Post by markbuntu on 2008-06-23
You can get keytouch and keytouch editor and make your own custom keyboard configuration. 

A lot of those manufacturer keyboard things are wrong or for only one patricular keyboard which is most likely not yours. The manufacturers change keyboards and layouts all the time, even within the same model and don't really tell anyone.

---

### Post by sydbat on 2008-06-23
System > Preferences > Keyboard > Layout tab.

---

### Post by OliW on 2010-03-12
Did you ever fix this? My keyboard is set as UK everywhere but as of 10 minutes ago, it's behaving like a US keyboard.

It's a shame that nobody read your posts (and saw what you had tried) but I've also reconfigured xserver and used the gnome tool.

Edit: Turns out I overlooked the fact I installed kernel 2.6.24 (yeah, barely RC2 and fully of buggage). My bad.

---

