---
title: "Unity gone, no app access, reinstall?"
date: 2012-02-10
forum: New to Ubuntu
---

### Post by Jonathan Rung on 2012-02-10
Hello,

I just finished installing Ubuntu (11.10 on a toshiba notebook).  After looking around the desktop, system settings, and Unity, I launched the ubuntu software application to browse the selection.  Some dock replacements caught my eye, because I wasn't really enjoying the preconfigured dock that lines the left side of the screen.  I installed one of them and liked it, but it didn't replace the Unity dock like I expected; they just sat next to one another.

SO, after consulting google, I downloaded another program from the Ubuntu software center, (I think it was called "config compiz" or just "Compiz"), with the intention of disabling the preconfigured dock.  Unfortunately, before I got that far, I started playing around with some of the cool UI settings, like enabling a wobble effect on the windows.

I only changed about three or four options, and this all took place in less than a sixty second window, so I don't even remember which options I enabled or disabled, but the last thing that I changed had the undesired effect of removing the.. "bezel" of application windows, the dock on the top of the screen that displays the time, your name, wifi, etc, and also the p reconfigured dock on the left.  I couldn't access anything so I just pressed the power button on my laptop and chose restart from the menu.

After booting back up, applications regained their "bezels" (is there a word for them? I mean the part of the window that has the X to close the window, the _ to hide the window, etc) but the side dock and the top dock remained missing.  The problem is that I cannot access anything now.  The new dock I installed is basically empty, and none of the applets launch a list of programs.  I can create a window and look at system files, but that's it.  If I could just open a terminal window, I could probably find the location of the Compiz program and launch it, but I can't even find a way to launch terminal.  I should also mention that the "Meta" key does not seem to be working either, but it wasn't working before I made the changes, either.

I installed ubuntu in a dual-boot configuration, so fortunately I can at least run windows 7 (what I'm currently using).  Is there anything I can do to return to stock settings, or is there any way I can launch an application in a way I haven't already tried?  Or should I just format the ubuntu partition in windows and completely reinstall everything?

**Thanks a lot for any help!**  I tried searching, and I'm sure this question has come up before, but I get search overload with all my searches.

---

### Post by d4m1r on 2012-02-10
> **Jonathan Rung said:**
> Hello,

I just finished installing Ubuntu (11.10 on a toshiba notebook).  After looking around the desktop, system settings, and Unity, I launched the ubuntu software application to browse the selection.  Some dock replacements caught my eye, because I wasn't really enjoying the preconfigured dock that lines the left side of the screen.  I installed one of them and liked it, but it didn't replace the Unity dock like I expected; they just sat next to one another.

SO, after consulting google, I downloaded another program from the Ubuntu software center, (I think it was called "config compiz" or just "Compiz"), with the intention of disabling the preconfigured dock.  Unfortunately, before I got that far, I started playing around with some of the cool UI settings, like enabling a wobble effect on the windows.

I only changed about three or four options, and this all took place in less than a sixty second window, so I don't even remember which options I enabled or disabled, but the last thing that I changed had the undesired effect of removing the.. "bezel" of application windows, the dock on the top of the screen that displays the time, your name, wifi, etc, and also the p reconfigured dock on the left.  I couldn't access anything so I just pressed the power button on my laptop and chose restart from the menu.

After booting back up, applications regained their "bezels" (is there a word for them? I mean the part of the window that has the X to close the window, the _ to hide the window, etc) but the side dock and the top dock remained missing.  The problem is that I cannot access anything now.  The new dock I installed is basically empty, and none of the applets launch a list of programs.  I can create a window and look at system files, but that's it.  If I could just open a terminal window, I could probably find the location of the Compiz program and launch it, but I can't even find a way to launch terminal.  I should also mention that the "Meta" key does not seem to be working either, but it wasn't working before I made the changes, either.

I installed ubuntu in a dual-boot configuration, so fortunately I can at least run windows 7 (what I'm currently using).  Is there anything I can do to return to stock settings, or is there any way I can launch an application in a way I haven't already tried?  Or should I just format the ubuntu partition in windows and completely reinstall everything?

**Thanks a lot for any help!**  I tried searching, and I'm sure this question has come up before, but I get search overload with all my searches.

1) I think "bezel" = title bar in your case (top of an unminimized window)

2) Bar at the top with time/wifi/etc is called the user bar or global application bar

3) You can launch the terminal and any installed applications by using CTRL + ALT + T (ex: just typing firefox should launch firefox, software-center for the software center and etc)

4) Google "reinstalling gdm" (gnome desktop manager) or "reinstalling unity desktop"

Oh and to launch the compiz tool I think you are talking about, just type ccsm into the terminal.

---

### Post by Jonathan Rung on 2012-02-10
> **d4m1r said:**
> 1) I think "bezel" = title bar in your case (top of an unminimized window)

2) Bar at the top with time/wifi/etc is called the user bar or global application bar

3) You can launch the terminal and any installed applications by using CTRL + ALT + T (ex: just typing firefox should launch firefox, software-center for the software center and etc)

4) Google "reinstalling gdm" (gnome desktop manager) or "reinstalling unity desktop"

Oh and to launch the compiz tool I think you are talking about, just type ccsm into the terminal.

Thanks so much!  That answers all my questions.  

As far as re-installing Unity or gnome: I like unity, but I don't like that dock... In your opinion, should I try to do what I was doing earlier and replace the dock with something else, or should I just go with gnome?  Is that dock like a critical part of unity?  I would like to keep unity and use Cairo dock, but not if switching docks will significantly hurt UI stability.

---

### Post by Frogs Hair on 2012-02-10
You may want to check this  out .[http://www.webupd8.org/2011/09/cairo-dock-240-released-with-custom.html](http://www.webupd8.org/2011/09/cairo-dock-240-released-with-custom.html)

---

### Post by Paqman on 2012-02-10
Try opening a terminal (Ctrl-Alt-T) and doing:
```
unity --reset
```
If that doesn't work, you could cheat by creating a new account (make sure you give it admin rights) and then deleting your current one.

As for Unity, you can set the launcher to hide, but you can't actually get rid of it.

---

### Post by Jonathan Rung on 2012-02-10
Wow, I have so much to learn!  I had no idea how the GUIs even worked; I always thought Linux was basically like Mac OSX.  Earlier today I was beginning to think it was just convoluted, but now I'm blown away at how deeply I can customize this.

You have all been incredibly helpful, thanks so much!

---

### Post by d4m1r on 2012-02-10
> **Jonathan Rung said:**
> Thanks so much!  That answers all my questions.  

As far as re-installing Unity or gnome: I like unity, but I don't like that dock... In your opinion, should I try to do what I was doing earlier and replace the dock with something else, or should I just go with gnome?  Is that dock like a critical part of unity?  I would like to keep unity and use Cairo dock, but not if switching docks will significantly hurt UI stability.

No problem, I only switched to Ubuntu at home a few months ago too ;)

As for what I think you should do, it is really up to how you work and what you like graphics wise, but from the sounds of it (and 1st hand experience at how much troubleshooting linux desktop issues SUCKS) I'd recommend sticking to Unity 3D which is the default. Those other dock applications are flaky in terms of support sometimes and CCSM is especially...Can seriously screw stuff up. If you still haven't fixed the problem, creating a new user is easer than reinstalling as it creates a new "instance" of that desktop program (resets Unity settings for a new user essentially).

If you REALLY hate the dock (which IS Unity), google how to "install Gnome 3 on 11.10" or something along those lines and only that is really officially supported apart from Unity. Any guide should include pictures as well so you can decide if you like the look or not.

---

### Post by sadaruwan12 on 2012-02-11
Well the same thing happened to me once but it was when I was starting to get a grip on unity what I did reinstalled from scratch.

If you're using unity be careful while playing around with the settings 'cos it might upset the unity set up.

The panel on the left is a very essential part of unity so it better be left alone until unity it self gives you a option to disable it.

if you want to customize the unity panel more better install unity 5 which has more customizing functions than the default version.

```

    sudo add-apt-repository ppa:unity-team/staging
    sudo apt-get update && sudo apt-get dist-upgrade

```


And yes MacOS is built on a BSD platform the platform is [Darwin]("http://en.wikipedia.org/wiki/GNU-Darwin") So there are differences and the other thing is that Linux is all about the user us you can do what every you want when ever you want 'cos the source is open.

So have target what you want your desktop to be and build toward that then it'll be blissful environment for you.

---

### Post by wildmanne39 on 2012-02-11
Hi, there is nothing wrong with using other docks with unity, I have since 11.04 came out without any problems.

I use awn launcher, I have the unity launcher hidden all the time which I did from ccsm.

I can even put awn launcher over the top of the unity launcher if I choose, but I like mine at the bottom.

Here is a link for resetting unity and compiz.
[http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html](http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html)

Link for setting up compiz without breaking unity.
[https://help.ubuntu.com/community/CompositeManager#preview](https://help.ubuntu.com/community/CompositeManager#preview)

How to set unity launcher to only open  when you hit the super key.

In the Unity plugin, set Reveal to Auto hide and the Reveal edge to None or Disabled. Screenshot shows that the edges are disabled so that it will not open ,you can tell because all around the little window it is in red, if it was set to open when the mouse was moved to the edge it would be in green. You do have to have ccsm installed to change unity plugin settings.

[COLOR="Red"]**Do not disable the unity plugin or change any other settings in compiz without reading the second link first.**[/COLOR]
I am including screenshots.
Thanks

---

