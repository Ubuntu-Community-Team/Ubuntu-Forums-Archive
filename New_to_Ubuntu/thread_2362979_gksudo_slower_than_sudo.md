---
title: "gksudo slower than sudo ?"
date: 2017-06-04
forum: New to Ubuntu
---

### Post by automate-stuff on 2017-06-04
I am using Ubuntu gnome 16.04. I have created a shortcut [Gedit-Root.desktop] in [COLOR=#242729][FONT=Consolas]/usr/share/applications with the following content : 

[/FONT][/COLOR]**[Desktop Entry]**
**Name=Gedit**
**Icon=/usr/share/icons/gnome/256x256/apps/accessories-text-editor.png**
**Exec=gksudo gedit**
**Terminal=false**
**Type=Application**
[B]Name[en_CA]=Gedit-Root



[/B]The problem is, when I launch this shortcut and enter the root password, it doesn't load fast enough, the mouse pointer turns into the loading circle and after a few seconds ( 4-5 seconds) the mouse pointer goes back to normal ....

But when i go to the terminal and run: **sudo gedit **- enter password - hit enter ... the app runs instantly and the mouse pointer never turns into a loading circle...


How Can I fix this ?

---

### Post by mc4man on 2017-06-04
You could install the nautilus-admin package which uses policykit. For text files the option in the context menu would be "Edit as Administrator"
(The other half is " Open as administrator" which opens directory in nautilus as root. A nautilus restart is required for the later option.
Pretty poor idea to have been using sudo gedit. You may wish to  recursively parse your $HOME directory for root owned files & get rid of or fix.

---

### Post by automate-stuff on 2017-06-04
that didn't answer my question, I want to start gedit as root through a shortcut icon. I don't want to browse for a file and edit it as root...I successfully was able to do this through creating a shortcut and changing the "exec" entry to gksudo gedit ... the problem I have is that **gksudo gedit **takes 4-5 seconds to load gedit fully after you enter the root password and hit enter...while **sudo gedit **&#8203;runs it instantly without loading delays...

---

### Post by yetimon_64 on 2017-06-04
> **automate-stuff said:**
> ... the problem I have is that **gksudo gedit **takes 4-5 seconds to load gedit fully after you enter the root password and hit enter...while **sudo gedit **&#8203;runs it instantly without loading delays...

4 to 5 seconds for gksudo to authenticate sounds about normal here. Yes running sudo gedit will be nearly instant that is also normal from the terminal. The gksudo command uses the gksu package to check your credentials then opens the file in the application which takes a few seconds normally, which is another layer of access compared to usage of straight "sudo" in a terminal.

What mc4man is commenting on is the potential for root to take ownership of your home folder files when using straight sudo with a graphical application (it is a very well known problem around here, especially for new users)... if it does so to either the ~/.ICEauthority or ~/.Xauthority files you may lose the ability to boot into your user account desktop.

If you continue to use sudo with graphical applications I strongly suggest you use the "-H" switch which will prevent a graphical application damaging your home folder ownership/permissions for example with gedit ...
```
sudo -H gedit <your-text-file>
```
Using straight sudo in terminal has always been faster but like I note above can be dangerous to your account access with some graphical applications. gksu and gksudo are a wrapper layer for safer usage with graphical applications, hence a bit more time taken to open is usual/normal so you will see the pointer "spinning" while it works on authenticating/opening etc.

---

### Post by automate-stuff on 2017-06-04
Now that i am checking, it is more like 10-14 seconds....Considering I am also using an ssd, this is a bit annoying....is there anyway to make this a lot faster ?

Thanks for responding everyone...

---

### Post by yetimon_64 on 2017-06-04
> **automate-stuff said:**
> Now that i am checking, it is more like 10-14 seconds....Considering I am also using an ssd, this is a bit annoying....is there anyway to make this a lot faster ?

Thanks for responding everyone...

I just remembered I have a similar launcher (on 14.04 here) stored in ~/.local/share/applications that works fairly fast; about 2 seconds from entering password. 

The entry I use is in the code box below, you may want to copy it and give it a try; or even just the exec line. Note that I locate it in my home folder (~/.local/share/applications) not in /usr/share/applicatons like you have done. Launchers stored in  ~/.local/share/applications will be used first even if another identically named launcher is in /usr/share/applications. 
```
#!/usr/bin/env xdg-open

[Desktop Entry]
Name=gedit as ROOT
GenericName=Root Text Editor
Comment=Edit text files
Exec=gksu gedit %U
Terminal=false
Type=Application
StartupNotify=true
MimeType=text/plain;
Icon=gedit-root.png
Categories=GNOME;GTK;Utility;TextEditor;
X-GNOME-DocPath=gedit/gedit.xml
X-GNOME-FullName=Root Text Editor
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=gedit
X-GNOME-Bugzilla-Component=general
X-GNOME-Bugzilla-Version=3.2.1
X-GNOME-Bugzilla-ExtraInfoScript=/usr/share/gedit/gedit-bugreport
X-Ubuntu-Gettext-Domain=gedit
```

Try the exec line from this one with gksu and the %U and see if that makes a difference first. 
Note the icon line above refers to a custom icon I made and store in ~/.icons so make sure you don't copy that line if you use the whole launcher :-)
Good luck, yeti.

**Edit:** I just booted into 16.04 (Unity) and I have the same launcher in use here as well and it works just as fast as 14.04 and xfce etc.
Either because of the shebang line (#!/usr/bin/env xdg-open) or the MimeType line (not sure which) I have this entry available from the right click context menu for opening files with gedit as root.

---

### Post by automate-stuff on 2017-06-04
No luck, I tried the gksu gedit %U     restarted...still takes too long....reinstalled gedit...still the same...

---

