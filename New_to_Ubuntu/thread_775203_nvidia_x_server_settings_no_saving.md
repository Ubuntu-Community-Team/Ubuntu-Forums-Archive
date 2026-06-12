---
title: "nvidia x server settings no saving"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by Motif31G on 2008-04-29
hello

it seems my nvidia x server settings are not saving. When I start up Ubuntu it's as if I never tweaked my settings( like digital vibrance or contrast). But once I click on nvidia x server settings agian, the setting appear like I want them. Is there anyway to make it so it stays permanent?

---

### Post by EXCiD3 on 2008-04-29
Are you running nvidia-settings with root permission and are you merging the changes to the xorg.conf file?

---

### Post by Motif31G on 2008-04-29
> **EXCiD3 said:**
> Are you running nvidia-settings with root permission and are you merging the changes to the xorg.conf file?

no i don't believe so, how do I do that?

---

### Post by EXCiD3 on 2008-04-29
You can start nvidia-settings with root permission by pressing Alt-F2 and typing "gksudo nvidia-settings" or run that command from terminal. This allows your settings to be saved to the xorg.conf so that they will be loaded next time you start the xserver. To save to your xorg, on the X Server Display Configuration tab, after you have configure your monitors, click the Save to X Configuration File and make sure the "Merge" checkbox is checked. That should do the trick.

---

### Post by Motif31G on 2008-04-30
> **EXCiD3 said:**
> You can start nvidia-settings with root permission by pressing Alt-F2 and typing "gksudo nvidia-settings" or run that command from terminal. This allows your settings to be saved to the xorg.conf so that they will be loaded next time you start the xserver. To save to your xorg, on the X Server Display Configuration tab, after you have configure your monitors, click the Save to X Configuration File and make sure the "Merge" checkbox is checked. That should do the trick.

ok no good.

I guess what i want to go is have xserver start when ubuntu starts

so my setting are automatically loaded at start up

---

### Post by EXCiD3 on 2008-04-30
Ok it looks like i found a fix for it. I found this in the Nvidia section on the Compiz website: 

> We can set *AA* and *FSAA* settings using an export command in various locations, including the following: 

[LIST]
[*]manually in a terminal after login 
[*]in one of the following files: 
[LIST]
[*]/etc/init.d/xdm 
[*]/etc/profile 
[*]/etc/env.d/03opengl 
[*]/home/user/.bashrc 
[/LIST]
[/LIST]
However, this does not help us with the other options available to us in nvidia-settings, including *Cursor Shadows*, *Vibrance Controls*, and others. 
To address this issue, it is possible to execute the settings file itself from ~/.kde/Autostart or Gnome session manager. To accomplish this, you will need to have nvidia-settings installed. It can then be used to set the desired options. Once this is done, create a bash script 'my-nv-settings.sh`. We will use this script to start the nvidia-settings config file without starting the application. Do not use the '>' character in the script. 

```
>#!/bin/bash[FONT=monospace]
[/FONT]>/usr/bin/nvidia-settings -l &
```

Please be aware that the "-l" part is a lowercase "L" and not an uppercase "i". You can also add a third line to verify that the script is actually running 'touch ~/nvidia'. Next time you login this will create an empty file called ~/nvidia. If it is there then you know the script ran and you are ok. Now make the script executable with 'chmod a+x ~/my-nv-settings.sh'. If using KDE simply move/copy the script to ~/.kde/Autostart. If using Gnome you do not need the script. For Gnome simply insert '/usr/bin/nvidia-settings -l &' into Gnome session manager. You must make sure that nvidia options are started before compiz in order for this to work properly. 
Keep in mind this can also be added to /etc/init.d/xdm or /etc/profile to make the settings global; however, your settings file would also have to be in /root, making this second approach less than ideal.

Original page: [http://wiki.compiz-fusion.org/Hardware/NVIDIA](http://wiki.compiz-fusion.org/Hardware/NVIDIA)

---

### Post by Motif31G on 2008-04-30
this is not working. please keep in mind that i am a linux "noob" and am probably not doing something right. a step by step guide would be helpful

---

### Post by sdennie on 2008-04-30
I think if you just go to System->Preferences->Sessions and add a new startup command that is simply "nvidia-settings -l", it will probably do what you want.

---

### Post by EXCiD3 on 2008-04-30
> **vor said:**
> I think if you just go to System->Preferences->Sessions and add a new startup command that is simply "nvidia-settings -l", it will probably do what you want.

Yes that should do the trick. Sorry if the instructions were a little technical. I was busy and didnt have a chance to write a step-by-step for you.

---

### Post by Motif31G on 2008-04-30
SOLVED!

That did it! Thank you both for all your help!

---

### Post by EXCiD3 on 2008-04-30
Glad you got it fixed! You should click the Star button on posts that help you. It is a way of saying "thanks" that the post helped you. Also mark your thread as solved. At the top there is a Thread Tools button. Unless they removed it with the recent site update there should be a Mark Thread as Solved button. Feel free to contact me if you need help on anything else. Contact info (IM, email, etc) is in my profile.

---

