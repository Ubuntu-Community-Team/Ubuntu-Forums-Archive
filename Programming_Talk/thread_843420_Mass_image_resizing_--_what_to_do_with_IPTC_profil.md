---
title: "Mass image resizing -- what to do with IPTC profiles?"
date: 2008-06-28
forum: Programming Talk
---

### Post by Asham on 2008-06-28
There's a need to scale a large number (5000+) of tif-images at work but I am no expert at image handling, haven't got a clue what to do with the IPTC profiles! At first I thought it'd be best to strip them from the generated images since they got significantly smaller file size wise if they are stripped from this information. What's your say? 

What's the best approach for handling images that must look like the original file on all platforms (Mac, Linux and Windows)?

Do we need to append the IPTC profile(s) when we resize the images? Even for thumbnails? The new images are to be used on the web so it's important that the colors do not vary too much from the original file. Is this where IPTC/color profiles come into place?

Please shed some light at this. I am lost, again. :lolflag:

---

### Post by thk on 2008-06-28
I've no idea what IPTC profiles are. Something like
```

mkdir rescaled
for f in *.tif; do convert -density 100 $f rescaled/$f; done

```
might do the trick. The convert command is part of the imagemagick package.

---

### Post by Asham on 2008-06-28
I'm not sure but I think the color profile is in the IPTC. Some images appear to have different color schemes, while some images have the same colors on the different platforms, others don't. So my conclusion is that it has to to with color profiles/IPTC.

---

### Post by Asham on 2008-07-03
I apologize for the bump but I could need someones input. Someone must have done a batch resize of high resolution images!?

---

