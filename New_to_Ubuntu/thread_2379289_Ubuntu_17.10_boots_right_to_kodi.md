---
title: "Ubuntu 17.10 boots right to kodi"
date: 2017-12-03
forum: New to Ubuntu
---

### Post by kyle-amsoil on 2017-12-03
I am somewhat new to linux so I apologize for my ignorance in advance. I have searched online for hours to try and fix my problem with no results. I installed Ubuntu 17.10 and got everything all set up and was working great. Started kodi up this morning and when I went to close it the pc restarted and booted right back into kodi. Now I can not figure out how to get back to my desktop. No mater what I do It boots right back to kodi. I have tried to open terminal with hot keys (alt f2, ctrl alt t, ctrl alt function) with no luck. Any help would be greatly appreciated. I really dont want to start all over!!!!

---

### Post by kyle-amsoil on 2017-12-03
Was able to get to terminal using Ctrl alt f1 and remove Kodi from the system. Still have no idea why it was auto booting to Kodi though?

---

### Post by SuperFreak on 2017-12-03
If Kodi was one of the start up programs this might explain it. On my Mint PC startup applications are under preferences

---

### Post by again? on 2017-12-04
Have you enabled autologin?
Kodi also installs a standalone session that can be chosen at the greeter.
If you are taken to the login greeter when you exit kodi, then you are in the kodi session.
Choose your session at the greeter.

---

### Post by kyle-amsoil on 2017-12-04
Auto login is not enabled. When I install kodi, if I don't open it pc works fine. When I open and set up Kodi it crashes after being in it for a while. After it crashes it will only boot to Kodi. As soon as I turn pc on it goes to Kodi. No login screen. I am able to use Ctrl alt f2 and remove Kodi. That is the only way I have found to get back to desktop. I checked to see if Kodi is listed in start up programs and it is not. If it is going to the standalone session like guber2 said, how do I prevent this?

---

### Post by again? on 2017-12-04
That's odd. I don't see how you would bypass the login greeter on a reboot if autologin is not enabled.
Is this the only operating system installed on this computer?

I don't  use kodi but installed it in 17.10 to test.
Starts ok here.

Behaves just like a normal fullscreen window and can be minimized with Super+d.
Tested in the "Ubuntu" and "ubuntu-xorg sessions".

How did you install kodi?
Did it ever start and now fails to start after configuring?

Posting the output of these commands while logged into your normal desktop session will help.
```
lsb_release -a
echo $DESKTOP_SESSION
apt policy kodi
```

---

### Post by vasa1 on 2017-12-04
Similar thread: [https://ubuntuforums.org/showthread.php?t=2379317](https://ubuntuforums.org/showthread.php?t=2379317)

---

### Post by sp40140 on 2017-12-05
Like a user above said, Kodi has a desktop session. So, just like you can install xfce, lxde sessions on regular ubuntu and you can select one of them at the log-in screen. All you have to do is select your regular desktop session from the dropdown and you will be back to normal.

---

### Post by kyle-amsoil on 2017-12-05
I attached a screenshot of your request guber2. Kodi works fine until I install a build on it such as misfit mods. Even after that it is fine until it crashes. I can close kodi like normal until then. once it crashes (freezes) and I am forced to hard shutdown the pc, it boots straight to kodi. When you try to exit kodi it just restarts kodi. I will try and get video with my phone to show it crashing and then restart.

---

### Post by again? on 2017-12-06
Can't get kodi to crash here.
I would test in the "ubuntu-xorg" session.
...and just for good measure make sure you don't have any broken packages.
```
sudo apt update
sudo apt install -f
sudo apt **full-upgrade**
```
> **upgrade** is used to install available upgrades of all packages currently installed on the system from the sources configured via sources.list. 
New packages will be installed if required to satisfy dependencies, but existing packages will never be removed. 
If an upgrade for a package requires the remove of an installed package the upgrade for this package isn't performed.

**full-upgrade** performs the function of upgrade but will remove currently installed packages if this is needed to upgrade the system as a whole.

---

### Post by kyle-amsoil on 2017-12-07
[https://drive.google.com/open?id=1LqDZ2OcCTiOtklrJNnINBHumiz-IUKqE](https://drive.google.com/open?id=1LqDZ2OcCTiOtklrJNnINBHumiz-IUKqE)

Not sure if im allowed to share links here but this has screen recordings of me installing kodi, opening and running kodi, and what happens after it crashes.

---

### Post by SuperFreak on 2017-12-07
If you press the shift key when booting does it get you into the GRUB menu. That might help you see if there are any login options aside from Kodi
Just a thought

---

### Post by again? on 2017-12-07
> **kyle-amsoil said:**
> [https://drive.google.com/open?id=1LqDZ2OcCTiOtklrJNnINBHumiz-IUKqE](https://drive.google.com/open?id=1LqDZ2OcCTiOtklrJNnINBHumiz-IUKqE)

Not sure if im allowed to share links here but this has screen recordings of me installing kodi, opening and running kodi, and what happens after it crashes.

Watched the videos.
To be honest I can't really tell what's going on.

Does kodi need to be restarted after installing the add-on or is that an error message?
I would try installing add-on again and use windowed mode.(you can toggle with backslash key above Enter key)
When you get the "force close" message , quit kodi using the right click launcher menu.
Then restart kodi.

Did you have an older version of kodi installed before installing the ppa version?
Are you using a stable or development release?
From the [kodi wiki]("http://kodi.wiki/view/HOW-TO:Install_Kodi_for_Linux")
> Some (later) Ubuntu versions include Kodi built by Ubuntu themselves. 
If you have installed Ubuntu Kodi, please remove the packages "kodi kodi-bin kodi-data" before trying to install team-xbmc PPA packages.

---

### Post by kyle-amsoil on 2017-12-08
When you see the force close that is just me showing that I can quit Kodi normally at that point. It does not crash until I go to play the music. When I pushed play the screen froze but the recording did not show that. I can also restart the PC and it will start normally. It's not until after the screen freezes that I can no longer boot to desktop

---

