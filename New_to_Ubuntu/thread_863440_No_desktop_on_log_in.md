---
title: "No desktop on log in"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by divindavid on 2008-07-18
hello, i have ubuntu 8.04 on my IBM T41. when i log in it goes to a orange screen with a mouse which i can move around, but nothing else. any ideas? i just did a update after an install. there were like 528 things to update and took like 30min. then prompted me to restart and here i am.

---

### Post by seagullplayer77 on 2008-07-18
Can you do anything with the mouse besides moving it around, like right click and get a menu?

---

### Post by divindavid on 2008-07-18
i cannot right click. but  i can hit print screen and bring up that menu

---

### Post by divindavid on 2008-07-18
i can also hit controll alt. arrow to the left and it brings up a little box saying desk 1  and desk 2

---

### Post by seagullplayer77 on 2008-07-18
Certainly is odd...Not being able to right click would imply that you don't have a desktop, but being able to a print screen would imply that you do. Maybe try going into a virtual terminal and then back to the desktop (or lack thereof, as the case may be)?

---

### Post by seagullplayer77 on 2008-07-18
The Ctrl+Alt+Left/Right also implies you have a desktop. Ubuntu is set by default to have two desktops, and that key combo is the one to switch between them, if memory serves me. Try Alt+F2, just for kicks.

---

### Post by divindavid on 2008-07-18
i can hit controll alt. F1 and do that. but when i go back to the desktop it still is not there. was there an error in the install??? if so i am fine with reinstalling but this is the second time this has happened.

---

### Post by divindavid on 2008-07-18
> **seagullplayer77 said:**
> The Ctrl+Alt+Left/Right also implies you have a desktop. Ubuntu is set by default to have two desktops, and that key combo is the one to switch between them, if memory serves me. Try Alt+F2, just for kicks.

alt. F2 does nothing i tried that

---

### Post by seagullplayer77 on 2008-07-18
It doesn't sound like a bad install, especially if you can get a virtual terminal. I take it the login screen showed up OK?

---

### Post by divindavid on 2008-07-18
> **seagullplayer77 said:**
> It doesn't sound like a bad install, especially if you can get a virtual terminal. I take it the login screen showed up OK?

up i could log in fine and everything

---

### Post by seagullplayer77 on 2008-07-18
I was looking at another post regarding a similar problem, and someone suggested trying to boot into a failsafe Gnome desktop. If you can logout (Ctrl+Alt+Backspace), I believe the choice to go failsafe is under "Options" at the GDM login screen.

---

### Post by divindavid on 2008-07-18
> **seagullplayer77 said:**
> I was looking at another post regarding a similar problem, and someone suggested trying to boot into a failsafe Gnome desktop. If you can logout (Ctrl+Alt+Backspace), I believe the choice to go failsafe is under "Options" at the GDM login screen.

i do not see a fail safe log in or anything in the option menu

---

### Post by seagullplayer77 on 2008-07-18
Hmm...I guess that's out of the question then. Here's another idea: log back into the normal Gnome desktop and get into a virtual terminal and run a ps -ef, just to see what processes are running.

---

### Post by divindavid on 2008-07-18
> **seagullplayer77 said:**
> Hmm...I guess that's out of the question then. Here's another idea: log back into the normal Gnome desktop and get into a virtual terminal and run a ps -ef, just to see what processes are running.

ah...... theres like a screen full of things

---

### Post by seagullplayer77 on 2008-07-18
lol sorry about that...try running "top" instead. That'll output the processes that are using the most CPU power instead of all the processes on the machine. It'll also put a full screen of stuff, but see if there's anything with "Gnome" or "desktop" or something like that in it.

And another idea: if you can't get a "Run Application" window when you press Alt+F2 from a regular desktop, maybe the terminal got uninstalled somehow when you updated? When you're in the virtual terminal, try running "sudo apt-get install gnome-terminal" and see what happens.

---

### Post by divindavid on 2008-07-18
the only high CPU programs are top and Xorg and Init.

---

### Post by divindavid on 2008-07-18
> **seagullplayer77 said:**
> 

 try running "sudo apt-get install gnome-terminal" and see what happens.

but i am not connected to the internet. i alaways have to connect to  wifi place to get on?
i will try that command

---

### Post by philinux on 2008-07-18
[edit] You need to be connected to the net

If you can get to a command prompt/terminal. Use this

sudo apt-get --reinstall ubuntu-desktop

then

sudo apt-get update 

Then 
sudo reboot

---

### Post by seagullplayer77 on 2008-07-18
Xorg is at the top of my list when I run top, and on looking at my list, the only "Gnome" item I have listed is a game of Gnome Chess I played a little while ago. Did you try to reinstall the gnome-terminal package?

Perhaps philinux will be a little bit more helpful than myself. God knows he's more experienced than me! Anyway, to do any kind of updating or installing, you need to get connected to the Internet. Can you plug into a wired network somehow?

---

### Post by divindavid on 2008-07-18
this is what i get after the gnome-termanal code

E: dpkg was interrupted, you must manually run "dpkg --configure -a" to corrent the problem.

and it gives me a few options after that. on installing and reinstalling and deinstalling packages

---

### Post by divindavid on 2008-07-18
> **philinux said:**
> [edit] You need to be connected to the net

If you can get to a command prompt/terminal. Use this

sudo apt-get --reinstall ubuntu-desktop

then

sudo apt-get update 

Then 
sudo reboot

when i do that i get 
E:P invalid operation ubuntu-desktop

---

### Post by seagullplayer77 on 2008-07-18
I've only seen that happen when I've entered an "apt-get" command wrong. Are you sure you punched it in right, with all the proper dashes?

---

### Post by johnnybravo666 on 2008-07-18
apt-get doesn't have a reinstall command. Use this ```
sudo aptitude reinstall ubuntu-desktop
```

---

### Post by johnnybravo666 on 2008-07-18
> **divindavid said:**
> this is what i get after the gnome-termanal code

E: dpkg was interrupted, you must manually run "dpkg --configure -a" to corrent the problem.

and it gives me a few options after that. on installing and reinstalling and deinstalling packages

Did you run "sudo dpkg --configure -a" ? If not then do so. It may help.

---

### Post by philinux on 2008-07-18
> **johnnybravo666 said:**
> apt-get doesn't have a reinstall command. Use this ```
sudo aptitude reinstall ubuntu-desktop
```

Quite correct, more coffee on it's way.

Should be
sudo apt-get install --reinstall ubuntu-desktop

---

### Post by seagullplayer77 on 2008-07-18
There is a reinstall option for apt-get, but you need to enter the command as "sudo apt-get --reinstall install ubuntu-desktop." That said, both the aptitude and the apt-get commands should work.

---

### Post by mocoloco on 2008-07-18
Whoa.  Before you worry about reinstalling a bunch of stuff, sounds to me like you may just have some messed up configuration. 
I've had issues like this before, after messing around with compiz settings and other things.  Are there any other users set up on this box, and can they log in ok?
Even if you can't confirm that, you can log in to a terminal (Ctrl+Alt+F2) and from the command line rename the hidden folder that contains all the gnome config stuff.
```
mv .gconf .gconfOLD
```
Then Ctrl+Alt+F7 to get back to GDM. When you log in it will recreate the .gconf folder with the default settings.  You may then have to reconfigure your background and some other things but it's a small loss.
If you still can't log in maybe try renaming .gnome2 as well and try again.

---

### Post by divindavid on 2008-07-18
> **johnnybravo666 said:**
> Did you run "sudo dpkg --configure -a" ? If not then do so. It may help.

i did and it gave me a bunch of options and what not

---

### Post by divindavid on 2008-07-18
> **mocoloco said:**
> Whoa.  Before you worry about reinstalling a bunch of stuff, sounds to me like you may just have some messed up configuration. 
I've had issues like this before, after messing around with compiz settings and other things.  Are there any other users set up on this box, and can they log in ok?
Even if you can't confirm that, you can log in to a terminal (Ctrl+Alt+F2) and from the command line rename the hidden folder that contains all the gnome config stuff.
```
mv .gconf .gconfOLD
```
Then Ctrl+Alt+F7 to get back to GDM. When you log in it will recreate the .gconf folder with the default settings.  You may then have to reconfigure your background and some other things but it's a small loss.
If you still can't log in maybe try renaming .gnome2 as well and try again.

yeah i did that and nothing happened after i put the code in. and how to i rename the .gnome2???

---

### Post by divindavid on 2008-07-18
> **johnnybravo666 said:**
> apt-get doesn't have a reinstall command. Use this ```
sudo aptitude reinstall ubuntu-desktop
```

i did that and i got the same 
E: dpkg was interrupted, you must manually run " dpkg --configure -a"

:(:(:(:(
god this sucks nothing works

---

### Post by SunnyRabbiera on 2008-07-18
you need to run this command in a terminal: sudo dpkg --configure -a

Its possible this is an issue with gdm or gnome, after you see if you can fix your apt issue we can try to help you.
But i am suspecting a bad install or something like that here.

---

### Post by divindavid on 2008-07-18
i am thinking of getting the ubuntu server to controll all of my home computers and for email and what not

---

### Post by divindavid on 2008-07-18
> **SunnyRabbiera said:**
> you need to run this command in a terminal: sudo dpkg --configure -a

Its possible this is an issue with gdm or gnome, after you see if you can fix your apt issue we can try to help you.
But i am suspecting a bad install or something like that here.
it happened when i did an update of 528 updates

---

### Post by SunnyRabbiera on 2008-07-18
well it might have been one of the updates, did you use the ubuntu experimental stuff or anything?

---

### Post by divindavid on 2008-07-19
> **SunnyRabbiera said:**
> well it might have been one of the updates, did you use the ubuntu experimental stuff or anything?

nope

---

### Post by houbysoft.xf.cz on 2008-07-19
Have you tried to login with a failsafe session?

---

### Post by divindavid on 2008-07-19
how do i do that

---

### Post by mocoloco on 2008-07-25
> **divindavid said:**
> yeah i did that and nothing happened after i put the code in. and how to i rename the .gnome2???

Same way, mv means "move", and it's also how you rename a file, by "moving" it to a new filename.

```
mv .gnome2 .gnome2OLD
```

> Have you tried to login with a failsafe session? 
 >> how do i do that 

On the login screen (GDM) click "options" and then "select session", then "failsafe GNOME".
Come to think of it that's easier than all my renaming ideas, failsafe should bypass potentially problematic settings for you :)

---

### Post by crtlbreak on 2008-07-28
> **seagullplayer77 said:**
> .....Try Alt+F2, just for kicks.

ALT + F2 is default for "run application"

---

