---
title: "Brightness not changing"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by BOMEz on 2008-06-09
I'm having issues with using the FN keys on my Dell Inspiron 1501 with brightness. Volume controls work just fine using the FN key shortcuts, but brightness just kind of sticks. Whether I hit the keys for brightness to go up or down, the indicator which shows up on screen moves one notch, then goes back to where it originally was, and I see no change in my screens brightness.

I've read [this]("http://ubuntuforums.org/showthread.php?t=743329") post and followed the instructions on it, in addition to changing a few settings in my gconf-editor (which I found in another post, but can't find again since Ubuntu crashed on me...but thats for another post..). 

Could someone kindly offer some insight into this matte?

---

### Post by cariboo on 2008-06-09
Did you try out what it suggested in the last post of the thread. Adding blacklist video to /etc/modprobe.d/blacklist? You can edit blacklist using gedit:

```
sudo gedit /etc/modprobe.d/blacklist
```

Just add **blacklist video** to the bottom of the list and save. You will probably have to restart your computer for it to take effect.

Jim

---

### Post by BOMEz on 2008-06-09
Yeah, I did that but to no avail. Its still doing the same thing.

---

### Post by BOMEz on 2008-06-11
any other suggestions anyone?
*bump

---

### Post by aktiwers on 2008-06-11
Does it change if you type this in terminal?:

```
xgamma -gamma 1.5
```

You can change the number 1.5 to anything between 0 and 10 (or more if you like)

---

### Post by BOMEz on 2008-06-12
Yes it does change, but it seems a bit more ...whiter on screen, not brighter.

---

### Post by RSingh on 2008-06-12
Try adding the brightness applet to panel and using it.

Right click on the top panel and add to panel: brightness applet.

---

### Post by BOMEz on 2008-06-16
I tried adding it, but nothing changed.

---

