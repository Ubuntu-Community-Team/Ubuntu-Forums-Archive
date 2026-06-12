---
title: "[SOLVED] Reverted from KDE to GNOME, but now no desktop."
date: 2008-06-19
forum: New to Ubuntu
---

### Post by svigeneris on 2008-06-19
Hi,

I'm running Ubuntu 8.04, and decided to install and try KDE, which I didn't like, and spent a lot of time running on GNOME instead. Thus, this morning I went on to uninstall kubuntu entirely, and everything was working as normal after the uninstallation. I have since rebooted my PC (and the orange ubuntu sign comes up instead of the blue kubuntu one), but instead of going into GNOME, I am just given a login line. After I login and supply password, I'm just given a terminal line (sort of like DOS, but linux terminal), and I cannot access my desktop.

Any idea how to bring back my GUI?

---

### Post by Joshua Netterfield on 2008-06-19
> **svigeneris said:**
> Hi,

I'm running Ubuntu 8.04, and decided to install and try KDE, which I didn't like, and spent a lot of time running on GNOME instead. Thus, this morning I went on to uninstall kubuntu entirely, and everything was working as normal after the uninstallation. I have since rebooted my PC (and the orange ubuntu sign comes up instead of the blue kubuntu one), but instead of going into GNOME, I am just given a login line. After I login and supply password, I'm just given a terminal line (sort of like DOS, but linux terminal), and I cannot access my desktop.

Any idea how to bring back my GUI?

try typing in
```
sudo apt-get install ubuntu-desktop
```
and rebooting.

Oh. Or maybe
```
sudo gdm
```

If the second one works, try
```
sudo apt-get purge gdm
```
and then reinstall ubuntu desktop (see above)

No promises...

---

### Post by Inxsible on 2008-06-19
Before you re-install ubuntu-desktop, you might just want to try ```
startx
``` at the command prompt. If that starts up Gnome and the GUI...you already have what's needed and gdm should pick up from there.


EDIT : Just to be sure....where do you enter the username and password? At the command line itself or in GDM - which gives you a gdm theme and asks you for your username and password?

---

### Post by svigeneris on 2008-06-19
I type in the username and pw in the command line itself. Is that ok? If I get the goahead, I'll try one of the above methods.

Thanks.

---

### Post by hovzio on 2008-06-19
> **Inxsible said:**
> Before you re-install ubuntu-desktop, you might just want to try ```
startx
``` at the command prompt. If that starts up Gnome and the GUI...you already have what's needed and gdm should pick up from there

I recommend trying  this one first

EDIT: I have also had success with:

startx -- :1

---

### Post by svigeneris on 2008-06-19
Thanks very much. I have, in fact, used the startx command, and it has loaded without problems. Many thanks to all.

---

### Post by Inxsible on 2008-06-19
> **svigeneris said:**
> Thanks very much. I have, in fact, used the startx command, and it has loaded without problems. Many thanks to all.Cool. Now try and reboot, just to make sure that you get the GDM this time...if not, you will have to make sure that the GDM is the one that fires up when you start the computer.

---

### Post by svigeneris on 2008-06-22
Hi again:

1. In a follow-up to the above posts, I've managed to start accessing my desktop using the startx command, however I would really like it to load automatically, instead of me having to log in and issue the startx command every time. Is there any package I need to reinstall for that to happen?

2. Also, since I'd installed KDE, everytime I try to shutdown the GNOME desktop (using red power button, top right corner) I am not given the option to shutdown, but instead to log out. It wasn't a problem before, because I used to shut down from the kubuntu log-in screen. Now, that has been uninstalled, so I am returned to the DOS-like command line, and I can't shut it down from there. How can I get the shut-down option back?

Thanks.

---

### Post by MasterSander on 2008-06-22
Try adding startx to the sessions. Perhaps this was removed when deleting the KDE desktop.

---

### Post by Troll_the_Great on 2008-06-22
You should remove and then install again gnome desktop.It worked for me, and I had an identical problem.When you start,enter your user name and password and then type:

sudo apt-get remove gdm

and then 

sudo apt-get install gdm

reboot

And your done.

Tell me if it worked.

---

### Post by svigeneris on 2008-06-22
Before I do this, can I ask:
Will it change any of my settings (apart from desktop settings)?
Will I need to reinstall any applications etc, or is it just the desktop which re-installs?

Thanks.

---

### Post by Troll_the_Great on 2008-06-22
From my experience, I didn't have to reinstall anything.The only thing I had to do was to reconfigure some small settings in compiz and that was all.But I'm not a linux guru, I just told you what I did and it worked for me.Cheers and good luck.

---

### Post by svigeneris on 2008-06-22
Thanks very much, I ran those commands and the system looks to be back to 'normal', no problems.

Thanks once again.

---

### Post by Troll_the_Great on 2008-06-22
No problem, glad I could help.Please mark your thread as solved so other with similar problems cold benefit.
By by!

---

