---
title: "gedit problems: unusable"
date: 2014-11-29
forum: New to Ubuntu
---

### Post by James_Hall on 2014-11-29
Dear Ubuntu Forums:

I love Ubuntu Unicorn but I have had one problem which maybe you can help.

It is with gedit and it is a problem that does not appear in any word processing program or web browser.

Everything when I open gedit starts fine.
Then charaters I type get delays and mixed up (I have tested this with slow clear typing).
Then the program crashes.

Sometimes when it does this before it has crashed, I do a CTRL-A to select all (attempting to be able to put it on the copy/paste board) but when I try to CTRL-C, nothing happens and then the program crashes and I lose the text I had.

Also, before gedit crashes, it slows the machine a lot.

I am now using medit, which works fine.

Do you know what is going on there with gedit?

Thanks, James

---

### Post by Bucky Ball on 2014-11-29
Welcome. Not using a straight Ubuntu install so unsure if gedit is installed by default. If it's not, how did you install it? Via the Software Centre?

---

### Post by James_Hall on 2014-11-29
I installed straight Ubuntu Utopic Unity 14.10 and it has gedit as the default basic text editor. No idea why a basic program like that gives trouble with text entry when more complicated ones do not......

---

### Post by mcduck on 2014-11-29
Try starting Gedit from a terminal, at least you have a chance of getting some useful error messages when it crashes. It's kind of hard to figure out what might be the problem without any details...

---

### Post by James_Hall on 2014-11-29
Thanks, I have gedit opened via terminal, and I'm typing and copying and all. It is already "gummy" in that it responds slowly and the screen there in the window flickers a bit. But I've not yet got mixed characters and it hasn't yet crashed....

---

### Post by Impavidus on 2014-11-29
I believe gedit supports plugins (I don't have gedit installed here). Maybe a plugin is acting up. If you have them, try disabling some.

---

### Post by mc4man on 2014-11-29
Starting gedit from a terminal usually may prove useless unless it's an immediate crash, like many gnome/gtk apps no debug messages are presented in a terminal by default.

If it does crash there should be an apport .crash file in /var/crash. If so then right click on > Open with report a problem 
Once that opens don't continue but click on 'Details' & see what it says.

---

