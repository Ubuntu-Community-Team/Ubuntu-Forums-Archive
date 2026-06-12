---
title: "Android device showing up with much less free space than is."
date: 2013-03-08
forum: New to Ubuntu
---

### Post by irreleventuser on 2013-03-08
So I installed Ubuntu 12.10 yesterday and today I hook up my Samsung Galaxy Nexus with Sprint and running 4.2.2 Jelly Bean with CyanogenMod. In the file manager it shows up saying that there is about 500 megabytes left of open storage but my phone shows much more space, at least 20 gigabytes. How can I fix this? I am unable to copy most of anything to the device, even when I click 'copy anyway' at the prompt dialog.

---

### Post by wayneschutz on 2013-08-05
I'm having the same issue, except with 11.04.  Any thoughts?

---

### Post by BBQdave on 2013-08-05
This information is related to Rhythmbox and portable music players - but it may help with proper data read on your devices:

*If Rhythmbox Music Player does not detect your device as a portable audio player, you can create an empty file named* **.is_audio_player** *at the top level hierarchy of the filesystem of your player.*

I use this with Ubuntu Unity 12.04LTS and it reads my Sansa Clip+ properly - both in Rhythmbox and Nautilus. I am sorry I can not find the links, but I believe others have used this solution on smart phones too.

It may not matter, but my Sansa Clip+ is set to **MSC** mode.

---

