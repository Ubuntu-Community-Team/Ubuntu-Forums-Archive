---
title: "xubuntu alternative that is free and gui based?"
date: 2006-07-17
forum: Other OS Talk
---

### Post by macgig on 2006-07-17
I tried installing xubuntu on a older pc.... didnt work. 

is there another good free gui based linux version I could try that may work? 

thanks.

---

### Post by T700 on 2006-07-17
[Here's]("http://distrowatch.com/") a link to a site that lists and describe dozens and dozens of distros.  Not knowing why it failed, it's kind of hard to suggest anything in particular for you.

Paul

---

### Post by macgig on 2006-07-17
after I installed it, moving the mouse would make the screen stuff dissapear, like I was drawing on it. odd. not sure why it did that. im guessing the graphics card was/is too old? im only guessing.

I'll check the link out. thanks. :)

---

### Post by teet on 2006-07-17
I don't think these are based off of XFCE, but they're designed specifically for older machines:

[http://www.puppylinux.org/](http://www.puppylinux.org/)
[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

Also, if you're feeling a little brave, you try doing a base install of Debian (note: this method is NOT GUI based) and then at the command prompt just do a

sudo apt-get install xfce xdm x-window-system-core

or something to that effect.  This is the method I had to use when I tried to install Ubuntu on antiquated hardware...for whatever reason Debian worked when Ubuntu didn't.

-teet

---

### Post by tseliot on 2006-07-17
Try Zenwalk linux

---

### Post by K.Mandla on 2006-07-17
Depending on your hardware, you might start with a server install, then add on with some of the suggestions for [low memory systems]("https://help.ubuntu.com/community/Installation/LowMemorySystems"). I have an older laptop that I use as a music machine, and I started with a server and added. ...

```
sudo apt-get install x-window-system-core xfce4 xfce4-terminal thunar
```
That will give you the xfce4 environment, a terminal window and thunar as a file manager. 

After that, it's up to you. ;)

---

### Post by RAV TUX on 2006-07-17
> **macgig said:**
> I tried installing xubuntu on a older pc.... didnt work. 

is there another good free gui based linux version I could try that may work? 

thanks.

Try the new Dreamlinux:

[COLOR=#ff0000]2006-07-16[/COLOR]         [COLOR=#ff0000]NEW[/COLOR] • [Distribution Release: Dreamlinux 2.0 WORKS]("http://distrowatch.com/3575")                       [[IMG]http://distrowatch.com/images/icon-large/dreamlinux.png[/IMG]]("http://distrowatch.com/dreamlinux")         The Dreamlinux Project Team announced version 2.0 of [Dreamlinux]("http://distrowatch.com/dreamlinux"), a Brazilian Linux distribution based on the XFce desktop: "called WORKS and it brings the most known Linux apps for a production environment, like OpenOffice, Inkscape, Gimp, etc. Full support to multimedia, automatic detection of video cards and monitors, and the version 2.5 of MKDistro, tool for distros' building. This Dreamlinux version is the result of making use of various technologies that came from many different distros, like Kanotix, Elive, Morphix and Debian. With a 2.6.14 Kanotix Kernel, the distro also counts with Xorg 6.9, support for ALSA and many refinements and improvements, beyond the customized XFCE 4.4 environment and with exclusive icons for this distro." More [information]("http://www.dreamlinux.com.br/english/saiba-works.html") can be found at the project's [homepage]("http://www.dreamlinux.com.br/"). [Download (MD5)]("http://www.dreamlinux.com.br/english/download.html"): [DLxfce2.0_WORKS-060712en.iso]("http://www.linorg.usp.br/isos/dreamlinux/DLxfce2.0_WORKS-060712en.iso") (611MB). An experimental Dreamlinux 2.0 [XGL edition]("http://www.dreamlinux.com.br/english/saiba-xgl.html") was also released.
[IMG]http://www.dreamlinux.com.br/english/imagens/download-ico_box.jpg[/IMG]             [FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2]**Dreamlinux                  2.0 WORKS Edition ** [COLOR=#0066cc]**625                  MB**[/COLOR][/SIZE][/FONT] 
                                                    [FONT=Verdana, Arial, Helvetica, sans-serif][[IMG]http://www.dreamlinux.com.br/english/imagens/download.jpg[/IMG]]("http://www.linorg.usp.br/isos/dreamlinux/DLxfce2.0_WORKS-060712en.iso")[/FONT]                   [FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2]                      **MIRROR 1 [COLOR=#0066cc]english version[/COLOR]                      **[/SIZE][/FONT]                                                                                    [FONT=Verdana, Arial, Helvetica, sans-serif][[IMG]http://www.dreamlinux.com.br/english/imagens/download.jpg[/IMG]]("http://streaming.serv.iv.fapesp.br:8000/vod/dreamlinux/dreamlinux-works/DLxfce2.0_WORKS-060712en.iso")[/FONT]                   [FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2]                      **MIRROR 2 [COLOR=#0066cc]english version[/COLOR]**[/SIZE][/FONT]                                               
              [FONT=Arial, Helvetica, sans-serif][SIZE=2][COLOR=#666666]md5sum:                41bb3fb5379c93b6be692eaa64df6ec5 [/COLOR][/SIZE][/FONT]

---

### Post by weekend warrior on 2006-07-18
Another recommendation for [Zenwalk]("http://www.zenwalk.org/") - fast, slender and well put together with a smaller but knowledgable and friendly community.

---

### Post by bonzodog on 2006-07-19
i would also strongly recommend Zenwalk - i am using it and was very impressed. It is slackware based and comes with very little out of the box, and it has a samll repo, but there are members of the community packaging programs as binaries, so most well known stuff is available.

---

