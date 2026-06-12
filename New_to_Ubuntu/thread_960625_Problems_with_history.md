---
title: "Problems with history"
date: 2008-10-27
forum: New to Ubuntu
---

### Post by protargol on 2008-10-27
I have been getting some weird behavior when scrolling up through the history from a command line.  When I scroll up through the history (up arrow key) and reach a command that is more than 22 characters in length, it freezes those characters into the command line and continues scrolling after it.

For instance, here is what will be shown in order as I scroll up once, then again, and then scroll down in my history to the first item shown:
> ```
su
echo "vimdiff /etc/skel/.pr" | wc
echo "vimdiff /etc/sksu

```

When I scrolled through my history in this manner as root, I did not have the same problem so I'm wondering if I tinkered with something that may have messed this up (I have recently been updating my PC1 in various bashrc and profile files).  I thought I modified a file along the lines of bashrc.local, but can't seem to find it anymore so I'm not sure.  Thanks for any help.

---

### Post by protargol on 2008-10-28
bump

---

### Post by Bölvaður on 2008-10-28
I'm guessing this has it's origin in the program you use. The normal ubuntu terminal program is called gnome-terminal, but many other distros have even more than 1 or 2 terminal programs.

What I suggest is change the default settings in gnome-terminal if you changed the appearance.
If not, get Konsole or some other terminal program :)

---

### Post by dracayr on 2008-10-28
I recommend terminator (it doesn't support real transparency though)

dracayr

---

