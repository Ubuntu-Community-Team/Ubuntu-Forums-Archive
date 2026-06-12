---
title: "On websites that use Flash I am unable to use microphone of laptop"
date: 2013-08-19
forum: New to Ubuntu
---

### Post by ask_ on 2013-08-19
Hello,

I am using Ubuntu 12.04 . There is a website which helps tune a guitar and it uses Flash. Whenever I try to use that website the flash application loads alright and it asks for permission to use the computer's microphone ,but I am unable to click on 'accept' , the entire browser window becomes unresponsive. This is happening both in Chromium and Firefox. Can you suggest a way to fix this issue ? I am not even sure if it is an Ubuntu issue or a Firefox/chromium issue.

But on the same PC I am running Windows XP as dual boot and Flash is able to access mic properly from Windows XP browsers  -Chrome , Internet Explorer, Firefox.

Thanks.

---

### Post by Vladlenin5000 on 2013-08-20
Is there any reason for not posting the actual website's URL? It might be easier to troubleshoot in the real environment...

---

### Post by SweetAurora on 2013-08-20
OHHHHH..... What you are expireincing is a uncorrectable bug with Compiz. In order to work with the Flash Player dialogue boxes that pop up over an Embedded Flash file, or any flash content for that matter, you have to use a non-compiz based desktop like XFCE, Gnome Shell or Classic, LXDE, ect...

Here's the bug report if intrerested. There are work arounds like change setting in fullscreen flash mode or going to Adobe's html based flash settings page.
[https://bugs.launchpad.net/ubuntu/+source/adobe-flashplugin/+bug/865672](https://bugs.launchpad.net/ubuntu/+source/adobe-flashplugin/+bug/865672)

---

### Post by ask_ on 2013-08-20
> **Vladlenin5000 said:**
> Is there any reason for not posting the actual website's URL? It might be easier to troubleshoot in the real environment...
 Hi Thanks for replying.[http://www.tunerr.com/](http://www.tunerr.com/) . This is the website.

> **SweetAurora said:**
> OHHHHH..... What you are expireincing is a uncorrectable bug with Compiz. In order to work with the Flash Player dialogue boxes that pop up over an Embedded Flash file, or any flash content for that matter, you have to use a non-compiz based desktop like XFCE, Gnome Shell or Classic, LXDE, ect...

Here's the bug report if intrerested. There are work arounds like change setting in fullscreen flash mode or going to Adobe's html based flash settings page.
[https://bugs.launchpad.net/ubuntu/+source/adobe-flashplugin/+bug/865672](https://bugs.launchpad.net/ubuntu/+source/adobe-flashplugin/+bug/865672)


Thanks for the reply. Compiz is having problems in other areas too. Often when I am viewing a youtube video , and I wish to go to full screen mode Compiz sort of crashes. And the lock-screen in Ubuntu appears for a brief while and desktop reappears. But the youtube video window becomes kind of unresponsive. 

I tried the workaround given on the page by going to Adobe's html based flash settings page. And it worked. Thanks again. That solves it.
Actually earlier I  used to use Lubuntu so didn't face any of these problems as it has LXDE as you say.

---

