---
title: "Problem removing animations"
date: 2014-11-09
forum: New to Ubuntu
---

### Post by skootar2 on 2014-11-09
I was generally pleased with my test of 14.04 until I tried to remove the desktop animations.

This issue leads to the following set of questions in order:

1. well what desktop is installed by default? No clue. 

2. after a search on animations, I assumed unity-tweak-tool was what I needed, so I installed it

3. I tried turning off animations using General in tweak tool. This didn't work. The animations were still there (opening app, closing, etc). Not only that, doing this deleted all my left side app icons. They seem to be gone for good. I had only added terminal, mysql workbench, but still it's a real problem. Flipping the tweak setting for animation seems to have no effect at all. Plus I can no longer place new icons on the tool bar or whatever it's called.

How can I get my original icons back? How can I determine the desktop manager name and version? And then how can I disable animations, they are way too slow. I tried searching for this but it's a real research project. And I was so happy at first with 14.04.

---

### Post by skootar2 on 2014-11-09
I found that "unity --reset-icons" restored the out of the box icons, but it threw up some errors, then the desktop froze completely. I just turned off the computer power. That's weird.

After restart I just added back the icons I had added before. 

I guess I don't dare run the tweaker app again.

---

### Post by grahammechanical on 2014-11-09
I do not understand what you mean by "animations."

I wonder if your hardware is up to running Ubuntu. Which, by the way, uses the Unity user interface and would be Unity 7 for Ubuntu 14.04. I cannot say what iteration of Unity 7 is used in Ubuntu 14.04 as I have moved on to 14.10 and then beyond onto the development version of Ubuntu 15.04. Search for unity in the software centre and click More Info and you can find out the full version number and all the other parts of the system that are attached to Unity. On my system it is Unity 7.3.1.

Do not remove Unity without first installing an alternative desktop. 

Ubuntu is built on Debian and uses the Gnome 3 desktop environment with the Compiz compositor/window manager and Unity 7 as a Compiz plugin. If you really want to break Ubuntu install Compiz Configuration Settings Manager (CCSM) and use it to disable the Unity plugin and then reboot.

Tweak tools, even official tools like CCSM can do great damage. We are warned about this. When we use tweak tools to change settings weird things can happen.

Regards.

---

### Post by skootar2 on 2014-11-09
Okay thanks for the details. "Animations" in this case refer to the fade in/fade out effect when menus open/close, or windows open/close, etc. I prefer to have everything just appear instantly. On Windows there is one universal setting for the shell animation effects, but it appears in unity that this is not the case, not sure.
BTW, I am running in VirtualBox, and 14.04 runs really well, I am very happy with it. I was able to set up samba file sharing, music and video in a couple of hours, a new record for me.

---

### Post by CantankRus on 2014-11-10
You can use **compizconfig-settings-manager** (ccsm)to adjust the speed of animations or
disable the animations plugin completely.
[ATTACH=CONFIG]257863[/ATTACH]

If you want to use ccsm you may want to install an alternative DE first if you need to recover.
CCSM in the most part works but sometimes fails to load properly
leaving you unable to access a terminal or the unity launcher or panel.

**_Do this before using ccsm_**
Send a terminal shortcut to your desktop with this terminal command.
```
cp /usr/share/applications/gnome-terminal.desktop ~/Desktop && chmod +x ~/Desktop/gnome-terminal.desktop
```
Install alternate DE that you can access at the login menu.
```
sudo apt-get --no-install-recommends install gnome-panel
```
This gives you 2 more login choices if needed...
[LIST]
[*]Gnome Flashback (metacity)
[*]Gnome Flashback (compiz)
[/LIST]
Use the Metacity session for recovery.
[ATTACH=CONFIG]257864[/ATTACH] [ATTACH=CONFIG]257865[/ATTACH]


_**Recovery commands**_
If unity hasn't reloaded properly when using ccsm, reload with(Only use i ubuntu/unity session and can take up to 30 secs to run. May also need to repeat.)
```
setsid unity
```

Still doesn't reload, **reset** compiz.
Run in any session.
```
dconf reset -f /org/compiz/
```

If you are in the ubunt/unity session you can combine the commands...
```
dconf reset -f /org/compiz/ && setsid unity
```

If you have no access to the logout menu, run
```
kill -9 -1
```

A useful application is wmctrl.
```
sudo apt-get install wmctrl
```

Use this command to show your current session and window manager...
```
echo $DESKTOP_SESSION && wmctrl -m | awk '/Name:/{print $2}'
```

---

