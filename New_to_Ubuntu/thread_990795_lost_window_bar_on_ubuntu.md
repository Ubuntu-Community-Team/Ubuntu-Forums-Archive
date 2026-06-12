---
title: "lost window bar on ubuntu"
date: 2008-11-23
forum: New to Ubuntu
---

### Post by Paul VW on 2008-11-23
please help, or I will go back to windows, as I am getting fed up with getting nowhere!!

I did post a thread about this problem a couple of weeks ago [http://ubuntuforums.org/showthread.php?t=967442](http://ubuntuforums.org/showthread.php?t=967442)

my wifes account has (not mine!!) has lost its window bar (this bit at the top, eg its brown and currently says "Ubuntu Forums - Post New Thread")

I have tried a lot of things like changing the appearance settings, I even deleted her account, and made a new one with a different name, and the problem is still there.

its very difficult to do anything in terminal, as that appears as a white box ans I cant see what I am typing!!

would some screen shots help?

---

### Post by cdtech on 2008-11-23
"would some screen shots help?"

Yes,,

---

### Post by Paul VW on 2008-11-23
ok here you go, 1 screen shot of terminal, and one of firefox with the window bar missing

---

### Post by lswest on 2008-11-23
try running ```
gtk-window-decorator --replace
``` from the run command dialog (alt + F2)

---

### Post by Paul VW on 2008-11-23
no, did not change a thing :confused:

---

### Post by lswest on 2008-11-23
> **Paul VW said:**
> no, did not change a thing :confused:

Hmm, then you can try running ```
metacity --replace
``` from the same window dialog as before.  If that also doesn't work, what's your graphics card, and are you using compiz?  Give me some info about your graphical setup (screen resolution, driver, card, etc.)

Also, please post the output of ```
uname -r
``` from the terminal (applications-->accessories-->terminal).

Thanks, and I think we can fix this yet.

---

### Post by Paul VW on 2008-11-23
metacity worked, but when I closed the terminal window I lost it.

when I re-opened terminal, I now cant type in it. time for a reboot I think.

I have a onboard card on a dell desktop, been using ubuntu for 3 years never touched the graphical setup

---

### Post by lswest on 2008-11-23
> **Paul VW said:**
> metacity worked, but when I closed the terminal window I lost it.

when I re-opened terminal, I now cant type in it. time for a reboot I think.

I have a onboard card on a dell desktop, been using ubuntu for 3 years never touched the graphical setup

if you run it from the alt+F2 dialog (run command) it will run in the background.  If that solves it for you it should work after every reboot, if not add it to the sessions menu under System-->Preferences-->Sessions

---

### Post by pixelstuff on 2008-11-23
look in the system-> preferences -> compizconfig settings manager if you have "windows decorations" under "effects" activated, if not do so. If you have to install it it is called "Advanced Desktop Effects Settings" in the Add/Remove app.

---

### Post by chuckyp on 2008-11-23
Its a problem with your window decorations. As others have suggested I would hit alt+F2 and type in metacity --replace .  Also you may want to go to Preferences > Appearance there should be a tab called "Visual Effects"  turn them off for the time being. Untill you get your video card issues sorted out.

---

### Post by Paul VW on 2008-11-23
> **lswest said:**
> if you run it from the alt+F2 dialog (run command) it will run in the background.  If that solves it for you it should work after every reboot, if not add it to the sessions menu under System-->Preferences-->Sessions

i tried that a few weeks ago......

got metacity running as a session now, and that seems to work.

I have noticed that compared to my account this one seems to pause when starting up, I dont know if that has something to do with it 

oh and the output of uname -r is 2.6.27-7-generic

---

### Post by lswest on 2008-11-23
> **Paul VW said:**
> i tried that a few weeks ago......

got metacity running as a session now, and that seems to work.

I have noticed that compared to my account this one seems to pause when starting up, I dont know if that has something to do with it 

oh and the output of uname -r is 2.6.27-7-generic

```
sudo lshw -C Display
``` could give us a bit more info about drivers.  As a comparison, could you post the output of the same results from your account (which, I believe, runs fine?) as well?

---

### Post by Paul VW on 2008-11-23
right from my wifes account I get this:

  *-display UNCLAIMED     
       description: VGA compatible controller
       product: 82865G Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0

and mine:
 *-display UNCLAIMED     
       description: VGA compatible controller
       product: 82865G Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0

---

### Post by lswest on 2008-11-23
Well, that didn't quite do what I expected :P  I was expecting there to be a driver= line, but there isn't in either.  I'm not sure, but if it's working for now, I'd stick with that and wait to see if anyone else can give you a more thorough explanation of what went wrong.

---

### Post by Paul VW on 2008-11-23
I have noticed another problem since the upgrade to 8.10, thats I am no longer able to switch user, I have to log out, I dont know if thats related.

---

### Post by lswest on 2008-11-23
Well if you upgraded it might have caused a few problems, a fresh install could possibly fix it for you, but if you don't want to do that then I'm also pretty sure someone here has a fix for you.

---

