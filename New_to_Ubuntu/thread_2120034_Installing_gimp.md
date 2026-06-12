---
title: "Installing gimp"
date: 2013-02-25
forum: New to Ubuntu
---

### Post by DaveMcC on 2013-02-25
Hi
I have upgraded the other computer to Lubuntu 12, and I have to install gimp on it, 
With Ubuntu I have a **Ubuntu Software Center** but with Lubuntu I can't find it, nor any **Software Center**, yet on my first attempt at installing Lubuntu I thought I saw some thing like **Lubuntu Software Center** in ***System Tool***s or*** Preference ***

I changed to** K **then back to** L**_ ubuntu_

Nor can I find a terminal window?

Dave

---

### Post by TheFu on 2013-02-25
<cntl>-<alt>-t should open a terminal.
```
 sudo apt-get update && sudo apt-get install gimp
```

<alt>-F2 should open a "RUN" dialog if that doesn't work, then you can type any command you like - but using an **xterm** would be smart.

**Synaptic** is the GUI package manager, if you prefer.  I like it better than Software Center because it doesn't hide available packages.

---

### Post by DaveMcC on 2013-02-25
Found UXterm along with Xterm, strange, two of them?

I typed in Sudo apt-get install gimp[FONT=monospace], "Opps forgot to add, that worked"

Would that work if I was to type in the same but change the last bit to Ubuntu Software Center as there is a load of crap I wish to del out of the "Menu Settings" ie office / games Xpad / LXterminal / abiword etc
  which I think can be done safer than via Synaptic (manager)
Dave
[/FONT]

---

### Post by TheFu on 2013-02-25
> **DaveMcC said:**
> Found UXterm along with Xterm, strange, two of them?

I typed in Sudo apt-get install gimp[FONT=monospace], "Opps forgot to add, that worked"

Would that work if I was to type in the same but change the last bit to Ubuntu Software Center as there is a load of crap I wish to del out of the "Menu Settings" ie office / games Xpad / LXterminal / abiword etc
  which I think can be done safer than via Synaptic (manager[/FONT]

**Forget about software center. That is a Unity thing.**  Synaptic, apt-get, aptitude all use the same back-end database.  They all modify the same data inside APT - the package manager.  Synaptic is just as safe to use as Software Center.  If you remove any application through APT, it should be removed from the menu too.

"gimp" was the name of the package, not necessarily the name of the program you wanted installed.

If you want to learn more about apt-get - and you should - read the man page. RTFM - this was a common response for 20+ yrs when someone new to UNIX/Linux asked a question. It has become frowned upon, but still makes sense. Read The F..... Manual.   Type this in:
```
$ man apt-get

```without the $.  The '$' is meant to mean you can do this from any regular userid.  Sometimes a '#' will be shown, which means you must be root for a command to work.  sudo is a way to temporarily elevate a userid permissions to some other userid - often root - for a single command.  It is the user's responsibility to request the elevation, unlike on Windows where the program will notify a user that elevated privileges are needed.  Further, not every userid has sudo privileges - that is a special feature for certain accounts only.  How would you learn more about sudo?  RTFM, of course.

$ **man sudo**

Almost every command on any Linux machine will have a man page. Man pages are really impressive and efficient. Learning to read and understand a man page does take some time, but once you learn that skill, it will forever pay off.  To learn more about man pages ....
$ man man

If you ask to have software center installed - first, that is not the name of the package, so it will not work. Second, software center has a huge number of dependencies - which sorta defeats the reason that you run Lubuntu, right? You wanted a lite-weight GUI.

Also, please be extremely careful about case-sensitivity.  "Sudo" and "sudo" are completely different things. Hopefully, "Sudo" does not exist on your system. If it does, then it is probably a back-door.  I love case-sensitivity, but it took some getting used to. Now it drives me crazy on Windows that it doesn't matter. Just today, I was trying to rename a file to fix the case and it refused because the file was on an NTFS file system that I was accessing from Linux.

Sorry for rambling.  I'd like to teach you to fish, not just give you a fish today. ;)

---

