---
title: "How to allow microphone on a site?"
date: 2012-04-27
forum: New to Ubuntu
---

### Post by emrextreme on 2012-04-27
There's a guitar tuner site that i use on windows which is;

[http://www.proguitartuner.com/guitar-tuner/](http://www.proguitartuner.com/guitar-tuner/)

The site asks to allow camera and mic but i can't choose yes or no. It just stuck. How can i get this work?

Ubuntu 12.04 Chromium

---

### Post by calavier62 on 2012-04-27
Hello emrextreme.

I checked out the guitar tuning site that you wanted to allow access to your microphone with, and I could not get the controls to work either. This would most likely be due to a bug in Adobe Flash, and unfortunately, Adobe isn't the best by any means when it comes to updating their Linux compatible software. And what's worse is that all of the flash alternatives are only for playing videos and music. Not sending it.

Here's a few things that I might try:
1) check out different web browsers. Chromium (Google Chrome for Linux), and Opera are really popular. ***edit: I just saw that you run chromium***

2) The version of Firefox that ships with Ubuntu is packaged by Canonical, and I'd imagine that a few things have been changed. Download the latest official build of Firefox off of Mozilla's website, and run it (It should download as a simple tar or zip file, so all you have to do is unpack it, and run the file named "firefox". Keep in mind that this WILL NOT replace any existing binaries, and is kind of a ...portable? install. Thus, it runs in a folder that can be located in your home partition. 

3) If none of the above works, download an application known as Wine from the Software Centre. Then, download the **Windows** version of Firefox, and run it. Keep in mind that you will need to download a Windows version of flash to go with the windows version of Firefox, because Wine runs in a "sandbox" environment. 

If you need tutorials on any of the above, please let me know, and I'd be more then happy to help you.

---

### Post by lechien73 on 2012-04-27
I've encountered this issue before and, although I've seen many fixes, the only way I've been able to solve the problem is by going here:

[http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager06.html](http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager06.html)

Click on the **[www.proguitartuner.com](www.proguitartuner.com) website**, and then click **Always Allow**

Restart your browser, and the site should stop asking you for access to the microphone and should now just work.

---

