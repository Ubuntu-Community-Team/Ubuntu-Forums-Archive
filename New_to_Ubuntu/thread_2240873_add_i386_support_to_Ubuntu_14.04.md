---
title: "add i386 support to Ubuntu 14.04"
date: 2014-08-22
forum: New to Ubuntu
---

### Post by dave131 on 2014-08-22
I worked with another user to get their printer working, and can't for the life of me remember what I did to get 32-bit support libs in Ubuntu 14.04 64-bit.  I created a quick how-to on the forum [here]("http://ubuntuforums.org/showthread.php?t=2240872&p=13105345#post13105345") but need specific instructions for installing what used to get installed with the ia32-libs or what ever it was called.  I had gone through Synaptic and installed a couple of packages that looked like they installed it, but I don't remember them or if I had to do more.

I'm just a newbie here, so please excuse my ignorance on the matter.

---

### Post by westie457 on 2014-08-22
Hi
Is one of the packages you installed 'multiarch-support'

---

### Post by dave131 on 2014-08-22
According Synaptic it is installed.  For some reason I was thinking this was part of Ubuntu now anyway, but I guess not.  I have also installed Wine last night and now of course there are the proverbial "ton" of i386 packages installed.  Now I'm really lost! 

Thanks for the help.

---

### Post by dave131 on 2014-08-22
I had read [this thread]("http://stackoverflow.com/questions/23182765/how-to-install-ia32-libs-in-ubuntu-14-04-lts") prior to opening this thread but it just left me confused.  I can't tell if it's just the 3 packages mentioned in the early part of the thread (the ones that includes lcurses or something like that) or if there is a lot more I'm supposed to install.  I also need to keep this as simple as possible - both for me and for anyone who might read the little how to I created ;)  

Is there any tool that can read a .deb and echo out the dependencies?  Would that help for installing what is needed for this?

Thanks for your help.

---

### Post by dave131 on 2014-08-22
I just found [this thread]("http://askubuntu.com/questions/454253/how-to-run-android-sdk-in-ubuntu-64-bits") as well - is it as easy as installing just those 3 packages?

---

### Post by grahammechanical on 2014-08-22
Have you read this?

[https://help.ubuntu.com/community/MultiArch](https://help.ubuntu.com/community/MultiArch)

[http://ubuntuforums.org/showthread.php?t=2183444](http://ubuntuforums.org/showthread.php?t=2183444)

What program do you want to run?

---

### Post by dave131 on 2014-08-22
I've read that, but not sure what to make of it.  Is it saying it's just for Wine, or is that just an example?  It also mentions the ia386-libs, and that's what isn't available now (I'm running 14.04) in Ubuntu - trying to find the quickest way to do this.  The link I posted in my first post shows the package - a 32-bit printer driver.  I found it via [this link]("http://askubuntu.com/questions/71424/how-do-i-get-a-lexmark-x4690-printer-working/514846#514846").  I'm a newbie so I don't understand what it being done in that thread so I followed the link it posted to download the file.  I had done quite a few things leading up to getting that file, so I don't actually know if the 32-bit "stuff" is needed or not now - it was needed to try the old .deb for the installation. 

Thanks for the help.  I'm an newbie so I really don't know what the heck I'm doing! ;)

---

### Post by grahammechanical on 2014-08-22
As far as I can make out the i32-libs package pulled in to very large number of 32bit libraries. The purpose of multiarch is to avoid that happening. Ubuntu 14.04 should have something called mutiarch support. It is a transitional package. What that means I do not know but that mulitarch-support package is, I guess, what is supposed to help run a i386 (32bit) program. Perhaps it pulls in just the i386 libraries that are needed and not a massive number of them.

Printer drivers may be a special case.

Regards

---

### Post by dave131 on 2014-08-22
Thanks.  As per westie457 above I noticed that is installed now also.  Guess I'll just put that in the how to and wait for any comments about something missing.

Thanks everyone.

---

