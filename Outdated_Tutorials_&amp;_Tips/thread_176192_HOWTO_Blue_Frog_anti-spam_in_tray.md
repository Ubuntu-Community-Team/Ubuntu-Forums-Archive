---
title: "HOWTO: Blue Frog anti-spam in tray"
date: 2006-05-14
forum: Outdated Tutorials &amp; Tips
---

### Post by wblancqu on 2006-05-14
Hi guys, as promised... This is what it looks like:
[IMG]http://studwww.ugent.be/~wblancqu/ubuntu/bluefrog.png[/IMG]
Download rpm from [http://sourceforge.net/project/showfiles.php?group_id=153754]("http://sourceforge.net/project/showfiles.php?group_id=153754").
Now open up a terminal and cd tot the path where you've downloaded the file.
```
sudo alien bluefrog*.rpm
sudo dpkg -i bluefrog*.deb
```

```
sudo gedit /etc/apt/sources.list
```

Add the following lines in the file (Change breezy to dapper when using dapper):

deb [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) breezy main dupdate french
deb [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) ubuntu main dupdate french

Save the file.
```
sudo apt-get update
sudo apt-get install alltray
```

Then, in gnome-terminal, choose Edit - Profiles - New. Choose "tterm" as name. Edit the setting to whatever you like and save. I've made it transparant and removed the sliders, and changed the font color.

Now:
```
cd /usr/share/pixmaps
sudo wget http://studwww.ugent.be/~wblancqu/ubuntu/bluefrog.ico
sudo gedit /usr/bin/bluefrogtray
```
Paste this:
```
#!/bin/bash
alltray -i /usr/share/pixmaps/bluefrog.ico -x -g 600x250+660+50 "gnome-terminal --hide-menubar --window-with-profile=tterm -x bluefrog"
```

You might want to change the +660. Change it into the x-res of your screen minus 620. So if you hava 1024x768 then use +404. I hava 1280x800 so I'm using +660.
Now save the file and make it executable.
```
sudo chmod +x /usr/bin/bluefrogtray
```

That's it, now run bluefrogtray. I've made it run at boot (System-Preferences-Sessions). And also created a menu entry using smeg.

Now, you might want to download thunderbird and/or firefox blue frog extension, for reporting spam mails. These can be found [here for firefox]("https://addons.mozilla.org/firefox/1863/") and [here for thunderbird]("https://addons.mozilla.org/thunderbird/2486/"). I'm using latest Firefox and Thunderbird (1.5.*), so I don't know if these extensions still work with the older versions (1.0.x).

One more thing, now, at time of writing, there seems to be a problem](*,) .There is a problem with logging in, but I think that is because blue frogs server is down again. Anyway it worked fine a couple of days ago, and it'll will work fine again in the near future.

I hope someone likes this howto, it's my first ;)
Grtz

---

### Post by kaveraj on 2006-05-16
And for users like me wondering what ALL TRAY is here is a desc from sourceforge :

> With AllTray you can dock any application with no native tray icon (like Evolution, Thunderbird, Terminals) into the system tray. A high-light feature is that a click on the "close" button will minimize back to system tray.  It works well with Gnome,  KDE,  XFCE 4*, Fluxbox* and WindowMaker* 



Thanks for the tut .. I will try it and post my comments.

---

### Post by wblancqu on 2006-05-17
Bad news... Blue Security stopped the Blue Frog project due to spammer attacks...](*,) Read [here]("http://www.bluesecurity.com/blue-frog/").

---

### Post by frodon on 2006-05-18
See this post too : [http://ubuntuforums.org/showthread.php?t=178684](http://ubuntuforums.org/showthread.php?t=178684)

---

### Post by nocturn on 2006-05-18
I just posted an advisory in the Cafe, but I'll put it up here too.

To all users of Blue Frog, uninstall the software ASAP.  With the demise of the central server, there is chance that the clients are hijacked to send SPAM or do DOS attacks.

---

### Post by wblancqu on 2006-05-18
Is there any other good free antispam software for linux ?

---

