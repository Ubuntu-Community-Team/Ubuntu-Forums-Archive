---
title: "What do I edit for new default apps?"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by marcelo danico on 2008-05-21
I want to open pdf with acroread, music with mplayer, video with gxine. Not the default evince, totem.

I had all this down under 6.06 but can't remember where I edited all these default applications. Anyone have a clue?:confused:

---

### Post by bobbocanfly on 2008-05-21
You can change most of these settings in System -> Preferences -> Preferred Applications.

---

### Post by SunnyRabbiera on 2008-05-21
well if you want to you can do it yourself by right clicking the pdf or whatever and select "properties"
and then go to the "open with" tab
if its a PDF, adobe reader should be on the list if you installed it, and if its not you can go to the "add" button.
you can choose the app you want by clicking on the little circle/square/whatever next to the application name

---

### Post by anotherdisciple on 2008-05-21
I always sudo aptitude remove totem and it's plugins and such... I use vlc instead... it becomes the new preffered app

---

### Post by marcelo danico on 2008-05-21
I already went into Preferences-->Preferred applications and changed what I could.

I'm not on a linux machine so I can't check, but I've been googling and some results say the preferred apps are in usr/bin/

Perhaps I was editing a script last time.

---

### Post by aktiwers on 2008-05-21
> **marcelo danico said:**
> I already went into Preferences-->Preferred applications and changed what I could.

I'm not on a linux machine so I can't check, but I've been googling and some results say the preferred apps are in usr/bin/

Perhaps I was editing a script last time.

If you right-click on the videofile (lets say an .avi file) and pick properties.
Then go to the "open with" tab and pick your app.

After this all .avi files will open in that app by default.

---

### Post by marcelo danico on 2008-05-21
Thanks.

---

### Post by marcelo danico on 2008-05-27
I think this is what I was looking for

> sudo gedit /etc/gnome/defaults.list


---

### Post by mc4man on 2008-05-28
On hardy gxine is added as a choice of default player when installed. Change from totem in preferences -> file management -> media. (Not enabled by default, go to pref. -> main menu or r. click apllications edit menus)

You should edit defaults.list with _care_

---

