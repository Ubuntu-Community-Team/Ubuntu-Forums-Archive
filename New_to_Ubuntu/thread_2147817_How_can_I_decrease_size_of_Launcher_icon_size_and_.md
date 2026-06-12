---
title: "How can I decrease size of Launcher icon size and other things?"
date: 2013-05-23
forum: New to Ubuntu
---

### Post by Tjkhan on 2013-05-23
How to decrease size of Launcher icons? I can not use **MyUnity. **So please give me some other way.

Another thing, how can i make my desktop different? (not themes) any software? 

I am noob so please explain in details. 

Thank you.

---

### Post by marianoa on 2013-05-23
To change the size of the icons in the launcher you can go to "System settings" and then in "Appearance", there you should find a slider to set the size of the icons together with the wallpaper settings. I'm on 13.04

---

### Post by Maverick Meerkat on 2013-05-23
Hi Tjkhan,

Marianoa's advice is correct, but for additional "tweaks" I use the "Unity Tweak Tool" available in the Software Center.
I use that on my system running Ubuntu 13.04

Rick

---

### Post by Maverick Meerkat on 2013-05-23
Also...
If you right-click on the desktop, and select "Change Desktop Background" that will open the window Marianoa had mentioned.
Now, once you are there you will see a selection of different desktop backgrounds on the right. The first one, which has a little clock drawn on it, is a slideshow that changes throughout the day.
Above those thumbnails, you will see the tab "Wallpapers", if you click on that, you will then see that "Picture Folder" becomes available, allowing you to easily use any pictures you have stored in that folder as your desktop.

Below the thumbnails, you will see the "Theme" selector.
Below that, is the "Launcher icon size" selector.

Rick

---

### Post by newb85 on 2013-05-23
If you want your wallpaper to automatically change periodically from a list you choose, Wallch is a great program for that.  If you're using 13.04, it's in the repositories.  Otherwise, you can add their PPA like this:

```
sudo add-apt-repository ppa:wallch/3+
sudo apt-get update
```

Then you can install using Software Center, apt-get, Synaptic, or your preferred method.

---

### Post by Tjkhan on 2013-05-23
There is the problem. Below the thumbnails, "Theme" selector "Launcher icon size" selector doesnt show up. plz see the image below 

[IMG]http://i1278.photobucket.com/albums/y504/tjkhan1/no_zps13c381bc.jpeg[/IMG]

I updated all things and but nothing. This making me MAD :(

---

### Post by marianoa on 2013-05-23
What is your Ubuntu version? Maybe in older versions (even if they're not so old afterall) the slider is missing, in that case unity-tweak-tool or ubuntu-tweak should help you change the icons size in the launcher

---

### Post by Tjkhan on 2013-05-23
> **marianoa said:**
> What is your Ubuntu version? Maybe in older versions (even if they're not so old afterall) the slider is missing, in that case unity-tweak-tool or ubuntu-tweak should help you change the icons size in the launcher

Mine is 12.04
About tweak, not helping.

Did you try 12.04?
Is Ubuntu 13.04 better than 12.04? whats your opinion?

---

### Post by marianoa on 2013-05-23
What do you mean by "About tweak, not helping."? Did you try to install and use both unity-tweak-tool and ubuntu-tweak? Did you have problems in installing/using them?

As for installing a version more recent than 12.04, your current version is a LTS, it's meant to be more stable than non-LTS version. If you're a newbie and you have no big problems with 12.04 I'd suggest you stick to it. You can read more about LTS here
[https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)

---

### Post by Dave_L on 2013-05-23
> **Tjkhan said:**
> There is the problem. Below the thumbnails, "Theme" selector "Launcher icon size" selector doesnt show up. plz see the image below 

The selector is available if you're using Unity 3D, but not Unity 2D.

You can determine which with this command:
> echo $DESKTOP_SESSION

The output is "ubuntu-2d" for Unity 2D and "ubuntu" for Unity 3D.

---

### Post by Maverick Meerkat on 2013-05-23
Dave is right, I checked on my 12.04 computer and I have the icon size on it, so I must be running Unity 3D.

What you may want to try, is this... on the top of the Appearance window you posted a picture of, click on the "Behavior" tab.
It might allow you to turn on "Auto-hide" which gets the launcher off your screen completely, until you move the pointer over there.
I use this feature more than the size anyway.

Rick

---

### Post by Dave_L on 2013-05-23
I came across this article, but I cannot vouch for its accuracy or safety. Use it at your own risk:
[http://www.dedoimedo.com/computers/ubuntu-unity-2d-resize-launcher.html](http://www.dedoimedo.com/computers/ubuntu-unity-2d-resize-launcher.html)

---

### Post by deadflowr on 2013-05-23
The script and suggested method of using it [here]("http://ubuntuforums.org/showthread.php?t=1954637") works well enough for me on a not so great PC.

Whether you want to trust it or not is up to you.

---

### Post by Tjkhan on 2013-05-24
Thanks guys. Problem solved. Ubuntu 13.04 fixed everything. Facing no problem so far. ;)

---

