---
title: "Update libc6? Trying to install free Pascal &quot;fpc&quot;"
date: 2008-10-08
forum: New to Ubuntu
---

### Post by MSPhobe on 2008-10-08
I'm very new to Ubuntu, but experienced with computers generally.

I'm trying to install the free Pascal compiler "FPC". I've made a certain amount of progress... I've got the compiler in, I think, using sudo dpkg.

Note that I'm NOT trying to install Lazarus on top of FPC (yet!)

I found some .deb files for fpc... 

[http://www.freepascal.org/down/i386/linux.var](http://www.freepascal.org/down/i386/linux.var)

... but now I'm trying to install the ide, using sudo dpkg.

I'm being told that my...

libc6

... and...

libncurses5

are too old. (My Ubuntu is ver 7)

Synaptic Program Manager tells me that my libc6 and libncurses5 are the most up to date... known to it.

What are my options? Can I replace the two modules? Where do I get the more up to date ones? What's the downside? Do I have to re-compile of the whole OS, or can I just replace the modules simply?

Thanks for whatever ideas and advice you can offer....

Tom

---

### Post by bumanie on 2008-10-08
Type libc6 debian into a search engine and you will be taken to where you can download the latest stable version of the library. Repeat the process for the other library.

---

### Post by MSPhobe on 2008-10-08
Thank you! Before I try that, does anyone else what to jump in? I'm hoping the upgrade is a) easy, b) a safe thing to do? (Well, within reason!)

Thanks

---

### Post by Sef on 2008-10-08
1) What version of Ubuntu are you running?

2) This has been a problem of late. Have not found a post that is relevant yet.

3) Check [packages]("http://packages.ubuntu.com").

---

