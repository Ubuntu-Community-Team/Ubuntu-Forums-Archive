---
title: "[SOLVED] Firefox -- what's wrong with the fonts?"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by altonbr on 2008-06-04
I've found that since firefox-3.0 was included in Hardy, its had this horrible bug where my fonts don't know up properly (on some occassians).

I thought it had to do with character-encoding, but I found that it was mostly older sites that had this problem, so I wasn't too worried.

I've also been doing my own development on my localhost and have seen no problems, until today.

Attached is a screenshot of the box in Firefox 3.0 RC1/Linux (above) and Firefox 3.0 RC1/Windows (below)

The HTML I have is:
> <p class="warn"><strong>Warning:</strong> Images larger than 640x480 should not be used! It is suggested to edit the image with an image editor, such as <a href="http://gimp-win.sourceforge.net/stable.html">The GIMP</a>, and make them exactly 640x480, 480x640, or smaller.</p>
and it should have been served as UTF-8. I'm also using gEdit which saves as UTF-8.

---

### Post by sayakb on 2008-06-04
Try adding more fonts in the ~/.fonts folder. I guess you already have the msttcorefonts package installed.?

---

### Post by altonbr on 2008-06-04
I have hundreds of fonts installed at ~/.fonts and msstcorefonts installed.

I also just deleted my ~/.mozilla folder to see if it would help and it didn't.

---

### Post by sayakb on 2008-06-04
I'm still stuck with beta5. Due to some reasons (predominently lack of time to experiment with the installation), I have to keep my proposed and backports updates repos disabled. This might be a bug. Have you reported it?

---

### Post by altonbr on 2008-06-04
> **LinuxIsInnovation said:**
> I'm still stuck with beta5. Due to some reasons (predominently lack of time to experiment with the installation), I have to keep my proposed and backports updates repos disabled. This might be a bug. Have you reported it?

It was there in beta 5 as well.

I think it may be one of my fonts, because when I disabled "Helvetica" (which I have in my ~/.fonts folder) and replaced it with "DejaVu Sans", the problems went away.

Sorry to waste your time.

Its just really odd that the whole entire site can use Helvetica, but then all of a sudden and only in that box, does that error appear!

---

