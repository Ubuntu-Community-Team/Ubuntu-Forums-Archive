---
title: "how do I log onto the terminal as superuser?"
date: 2014-03-10
forum: New to Ubuntu
---

### Post by gregg3 on 2014-03-10
That's it really. Thanks!

---

### Post by spectatorx on 2014-03-10
Type "su" and press enter, you will be prompted to enter password.

Or the second method is just to execute command as su:
sudo apt-get -f install

sudo stands for, if i'm correct, SuperUser DO, or something like this. With sudo you will be prompted to enter password as well.

---

### Post by oldos2er on 2014-03-10
```
sudo -i
``` is the preferred method on Ubuntu.

---

### Post by deadflowr on 2014-03-10
> **spectatorx said:**
> Type "su" and press enter, you will be prompted to enter password.

You can type su till the cows come home on Ubuntu, but nothing will happen since su needs the root password and Ubuntu has that locked and disabled.
So, you would have to make a password for root.

I'll second sudo -i, though.
sudo runs per command, but the -i option makes sudo run interactively.
To end the root session, simply type exit.

Best advice though, would be to forgo either option and run every instance with a simple sudo when needed.
Runing as root can have devastating consequences for the uninitiated.
(Power corrupts, and absolute power corrupts absolutely, leaving a file system owned by someone named george, and some files missing?/or broken)

---

### Post by QIII on 2014-03-10
Personally, I like to use sudo.

That way I'm reminded at each command that I am working under elevated privilege.

Use sudo -i, forget what you are doing, mess with some file and save it ... and you have permissions problems.

---

### Post by gregg3 on 2014-03-11
Just starting to get familiar with the terminology (sudo and sudo -i seem so similar!). An expert is helping me with something and that's the only reason I'm doing anything like this. Really appreciate all the warnings. Thanks much.

---

### Post by Lars Noodén on 2014-03-11
Programs that you will run in the terminal usually have a corresponding manual page.  At the very least, these pages cover what the options do.  Sometimes you get a well-written page that makes sense.  That's not always the case, some are better than others in quality but it's a good practice to get into skimming them for ideas.  You use the utility [man](http://manpages.ubuntu.com/manpages/saucy/en/man1/man.1.html) to view the pages.  For example,

```

man sudo

```

will tell you about the utility [sudo](http://manpages.ubuntu.com/manpages/saucy/en/man8/sudo.8.html).  They make more sense over time and, again, the quality does vary.

---

