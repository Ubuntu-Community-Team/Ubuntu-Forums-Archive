---
title: "Would this be easy/hard to do?"
date: 2010-07-18
forum: Programming Talk
---

### Post by fallenshadow on 2010-07-18
Well this all came about when my brother wanted a program which would record and playback mouse actions. (like a macro program)

I then set about searching up for one. The two I came across constantly was Xmacro and Gnee.

Xmacro is a command-line program... so its not an option. (he needs to be able to use it)

Gnee seemed too complicated/confusing and failed miserably. 


So my question is: how hard would it be to develop this kind of app?

---

### Post by BenAshton24 on 2010-07-18
It depends on how much programming experience you have. The concept is pretty simple, I'd suggest using python and PyGTK (for the GUI). You can use Xlib for the mouse coordinates.

---

### Post by fallenshadow on 2010-07-18
Well ive no Python experience so I couldn't do that. Im already pretty good with glade and C++ so I can do the GUI with those.

Im asking more about the backend... I don't have much experience with proper mathematical programming. So would programming with X and all that be hard?

Could I use C++ or would I have to use a different language?

---

### Post by wmcbrine on 2010-07-18
> **fallenshadow said:**
> So my question is: how hard would it be to develop this kind of app?Pretty hard. Easier would be a GUI frontend for Xmacro.

---

### Post by BenAshton24 on 2010-07-18
> **wmcbrine said:**
> Pretty hard. Easier would be a GUI frontend for Xmacro.

I dunno... It shouldn't be that hard. Receive global mouse events and log the amount of time between each one. Store data for retrieval and replaying.

---

### Post by fallenshadow on 2010-07-18
> Pretty hard. Easier would be a GUI frontend for Xmacro.

Yes I was thinking of this idea myself. I decided to test Xmacro for myself and it actually does work properly.

One question: where does xmacro store its recorded data? (is it temporary or permanent data?)

---

### Post by ju2wheels on 2010-07-18
Something like this: [http://groups.csail.mit.edu/uid/sikuli/](http://groups.csail.mit.edu/uid/sikuli/) ?

---

### Post by fallenshadow on 2010-07-19
Hey I did it guys! :D

However it kinda sux! :lolflag:

The main problem is it doesn't take into account the speed that you do things at. I can do something slowly and it still does it too fast!

This is most likely a problem with Xmacro not doing things in realtime.

---

### Post by StunnerAlpha on 2010-07-19
You need to store the time between actions and then when replaying hold the mouse position/make the mouse take x time to move from one point to another. Glad to hear you got something working. :)

---

### Post by pbrane on 2010-07-19
> **fallenshadow said:**
> ...
This is most likely a problem with Xmacro not doing things in realtime. ...

Remember, the idea behind most macros is to *speed* things up!

---

### Post by fallenshadow on 2010-07-19
> Remember, the idea behind most macros is to speed things up!

Yes I understand but sometimes speed sacrifices accuracy. For example I can record me opening a browser and typing an address in. 

However when I replay with Xmacro it starts typing the text as the web-browser is opening. This extra speed is not so useful.

---

### Post by fallenshadow on 2010-07-19
> You need to store the time between actions and then when replaying hold the mouse position/make the mouse take x time to move from one point to another. 

Interesting idea but probably too complicated.

Here are some pics, its pretty simple but it works.

[IMG]http://i31.tinypic.com/2w750gi.png[/IMG]

[IMG]http://i28.tinypic.com/33faiv7.png[/IMG]

---

### Post by BenAshton24 on 2010-07-23
> **fallenshadow said:**
> Interesting idea but probably too complicated.

Not really... all you have to do is write "Delay [seconds]" to every line that doesn't follow a MotionNotify event in the recorded file before you play it. Example:

```
MotionNotify 32 581
ButtonPress 1
Delay 10
ButtonPress 2
Delay 10
```

Although that still isn't a very good solution because you need a long delay for certain things and a shorter delay for others...

I'm bored and I have lots of free time so I'm going to try and write something from scratch that records all events and the time between each one. I'll post it here if you are still interested.

Ben.

---

### Post by fallenshadow on 2010-07-24
> I'm bored and I have lots of free time so I'm going to try and write something from scratch that records all events and the time between each one. I'll post it here if you are still interested.

Yes I would be quite interested! :) My Xmacro program is actually pretty ok. However one annoying thing I found out is that the Xmacro library does not seem to have a way to stop playback.

This is very annoying if the macro you recorded is too long as you have to wait until it finishes. :(

Thanks for the info on Delay... I will use it for now!

---

### Post by BenAshton24 on 2010-07-25
> **fallenshadow said:**
> Yes I would be quite interested! :) My Xmacro program is actually pretty ok. However one annoying thing I found out is that the Xmacro library does not seem to have a way to stop playback.

This is very annoying if the macro you recorded is too long as you have to wait until it finishes. :(

Thanks for the info on Delay... I will use it for now!

I did a bit of work on the program yesterday and I've got the basics sorted. Today I'm going to neaten up the code a bit and add a few more features. Current/Planned features include:
[LIST]
[*]Play/Record mouse &| keyboard events
[*]Customizable delay before playing & recording
[*]Database for storing macros
[*]Minimize to tray whilst recording &| playing
[*]Customizable key binding to stop recording/playing
[*]Record events for a specific program so that when replayed, the position of the target program's window does not affect the coordinates.
[*]Ability to run the program from the command line to execute a macro without showing the GUI (eg. tracker -s -m "Name of Macro")
[*]Lots of other stuff that I will think of and add today
[/LIST]

---

### Post by fallenshadow on 2010-07-26
Sounds like you have set out a pretty amazing feature list! Good luck with it!

Actually a keyboard shortcut to stop it is something im gonna work on for mine. I really need something to stop the playback.

Anyone know how to set a keyboard shortcut in GTKmm? :)

---

### Post by BenAshton24 on 2010-07-26
> **fallenshadow said:**
> Sounds like you have set out a pretty amazing feature list! Good luck with it!

Actually a keyboard shortcut to stop it is something im gonna work on for mine. I really need something to stop the playback.

Anyone know how to set a keyboard shortcut in GTKmm? :)

It would have to be a global key binding so that you could stop it even if your application didn't have focus. You could use libgtkhotkey:
[http://www.grillbar.org/wordpress/?p=250](http://www.grillbar.org/wordpress/?p=250)

I'll post an update on my program soon... it's nearing completion :)

---

