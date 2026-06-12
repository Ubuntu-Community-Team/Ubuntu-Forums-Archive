---
title: "HowTo: Remap Caps_Lock as Escape (Nice for Vim)"
date: 2006-09-23
forum: Outdated Tutorials &amp; Tips
---

### Post by incubus on 2006-09-23
I wanted to share something with you all.

**Background**
I'm a big fan of Vim's philosophy of avoid taking your hands out of their standard position on the keyboard. In my experience, this saves time and provides comfort. Ironically, one of Vim's main keys goes against this principle: you have to lift your left hand to reach Escape (at least I do).

**Idea**
Since I don't use Caps Lock, not even when I have to write SQL statements (I always use the Shift key), I thought I could put it to some good use. Specifically, I decided to map Caps Lock as Escape. Note that I decided not to swap them, at least for now. I know my left hand will subconsciously try to reach Escape, so I'm going for a smooth transition.

In Ubuntu we can tweak this at the Xserver level, so it will work independently of desktop environment (as far as I know). The magic command for mapping keys and buttons is 'xmodmap'. See its man entry for more details, it's very easy to follow.

**Recipe**
Open up your favorite editor and create the file:
~/.xmodmap
```

!Remap Caps_Lock as Escape
remove Lock = Caps_Lock
keysym Caps_Lock = Escape

```

Now you just have to load that file:
$ xmodmap ~/.xmodmap

You have to do something to have your file loaded everytime you log in. In KDE, you can create the following script: 
~/.kde/Autostart/capslock.sh
```

#!/bin/sh
xmodmap ~/.xmodmap

```

Remember to make it executable:
$ chmod u+x ~/.kde/Autostart/capslock.sh

Please, let me know how you do this in Gnome and XFCE and I will update this entry.

**Discussion**
Note that this is not a new idea (although I had it by myself). After writing this HowTo, I googled and found this nice page. It teaches how to swap Caps_Lock and Escape:
[http://www.vim.org/tips/tip.php?tip_id=166](http://www.vim.org/tips/tip.php?tip_id=166)

Also note that you can regard this as a general tip. You can remap any key to anything else, for the most part. Use 'xev' to learn the key names. I've seen some people mapping Caps_Lock as the Control key. Again, the man page is very helpful.

I hope this helps somebody. : )

Best,
incubus

<caps_lock> :wq

---

### Post by tr333 on 2008-01-23
If you create the ~/.Xmodmap file when using GNOME, you will be asked whether you want to load the Xmodmap file when you login to the system.  There is no need to tell the system to load the file on login as this will happen automatically, as long as the file is called ~/.Xmodmap.

---

