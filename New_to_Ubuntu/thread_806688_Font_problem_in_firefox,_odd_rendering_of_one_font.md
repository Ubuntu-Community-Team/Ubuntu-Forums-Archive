---
title: "Font problem in firefox, odd rendering of one font type."
date: 2008-05-25
forum: New to Ubuntu
---

### Post by philinux on 2008-05-25
Does anyone know why this is happening, and a fix.
Sorry for the ad but it's where it happens most.

Cheers

---

### Post by kerry_s on 2008-05-25
those are bitmapped fonts, you can turn off bitmaps->
sudo dpkg-reconfigure fontconfig-config
say no to bitmaps.
or
you can send them to another font using a ~/.fonts.conf file, you need to create it if don't have it.

```


<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>

<match target="pattern" >
 <test name="family" qual="any" >
 <string>Helvetica</string>
 </test>
 <edit mode="assign" name="family" >
 <string>Nimbus Sans</string>
 </edit>
</match>

<match target="pattern" >
 <test name="family" qual="any" >
 <string>Verdana</string>
 </test>
 <edit mode="assign" name="family" >
 <string>Nimbus Sans</string>
 </edit>
</match>

<match target="pattern" >
 <test name="family" qual="any" >
 <string>Arial</string>
 </test>
 <edit mode="assign" name="family" >
 <string>Nimbus Sans</string>
 </edit>
</match>

<match target="pattern" >
 <test name="family" qual="any" >
 <string>Lucida</string>
 </test>
 <edit mode="assign" name="family" >
 <string>Nimbus Sans</string>
 </edit>
</match>

<match target="pattern" >
 <test name="family" qual="any" >
 <string>Times</string>
 </test>
 <edit mode="assign" name="family" >
 <string>Nimbus Roman</string>
 </edit>
</match>

<match target="pattern" >
 <test name="family" qual="any" >
 <string>Courier</string>
 </test>
 <edit mode="assign" name="family" >
 <string>Nimbus Mono</string>
 </edit>
</match>

</fontconfig>


```

---

### Post by philinux on 2008-05-25
Right ok, They look worse cos I did view zoom, just one step as the fonts were so small.

If I just do the "say no to bitmap fonts" what do they get replaced with.

---

### Post by kerry_s on 2008-05-25
> **philinux said:**
> Right ok, They look worse cos I did view zoom, just one step as the fonts were so small.

If I just do the "say no to bitmap fonts" what do they get replaced with.

bitmap fonts, will be replaced with truetype fonts(ttf) so they'll match the other fonts surrounding those bad fonts. those bad fonts are microsoft font substitutes, the way it's set up now your system offers them a choice from all your fonts, you want it to only use the good fonts.

web pages have a list they go down and take the first 1 you have, it's like this->
.h{font-family:helevicta,times,verdana,arial,sans-serif}

so if you don't have: helevicta,times,verdana,arial
offered to the webpage it will use: sans-serif

don't forget you need to reboot, so it can switch the fonts.

---

### Post by philinux on 2008-05-26
Ok did this

> sudo dpkg-reconfigure fontconfig-config
say no to bitmaps.


There were three choices so I took.
autohinter
automatic
no

Still got bitmaps yuk.

---

### Post by kerry_s on 2008-05-26
> **philinux said:**
> Ok did this



There were three choices so I took.
autohinter
automatic
no

Still got bitmaps yuk.

did you reboot? you need to reboot or restart X, sometimes just restarting X is not enough as fonts are cached.

---

### Post by philinux on 2008-05-26
> **kerry_s said:**
> did you reboot? you need to reboot or restart X, sometimes just restarting X is not enough as fonts are cached.

Quit then restart as you suggested.

Like I said it looks worse cos I'm zoomed in 1 step.

---

### Post by kerry_s on 2008-05-26
> Quit then restart as you suggested.

:confused:

just quiting the browser and restarting is not good enough.

reboot
or
restart X (press ctrl+alt+backspace at the log in screen)

---

### Post by philinux on 2008-05-26
> **kerry_s said:**
> :confused:

just quiting the browser and restarting is not good enough.

reboot
or
restart X (press ctrl+alt+backspace at the log in screen)

Nah not quit the browser, the big quit. Anyway just rebooted system again after updates.

---

### Post by kerry_s on 2008-05-26
wait a second, i just went there, that's a gif(picture) you cant do nothing about that font wise. changing the size of images will give effects like that depending on the image type, some types scale better than others.

---

### Post by philinux on 2008-05-26
[http://www.pcworld.co.uk/](http://www.pcworld.co.uk/)

What about this site. The text under each pic is bitmap for me.

---

### Post by kerry_s on 2008-05-26
> **philinux said:**
> [http://www.pcworld.co.uk/](http://www.pcworld.co.uk/)

What about this site. The text under each pic is bitmap for me.

the font under each pic is part of the pic, right click the pic and choose view image and you will see what i mean

---

### Post by philinux on 2008-05-26
IEs4Linux has no problem with these. How do I get Firefox to behave.

---

### Post by taisao on 2008-05-26
It's because the firefox version you are using. With firefox version 2 it looks good like it should be.
--

Firefox 3 offer 2 zoom mode: full page or just text, you can choose that within menubar -> view -> zoom.

---

### Post by kerry_s on 2008-05-26
hmmm, i don't know what to tell you. most sites are made to work with IE so i'm pretty sure it's optimized for ie's rendering engine. your kinda splitting hairs though, the sites still display nice enough that you should have no problems reading it, sure some may not look 100% percent perfect but that's the sites fault, as there not standard compliant but rather built for IE.

---

### Post by philinux on 2008-05-26
> **kerry_s said:**
> hmmm, i don't know what to tell you. most sites are made to work with IE so i'm pretty sure it's optimized for ie's rendering engine. your kinda splitting hairs though, the sites still display nice enough that you should have no problems reading it, sure some may not look 100% percent perfect but that's the sites fault, as there not standard compliant but rather built for IE.



> It's because the firefox version you are using. With firefox version 2 it looks good like it should be.

Ok so maybe RC1 will fix it.

---

### Post by taisao on 2008-05-26
Firefox 3b5 is fine. I just edit my post above.

You may want to try this extension if you like zooming :KS -> [No Squint 1.93.2]("https://addons.mozilla.org/en-US/firefox/addon/2592")

---

### Post by philinux on 2008-05-26
> **taisao said:**
> Firefox 3b5 is fine. I just edit my post above.

You may want to try this extension if you like zooming :KS -> [No Squint 1.93.2]("https://addons.mozilla.org/en-US/firefox/addon/2592")

I'll just put up with it.
I use right window key and mouse wheel to zoom in on flash video. Better than full screen for now.

---

