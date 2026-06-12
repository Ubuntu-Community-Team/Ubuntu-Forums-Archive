---
title: "Insignia TV"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by crazyclown on 2008-04-27
I have a 37" Insignia television and I am trying to hookup 8.04 that I just loaded to it.  I have plugged in my Windows laptop and it works fine.  I can even press CTRL+ALT+F1 and get to a terminal fine.  I loaded the install from the box.  

So how do I get it display kde?

---

### Post by crazyclown on 2008-04-27
I have decided to just connect my 15" flat panel.   I will work on connecting the 37" later.

---

### Post by chip616 on 2009-08-19
I have an Insignia 42" that should have the same electronics as yours.  I have mine connected using Kubuntu 8.04, but there is some weirdness.

Maybe we can compare notes?

Frank.

---

### Post by aaronbartell on 2009-10-05
I have a 37" Insignia hooked up to my DVI on my monitor card (i.e. DVI to HDMI conversion cable required) and it is working relatively fine.  I must say the fonts and images aren't as good as my 23" Samsung.  I think a higher resolution would help that out.  Note I am using Ubuntu 9.04.

What problems specifically are you having?

Aaron Bartell
[http://mowyourlawn.com](http://mowyourlawn.com)

---

### Post by chip616 on 2009-10-05
Aaron:

I am unable to get a proper-sized image on the screen over the digital connection.  My video card will do 1920 x 1080 (MSI MX8400GS), but the image is too large for the display - much like it was stretched somehow.  All 4 borders of the image are beyond the edge of the physical screen area, and I'm unable to 'pan' it as the display and the video card both think that the image fits.

I've also had difficulties with boot up.  On the digital interface, a lot of the normal boot-up information does not appear on the display.  I just get a message on the screen 'not supported'.  I had to set up my machine with an old VGA monitor, THEN connect it to the TV.

A lot of this has to do with video modes that my card/TV monitor do not have in common.  It has been a while since I originally posted this, however, and I don't remember anymore the exact details.

At the moment, I have it running at about 7/8 of full screen doing 1450 x somethingorother using the VGA connection.  As expected, the display is  not as crisp as it should be, but it works.

I hope to get a newer machine with a much more powerful nVidia video card later this year, but I'll probably wait now until 10.04 comes out.  I prefer to run only the LTS releases as they tend to be more stable.

Frank.

---

### Post by LewRockwell on 2009-10-05
we've pumped stuff into a 42 inch plasma but it looked pretty shabby

.

---

### Post by aaronbartell on 2009-10-05
> **chip616 said:**
> I am unable to get a proper-sized image on the screen over the digital connection.  My video card will do 1920 x 1080 (MSI MX8400GS), but the image is too large for the display - much like it was stretched somehow. 

When I bring up System->Preferences->Display it asks me to use my video cards config vs. Ubuntu.  I seem to remember having a similar issue to yours initially so that is why I brought up the previous sentence.

Config:
Ubuntu 9.04
GeForce 6200 TurboCache, NVIDIA Driver Version: 180.44

Also note, for the archives, that selecting the right settings on your Insignia LCD will make a BIG difference on how "block-y" things look.  I had to go to MENU->Picture->Mode and create a custom entry.  A lot of it had to do with the contrast I believe.

Aaron Bartell
[http://mowyourlawn.com](http://mowyourlawn.com)

---

