---
title: "Firefox won't display CJK text any more..."
date: 2012-04-07
forum: New to Ubuntu
---

### Post by baruch60610 on 2012-04-07
When I first installed Oneiric, Firefox worked well.  As I was trying to clean up my distro - removing unnecessary programs and files - I apparently got carried away and removed some files that FF needs to properly display Chinese, Japanese, and Korean (CJK) text.

The good news is that since I don't know any of these languages, I'm not losing any information I might otherwise have.  The bad news is that those boxes with the numbers in them look ugly; I'd rather see the attractive Asian characters.

Does anyone know what files I need to replace?  Or, can anyone kindly direct me to somewhere I can find this information?  I don't even know how to Google it (what search terms to use)...

BTW:  I've already tried modifying the "View | Character Encodings" options in Firefox, but those are fine.  As far as I can tell, I'm missing the actual CJK font files.  There are dozens of these (84 in synaptic).  I really don't want to have to install them all, just to get FF back to normal.

---

### Post by NikTh on 2012-04-07
Hi , 
I don't care about Japanese or Chinese language too , but those little boxes with numbering are annoying . 
Install this font and you will be ok. 
```
sudo apt-get install ttf-wqy-microhei
```

---

### Post by baruch60610 on 2012-04-08
Thanks for the idea, NikTh.  I appreciate it...

---

### Post by Zorael on 2012-04-08
You could also try to rename your **~/.fonts.conf** file in case there are (now-stale) font references in there that muck things up. They shouldn't, but hey. Just make sure to go into the Font section of System Settings afterwards and make sure your settings are correct.

(KDE saves its own font/color/etc settings in **~/.kde/share/config/kdeglobals** but also updates said .conf file -- which other non-KDE applications rely upon -- to mirror the basic antialiasing/hinting settings you setup.)

FWIW I use (and explicitly specify) [**Kochi Mincho**](apt://ttf-kochi-mincho-naga10) and [**Kochi Gothic**](apt://ttf-kochi-gothic-naga10) for CJK characters, mostly because they have non-antialiased bitmaps for font sizes 8 and below. I find that antialiased vertex fonts of such characters just become blurry messes at those sizes. ;/

---

### Post by baruch60610 on 2012-04-08
Zorael, I appreciate this information.  Thank you.

---

