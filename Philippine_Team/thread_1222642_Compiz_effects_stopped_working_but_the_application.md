---
title: "Compiz effects stopped working but the application is still there"
date: 2009-07-25
forum: Philippine Team
---

### Post by randytan on 2009-07-25
Hi All!

I've encountered a little issue with compiz, when you check it in the preferences, it's still there but the effects are not working.

It all started like this, I had to hook up my notebook to a projector to test out a presentation my sister made for my nephew's function tomorrow. Thing is, before the image could come out via the projector, the notebook gave a warning of sorts that I had to run using a virtual resolution and asked if I wanted to continue, upon saying that I wanted to, I was required to enter my password and to log off then log back on.

Once this was done, I was able to link with the projector but I noticed that my workspaces was reduced back to 2 instead of the usual 4 and using the compiz short cuts to make the cube rotate only yielded a display of sorts with highlighted workspaces instead of the usual cube rotating. And the burning animation I usually get when I close windows no longer shows itself.

Other than that, the unit seems to be running normally but I'd really like to get them effects back. Can anyone help me out?

Bad trip talaga to.

Your assitance and guidance is, as usual, greatly appreciated.

Hope to hear from y'all soon. :)

---

### Post by kingkalag on 2009-07-25
tol anong klasing notebook yan if you dont mind me asking.
try mo kayang remove ang compiz then reinstall it

```
 sudo apt-get remove --purge compiz compiz-core 
```

reboot (coldstart) and reinstall compiz



tapos sa projector as fas as i know kailangan mo yatang edit mona ang 
/etc/X11/xorg.conf

 to mirror desktop ```
 xrandr --auto 
```

for VGA   ```
 xrandr
xrandr --output VGA --auto 
```

for DVI ```
 xrandr --output TMDS-1 --output LVDS --off 
```

```
 sudo gedit /etc/X11/xorg.conf 
```

folks correct me if Im wrong

```
  SubSection "Display"
                Virtual      2960 1050
        EndSubSection  
``` 
  
palitan mo lang ang 2960 1050 ng size ng external screen.
tapos add mo to sa Device section:

```
 Option          "FramebufferCompression" "off" 
```

 ang xorg.conf should look like this

```
 Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        SubSection "Display"
                Virtual      2960 1050
        EndSubSection
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Option          "FramebufferCompression" "off"
EndSection 
```

Im guessing your laptop have a DVI.
unplug it tapos restart and run

```
 xrandr --output TMDS-1 --left-of LVDS 
```

for more option run  

```
 xrand 
```

good luck

---

### Post by abhilashm86 on 2009-07-25
maybe you can use compiz-check for checking fault in it, [use this ]("http://http://www.ubuntugeek.com/check-compiz-will-run-on-your-ubuntu-desktop-or-not.html"), also workplaces are controlled by you, open ccsm, then go to general options, then Desktop Size, set horizontal and vertical to 4, done.........

---

### Post by kdetech on 2009-07-25
If problem persists boot in recovery mode and choose XFIX.

Now only if you have Nvidia or ATI card reinstall driver.

---

### Post by kingkalag on 2009-07-25
if you have nvidia GPU dont push the video hard...

---

### Post by randytan on 2009-07-25
> **kingkalag said:**
> tol anong klasing notebook yan if you dont mind me asking.
try mo kayang remove ang compiz then reinstall it

```
 sudo apt-get remove --purge compiz compiz-core 
```

reboot (coldstart) and reinstall compiz.....

good luck

Hi kingkalag,

The notebook is a Fujitsu LifeBook S2020 with an AMD prcessor and an ATI video.

I'll try the uninstall - reinstall bit like you suggested. I'll need an internet connection for that since I used synaptic to install it.

As for the projector, it already works fine with the notebook so I'll leave it be for now since I have to do the slideshow later already.

I don't think that I'm pushing the video as it worked fine before, a bit slow, but it worked. I attribute the slowness to the notebook as it's not know for it's speed but rather to let you work and get things done :)

abhilashm86: I'll also try your suggestion of using compiz-check before the uninstall - reinstall.

I'll let you all know how it turns out.

Thanks for the assistance.

If you guys still have any tip or suggestions, please keep them coming, this benefits us all anyways, right?

---

### Post by randytan on 2009-08-01
Well folks, I tried uninstalling compiz-core, shutting down, starting up, and reinstalling compiz-core.

It still doesn't work!!!! :confused: :frown: ](*,) 

On the up side though, without the effects, the notebook does things a bit faster...

May just leave it as is for that particular unit.

Would still like to know the solution though in the event that it happens to the other units as well.

HELP!!!!

---

### Post by echo6 on 2009-09-20
Hmm, I noticed very similar behaviour with my laptop (Intel 945GM/GMS)

Everything works fine, but I loose the capability of enhanced zoom in/out desktop functions.  Switching workspaces doesn't work in the same way either, e.g. workspace switcher doesn't move to the appropriate workspace when using the keyboard shortcuts.

I can get by but these features would enhance presentations greatly!

---

### Post by Samhain13 on 2009-09-20
From experience, when for some reason you turn off Desktop Effects, then turn them back on, your customisations are lost.


So, you'll have to customise your desktop effects again. But this time around, save the profile. In the CompizConfig Settings Manager, you'll find the saving thing under Preferences. Choose "Export" and give your profile a file name, like "something.profile".

When you turn Desktop Effects off in the future, and you turn them back on again, go back to the Settings Manager then import your "something.profile".

But I'm using 8.04. I don't know if this has changed in the current Ubuntu.

---

### Post by ache109 on 2009-09-21
> **Samhain13 said:**
> From experience, when for some reason you turn off Desktop Effects, then turn them back on, your customisations are lost.


So, you'll have to customise your desktop effects again. But this time around, save the profile. In the CompizConfig Settings Manager, you'll find the saving thing under Preferences. Choose "Export" and give your profile a file name, like "something.profile".

When you turn Desktop Effects off in the future, and you turn them back on again, go back to the Settings Manager then import your "something.profile".

But I'm using 8.04. I don't know if this has changed in the current Ubuntu.

In my experience, just like sir samhain said, when you turn off desktop effects, all will be somewhat reset.

What ive done is: open terminal> type compiz > enter. By clicking enter compiZ will renable again.  then activate deskTop effects again (you can choose best or normal). And just researched on google that compiz is having conflicts with metacity, Which enables when you disable desktop effects. Just disable metacity and compiz will be fine.

---

### Post by Ravskie on 2009-09-23
> **Samhain13 said:**
> From experience, when for some reason you turn off Desktop Effects, then turn them back on, your customisations are lost.


So, you'll have to customise your desktop effects again. But this time around, save the profile. In the CompizConfig Settings Manager, you'll find the saving thing under Preferences. Choose "Export" and give your profile a file name, like "something.profile".

When you turn Desktop Effects off in the future, and you turn them back on again, go back to the Settings Manager then import your "something.profile".

But I'm using 8.04. I don't know if this has changed in the current Ubuntu.

i experienced that one also need to re customized my desktop effects again and save a profile i'm using jaunty .....

---

