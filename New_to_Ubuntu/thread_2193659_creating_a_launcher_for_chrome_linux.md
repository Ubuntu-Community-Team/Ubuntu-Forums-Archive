---
title: "creating a launcher for chrome linux"
date: 2013-12-14
forum: New to Ubuntu
---

### Post by thetotalbadger on 2013-12-14
Hello I got my hands of Google chrome linux 64 bit.. It works flawlessly other then one little minor issue, it only runs from a terminal  command > google-chrome-stable to be precise.  I know there has to be a way to make a launcher file for this that I could just throw on the launcher bar and just click that have it automatically run the terminal command and blam I got my muitplatform browser at my finger tips :D. 

(Ps I tried searching but the results I kept on getting weren't helpful towards my need, also I wasn't sure where to put this. Haven't been here in a loooooooong time.)

Signed Darko.

---

### Post by monkeybrain20122 on 2013-12-14
There should be a chrome .desktop file in /usr/share/applications. If for some reasons it is not there just symlink the one from chrome's install directory 

```
sudo ln -s /opt/google/chrome/goole-chrome.desktop /usr/share/applications/google-chrome.desktop
```

---

### Post by deadflowr on 2013-12-14
It should already have a launcher.
Press the windows key on the keyboard, this opens the dash menu, and then type chrome.
An icon should appear for google-chrome.
You can either drag it to the launcher or launch it from there(theere meaning the dash menu)

Alternatively, you can click on the top most icon in the launcher pane(the left side area with all the apps going down) the top one is the dash.

Of course this also depends on whether or not you're running normal Ubuntu.
Most other desktop variants such as lubuntu or kubuntu have different layouts.
Gnome-shell, however would be quite similar in that you can open it's dash and search much in the same way as normal Ubuntu.
But now I'm just rambling...

---

### Post by thetotalbadger on 2013-12-14
Thanx guys when i installed it it said it launched from a terminal command.. So I wasn't expecting it to be that simple. Ahhaa, haven't played with linux in quite some time, stuff's changed.

---

### Post by deadflowr on 2013-12-14
You installed a deb file in the ubuntu software center?
And it shows the launch in terminal thingy.
Yeah, I think I've read about that behavior.
I'm sure it's a bug.

A quick tip with Ubuntu/unity.
If you drag the app to the launcher, you can use mouse right-click to access the quicklist function.
The quicklist functions give you extra functions for the launcher.
An example would be for chrome with launching the incognito mode directly.
It's can also be used to lock apps or unlock apps from the launcher pane.

---

### Post by monkeybrain20122 on 2013-12-14
Use gdebi to install deb files in the future. 

sudo apt-get install gdebi

By the time the USC has started gdebi already finishes install. :)

---

### Post by tajreed on 2013-12-14
Same problem here. Chrome won't launch except from CLI. I tried the sim link proposal but that also wouldn't work. Any thoughts?

---

### Post by deadflowr on 2013-12-14
> **tajreed said:**
> Same problem here. Chrome won't launch except from CLI. I tried the sim link proposal but that also wouldn't work. Any thoughts?

Even if you launch chrome from the cli, a launcher will be added to the left-side dock.
When it does, lock it(right-click on it and choose lock to launcher).
It goes without saying this is a unity behavior, and should be disregarded for other desktops.

---

### Post by monkeybrain20122 on 2013-12-14
> **tajreed said:**
> Same problem here. Chrome won't launch except from CLI. I tried the sim link proposal but that also wouldn't work. Any thoughts?

Can you look for google-chrome.desktop?

```
sudo updatedb
locate google-chrome.desktop
```

---

### Post by tajreed on 2013-12-14
Chrome is locked to the Dash but will not launch.
Google-Chrome.desktop is located in usr/share/applications

---

### Post by deadflowr on 2013-12-14
> **tajreed said:**
> Chrome is locked to the Dash but will not launch.
Google-Chrome.desktop is located in usr/share/applications

Does it launch from the dash?
If so, try unlocking the one on the launcher and then re-lock it again.

we could also look at the exec command being used in the launcher.

---

### Post by monkeybrain20122 on 2013-12-14
Can you open Nautilus, click on computer then navigate to /usr/share/applications and click on the chrome icon and see if it works?

 Also post the content of the desktop
```
gksudo gedit  /usr/share/application/google-chrome.desktop
```
Then copy the content and paste here.

---

### Post by tajreed on 2013-12-14
Where would I find the exec command.

Chrome does not open from Dash.

---

### Post by monkeybrain20122 on 2013-12-14
The exec command is in the .desktop file, which is /usr/share/applications/google-chrome.deskop.

Navigate there and click on it and see if it works, and copy the content here.

---

### Post by tajreed on 2013-12-15
I copied google chrome from /usr/share/applications to desktop and to launcher now all is well. 

Thanks to all for the help.

---

### Post by monkeybrain20122 on 2013-12-15
Can you navigate to /usr/share/applications and click the icon there and  see if it launch?

---

