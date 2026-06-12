---
title: "Install Xorg without apt-get?"
date: 2008-06-21
forum: New to Ubuntu
---

### Post by mishathegoat on 2008-06-21
Hey everyone,

I was wondering how I could install Xorg without an internet connection (no apt-get)?

I have a computer with a fresh install of Ubuntu Server 7.10 and I'm interested in installing Fluxbox on it which requires X11 or Xorg or something..

Any help is appreciated..

Thanks,
mishathegoat

---

### Post by alienexplorers on 2008-06-21
You computer should have xorg at /etc/X11.  To edit xorg.conf from terminal enter:
> gksu gedit xorg.conf

---

### Post by mishathegoat on 2008-06-21
Hmmm... it doesn't seem to be there.

Note, I am using Ubuntu Server and not Ubuntu Desktop..

---

### Post by Eisenwinter on 2008-06-21
Do you have another computer? if so, you may be able to download the source for xorg and install it manually.

---

### Post by Dr Small on 2008-06-21
Any way possible that you could temporarily hook it up to ethernet or something to get a network connection so you could just use apt ?

---

### Post by maybeway36 on 2008-06-21
Could you just get an Ubuntu/Kubuntu alternate CD? You could do sudo apt-cdrom add, then sudo apt-get install xorg.

---

### Post by mishathegoat on 2008-06-21
> **Dr Small said:**
> Any way possible that you could temporarily hook it up to ethernet or something to get a network connection so you could just use apt ?

Probably not.. I only have wireless cards lying around.. and I'm gonna guess it's difficult to set wireless up on Ubuntu Server.. Unless you know of any easy way to do that?

[QUOTE=maybeway36]Could you just get an Ubuntu/Kubuntu alternate CD? You could do sudo apt-cdrom add, then sudo apt-get install xorg.
[/QUOTE]

I can get a copy of the alternate CD, yes. What does "sudo apt-cdrom add" do?

---

### Post by cariboo on 2008-06-21
See this thread to answer your question

[http://ubuntuforums.org/showthread.php?t=209859](http://ubuntuforums.org/showthread.php?t=209859)

Jim

---

