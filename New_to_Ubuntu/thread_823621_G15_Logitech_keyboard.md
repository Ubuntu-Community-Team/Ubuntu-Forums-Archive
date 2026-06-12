---
title: "G15 Logitech keyboard"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by szaqlon on 2008-06-09
I have seen things written on this subject but nothing seems to work. What exactly is the secret to get the G keys to work. I have the LCD working, but the M keys are not lit up, and the first 12 G keys are duplicates of F1-12. I just need to be able to bind these keys to combinations, like ctrl-alt-F1. Just basically shortcut keys not macro keys. Once I can do that I can use those keys in games.

---

### Post by signseeker on 2008-06-09
Good question - one that I havent gotten around to asking yet. Will be watching this space with interest.

---

### Post by *malagant* on 2008-06-13
You can use g15macro ([http://sourceforge.net/project/showfiles.php?group_id=172261&package_id=196992](http://sourceforge.net/project/showfiles.php?group_id=172261&package_id=196992)) to remap the G-keys.

---

### Post by melrom on 2008-06-13
[http://www.g15tools.com/Welcome.html](http://www.g15tools.com/Welcome.html)

---

### Post by szaqlon on 2008-06-22
I have followed the instructions here: [https://help.ubuntu.com/community/LogitechG15](https://help.ubuntu.com/community/LogitechG15) and I have the lcd screen working, which is nice but my main concern is the Gkeys which do not. The only thing I wasn't able to do was add "ALL ALL= NOPASSWD: /usr/sbin/g15daemon" from sudo visudo. I can't seem to navigate or do anything with that. Could that be the problem and if so, how can I add that line?

---

### Post by BerrantRyke on 2008-10-05
```
export EDITOR=gedit && sudo -E visudo 
```

Will allow you to use gedit to edit the sudoers file.

And I'm pretty sure it will also check it for errors like just using visudo. Just be careful.

To emphasize:

```
**[COLOR="black"][COLOR="Red"][SIZE="5"]YOURUSERNAME[/SIZE][/COLOR][/COLOR]** ALL= NOPASSWD: /usr/local/sbin/g15daemon
```

I also read somewhere to use TAB after user, after NOPASSWD as well.

Good luck.. now If I could just add wait and repeat commands to my macros... :/

[Reference for the gedit code.]("http://bapoumba.wordpress.com/2008/05/07/edit-etcsudoers-with-gedit-in-ubuntu-hardy-heron/")

---

