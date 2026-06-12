---
title: "Horizontal bars at the top of my desktop screen"
date: 2012-01-29
forum: New to Ubuntu
---

### Post by rachelisusinglinux on 2012-01-29
So a few weeks ago I broke the hard drive on my netbook and after replacing it installed Ubuntu and fell in love with Linux (even though I'm fairly computer retarded, it is just so easy to use and fast). So I decided to resurrect my old Vista laptop to run Ubuntu as well. It runs perfectly but when I first started it up there was a band of multicoloured stripes at the very top of the desktop- this was not present if I opened any windows, merely on the home desktop. So I changed the back ground. Still there. So I restarted. Now most of the lines were black. Restarted again and now there are just four black lines, as in the enclosed image.

It doesn't impact on the function at all, and like I said it isn't present in any of the windows I open. It's just a bit annoying to have on the desktop. Does anyone know how to fix it?

I'm running Oneiric Ocelot (32 bit) on a Samsung R60+. I know it is not the copy that is at fault because its from the same USB boot I used to install it on my netbook and that works fine.

---

### Post by corncob on 2012-01-29
Welcome to the forums!  I don't have the problem myself so I can't test it but I'll tell you what I'd try.  Open the Terminal and install gconf-editor
```
sudo apt-get install gconf-editor

```
Then run it by typing 
```
gconf-editor
```
in the Terminal. (You could also install 'configuration editor' from the software center and run it from the Dash).  When opened, go to apps/metacity/general/composting manager and check the box.

---

### Post by rachelisusinglinux on 2012-01-29
Thanks for the advice- very clear! Did as you suggested, sadly they are still there but they are pink now?? No idea why, they obviously aren't in the way because they don't interfere with any of the windows but they are still just a bit annoying!

---

### Post by corncob on 2012-01-30
Phooey!  Made it worse.  Anyway, you can always uncheck that box.  What happens if you press [F11] (toggles the panel on/off)?

---

### Post by grahammechanical on 2012-01-30
I saw you post last night. Or was it early this morning. I had now idea what to suggest but looking at the images again an idea has come into my head.

Are you using CompizConfig Settings Manager? If not then my idea is useless.

In CompizConfig Settings Manager (CCSM) there is a setting called Window Decoration. Enabling that will/should put a shadow along the top of the desktop where the wallpaper meets the top panel. I have this set in 11.10 and it is noticeable because I have the opacity of the top panel set to zero (through the Unity Plugin).

I wonder if this issue is due to the shadow effect not working correctly on your machine. This is just another of my out of nothing insights.

Regards.

---

### Post by corncob on 2012-01-30
It seems to me that my system already had compiz installed.  It was the CompizConfig Settings Manager (CCSM) that I had to download in the Software Center to see what the settings are and to change them. Windows Decoration was checked.  I unchecked it but, not having the problem myself, I had nothing to test.  It seemed to screw things up a bit so I re-checked it.

Since enabling the compositing_manager had some effect, try unchecking compositor_effects -- just a stab in the dark.

---

### Post by rachelisusinglinux on 2012-01-30
Thanks for the tips... so here is what has happened so far. First off, the horizontal bars are now green, which I guess helps blend with the background a bit. Secondly they have sadly not altered much (after deselecting window decoration some of them went thin and black) despite trying both suggestions. F11 seems to do nothing (possibly because it is half broken off). If I go to workplace switcher, again it is gone.

The did disappear very briefly and here is how. Whilst in config manager, I got a bit intrigued by 3D desktop and foolishly decided to click on it (which disables the unity plug in). This made all my icons disappear and also the lines. After a long time of trying to work out how to find anything on my computer I resorted to the terminal and reset unity. This made the icons reappear but without the bars! Success I thought. Then the whole thing froze and crashed and once I switched it back on... bars again. Hmmmm.

---

### Post by jbalazs on 2012-01-30
Remote chance but try to run "nvidia-xconfig" from a terminal

Or try when starting up 
press esc when you see the purple screen
Press whatever key corresponds to "more options" (i don't remember which one it is..), and choose nomodeset.

---

### Post by corncob on 2012-02-04
One more wild thought:  You say your F11 key is messed up -- do you have another keyboard to try?

---

