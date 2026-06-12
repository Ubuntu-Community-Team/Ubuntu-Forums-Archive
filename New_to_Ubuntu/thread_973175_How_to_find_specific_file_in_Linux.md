---
title: "How to find specific file in Linux"
date: 2008-11-06
forum: New to Ubuntu
---

### Post by Lakeside on 2008-11-06
I am trying to find the `php.ini` file that, apparently is causing some problems for my Joomla install, but that people say is either in my  `root``(I think var/www in my case)  or public_html  I have looked there scanning through the folders/files,  using `search` in file browser, using tracker tool..just can`t find it.  Can someone kindly tell me if there is a way in Hardy Heron (linux in general) maybe using the terminal command, somehow to find it? I am going crazy](*,) thanks

---

### Post by drs305 on 2008-11-06
```

sudo find / -type f -iname php.ini
```

If that doesn't find it, use *php*

Added: When you find the file, by whatever method presented in this thread, please mark it 'Solved' via the *Thread Tools* link.

---

### Post by philinux on 2008-11-06
In a terminal use 

locate filename

---

### Post by Lakeside on 2008-11-06
You guys are too quick! Was just about to delete this as I found a way :) Thanks, now I have two other ways to try.  I just used sudo find / -name 'php.ini' (and yes, you do need the quotes around the filename, I didn`t at first, and it goes crazy!  I`m glad I found it, that php.ini file is driving me crazy...whoa, locate filename dug up a few more than the others!  *edit* Just tried the find / -name "php.ini" again even without the quotes), and it was fine unless I forgot to use the `sudo` command in front, guess that was really my problem before.

---

### Post by philinux on 2008-11-06
You can also use the wildcard like this

locate *.ini

etc

---

### Post by Lakeside on 2008-11-06
Ahh, thanks philinux, is helpful to know too.

---

