---
title: "amiga/free bsd"
date: 2007-10-16
forum: Other OS Talk
---

### Post by mynis on 2007-10-16
well, i've been using ubuntu for about 6 months now, and its been awesome.  its astounding the difference in system recource usage vs windows that it presents. i don't even have to look at logs to see the difference, i can just listen to my pc. but after having installed the new system kernel a couple weeks back, my soundcard completely stoped working whatsoever. i know i shoulda followed the whole "if it ain't broke don't fix it" school of thought, but i've always installed updates as they came for security reasons, and never had a problem until now. i've followed the 'comprehensive sound faq' and nothing realy helps. the most of been able to do is get the startup sound to play (occasionally randomly and unnintentionally). so im highly considering switching to a new linux distro. the features of ubuntu i enjoy the most are the gnome gui, ntfs3g, k3b/k9copy/libdvd, xmms, and synaptic package manager. i've also heard red hat can be pretty easy to use. if nothing else i at least need to revert to the old system kernel.

if you have any comments about my technical issue please post them here [http://ubuntuforums.org/showthread.php?t=568741](http://ubuntuforums.org/showthread.php?t=568741)

---

### Post by SunnyRabbiera on 2007-10-16
From your topic it looks like you are having issues with Feisty.
I have found in my experience and looking at some posts here and there what works in one version might not work in the next especially if its a beta quality software/OS.
You might want to wait out and try gutsy, or maybe try another distro if it doesnt work out.

---

### Post by Tom Mann on 2007-10-17
what's Amiga got to do with anything? You should be able to boot the previous kernel from the grub menu you get when you first start up the computer. Does the sound work then?

Also try:

 
```
asoundconf list
```

and see if your card is in there. If so then try

```
asoundconf set-default-card [name of card]
```

where the name of your sound card matches the response you get from the the first command. This has worked for me in the past.

---

### Post by mynis on 2007-11-09
finally got it working after installing gutsy, thanks!

---

### Post by mips on 2007-11-10
> **Tom Mann said:**
> what's Amiga got to do with anything? .

I'm also baffled by that, cant see the connection or even the freebsd one ?

---

### Post by pelle.k on 2007-11-10
> I'm also baffled by that, cant see the connection or even the freebsd one ?
haha +1 :popcorn:

---

