---
title: "[SOLVED] Cairo-dock black background (Intrepid)"
date: 2008-11-17
forum: New to Ubuntu
---

### Post by kestrel1 on 2008-11-17
Been using Cairo-Dock on Ubuntu 8.04 (hardy) with no problems. The background was transparent as I wanted it, but now I have upgraded to 8.10 (intrepid) & the background stays black & I have been unable to find a solution to this. Compiz appears to be running correctly, I have removed & re-installed Cairo-Dock, nothing seems to help.
The version I am using is 1.6.3.1 & it was downloaded from the repo's. I had the same issue with the older version in Intrepid.
Has anyone had the same problem & fixed it or does anyone know how to fix this. I normally try to figure these things out for myself, but I am at a loss with this one.
Thanks in advance.

---

### Post by kestrel1 on 2008-11-17
bump

---

### Post by kestrel1 on 2008-11-17
Has anyone got any ideas on this one or do I give up & re-install 8.04?

---

### Post by nhasian on 2008-11-17
hello, the cairo-dock does not work yet with 8.10.  I thought i read somewhere that a new version is the works, but I dont know when it will be released.  hopefully soon.

---

### Post by brianfriedkin on 2008-11-17
> **kestrel1 said:**
> Has anyone got any ideas on this one or do I give up & re-install 8.04?
I had the same problem and then I noticed Compiz was not loaded. If Compiz is not loaded click it on and then try re-loading Cairo-dock. If that is not your problem try restarting Compiz then re-start Cairo-dock.

---

### Post by kestrel1 on 2008-11-18
Just tried to restart compiz, but I got this error message:
```
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity
```
Any ideas?

---

### Post by wieszti on 2008-12-13
If you don't want use Compiz try this:

```
gconftool-2 -s '/apps/metacity/general/compositing_manager' --type bool true
```

it's works

---

### Post by kestrel1 on 2008-12-15
Thanks, I will give that a go. I have actually reverted to 8.04 at present, but I have another machine I can try it on.

---

### Post by kestrel1 on 2008-12-16
Thanks, I have now tried that & everything is working correctly.
I did have a problem with Open Office, where the text menu's had become transparent. I got around this by going to System - Preferences - appearance & then going to the fonts tab & selecting Subpixel smoothing (LCD's) The menu's came back correctly then.
Anyway, thanks for your help on the other issue. I think it is down to the NVidia driver with OO.org, because it is OK until you start using the propriety drivers

---

### Post by SumyTheSlayer on 2009-07-30
> **wieszti said:**
> If you don't want use Compiz try this:
```
gconftool-2 -s '/apps/metacity/general/compositing_manager' --type bool true
```

thank you man, it worked for me...

---

### Post by slimjimmy23 on 2009-11-26
Thanks, It worked for me too, I just put Karmic Koala on my little brother's computer and I had the same problem.

---

### Post by robertoaguiarlima on 2010-01-07
It's don't works for me, but this works: [http://www.pendrivelinux.com/cairo-dock-black-background-fix/](http://www.pendrivelinux.com/cairo-dock-black-background-fix/)

The solution was:
1 - Go to cairo-dock config (right click any icon in cairo dock)
2- Select cairo-dock->config
3 - select behavior -> System
4 - go to composition in the botton of scroll
5 - enable the option "Emulates composition with fake transparency" 
6 - click ok!

---

### Post by robertoaguiarlima on 2010-01-07
Another Solution!
In this solution you don't need enable fake transparency, but it is only for ati graphic cards (Raideon HD Series), on ubuntu 9.10.
If you use proprietary graphic card remove it.
Go to the ati site and download de driver of your graphic card.
it's works for me too.

---

