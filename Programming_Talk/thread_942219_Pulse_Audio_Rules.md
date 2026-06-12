---
title: "Pulse Audio Rules"
date: 2008-10-09
forum: Programming Talk
---

### Post by KillerKiwi on 2008-10-09
**Version 0.4**

What works now :
 - All volume adjustments are fades
 - Fade out music/video players on skype call
 - Fade to music player with focus when more than one
 - Fade out music player when video playing
 - Push sound to USB headsets on plugin
 - Categories to assign to clients
 - Sniffs desktop files to guess application category ... music/video/VoIP
 - Simplified pref UI for creating rules
 - Volume sniffing to fix youtube video issue

Goals to aim for :
 - Mute all clients on suspend / hibernate

have a look at [https://launchpad.net/eyecandy/0.4](https://launchpad.net/eyecandy/0.4) if your interested....

---

### Post by mssever on 2008-10-09
> **KillerKiwi said:**
> I've been messing with some code to control pulseaudio volum levels based on some rules

Really simple stuff like mute the music player when skype is making noise... that sort of thing

have a look at [http://bazaar.launchpad.net/~killerkiwi2005/eyecandy/trunk/files]("http://bazaar.launchpad.net/%7Ekillerkiwi2005/eyecandy/trunk/files") if your interested....

Theres basic rules for skype and totem at the moment and the UI dosnt update but it works alright...

Its in python which probably isnt ideal but my C skills arnt up to it
I tried to run it, but I got the following exception when running eye_candy.py: ```
Traceback (most recent call last):
  File "eye_candy.py", line 10, in <module>
    import Xlib.display
ImportError: No module named Xlib.display
```Perhaps you forgot to mention a dependency? Also, is the program called ear candy or eye candy? You're using both names, which is confusing. I'm assuming that ear candy is what you're after.

I've made a few changes, which are at lp:~scott.severance/eyecandy/main, and which are ready for merging into trunk. See the commit log for details.

Oh, and by the way, I think Python is quite a reasonable language choice for this project.

---

### Post by KillerKiwi on 2008-10-09
I'll plead "stupidity" for the name I started with eye but changed to ear and lp dosnt change the url's ;)


The dep is python-xlib, I just merged your changes

---

### Post by mssever on 2008-10-09
I just made a few more changes. There are two bugs I've noticed that I haven't tracked down so far:

[LIST=1]
[*]According to Glade, there are two tabs in the inteface. However, I only see the Applications tab. I get the following warning: ```
/home/scott/programming/projects/earcandy/main/glade_window.py:18: GtkWarning: gtk_notebook_set_tab_label: assertion `GTK_IS_WIDGET (child)' failed
  self.wtree = gtk.glade.XML(glade_file)
```
[*]When earcandy fades banshee's volume due to totem, it's done much too slowly. It takes about 5 seconds to get to 25%, then it starts lowering the volume a step at a time. When the volume reaches 20%, it next sets it to 29% and then resumes lowering it a step at a time. This means that the rule "Mute all others on focus" doesn't actually happen as described.
[/LIST]

---

### Post by KillerKiwi on 2008-10-09
> **mssever said:**
> I just made a few more changes. There are two bugs I've noticed that I haven't tracked down so far:

[LIST=1]
[*]According to Glade, there are two tabs in the inteface. However, I only see the Applications tab. I get the following warning: ```
/home/scott/programming/projects/earcandy/main/glade_window.py:18: GtkWarning: gtk_notebook_set_tab_label: assertion `GTK_IS_WIDGET (child)' failed
  self.wtree = gtk.glade.XML(glade_file)
```
 - I was planing on adding a general properties tab with a couple of options
> **mssever said:**
> 
[*]When earcandy fades banshee's volume due to totem, it's done much too slowly. It takes about 5 seconds to get to 25%, then it starts lowering the volume a step at a time. When the volume reaches 20%, it next sets it to 29% and then resumes lowering it a step at a time. This means that the rule "Mute all others on focus" doesn't actually happen as described.
[/LIST]
- Thats a logic fault in the fading at the moment it just detects if the volume level is greater or less than the target volume..

---

### Post by KillerKiwi on 2009-01-29
updated to version 0.2

---

### Post by GSMX on 2009-02-26
great program, i've set the 0.3 release to start at boot, i hope it will be included in the repo's soon

one thing: i like to keep my systray as clean as possible, these sort of programs don't belong there. thanks for the no-tray option ;) no way to edit preferences now though.

keep up the good work! :p

---

### Post by KillerKiwi on 2009-03-02
0.3 should have a "show icon" checkbox on the advanced tab,

Wait I see what you mean.. now you can get to the UI :)

Ill have to think about that should be away to get around it

---

### Post by KillerKiwi on 2009-03-02
Ask and you shall receive :)

The 0.4 branch registers its self with dbus

Starting the a executable second time will now show you the pref window and not start a second instance of ear candy

[https://code.launchpad.net/~killerkiwi2005/earcandy/0.4](https://code.launchpad.net/~killerkiwi2005/earcandy/0.4)

---

### Post by KillerKiwi on 2009-05-19
0.4 is now available

- Push's sound to USB headsets on plug-in
- Detects active streams using a volume meter (fixs video in firefox flash)
- Ability to lock sound to current rules
- Fixed a lot of crash bugs

[https://code.launchpad.net/~killerkiwi2005/earcandy/0.4](https://code.launchpad.net/~killerkiwi2005/earcandy/0.4)

bzr branch lp:earcandy/0.4

---

### Post by psychobillyjekyll on 2009-05-26
I'm noticing a bug where nothing else on my machine other than skype and amarok will get sound output. Programs like firefox, running a youtube clip, zsnes, xmoto, and others don't have any output sound anymore. This just occured when I put in Ear Candy 0.4. Is there a bug in the program, or is it just something on my machine? Thanks in advance.

---

### Post by KillerKiwi on 2009-05-26
Its probably that the volume for those applications had been set to zero...

You can use pulse volume control to raise the levels... 

This seems to be very a common problem people have.. even when not using Ear Candy... Im adding a new option to reset all application volume levels in 0.5

---

### Post by psychobillyjekyll on 2009-05-26
I checked my normal volume control stuff. All the volume controls are up, including the Pulse Audio ones. Am I just not looking in the right place? Sorry for all the questions, I literally installed the program two days ago.

---

### Post by KillerKiwi on 2009-05-26
if all else fails delete the files in your
$home/.pulse

That will reset all the pulse settings

---

### Post by psychobillyjekyll on 2009-05-26
Your previous search inspired me to do some searching. In this search I found a file named 1d1d855d2f9932e8710541bc49d3f0d9:device-volumes.i486-pc-linux-gnu.gdbm, in my home/user/.pulse folder. In this are where I could edit the volumes for my output programs. Trouble is, I have absolutely no idea how to open, let alone edit, that file. If you have any suggestions, feel free to fire them at me.

---

### Post by Reiger on 2009-05-26
You could delete it and then reboot. That should at least reset sound levels to default (which is usually way too loud but there you go); and give you a working configuration again.

A suboptimal solution, yes.

---

### Post by psychobillyjekyll on 2009-05-26
I beg to differ with the 'suboptimal' name, I tried it, and it fixed my problem. I can always turn the volume down, but when it's at zero, with no easy way to raise it, thats when things get difficult. Thanks for all the help.

---

