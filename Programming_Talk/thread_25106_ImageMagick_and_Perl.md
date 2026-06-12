---
title: "ImageMagick and Perl"
date: 2005-04-09
forum: Programming Talk
---

### Post by StonePiano on 2005-04-09
Hi,

I installed **Image::Magick** on my redhat machine at work, and in **Perl** I can resize images like:

```
#!/usr/bin/perl -w

use Image::Magick;

my $pic = Image::Magick->new();
my $x = $pic->Read("pic.jpg");
print $x if $x;
$y=$pic->Scale('150x150');
$pic->Write("new.jpg");
```

It works great on my redhat box.

But when I do it on my Ubuntu Warty machine at home, I get the following Exception error:
**420: no decode delegate for this image format `pic.jpg'**

Does anyone have any ideas as to what is is and _how I can get a *decode delegate* for jpg format on my ubuntu machine?_

(Running Warty.  It seems clear to me that it's a software component missing, so I've not included hardware details.)

Many thanks for any help or insight,
StonePiano

---

### Post by kperkins on 2005-04-09
Are your jpeg libraries (libjpeg*) installed?

---

### Post by StonePiano on 2005-04-09
*Are your jpeg libraries (libjpeg*) installed?*

I think so.  On a find, I get:

root@kiboko:/ # find . -name "libjpeg*" -print
./var/lib/dpkg/info/libjpeg62.postinst
./var/lib/dpkg/info/libjpeg62.list
./var/lib/dpkg/info/libjpeg62.shlibs
./var/lib/dpkg/info/libjpeg62.md5sums
./usr/share/doc/libjpeg62
./usr/lib/libjpeg.so.62.0.0
./usr/lib/libjpeg.so.62
./usr/lib/gthumb/modules/libjpegtran.so
./usr/local/jdk1.5.0_02/jre/lib/i386/libjpeg.so

Also, in the Synaptic Package Manager, a search turns up libjpeg62, which I have.

StonePiano

---

