---
title: "Laptop getting really hot"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by Bazirker on 2008-06-12
Hey guys so now that it's summer, my laptop has gone from being warm to being hot and making a ton of noise and it stinks.  It stays a bit cooler (to the touch) in Ubuntu but only because the fan runs like a race horse.  I'm wondering if new thermal paste will help?  (I built my laptop, so new thermal paste is do-able.)  I have an Intel T7600 processr and it kinda has this stuff on the core(s) already but I put thermal paste on it anyway since that stuff didn't look like normal thermal paste.  Should I not have done that?  Anyone have any tips how to get my laptop to run cooler (without amping the fan)?

Help....  :(

---

### Post by Nessa on 2008-06-12
What's the temp reading?

---

### Post by Bazirker on 2008-06-12
I have no idea...how can I find out?  I installed xsensors but it doesn't seem to do anything but open a blank window.

---

### Post by wolfen69 on 2008-06-12
> **Bazirker said:**
> Hey guys so now that it's summer, my laptop has gone from being warm to being hot and making a ton of noise and it stinks.    :(

that would indicate that one of the vents/fans is clogged. the stink comes from dust burning. i could be wrong, but it probably needs a good cleaning.

---

### Post by niteshifter on 2008-06-13
Hi,

Er, that stink could also be printed circuit board roasting....

There are several different types of "heat sink compound" and characteristics vary. I take it you used the common white stuff?

If you've any left from the original kit, I'd tear down, clean up and re-apply with the supplied compound.

If you're stuck with the white stuff, remember a little goes a long way. A very thin layer is all that is needed. To thick a layer works against you. If you know a bit about electrical circuits: heat flow in a object is much like current flow in a circuit - too thick a layer of compound is like increasing the value of a resistor, the voltage drop across the resistor increases. For heat flow this means more heat stays with the source, less is transfered to the radiator.

Or for a non-tech thought experiment / analogy: Imagine placing a bit of alumimum (excellect heat conductor) foil in the palm of your hand and then pointing torch flame at it: immediate sensation of heat. Now replace the foil with a thick plate of alumimum: there will be a delay, but the hot side is hot now and getting hotter by the second. By the time you feel it, that hot side is way, way hot and will stay that way.

Good luck.

---

### Post by wolfen69 on 2008-06-13
nice to meet ya niteshifter.

---

### Post by Bazirker on 2008-06-13
Haha I need to be more careful in my wording...when I said "it stinks", I had originally said "it sucks" but changed it cause I've been trying to clean up my language...it smells fine actually.  My bad!

I reapplied the thermal paste (arctic silver 5) about 2 months ago and did so in a thin layer.  I'm an engineer and understand the basic physics of heat transfer, which is why I wonder about that stuff that came on the CPU.  Whatever it is, it looks sorta grey purple-ish, opaque, and looks like it was coated onto the core and then dried (it doesn't wipe off like thermal paste does).  Here's an image: [http://www.tgdaily.com/picturegalleries/20060801/1_merom_processor.jpg]("http://www.tgdaily.com/picturegalleries/20060801/1_merom_processor.jpg")Should I not have put more thermal paste on top of that?  What is that stuff?  Can I and should I get it off?  I just wanna be able to run Ubuntu without my laptop sounding like an overclocked desktop and behaving like a space heater...

---

### Post by niteshifter on 2008-06-13
Ok, never mind .... as to removing the mystery goop, if it looks it came from the foundry I'd leave it be, figuring that Intel knows what it's doing ;)

---

### Post by RSingh on 2008-06-13
> **Bazirker said:**
> I have no idea...how can I find out?  I installed xsensors but it doesn't seem to do anything but open a blank window.

Try using the sensors applet:
```

sudo aptitude install sensors-applet
```

Right click on panel >> Add to panel >> Sensors applet.

---

### Post by frankos44 on 2008-06-13
My Toshiba was having a heat problem, fan running fast all the time and it even shut itself down on occasions.

After taking it apart the fan look clean and no obvious problem but I removed the fan from the heat sink and inside the aluminium extrusion was a narrow channel and it was completely blocked with dust. Now it runs cool, quite and doesn't shut itself down anymore.

---

### Post by gunashekar on 2008-06-13
my heating laptop problem went away when i updated the bios. apparently the earlier bios had a problem .

---

