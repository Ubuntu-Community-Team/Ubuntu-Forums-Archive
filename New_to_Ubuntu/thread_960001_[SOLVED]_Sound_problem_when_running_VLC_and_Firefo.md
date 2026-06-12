---
title: "[SOLVED] Sound problem when running VLC and Firefox"
date: 2008-10-27
forum: New to Ubuntu
---

### Post by Eto_Demerzel on 2008-10-27
I've experienced this problem, it seems like a bug, its repeatable:

1) If I am viewing a video in Firefox (say in Youtube), and I open VLC and try to play a song, VLC gives no sound. The only way to get VLC to play the song is to close that tab in Firefox, and restart VLC.

2) If I open VLC first and play a song, and then try to view a video in Firefox (say in Youtube), the video has no sound now. Further, as long as VLC is running, trying to close Firefox simply causes Firefox to hang.

It seems that the two are competing for the same audio resources, causing this problem. 

Have any of you experienced this? How do I get past this?

Thanks.

---

### Post by bangmalley on 2008-10-27
switch to ALSA
System->Preferences->Sound

do the same thing for VLC too.

---

### Post by kansasnoob on 2008-10-27
If this is 8.04 this guide solved my pulse audio problems:

[http://ubuntuforums.org/showpost.php?p=5587712&postcount=472](http://ubuntuforums.org/showpost.php?p=5587712&postcount=472)

---

### Post by Eto_Demerzel on 2008-10-27
> **bangmalley said:**
> switch to ALSA
System->Preferences->Sound

do the same thing for VLC too.

How do I do the same for VLC? I'm unable to find an option in VLC that asks it to switch it to ALSA.

Thanks.

---

### Post by Eto_Demerzel on 2008-10-27
> **kansasnoob said:**
> If this is 8.04 this guide solved my pulse audio problems:

[http://ubuntuforums.org/showpost.php?p=5587712&postcount=472](http://ubuntuforums.org/showpost.php?p=5587712&postcount=472)

Yeah, I think this is my problem too. I'll try it. Thanks for the link!

---

### Post by hanciong on 2010-10-20
> **kansasnoob said:**
> If this is 8.04 this guide solved my pulse audio problems:

[http://ubuntuforums.org/showpost.php?p=5587712&postcount=472](http://ubuntuforums.org/showpost.php?p=5587712&postcount=472)
Hai.

I am using Lucid Lynx and I am experiencing this problem. In the link that you gave, therre is nothing for Lucid. How to do it in Lucid? thanx

---

