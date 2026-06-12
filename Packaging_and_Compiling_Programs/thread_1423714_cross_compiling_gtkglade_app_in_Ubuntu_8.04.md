---
title: "cross compiling gtk/glade app in Ubuntu 8.04"
date: 2010-03-07
forum: Packaging and Compiling Programs
---

### Post by jwkaisd on 2010-03-07
I have developed a gtk gui application under ubuntu linux.  I need to get it cross compiled to operate on windoze.  This application uses glade/libglade.

I have installed the mingw32 cross compiler and I installed a bundle that loads all of the gtk dev files needed including dependencies except for glade.

I set up the make file and got the project to build all the way except for not being ablet to find libglade-2.0.

I separately downloaded glade for win32 and installed it in the cross compiler install directory as well.

I insured that all the pkg-config files had all the correct entries for the prefix definition making it point to the cross compiler installation directory.

As you can tell, I am somewhat inexperienced in all of this, but I am learning.

So finally the project builds, except for it returns "cannot find -lxml2".  I thought that something must be missing from glade, but I have learned that even though glade uses xml2, in some cases the xml2 library should be installed with the mingw cross compiler even if glade is not used.

My mingw cross compiler was installed using the synaptic application manager and I am using Ubuntu 8.04 hardy.

I am sorry for the long explanation, but what I am looking for is - can someone tell me where to find and how to install xml2.  I have found libxml2, but I installed it, and the linker still complains taht it cannot find -lxml2.

If someone can point me in the right direction here, I will be really grateful!

Thanks!
john (jwkaisd)

---

### Post by SevenMachines on 2010-03-07
not sure if this is what you're looking for but the xml2 windows port is [here]("http://www.zlatkovic.com/libxml.en.html"). I don't really cross compile but i'm guessing you need that in your toolchain for it to work, you can take that advice with a heavy pinch of salt though :)

---

### Post by jwkaisd on 2010-03-07
Dear Seven Machines,

Thanks so much for your response.  I had actually been to this site, but when I downloaded the referenced library I had trouble getting it to install correctly.

I later found the archive libxml2-dev_2.7.4-1_win32.zip.

Several links referred to it, but I had some trouble finding it since the main gnome download point gave me 404 page not found errors.

I did find it at: [http://ftp.se.debian.org/pub/gnome/binaries/win32/dependencies/](http://ftp.se.debian.org/pub/gnome/binaries/win32/dependencies/)

Once I did it - it worked fine!

I would not cross compile for that other op system either, but work constraints require it.

I did get the app working and I really appreciate you responding to me so quickly.

Thanks and very best regards,
john

---

