---
title: "Resolution problems"
date: 2008-09-06
forum: New to Ubuntu
---

### Post by Shrimply on 2008-09-06
Hi all completely new Ubuntu user here, and beginning to wish I wasn't one.

I just fixed up an old computer and installed 8.04 on it.  I wasn't really happy from the off as it won't detect my wireless network so I'm having to connect through my Vista laptop.

I installed a nvidia graphics card as I was informed that they were the best bet for using with linux.

The resolution was fine, either 800x600 or 1024x768 works fine but then I installed the restricted graphics card driver.  Now I'm stuck with 640x480 or 320x240 I've installed the nvidia settings but those are the only two option I'm able to use. 

The screen is almost unusable at this size.

Would be very grateful of any help you can offer me.

---

### Post by Absolute4Zero on 2008-09-06
Did you try going into system-preferences-screen resolution ?

If you can go there, and it should tell you your current size and also give you options to chnage to other resolutions such as: 1280x1240

---

### Post by Shrimply on 2008-09-06
thanks, it offers the same two resolutions, 640x480 and 320x240

---

### Post by Absolute4Zero on 2008-09-06
In this case you should either reinstall Ubuntu or remove restricted graphic card

(in other words u screwed buddy)

---

### Post by fatality_uk on 2008-09-06
This may not be the case. We need more details.
What type of graphics card is it? 6800gt, 7900gt etc?

---

### Post by Shrimply on 2008-09-06
Thanks, its this one here

[http://www.msicomputer.com/product/p_spec.asp?model=FX5200-TD128LF&class=vga]("http://www.msicomputer.com/product/p_spec.asp?model=FX5200-TD128LF&class=vga")

---

### Post by fourthofjuly on 2008-09-06
> **Shrimply said:**
> Thanks, its this one here

[http://www.msicomputer.com/product/p_spec.asp?model=FX5200-TD128LF&class=vga]("http://www.msicomputer.com/product/p_spec.asp?model=FX5200-TD128LF&class=vga")
hi,

i have a nvidia 7 series card... used the following guide and i am now getting excellent graphics output with my 17" widescreen monitor (just like windows!)...

[http://howtoforge.com/sharp_fonts_gnome_p2]("http://howtoforge.com/sharp_fonts_gnome_p2")

you will need little tweaking & re-starting X though...

hope it helps...

cheers...!!!

devang.

---

### Post by Shrimply on 2008-09-06
Umm, it seems to be fixed, although not entirely sure why, I disabled the restricted drivers and restarted.

Upon restart the drivers were still enabled but the screen was at the right resolution.:confused:

---

### Post by fatality_uk on 2008-09-06
Glad to hear that. Does it still work if you do a reboot again?

---

### Post by Shrimply on 2008-09-06
Yeah it does,  bit bizarre but I'm not complaining.

Thanks for the help, I think I might be around here quite a bit in the near future

---

### Post by Shrimply on 2009-02-21
Hi, dunno if I should be bumping this back up but I've got exactly the same problem again after a ram upgrade.

I really don't know what to do it was all working fine.

everywhere I look for solutions it tells me to run 
sudo dpkg-reconfigure xserver-xorg

but when I do this I never get asked about the graphics card, it runs through the keyboard layout but nothing else.  I'm probably doing something wrong but I really don't understand very much of this yet.

Which is something that annoys me a bit, i hate blindly following instructions without understanding them, but as of yet I've never had the time to properly read about how it all works.

---

### Post by kestrel1 on 2009-02-21
Could you post your xorg.conf file.
To view the file do the following from a terminal.```
gedit /etc/X11/xorg.conf
```

---

### Post by Shrimply on 2009-02-21
Sorry to mess you around, once again I seem to have managed to resolve the issue, no real idea how.

I downloaded the nvidia driver from their website, fiddled around more or less randomly and upon restart a big nvidia screen popped up and it then continued to load ubuntu correctly with working drivers.

---

### Post by kestrel1 on 2009-02-21
Cool, as long as you are sorted that is good.

---

