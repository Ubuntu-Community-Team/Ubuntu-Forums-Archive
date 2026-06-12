---
title: "libreoffice quickstarter icon gone after reboot"
date: 2011-10-20
forum: New to Ubuntu
---

### Post by al.adab on 2011-10-20
this is definitely not a major issue though it'd be nice if I could fix it:

I've installed LibreOffice on Xubuntu 11.10 + enabled its "quickstarter". The icon appears on the top taskbar, though - after re-booting - it's no longer there. It gets back on the taskbar after launching LibreOffice writer from menu. 

any idea?

---

### Post by yaztromo on 2011-10-23
Had the same issue. The problem is caused by a mistake in the quickstarter script.

Open a terminal and type
```
sudo nano /usr/lib/libreoffice/share/xdg/qstart.desktop
```
Find the line that reads
```
Exec=libreoffice3.4 --quickstart --nologo --nodefault
```
Change it to
```
Exec=libreoffice --quickstart --nologo --nodefault
```
Press Ctrl-X and press y to save.
Reboot and it should work

---

### Post by Byb on 2011-10-24
Hi yazmotro
I had the same issue and I tryied your workaround. Althought now the syslog now shows (translated from french) when I want to logout/reboot/poweroff from the GUI. I have to sudo reboot ```

Oct 24 10:01:04 PC gnome-session[1500]: WARNING: Unable to load desktop file '/usr/lib/libreoffice/program/soffice.desktop': No file or folder of this kind
Oct 24 10:01:04 PC gnome-session[1500]: WARNING: Unable to find desktop file 'soffice.desktop': Unable to find a valid keys file in the search folders
Oct 24 10:01:04 PC gnome-session[1500]: WARNING: Unable to find desktop file 'gnome-/usr/lib/libreoffice/program/soffice.desktop': Unable to find desktop file 'soffice.desktop': Unable to find a valid keys file in the search folders

```I use gnome-panel as my video is not supported for Unity in ubuntu standard 11.10 (ubuntu classic without effects)
Please, do you know what happens?
I just gived a try with quitting the quickstarter first before reboot : this brings back the GUI reboot/logoff/poweroff working.
Something strange too is my .desktop file showing pt_BR locale when my pc is french, LibO and the quickstarter info bubble tooltip too ("Démarrage rapide de LibreOffice 3.4):
```
[Desktop Entry]
Version=1.0
Terminal=false
Type=Application
Categories=Office;
Exec=libreoffice --quickstart --nologo --nodefault
NoDisplay=true
Name=LibreOffice 3.4 Quickstarter
Name[pt_BR]=LibreOffice 3.4 Quickstarter
Comment=Hook for quickstarter startup
X-KDE-Protocols=file,http,smb,ftp,webdav
```

---

### Post by yaztromo on 2011-10-24
That's very odd. There isn't an soffice.desktop file in the program folder so nothing should be looking for it.

```
ls /usr/lib/libreoffice/program/so*
/usr/lib/libreoffice/program/soffice
/usr/lib/libreoffice/program/soffice.bin
/usr/lib/libreoffice/program/sofficerc

```

The correct startup script is located at /usr/lib/libreoffice/share/xdg/qstart.desktop

I don't run gnome so I'm not sure if the autostart on login for the quickstarter works the same as for XFCE, but it might do.

For XFCE it is simple. A symbolic link to qstart.desktop is placed in /home/yourusername/.config/autostart. That's all there is to it for Xubuntu. The check box for the quickstarter in libreoffice->tools->options->memory just deletes or adds the symbolic link as required.

For reference I am running 11.10 Oneric.

Hope that gives you something to go on.

---

### Post by al.adab on 2011-10-26
worked all right. Thanks! :)

---

### Post by beew on 2011-10-26
I notice that there is no option for quickstart icon if you install the .debs from Libreoffice. Moreover, I can't shut down the computer when the quickstart icon is activated. I find the difference in load speed  quite small whether you have the quickstart icon or not once you have reset the memory preferences. With OpenOffice it used to make a bigger difference.

---

