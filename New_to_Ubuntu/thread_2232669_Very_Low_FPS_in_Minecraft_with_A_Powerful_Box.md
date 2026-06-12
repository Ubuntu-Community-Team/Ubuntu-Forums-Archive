---
title: "Very Low FPS in Minecraft with A Powerful Box"
date: 2014-07-03
forum: New to Ubuntu
---

### Post by ChemE on 2014-07-03
I haven't used linux in over a decade and forgot almost all of what I once knew so I'm a total noob.  I just built what is intended to be a Minecraft FTB gaming computer that has altogether respectable components that should easily be running the Direwolf20 FTB pack at 60 fps+.  My Win7 laptop has dramatically inferior hardware and can manage 100+ fps.  I very much suspect my video card drivers are the issue but I'm a little out of my depth when it comes to isolating the issue and fixing it.  Here is the hardware/software I'm working with:

Mobo: AsRock H81M-ITX
Proc: Intel Pentium G3220 (2x3.0Ghz which is plenty to run modded minecraft)
Video card: MSI GTX 750Ti (nVidia chip)
SSD: Samsung 840 EVO 120GB
Ram: G.Skill 8GB DDR3-1600 9/9/9/24 timings
In short this rig should run modded minecraft without breaking a sweat; it was constructed from ground up to do so.

OS: Lubuntu 14.04LTS freshly installed, software update run with the Software Updater
FTB Launcher: I downloaded the ftb launcher.jar and ran it, it started right up downloaded the pack I wanted (Direwolf20) and launched the game no problems at all 142 mods loaded.

F3 shows that I'm getting 2-10 fps and even with all the video settings cranked down to minimum I only manage 20 fps staring at my feet not doing anything.

The output from```
lspci | grep VGA
``` is blank.

Can anyone advise me as to what to do next?

---

### Post by ChemE on 2014-07-03
I just installed glmark2 and produced a score of 186 which appears to be dramatically lower than it should be given my hardware.  It kept kicking a "GLX does not support GLX_EXT_swap_control or GLX_MESA_swap_control warning for each individual test" whatever that means.

---

### Post by sandyd on 2014-07-03
Have you installed the nvidia drivers from 'Additional Drivers'?

---

### Post by ChemE on 2014-07-03
When I open Software Update it says I'm up to date.  I then click settings and the Additional drivers tab and it still says "there are no additional drivers available".  But to answer your question I would say no I have not though not for a lack of trying.

---

### Post by gabriel.majeri6 on 2014-07-03
You should update to the latest Nvidia drivers.

Try these commands in the terminal for the latest Nvidia drivers (they are very new):
```

sudo add-apt-repository ppa:xorg-edgers
sudo apt-get update
sudo apt-get install nvidia-340

```
Then press 'y', wait for it to download the ~270MB drivers, unpack and _reboot_.
Try playing FTB and see if it it works well. Also see if lspci shows anything.

---

### Post by ChemE on 2014-07-03
The pack is building now...results soon.  Thanks for the help by the way.  When I came back from reboot my screen resolution moved from 1024x768 to 1920x1440 and now I have 2 sizes of text.  The text in xterm is pretty small and the fonts on lxde (or is it openbox?) are absolutely massive.  So much so that navigation is very difficult.

---

### Post by ChemE on 2014-07-03
Thank you very very much Gabriel.  As soon as I logged back into my SSP game F3 showed 150-250 fps.  Even with every setting turned up I'm still getting 100+ fps while looking around wildly.  Now if I can fix my system fonts I'll have a stable Lubuntu Direwolf20 gamer for $600.

---

