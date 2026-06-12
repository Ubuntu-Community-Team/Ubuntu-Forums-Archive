---
title: "[SOLVED] Help with monitor settings"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by rhomany on 2008-06-28
I have a Toshiba Satellite Pro A100-02Y running ubuntu 8.04.So far, so good; just a couple of teething issues with my wireless connection but that's fixed thanks to trawling these forums :)

Now I'm hoping someone can help with my display settings.

The monitor itself works just fine, but I have visual problems that mean I always have to fiddle around with monitor settings because they're too bright (I usually have my CRT set to 40% brightness/50% contrast and sometimes less, to give you an idea of how dark I need it!)

Is there a way to change my monitor settings on a laptop, where there's insufficient manual controls? In Windows Toshiba had its own monitor program that darkened the screen much more than the keyboard options. I have tried using the monitor settings available in unbunto and it just says it doesn't recognise my monitor
[I]
Error: No monitor supporting DDC/CI available. If your graphics card needs it, please check all the required kernel modules are loaded (i2c-dev, and your framebuffer driver.)[/I]
Frankly, that might as well be written in Chinese for all I understood of it. I assume either it's looking for an external monitor or the drivers for the onboard graphics aren't recognised?

Specs for the laptop are:-
[INDENT]Processor: Intel Pentium Dual Core T2080 / 1.73 GHz
Multi-Core Technology: Dual-Core
Data Bus Speed: 533 MHz
Chipset Type: Mobile Intel 943GML Express
Display Type: 15.4" TFT
Max Resolution: 1280 x 800 ( WXGA )
Widescreen Display: Yes
Colour support: 24-bit (16.7 million colours)
Graphics Processor / Vendor: Intel GMA 950
Video Memory: Dynamic Video Memory Technology 3.0
Max Allocated RAM Size: 128 MB[/INDENT]

rhomany@rhomany-laptop:~$ lspci -nn | grep VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)


Anyone able to help a learner please?

---

### Post by rhomany on 2008-07-02
Anyone, please?

---

### Post by silkstone on 2008-07-02
I'm sorry but I suspect there isn't a way to do this. What you need is an equivalent of the nvidia-settings package that works with your on-board Intel graphics processor, and I don't think such a thing exists. I asked a similar question many months ago about Intel on-board graphics on an old desktop PC, and nobody came up with any ideas.

I know it's no help to you, but I have a laptop with an Nvidia Geforce Go 7300 card in it, and that uses the proprietary Nvidia drivers plus nvidia-settings.

My only suggestion would be if you could fit an Nvidia card in your laptop, but I don't know if that is possible.

---

### Post by bijeeshvs on 2008-07-02
> **rhomany said:**
> Anyone, please?

hello pal, i am not so sure, but if compiz is working on ur system there is a brightness and saturation plugin in the compiz setings manager may be it could help.................................

---

### Post by bijeeshvs on 2008-07-02
There is a brightness applet in the panel ( just right click on panel and select "add to panel an then select brightness applet from the list, give it a try)

---

### Post by rhomany on 2008-07-02
Thank you both for your replies, I appreciate it.

> **bijeeshvs said:**
> hello pal, i am not so sure, but if compiz is working on ur system there is a brightness and saturation plugin in the compiz setings manager may be it could help.................................
I've just had a play with that and unfortunately it doesn't appear to be doing anything more than the keyboard settings.

I have Wine installed. I realise it's probably a silly question but could I perhaps install the Toshiba driver for Windows using Wine? I haven't used Wine so I'm not sure of its capabilities.

Thanks again, I really appreciate the help

---

### Post by silkstone on 2008-07-02
I think the problem is that Ubuntu doesn't play nicely with Intel graphics, and therefore I doubt if installing drivers with Wine will help. But I can't be sure of this as it's totally outside my experience.

It would be good if one of the Ubuntu gurus could help here. Apart from installing an Nvidia card, if possible, I'm afraid I can't think of anything else.

---

### Post by rhomany on 2008-07-02
Thanks, unfortunately there's no room for an additional graphics card. I was wondering if reducing the gamma might help. Trawling through the laptops section tells me this is possible but I've yet to find any code that works.

Perhaps I should be asking this in the Laptops section rather than the beginners section. I'll give it another day or so and then try over there. I might get lucky and find someone else who has fixed this issue. :)

---

### Post by silkstone on 2008-07-02
Ah, I'd forgotten about xgamma.

You could try this...

Open the terminal and enter a value like...

```
xgamma -gamma 0.7
```

You can also adjust each RGB channel independently...

```
xgamma -rgamma 0.700 -ggamma 0.800 -bgamma 0.900
```

To apply the settings at startup, write a shellscript:

1. Create a new file in your home folder...

```
gedit init-xgamma.sh
```

2. Type in the xgamma-settings (as above) and save the file.

3. Make the shellscript executable...

```
chmod 755 init-xgamma.sh
```

4. Add init-xgamma.sh to the startup applications...

Go to System > Preferences > Sessions > Startup, and add a new entry. Call it whatever you like (e.g. xgamma startup) and set up the path to your shellscript (/home/Yourusername/init-xgamma.sh).

The xgamma settings should then be applied on startup.

---

### Post by eapache on 2008-07-02
Laptops aren't really my area of expertise, but I just wanted to note that installing the drivers via Wine won't work. Wine programs are kept isolated from the system stuff so that Ubuntu can't be infected by Windows viruses.

---

### Post by rhomany on 2008-07-03
> **silkstone said:**
> Ah, I'd forgotten about xgamma.

<snip>

That is superb. It's exactly what I needed. I've managed to do it manually and later when I've had some caffeine and fully recovered form a day at the office I'll have a go at setting it up on start up.
You're awesome :KS

---

### Post by silkstone on 2008-07-03
If I were awesome I'd have remembered about that sooner! :)

Glad it worked!

---

