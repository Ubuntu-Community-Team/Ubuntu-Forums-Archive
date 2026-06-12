---
title: "Natty. How do I change the hostname of my PC?"
date: 2012-03-11
forum: New to Ubuntu
---

### Post by GiuHei3u on 2012-03-11
Is there a way I can change the hostname of my pc without having to reinstall?

thanks

---

### Post by Krytarik on 2012-03-11
Please see the first part of this guide:

[http://www.tuxgarage.com/2012/02/change-command-prompt-in-ubuntu.html](http://www.tuxgarage.com/2012/02/change-command-prompt-in-ubuntu.html)

Regards.

---

### Post by GiuHei3u on 2012-03-11
> **Krytarik said:**
> Please see the first part of this guide:

[http://www.tuxgarage.com/2012/02/change-command-prompt-in-ubuntu.html](http://www.tuxgarage.com/2012/02/change-command-prompt-in-ubuntu.html)

Regards.

Thanks. I am still doing something incorrectly. I brought up a terminal and typed the command in the one terminal. Had to put my password in and upon entering the command I get this .....

(gedit:5511): Gtk-WARNING **: cannot open display: :0.0

But I only did the first command on the one terminal. Not sure how to do the second at the same time.

---

### Post by Krytarik on 2012-03-11
> **gumshoegrant said:**
> **I brought up a terminal** and typed the command in the one terminal. ... I get this .....

(gedit:5511): Gtk-WARNING **: **cannot open display: :0.0**
It seems you rather mean, "I switched to the console/tty". :P

Are you even using a desktop environment? If yes, press Ctrl+Alt+T to *really* "bring up a terminal".

Or, if you are running a server version, just replace "gksudo gedit" with "sudo nano".

---

### Post by GiuHei3u on 2012-03-11
I brought up the terminal by CTRL, ALT, and T and typed 

gksudo gedit /etc/hostname [and my hostname] 

Now the hostname I chose is shown in the folder Hostname but not in Hosts.

Now my prompt is showing the new hostname. And not sure how that happened quite honestly but  would like to eliminate the hostname altogether. I did reboot.

---

### Post by ajgreeny on 2012-03-11
I suspect you may have used Ctrl+Alt+F1 to get a "terminal" (command line interface) and doing it that way, you will not be able to open gedit, as it needs the gui (gnome).

From your normal gnome or unity desktop just open a gnome-terminal (Ctrl+Alt+T) to run the commands one by one to change the current name to the new one in each file that will open.  Now reboot and you should see the new hostname.

---

### Post by GiuHei3u on 2012-03-11
> **ajgreeny said:**
> I suspect you may have used Ctrl+Alt+F1 to get a "terminal" (command line interface) and doing it that way, you will not be able to open gedit, as it needs the gui (gnome).

From your normal gnome or unity desktop just open a gnome-terminal (Ctrl+Alt+T) to run the commands one by one to change the current name to the new one in each file that will open.  Now reboot and you should see the new hostname.

Did as you stated , ctl,alt, T not f1 and put those two commands in for the folders hostname and hosts and deleted the hostname in both folders, saved, and rebooted.

Now I cannot bring up a terminal when I do a ctrl, alt, T

I can bring up a terminal by doing ctrl alt and any of the 6 F keys.

How do I get back my ctrl alt T terminal? and now my prompt using ctrl alt F1 is now..

john@linux:~$

thanks

---

### Post by GiuHei3u on 2012-03-11
By the way, that prompt name is not what i wanted or typed! No idea where the "linux" came from.

All I wanted was John@~$

thanks again.

---

### Post by ajgreeny on 2012-03-11
> **gumshoegrant said:**
> Did as you stated , ctl,alt, T not f1 and put those two commands in for the folders hostname and hosts and deleted the hostname in both folders, saved, and rebooted.

Now I cannot bring up a terminal when I do a ctrl, alt, T

I can bring up a terminal by doing ctrl alt and any of the 6 F keys.

How do I get back my ctrl alt T terminal? and now my prompt using ctrl alt F1 is now..

john@linux:~$

thanks
You should have changed to old hostname to the new one, not just deleted the old one, which may be why you now get the hostname linux, so re-edit those two files back to what they were.

I don't think it is possible to run without a hostname, though I may be wrong about that.  You can, however remove it from the terminal prompt by removing the **/h** (shown in red below) from the two lines as shown in the link that are something like
> if [ "$color_prompt" = yes ]; then     PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ ' else     PS1='${debian_chroot:+($debian_chroot)}\u@[COLOR=Red]\h[/COLOR]:\w\$ '     
fi unset color_prompt force_color_prompt  # If this is an xterm set the title to user@host:dir case "$TERM" in xterm*|rxvt*)     PS1="\[\e]0;${debian_chroot:+($debian_chroot)}\u@[COLOR=Red]\h[/COLOR]: \w\a\]$PS1" in .bashrc file in your /home. Make a backup first in case you do something wrong.

---

### Post by GiuHei3u on 2012-03-11
> **ajgreeny said:**
> You should have changed to old hostname to the new one, not just deleted the old one, which may be why you now get the hostname linux, so re-edit those two files back to what they were.

I don't think it is possible to run without a hostname, though I may be wrong about that.  You can, however not show it in the terminal prompt by removing the **/h** from the two lines as shown in the link, in .bashrc file in your /home. Make a backup first in case you do something wrong.

Well something has gone wrong since I now cannot edit it to put any hostname in those two folders. At this point I am not concerned about having a hostname in the prompt but to get my CTRL, ALT, T working again so I can go in and edit the hostname to what they were prior to this. 

Any suggestions?

---

### Post by matt_symes on 2012-03-11
Hi

I have just answered on the other thread you created. 

You should really only create one thread for each support question, but as you are new you may not have known.

EDIT: Thought i would add the link.

[http://ubuntuforums.org/showthread.php?t=1939453](http://ubuntuforums.org/showthread.php?t=1939453)

Kind regards

---

### Post by ajgreeny on 2012-03-11
> **gumshoegrant said:**
> Well something has gone wrong since I now cannot edit it to put any hostname in those two folders. At this point I am not concerned about having a hostname in the prompt but to get my CTRL, ALT, T working again so I can go in and edit the hostname to what they were prior to this. 

Any suggestions?
You may need to boot to recovery mode, which gives you root permissions, and edit the files this time using nano.

I have never seen a similar situation so am totally unaware whether or not removing the hostname from both those two files would stop Ctrl+Alt+T opening a gnome-terminal.

What happens when you use those **gksudo gedit** commands and try to edit either file?  You are using the **gksudo** prefix, aren't you?

PS:  Why did you want to do all this in the first place?

---

