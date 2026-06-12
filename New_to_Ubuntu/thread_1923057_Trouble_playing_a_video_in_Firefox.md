---
title: "Trouble playing a video in Firefox"
date: 2012-02-09
forum: New to Ubuntu
---

### Post by KillianO92 on 2012-02-09
Alright, so I have been having trouble playing videos off of wimp.com. So first I searched through the forum trying to find some viable help, but to no avail. So if anyone could help that would be great

---

### Post by shakabra on 2012-02-09
Did you install flash? I used to use flashaid add on for Firefox. It helps resolve dependencies and conflicts then installs the latest flash plugin

---

### Post by KillianO92 on 2012-02-09
Well I have tried to install it a few times and keep getting the error saying that there is an error downloading it. But my internet is fine so I am not sure what is going on.

---

### Post by wolfen69 on 2012-02-09
Go to **get.adobe.com/flashplayer/** and download the .tar.gz file. Right click it and *extract here*. Put the resulting *libflashplayer.so* file into ~/.mozilla/plugins (this means opening your home folder, doing Ctrl-H, and looking for your .mozilla folder. You might have to create the plugins folder. Restart firefox.

---

### Post by KillianO92 on 2012-02-09
Thank you Wolfen, that did the trick. I had downloaded the files for flash-aid but they apparently weren't the right type. I had also tried downloading the same files you had me download but I had selected the YUM option. Thanks again.

---

### Post by lovinglinux on 2012-02-10
There is an issue with Mozilla file right now. Get Flash-Aid from [https://github.com/webgapps/flashaid/downloads](https://github.com/webgapps/flashaid/downloads)

---

### Post by aura7 on 2012-02-10
You can also enable HTML5 video playing ability in certain sites like Youtube. 
[http://www.youtube.com/html5](http://www.youtube.com/html5)

---

