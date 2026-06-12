---
title: "HDMI and VGA output problems"
date: 2013-10-06
forum: New to Ubuntu
---

### Post by drewhamm7292 on 2013-10-06
Ok, so I have two problems here. First, I have an MSI A6000 series laptop that I have connected to my 32 inch Emerson by VGA, although I would rather use HDMI. I'll get to that just a little bit later on down the line. Now with VGA the picture is perfect although I am constantly on two separate workspaces between my monitor and my tv. Now, anytime that I open any of my games, most importantly SuperTux 1 and 2, I can play it perfectly on my television right up until the point I try to maximize the screen. As soon as I try to maximize to go full screen it shows up full screen on my laptop and no matter what I do it will not go to the television monitor so I'm stuck playing in a tiny part of my television screen and I have no idea why. I have even turned the laptop monitor completely off through the display settings and still when I go to full screen it shows up on the laptop.


My second problem is that when I connect by HDMI, whether with my MSI or my Dell 3521 laptop, the overscan is horrible and I am so zoomed in I can only see like 20 percent of the screen. I have went into the display settings and changed the resolution to every single option but still no go. With one of them it gets really close but I'm still missing a good portion off the left and bottom parts of the screen. Any ideas to fix this? It would be greatly appreciated due to the fact that the Dell doesn't have a VGA port at all so at this point in time I cannot even connect it to the TV. Also that is the one that I download all my movies on, so therefore it would be nice to be able to connect straight through to the TV instead of having to burn every single movie I download.


Any help with this would be greatly appreciated,
DrewHamm7292

---

### Post by DuckHook on 2013-10-07
I may not be able to help much, but you really need to provide more info for a fighting chance at attracting help. Please post system details. Need at least details of graphics chip, but more info is better.

1. Post results from both laptops of:```
lspci -vk | grep -1A13 vga
```
2. Tell us CPU, RAM, everything you know about your HW.
3. Did you try to install proprietary drivers?
4. What settings have you already fiddled with?
5. Are you connecting with good HDMI cable or through DVI>HDMI converter?
6. Are you connecting through a receiver or straight into TV? Need all details of setup.

---

### Post by Donut50 on 2013-10-08
have you already tried to find drivers for the outputs in you laptop?

---

