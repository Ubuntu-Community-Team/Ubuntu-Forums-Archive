---
title: "Video Resolution"
date: 2008-09-21
forum: New to Ubuntu
---

### Post by john010766 on 2008-09-21
HI All

My first time with Linux type Os since around 2000ish

I have just installed an older version of UB I think 6 (odd) it wont let my monitor go to 1440x900 @32 bits, I know the Video card can handle but I am not sure about configuring it? Any ideas would be welcome

Many thanks 

John

---

### Post by phidia on 2008-09-21
What video card do you have? If you don't know open a terminal and enter this: > lspci | grep VGA Also see the video wiki [here]("https://help.ubuntu.com/community/Video").

---

### Post by roger_1960 on 2008-09-21
HI

Try in terminal

sudo displayconfig-gtk

ten enter your password, then edit the settings in the GUI to suit.  Good luck!

---

### Post by john010766 on 2008-09-21
HI All 
and thanks for the timely response, will try it tomorrow brain fired now.

John

---

### Post by john010766 on 2008-09-22
> **john010766 said:**
> HI All 
and thanks for the timely response, will try it tomorrow brain fired now.

John

hi All
I have tried what everyone says and it only lets me select 1024x768

---

### Post by bhadotia on 2008-09-22
Here is quote from the [Comprehensive Video Howto]("http://ubuntuforums.org/showthread.php?t=766683"):
> **[COLOR=DarkRed]Resolution:[/COLOR]** To enable the correct display resolution in Ubuntu, you have several options. First of all, there is the fairly useless tool in System > Preferences, the soon to be dead displayconfig-gtk tool, and finally, RandR - the newest method. There will be a graphical frontent (GUI) for RandR soon (keep an eye out for it in System > Administration), but for now you will need to use the command line. Let's say you wanted to change your resolution to 1280x800, you would need to execute the following command:

**sudo xrandr -s 1280x800**

If that fails, bring up a list of "supported" resolutions with this command:

**sudo xrandr -q**

Use the first command again and set the highest resolution that RandR claims is supported. Once that is set, try setting the resolution you know is correct, as it may now accept that resolution.

If you're still having issues, press Alt+F2 and type "gksudo displayconfig-gtk" (without "gtk" in Kubuntu), type your password and execute, then select the resolution you want from the list. Some of you may have to select a different screen/monitor in the list before you can successfully change the resolution. Reboot/logout if necessary, then go to [Launchpad]("http://launchpad.com/") and report a bug.

Hope this helps;-)
Abhishek

---

### Post by john010766 on 2008-09-22
> **bhadotia said:**
> Here is quote from the [Comprehensive Video Howto]("http://ubuntuforums.org/showthread.php?t=766683"):


Hope this helps;-)
Abhishek

hi have managed to do this but lost all my menus etc etc 

John

---

### Post by bhadotia on 2008-09-22
> **john010766 said:**
> hi have managed to do this but lost all my menus etc etc 

John
What does "etc. etc." exactly mean?
You say you lost all the menus this means that you lost your panels (top and bottom) both, am I right?
If this is so please try restarting and if this does not help post back with exact description of the problem.

---

### Post by john010766 on 2008-09-22
> **bhadotia said:**
> What does "etc. etc." exactly mean?
You say you lost all the menus this means that you lost your panels (top and bottom) both, am I right?
If this is so please try restarting and if this does not help post back with exact description of the problem.

Hi this means exactly that, I have a desktop but no visible menus, bars etc
except for a cd-r icon

---

### Post by bhadotia on 2008-09-22
> **john010766 said:**
> Hi this means exactly that, I have a desktop but no visible menus, bars etc
except for a cd-r icon
Alright first try restarting the computer and see what happens and then post back.
In case you are wondering how to start firefox if you don't get the panels back after restarting then press alt+f2 and type "firefox" in the run box.

---

### Post by john010766 on 2008-09-22
> **bhadotia said:**
> Alright first try restarting the computer and see what happens and then post back.
In case you are wondering how to start firefox if you don't get the panels back after restarting then press alt+f2 and type "firefox" in the run box.

hi 
tried that still no panels, absolutely nothing i odnt even get a run box

---

### Post by bhadotia on 2008-09-22
Oh sorry for the late reply .


How are you using the fiefox if you don't even get the run box?
Is your sceen resolution correct after the restart?

---

### Post by john010766 on 2008-09-22
> **bhadotia said:**
> Oh sorry for the late reply .


How are you using the fiefox if you don't even get the run box?
Is your sceen resolution correct after the restart?

I am having to use the cd-r then search for a terminal window

---

### Post by john010766 on 2008-09-22
> **bhadotia said:**
> Alright first try restarting the computer and see what happens and then post back.
In case you are wondering how to start firefox if you don't get the panels back after restarting then press alt+f2 and type "firefox" in the run box.

have tried restarting, still nothing just wallpaper
What run box I get no top or bottom panels at all the only way I can stasrt FF is buy leaving a cd in the drive then, using search for a term window

---

### Post by bhadotia on 2008-09-22
> **john010766 said:**
> I am having to use the cd-r then search for a terminal window
Alright in the terminal type:
```
gnome-panel &
```and then right click on the panel and select 'add to panel' option and then add all the needed things manually, e.g, adding the 'Menu Bar' will bring back the ubuntu menu. You can drag and drop the panel to the required position. Right click on the panel and select new panel to add another panel and similarly configure it.
To move the panel objects/applets middle click and hold and drag  the item or right-click and select 'Move'.


This way we will be able to manually bring back your panels atleast.

If there is anything else missing on your desktop or you need some more help/clarification please post back.

Hope this helps;-)
Abhishek

---

### Post by john010766 on 2008-09-22
> **bhadotia said:**
> Alright in the terminal type:
```
gnome-panel &
```
and then right click on the panel and select 'add to panel' option and then add all the needed things manually, e.g, adding the 'Menu Bar' will bring back the ubuntu menu. You can drag and drop the panel to the required position. Right click on the panel and select new panel to add another panel and similarly configure it.
To move the panel objects/applets middle click and hold and drag on the item.


This way we will be able to manually bring back your panels atleast.

If there is anything else missing or you need some more help/clarification please post back.

Hope this helps;-)
Abhishek



it says 

sh: gnome-panel: not found
[1] + Done(127)                  gnome-panel

---

### Post by bhadotia on 2008-09-22
> **john010766 said:**
> it says 

sh: gnome-panel: not found
[1] + Done(127)                  gnome-panel
Why are you using the sh shell?
Type:
```
bash
```
And try again and post back.

---

### Post by waspbr on 2008-09-22
there was a bug about gnome-panel not being installed in some update on some boxes. 

just enter 

```
sudo apt-get install gnome-panel
``` 

or look for gnome-panel in synaptic if you prefer, install it and it shouldwork.

for the resolution, the best method I found was  to do 

```
sudo displayconfig-gtk
```

if your monitor is already selected and the resolution is too low, select a generic monitor of the size(resolution) you want or the highest your monitor can handle, mine is 1680x1050 for example.

then after that you will be able to select the resolution you want. 

on the event that your GDM's resolution may get a little funky check out this link:

[https://help.ubuntu.com/community/FixVideoResolutionHowto]("https://help.ubuntu.com/community/FixVideoResolutionHowto")

this link gives a pretty complete how to on the whole resolution thing, good luck

---

### Post by john010766 on 2008-09-22
> **waspbr said:**
> there was a bug about gnome-panel not being installed in some update on some boxes. 

just enter 

```
sudo apt-get install gnome-panel
``` 

or look for gnome-panel in synaptic if you prefer, install it and it shouldwork.

for the resolution, the best method I found was  to do 

```
sudo displayconfig-gtk
```

if your monitor is already selected and the resolution is too low, select a generic monitor of the size(resolution) you want or the highest your monitor can handle, mine is 1680x1050 for example.

then after that you will be able to select the resolution you want. 

on the event that your GDM's resolution may get a little funky check out this link:

[https://help.ubuntu.com/community/FixVideoResolutionHowto]("https://help.ubuntu.com/community/FixVideoResolutionHowto")

this link gives a pretty complete how to on the whole resolution thing, good luck


Hi And thanks for all your help, I have managed to get things working and going well with the correct resolution, but have 2 error messages one is

0AFIID:MixerApplet and the other is missing a recycle bin ( which is not longer on the desktop how can I rebuild these?

---

### Post by bhadotia on 2008-09-22
> **john010766 said:**
> Hi And thanks for all your help, I have managed to get things working and going well with the correct resolution, but have 2 error messages one is

0AFIID:MixerApplet and the other is missing a recycle bin ( which is not longer on the desktop how can I rebuild these?
Glad to hear that your panel has finally started working. For the remaining problem solution is actually easy:
Right-click on the panel and select 'add to panel', then add 'volume control', 'notification area', and 'trash' applets to the proper panels.
 And I'm just curious: as **waspbr** said, was your gnome-panel really un-installed after you changed the resolution of the monitor? I mean he said that the bug showed up when you updated the system but you just changed the resolution. 

Hope that helps.

---

### Post by john010766 on 2008-09-22
> **bhadotia said:**
> Glad to hear that your panel has finally started working. For the remaining problem solution is actually easy:
Right-click on the panel and select 'add to panel', then add 'volume control', 'notification area', and 'trash' applets to the proper panels.
 And I'm just curious: as **waspbr** said, was your gnome-panel really un-installed after you changed the resolution of the monitor? I mean he said that the bug showed up when you updated the system but you just changed the resolution. 

Hope that helps.

HI 
I try to add the mixer and trash but it just comes up with 

The panel encountered a problem while loading "OAFIID:GNOME_MixerApplet".


The gnome became uninstalled after I changed the resolution, but I thing it could be the drivers

---

### Post by bhadotia on 2008-09-22
Give the terminal output of :
```
/usr/lib/gnome-volume-manager/gnome-volume-manager --sm-disable
```
What error is the trash applet giving?

---

### Post by john010766 on 2008-09-22
they are giving the same error message

0AFIID:

The panel encountered a problem while loading "OAFIID:GNOME_Panel_TrashApplet".


The panel encountered a problem while loading "OAFIID:GNOME_MixerApplet".


theres no output from the command you listed

---

### Post by waspbr on 2008-09-22
if you want you can re-enable the recycle bin in the desktop in the following way

press ALT + F2

type

```
gconf-editor
```

go to apps>nautilus>desktop

tick the box that says "trahs_icon_visible"

this should sort you out, as for the other problem... I am not sure, you might have better luck googling for it

[COLOR="Red"]update:[/COLOR] just had an idea about the applets that might work, go to synaptic and search for "gnome-applets"

it should already be installed, if it is not mark, otherwise set it for re-installation. 

good luck

---

### Post by john010766 on 2008-09-22
hi
Done and Done

Thanks for all the help very much appreciated.

Just to connect the ipod now. LOL


John

---

### Post by waspbr on 2008-09-23
Don't forget to mark the thread as solved, the option is in the thread tools menu

---

