---
title: "Older Wallpaper-Tray for 10.04 &amp; beyond...."
date: 2010-07-15
forum: Outdated Tutorials &amp; Tips
---

### Post by autocrosser on 2010-07-15
I have used Wallpaper-Tray for several years now & really like the way it works. I'm the "guy" that campaigned to update Wallpaper-Tray to the 0.5.x version back during Jaunty & have kept a eye on where the app is "going". 

Well, it's not going anywhere right now. The developer (earthworm) seems to have dropped it & he is no longer to be found---the Debian maintainer has stopped support as of December of 2009. The 0.5.x series will no longer compile against the newer Ubuntu versions--I've tried several different approaches without success.

So, all is lost & we can't have Wallpaper-Tray any more?  Wrong--I've tested the older 0.4.x series on both x86 & x86-64 & it works just fine, so let's get it installed!!!!

I have kept the last 0.4.x series on my system & you will find both arches at the end of this post. Installing is as simple as downloading the correct one to your desktop & clicking on it.....a little app called gdebi should ask you for root permissions & install it with the correct dependencies. If you have used Wallpaper-Tray before (Karmic & earlier), you should have the preferences still in your system (if you upgraded)---If this is your first install--

Wallpaper-Tray installs in the Notifications area (0.4.x versions do--the 0.5.x versions were just a panel app & that's where the problem came from). Being in the Notifications area will have a nice advantage very soon---Gnome-Shell which previews in October can work just fine (at this time) with Wallpaper-Tray---which makes it the only Wallpaper changer that that I know of that can be in the panel "natively" in Gnome-Shell....a real plus if you ask me.

There are 2 tabs---one where you define the pictures you want displayed & one that sets options.  There will be a menu item created under "Other" so you can start it there or you can create a "auto-start" in System-Preferences-Startup Programs. If you have never done it before---it's very easy.  Click the "+Add" tab & in the box that comes up:
```

Name:  Wallpaper-Tray
Command: wallpaper-tray
Comment: whatever you want it to say.
```That's it--you're done--you can just start the app from the menu item or do "Alt" & "F2" then type in wallpaper-tray to start it right away & set it up....the next time you logout/in or reboot it will auto-start & you will see the icon (current desktop picture) in the Notifications area.

Due to forum limits--I needed to add the .zip to the .debs---just rename the file by removing .zip before you install.

HAVE FUN!!!!!!

---

