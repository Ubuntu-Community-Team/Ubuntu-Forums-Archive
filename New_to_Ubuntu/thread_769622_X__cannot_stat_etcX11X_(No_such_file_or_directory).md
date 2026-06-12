---
title: "X:  cannot stat /etc/X11/X (No such file or directory)"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by angrmgmt on 2008-04-26
What on Earth does this mean?  In school (5 years ago), we had our RedHat distro up and running and got into X within minutes of installing it... what is wrong with Ubuntu that makes it fail to do so?

When typing the oh-so-simple command of "startx", we get the lovely error message contained in the title, indicating that there is no such file or directory, that the connection was refused (errno 111), that there is no such process (errno 3), and some other random error about a locking authority file.

Isn't linux supposed to be getting easier to use?  I could have had this file server up and running on M$ windows server 2k3 hours upon hours ago, and the only things I find about this in the forums (after searching for nearly 2 hours) are about upgrading from one version to another or installing new drivers... This is an initial install!!!  Help please!

I will likely be checking this post for about the next 2 hours or so, then I'll likely move to a server platform that I know will actually work - good old M$ server 2k3.

---

### Post by FuturePilot on 2008-04-26
Did you by chance install the server edition? If so, startx won't work because the server edition does not come with a graphical environment.
If you want a graphical environment I would suggest XFCE for a server.

```
sudo apt-get install xubuntu-desktop
```

---

### Post by LaRoza on 2008-04-26
> **angrmgmt said:**
> 
Isn't linux supposed to be getting easier to use?  I could have had this file server up and running on M$ windows server 2k3 hours upon hours ago, and the only things I find about this in the forums (after searching for nearly 2 hours) are about upgrading from one version to another or installing new drivers... This is an initial install!!!  Help please!

I will likely be checking this post for about the next 2 hours or so, then I'll likely move to a server platform that I know will actually work - good old M$ server 2k3.

Don't try to start flames, Windows has nothing to do with this problem.

Servers don't have GUI's, even MS is changing their ways.

---

### Post by angrmgmt on 2008-04-26
> **FuturePilot said:**
> Did you by chance install the server edition? If so, startx won't work because the server edition does not come with a graphical environment.
If you want a graphical environment I would suggest XFCE for a server.

```
sudo apt-get install xubuntu-desktop
```

This command gives me "E: Couldn't find package xubuntu-desktop"

As for no GUI - feh.  Maybe I'm just spoiled, but command line seems to remind me of being in fourth grade and typing "dazzle.exe" at a DOS prompt to watch pretty colors and writing autoexec.bat scripts to give me menus etc.  I figured that pretty much any distro of Ubuntu would give me the ability to be comfortable using it right away, but you say the server distro doesn't come with a GUI.  If that's the case (and I'm pretty sure I did download the server version) then thanks for the help (no srsly, I mean it), and I'll be moving along.

---

### Post by angrmgmt on 2008-04-26
> **LaRoza said:**
> Don't try to start flames, Windows has nothing to do with this problem.

Servers don't have GUI's, even MS is changing their ways.

Bro (or Bra) - not trying to start flames, but daaaaaaang it's frustrating to scour forums for hours and find nothing helpful already posted about my issue - especially when the software in question is supposed to have a super-helpful and robust support community.  Check out the poster above you - there's an example of what I mean by "super-helpful".

By the way, Server 2k3 has a GUI.  Just an FYI.

Anyway, I won't bug you folks anymore - enjoy.

---

### Post by LaRoza on 2008-04-26
> **angrmgmt said:**
> 
By the way, Server 2k3 has a GUI.  Just an FYI.

Anyway, I won't bug you folks anymore - enjoy.

I know it does.

Ubuntu Server doesn't have a GUI like all but MS servers. If you want to install one you can. 

Yes, the poster above was helpful. That would have installed a GUI for you that is quite modern.

If you want a server and GUI, I suggest installing the desktop version of Ubuntu (or Xubuntu, or Kubuntu) and running this command:

```

sudo tasksel

```

Select LAMP from the list.

You can run that command now, and install a GUI as well.

---

