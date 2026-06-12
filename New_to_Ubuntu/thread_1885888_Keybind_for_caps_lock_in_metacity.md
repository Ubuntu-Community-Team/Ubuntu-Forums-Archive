---
title: "Keybind for caps lock in metacity"
date: 2011-11-24
forum: New to Ubuntu
---

### Post by igel_au on 2011-11-24
I'm trying to hack together a caps-lock notifier in the style of ayamaguerida's solution ( [http://ubuntuforums.org/showthread.php?t=1348042](http://ubuntuforums.org/showthread.php?t=1348042) ). The gist is that the Capslock key is bound to a script which displays a notification.

I want to do this but I'm running Unity 2d (Ubuntu 11.10 64-bit) on my netbook, so Compiz isn't already running. I've tried binding <caps> or <capslock> to run_command_1 in apps/metacity/global_keybindings using gconf editor, but it seems those key values aren't recognised.

Is it possible to bind capslock from metacity? Failing that, is it possible to run compiz on low-end hardware without a performance/battery life hit?

---

### Post by stinkeye on 2011-11-24
I use this script using the compiz method as shown in the link you provided.
> In your Compiz Configuration Settings Manager, click on the "Commands" icon.
 Choose the "Key Bindings" tab. For "Run Command 0", click the "Disabled" box.
 Choose "Enabled". Press the "Grab Key Combination" button and press your CAPS LOCK key.
 Compiz won't view CAPS LOCK as a key combination, so just X out of the box and CAPS LOCK should now be the key combination.


caps_notify {needs **sox** for the play command)
```
#!/bin/bash

value=$(xset -q | grep "Caps Lock:" | awk '{print $4}' | grep -c on)

if [ "$value" -eq "1" ]; 
then
   notify-send -i  "/usr/share/icons/gnome/48x48/devices/keyboard.png" "                    Caps Lock ON" &
   play -q /home/glen/Sounds/ting.wav



else
   notify-send -i  "/usr/share/icons/gnome/48x48/devices/keyboard.png" "                    Caps Lock OFF"
   
fi
```

If I login in to unity 2d with metacity as the window manager
it still works.
I used to change the mouse cursor to redglass as well 
when caps was on, but changing cursors is stuffed up lately.

You may also be interested in [**_[COLOR="DarkRed"]indicator-keylock[/COLOR]_**]("http://www.webupd8.org/2010/07/indicator-keylock-displays-keyboard.html")

---

### Post by igel_au on 2011-11-25
Thanks stinkeye.

Just to make it clear for anyone reading the thread, the answer to my original question is that you can use Compiz configuration tool to bind the caps lock key, no matter whether you use Compiz or not.

---

