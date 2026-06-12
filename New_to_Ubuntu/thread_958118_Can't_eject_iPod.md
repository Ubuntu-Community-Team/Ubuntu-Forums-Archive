---
title: "Can't eject iPod"
date: 2008-10-25
forum: New to Ubuntu
---

### Post by adobrakic on 2008-10-25
It worked before, idk whats wrong with it.
When I right click on the icon and press eject, it says another application is using it -- but its not.

and from terminal:

```
ado@ado-desktop ~ $ eject /media/ADMINISTRAT
/sbin/umount.hal: Unmounting /media/ADMINISTRAT failed: org.freedesktop.Hal.Device.Volume.Busy: umount: /media/ADMINISTRAT: device is busy
eject: unmount of `/media/ADMINISTRAT' failed
ado@ado-desktop ~ $ 

```

---

### Post by coldcoffee on 2008-10-25
I don't know if this is the best advice, but I suppose you could always end the process through system monitor or use xkill.

Type xkill in terminal then whatever you click on with the cursor will be killed.

---

### Post by acidsolution on 2008-10-25
why dont u unmount it 

```

sudo umount -f /media/ADMINISTRAT

```

---

### Post by adobrakic on 2008-10-27
^ no worky :/

```
ado@ado-desktop ~ $ sudo umount -f /media/ADMINISTRAT
[sudo] password for ado: 
umount2: Device or resource busy
umount: /media/ADMINISTRAT: device is busy
umount2: Device or resource busy
umount: /media/ADMINISTRAT: device is busy
ado@ado-desktop ~ $ 

```

I really don't get why it's doing this, my iPod is literally doing NOTHING. :x

---

### Post by adobrakic on 2008-10-28
bump

---

### Post by SuperSonic4 on 2008-10-28
Does this happen after syncing with anything? When mine is like this I used amarok to 'remove' it

---

### Post by OutOfReach on 2008-10-28
Is another application using the device?
That's probably why it's saying the device is busy.

---

### Post by adobrakic on 2008-10-28
I try that also, but it says like 'post-disconnect command failed' or something.
:/

> 
Is another application using the device?
That's probably why it's saying the device is busy.

i don't think there is at least
i didnt open anything

---

### Post by anti-node on 2008-10-28
can't you just try shutting of the ipod? that is what i have had to do for my friends, but then again that was Windows

---

### Post by mc4man on 2008-10-28
In ubuntu (vs kubuntu) the post-disconnect command will fail meaning the ipod was disconnected but not ejected. Then the right click eject normally works (returns ipod to it's main menu vs. the red circle - do not disconnect.

What is the default setting for 'music player' (nautilus -> edit -> preferences -> media -> Music Player?

---

### Post by macogw on 2008-10-29
You have an application using the device right now.  Exit that application (your music player, maybe?  Or maybe you have a Terminal window or file browser window open looking at the inside of it?), and it should work.

---

### Post by adobrakic on 2008-10-30
I have nothing open.

[http://i33.tinypic.com/2ytpa4z.png](http://i33.tinypic.com/2ytpa4z.png)

i've tried right clicking on 'administrat' (my ipod) and opening in terminal, to eject like that. but when i put the eject command in and press enter, my CD Drive opens. 
0_0

---

### Post by adobrakic on 2008-10-31
bump

---

### Post by adobrakic on 2008-11-01
bump

---

### Post by fornix on 2008-11-01
I remember I had a problem with my Ipod once and it was just because amarok was open. It was not doing anything.
I closed amarok and did a 

```
$ sudo umount /dev/sda1 && sudo eject /dev/sda1
```

where sda1 was my ipod device.

---

### Post by adobrakic on 2008-11-02
```

ado@ado-desktop ~ $ sudo umount /media/ADMINISTRAT && sudo eject /media/ADMINISTRAT
[sudo] password for ado: 
umount: /media/ADMINISTRAT: device is busy
umount: /media/ADMINISTRAT: device is busy
ado@ado-desktop ~ $ 

```

><

ill just keep unplugging it :P
thanks anyway

---

### Post by mc4man on 2008-11-02
Still wondering  about what happens when you connect the ipod, what's the default action?

For curiosity sake plug the ipod in while holding down the shift button. In the popup that will appear click the eject button and see if it's properly ejected. (returns ipod to main menu window

---

### Post by adobrakic on 2008-11-02
When I plug the iPod in, the 'administrat' icon just appears on my desktop and thats it

and holding down the shift button and pressing eject got it to eject

---

### Post by mc4man on 2008-11-02
> holding down the shift button and pressing eject got it to eject 
That's a good thing, indicates that the mount is okay and something is using the ipod after it'd mounted.

Why don't you set an app to auto run upon ipod insertion. By default your choices would be ' open rhythmbox music player', 'do nothing' and 'ask what to do'. Try setting the default to rhythmbox. (either again hold down the shift and pick rhythmbox or go home folder -> edit -> preferences -> media -> music player and set there.

After rythmbox opens try the eject button in rythmbox's main panel.

If you want to set amarok to auto open and connect upon plugging in the ipod let me know.

---

### Post by adobrakic on 2008-11-02
yeah, i want to make it use amarok, because that's what i use now anyway

---

### Post by mc4man on 2008-11-02
> yeah, i want to make it use amarok

Okay but first did you set the default to rhythmbox and if so can you eject the ipod ok?

I'll post the way to set amarok in a bit, I'll think we'll use the easy way so in the meantime install banshee and ck. in preferences -> media that it's a choice for default music player. (will make sense in a bit

Get back to me on the above question.

---

### Post by J03y on 2008-11-02
You can always try to turn off the computer and then disconnect the ipod. No harm in that, at least I think.

---

### Post by adobrakic on 2008-11-02
Yeah, it ejects fine using banshee

---

### Post by mc4man on 2008-11-02
Good
I worked out a way to get amarok to open and auto connect properly a ways back but due to lack of interest never updated the post for a slightly better though more involved method.
I think maybe we should use that so give me about 20 min. and I'll post a complete step by here.

I need you to make sure that amarok's post disconnect command doesn't unmount the ipod. In ubuntu that command will always fail which doesn't matter, we just don't want it to semi succeed.

So open amarok -> settings -> configure amarok - click on media devices and look for the small box with gears in it(next to remove, see screen
Click on the gears and change command to something that absolutely won't work like in screen 2. Then apply and ck. back here in about 20 min.

If your curious about 'easy' method see here, we'll be using the same idea but not using banshee (we'll use a copy .desktop method, much cleaner

We will be using the script so if you want to go ahead and make it, if so use test1 as name for the script so you can copy and paste (if you wish to name otherwise just make sure to make proper adjustments in what I'll post 

[http://ubuntuforums.org/showthread.php?p=5562637#post5562637](http://ubuntuforums.org/showthread.php?p=5562637#post5562637)

edit : look in post 3 in above link for what i mean by auto connect properly

---

### Post by mc4man on 2008-11-02
In the terminal run (copy and paste so no mistakes
```
cp /usr/share/applications/kde/amarok.desktop ~/.local/share/applications/amarok-ipod.desktop
```

Then run 
```
gedit ~/.local/share/applications/amarok-ipod.desktop
```

Scroll down till you find the line Exec=amarok %U (about 2/3 of way down.
Change to (no space between = and ./test1
```
Exec=./test1
```

On the 4th line from top, Name=AMAROK change it to something else to differentiate from Amarok (I used Amapod, Amarok1 would suffice. **Save changes**.

Then run 
```
gedit ~/.local/share/applications/mimeapps.list
```

Look for this line 'x-content/audio-player=' and add this to end

```
amarok-ipod.desktop;
```
Make sure to have no spaces between entries and end with the ;

Example from a new install so list is small

> [Added Associations]
audio/mp4=kde-amarok.desktop;
audio/ac3=kde-amarok.desktop;vlc.desktop;
x-content/video-dvd=totem-xine.desktop;vlc.desktop;
[COLOR="Red"]x-content/audio-player=banshee.desktop;rhythmbox.desktop;amarok-ipod.desktop;[/COLOR]

Save the changes and go to **home folder** and right click create a text file.
Name it test1

Copy and paste this into test1 and save

```
#!/bin/bash
amarok -m %d -m
```

then in the terminal go this

```
chmod +x test1
```

Now go back into edit -> preferences -> media and pick amapod or whatever as default choice for music player, plugin your ipod and see.

Note the caveats posted on other thread about if amarok is already running when you plug in ipod

To eject first disconnect in amarok (or just quit /close amarok)  and then r. click eject on ipod icon or go to places -> computer r. click eject.

Hopefully the  r. click eject on the icon now works for you, if not post back

also note that amarok may report 'some media couldn't be loaded' which is okay (refers to the ipod control files which you don't want loaded

---

### Post by adobrakic on 2008-11-02
ah, that worked perfectly
thank you SO much :D

---

### Post by mc4man on 2008-11-03
Glad your back in business
If your using amarok you may also be interested in making it the default audio cd player.
Again for various reason a custom launch command works better from a script then directly from the .desktop

see here
[http://ubuntuforums.org/showthread.php?p=5459412#post5459412](http://ubuntuforums.org/showthread.php?p=5459412#post5459412)

got some other amarok stuff, let me know

edit; if you decide to do you already have the directory (applications), and the file (mimepps.list)
The only thing maybe missing is the proper line to add to. (x-content/audio-cdda=
 Either paste in as shown or go into ...preferences -> media and change the existing default for cd audio to something else. If banshee is there choose that and the line will be there for you. If not choose 'do nothing', then close preferences, reopen and switch back to rhythmbox which will also create the proper line.

---

