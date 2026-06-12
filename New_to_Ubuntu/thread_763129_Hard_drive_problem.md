---
title: "Hard drive problem"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by GreenfieldMark on 2008-04-22
So Ubuntu keeps telling me that I'm using up most of the space on my main hard drive, but when I use the disk usage analyzer the total only comes to about 4 gigabytes being used when I add everything up. However, at the top it still says I'm using most of the space just like everything else. The hard drive is about 19 GB by the way. 

So I can't for the life of me figure out where all the bloat is coming from and how to get rid of it. I'd be content to ignore it, except I think it's gotten to the point where it is actually slowing down my system. So if anyone has any idea what to do about this, I'd greatly appreciate the help.

---

### Post by mister_pink on 2008-04-22
Looked in trash folders? Also try doing a "sudo apt-get clean" to delete cached downloads.

---

### Post by GreenfieldMark on 2008-04-22
There's nothing in my trash folder, which I'm very meticulous about, and I don't think sudo apt-get clean did a whole lot. Any other ideas?

---

### Post by stevek123 on 2008-04-22
I'm a noob - so sorry if I'm not much help or am out of line here... but possibly a partition issue?

---

### Post by mister_pink on 2008-04-23
Try running the disk usage thing as root, it doesnt seem to always show files that you don't own. That could reveal whats using all the space up.
gksudo baobab

---

### Post by GreenfieldMark on 2008-04-23
Oh hey, that helped a lot. It turned out I had a lot of stuff in the /root/.Trash directory. Thanks for the tip.

---

