---
title: "stop spontaneous keyboard layout switch"
date: 2011-09-20
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by RikoW on 2011-09-20
Dear all,

I have a laptop with a built-in English keyboard. When the laptop sits at work in its docking station it has attached a wireless keyboard with German layout. 

I use the keyboard layout applet to switch between the layouts. However, it seem like Ubuntu is switching the layout often by itself and always to the one which is NOT connected, which is driving me nuts. So far I have not discovered a systematic behind it.

This is actually something that was already bothering me with previous Ubuntu installs. I use ALT+SHIFT to switch the layout via the keyboard. 

Anyone has any idea how to stop this annoying behaviour?

Cheers,

       Riko

---

### Post by dino99 on 2011-09-20
and what happens if you only set "german" ? meaning removing the 2 others.
By the way your comments are saying that user choice is ignored by default: might need to report against such issue

---

### Post by pressureman on 2011-09-20
Are you sure it's not just per-window keyboard layout? I use that because I prefer the English layout for programming, but I'm often chatting to German people on IM. If you're switching between windows a lot, it can sometimes feel like the system is choosing the exact keyboard layout that you don't want.

---

### Post by RikoW on 2011-09-20
> and what happens if you only set "german" ? meaning removing the 2 others.

I removed the other layout and only left German, and so far no switching tool place. However that's not very convenient when I go back home and only what to go back to English.

> Are you sure it's not just per-window keyboard layout?

Yes I'm sure, it's not a per window layout. See the attached screenshot and OP.

Thanks and cheers,
               Riko

---

### Post by Yumi on 2011-09-20
How would you set a "per-window keyboard layout" in Ubuntu? I did not know this is possible and a search found nothing.

Also I use English, German and Chinese layouts - no problems here.

Michael

---

### Post by jbicha on 2011-09-20
Could you go ahead and report a bug? I'd use ```
ubuntu-bug gnome-control-center
``` . I don't know if it's a g-c-c issue but that should get you close.

Developers don't generally hang out on the forums.

---

### Post by RikoW on 2011-09-21
After I removed additional layouts and kept only one, I didn't have any problems anymore (I guess, that's not really a surprise) :)

However, later I added the English layout again to the German one and so far, I didn't suffer from the spontaneous switching anymore.

I did disable the switching of the layout via ALT-SHIFT, however. Maybe that's what did it!? I'll work a bit more and then turn the keyboard sequence back on. If it comes back, it's probably that.

Then I'll report bug.

Cheers,

            Riko

---

