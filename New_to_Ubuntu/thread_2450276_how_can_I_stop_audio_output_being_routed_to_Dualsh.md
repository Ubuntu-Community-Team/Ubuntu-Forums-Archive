---
title: "how can I stop audio output being routed to Dualshock 4 controller when plugged in?"
date: 2020-09-10
forum: New to Ubuntu
---

### Post by jcdenton1995 on 2020-09-10
Hello all,

When I plug in my Dualshock 4 controller the audio is automatically routed to its 3.5mm port, meaning I have to go to "settings > sound > output device" and change it back to my monitors speakers.

Can anyone tell me how to stop this? I've looked under /lib/udev/rules.d to try and find anything obvious, and have checked a few .rules files there, but no luck.

Thanks!

---

### Post by TheFu on 2020-09-10
PulseAudio thinks that any new audio device that shows up is the one you want to use. This is often wrong.
Have you tried setting the default in the "client.conf" file in your ~/.config/pulse/ directory?  An example is in /etc/pulse/client.conf.  Don't know if this will work or not. Worth a try.

Use 
```
pactl list short sinks
pactl list short sources
```
to see which exact names need to be used for the devices you have. They are long, as is typical from the SystemD guys.

---

### Post by Holger_Gehrke on 2020-09-10
The pulse audio module 'module-switch-on-connect' is responsible for setting newly connected audio devices as the default device. To (temporarily) inhibit this behaviour you can remove this module with 'pacmd unload-module module-switch-on-connect' before connecting the controller and re-enable it with  'pacmd load-module module-switch-on-connect'.

Holger

---

### Post by jcdenton1995 on 2020-09-11
Okay, so to help me understand, I would want to open the file "~/.config/pulse/*-default-sink" and change the contents to the name of my monitor that can be revealed with...```
pactl list short sinks
```Or is it the case that I need to open "/etc/pulse/client.conf" and append the monitors name to the following line...```
; default-sink =
```while also removing the semi-colon (as I believe this is the same as using a '#' to comment the line out?)

---

### Post by jcdenton1995 on 2020-09-11
would it be possible to set this command to run at startup, or would that somehow cause problems?

The reason I ask is that having to manually un-load and re-load the module is about as much work as going into settings and changing the audio output back to the monitor, but perhaps I could set the command to run at startup, because I don't have any other audio devices that I use with my computer at the moment.

---

### Post by CatKiller on 2020-09-11
> **jcdenton1995 said:**
> Okay, so to help me understand

So PulseAudio is pretty flexible, which means there are lots of ways to achieve what you're after.

As you now know, there's a PulseAudio module whose sole purpose is to go "hey, there's a new audio device, let's switch to it!" If you *never* want that to happen, you can stop that module from loading; there's a config file that loads all the modules and you'd just tell it not to load that one.

If you *like* that function, but don't like the audio output from your controller being used, each device has a profile for how audio should be routed to it - stereo, surround, whether there's a microphone, and so on. One of those profiles is "Disabled." That would stop it from ever being picked, but would still let the audio stream get moved to a Bluetooth headset, say. You used to be able to set that in Gnome's volume panel widget, but they took that function out; you can still use PulseAudio's own tools to do it, though. KDE still has the function in its widget.

KDE also has another function readily available, of setting the priority of audio devices for different classes of audio task. So you can have music preferring one device, voice calls preferring a different device, and system sounds on another, say.

---

### Post by Holger_Gehrke on 2020-09-11
> **jcdenton1995 said:**
> would it be possible to set this command to run at startup, or would that somehow cause problems?

The reason I ask is that having to manually un-load and re-load the module is about as much work as going into settings and changing the audio output back to the monitor, but perhaps I could set the command to run at startup, because I don't have any other audio devices that I use with my computer at the moment.

I thought more along the lines of a script and a .desktop-file to start the script
```

pacmd unload-module module-switch-on-connect
zenity --info --text 'Connect the controller now !'
pacmd load-module module-switch-on-connect

```
This would shut  off the automatic switching, wait for a click on the 'OK'-button of the info-dialog or the enter key being pressed and then reactivate automatic switching.

Or if you really don't want any automatic switching ever, you could just comment out the line loading that module in /etc/pulse/default.pa. You might want to add a comment to the file reminding you that you commented out the line and why. I always start such comments with my initials so I can easily grep for changes I made.

Holger

---

### Post by jcdenton1995 on 2020-09-15
Thanks! that would be a handy thing to have, I'll have a poke about and try it out.

---

### Post by jcdenton1995 on 2020-09-15
I'll take a look at this too. To be honest I don't really have any other audio devices so I could disable the module or edit the controllers profile. I'd probably go with the latter. Thanks for the help!

---

