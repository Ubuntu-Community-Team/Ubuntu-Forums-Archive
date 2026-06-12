---
title: "Improved font rendering"
date: 2006-06-06
forum: Outdated Tutorials &amp; Tips
---

### Post by johnc4510 on 2006-06-06
I just was reading some old posts and ran across this one:
[http://ubuntuforums.org/showthread.php?t=4456&highlight=fonts](http://ubuntuforums.org/showthread.php?t=4456&highlight=fonts)
It worked so well, I thought everyone might gain from it.
Much belated thanks to the author:Zenwhen

---

### Post by Sukarn on 2006-06-08
I dont know how, but without any of those patches I had already got the fonts being rendered like the ones in the screenshots. I tried to get myself those patched files anyway and I tried installing them.
They replaced some fonts with the patched ones (warning me about it on the way) and then after a restart I saw that... I still had the same fonts.

I think I had the better fonts because I had run some command in the terminal which guides us through the complete reconfiguration of the system (I dont remember the command though, the list of options was quite long). The reconfiguration asked me about which fonts I want to use and I had not selected the defaults, rather some other ones.

EDIT: Oops, what I was talking about was that I had followed another howto in the forums that included installing patched versions of the font files and it included screenshots of before and after the patch.

---

### Post by morgengenuss on 2006-06-08
you were right, man. this is still good :D

---

### Post by snop on 2006-06-08
Hi Sukarn,

> I tried to get myself those patched files anyway and I tried installing them.
They replaced some fonts with the patched ones (warning me about it on the way) and then after a restart I saw that... I still had the same fonts.


I guess you refer to [this how to]("http://www.ubuntuforums.org/showthread.php?t=180647").

Ensure that you checked "Subpixel smoothing" on System->Preferences->Font.

Once I checked this and restarted I saw a HUGE improvment in font rendering quality. Specially for small fonts in firefox (they turned from nearly unreadable to very clear letters).

---

