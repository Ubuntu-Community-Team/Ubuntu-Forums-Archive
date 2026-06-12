---
title: "Need your input to applications list"
date: 2012-04-26
forum: Programming Talk
---

### Post by Jacobonbuntu on 2012-04-26
Hi people, I am working on a quicklist editor, see [this]("http://ubuntuforums.org/showpost.php?p=11857127&postcount=1") post.
The latest version(s) edits and recognizes both "old style" (Ayatana...) and new style (Actions=) desktop files. It also lists "standalone" quicklists (not representing an installed application) you might have created, and offers edit functionality to those.
My issue is: I could let the editor list all desktop files in /usr/share/applications, but there are a lot of irrelevant desktop files in there. Therefore I use a whitelist of applications that will be presented to the user, if installed. Of course I want to have as many applications in it as possible, so please tell me what applications you use that should be editable in a quicklist editor.
Secondly, I would like to ask what applications should have special features in the editor in your opinion (for example nautilus -> add directory+check, Vbox -> add Vbox+check etc etc)

what I have so far:
       
self.applist = {"Nautilus-home": "nautilus-home", "Software-Center": "ubuntu-software-center", "VirtualBox": "virtualbox",\
                       "Thunderbird": "thunderbird", "Firefox": "firefox", "Opera": "opera-browser", "Banshee": "banshee", "Exaile": "exaile",\
                        "Clementine": "clementine", "Gimp": "gimp", "Terminal": "gnome-terminal", "Inkscape": "inkscape", "Gnome-Tweak": "gnome-tweak-tool",\
                        "Almanah Diary": "almanah", "Arista video converter": "arista", "Audacity audio editor": "audacity", "Idle (2.7)": "idle-python2.7", "MyUnity": "myunity",\
                        "OpenShot video editor": "openshot", "PDF Chain": "pdfchain", "Rhythmbox music player": "rhythmbox", "Scheduled tasks": "gnome-schedule",
                        "Pinta": "pinta", "MuseScore": "mscore", "LibreOffice": "libreoffice", "Abiword": "abiword", "Planner": "planner", "Blender": "blender", "Xine": "xine",\
                        "Xsane": "xsane", "CompizConfig": "ccsm", "Gscan2pdf": "gscan2pdf", "Totem": "totem", "Character map": "gucharmap", "Gedit": "gedit" }

help appreciated!!

---

