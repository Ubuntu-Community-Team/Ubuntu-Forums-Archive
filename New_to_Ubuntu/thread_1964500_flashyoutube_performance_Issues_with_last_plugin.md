---
title: "flash/youtube performance? Issues with last plugin?"
date: 2012-04-24
forum: New to Ubuntu
---

### Post by Dahm on 2012-04-24
Hi everyone!

I'm a newbie in the linux world and have just installed Xubuntu 11.10 on an old laptop (Pentium II - 1,20GHz - 512 MB RAM).

I thought initially that youtube, and hence flash, didn't work at all in firefox: back hole where the flash player should be. 
I've tried every possible installation with flash aid, then also reinstalled with " sudo apt-get install flashplugin-installer", then tested with youtube/html5, before I discovered that not all youtube videos had this black hole. Some videos worked, although the image was of bad quality, only 1 image every half second or so.

So I concluded it was a performance problem. 
I then reinstalled flash properly one last time with flash aid:
- stable version 
- with "Overide GPU validation"
>>> current plugin version = Shockwave flash 112r r202

I left youtube with html5 because the image looked slightly better than without (when there was an image and not this black hole).
I tested with minimal resolution (480p), nothing better.

>>> What can I do to better the situation? Do you think it might be linked to the issues with the last version of this plugin?

Please explain me step by step what I must do, since I'm really brand new in linux and nothing is straight forward for me.

Furthermore my installation is in French. Can I switch easily between French and English versions of Xubuntu so that I can find easily what you'll explain to me?

Thanks in advance!

---

### Post by scheuri on 2012-04-24
Hi there

I personally think there is not much to do.
That flash aid you are using? Never heard of it. I usually only install using apt-get or the software centre of Ubuntu because using third party helpers can (well, CAN, does not need to) make more issues than not.

Fact, however, is that your computer is not really the best there is.
A Pentium 2 with 512 MB RAM? Did youtube work when you were using windows on it?
Flash can be rather ressource intense.

Sorry, but I am not sure how easy that is to solve (if it is).
cheers
scheuri

---

### Post by lovinglinux on 2012-04-24
> **scheuri said:**
> Hi there

I personally think there is not much to do.
That flash aid you are using? Never heard of it. I usually only install using apt-get or the software centre of Ubuntu because using third party helpers can (well, CAN, does not need to) make more issues than not.
i

I am the developer of Flash-Aid.

> **scheuri said:**
> Fact, however, is that your computer is not really the best there is.
A Pentium 2 with 512 MB RAM? Did youtube work when you were using windows on it?
Flash can be rather ressource intense.

I am afraid you are correct. That machine will struggle to play flash, if it can play it at all without stuttering and overheating the CPU.

See [http://webgapps.org/groups/firefox/docs/flash-optimization/](http://webgapps.org/groups/firefox/docs/flash-optimization/) for some possible optimizations.

---

