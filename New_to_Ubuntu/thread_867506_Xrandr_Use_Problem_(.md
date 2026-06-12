---
title: "Xrandr Use Problem :("
date: 2008-07-22
forum: New to Ubuntu
---

### Post by hungryOrb on 2008-07-22
Hi!
The display is not working properly on this ubuntu server. It is completely messed up, not just too big for the screen. Check the screenshot:

[[IMG]http://img34.picoodle.com/img/img34/4/7/22/f_screenscrewm_cac94d6.png[/IMG]](http://www.picoodle.com/view.php?img=/4/7/22/f_screenscrewm_cac94d6.png&srv=img34)

So on recommendation from friend, I try xrandr to right it with:
```
sudo xrandr -s 800x600
```

but I get the error message:
```
Can't open display
```

this happened before and after using:
```
sudo /etc/init.d/gdm stop
```

Does anyone have an idea? :S
Orb

---

### Post by Canuckelhead on 2008-07-22
post results from xrandr -q

---

### Post by jordanmthomas on 2008-07-22
It seems like you're running this from somewhere other than X, yes?  If so, the DISPLAY variable will not be set, and you can't launch applications on your xserver.

1.  Make sure X is running (with the buggy screen)
2.  Go to a virtual terminal (Ctrl - Alt - F2)
3.  Type:  
```
DISPLAY=:0.0 sudo xrandr --mode 800x600
```
4.  See if that fixes it by going back with Ctrl - Alt - F7

---

### Post by hungryOrb on 2008-07-22
> **Canuckelhead said:**
> post results from xrandr -q

I get the same error message: 
```
Can't open display
```

However, if I stop KDM:
```
sudo /etc/init.d/kdm stop
``` then ubuntu sort of shuts down, and I get a black blank screen with a flashing cursor but no response from commands..

---

### Post by hungryOrb on 2008-07-22
> **jordanmthomas said:**
> It seems like you're running this from somewhere other than X, yes?  If so, the DISPLAY variable will not be set, and you can't launch applications on your xserver.

1.  Make sure X is running (with the buggy screen)
2.  Go to a virtual terminal (Ctrl - Alt - F2)
3.  Type:  
```
DISPLAY=:0.0 sudo xrandr --mode 800x600
```
4.  See if that fixes it by going back with Ctrl - Alt - F7

Thanks, although doesn't seem to fix. Just gives a syntax list:
[[IMG]http://img27.picoodle.com/img/img27/4/7/22/t_sntaxlistm_c2cd0cf.png[/IMG]](http://www.picoodle.com/view.php?img=/4/7/22/f_sntaxlistm_c2cd0cf.png&srv=img27)

Not sure what this means :O

---

### Post by jordanmthomas on 2008-07-23
oops, forgot to say that you need to specify an output
```
sudo DISPLAY=:0.0 xrandr --screen 0 -s 800x600
```

Try this instead.  Usually when I use xrandr, I have two monitors and it seems a little different than I expected with just one.

---

### Post by hungryOrb on 2008-07-23
> **jordanmthomas said:**
> oops, forgot to say that you need to specify an output
```
sudo DISPLAY=:0.0 xrandr --screen 0 -s 800x600
```

Try this instead.  Usually when I use xrandr, I have two monitors and it seems a little different than I expected with just one.

Thanks again, although this gave the same result :D !
Arg!

---

### Post by jordanmthomas on 2008-07-23
Grr, well, let's see if we can get SOME info here.
```
DISPLAY=:0.0 sudo xrandr -q
```
If this fails I am going to throw xrandr into the bitbucket.  :)

Also, try stopping kdm then logging in as your user and running
```
startx `which xterm`
```

See if this starts X up with a terminal.  If it does, then this is an issue with kdm.

---

### Post by hungryOrb on 2008-07-23
> **jordanmthomas said:**
> Grr, well, let's see if we can get SOME info here.
```
DISPLAY=:0.0 sudo xrandr -q
```
If this fails I am going to throw xrandr into the bitbucket.  :)

Also, try stopping kdm then logging in as your user and running
```
startx `which xterm`
```

See if this starts X up with a terminal.  If it does, then this is an issue with kdm.

Thanks, err.. hehe.. noob q: I stopped KDM, but then all I have is a blank black screen with flashing cursor. i can type things but commands dont seem to have effect. If I press ctrl+alt+del then ubuntu restarts. Is that what I should do? Or I should login differently?

the first line you suggested did not work, same as before.

---

### Post by jordanmthomas on 2008-07-23
When you get the flashing cursor, press ctrl-alt-F2
Then, you can type commands.

I'm still interested to see if that startx command works out for you.  Note that the ` in it is the key next to the one, not the key next to :

...and just as proof that I'm not crazy, xrandr works for me on the terminals.

---

### Post by hungryOrb on 2008-07-23
> **jordanmthomas said:**
> When you get the flashing cursor, press ctrl-alt-F2
Then, you can type commands.

I'm still interested to see if that startx command works out for you.  Note that the ` in it is the key next to the one, not the key next to :

...and just as proof that I'm not crazy, xrandr works for me on the terminals.

aha! Thanks :] LOL, love the concept of sanity proof <3
The first one now gives error:
```
Can't open display0.0
```

the second, starts the display, a little differently than usual.. instead of it being blue, I can see just tones of grey and black and white!
I get screenshot in moment.

---

### Post by hungryOrb on 2008-07-23
[[IMG]http://img27.picoodle.com/img/img27/4/7/22/f_111m_f3fb49f.jpg[/IMG]](http://www.picoodle.com/view.php?img=/4/7/22/f_111m_f3fb49f.jpg&srv=img27)

---

### Post by jordanmthomas on 2008-07-23
OK, it seems to be a problem in general with X.
Since you say it's a server, I assume you won't need hardware acceleration, so this may be an acceptable fix.

On the terminal (ctrl - alt - f2), type this
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

Now, from here, you have two options:
1.  ```
sudo rm /etc/X11/xorg.conf
```
Now, when you run kdm or startx, X will attempt to configure itself.  This may or may not work well for you.  For me, it configures itself well enough for compiz to run.

**OR**

2.  You could instead try the "vesa" driver
```
sudo dpkg-reconfigure xserver-xorg
```
Mostly, default answers will be OK, but try the vesa driver when it asks you for a graphics driver.  Alternatively, you could manually edit /etc/X11/xorg.conf, find the device for your graphics, and change the driver to vesa:
```
sudo nano /etc/X11/xorg.conf
```
Ctrl - o (oh), Enter, Ctrl -X when you are done.

I don't know if you've ever said what kind of graphics card it had.  If it's anything other than integrated intel, I'm unfamiliar with any bugs (as that's what I myself have)

Sorry for the delayed response, gaming beckoned me.

---

### Post by hungryOrb on 2008-07-23
> **jordanmthomas said:**
> OK, it seems to be a problem in general with X.
Since you say it's a server, I assume you won't need hardware acceleration, so this may be an acceptable fix.

On the terminal (ctrl - alt - f2), type this
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

Now, from here, you have two options:
1.  ```
sudo rm /etc/X11/xorg.conf
```
Now, when you run kdm or startx, X will attempt to configure itself.  This may or may not work well for you.  For me, it configures itself well enough for compiz to run.

**OR**

2.  You could instead try the "vesa" driver
```
sudo dpkg-reconfigure xserver-xorg
```
Mostly, default answers will be OK, but try the vesa driver when it asks you for a graphics driver.  Alternatively, you could manually edit /etc/X11/xorg.conf, find the device for your graphics, and change the driver to vesa:
```
sudo nano /etc/X11/xorg.conf
```
Ctrl - o (oh), Enter, Ctrl -X when you are done.

I don't know if you've ever said what kind of graphics card it had.  If it's anything other than integrated intel, I'm unfamiliar with any bugs (as that's what I myself have)

Sorry for the delayed response, gaming beckoned me.

haha ;] I'm just glad you are willing to help :D Thanks!
Although.. I tried second option, and I didn't get the chance to choose a driver. I'll let you know how the first option goes ;p

---

### Post by hungryOrb on 2008-07-23
After deleting, I just get black screen, and the monitor goes on standby. :( I remember this is what happened at first, took a while to get a screen, but it did eventually get that screwed up screen. 
But you know, it is capable of at least a low res.. Because standard install with gnome gui of debian will run desktop fine..

---

### Post by jordanmthomas on 2008-07-23
Hmm, if it still doesn't work after setting the driver to vesa, I don't know what to tell you.

Anyone else?

---

### Post by hungryOrb on 2008-07-23
> **jordanmthomas said:**
> Hmm, if it still doesn't work after setting the driver to vesa, I don't know what to tell you.

Anyone else?

Thanks very much for all the help man :)

---

