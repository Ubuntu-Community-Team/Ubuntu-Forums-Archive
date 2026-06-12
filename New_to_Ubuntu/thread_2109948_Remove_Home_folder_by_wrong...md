---
title: "Remove Home folder by wrong.."
date: 2013-01-28
forum: New to Ubuntu
---

### Post by fairbird on 2013-01-28
I was made this command on terminal:
sudo rm -r /home/$uname
and i lose every things on home folder also all settings ... Any way to make restore same as windows system "System restore"
I using ubuntu 12.04..
Thank you

---

### Post by DuckHook on 2013-01-28
You've just deleted your whole home directory. I know that it's after the fact and you've already learned your lesson, but this is why I always advise new users to use the GUI file manager to delete files. Using *rm* in its many manifestations is just too arcane, powerful and dangerous for people not thoroughly familiar with the command line.

1. Did you back up your critical data prior to using such a powerful command? If you did, then you are in good shape with nothing to worry about. The easiest course of action now is probably to re-install your OS and your programs, and then simply copy your data back into your /home directory.

If you have a recent backup of your whole /home directory, this is even better. Just re-install your OS and apps, and restore your whole /home directory afterwards.

2. If you lost critical data files and must recover them, then *don't touch* the machine on which you deleted your /home directory. Any use will overwrite those critical files.

3. Read the following thread thoroughly before proceeding with downloads or recovery:

[http://ubuntuforums.org/showthread.php?t=1958605](http://ubuntuforums.org/showthread.php?t=1958605)

Especially pay attention to *oldfred*'s instructions.

4. It must be said and said again--you *MUST NOT* write anything to the disk you are trying to recover from. If you don't have an external USB drive, you will have to invest in one. Then follow the recovery instructions in the thread which will include downloading and burning CDs or USB keys. Downloads, burning, etc must be done from a different machine than the one you are trying to recover.

I can't help the morbid curiosity: just *what* were you trying to do??? It was very unwise to run such a command without knowing *exactly* what you are trying to achieve.

Good luck.

---

### Post by fairbird on 2013-01-29
Thank you...
No not really I have not made a backup never, and after i delete  mt home user by mistake I was made restart and my ubuntu returned back as like new install with same my user home but without any personal files and folders :(...i will read that topic what you given me and try to recover my files and folders..

---

