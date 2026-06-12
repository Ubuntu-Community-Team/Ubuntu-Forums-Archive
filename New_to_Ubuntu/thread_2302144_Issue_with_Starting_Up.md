---
title: "Issue with Starting Up"
date: 2015-11-08
forum: New to Ubuntu
---

### Post by Akul_Penugonda on 2015-11-08
Hi!

I just installed Ubuntu 15.10 off a live usb a couple of days ago. Yesterday I installed gnome-shell and then got an alert for updates. Upon rebooting after the updates, I get to a black screen with

```

fsck from util-linux 2.26.2 

/dev/sdb5: clean, 338599/2681728 files, 3928098/10727936 block

```

I used ctrl-alt-f1 to log in (thankfully that works) - I then tried to manually start gnome-shell but it says it cannot connect to display 0.

Starting unity also gives a similar error. I had some success by stopping the gdm service, then running startx, right click->open terminal, then gnome-shell. Clearly this is just a band-aid though - does anyone know what the problem could be?

Also I saw [http://ubuntuforums.org/showthread.php?t=2302067](http://ubuntuforums.org/showthread.php?t=2302067) - I think the problem is different, since at least they can get to the login screen.

---

### Post by Akul_Penugonda on 2015-11-08
Figured out the problem - I had only installed gnome-shell, not everything else. I ran "sudo apt-get install ubuntu-gnome-desktop" and that fixed my issue.
 
Also as a side note that created an issue where the Cantarell font got messed up, so text everywhere rendered as text instead of boxes - I had to do "sudo apt-get purge fonts-cantarell" then "sudo apt-get install fonts-cantarell" to fix that.

---

### Post by mörgæs on 2015-11-08
Good, please mark the thread solved using 'Thread Tools'.

---

