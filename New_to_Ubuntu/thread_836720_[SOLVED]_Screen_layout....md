---
title: "[SOLVED] Screen layout..."
date: 2008-06-21
forum: New to Ubuntu
---

### Post by dunbrokin on 2008-06-21
I have installed Ubuntu on my laptop. My laptop is attached to an external screen. Whatever I do I cannot seem to get the Ubuntu screen to cover the whole screen....I can drag and drop outside of the Ubuntu screen and that allows the use of the full screen....but why does the Ubuntu screen not cover the full screen and how can I get it to do so...

---

### Post by HalPomeranz on 2008-06-22
Could you please run "xrandr -q" on your machine and post the output?

Also, how would you like the two screens to work?  Do you want the laptop to just mirror what's on the external monitor or do you want them to act as separate screens?  Or would you prefer to disable the laptop display and just work on the external monitor?

---

### Post by dunbrokin on 2008-06-22
> **HalPomeranz said:**
> Could you please run "xrandr -q" on your machine and post the output?

Also, how would you like the two screens to work?  Do you want the laptop to just mirror what's on the external monitor or do you want them to act as separate screens?  Or would you prefer to disable the laptop display and just work on the external monitor?

Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 1280 x 1200
VGA-0 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 376mm x 301mm
   1280x1024      60.0*+   75.0     59.9  
   1152x864       74.8  
   1024x768       75.1     60.0  
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1  
DVI-0 disconnected (normal left inverted right x axis y axis)
LVDS connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0*+   60.0  
   800x600        60.3  
   640x480        59.9  
S-video disconnected (normal left inverted right x axis y axis)

Disable laptop and just work on Monitor would be good, thanks.

---

### Post by HalPomeranz on 2008-06-22
To disable the laptop display and just work on the monitor:

```

xrandr --output LVDS --off --output VGA --auto

```

That should also tell your X server to take advantage of the entire 1280x1024 external display.

---

### Post by dunbrokin on 2008-06-23
> **HalPomeranz said:**
> To disable the laptop display and just work on the monitor:

```

xrandr --output LVDS --off --output VGA --auto

```

That should also tell your X server to take advantage of the entire 1280x1024 external display.

Thanks for that....how should I set up a script that does this automatically when I log on and detects the vga?

---

### Post by HalPomeranz on 2008-06-23
> **dunbrokin said:**
> Thanks for that....how should I set up a script that does this automatically when I log on and detects the vga?

Create a shell script like:

```

#!/bin/bash

if [ "xrandr -q | egrep 'VGA.* connected'" ]; then
        xrandr --output LVDS --off --output VGA --auto
fi

```

Then add the script to your startup programs via System->Preferences->Sessions.

---

### Post by dunbrokin on 2008-06-23
> **HalPomeranz said:**
> Create a shell script like:

```

#!/bin/bash

if [ "xrandr -q | egrep 'VGA.* connected'" ]; then
        xrandr --output LVDS --off --output VGA --auto
fi

```

Then add the script to your startup programs via System->Preferences->Sessions.

Man, you are a real maestro at this stuff.....thanks again.

---

### Post by dunbrokin on 2008-08-25
> **HalPomeranz said:**
> Create a shell script like:

```

#!/bin/bash

if [ "xrandr -q | egrep 'VGA.* connected'" ]; then
        xrandr --output LVDS --off --output VGA --auto
fi

```

Then add the script to your startup programs via System->Preferences->Sessions.

I seem to have hit a bit of a problem on this one....it works perfectly for my large screen...however, today was the day when I wanted to take the PC out to give a Rotary talk...but when I powered it on, the PC screen remained blank....i.e. the detection did not seem to work...as in it did not detect that the big screen was not attached and so it remained blank on the PC. By deselecting the script at start up, I was able to get it to work....but I will have to remember to do that each time before I power down from the big screen....how do I change it so that it will detect if the big screen is not attached and then just use the normal PC screen? Thanks for your help.

---

### Post by HalPomeranz on 2008-08-26
I'm sorry, I left out a critical component of the script.  Here's the correct version:

```

#!/bin/bash

if [ "$(xrandr -q | egrep 'VGA.* connected')" ]; then
        xrandr --output LVDS --off --output VGA --auto
fi

```

The "$(...)" that I added in the version above actually causes the script to execute "xrandr -q | egrep 'VGA.* connected'" and then the "if" statement can evaluate whether that command line returned any output.  The earlier incorrect version was just testing to see if the string "xrandr -q | egrep 'VGA.* connected'" was non-null, which of course it always was.

Anyway, sorry for the error.  Hope it didn't cause you too much consternation for your talk.

---

### Post by dunbrokin on 2008-08-26
> **HalPomeranz said:**
> I'm sorry, I left out a critical component of the script.  Here's the correct version:

```

#!/bin/bash

if [ "$(xrandr -q | egrep 'VGA.* connected')" ]; then
        xrandr --output LVDS --off --output VGA --auto
fi

```

The "$(...)" that I added in the version above actually causes the script to execute "xrandr -q | egrep 'VGA.* connected'" and then the "if" statement can evaluate whether that command line returned any output.  The earlier incorrect version was just testing to see if the string "xrandr -q | egrep 'VGA.* connected'" was non-null, which of course it always was.

Anyway, sorry for the error.  Hope it didn't cause you too much consternation for your talk.

Cool...thanks.

---

