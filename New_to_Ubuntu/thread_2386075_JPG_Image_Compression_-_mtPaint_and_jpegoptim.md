---
title: "JPG Image Compression - mtPaint and jpegoptim"
date: 2018-02-28
forum: New to Ubuntu
---

### Post by electrosteam on 2018-02-28
Just started looking at mtPaint and tried to compress a photo image.
It is a bit confusing and lacks easy help pages, currently stuck at what Preferences to select to allow compression.

Along the way I discovered jpegoptim, and it seems an ideal tool to simply compress images.

Looking for assistance on nominating the appropriate Preferences in mtPaint, and comments on jpegoptim.

John.

---

### Post by TheFu on 2018-02-28
I don't use either of those tools, but to reduce the size of jpg images, perhaps for web publishing, I use a little script. It usually reduces the image sizes by 10x with zero perceived loss of quality to me.

```
#!/bin/bash
QUAL=40

for img in "$@"; do
  NEW=${img/%.???/-opt.jpg}
  echo " Working on $img ..."
   convert -quality $QUAL  "$img"  "$NEW"

done
echo "rename 's/-opt.jpg/.jpg/g' "
```

---

