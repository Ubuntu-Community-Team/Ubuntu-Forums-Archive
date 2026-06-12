---
title: "HOWTO: Switch workspaces by moving your mouse to the edge of the screen"
date: 2005-04-15
forum: Outdated Tutorials &amp; Tips
---

### Post by shakin on 2005-04-15
Brightside is a utility that allows you to switch to adjacent workspaces by moving your mouse cursor to the edges of the screen. Move your mouse left and you switch to the workspace to the left of your current one, move right to move to the workspace to the right, etc. You can also configure custom commands to run when you move to the corner of the screen, or set it to move to a diagonal workspace if you have a multi-row, multi-column layout.

Here's how you do it:

Install Brightside
```

$ sudo apt-get install brightside

```

Optionally configure brightside using the GUI (set custom commands for corner movement)
```

$ /usr/bin/brightside-properties

```

Run the program
```

$ /usr/bin/brightside

```

You should now be able to switch workspaces by moving your mouse to the edges of the screen.

Below are instructions to have brightside start when you login, otherwise you will need to run the /usr/bin/brightside command after each login.

- Menu: System -- Preferences -- Sessions.
- Go to the Startup Programs tab.
- Click Add.
- In the Startup Command text box type (without the quotes) '/usr/bin/brightside' and click OK.

Happy workspace switching!

---

### Post by henriquemaia on 2005-04-15
Nice tip!

Thanks a lot :)

---

### Post by Fab on 2005-04-15
my setup is to switch on left and right edges and to mute sound in the bottom right corner (i got nothing there except the pager)
i usually listen to music really loud, so when someone is coming, i point my mouse to the bottom right corner (no click :)) and the music fades out till its muted
really nice
also, i didnt need to put it into the start up programs, it did so automatically :S ?

---

### Post by Sham on 2005-04-15
Will this prog work under KDE too?

---

### Post by illmonkey on 2005-04-15
so so so nice!!!

---

### Post by totalshredder on 2005-04-15
Dang, now that is a really cool program. and it's so easy to set up!!

Good Work!

Luke

---

### Post by dataw0lf on 2005-04-15
Ugh.  xfce4 comes with that behavior by default, I couldn't stand it.  Ctrl+Alt + # or arrow works for me.

---

### Post by shakin on 2005-04-15
[QUOTE=Sham]Will this prog work under KDE too?[/QUOTE]

Sorry, I'm pretty sure it's Gnome-only.

---

### Post by Sarojin on 2005-04-16
[QUOTE=Sham]Will this prog work under KDE too?[/QUOTE]
KDE can do that without extra programs (don't remember how, the option is somewhere in kcontrol).

---

### Post by vapor on 2005-04-16
Kcontrol>Desktop>Window Behavior>Advanced tab

Sheesh... KDE has had that for years... and yes it still annoys me. :)

Come to think of it, I think fwvm had it, too.

---

### Post by Gandalf on 2005-05-02
cool tip thanks...

---

### Post by TravisNewman on 2005-05-02
rock on-- been wondering how to do this.

---

### Post by Gandalf on 2005-05-02
i'l like to do a script to run/stop it just by a shortcut like Alt+F3 for example because it's really ugly when you watch a movie, you hit the mouse by accident and Boom! you're on the next workspace...
so is it possible?

---

### Post by Eproxus on 2005-05-02
The thing I liked in XFCE4 is when you dragged a window to the edge and it would move to the next workspace, however it is quite confusing when just moving your mouse and the workspace switches. I also don't like the pager popping up in my face. I'll try it for a while though.

---

### Post by huh? on 2005-05-02
funny, just moving my mouse to the workspace icon, and using the scroll feature, quickly changes the workspace...that and CTL/ALT + an arrow, works just fine for me..

---

### Post by Happy on 2005-05-02
the mute volume button didna'e work for me  :| 
other then that this is a great plugin.
for the movie question, couldn't you just make it display on every screen so it don't matter if you knock the mouse to the next window?

---

### Post by Steel3 on 2005-05-02
Pretty cool, especially when combined with use of 3ddesktop

---

### Post by jkish on 2005-05-07
I agree. 3ddesk with brightside is very cool.  I setup brightside so  when I move my mouse to the corner 3ddesk kicks in.  All you have to do is click to switch windows.

Here's a screenshot.

---

### Post by bored2k on 2005-05-07
Just tried this for 15 secs. COuldn't stand it.
I'm 3ddesktop a try though..

---

### Post by funkenstein on 2005-06-04
sorry, I'm an idiot. No, just a n00b....

to remove brightside:
uninstall it using:
```

sudo apt-get remove brightside

```
outputting:
```

Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  brightside
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
Need to get 0B of archives.
After unpacking 946kB disk space will be freed.
Do you want to continue [Y/n]? y {<- Need to tell it yes}
(Reading database ... 64725 files and directories currently installed.)
Removing brightside ...

```

So there, me doing something right, imagine that!  \\:D/

---

### Post by Erucolindo on 2005-07-18
I also use brightside to switch desktops with 3ddesktop.. right now i have it set up to switch to my right desktop in the upper right corner (by running '3ddesk --nozoom --gotoright') and vise versa.. however every third or fourth time i switch desktop it dosn't return focus to my desktop, this is very anoing.. it's probibly a bug in 3ddesktop and i can probibly not do that much about it.. but if anyone have a  sugestion....?

---

### Post by MrMunson on 2005-07-27
Oh.... So... great... app.... thank you! *bow* This is amongst the funkiest, coolest AND most useful app I have seen in ages.

THX  \\:D/

---

### Post by hunteramor on 2005-07-29
Is there any way I could use the corner settings to switch left and right workspaces?  My girlfriend, who needs to be able to use the computer too, winds up switching workspaces accidentally too often when it's set to switch at the right and left borders, even with the delay set high.  If it only switched in the corners, she might still be able to use it and I'd still have the functionality.

Anyone figured out a way to do this yet?

---

### Post by deNoobius on 2005-11-24
Nice, this is a terrific tool.  I was wondering how to switch workspaces in Blender (it covers up the bottom taskbar).

---

### Post by Crashmaxx on 2006-05-16
[QUOTE=Erucolindo]I also use brightside to switch desktops with 3ddesktop.. right now i have it set up to switch to my right desktop in the upper right corner (by running '3ddesk --nozoom --gotoright') and vise versa.. however every third or fourth time i switch desktop it dosn't return focus to my desktop, this is very anoing.. it's probibly a bug in 3ddesktop and i can probibly not do that much about it.. but if anyone have a  sugestion....?[/QUOTE]
Oh wow! That's even better then either alone.

I don't have your problem though.:-k

---

### Post by trazek on 2010-06-28
Hello all.

I am new to Ubuntu and recently installed 10.04 LTS. I installed Brightside to move around my workspaces a little easier and for some reason, I cannot switch between workspaces with my mouse. All the custom corner functions work but not the workspace switching.

Any ideas?

Update: Nevermind, more Googling lead me to the answer. It seems I had to turn off all visual effects for Brightside to work properly.

---

### Post by pt123 on 2010-06-28
you can have visual effects, and use Compiz to attain the same functionality as Brightside

just install compiz settings manager

---

### Post by Pougnet on 2010-06-28
Thanks for this.

---

