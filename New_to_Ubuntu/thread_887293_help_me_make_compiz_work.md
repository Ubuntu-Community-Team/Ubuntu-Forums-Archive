---
title: "help me make compiz work"
date: 2008-08-12
forum: New to Ubuntu
---

### Post by the wombat on 2008-08-12
i have looked all over the forums and i have gotten as far as i can, i have downloaded and installed compiz, the only problem is... i cant select the "extra" button in visual effects.this always pops its ugly head (second thubmnail) now i did the compiz-check thing and this is wat i got... (first thubmnail) so i need help, ive been running hardy for about a good two months now, so im kinda getting my unix legs so to speak, but i still need help, any suggestions? machine specs are: compaq evo w6000 workstation, nvidia video card( no product # or anything) and yea, any help will be greatly appreciated, pretty sure im gonna look dumb, but i really want those desktop effects enabled! thanks :-D ps if pics dont show up, they are attached

---

### Post by Crafty Kisses on 2008-08-12
Post the following output:
```
glxinfo
```

---

### Post by Lord Xeb on 2008-08-12
Go to the Synaptic manager: System>Administration>Synaptic 

Type in compiz and install everything with the ubuntu symbol next to it. Now you will have the "extra" there.

---

### Post by Crafty Kisses on 2008-08-12
It sounds like you have a onboard video card, I know a lot of times it says "Desktop Effects could not be enabled" when you have onboard for some reason, can you give us your specs?

If you do, then see if you can install drivers for it, but I'm almost positive that's what the issue is.

---

### Post by Ryadt on 2008-08-12
Enable your video card in System > Administration > Hardware Drivers.

---

### Post by the wombat on 2008-08-12
well i did everything you guys told me to, and loading the sunaptic stuff almost worked, i think. but it told me to restart my computer and i am right where i was before. as far as specs go: 
processor: Intel Pentium III Xeon 2 GH
speed:   	 2 GHz 
1 gb of ram
160 gb hardrive
and the video card.... it says nvidia, but a fan is covering where the model number should be, and i searched this around the web, and apparently lots of people have no idea wat this is either, the ./compiz-check thing says my NV-CONTROL is too old, 1.6 and it needs 1.11 could that make any difference? the nvidia accelerated graphics driver (legacy cards) is in use so i have no idea wat to do anymore! :confused:

---

