---
title: "Failing to disable sleep when lid closed"
date: 2014-10-05
forum: New to Ubuntu
---

### Post by doug21 on 2014-10-05
I've been trying to edit logind.conf as per [http://askubuntu.com/questions/363795/closing-laptop-lid-suspends-lubuntu-since-upgrade](http://askubuntu.com/questions/363795/closing-laptop-lid-suspends-lubuntu-since-upgrade) but when I save I get the message 'Can't open file to write'.  I assume this means I haven't opened the file as root (I certainly haven't been asked for my password).
 

 I've failed to understand any instructions for opening files as root.
 

 In this one I don't understand option 1, for option 2 I don't have 'nautilus-gksu' in my synaptic package manager, and when I follow option 3 I don't get the 'script' option in my menu after right clicking.
 [http://www.maketecheasier.com/ubuntu-easy-and-quick-ways-to-open-any-files-as-root/](http://www.maketecheasier.com/ubuntu-easy-and-quick-ways-to-open-any-files-as-root/)
 

 I've tried these instructions too but it made no difference.
 [http://www.noobslab.com/2014/04/add-open-as-rootadministrator-option-in.html](http://www.noobslab.com/2014/04/add-open-as-rootadministrator-option-in.html)
 

 Searching for answers seems to bring up mostly solutions for opening file managers as root.
 

 I'm not experienced with the terminal.
 

 Can you help me please?

---

### Post by yancek on 2014-10-05
I believe the default file manager for Lubuntu is 'Thunar' not nautilus which is the default in Ubuntu.  Ao sudo thunar, sudo su  and then thunar are possibilities.  I think the default text editor is 'leafpad' so sudo leafpad should open it and then you can navigate to the file you want to edit.

---

### Post by Paulgirardin on 2014-10-05
Terminal command: gksu thunar will open thunar as root

---

### Post by doug21 on 2014-10-05
I've done yancek's steps with leafpad (thanks both, I learned) and still get asked for a password.  I also did the steps in the 2nd answer for configuring the power manager here [http://askubuntu.com/questions/517581/lubuntu-14-04-how-to-avoid-lock-screen-on-closing-laptop-lid](http://askubuntu.com/questions/517581/lubuntu-14-04-how-to-avoid-lock-screen-on-closing-laptop-lid) and still get asked for a password.

Other ideas for getting rid of the password request?  Have double checked settings in power manager.

It has improved in that I was previously getting a lit black screen with a line of white text/ code at the top, and I don't get that any more.

Thanks.

---

### Post by doug21 on 2014-10-16
Solved.  With some surprising changes in settings.  In Power Manager the 'When laptop lid is closed' I had to change it from 'Do nothing' to 'Lock screen' and in Users and Groups I have to change Password setting to 'Not asked on login'.  Now closing the lid only makes the screen black, an audio file for example will continue to play.

---

