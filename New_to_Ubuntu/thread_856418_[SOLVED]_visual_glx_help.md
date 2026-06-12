---
title: "[SOLVED] visual glx? help"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by phantomjoker on 2008-07-11
What does it mean if this happens in terminal

> doc@ubuntu:~$ glxinfo | grep "render"
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

I cant play ppRacer and was told to use this code - trivial but related...

What does it mean? what do I do... when I go to play the game this comes up in the terminal

> PPRacer 0.3.1 -- [http://racer.planetpenguin.de](http://racer.planetpenguin.de)
(c) 2004-2005 The PPRacer team
(c) 1999-2001 Jasmin F. Patry<jfpatry@sunspirestudios.com>
PPRacer comes with ABSOLUTELY NO WARRANTY. This is free software,
and you are welcome to redistribute it under certain conditions.
See [http://www.gnu.org/copyleft/gpl.html](http://www.gnu.org/copyleft/gpl.html) for details.

*** ppracer error: Couldn't initialize video: Couldn't find matching GLX visual (Resource temporarily unavailable)

whats going on?

thanks

---

### Post by nowshining on 2008-07-11
A:) are u using a ATI or Nvidia driver?
if A = yes then B) did u install the restricted Drivers?

---

### Post by mcduck on 2008-07-11
The person who told you to run was probably waiting that you'd post the result to the thread where you asked for help in the first place..

It's quite hard to help if you make new threads all the time instead of posting back to the original thread..

(anyway,I he wanted you to run that command because it tells if your graphics drivers are working correctly or not. Based don the output,, they aren't.. And that's the reason why tou can't run the game)

---

### Post by phantomjoker on 2008-07-11
Thats all very well but as this forum states - i am an *absolute beginner*.. so where do I go from here? advice _rather than_ criticism maybe?

thanks :)

---

### Post by neurostu on 2008-07-11
No one is trying to critisize you, and you're right these forums are for * Absolute Beginners*.  

All of the responses were actually quite helpful, in as much as they could be,  what we really need to help you solve your problem is to know more about the problem.

When you go to the doctor and say my arm hurts that doesn't help much. We like the doctors will be able to better help you the more information we have.

Can you please explain the entire problem and we will do our best to help and teach you.

---

### Post by phantomjoker on 2008-07-11
Well thank you for your kind words -

Ok, if trying to run particular games (not my biggest issue but relevant) through the terminal I will get the following message

> doc@ubuntu:~$ ppracer
PPRacer 0.3.1 --  [http://racer.planetpenguin.de](http://racer.planetpenguin.de) 
(c) 2004-2005 The PPRacer team
(c) 1999-2001 Jasmin F. Patry<jfpatry@sunspirestudios.com>
PPRacer comes with ABSOLUTELY NO WARRANTY. This is free software,
and you are welcome to redistribute it under certain conditions.
See [http://www.gnu.org/copyleft/gpl.html](http://www.gnu.org/copyleft/gpl.html) for details.

*** ppracer error: Couldn't initialize video: Couldn't find matching GLX visual (Resource temporarily unavailable)


I have looked for GLX packages and downloads in the Synaptic package manager but nothing appears. Also if I attempt to change the visual effects in the appearance to any setting other than 'None' I get the message - 

> Desktop effects could not be enabled

I have also tried to enter the following command as told to - expecting to be told about my graphics details but instead got

> doc@ubuntu:~$ glxinfo | grep "render"
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0". 

When I set up Ubuntu and started using it - 3 days ago - a friend gave me lots of packages to download - one of which was graphics - after this I have not been able to change the visualizations... I don't know whether this is related - but I could change the visualizations before.

I would ask him seeming as he seems to know what he's talking about and could tell me what package it was I downloaded - but he is unfortunately not reachable at present. I think the package was called

> nvidia-glx-new

this is just about all I can say on the topic.

thanks for all your comments!

---

### Post by neurostu on 2008-07-11
so it looks like you're having problems enabling desktop effects, is that right?

Do you have an nvidia video card? If you don't then you should remove nvidia-glx-new.

You should also start a new thread explaining that you can't enable desktop effects.

To get the right video card drivers downloaded and installed click on System-->Administration-->Hardware Drivers, if you have a video card listed there, make sure you have it check to install and use the restricted driver, if that driver is Nvidia-glx-new then don't uninstall it.


good luck!

---

### Post by eaterjolly on 2010-05-02
> **neurostu said:**
> so it looks like you're having problems enabling desktop effects, is that right?

Do you have an nvidia video card? If you don't then you should remove nvidia-glx-new.

You should also start a new thread explaining that you can't enable desktop effects.

To get the right video card drivers downloaded and installed click on System-->Administration-->Hardware Drivers, if you have a video card listed there, make sure you have it check to install and use the restricted driver, if that driver is Nvidia-glx-new then don't uninstall it.


good luck!
i have mint kde and i have the same problem he has with world of goo demo. i get this when i check the logs ```
sudo bash /home/eaterjolly/.WorldOfGoo/WorldOfGoo.log
/home/eaterjolly/.WorldOfGoo/WorldOfGoo.log: line 1: [t=0.00]: command not found
/home/eaterjolly/.WorldOfGoo/WorldOfGoo.log: line 6: syntax error near unexpected token `('
/home/eaterjolly/.WorldOfGoo/WorldOfGoo.log: line 6: `[t=0.00] SDL_SetVideoMode(1280, 800, 0, 2684354562) failed: Couldn't find matching GLX visual'

```i checked synaptic and i have nvidia-glx-185 even though my graphics card is Intel mobile graphics media accelerator X3100

---

