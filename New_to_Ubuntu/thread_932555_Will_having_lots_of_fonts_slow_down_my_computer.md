---
title: "Will having lots of fonts slow down my computer?"
date: 2008-09-28
forum: New to Ubuntu
---

### Post by Sarah L on 2008-09-28
I've installed a large amount of fonts on my computer for photo editing and to display foreign glyphs such as Chinese and Japanese. Will this have the effect of slowing down system and application startup times?

I've also added a lot of conditions to my ~/.fonts.conf file, such as the following:
```

<!-- Disable antialias feature of AR PL ShanHeiSun Uni when pixelsize less than 17 -->
        <match target="font">
                <test name="family"><string>AR PL ShanHeiSun Uni</string></test>
                <edit name="antialias"><bool>false</bool></edit>
                <edit name="hinting"><bool>true</bool></edit>
                <edit name="autohint"><bool>false</bool></edit>
        </match>
        <match target="font">
                <test name="family"><string>AR PL ShanHeiSun Uni</string></test>
                <test name="pixelsize" compare="more_eq"><int>17</int></test>
                <edit name="antialias" mode="assign"><bool>true</bool></edit>
                <edit name="hinting" mode="assign"><bool>true</bool></edit>
        </match>

```
Will this substantially slow down any font loading and processing?

Thanks,
Sarah

---

### Post by steveneddy on 2008-09-28
Loads of fonts - like over 200-250 - will slow it down a little, but a font count over 1000 will be something you will notice on start up and launching the application.

---

### Post by Gannon8 on 2008-09-28
In other words, unless you have 100 different fonts for each language or something like that in the document, you should not be worrying about it.

---

