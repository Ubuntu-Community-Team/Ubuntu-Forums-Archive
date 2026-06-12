---
title: "Compiz Showing Funny Screen"
date: 2008-09-18
forum: New to Ubuntu
---

### Post by kolisikepu on 2008-09-18
Hi Community,

I'm using a Dell Latitude D520 Notebook running Ubuntu and it is awesome!!  There is one problem with mine and another friend of mine who has the same problem....

My current setup, I have a Notebook docked and using my 17inch monitor as my screen at 1280x1024.  When ever I do a Compiz animation, such as cube rotation holding crtl+alt+left click mouse and then move the mouse, I get a funny "cut" in my screen as if it is displaying the resolution of my Notebook on top of my 17" monitor.  Is this a bug in Compiz/Ubuntu?  How can I fix it?  I love using the animations on Compiz, like host (windows) key and tab to slide through my windows, but I can't see anything because it is hiding behind this cut window size of my Notebook, or rotate cube and then having this annoying cut off the Notebook screen size resolution.

I have noticed this though in the Screen resolution settings.  Please see screen dump.  The first screen dump is me sorting how screens sit aside.  The 2nd is what the screens are doing when I do a Compiz animation.  Is there a way where I can keep the Notebook display on the side of my main display?

I hope someone can help.

---

### Post by silverglade00 on 2008-09-18
I had this problem and the fix was to make sure that the two screens in your screenshot are next to each other, but not overlapping at all. Make sure that you can see the brown border around each one when they are next to each other.

---

### Post by kolisikepu on 2008-09-18
> **silverglade00 said:**
> I had this problem and the fix was to make sure that the two screens in your screenshot are next to each other, but not overlapping at all. Make sure that you can see the brown border around each one when they are next to each other.

That I certainly do... you can see in one of my screendumps.  Once I use a compiz animation, the Notebook monitor overlaps my external 17" monitor where I get a resolution of my Notebook monitor over my external display... hence my other screenshot.

I think I can mark this resolved as I have managed to resolve it on my friends Notebook as he had the same issue.

Notebook monitor needs to be disabled and then X restarted.

Thanks for your suggestion though silver.

---

### Post by silverglade00 on 2008-09-18
Now that I think about it, I was incorrect. I had the issue on an Nvidia card. If that is what you are using, then try using nvidia-settings (you might have to install) and enable Twinview. Sorry for the incorrect info and I hope your fix works!

---

### Post by kolisikepu on 2008-09-18
> **silverglade00 said:**
> Now that I think about it, I was incorrect. I had the issue on an Nvidia card. If that is what you are using, then try using nvidia-settings (you might have to install) and enable Twinview. Sorry for the incorrect info and I hope your fix works!

Thanks Silver... my friends Notebook has an nVidia.  Alot easier to disable and enable Notebook monitor than my intel chip.  I think I'll have to find a way to auto disable my Notebook monitor when I dock and then auto use my Notebook monitor when I'm not docking to use my external monitor.

I still have the issue, although I know what the issue as know what will fix it.

Any suggestions where I can find an easier way to disable and enable my Notebook monitor?

---

