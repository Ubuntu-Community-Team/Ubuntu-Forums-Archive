---
title: "Need help with preferred Apps"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by Samurai Penguin on 2008-06-08
I just installed MPlayer Movie Player and it works well. So I want to make
it the default DVD player. I opened Preferred Applications and it shows two
players under the Multimedia tab: Rhythmbox Music Player and Totem Movie
Player.
There's one more choice called CUSTOM and has a place to type a command
but I have no idea how it would be used. Any help is appreciated. Thanks

---

### Post by Bigtime_Scrub on 2008-06-08
Ok, I think this will work but Im not on a machine running Linux right now so I cant test it myself. 

open terminal

```
gksudo gedit /etc/gnome/defaults.list
```

ctrl-f and search option x-content/video

you should see some enteries that say totem.desktop or vlc.desktop. It will be whatever the currect default player is. Change all of them to MPlayer Movie Player.desktop

---

### Post by mikewhatever on 2008-06-08
The executable should be in /usr/bin. Verify that with <which mplayer> command. You may need to run <sudo updatedb> first.

---

### Post by Samurai Penguin on 2008-06-08
tried all the above, didn't work. Totem still opened when
I load a DVD movie

---

### Post by mgmiller on 2008-06-08
Open your home folder  Places > Home Folder

On the top click on Edit > Preferences and go to the Media tab.  Select what you want from there.  You could try "Do Nothing" and then just start vlc or mplayer and have them play the disc.  

In hardy, I had to change the path for the optical drives for both vlc and mplayer to find the DVD because optical drives are not really handled by /etc/fstab anymore.

In mplayer, right click the player to get the context menus and go to Preferences > Mis.

Near the bottom is the path to the DVD drive.  Mine used to say "/dev/hda".  I had to change it to "/dev/scd0"  (without the quotes).

Now, after running mplayer, just right click and select DVD > Open Disc    and it should play.


For vlc, Click the Open button to the left of the Play button and select the Disc tab.  In the Device name entry, change it to /dev/scd0 or whatever you need.

I have found that the settings change is persistent in mplayer, but not in vlc.  You have to change it every time.

I realize this isn't an ideal solution.  I liked the way it worked in Gutsy and earlier better, where you could put in the command line for any player and it would run that one when you put in the disc.

Read this for more info:

[http://ubuntuforums.org/showthread.php?t=782759&highlight=preferred+apps+hardy]("http://ubuntuforums.org/showthread.php?t=782759&highlight=preferred+apps+hardy")

---

