---
title: "Moving media"
date: 2013-01-11
forum: New to Ubuntu
---

### Post by Numetrick on 2013-01-11
Hi All, 

I want to move over to Ubuntu in the next few months; however, before I do, I want to move all my media off my media off my mac and onto a NAS drive. 

First, does the NAS drive need to be formatted specifically for Ubuntu? 

Also, anybody have any tips on how to move my media media? I was thinking about putting it all onto a 1/2tb portable drive and moving it onto NAS through my new Ubuntu laptop. 

Thoughts?

---

### Post by audiomick on 2013-01-11
> **Numetrick said:**
> First, does the NAS drive need to be formatted specifically for Ubuntu? 

No. As far as I understand it, the operating system of the NAS device takes care of the actual accessing of the drives, and communicates outwards via protocols such as Samba, FTP or NFS.


> Also, anybody have any tips on how to move my media media? I was thinking about putting it all onto a 1/2tb portable drive and moving it onto NAS through my new Ubuntu laptop. 

That is one way of doing it, but I believe you should be able to store to the NAS from your Mac and later access the files from the Linux OS. That is the nature of an NAS: it sits in the network and should be accessible from other computers regardless of which OS they are running.

You must, of course, have support for whatever file sharing protocol is being used on whichever OS you are using. Having said that, Ubuntu can deal with all three of the ones I mentioned above. I would assume that a Mac would have at least FTP, most probably something equivalent to Samba, which deals with Windows file shares, and likely NFS too.

I have an NAS. I don't use it all that much, to be honest, so I am a bit hazy, but I believe it is possible with it to put stuff on it via one protocol and access it via another.

---

### Post by Rocklobster690 on 2013-01-12
[QUOTE=Numetrick]anybody have any tips on how to move my media media?[/QUOTE]

```
CP
``` 

:-P

You can also use the NAS box as a TimeMachine to backup the Mac. \\:D/
(FreeNAS anyway)

---

