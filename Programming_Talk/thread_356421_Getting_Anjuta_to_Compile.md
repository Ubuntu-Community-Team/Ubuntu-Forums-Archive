---
title: "Getting Anjuta to Compile"
date: 2007-02-08
forum: Programming Talk
---

### Post by studiesrule on 2007-02-08
After many efforts to try and coax the source code for Anjuta 2.* to work (the repo version breaks down on me), I decided to try and post here. I'm compiling the 2.1.0 (the Wind) version. It seems to use some cutting edge libs, so I got a bunch of dependencies:
lib-dbus-dev (1.0.2) (repo has 0.93. This conflicts with libdbus 1-3-0 ver 1.*)
gnome-build 0.14

Now, while trying to build gnome-build, I run across this linker error:
>  can't find library: -lgdl-gnome-1 

I've installed all the gdl libs in the repos. I think that this might require a newer version, but can't seem to find one.

Can someone point out what I might need to compile? Or better yet a way of getting Anjuta 2 series to work without all this hassle?

Thanks a bunch

---

### Post by neilp85 on 2007-02-08
With a little bit of effort I was able to compile anjuta 2.1.0. I had to install quite a few dev libs from the repos. The only two I had to install from source were gdl-0.7.1 and gnome-build-0.1.4. Here are the links to those:
[http://ftp.gnome.org/pub/GNOME/sources/gdl/0.7/](http://ftp.gnome.org/pub/GNOME/sources/gdl/0.7/)
[http://ftp.gnome.org/pub/gnome/sources/gnome-build/0.1/](http://ftp.gnome.org/pub/gnome/sources/gnome-build/0.1/)

---

