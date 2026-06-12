---
title: "Wrong Monitor Detected"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by Anthony M on 2008-07-07
On my new Hardy installation, the screen is outputing the correct resolution but it is for a 16 inch monitor rather than a 17. I know in Gutsy there was a way to choose your monitor. I have already tried to reconfigure xorg. 

How can I choose my 17" Monitor?

Thanks

---

### Post by overdrank on 2008-07-07
> **Anthony M said:**
> On my new Hardy installation, the screen is outputing the correct resolution but it is for a 16 inch monitor rather than a 17. I know in Gutsy there was a way to choose your monitor. I have already tried to reconfigure xorg. 

How can I choose my 17" Monitor?

Thanks

Hi and you can try using the alt, f2 keys and enter ```
gksu displayconfig-gtk
```

---

### Post by mcduck on 2008-07-07
> **Anthony M said:**
> On my new Hardy installation, the screen is outputing the correct resolution but it is for a 16 inch monitor rather than a 17. I know in Gutsy there was a way to choose your monitor. I have already tried to reconfigure xorg. 

How can I choose my 17" Monitor?

Thanks

What do you mean? So you have 2 monitors connected and Ubuntu is using the wrong one? Or that you have one 17" monitor, the resolution is correct ut picture doesn't fill the whole screen?

In the first case try overdrank's suggestion, or if you have Ati or nVidia graphics card get install the correct configuration tool for it and use that to configure your displays.

In te second case use the adjustment buttons on yourr monitor to fit the image on the screen. Disply resolution has nothing to do with monitor size, 1024x768 is 1024x768 regardless of if the display is 10" or 60"..

---

### Post by Anthony M on 2008-07-07
> **mcduck said:**
> What do you mean? So you have 2 monitors connected and Ubuntu is using the wrong one? Or that you have one 17" monitor, the resolution is correct ut picture doesn't fill the whole screen?

In the first case try overdrank's suggestion, or if you have Ati or nVidia graphics card get install the correct configuration tool for it and use that to configure your displays.

In te second case use the adjustment buttons on yourr monitor to fit the image on the screen. Disply resolution has nothing to do with monitor size, 1024x768 is 1024x768 regardless of if the display is 10" or 60"..


Yes I have one 17" Dell monitor that the picture does not fill the whole screen. In the Resolution Settings box, it indicates that my monitor is a "16 inch Dell", which is not correct.

- overdrank- I will try that when I get home tonight!

- mcduck- Yea, I could adjust the monitor, but this is a dual-boot machine, and I do not want to have to readjust the monitor every time I switch OSs.

Besides, I am installing on a 17" monitor, there is no reason Ubuntu shouldn't be able to correctly detect that...

Thanks!

---

### Post by mcduck on 2008-07-07
It shouldn't make any difference how the system recognizes the display, or if it recognizes it at all (On most of my machines the display is just listed as "Generic Monitor", and the name can actually be changed to anything you ant in xorg.conf). The same things should apply even if there was no monitor connected at all.The resolution is the same and that's the only thing that counts.. 

..besides the refresh rate.. Are you sure you are using the same refresh rate with both operating systems? You'd better check that..

If the resolution and refresh rates are the same the picture should be more or less the same size and in same position.

Operating systems and graphics adapters don't care what size your display is or if there's any display at all. They only care about outputting the right resolution with right refresh rate to the display output port.

(Well, you can configure the right dpi setting for your monitor, but that only affects in smaller details like font rendering, and certainly doesn't affect the size of the picture you see on your monitor.)

---

### Post by Anthony M on 2008-07-08
Bump

Any other Ideas??

Thanks!

---

### Post by darkwar on 2009-05-15
So, 1 year have passed... nobody fixed this?

My problem is the same 17inch recognized as 16

---

### Post by wpshooter on 2009-05-15
When you are doing your Ubuntu O/S installation are you installing from the live CD version or the ALTERNATE (text based) CD version.  If you are installing from the live version, I would try the ALTERNATE instead.

---

### Post by catzlai on 2009-08-16
Everything on my laptop was fine until this morning.
Ubuntu suddenly think my monitor is 13" when it is 15".
I didn't do anything installation nor any administrative operation.
What can I do about...?

---

