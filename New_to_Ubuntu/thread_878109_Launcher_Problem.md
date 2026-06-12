---
title: "Launcher Problem"
date: 2008-08-02
forum: New to Ubuntu
---

### Post by theoldgit on 2008-08-02
I have a very strange thing going on here. Last week i was messing with desklets and screenlets (trying to get them to work and gave up). Now that I have switched on again I find that all my desktop launchers have no icons attached and in their place is an icon that looks like a text page with the name under as xxxxx.desktop. Add to that, none of them will launch but instead open a text editor with some text in it. Also if I try to look at any .png files I cant see them.

I have searched but cant find the answer and have no idea where to start.

I am running 8.04 64bit version with Gnome desktop.

Any ideas where to start?
Thanks

---

### Post by Diabolis on 2008-08-02
.desktop files are just text files with a format that allows them to launch applications

example:
```
**cat /usr/share/applications/emesene.desktop** 
[Desktop Entry]
Name=Emesene
GenericName=Emesene
Comment=MSN Messenger client
Exec=emesene
Icon=emesene
Terminal=false
Type=Application
Categories=Network;InstantMessaging;

```

I don't know why they are screwed, but you can fix them if you right click on them so you can modify their values.

---

### Post by theoldgit on 2008-08-02
Sure I can change all the permissions, none are set to executable but I cant see any of the icons either.  Even when I try to add new icons they cant be found. They are there because i find them with nautilus but I cant see them as Ubuntu doesnt seem to know what to do with .png files.

---

