---
title: "New Ubuntu User Problems with AWN + More"
date: 2008-08-07
forum: New to Ubuntu
---

### Post by Socca on 2008-08-07
Hey!
If in wrong thread, could you please move it to correct one since I have no clue which subforum this specific thread should go to.

Start off with saying Hey! Name is Sean, age 16 and currently testing out Linux. I have installed Ubuntu on my old laptop for just work and its been very helpful. I helped a friend install it and he wanted AWN Navigator on it. I installed i and it was all good. With me though....I don't see anything. I clicked on AWN in Accessories and it made a quick grey box in the top left corner and then it disappeared. I checked System Monitor and all the awn "processes" were Sleeping. Not sure if that matters. I have no clue what the problem is but I would really like to have it working.
Check the screenshot.

2nd question is I want to install Shiftie July Black GTK and Metacity themes. I downloaded them and I thought they would be tar.gz files but they werent. The were folders with images inside. I have no clue how to go around it but I would really like to make my desktop more sexy :p


Thanks for the help

Socca

---

### Post by kestrel1 on 2008-08-07
Hi Sean Welcome to Linux.
Have you got Compiz running?
Personally I prefer Cairo Dock to AWN, it is easy to get running & looks better than AWN.

---

### Post by gjoellee on 2008-08-07
how much RAM do you have? this may happen if you have like 512mb of RAM...

---

### Post by Socca on 2008-08-07
> **kestrel1 said:**
> Hi Sean Welcome to Linux.
Have you got Compiz running?
Personally I prefer Cairo Dock to AWN, it is easy to get running & looks better than AWN.

How can i see that Compiz is running?

Would you also be able to tell me ow to get My Panel menu all the way to the left instead of like a bit left of center.

---

### Post by gjoellee on 2008-08-07
> **Socca said:**
> Hey!
2nd question is I want to install Shiftie July Black GTK and Metacity themes. I downloaded them and I thought they would be tar.gz files but they werent. The were folders with images inside.


right click on the folder and click on "Create Archive", this should make the folder compressed to .tar.gz

---

### Post by OutOfReach on 2008-08-07
AWN can't start without Compiz, to enable compiz goto System>Preferences>Appearance and goto the Visual Effects tab and select 'Normal'. And try to start AWN again. :)

---

### Post by gjoellee on 2008-08-07
> **Socca said:**
> How can i see that Compiz is running?

Would you also be able to tell me ow to get My Panel menu all the way to the left instead of like a bit left of center.

Go to System->Administration->System Monitor->Precesses and look for compiz if it is there compiz is running

---

### Post by gjoellee on 2008-08-07
you can install compiz by clicking on the link below: 
[apt://compizconfig-settings-manager](apt://compizconfig-settings-manager)

---

### Post by OutOfReach on 2008-08-07
Compiz is already installed by default in Ubuntu.

---

### Post by gjoellee on 2008-08-07
> **OutOfReach said:**
> Compiz is already installed by default in Ubuntu.
  I havent seen that yet neither in Intrepid Ibex or Hardy Heron

---

### Post by LowSky on 2008-08-07
if you want to make sure compiz is running, install the foloowing application and make it start up with logon, it also make it easy to turn off compiz effect if needed. This was something I missed when upgraded from 7.04's beryl. and its great for people who hate typeing in CLI all day

sudo apt-get install fusion-icon

---

### Post by Socca on 2008-08-07
OK Compiz is running but can't get normal desktop effects to work. It says Desktops Effects could not be enabled.

So I am trying Cairo Dock but guess what. The repostitories are old and corrupt so i can't do that. Now i don't know how to install it.

Does anybody know how I can move my Menu icon + Applications Places Systems to faar left?

Thanks

---

### Post by nkri on 2008-08-07
To install from the repo:

In Synaptic, go to Settings>Repositories>Third Party Software and click add.

Paste this into the add line:
```
deb http://repository.cairo-dock.org/ubuntu hardy cairo-dock
```

Click Add, OK, and in the top left corner of Synaptic, click Reload.  Now search "cairo-dock" (without the quotes) and it should be there.

As for moving things in the panels: right click the applet, select move, and move the mouse to where you want it.  Click again to stop moving it.

Good luck!
-nkri

---

### Post by quinnten83 on 2008-08-07
> **OutOfReach said:**
> AWN can't start without Compiz, to enable compiz goto System>Preferences>Appearance and goto the Visual Effects tab and select 'Normal'. And try to start AWN again. :)

he is running screenlets, so he should be able to run awn without compiz.
AWn has some quirks, it didn't work well on my desktop either while all the while running like peach om my laptop.
You can try installing it from their launchpad repositories. But I can't remember the repos name right now.

---

### Post by Socca on 2008-08-08
Well to start off, thanks everybody for the help they have given me. My panel is fixed. Instead of AWN i have installed Cairo Dock and thats worked.

But i have a last question.

I have cairo dock installed ( Check screenshot ). But i want to change the icons to more suitable ones for my desktop + the background of the cairo dock covers the bottom of my own desktop background when its not being hovered over my mouse and when it is.

If you see the screenshot, you will understand. Is there anyway I can fix that?

Thanks,

Socca

---

### Post by kestrel1 on 2008-08-08
You can choose your own icons by right clicking on a launcher in the dock & select Modify this Launcher.
When the modify launcher window appears you can change the icon by changing the path to the image in Image's name or path. Click on Load to select a different location.
You can make the dock autohide by going to the Cairo-dock configuration page & under Position tick the box that says Activate Auto-Hide?
Hope that helps

---

### Post by Socca on 2008-08-08
No not autohide. Its shown all the time and not when the window is maximed. But when im on my desktop and its shown its got black background. Can i make it transparent so i see my desktop background behind it ?

---

### Post by kestrel1 on 2008-08-08
Sorry, miss understood what you wanted. Yes you can change the transparancy. Go to Cairo configuration page & under Background move the slider to 0.000 under Background Image

---

### Post by fabounet on 2008-08-11
launch it with "cairo-dock -F" for fake transparency, or launch a composite manager (compiz, xcompmgr, etc)

---

### Post by Socca on 2008-08-11
What do you mean with cairo dock -F ? How do I launch that?

---

### Post by fabounet on 2008-08-11
in a terminal.
or in the starting applications list if you want it on start-up.
only if you can't run a composite manager of course.

---

### Post by kestrel1 on 2008-08-12
type it in a terminal

---

