---
title: "installing software Autozen"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by nightware on 2008-06-12
Hello there, this is my first message. I'm here to learn more with you!

The program autozen doesn't have the file "configure". So i did "sudo make install" and appeared something. The program, though, did not install. What do I do?

I'm using Ubuntu 8.04.

link for software:
[http://www.linuxlabs.com/autozen.shtml](http://www.linuxlabs.com/autozen.shtml)

Thanks in advance,
nightware

---

### Post by MmmmJoel on 2008-06-12
You may have better luck trying to install the .deb file available on the website instead of the .tar.gz.

---

### Post by Ripfox on 2008-06-12
Yes the .deb will automatically install upon double click!

---

### Post by nightware on 2008-06-12
Thanks for the answers!

I tried the .deb. It asked for a lib that I don't remember. I installed it. Then it asked for another lib called xlib6g. I downloaded and xlib6g asks for xfree86-common. 

I try to install it xfree86-common from apt-get and it says that it has a replacement called x11-common. Then I type "sudo apt-get install x11-common" and it says "x11-common is already the newest version".

It appears that I reached a non-end problem. I hope no.

What should I do?

thanks!

---

### Post by MmmmJoel on 2008-06-12
Hm. It's a very, very old program that used an old version of the X windowing system when it was called something else. At this point, you would probably have to dive into the code and make a few changes for it to run correctly.

---

### Post by nightware on 2008-06-12
It's strange, because the same program run under Mandriva 2008. What do I need to change in the code?

---

