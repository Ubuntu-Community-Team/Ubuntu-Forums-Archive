---
title: "microsoft mouse 6000 magnifier function"
date: 2011-10-17
forum: New to Ubuntu
---

### Post by R.Freeman on 2011-10-17
My Microsoft wireless laser mouse 6000 works very well on UBUNTU 11.04 and the 11.10 upgrade EXCEPT for the magnifier function which seems to have been lost. The button under the wheel remains unassigned. Without it I have to read the location bar and toolbars with a hand held magnifying glass--very tedious! Can this function be recovered in UBUNTU?

---

### Post by mcduck on 2011-10-18
If your mouse comes with such a function, it's actually something that's built into the Windows drivers of the mouse, not the mouse itself. Since the windows drivers do absolutely nothing outside of Windows, you can't get the exactly same feature.

Luckily for you Ubuntu has it's own magnifier function. Or at least three of them, so you'll even have some choice... :D

First, there's always the text size and Zoom functions available in Universal Access options (in System Settings). I've never tried them so I can't say much about their options or how they work, but since they are specifically made for this kind of purposes I'd assume they should do the job...

What I'd recommend instead, assuming you have a computer that's capable of running the normal Unity desktop with all the effcts and nice stuff, is using the "Enhanced Zoom Desktop"-plugin of the Compiz window manager. It's already instaled by default, bt you still need to start by installing the [compizconfig-settings-manager]("apt:compizconfig-settings-manager") so you can configure it's options.

Once that's done, open CompizConfig, find the "Enhanced Zoom Desktop"-plugin (under the Accessibility section) and make sure it's enabled. Go to it's settings, and you'll get plenty of options for how you want the zooming to behave. Most common basic setup would be setting the "Zoom in" mouse shortcut to "<Super>Button4) and "Zoom Out" to "<Super>Button5". That would allow you to zoom in and out with your mouse wheel when holding down the Super button (the one with the Windows logo on your keyboard).

---

### Post by R.Freeman on 2011-10-18
Thank you for your help.  If I were a kid I'd have it going by now, but I'm a visually impaired old man so it will take a while.

---

### Post by mcduck on 2011-10-19
No problem, and I hope you get it working.

---

### Post by R.Freeman on 2011-10-20
It's hard to believe, but I got off to a bad start in the settings box - clicked here, pushed a couple keys there - and managed to unleash some sort of cataclismic event.  I was distracted and a bit worried as a rapid sequence of screens flashed in front of me.  Ubuntu quickly recovered, however, and the settings box returned, but this time it looked more like what you indicated.  The problem is that whenever I press the super button the sidebar appears with little numbers over the icons (shortcuts).  I tried to change from super to another button but got warning signs.  I decided I'd caused enough disturbance already and backed off.  Is there a way out?

---

### Post by mcduck on 2011-10-20
Don't worry about the numbers appearing in the side bar, it's just because the Super key is also used for the keyboard shortcuts for the programs you have there. It doesn't interfere with the zoom in any way.

...and of course you are free to choose any other modifier key you want for the zoom (Ctrl, Shift, Alt or Super, or even combine some of them together), as long as it's not used for something else already. The warnings are of course important, as they are telling you if the shortcut you tried to pick is already in use.

---

### Post by R.Freeman on 2011-10-20
It works!  I had neglected to click "enable this plugin".  Thanks again.

---

### Post by mcduck on 2011-10-21
No problem!. I hope that serves the purpose at least as well as the magnifier you used to have.

If not, the zoom plugin is highly customizeable. You can read decent explanations about the various settings here: [http://wiki.compiz.org/Plugins/Ezoom]("http://wiki.compiz.org/Plugins/Ezoom")

And one more thing, the [Advanced Settings]("apt:gnome-tweak-tool")-tool for Gnome 3 allows you to set your fonts and font sizes, and also has a slider for text scaling...

---

### Post by PaulInBHC on 2011-10-21
I have a similar mouse. It has a side button for the magnifier. It opens a size adjustable window that you hover over the screen like a magnifying glass. It works from the MS driver and there is no linux version.

---

