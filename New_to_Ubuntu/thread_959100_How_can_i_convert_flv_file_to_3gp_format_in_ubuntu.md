---
title: "How can i convert flv file to 3gp format in ubuntu"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by luckydeveloper on 2008-10-26
hi,
 
i have a flv video which i want to put into  my mobile. i want to convert that video into 3gp format. is there any software for my to do that task.

please help
thanks

---

### Post by sleepingdragon on 2008-10-26
Yes, I use Mobile Media Converter. It's a front-end to it's own custom ffmpeg. Nice and easy 3-click process. [You can find it here.]("http://www.miksoft.net/mobileMediaConverter.htm") Go to the bottom of the page and you'll find an Ubuntu .deb package, should be about 4-5Mb to download. You might need to convert the flv into avi first using something like Avidemux, or you can use ffmpeg itself to do the job by calling the command line:

> ffmpeg -i vidfile.flv vidfile.avi

From there, MMC can run the 3gp conversion.

---

### Post by fikelfikel on 2008-10-26
> **sleepingdragon said:**
> Yes, I use Mobile Media Converter. It's a front-end to it's own custom ffmpeg. Nice and easy 3-click process. [You can find it here.]("http://www.miksoft.net/mobileMediaConverter.htm") Go to the bottom of the page and you'll find an Ubuntu .deb package, should be about 4-5Mb to download. You might need to convert the flv into avi first using something like Avidemux, or you can use ffmpeg itself to do the job by calling the command line:

I use the Wine version of Prism, which is good and stable. Google "Prism Media Converter". There is the free version, and the payed version. You'll need Wine.

If that don't work, get Mobile Media Converter, it's also good because it's an official Linux app.

---

### Post by Anghei on 2010-03-18
> **sleepingdragon said:**
> Yes, I use Mobile Media Converter. It's a front-end to it's own custom ffmpeg. Nice and easy 3-click process. [You can find it here.]("http://www.miksoft.net/mobileMediaConverter.htm") Go to the bottom of the page and you'll find an Ubuntu .deb package, should be about 4-5Mb to download. You might need to convert the flv into avi first using something like Avidemux, or you can use ffmpeg itself to do the job by calling the command line:



From there, MMC can run the 3gp conversion.

Where I may found the 64-bits package?!

---

