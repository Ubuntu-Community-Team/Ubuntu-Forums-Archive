---
title: "Remote Desktop control from XP systems."
date: 2012-09-14
forum: New to Ubuntu
---

### Post by ZombieWoof on 2012-09-14
I've searched the forum, and haven't found the answer(s) to my particular requirements.

I was given a laptop, which I upgraded with memory and installed Ubuntu (the last one  - what was that?  Perplexed Pangolin? Quixotic Quahog? ... nevermind).  I installed VLC, tested a USB wifi adapter, and tried out TightVNC, UltraVNC, and Teamviewer on the laptop as a headless music server.  This works for me, but I'm the geek.  The controlling systems are running XP.  I'm an Ubuntu noob, but have 38 years in computer service.

The hurdle is:
All of the remote desktop programs require something from the music server:  Either one must click an acceptance of the remote session dialog on the laptop desktop, or an access pass code from the laptop display.  If you have to touch the laptop to access the laptop remotely, why bother doing it remotely in the first place?

Also, I need to simplify the entire process down to just a couple of steps for my wife.  If I give her 7 or 8 steps to follow to access the music server, before she can choose her They Might Be Giants playlist, she'll just play it through her laptop with the tiny, tinny speakers.

So, is there a way in Linux to get remote desktop control with only one-ended authentication?  


Did this make any sense?


Thanks for your attention.

ZombieWoof

---

### Post by Epodx64 on 2012-09-14
you could try remmina 
sudo apt-get install remmina

> Remmina is a remote desktop connection client able to display and control a
remote desktop session.

It supports multiple network protocols in an integrated and consistant user
interface. Currently RDP, VNC, NX, XDMCP and SSH protocols are supported.

and there's always good ol' SSH from a terminal.

---

### Post by Gone fishing on 2012-09-14
Desktop Sharing will allow others to connect to your Machine from Windows etc the security section has > you must confirm access to this machine selected by default unselect it

---

### Post by megamister on 2012-09-14
I just shared the music folder on server using System-Config-Samba and any network computer can access the music. In Win Media player you can set up a library using the shared folders, no direct accessing the server needed. It's all done for you. In the Media player library you just see all your albums sitting there like they are on your own HDD.

---

### Post by ZombieWoof on 2012-09-15
> **megamister said:**
> I just shared the music folder on server using System-Config-Samba and any network computer can access the music. In Win Media player you can set up a library using the shared folders, no direct accessing the server needed. It's all done for you. In the Media player library you just see all your albums sitting there like they are on your own HDD.

It's not the file sharing I need to worry about.  It's remotely controlling the headless music server from my wife's XP laptop or my XP desktop.  (see attached)

I'm not sure the picture uploaded.  If not I'll try again.


ZW

---

### Post by ZombieWoof on 2012-09-15
[Epodx64]("http://ubuntuforums.org/member.php?u=1728792"),

Will try Remmiina.  Let you know.  I'm not sure about ssh to run VLC  will be simple enough for my wife.  That's the big hurdle.  Also if Remmina requires a access confirmation from the music server, it's no better use than what I've tried so far.

---

### Post by ZombieWoof on 2012-09-15
Gone,

I'll loook into that and post back.

Thanks,

ZW

---

### Post by ZombieWoof on 2012-09-15
> **Gone fishing said:**
> Desktop Sharing will allow others to connect to your Machine from Windows etc the security section has selected by default unselect it


That's what I'm talking about!

Thanks, [Gone fishing]("http://ubuntuforums.org/member.php?u=313801").

The next thing I need to know:

I set this all up under my original login.  I created another login that I would set for fewer permissions to keep the music server safe from accidental erasures.

When I try to access TightVNC while the music server is logged in as this secondary login, it actively refuses the connection.  I tried installing TightVNC while logged into the secondary login, but it says it's already installed.  The only .vnc directory I find is under my primary login's home directory.  Do I need to chmod the directory?  My noobness is showing.


Thanks,

ZW

---

### Post by Gone fishing on 2012-09-15
I think this is how.

On the second login you made no need to re-install but you will need to open Desktop sharing from that account and Allow other users to view your desktop.

Then in your account create a symlink to the files you want to share to the new account setting the permission to allow the other account to read but not change the files. Much of this can be done using nautilus ```
gksu nautilus
``` It might be quicker to use chmod and the -R switch (recursive) and permission 755 full for owner read other users

---

### Post by ZombieWoof on 2012-09-16
Will try after the Ravens game and report back.

Thanks ;)

ZW

---

