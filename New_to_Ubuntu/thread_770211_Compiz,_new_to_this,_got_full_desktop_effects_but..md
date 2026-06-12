---
title: "Compiz, new to this, got full desktop effects but..."
date: 2008-04-27
forum: New to Ubuntu
---

### Post by philinux on 2008-04-27
Synaptic says compiz installed. I'm missing something, spinning cubes etc.

Old pc was never capable of any desktop effects so all new territory.

---

### Post by ripdisk on 2008-04-27
There should be a control panel for all of that stuff somewhere in system>administration, i think it's called advanced desktop settings.

---

### Post by KillerKiwi on 2008-04-27
System -> Preferences -> Appearance 

Then goto the "Visual Effects" tab

---

### Post by LaRoza on 2008-04-27
```

sudo aptitude install compizconfig-settings-manager 

```

It will by in System->Preferences

---

### Post by linux phreak on 2008-04-27
Open synaptic and in search enter compiz.Then select the Advanced compiz settings manager and install it.Then you can configure everything.

---

### Post by ajgreeny on 2008-04-27
To get the full configuration possibilities you need to install *compiz-config-settings-manager*, or something like that.  It was called that in gutsy but I think it may have slightly changed name for hardy.  Search in synaptic and you should find what you need, then go to *System>>Preferences>>Advanced Desktop Effects*, and you can play around with the plugins to your hearts content.

---

### Post by philinux on 2008-04-27
> **LaRoza said:**
> ```

sudo aptitude install compizconfig-settings-manager 

```

It will by in System->Preferences

Everything else was installed bar that. I suppose thats normal.

Wow there's a lot of options. Where do you start?

---

### Post by forestpixie on 2008-04-27
If after all that you don't have the csutom option in appearances to get the cube going you need to install simple-ccsm - a chance read of a thread taught me that, I didn't get anything until I installed that.

```
sudo apt-get install simple-ccsm
```

---

### Post by artir on 2008-04-27
> **philinux said:**
> Everything else was installed bar that. I suppose thats normal.

Wow there's a lot of options. Where do you start?

Welcome to ubuntu !:)

---

### Post by philinux on 2008-04-27
Ok all set, got the desktop cube enabled, no errors.

got 4 desktop rotating cube.

---

### Post by lovecrime on 2008-04-27
I miss the cube too 

there is no cube like the one we saw in google and sites 

just an animation similar to the cube but not the full cube

how to get the full cube

---

### Post by ajgreeny on 2008-04-27
> **lovecrime said:**
> I miss the cube too 

there is no cube like the one we saw in google and sites 

just an animation similar to the cube but not the full cube

how to get the full cube

So what do you get?  If we are to help we need to know where you are at the moment with the cube etc, and what you mean by "an animation".  If you just get a single plain with two sides it is because you don't have the 4 desktop enabled in General settings like the attachment.

---

### Post by starfunker on 2008-04-27
I found this site useful for setting up Compiz fusion effects: [http://forlong.blogage.de/article/2008/4/26/How-to-set-up-Compiz-Fusion-074](http://forlong.blogage.de/article/2008/4/26/How-to-set-up-Compiz-Fusion-074)

---

### Post by linux phreak on 2008-04-27
For enabling 'cube' The desktop cube must be enabled in the CCSM.Along with that cube rotation must also be enabled.Make four workspaces.One can enable desktop cube reflection and cube caps for extra bling.alt+ctrl+leftclick can be used to rotate the cube.

---

### Post by philinux on 2008-04-27
I've got 4 desktops so when i click the second it rotates round. Are there other key shortcuts to flip it?

---

### Post by starfunker on 2008-04-27
hold ctrl and alt down and then press the left or right arrow key.  This will turn the cube too.  If you hold down ctrl and alt and hold your left mouse key you can drag the cube around.

---

### Post by caro on 2008-04-27
> **linux phreak said:**
> For enabling 'cube' The desktop cube must be enabled in the CCSM.Along with that cube rotation must also be enabled.Make four workspaces.One can enable desktop cube reflection and cube caps for extra bling.alt+ctrl+leftclick can be used to rotate the cube.

It took me a couple of hours of searching on my own to find that the other night after I set everything up.  Fortunately, there is a decent wiki and forums at [http://www.compiz-fusion.org/]("http://www.compiz-fusion.org/")

Good luck!

---

