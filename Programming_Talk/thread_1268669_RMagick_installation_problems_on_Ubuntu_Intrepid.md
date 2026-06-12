---
title: "RMagick installation problems on Ubuntu Intrepid"
date: 2009-09-17
forum: Programming Talk
---

### Post by yt_vinay on 2009-09-17
Hi,

I have tried to install rmagick, imagemagick and dependencies about 5 times on my ubuntu intrepid server but something or the other keeps failing.

Now, I have half/fully installed files hanging around for all these libraries (jpeg-6b, libpng-1.0.6, libtiff-lzw-compression-kit, libwmf, tiff-v3.5.5, ImageMagick-6.3.7 and a lot more) and I just discovered that I havent configured the Makefile to uninstall so make uninstall too is failing.

I need some guidance from someone who has done this before. Is there a way for me to clean the server of these hanging files and then starting over? Or should I start with a fresh server running Ubuntu Intrepid and start from there?

In either case, does anyone know of a good, reliable resource for getting RMagick up and running in a Ubuntu Intrepid server?

Thanks!

---

