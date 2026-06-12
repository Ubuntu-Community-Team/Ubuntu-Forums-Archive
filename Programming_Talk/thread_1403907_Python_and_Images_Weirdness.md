---
title: "Python and Images Weirdness"
date: 2010-02-10
forum: Programming Talk
---

### Post by HalfEmptyHero on 2010-02-10
I was testing out using python to resize images, and something really strange happened. I image I was using was a png image with a transparent background that came from a jpeg picture I had taken and edited. When I resized the image, the background came back, but I don't know how this is possible. If I open the same picture in gimp, there is no background and only one layer like there should be. Why did this happen and how can I stop it. This is the code I was using

[PHP]
import image
im1 = Image.open("image.png")
im2 = im1.resize((128, 128), Image.ANTIALIAS)
im2.save("image.png")

[/PHP]

---

