---
title: "Need a little help running 10.04 on my iMac"
date: 2012-02-18
forum: New to Ubuntu
---

### Post by ions82 on 2012-02-18
Hello!

I've recently installed 10.04 onto an iMac G5.  It took a little figuring out before I had it up and running.  It's running WAY better than the install of Mac OSX that I tried to do.  However, I am having trouble with online media playback.  I have been unable to use virtually all Flash-based media, and certain videos on YouTube are also giving me trouble.  Additionally, I haven't been able to use most streaming stations for internet radio.  Have I overlooked something simple?  Is there a relatively easy solution?  I am still very new to Linux, and I don't have a background in anything too technical (in terms of computers and programming).  Hopefully, it's not just something I'll have to live with.  Then again, I am using a rather outdated computer.  Thank you for any help or advice you can offer!

---

### Post by 3rdalbum on 2012-02-18
Unfortunately, although Adobe makes Flash Player for Linux, it's only x86 Linux and won't run on your PowerPC-based Mac. If Youtube is working mostly for you, then you must be using an open-source Flash implementation; reverse-engineered, hence the troubles you've had.

Solutions? I can't really give you any. There are programs around like Minitube that can let you watch Youtube videos without Flash, so that might help with the ones that have been giving you trouble. But that won't help for other sorts of Flash media.

As for codecs, on PowerPC you just need to make sure you have the "ubuntu-restricted-extras" package installed. If something still doesn't play, then it's probably never going to play on your PowerPC.

It's a huge shame that proprietary stuff on Linux doesn't work on anything but x86 PCs, but I pretty well survived for six months with only a PowerPC machine running Linux. You might find you can do without the missing pieces.

---

