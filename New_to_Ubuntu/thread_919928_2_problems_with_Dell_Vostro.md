---
title: "2 problems with Dell Vostro"
date: 2008-09-14
forum: New to Ubuntu
---

### Post by shivkrish22 on 2008-09-14
Hi
I have Ubuntu 8.04 installed on my dell vostro 1500 (2Gb, Nvidia 8400GS).
I have a couple of nagging problems with it.

1. The screen brigtness control is extremely sensitive. It changes by 2 or 3 levels when i try to reduce or increase it a single step. How can i configure it to be less sensitive to the key input?

2. I have Gkrellm installed with the dell i8k fan control plugin. I had ubuntu 7.1 installed before i upgraded to 8.04 and had installed the plugin initially. I am not sure if it is still required. Can i remove gkrellm and the i8k plugin without causing any overheating issues? if it is required is there any way to run gkrellm as a process in the system tray? right now it runs as a normal window with a tab in the taskbar. 

Thanks.

---

### Post by adult swim on 2008-09-14
1. not sure
2. i use grkellm with hardy as well.  my fans will work without it but they dont kick on until around 62C which is way to hot.  an easy fix to run gkrellm and not have it clutter up the taskbar is to right click it in the task bar and move it to another workspace.  then switch back to the orginal workspace and it should be off the bar.

---

### Post by shivkrish22 on 2008-09-14
i tried switching gkrellm to a different workspace but it still keeps showing up(some config file messed up?). its not that important to have it hidden, just one of those small things that you cant help but keep noticing. :P 
Thanks for the reply though.

---

### Post by adult swim on 2008-09-14
i just saw in the gkrellm configuration, right click on grkellm to pop it up, on general and the properties tab there is an option to not show it in the taskbar, its towards the bottom.

---

### Post by shivkrish22 on 2008-09-14
yes.. i checked that. but now how do i access the window if i need to? it doesnt even come up if i run it through the terminal and i minimized the existing window. so now even though it is running i cant access it!

---

### Post by adult swim on 2008-09-14
hmm a way to fix that would be to go to the terminal and type in ```
killall grkellm
```  now when you restart it, it will be maxmized.  if you have set temperatures for when  your fan should come on, minimizing it and it not showing up shouldnt be a problem.  it will be running in the background controlling your temps.

---

### Post by shivkrish22 on 2008-09-14
thanks. 
I am still struggling with the screen brightness control problem though.

---

### Post by jago25_98 on 2008-10-30
I don't understand the brightness problem. I have a Vostro1500, Heron and the Fn+brightness keys go in ok increments. hmm... check bios brightness settings see if that effects it, just a check. Then you might also fiddle to see what happens in a fullscreen GL program, or in X11 without dri/acceleration to pin point a problem.

Another thing, what about trying to adjust brightness through software as a test? Possibly more than one way to do it; though gnome, or though X11 and some sort of front-end program to do it.

That's all the ideas I got now

---

### Post by jago25_98 on 2008-10-30
I don't understand the brightness problem. I have a Vostro1500, Heron and the Fn+brightness keys go in ok increments. hmm... check bios brightness settings see if that effects it, just a check. Then you might also fiddle to see what happens in a fullscreen GL program, or in X11 without dri/acceleration to pin point a problem.

Another thing, what about trying to adjust brightness through software as a test? Possibly more than one way to do it; though gnome, or though X11 and some sort of front-end program to do it.

That's all the ideas I got now

---

### Post by TDK800 on 2009-04-05
have the opposite problem - the fan is _always_ working at maximum speed under ubuntu on dell vostro 1510...  is grkellm the app for setting fan speed and does it come default with Ubuntu? the fan rarely works under windows yet the notebook stays normal temperature.

---

