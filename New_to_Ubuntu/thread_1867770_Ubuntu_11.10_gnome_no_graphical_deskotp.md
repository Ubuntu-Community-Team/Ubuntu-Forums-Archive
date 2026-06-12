---
title: "Ubuntu 11.10 gnome no graphical deskotp"
date: 2011-10-23
forum: New to Ubuntu
---

### Post by yoramdavid on 2011-10-23
Hello,

This happened after I installed an upgrade just after upgrading to 11.10. I also uninstalled some programs I did not want (and perhaps dependencies, but I trusted it would not uninstall needed programs).
Note: Unity 3D never worked, Unity 2D works but I do not like it, so I was using gnome classic, but now I cannot select gnome classic from the login screen since there is none.
I also have KDE installed but it stopped loading. I do not use it anyway.
After many days trying to fix my problem using the threads already existent (those are many), I still have the problem which is:

I boot the computer, and I do not get the Light-DM login screen, the computer stops at a black screen with some text (varies from session to session):
_________________________________________________________________[SIZE="1"]
* "Staring System v runlevel compatibility"    (OK)
* "Stopping automatic crash report feneration"   (Fail)
* "Starting regular backfroud program processing daemon"   (OK)
* "Staring Gnome Display Manager"   (OK)
* "Starting ACPI daemon"   (OK)
* "Starting anc(h)ronistic cron"    (OK)
* "Starting save kernel messages"    (OK)
* "Starting CPU interrupts balancKubuntu 11.10"   (OK)
* "Stopping anc(h)ronistic cron"   (OK)
* **"Stopping Gnome Display Manager"   (OK)**
"exportfs: scandir /etc/exports.d: No such file or directory"
* "Starting bluetooth"     (OK)
* "Exporting directories for NFS kenerl daemon"   (OK)
[COLOR="Red"]*[/COLOR] "PulseAudio configured for per-user sessions"   (OK)
"starting SANE network scanner server: saned.g NFS kernel daemon (OK)"
* "Checking battery state   (OK)"
* Starting timidity** Alsa midi emulation...  Ispatcher emulation 0.7.1 Start" (OK)
"Starting CUPS printing spooler/server"      (OK)[/SIZE]
_________________________________________________________________

If I hit "CTRL+ATL+F2", I can login in text mode.
If I then run the command "startx", I go in graphical mode but all I get is the desktop.
To get the menu and taskbar I have to open a console and type "gnome-panel" things work, but visual settings limited and different from what I had.

Things I have done so far: I have reinstalled Linux-image, unity 2d and gnome-desktop, installed gnome-shell, gnome-session-fallback, Light-DM.
I have set automatic login to by-pass the login screen, but still it stops at the screen I describe above.

Commands used:
"sudo dpkg --configure -a"   (no errors reported)
"sudo apt-get update"   (at 99% done it takes some time then returns some 404 Not found errors)
"Sudo apt-get update"     (system is already updated)
"sudo apt-get -f install"  (no errors reported)
"sudo /usr/lib/lightdm-set-defaults -s gnome-shell"   (não mudou nada)

I tried to call the login screen once logged on text mode with:
"sudo lightdm start"   (brings me back to same screen)
"gui-login"  (comando não encontrado).

I do not know what else to do, I am hoping someone can help.
Thanks in advance.

[B]24-10-2011
Some improvements:[/B]
I am now able to start Ubuntu with XServer after doing the following:
Uninstalled LilghtDM, installed GDM and ran the command "sudo dpkg-reconfigure gdm"
Now, I have to find a way to bypass the login screen to logind automatically into the desktop (automatic login is enabled, well it does not ask for password but still stops at login screen)

To make desktop function with panel and upper bar on windows, I had to add to the startup programs the following commands:
"metacity --replace" to have the minimize, maximize and close buttons on windows.
"gnome-panel" to have the menu and task bar displayed.
"xscreensaver -nosplash" to have screensaver daemon to load at startup.

But system is quite slow and I cannot get my visual settings back.

---

### Post by yoramdavid on 2011-10-26
Since no one is getting interested in this thread, I am closing it. It is not solved. ):

---

