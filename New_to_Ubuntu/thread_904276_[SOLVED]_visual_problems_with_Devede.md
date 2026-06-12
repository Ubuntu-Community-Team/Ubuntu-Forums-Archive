---
title: "[SOLVED] visual problems with Devede"
date: 2008-08-29
forum: New to Ubuntu
---

### Post by lunanueva on 2008-08-29
I use Devede to convert .avi to .iso to burn dvds to watch on regular dvd players and the program runs fine.  However, when i burn the .iso file to disk there are several multi-colored lines throughout the video.  Maybe i'm not setting the preferences correctly in Devede, but i don't understand how i'm compromising a clean video.  If anyone has suggestions on how to tweak devede to resolve this problem, or comment on what i may be do wrong, i welcome them.  Thanks in advance.

---

### Post by tjwoosta on 2008-08-29
i had the same exact problems with devede

the solution was messing with the settings at the bottom (like aspec ratio and different filtering) before creating the .iso

im pretty sure what i did was set everything to speed rather then quality and for some reason it worked (and the quality was not effected)

(im not currently on ubuntu so i cant give you the exact settings i use)


but the trick is to make a change, then use preview to see if it worked or not, before creating an iso

---

### Post by timcredible on 2008-08-29
make sure your ntsc/pal setting is correct for your location.

---

### Post by lunanueva on 2008-09-01
Okay, sounds promising.  I forgot about the preview option for some reason.  I'll post my results when I get them.

---

### Post by lunanueva on 2008-09-01
So it turns out that it was a deinterlacing issue.  The "don't deinterlace" box was checked off under the advanced options.  I can't really decipher which filter is better, Median or ffMPEG???  Also, the "aspect ratio" box was marked, which created a larger image.  

After I figured out how to tweak the advanced options in DeVeDe and create a  great .iso file, I found a thread in the forums relating to this exact problem.  I had already searched for a thread before starting my own, but nothing came up.  Maybe the search engine is case sensitive.  Anyway, the problem has been resolved.  Thanks for your helpful suggestions.

---

