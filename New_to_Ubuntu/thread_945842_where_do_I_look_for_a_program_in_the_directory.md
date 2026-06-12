---
title: "where do I look for a program in the directory?"
date: 2008-10-12
forum: New to Ubuntu
---

### Post by reltor on 2008-10-12
I am trying to set the default application that opens shoutcast streams in Firefox 3 to the VLC player instead of my two choice of media player or gecko.  When I click other, I do not know enough about the linux directory structure to find what I need to set the VLC player.  

Where do I find the links to the standard program files?  

Any help is appreciated.

---

### Post by Helios1276 on 2008-10-12
Can't you go Places-Home , then click View and 'view hidden folders' . Scroll to find .vlc  and thats your path?

---

### Post by oldos2er on 2008-10-12
> **reltor said:**
> I am trying to set the default application that opens shoutcast streams in Firefox 3 to the VLC player instead of my two choice of media player or gecko.  When I click other, I do not know enough about the linux directory structure to find what I need to set the VLC player.  

Where do I find the links to the standard program files?  

Any help is appreciated.

 /usr/bin/vlc

---

### Post by reltor on 2008-10-12
VLC is the name of the Video/Audio program. I am trying to figure out how to link to it in firefox applications, so that it is the default service for shoutcast files.  

I could also use Tunapie, but I cant find it either.  

I have some learning and unlearning to do with the linux directories:)

---

### Post by drs305 on 2008-10-12
App files:
```

whereis <appname>

```
Example: gimp: /usr/bin/gimp /etc/gimp /usr/lib/gimp /usr/lib64/gimp /usr/share/gimp /usr/share/man/man1/gimp.1.gz

App command:
```

which <appname>

```
Example result: /usr/bin/gimp

---

### Post by lovinglinux on 2008-10-12
> **reltor said:**
> VLC is the name of the Video/Audio program. I am trying to figure out how to link to it in firefox applications, so that it is the default service for shoutcast files.  

I could also use Tunapie, but I cant find it either.  

I have some learning and unlearning to do with the linux directories:)

The solution is the post above yours. When you click "Use other" in the Firefox Applications prefernces, next to the shoutcast files you should browse /usr/bin/vlc

The /usr directory is above your personal directory, which is /home/you/

To learn more about Linux directory structure visit the following links:

[http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/5022-linux-directory-structure-overview.html](http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/5022-linux-directory-structure-overview.html)

---

### Post by reltor on 2008-10-13
Thanks, I will give it a try.

---

