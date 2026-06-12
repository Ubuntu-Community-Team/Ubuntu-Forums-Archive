---
title: "Unity-2D daily ppa"
date: 2011-07-27
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by lucazade on 2011-07-27
Unity-2D available in daily PPA switched to Gtk3 rendering and to Dconf instead of old Gconf.

Now it follows different theme colors for the panel, uses new indicator applets and it shares the same settings with Unity-3D.
Althought is still under heavy development and porting is not finished, is really nice to play with and it feels snappier.

Daily PPA:
[https://launchpad.net/~unity-2d-team/+archive/unity-2d-daily](https://launchpad.net/~unity-2d-team/+archive/unity-2d-daily)

BZR source code:
[https://code.launchpad.net/unity-2d](https://code.launchpad.net/unity-2d)

---

### Post by rburkartjo on 2011-07-27
luc yes a nice improvement

---

### Post by akoskm on 2011-07-28
[https://bugs.launchpad.net/unity-2d/+bug/753481]("https://bugs.launchpad.net/unity-2d/+bug/753481") seems to disappeared \o/.
It feels snappier a lot!

---

### Post by lucazade on 2011-07-28
> **akoskm said:**
> [https://bugs.launchpad.net/unity-2d/+bug/753481]("https://bugs.launchpad.net/unity-2d/+bug/753481") seems to disappeared \o/.
It feels snappier a lot!

good to know that issue is no more present!
I'd like to ask you if session close quickly if you do a logout or a restart, here there is a long delay (this happened also with previous bzr commits btw).
[https://bugs.launchpad.net/unity-2d/+bug/812104](https://bugs.launchpad.net/unity-2d/+bug/812104)

---

### Post by LADmaticCA on 2011-07-28
any screenshots?

---

### Post by lucazade on 2011-07-28
> **LADmaticCA said:**
> any screenshots?

Ambiance:
[[IMG]http://dl.dropbox.com/u/1338581/varie/Schermatas.png[/IMG]]("http://dl.dropbox.com/u/1338581/varie/Schermata.png")

Radiance (with some visual glitches!):
[[IMG]http://dl.dropbox.com/u/1338581/varie/Schermata-1s.png[/IMG]]("http://dl.dropbox.com/u/1338581/varie/Schermata-1.png")

---

### Post by jbicha on 2011-07-28
unity-2d 3.8.12 was just pushed into the repositories.

---

### Post by mc4man on 2011-07-28
> **jbicha said:**
> unity-2d 3.8.12 was just pushed into the repositories.
The upgrades are available, though proved to be an odd one here on 2 installs where I've have launcher favorites different than the default in unity 3d.

unity-2d is now using gio(gsettings), so it appears will use the same launcher favorites list as unity (3d)
The upgrade though  did reset unity 3d's  launcher to unity-2d's default or there-abouts, swapped google-chrome for chromium-browser which isn;t even installed

After gsettings back to what I use unity-2d now uses the same as unity 3d

So before the upgrade - 
> gsettings get com.canonical.Unity.Launcher favorites
['nautilus.desktop', 'google-chrome.desktop', '/home/doug/.local/share/applications/utility.desktop', '/home/doug/.local/share/applications/multimedia.desktop', '/home/doug/.local/share/applications/gnome-terminal.desktop', '/home/doug/.local/share/applications/mplayer1.desktop', '/home/doug/.local/share/applications/mplayer2.desktop', 'firefox.desktop']

After the upgrade - 
> gsettings get com.canonical.Unity.Launcher favorites
['nautilus-home.desktop', 'firefox.desktop', 'libreoffice-writer.desktop', 'libreoffice-calc.desktop', 'libreoffice-impress.desktop', 'ubuntu-software-center.desktop', 'chromium-browser.desktop']

---

### Post by akoskm on 2011-07-29
> **lucazade said:**
> good to know that issue is no more present!
I'd like to ask you if session close quickly if you do a logout or a restart, here there is a long delay (this happened also with previous bzr commits btw).
[https://bugs.launchpad.net/unity-2d/+bug/812104](https://bugs.launchpad.net/unity-2d/+bug/812104)

Did't happen yesterday but logged out only once, when I get home I'll experiment more.
A new bug seems to be appeared [https://bugs.launchpad.net/unity-2d/+bug/817458]("https://bugs.launchpad.net/unity-2d/+bug/817458").

---

### Post by akoskm on 2011-08-02
> **lucazade said:**
> good to know that issue is no more present!
I'd like to ask you if session close quickly if you do a logout or a restart, here there is a long delay (this happened also with previous bzr commits btw).
[https://bugs.launchpad.net/unity-2d/+bug/812104](https://bugs.launchpad.net/unity-2d/+bug/812104)

After 4 days still isn't experiencing any delay on log-out, seems to be fixed?
Does anyone experience [https://bugs.launchpad.net/unity-2d/+bug/817458]("https://bugs.launchpad.net/unity-2d/+bug/817458")?

---

### Post by mc4man on 2011-08-02
> **akoskm said:**
> ?
Does anyone experience [https://bugs.launchpad.net/unity-2d/+bug/817458]("https://bugs.launchpad.net/unity-2d/+bug/817458")?
If you mean left edge reveal, then yes it does that here. I hardly ever use unity-2d so would assume it's a feature

(if and wishing to turn off haven't looked into...

---

### Post by akoskm on 2011-08-02
> **mc4man said:**
> If you mean left edge reveal, then yes it does that here. I hardly ever use unity-2d so would assume it's a feature

(if and wishing to turn off haven't looked into...

Indeed there is a feature to do that, however I checked otherwise in Launcher & Menus.
It would be good if somebody could test what is the difference between those options, here it seems to be totally redundant.

---

### Post by lucazade on 2011-08-02
> **akoskm said:**
> Indeed there is a feature to do that, however I checked otherwise in Launcher & Menus.
It would be good if somebody could test what is the difference between those options, here it seems to be totally redundant.

confirmed bug is present also here.
probably the switch from gconf to dconf/gsettings is the cause of this.

---

### Post by akoskm on 2011-08-02
> **lucazade said:**
> confirmed bug is present also here.
probably the switch from gconf to dconf/gsettings is the cause of this.

Glad that you confirmed, thank you!
(I thought first it is due to remained config files or such as..)

---

### Post by akoskm on 2011-08-17
This happened with the latest update:
[http://imagebin.org/168347](http://imagebin.org/168347)
all of the panel applets are aligned somewhere but not to the edge of my screen.
unity-2d-panel version: 3.8.16-0ubuntu1~bzr673

---

### Post by akoskm on 2011-08-17
I found a temporary workaround for this issue.
Open dconf-editor and from com.canonical.unity-2d.panel.applets value delete the  '!legacytray':
**['!homebutton', '!separator', 'appname', 'indicator']**.
I'm not sure for what is it used for but removing it makes everything work like before.

---

### Post by lucazade on 2011-08-17
> **akoskm said:**
> I found a temporary workaround for this issue.
Open dconf-editor and from com.canonical.unity-2d.panel.applets value delete the  '!legacytray':
**['!homebutton', '!separator', 'appname', 'indicator']**.
I'm not sure for what is it used for but removing it makes everything work like before.

Nice find! I'll try it :)

---

### Post by akoskm on 2011-08-17
'!legacytray' shows the systray for applications which have no integration so far in the indicator.
The bug is that the **expanding** property of com.canonical.unity-2d.panel doesn't work as expected, it says:
[I]If this property names a valid applet from the list in the applets property, then this
        applet will be setup so that it tries to use all the panel space that remains empty after
        the other applets have resized themselves to display their content.[/I]
It is using more than the available space on the panel. Simply to reproduce:
1. open dconf-editor
2. navigate to **com.canonical.unity-2d.panel**
3. set applets to ['!homebutton', '!separator', 'appname', '!legacytray', 'indicator', 'indicator']
4. open an application which have a bit longer titlebar (usually a web browser with long <title> pages)
5. point to the title bar on the panel > the applications menu comes up
6. move out with mouse from the panel area > the expanding applet used much more space that the available

EDIT: the bug tracker says [Fix Committed]("https://bugs.launchpad.net/unity-2d/+bug/827673") \o/

---

