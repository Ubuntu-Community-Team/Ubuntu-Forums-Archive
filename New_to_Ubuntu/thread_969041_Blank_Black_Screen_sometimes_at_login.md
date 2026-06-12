---
title: "Blank Black Screen sometimes at login"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by cool_penguin on 2008-11-03
Hi Everyone,

I recently upgraded to Ubuntu 8.10. While at the first impression everything looked good, I was very disappointed to see a Blank Black Screen at GDM login after the first re-start (following fresh installation using Live USB). When I am greeted by a Blank Black Screen, I hit Ctrl+Alt+F6 and then I am taken to a text based command line login console. Then at this point if I type nothing and instead hit Ctrl+Alt+F7, then I am taken to the graphical GDM login screen. The same problem occurs also when I log out and try to log in. I am forced to follow the same sequence of hitting Ctrl+Alt+F6 first and then hitting Ctrl+Alt+F7 to see the graphical login screen.

I was looking up various blogs and forums, where one guy advised adding the line Driver "vesa" to the xorg.conf under the section "device". When I do that I can see the graphical GMD at start up and also when I log out and try to log in. But then the problem is that the max screen resolution that I get is only 800x600 while my notebook supports a max of 1024x768. 

BTW, when I follow the sequence of hitting Ctrl+Alt+F6 first and then hitting Ctrl+Alt+F7 to see the graphical login screen, the screen resolution even at login is 1024x768. But only after adding vesa to xorg.conf, the login screen and the normal desktop screen all scale down to 800x600 :(

Could anybody please help me with this? I am using an Acer Travelmate 2310 notebook which has an integrated SiS Graphics card. Not the best, I know, but its a 4 year old notebook and all version of Ubuntu until Hardy worked perfectly like a charm. 

Thanks a lot in advance.

Cheers,
Harry

---

### Post by cool_penguin on 2008-11-04
Surprising. Nobody out there to help me. I was told that the forum is a great resource place. But looks like nobody wants to help.

---

### Post by Idaho Dan on 2008-11-04
I know what you mean cool_penguin, I had the same thing happen after I tried to upgrade from Hardy. I gave up my feeble attempts to correct it and downloaded the disc, burned it and installed that way.
It worked.
Sorry I'm not any help.

---

### Post by Peter09 on 2008-11-04
Go into recovery mode - hit ESC at GRub and select it.

Then try the reconfigure X option - good to start.

If this doesnot work, go to recovery mode and select the command shell and type startx.

Come back and tell us what happens.

---

### Post by soulspit on 2010-12-20
Hello folks.

I had this identical problem, on the same kind of laptop, an Acer Travelmate 2310.  I came across this thread and various others but was unable to find a solution, but I came up with my own hack/kludge that does the job and I thought I'd share it in case it helps anyone else!

(Normally, I wouldn't care about this minor annoyance, except that this is my grandmother's computer, and I'm trying to make things as simple as possible for her... someone on another site also mentioned that "it doesn't look good for Linux" when you start your laptop in front of someone and have to go "oh, damn, hold on...")

Anyway, here's what I did (I'm almost embarrassed at how kludgey this is).

Step 1: install xdotool (a program that allows you to simulate key presses).  In a terminal:
```
sudo aptitude install xdotool
```Step 2: make a script that does the kludge.  Make a text file containing:
```
#! /bin/bash
xdotool key ctrl+alt+F8
sleep 2
xdotool key ctrl+alt+F7
```Let's save it as... blank-fix.sh

Step 3: Put it where your autostart is.  For Kubuntu/KDE, this is  "/home/yourname/.kde/Autostart".  If it's executeable and it's here,  it'll get run on start-up.  I'm sure you can figure out where it is for  other desktop environments.

Step 4:  make it executeable.  In a terminal in the same folder as the file, type:
```
sudo chmod +x blank-fix.sh
```Step 5: carry on with your life.

You can change, obviously how many seconds the script sleeps in between the two commands, and I suppose there are some situations (say, if your computer isn't very responsive at start-up) where you might want it to sleep a bit before the first command.  Terminal 8 is the second GUI terminal which should just have a blank screen and blinking cursor - looks more like a proper startup than flashing the login text that you'd see at the text terminals 1-6.  That's it I guess!  Wasn't that silly.

---

