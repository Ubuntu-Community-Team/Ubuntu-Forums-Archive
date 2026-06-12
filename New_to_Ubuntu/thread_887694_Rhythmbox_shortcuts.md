---
title: "Rhythmbox shortcuts"
date: 2008-08-12
forum: New to Ubuntu
---

### Post by Tom--d on 2008-08-12
Hello,

I can't find the shortcuts to allow you to go forward and back, play/pause etc.. 
I want it in the form of a Application Launcher. 

I know the keyboard shortcuts.. just want an icon on the panel. click it, skips the track. etc. 

Thanks, 
Tom

---

### Post by Elfy on 2008-08-12
I installed music-applet which you can add to your panel

```
sudo apt-get install music-applet
```

Right click panel - add to panel - look for music-applet

Not sure of another way of doing it myself, doesn't mean there isn't though of course.

---

### Post by Tom--d on 2008-08-12
> **forestpixie said:**
> I installed music-applet which you can add to your panel

```
sudo apt-get install music-applet
```

Right click panel - add to panel - look for music-applet

Not sure of another way of doing it myself, doesn't mean there isn't though of course.

Thanks for helping but thats the last resort. 

I want something like,
```
rhythmbox --next
```
```
rhythmbox --playpause
```
etc etc.

---

### Post by Elfy on 2008-08-12
Nah - sorry, one of the reasons I don't use it - amongst others...

---

### Post by Tom--d on 2008-08-12
> **forestpixie said:**
> Nah - sorry, one of the reasons I don't use it - amongst others...

I see, 

Thank you for your help tho :)
I might email the developers..

---

### Post by Elfy on 2008-08-12
I've found a couple of scripts for raising lowering volumes - maybe you could change them to suit your needs.

[http://ubuntuforums.org/showpost.php?p=3902806&postcount=1](http://ubuntuforums.org/showpost.php?p=3902806&postcount=1)

Rhythmbox seems to be quite basic, which I assume is it's appeal to some, sorry couldn't help more.

---

### Post by Tom--d on 2008-08-12
> **forestpixie said:**
> I've found a couple of scripts for raising lowering volumes - maybe you could change them to suit your needs.

[http://ubuntuforums.org/showpost.php?p=3902806&postcount=1](http://ubuntuforums.org/showpost.php?p=3902806&postcount=1)

Rhythmbox seems to be quite basic, which I assume is it's appeal to some, sorry couldn't help more.

Thanks, but I dont know what to do xD

But thats like what I want to do just forward/back/pauseplay

I could do it with amarok tho due to it uses dbus.

---

### Post by kostkon on 2008-08-12
You can do it with *rhythmbox-client*. It allows you to control an already running instance of *Rhythmbox*, so don't forget to run it first.

So for example to go to the next track, you'll do:
*rhtyhmbox-client --next*

Give
*man rhythmbox-client*
in a terminal for more info.

---

### Post by Tom--d on 2008-08-12
> **kostkon said:**
> You can do it with *rhythmbox-client*. It allows you to control an already running instance of *Rhythmbox*, so don't forget to run it first.

So for example to go to the next track, you'll do:
*rhtyhmbox-client --next*

Give
*man rhythmbox-client*
in a terminal for more info.

Thanks thanks thanks, 
Just what I wanted :)

---

