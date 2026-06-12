---
title: "Installed Emerald and AWN, can't see either of my panels"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by Cossar on 2008-06-16
Hey, so I'm running 64bit ubunte. I installed and enabled Emerald, then I went through the AWN installation tutorial found [here.]("http://ubuntuforums.org/showthread.php?t=762363") I restarted after, and when it booted up I could neither see the top or bottom panels. I can't access any applications or adjust any preferences. What did I do wrong? How can I get back to where I was before I installed AWN and Emerald? 

Thanks alot guys, I appreciate you putting up with us noobs :)

---

### Post by kdm on 2008-06-16
> emerald --replace & disown

I just had the same problem and solved it by typing the above into terminal!

---

### Post by Cossar on 2008-06-16
thanks! how do I access terminal? cause I can't go to Applications -> accesories -> terminal...

---

### Post by Happy_Man on 2008-06-16
Try pressing alt-f2 and seeing if that works (it should pop up a box). If it does, go ahead and type what kdm said. If it does not, then press ctrl-alt-f3, log in to the text prompt, and then type ```
gnome-panel
```

---

