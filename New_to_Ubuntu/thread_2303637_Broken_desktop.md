---
title: "Broken desktop"
date: 2015-11-20
forum: New to Ubuntu
---

### Post by c10h15n2 on 2015-11-20
Hi. My wallpaper disappeared and the desktop keeps showing the last windows that I used. For example, if I open nautilus and then minimize it, I will get something like a screenshot on the desktop of that nautilus window. When I move it, I get this trail thing: [img]("http://i.imgur.com/lsiEeBd.png")

I've recently done some changes in "Ubuntu Tweak" (changed the theme, mouse pointer and stuff like that) so maybe I did something wrong there ? Someone told me to run the commands below, but it didn't work.

```
[COLOR=#111111][FONT=Consolas]$ sudo apt-get autoremove ubuntu-desktop [/FONT][/COLOR]$ sudo apt-get autoremove unity 
$ sudo apt-get update 
$ sudo apt-get install unity-2d 
$ sudo apt-get install unity
$ sudo apt-get install ubuntu-desktop 
$ sudo apt-get dist-upgrade  [COLOR=#111111][FONT=Consolas]$ sudo shutdown -r

[/FONT][/COLOR]$ [COLOR=#111111][FONT=Consolas]setsid unity [/FONT][/COLOR]
```

thank you.

---

### Post by grahammechanical on 2015-11-20
You should tell us the version of Ubuntu you are using and the hardware specification of the machine. Of importance is the video adapter and how much video memory it has.

Ubuntu has a fall back open source video driver called llvmpipe that is used to give an approximation of Unity 3D on video adapters that cannot do hardware accelerated 3D rendering. If llvmpipe is being used it can give the affect that you see. Especially when the video adapter does not have sufficient video memory.

Oh, by the way, Unity 2D is no longer being developed. Unity 2D was used when the video adapter could not run Unity 3D and now that Ubuntu has llvmpipe Unity 2D should not be needed.

And yes, tools like Ubuntu Tweak are powerful enough to break things. It is always best to make one change at a time and keep a list of the changes we make so that we can revert them.

Regards.

---

### Post by c10h15n2 on 2015-11-20
Ubuntu 15.10, Intel Core i5-3230M 2.60GHz, 8 GB memory and graphics: Intel HD 4400 (or 4000; I can't remember correctly...) + NVIDIA GeForce GT 740M 2GB. 
I'm using 3 tools for customization: Ubuntu Tweak, Unity Tweak tool and Gnome Tweak Tool. I can't remember which settings I modified in each one of them :(.

---

### Post by Frogs Hair on 2015-11-21
Unity 2D was last used on the 12.04 release and not an option for later releases. Try the following and reboot.

```
sudo apt-get autoremove
``` ```
sudo apt-get update

``````
sudo apt-get upgrade
``````
 sudo apt-get install ubuntu-desktop

``` I would not recommend ubuntu-tweak on releases later than 14.04.

---

### Post by c10h15n2 on 2015-11-21
It doesn't work :(. [screenshot]("http://i.imgur.com/OLYXoe8.png") (I can still right click on the desktop, create folders and access them. The only problem is the wallpaper, which is shown in the screenshots.)

---

### Post by Frogs Hair on 2015-11-21
Try the following.

```
 [COLOR=#000000][FONT=UbuntuBeta Mono]sudo apt-get install dconf-editor[/FONT][/COLOR]
``` ```
[COLOR=#666666][FONT=Consolas]dconf reset -f /org/compiz/[/FONT][/COLOR]
```

---

### Post by c10h15n2 on 2015-11-21
Still nothing... That command just made the sidebar go back to the default settings.

---

### Post by deadflowr on 2015-11-21
Since you have gnome-tweak-tool installed, do you also have gnome-shell installed?
(it used to be the default that installing gnome tweak tool also installed gnome shell, but I'm not sure anymore)

You can tell by logging out and checking the session icon if there is an extra session for gnome.
(The session icon would be inside the username/password box, in that boxes top right corner)

If it does exist, try selecting it and logging into that session.
See if the odd screen artifacts exist in that session as well.

To me it looks more like a system graphics problem, typically related to funky drivers than the desktop session in use.

Sidenote:
In case something about this goes belly up try these steps to kill it and get back to the login screen:
press ctrl +alt + F1 > this gives you access to a console
then login like normal > user and password
then run
```
sudo systemctl restart lightdm
```
this will bring you back to the login screen, where you can reset it to log into unity (Ubuntu).

---

### Post by c10h15n2 on 2015-11-21
> **deadflowr said:**
> [COLOR=#000000]You can tell by logging out and checking the session icon if there is an extra session for gnome.[/COLOR]
[COLOR=#000000](The session icon would be inside the username/password box, in that boxes top right corner)[/COLOR]
 

No, nothing's there.

---

### Post by c10h15n2 on 2015-11-23
Would it make things better if I install other desktop environment ? If yes, what alternative to Unity should I choose ?

---

### Post by deadflowr on 2015-11-23
> **c10h15n2 said:**
> Would it make things better if I install other desktop environment ? If yes, what alternative to Unity should I choose ?
Sorry for the delay, meant to respond earlier.

Perhaps look into a gnome variant.
Either gnome-flashback or gnome shell.
Both work quite well with the existing Ubuntu system.
For gnome-shell
```
sudo apt-get install gnome-shell
```
for gnome-flashback
```
sudo apt-get install gnome-panel
```
after install, you should only need to logout and select the session as suggested earlier.
(usually there is no need to reboot)

---

### Post by c10h15n2 on 2015-11-24
well, I did what you said and it worked perfectly after logging out and back in again, but after reboot, it gets stuck at this screen: [img]("http://i.imgur.com/rGMPA1f.jpg") (I can't even use the keyboard). I took a picture of how that screen looks like after a second reboot (because I see they are different): [img2]("http://i.imgur.com/TgY02VU.jpg") .

---

### Post by deadflowr on 2015-11-24
Unfortunately if seems you've been hit with either of these bugs:
[https://bugs.launchpad.net/ubuntu/+source/tp-smapi/+bug/814380](https://bugs.launchpad.net/ubuntu/+source/tp-smapi/+bug/814380)
[https://bugs.launchpad.net/ubuntu/+source/tp-smapi/+bug/1036075](https://bugs.launchpad.net/ubuntu/+source/tp-smapi/+bug/1036075)
or at least a very similar bug.

---

### Post by c10h15n2 on 2015-11-24
lucky me... So I can't do anything now ? I can live with that broken desktop, but how do I get Ubuntu to start normally?

---

