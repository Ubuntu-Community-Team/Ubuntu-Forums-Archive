---
title: "How to create a package"
date: 2005-10-11
forum: Programming Talk
---

### Post by dzonekl on 2005-10-11
Hi, 

I have requests from Ubuntu users who want to use jPodder on this OS. 
We have a generic linux distribution, but I am looking at creating a package. 
I have never made a linux (or ubuntu) package before and therfor would appreciate some pointers to instructions etc.. on how to do this. I also need to set file extensions/ protocol and MIME type association for my application somewhere in the OS so Firefox or other browser can act accordingly. 

The application (GPL) is a podcasting client named jPodder. it's written in java/Swing. If you want to know more about jPodder, you can download it from [http://www.jpodder.com](http://www.jpodder.com) 

Thanks for the help. 
Christophe Bouhier

---

### Post by toojays on 2005-10-11
For the basics on how to make a .deb package, see the [Debian New Maintainer's Guide]("http://www.debian.org/doc/manuals/maint-guide/index.en.html").

When it comes to changing mimetypes, etc, your best bet is to see how a similar package already does it, or ask on the ubuntu developer's mailing list.

---

