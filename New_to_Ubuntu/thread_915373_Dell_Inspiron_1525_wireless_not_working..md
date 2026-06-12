---
title: "Dell Inspiron 1525 wireless not working."
date: 2008-09-09
forum: New to Ubuntu
---

### Post by Fearthebait on 2008-09-09
Whenever I download the drivers for the card and use ndiswrapper, it says its not a proper .inf file. All the downloads are just .exes so how can i get a "proper .inf" file to use with ndiswrapper?

---

### Post by starcannon on 2008-09-09
Open a terminal

R-click on Desktop and Create Directory for the .exe files to go into

Applications>Accessories>Terminal

```
cd ~/Desktop/Created_Directory
cabextract /path/to/file_name.exe
```

---

### Post by Zippo Master on 2008-09-09
This is the post I followed to get mine to work a while ago.

[http://ubuntuforums.org/showthread.php?t=704088](http://ubuntuforums.org/showthread.php?t=704088)

It's for gutsy but I think it should work for Hardy.  If that is no help I think you can unzip the .exe file in konsole.  If that doesn't work and someone can confirm that it isn't against some rule, I can post the .inf file I used.

---

### Post by Fearthebait on 2008-09-09
I got the following error:

:~/Desktop/Wireless$ cabextract /home/skyler/Drivers/Dell_multi-device_A17_R174291.exe

/home/skyler/Drivers/Dell_multi-device_A17_R174291.exe: no valid cabinets found

All done, errors in processing 1 file(s)
skyler@America:~/Desktop/Wireless$

---

### Post by Fearthebait on 2008-09-09
Alright, i got it now. thanks a bunch guys :)

---

### Post by Zippo Master on 2008-09-09
ok good.

---

### Post by starcannon on 2008-09-09
Grats on solving

ah cool thanks Zippo nice new toy for me to play with.

---

