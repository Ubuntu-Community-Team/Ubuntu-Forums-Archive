---
title: "PSX (1/2/3) Controller Emulation"
date: 2008-02-07
forum: Programming Talk
---

### Post by lansirill on 2008-02-07
I was leveling in Oblivion when I thought that it would be awfully nice if I could just automate mashing the 'X' button. I've searched Google a bit to see if anyone had already done the work to let me use my laptop , or pick your computer size of choice, as a controller for the PS3. Unfortunately all I've been able to find has been information on using the actual controller on Linux, rather than the other way round. So, unless I missed something (and I would love to have missed something) it looks like I may have  found a project for myself.

I've researched the controller signals well enough to feel comfortable at least -attempting- this project, even if I might not be able to pull it off. I'd like to start by learning how to communicate with the controller and then reverse the process. Unfortunately, while the logic for how the two should communicate is pretty simple, I haven't a clue how to actually read and write signals between the computer and controller.

The vast majority of my programming experience is mathematical, so this is definitely stretching my abilities. I suppose what I'm really trying to find out is where should I start if I want to learn how to work with hardware at this level? My best guess at this point is to dig up the source for the PS3 controller driver, but I suspect that may be a little overwhelming at first. Baby steps and all that good stuff.

---

### Post by Andrew Stone on 2008-02-09
If I were you, I'd keep it as simple as possible by letting the existing hardware do most of the work.  Buy a used controller (I've seen them for 8 bucks) and take it apart.  When you do, you'll probably see that what depressing each button does is simply make a connection between 2 wires on the circuit board (I have taken apart many similar devices but not a PSX controller.  

Next buy a USB to digital IO board like this:
[http://www.delcom-eng.com/productdetails.asp?productnum=802004](http://www.delcom-eng.com/productdetails.asp?productnum=802004)

Wire the IOs on the board to make or break connections on the controller.  There are a variety of ways to do this, from mechanical to electrical.  One way to do it would be to feed the IO into the base of a transistor, and the emitter and collector across the switch on the controller.  So when current is applied to the base, current is allowed to flow across EC gap -- i.e the button is pressed.

---

