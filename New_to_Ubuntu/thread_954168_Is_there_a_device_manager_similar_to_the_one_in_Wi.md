---
title: "Is there a device manager similar to the one in Windows in Ubuntu?"
date: 2008-10-20
forum: New to Ubuntu
---

### Post by psyoptic on 2008-10-20
Just curious to know if there's something like Windows' device manager in Ubuntu. Not sure if I have all my proper drivers installed, so something like that would help out.

---

### Post by fooman on 2008-10-20
there is a gnome device manager available in synaptic, or in a terminal:

```
sudo apt-get install gnome-device-manager 
```

after it installs,  find it in applications > system tools

...not sure how similar it is to the windows version though.

---

### Post by ArdentMoth on 2008-10-20
that's useful; just too bad it can't help find the drivers i need (and install them).

---

### Post by ardvark71 on 2008-10-20
> **ArdentMoth said:**
> that's useful; just too bad it can't help find the drivers i need (and install them).

Hi...

What devices do you need drivers for?

Best Regards...

---

### Post by ArdentMoth on 2008-10-20
well, let's see... It's an Acer Aspire 5610.

1 and 2) Intel Core 2 Duo T2050 with GMA950 on-board graphics.  I have no 3D acceleration for some reason, OpenGL is apparently disabled, and so on.

3) my MMC SD flash reader. Nothing happens when a stick gets inserted.

Meanwhile, there's the question of the programmable buttons (email, internet, P, e, rewind, fast forward, play/pause, vol-, vol+) and bluetooth which simply don't work.


I could be wrong about it being drivers,  but at the moment I can't imagine what else it might be.

---

### Post by starcannon on 2008-10-20
I use lshw, the command to create a nice html list of all the hardware on your machine would be:
```
sudo lshw -html > hardwareList.html
```

Open your home folder and you'll see a file named "hadwareList.html" open it with Firefox, and then start working on installing drivers; most people will only need to deal with Video and or WiFi drivers, occasionally sound drivers.

GL

---

### Post by ArdentMoth on 2008-10-20
also a very useful tool; perhaps it's not drivers though, they all seem to be correct... I guess i'll throw my info up on a new thread and see what everyone thinks. I'm a little bit at a loss, I'm sure it's simpler than I'm making it.  Thanks.

/threadjack

---

### Post by psyoptic on 2008-10-21
Threadjack away. I'm just glad that I was able to pick up some more useful info about using Terminal. Thanks again starcannon.

---

### Post by SabreWolfy on 2008-10-21
> **ArdentMoth said:**
> well, let's see... It's an Acer Aspire 5610.

1 and 2) Intel Core 2 Duo T2050 with GMA950 on-board graphics.  I have no 3D acceleration for some reason, OpenGL is apparently disabled, and so on.

3) my MMC SD flash reader. Nothing happens when a stick gets inserted.

Meanwhile, there's the question of the programmable buttons (email, internet, P, e, rewind, fast forward, play/pause, vol-, vol+) and bluetooth which simply don't work.


I could be wrong about it being drivers,  but at the moment I can't imagine what else it might be.

I have an Acer Aspire 4710 laptop with Ubuntu 8.04. Graphics chipset is not the same as yours, but Compiz, etc. works fine "out of the box". The only driver I needed was a restricted one for wireless, but this installed easily via the restricted hardware dialog after updating my packages. AFAIK Intel provides drivers for their graphics controllers, so you should be able to get that working. I have a built-in card-reader as well, which just worked with the SD card which I inserted -- a cool little card icon appeared on the desktop when it automounted. Some of the special buttons work (internet, email, mute, play/pause, stop, screen brightness), but some don't (wireless, bluetooth (?), rewind, fast forward).

---

### Post by seshomaru samma on 2008-10-21
Sorry I can't help you with your problems but I suggest several things:
Run a search on this forum for similar hardware, for example put GMA950 in the search box on the top right corner and check the resulting threads
Run a Google search for (as an example), "GMA950 , Ubuntu, Driver" or " GMA950 , Hardy, Driver" 
Finally if you can't find a solution, start new threads for each problem using a descriptive title like "Help me find a driver for GMA950 on Hardy" , "Help me get special buttons work on Acer Aspire 4710"

---

### Post by ardvark71 on 2008-10-21
Hi...

I've attempted some research on the GMA 950 and if I understand correctly, there aren't any specific Intel drivers for this chipset, at least for now. Here are a couple links for answers and a workaround...

[http://forum.freespire.org/archive/index.php/t-11111.html](http://forum.freespire.org/archive/index.php/t-11111.html)

[http://ubuntuforums.org/showthread.php?t=220410](http://ubuntuforums.org/showthread.php?t=220410)

If anyone has updated information on this, it would be most welcome! :)

I'll see if I can help you tackle the flash reader tommorrow...(yaaaawnnn, where's the sleeping smiley at?)

Best Regards...

---

### Post by ardvark71 on 2008-10-22
Hi...

What is the chipset "make and model," including number, for your flash reader?

Best Regards...

---

