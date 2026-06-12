---
title: "2Gb Ipod Shuffle won't work with Amarok - Please help!"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by Radissthor on 2008-09-30
This is an old issue, I know. I posted this in another part of the forum but I got no answers.

I connect the Ipod to Amarok, it reads the songs. I can transfer songs to the Ipod perfectly. I eject the volume from the desktop and then when I press play, there are no songs in the Ipod. 

I swear I've read everything there is to read and I haven't been able to work it out. I have a 2GB Ipod Shuffle.

please, please... I need help!!

---

### Post by stoogiebuncho on 2008-09-30
I can't help you with Amarok, but I've found that gtkpod works pretty well with my ipod.

---

### Post by Radissthor on 2008-10-01
I have tried to install Gtkpod, but I get the following message:

Cannot install 'gtkpod-aac'

This application conflicts with other installed software. To install 'gtkpod-aac' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict.

What should I do?

---

### Post by SneakPeak on 2008-12-23
I have exactly the same problem with a 1GB shuffle.  I have posted a question here:

[http://ubuntuforums.org/showthread.php?p=6421879#post6421879](http://ubuntuforums.org/showthread.php?p=6421879#post6421879)

I have tried Songbird and I get the exact same problem.  I think Songbird uses gtkpod in the background to transfer songs to the iPod so I am not sure if gtkpod is going to solve your problem???

Songbird appears to have a very nice iPod interface but on my machine the quality of playback in Songbird is terrible and it doesn't solve my iPod problem so I am back to Amarok but I still can't play songs on my iPod.

Any help would be great

Sneaks

---

### Post by SneakPeak on 2008-12-23
Got my problem sorted see details in:

[http://ubuntuforums.org/showthread.php?t=1018986](http://ubuntuforums.org/showthread.php?t=1018986)

---

### Post by mrserious on 2009-01-09
I personally spent some hours finding out how to make use of my 2GB Shuffle in Linux. Using debian though, but I had the exact same problem. After you have uploaded the music to your ipod simply type this in bash:
mktunes -m /mnt/ipod/

when you are done:
umount /dev/sdb/
eject /dev/sdb/

If anyone needs a full guide i wrote one for that as well both for using it with amarok and pure-command which can be located [here]("http://solutionsandtips.blogspot.com/2009/01/using-2gb-ipod-shuffle-with-linux.html").

---

### Post by greenjumper on 2009-03-22
mrserious' guide worked a treat for me! Thanks!

---

