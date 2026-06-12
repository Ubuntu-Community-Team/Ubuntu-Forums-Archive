---
title: "[SOLVED] switch desktop sessions in terminal"
date: 2008-09-07
forum: New to Ubuntu
---

### Post by karlmp on 2008-09-07
how can i go to options-select session in terminal without GDM login window?

i disabled GDM login screen because of the error:"there already appears to be an X server running on display :0 should another display number by tried?"

is there a command that i can type to switch to LXDE and allow it just for the session?

---

### Post by karlmp on 2008-09-07
anyone?

---

### Post by karlmp on 2008-09-07
please?

---

### Post by schauerlich on 2008-09-07
Please wait between 24-48 hours before bumping your post.

---

### Post by drubin on 2008-09-07
You need to give it some time. Waiting less then 15minutes is a little impatient.

Reasons for no one answering:
1) They do not know the answer
2) They are investigating possible options.  


I would suggest waiting at least 24hours before bumping your post.

---

### Post by karlmp on 2008-09-07
:(

---

### Post by schauerlich on 2008-09-07
> **karlmp said:**
> :(

For more immediate help, you can go onto #ubuntu on irc.freenode.net. That channel tends to be pretty busy, but you will be able to interact with people in real time.

Ironic how this thread has been bumped 4 times telling someone not to bump too often...

---

### Post by drubin on 2008-09-07
> **karlmp said:**
> :(

This is not something to be upset about. Currently  there is no one that has any experience with your issue. If you wait some one should answer your question. 

I would suggest reading  the following in the mean time.
This is the forum FAQ's
[http://ubuntuforums.org/announcement.php?f=48](http://ubuntuforums.org/announcement.php?f=48)
This is in the stickies, maybe read the others as well.
[http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404)

---

### Post by dioltas on 2008-09-07
Maybe this will help :
[http://ubuntuforums.org/showthread.php?t=820355]("http://ubuntuforums.org/showthread.php?t=820355")

You want to get back the graphical login right?

How did you disable it in the first place? Did you uninstall GDM or change the default runlevel or what? 

If you just want gui for one session try logging in and typing startx or xinit.
Then type gdm maybe? As I said don't really hav time to look into it at the mo.

Longshot, but try pressing ctrl+alt+F7

---

### Post by karlmp on 2008-09-07
i disabled it following this:[http://ubuntuforums.org/showthread.php?t=8648&page=3](http://ubuntuforums.org/showthread.php?t=8648&page=3)

---

### Post by dioltas on 2008-09-07
ok so typing startx, or maybe 
"sudo /etc/init.d/gdm start" should start it again, only for that session.

If your having trouble with gdm, maybe install kde?
"sudo apt-get install kde" should do it. It'l probably automatically set it as your default destop manager when you install it tho.

What happens if you type "startx", and then either "gdm" or "/etc/init.d/gdm start"?
Do you want to re-enable the gui permantly or just for one session. If its just for one session that should work i think. If gdm is giving trouble maybe install fluxbox or xfce with apt-get.

Hope this helps,dont have time to try any of it out myself, doing some stuff for work at the mo.


EDIT: actually, logged in at a text based terminal,just typing "sudo /etc/init.d/gdm start" should give you a graphical login screen. Just reread the OP, you want to use LXDE, so if you have it installed maybe try typing ""sudo /etc/init.d/lxde start". If that dosn't work maybe it's there called something else. 

Try "ls /etc/init.d/" and see if you can spot something that might be it. Or else try just typing lxde or man lxde for info. I've never used lxde so I don't really know.

--------------------------------------------------------------------------------------------------------------------------

To change your default desktop manager try "sudo update-alternatives --config x-window-manager" and select lxde. Then when you type startx, that desktop manager should start for you i think.

If that dosn't work try editing /etc/X11/default-display-manager by typing
"pico /etc/X11/default-display-manager".

---

### Post by karlmp on 2008-09-08
i reinstalled GDM and now it seems to be fixed:)

---

