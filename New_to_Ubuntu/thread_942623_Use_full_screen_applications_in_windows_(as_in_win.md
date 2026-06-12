---
title: "Use full screen applications in windows (as in windows, not the OS)"
date: 2008-10-09
forum: New to Ubuntu
---

### Post by giordun on 2008-10-09
Hi. I'm playing a game that's in full screen (more specifically, NBA Live 08) with Wine and I was wondering if there was anyway that I could play it windowed because I'm not really sure how you switch back to the desktop properly. I use alt tab but because in game it changes the resolution it makes the resolution of my desktop super small.

Thanks.

---

### Post by jamesrl on 2008-10-09
Run ```
winecfg
```.  I'm pretty sure there is an option to run wine within windows of a specified size on one of the first few tabs.  (I'd give more detailed advice but don't have wine currently installed on my desktop).

---

### Post by Marshal0505 on 2008-10-09
Indeed, Follow James's instructions and tick 'emulate a virtual desktop' to make sure the wine program is windowed.
Sometimes i start a wine program with command : wine explorer /desktop=ref,800x600 "wine executable" to achieve the same result

```
 wine explorer /desktop=ref,800x600 /home/marshal/.cxgames/win2000/drive_c/Program Files/World of Warcraft/Wow.exe
```

Here's an example I used to use daily before i quit that game :p

---

