---
title: "[SOLVED] Forced to use low graphics mode after installing KDE on hardy"
date: 2008-08-05
forum: New to Ubuntu
---

### Post by Anticitizen2 on 2008-08-05
I decided to change my old dell inspiron 9100 laptop over to a linux box  and installed hardy ubuntu on it.  After seeing the spiffiness of the latest version of KDE, I decided to install it.  So, I followed a guide I found on this website, and it worked...sort of.  I can use the KDE, but it is forced to a low res.

Before the install I was able to use native resolution for my screen and to the best of my knowledge, the video card (Mobility radeon 9800) drivers were installed correctly.  I used EnvyNG to do this.  In addition to the native res, the more 3D screensavers were running smoothing, implying hardware acceleration (i think).  After the installation of KDE, during the reboot, a box came up saying that the video card and display where not being detected correctly and I would have to use low res mode.

There is an option at this point to configure, but if I do not check the "always use low res" box and click continue, the screen goes black and as far as I know nothing else can be done with it and I have to restart.  I would greatly appreciate any help I can get on this, and am happy to provide any additional information.

---

### Post by peakshysteria on 2008-08-05
This should work:> **peakshysteria said:**
> ```
sudo displayconfig-gtk
```

And adjust the resolution.

(alt: System --> Prefrences --> Main menu --> Other --> Check screens and graphics and you'll find it under: Applications --> Others)

:)

---

### Post by Anticitizen2 on 2008-08-05
Im not sure you are understanding what is going on.  I cannot change the resolution at all.  In order to get to the desktop I have to use the low res mode because the video card or display is not detecting correctly after installing KDE.  Thanks for the help though.

---

### Post by Anticitizen2 on 2008-08-05
bumping to prevent burial

---

### Post by peakshysteria on 2008-08-06
So you can't open any programs after you have to go into low resolution? Don't you see your desktop at all? The black screen issue is mentioned several places in the forums. This is an old ATI problem which is fixed for some time ago. What driver are you using? It sounds like Envy isn't using the latest driver! You might be better of with another way to install the driver. And please give us some more details. Which Kubuntu are you running?

[http://ge.ubuntuforums.com/tags.php?tag=black+screen](http://ge.ubuntuforums.com/tags.php?tag=black+screen) just to mention a few. Google gives you more.

---

### Post by Anticitizen2 on 2008-08-06
> **peakshysteria said:**
> So you can't open any programs after you have to go into low resolution? Don't you see your desktop at all? The black screen issue is mentioned several places in the forums. This is an old ATI problem which is fixed for some time ago. What driver are you using? It sounds like Envy isn't using the latest driver! You might be better of with another way to install the driver. And please give us some more details. Which Kubuntu are you running?

[http://ge.ubuntuforums.com/tags.php?tag=black+screen](http://ge.ubuntuforums.com/tags.php?tag=black+screen) just to mention a few. Google gives you more.
I will try one of the other ways to install the drivers, thanks for the advice.  

I'm not running a version of kubuntu, I started with ubuntu 8.04 and installed KDE 4.1 by following a guide I found on the forums.  When I restarted after this, a message came up after the new kubuntu splash screen saying that the video card and displays were not being detected correctly and in order to continue you have to check the "run in low graphics mode" box.  If you wait for too long at this point the screen will go black and you have to restart.  Before I installed KDE everything was working fine, and after I am limited to 800x600 resolution, but I can see the desktop, and in the resolution settings the screen is detected as unknown.  Pressing "detect displays does nothing.

[version of ubuntu is the 32bit one, thought this might help]

Thanks for the help so far.

---

### Post by peakshysteria on 2008-08-06
Then once again this should work:> **peakshysteria said:**
> Open up a terminal and:```
sudo displayconfig-gtk
```

And adjust the resolution.

Or you could go to: System --> Prefrences --> Main menu --> Other --> Check screens and graphics and you'll find it under: Applications --> Others

:)

And whats the output from ```
lspci -nn | grep VGA
``` and```
fglrxinfo
```

---

### Post by Anticitizen2 on 2008-08-06
> **peakshysteria said:**
> Then once again this should work:

And whats the output from ```
lspci -nn | grep VGA
``` and```
fglrxinfo
```

output from the first command:
```
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc M18 JN [Radeon Mobility 9800] [1002:4a4e]
 
```

output from the second
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY RADEON 9800
OpenGL version string: 2.1.7412 Release
 
```

---

### Post by peakshysteria on 2008-08-06
Hm, then all seems good. Have you tried to change the resolution like I mentioned above?
[[img]http://bildr.no/thumb/236351.jpeg[/img]](http://bildr.no/view/236351)
You might have to adjust the resolution one step at a time. This worked for me. If all fails you might have to reconfigure your xorg with ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` But I really don't think you have to go that way now since the driver is working. Try the screens and graphics manager and see how it goes.

Or you could flip through some of these: [http://ubuntuforums.org/search.php?searchid=45813402](http://ubuntuforums.org/search.php?searchid=45813402)

---

### Post by Anticitizen2 on 2008-08-06
I tried the command you gave to get to the screen and graphics preferences, and I can change the resolution from there.  However, when I set the resolution to native, it does not scale things correctly so the native resolution does not fit on the screen.  It still looks like 800x600, and it just expands the edges past the size of the screen.

I may just reinstall ubuntu and try again.  I'm pretty new to linux and I dont know how to fix most problems, so if I haven't done much on a new install I usually just wipe it and try again.

---

### Post by peakshysteria on 2008-08-06
The install really is just 30 minutes. And if you like KDE you could go for [Kubuntu]("http://www.kubuntu.org/"). Anyway I'm really sure you're not far from solving this irritating but trivial problem.

---

### Post by Anticitizen2 on 2008-08-06
> **peakshysteria said:**
> The install really is just 30 minutes. And if you like KDE you could go for [Kubuntu]("http://www.kubuntu.org/"). Anyway I'm really sure you're not far from solving this irritating but trivial problem.

Thanks for the help, setting to solved.

---

