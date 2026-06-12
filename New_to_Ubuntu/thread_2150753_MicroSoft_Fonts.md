---
title: "MicroSoft Fonts"
date: 2013-06-02
forum: New to Ubuntu
---

### Post by monkeybrain2012 on 2013-06-02
When I installed Ubuntu-restricted-extras it pulled in ttf-mscorefonts-installer and the EULA came up. I did NOT agree to it but it got installed anyway, Is this a bug? 

I have since completely removed this package, yet I still find "msttcorefonts" in /usr/share/fonts/truetypes. Can I just remove it?

Ubunti version 13.04

Thanks.

---

### Post by 3rdalbum on 2013-06-02
ttf-mscorefonts-installer is a package that contains pretty much nothing, except a script that downloads and installs the fonts.

If you choose "No", the package will still be installed, but the script will not continue and you won't get the fonts.

So, yes you can just remove it, or remove the package - whatever you want.

---

### Post by coffeecat on 2013-06-02
> **monkeybrain2012 said:**
>  yet I still find "msttcorefonts" in /usr/share/fonts/truetypes. 

Do you mean you have a folder /usr/share/fonts/truetype/msttcorefonts? If you want to be sure whether or not the actual MS fonts have been installed - which from what you say won't have happened - have a look inside /usr/share/fonts/truetype/msttcorefonts. If it's empty, they haven't been installed. If you have about 60 *ttf files, they have.

---

