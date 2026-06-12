---
title: "open office presentation script"
date: 2011-01-12
forum: Programming Talk
---

### Post by amcnm on 2011-01-12
Hi,

I need a simple script to run an open office presentation at pc startup, but open office has a nice bug that gives a black screen in stead of running the presentation. All i need to do is give it time to load and then press the space bar key to get passed the black screen and start the actual slide show. Something like:

#!/bin/bash
openoffice.org -norestore -show /home/bla-bla/etc.odp && sleep 20 && (add space bar action here :D)

Can anyone help ?
TY !

---

### Post by sanderd17 on 2011-01-12
You can use xdotool (in the repos) to simulate key presses and clicks. Or, if the presenatation doesn't use animation inside the slides (no videos ...) you can export it to pdf and use impressive which is build for such purposes.

---

### Post by amcnm on 2011-01-13
So bash has no key press features ? 
Impression seems to lack that "eye candy" feature compared to oo. The images from the exported pdf look bad and impressive needs tweaks to get it running in the first place. 

impressive -A 4:3 -w -a 20 -g 800x600 /home/bla-bla/etc.pdf 
=>

Welcome to Impressive version 0.10.2
/usr/bin/impressive:94: DeprecationWarning: the md5 module is deprecated; use hashlib instead
  import random, getopt, os, types, re, codecs, tempfile, glob, StringIO, md5, re
OpenGL renderer: Mesa DRI ProSavageDDR 20061110 x86/MMX/SSE2
Using conventional power-of-two textures with padding.
I'm sorry, but your graphics card is not capable of rendering presentations
in this resolution. Either the texture memory is exhausted, or there is no
support for large textures (1024x1024). Please try to run Impressive in a
smaller resolution using the -g command-line option.

xrandr
Screen 0: minimum 320 x 240, current 800 x 600, maximum 1280 x 1024
default connected 800x600+0+0 0mm x 0mm
   1280x1024      75.0     60.0  
   1280x960       60.0  
   1024x768       75.0     70.0     60.0  
   800x600        75.0     72.0     60.0*    56.0     65.0  
   640x480        75.0     73.0     67.0     60.0  
   512x384        75.0     70.0     60.0  
   400x300        75.0     72.0     60.0     56.0  
   320x240        75.0     73.0     60.0  

synaptic has no hashlib package

xdotool is crap to install. i don't even want to waste time with it. maybe when they make it more user friendly (no secret in the fact that i am a noob in linux and programming). i really miss autohotkey...

---

### Post by sanderd17 on 2011-01-13
> **amcnm said:**
> So bash has no key press features ? 
Impression seems to lack that "eye candy" feature compared to oo. The images from the exported pdf look bad and impressive needs tweaks to get it running in the first place. 

impressive -A 4:3 -w -a 20 -g 800x600 /home/bla-bla/etc.pdf 
=>

Welcome to Impressive version 0.10.2
/usr/bin/impressive:94: DeprecationWarning: the md5 module is deprecated; use hashlib instead
  import random, getopt, os, types, re, codecs, tempfile, glob, StringIO, md5, re
OpenGL renderer: Mesa DRI ProSavageDDR 20061110 x86/MMX/SSE2
Using conventional power-of-two textures with padding.
I'm sorry, but your graphics card is not capable of rendering presentations
in this resolution. Either the texture memory is exhausted, or there is no
support for large textures (1024x1024). Please try to run Impressive in a
smaller resolution using the -g command-line option.

xrandr
Screen 0: minimum 320 x 240, current 800 x 600, maximum 1280 x 1024
default connected 800x600+0+0 0mm x 0mm
   1280x1024      75.0     60.0  
   1280x960       60.0  
   1024x768       75.0     70.0     60.0  
   800x600        75.0     72.0     60.0*    56.0     65.0  
   640x480        75.0     73.0     67.0     60.0  
   512x384        75.0     70.0     60.0  
   400x300        75.0     72.0     60.0     56.0  
   320x240        75.0     73.0     60.0  

synaptic has no hashlib package

xdotool is crap to install. i don't even want to waste time with it. maybe when they make it more user friendly (no secret in the fact that i am a noob in linux and programming). i really miss autohotkey...

In what way is xdotool difficult?
install it with 
```

sudo apt-get install xdotool

```

and to send a space key to the active window, use the command 
```

xdotool key space

```

---

### Post by amcnm on 2011-01-14
It seems you saved me :D Thank you very much ! 

I take back what i said about xdotool, i was mislead by [http://groups.google.com/group/xdotool-users/browse_thread/thread/b9d68b25765a9310?pli=1](http://groups.google.com/group/xdotool-users/browse_thread/thread/b9d68b25765a9310?pli=1) :( Xdotool really did the job.

One more question remains, but it's not a matter of life or death: is there any way to set open presentation to "always on top mode" from cli ? Some thing like: 

openoffice.org -norestore -show -"always_on_top"/home/bla-bla/etc.odp && sleep 60 && xdotool key space

---

### Post by sanderd17 on 2011-01-14
I don't know that. Maybe a dirty way is to set a shortcut key to let your window stay on top and emulate it with xdotool. I think there has to be a native way for this, but I don't know it.

---

