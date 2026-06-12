---
title: "How to roll your own desktop environment!"
date: 2010-05-26
forum: Outdated Tutorials &amp; Tips
---

### Post by aeron005 on 2010-05-26
I don't know about you, but for me, I hated having to configure GNOME's startup process through the Startup Applications dialogs, which seemed to only work *sometimes*, and also left me in the dark about what else is started by gnome-session. I also didn't like the idea of trusting everything to the session manager (What if it couldn't restore my session for some reason? What if gnome-session made it impossible for me to deduce exactly what was preventing me from logging in?)

Regardless, I decided to hack together an editable script that would allow me to fine-tune my startup process in a clear and precise manner. What follows is the steps I took to get my desktop Just The Way I Like It™ (and now you can do it too!) :)

First, we are going to create our startup script. You can put this file anywhere but if you are the only person using your computer, I would recommend putting it in your home directory for easy access. So to get started:
```
cd ~
gedit .csession
```
Of course you can name it whatever you want, just make sure you know where you save it or you might screw yourself over in the long run. At the top of the file put:
```
#!/bin/bash
```
We need this for obvious reasons. Next, we're going to start adding our startup programs one line at a time. If you want to get an idea of what currently auto-starts, go to Preferences->Startup Applications on the menu. Start thinking about what you want to keep in your custom session. I started out with the nVidia settings stuff, as this seemed pretty important to me:
```
sh -c '/usr/bin/nvidia-settings --load-config-only' &
```
Make sure to append an & after each line to fork the processes (otherwise they would run sequentially instead of in parallel). Next I started the network applet:
```
nm-applet --sm-disable &
```
Another important one was the gnome settings daemon. If you don't put this your appearance settings won't be loaded, among other things.
```
gnome-settings-daemon &
```
If you want to receive updates:
```
update-notifier &
```
Now we've got some of the basic stuff, but it's not really usable at this point. So! Now it's time to build our desktop environment! The first thing I decided on was a panel/dock. I chose AWN, but nothing's stopping you from using your own favorite panel. There are tons to choose from, so try a few out!
```
avant-window-navigator --startup &
```
If you want a desktop wallpaper and/or icons, you will have to get a special program to do that for you, as most window managers don't provide it themselves. Most file managers can manage your desktop (and many do, whether you like it or not), but there are also standalone wallpaper managers such as feh. My personal preference is good ole' Nautilus, since I'm gonna be using it as my main file manager anyway.
```
nautilus --no-default-window &
```
Now for the most important part of any graphical desktop (save X itself): the window manager. There are quite a few to choose from, so choose wisely. If you are going for minimalism, the *boxes are an excellent choice and they are still very functional. You can also borrow from an existing desktop environment and use a window manager such as metacity or compiz fusion. The one I keep coming back to, however, is xfwm4, for it's light weight and simple compositing support.
```
exec xfwm4 &
```
If this is the last line in your file, you don't have to put the final &. But I'm gonna take this one step further, and add a bit of icing to the cake:
```
sleep 10 && conky
```
Okay, NOW it's complete! (By the way, the sleep command just helps keep conky from clashing with the window manager, as this tends to happen on startup.)

Now we have our completed script (save it!), but how can we make this a session that we can choose from gdm? Well, first, we have to make the script executable.
```
chmod +x .csession
```

Next, we must create a session file. For this we need su:
```
gksudo gedit /usr/share/xsessions/csession.desktop
```

Of course, this can be named anything, just make sure it's .desktop and under /usr/share/xsessions/. Inside the file, we'll fill in the details to give us a fully functional session.

Here's the contents of my file:
```
[Desktop Entry]
Name=CSession
Comment=A custom session!
Exec=/home/mitchell/.csession
TryExec=/home/mitchell/.csession
Icon=
Type=Application
X-Ubuntu-Gettext-Domain=csession-1.0

[Window Manager]
SessionManaged=true
```
I simply copied the contents of the gnome session and changed the name, exec, and comment. Now, make sure everything is saved, and logout. Type in your password, but before you hit enter check the session list on the bottom panel. If your entry is valid you will see your fresh session in the list. Select it and take it for a spin! Now for the obligatory screenshot:

[[IMG]http://img245.imageshack.us/img245/2343/screenshotev.png[/IMG]]("http://img34.imageshack.us/img34/5344/screenshotmr.png")

I hope you enjoyed this tutorial! If you come up with something cool, share it with the rest of us or post a screenshot! Any other questions/comments/criticisms are welcome. Happy hacking!

---

### Post by bapoumba on 2010-05-28
Welcome to the T&T :)

---

