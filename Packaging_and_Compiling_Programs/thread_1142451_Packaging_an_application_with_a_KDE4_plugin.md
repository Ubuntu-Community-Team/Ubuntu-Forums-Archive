---
title: "Packaging an application with a KDE4 plugin"
date: 2009-04-29
forum: Packaging and Compiling Programs
---

### Post by becrux on 2009-04-29
Hi all :)

I've a problem with my Ubuntu package creation.

I'm trying to make a .deb of my Wally ([http://sourceforge.net/projects/wally](http://sourceforge.net/projects/wally)).

Wally is a wallpaper changer, and it works with all major WMs, including KDE4. Its main dependencies are EXIF and Qt4.

When it's used with KDE4, it needs an additional .so module, called WallyPlugin (compiled aside from standard sources), that depends on kdelibs5 and kdebase-workspace.

My problem is that I don't want to have a debian package depending on these two packages, cause:

a) you don't use KDE4. Ok, that's fine. You'll have a wallyplugin.so installed in your system that is useless, it's never used and it will be removed on uninstallation.

b) you use KDE4. Of course you HAVE TO install kdelib5 and kdebase-workspace, otherwise your KDE4 won't work, so they're implicitly satisfied.

If I ask "debuild" for wally & wallyplugin installation, its correct behaviour imposes these two dependencies. Of course, I won't ask you to install kdelibs5 if you are using FVWM!!! :(

I found two solutions to this problem, but I don't know which one is right, and if there's a better one.

a) I can produce two debian packages, one for general use, another one only for KDE4 users. In this case, which standard packaging name should I use?

b) I can manually remove the two dependencies from control file, and repackage. Frankly speaking, I don't like this :( (it seems to me that I'm not following Packaging Guide rules). Moreover, will MOTU accept this modified package?

Thanks so much in advance for all your suggestions and help,

Tony.

---

