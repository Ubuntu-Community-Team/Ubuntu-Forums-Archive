---
title: "How to uninstall vlsub extension?"
date: 2014-01-13
forum: New to Ubuntu
---

### Post by still_learning_to_ on 2014-01-13
I installed this extension to my vlc player, following these instructions: 
[http://www.webupd8.org/2012/02/vlsub-vlc-extension-to-search-and.html](http://www.webupd8.org/2012/02/vlsub-vlc-extension-to-search-and.html)

and now the vlc player doesn't work anymore, even though I uninstalled and reinstalled it again. The vlsub still shows up in the dropdown menu 'View' even though I actually even tried removing the whole folder (the 'vlc' part and what was in it) into which I moved the .lua file. What could I try?

Thank you for any help!

---

### Post by whitesmith on 2014-01-13
Try ```
sudo apt-get purge xyz
```This will remove the package you installed (xyz), including configuration files that may be your problem. Cheers!

---

### Post by still_learning_to_ on 2014-01-15
Thank you, didn't work though. Got this answer:

sudo apt-get purge vlsub
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package vlsub

I didn't install the extension in Terminal, and it doesn't show in the Ubuntu Software Center either.

---

### Post by still_learning_to_ on 2014-01-15
Or I did create the folder into whih I moved the .lua file in Terminal:
mkdir -p ~/.local/share/vlc/lua/extensions

---

### Post by Bucky Ball on 2014-01-15
No. You want:

sudo apt-get purge vlc

That should kill vlsub. Then install vlc again.

---

