---
title: "Program to change track of Banshee"
date: 2009-10-11
forum: Programming Talk
---

### Post by mattgaunt on 2009-10-11
Hey everyone,

I just want to play around with developing a little with Ubuntu and Android. Basically I want the phone to connect to my program running on my Ubuntu laptop, do a little authentication, then depending on messages change track, pause etc of banshee, or if possible, anything currently running, same as what happens when the multi media keys are pressed on my keyboard.

But I have never done anything effecting other programs before, only developed programs that keep themselves, so could anyone point me in the right direction or even any tutorials?

Many Thanks,
Matt

---

### Post by cszikszoy on 2009-10-11
You can use dbus to control the playback on banshee.  You're looking for org.bansheeproject.Banshee.PlaybackController and org.bansheeproject.Banshee.PlayerEngine

---

### Post by mattgaunt on 2009-10-12
Thank you so much did some Googling and found it, I just needed to know it was the DBus I needed to use, many thanks.

Matt

---

### Post by cszikszoy on 2009-10-12
If you need some more stuff to look at, take a look at the source for GNOME Do plugins ([http://launchpad.net/do-plugins](http://launchpad.net/do-plugins)).  There's a Banshee plugin in the source tree that does lots of stuff with Banshee over dbus.  It's written in C#, but should be pretty easily translatable to any other language.

---

### Post by SeanHodges on 2009-10-14
> **mattgaunt said:**
> Hey everyone,

I just want to play around with developing a little with Ubuntu and Android. Basically I want the phone to connect to my program running on my Ubuntu laptop, do a little authentication, then depending on messages change track, pause etc of banshee, or if possible, anything currently running, same as what happens when the multi media keys are pressed on my keyboard.

But I have never done anything effecting other programs before, only developed programs that keep themselves, so could anyone point me in the right direction or even any tutorials?

Many Thanks,
Matt

Hi Matt,

This may or may not interest you, but I'm the author of [Tesla]("http://tesla.seanhodges.co.uk"), a PC remote control project for Android. One of the media players that it supports is Banshee.

I understand you are really looking to do a small program as a learning exercise, but if you later decide you'd like to help contribute to Tesla and extending it's capabilities with Banshee, I'll be grateful for the help :) 

In the meantime, the project [source code]("http://github.com/seanhodges/Tesla") might give you some ideas on how to accomplish what you are trying to do. 

You can use the "dbus-send" command-line program to send D-Bus commands to Banshee, and there is a GUI tool called [D-Feet]("apt://d-feet") that allows you to browse all the available commands and try them out. As an example, the command below causes Banshee to toggle between pause/play during playback:

```
dbus-send --session --type="method_call" --dest=org.bansheeproject.Banshee /org/bansheeproject/Banshee/PlayerEngine org.bansheeproject.Banshee.PlayerEngine.TogglePlaying
```

---

