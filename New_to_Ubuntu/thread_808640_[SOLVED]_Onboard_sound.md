---
title: "[SOLVED] Onboard sound"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by JimmyJim on 2008-05-26
Hello,

I'm trying to get onboard sound to work due to Creative's poor Linux support. I went to the BIOS (for my Asus A8N SLi Premium) and enabled AC97 sound and saved. I rebooted and there still isn't any sound. What could be wrong?

Thanks

---

### Post by ardvark71 on 2008-05-26
> **JimmyJim said:**
> Hello,

I'm trying to get onboard sound to work due to Creative's poor Linux support. I went to the BIOS (for my Asus A8N SLi Premium) and enabled AC97 sound and saved. I rebooted and there still isn't any sound. What could be wrong?

Thanks

Hi...

What is the chipset, specifically? If it's an X-Fi, this thread may be of help...

[http://ubuntuforums.org/showthread.php?t=239981](http://ubuntuforums.org/showthread.php?t=239981)

Hope this helps...:)

Best Regards...

---

### Post by JimmyJim on 2008-05-26
> **ardvark71 said:**
> Hi...

What is the chipset, specifically? If it's an X-Fi, this thread may be of help...

[http://ubuntuforums.org/showthread.php?t=239981](http://ubuntuforums.org/showthread.php?t=239981)

Hope this helps...:)

Best Regards...

It is X-Fi (XtremeMusic to be specific). I'll check out that thread. Thanks.

---

### Post by Happy_Man on 2008-05-26
Interesting... I have Creative sound and it has always worked fine for me.

---

### Post by OpposingForce on 2008-05-26
> **Happy_Man said:**
> Interesting... I have Creative sound and it has always worked fine for me.

It's probably an Audigy or older.  Linux support is poor with the xfi because it uses a completely new and different chipset.  Meaning basically that anyone with the card is screwed (well there's a workaround..OSS4, but I've been having some trouble with it).  But I just read on the ALSA site that Creative has supplied the alsa team with data sheets so hopefully ALSA will be fully supporting the xfi soon.

---

### Post by JimmyJim on 2008-05-26
> **ardvark71 said:**
> Hi...

What is the chipset, specifically? If it's an X-Fi, this thread may be of help...

[http://ubuntuforums.org/showthread.php?t=239981](http://ubuntuforums.org/showthread.php?t=239981)

Hope this helps...:)

Best Regards...

I tried that method and I'm still getting beeps from my motherboard rather than sound. I tried the ossdetect -v and ossinfo and it gives all the info for my sound card. Does something else have to be configured? I don't see what I'm doing wrong here.

Thanks again.

---

### Post by ardvark71 on 2008-05-27
> **JimmyJim said:**
> I tried that method and I'm still getting beeps from my motherboard rather than sound. I tried the ossdetect -v and ossinfo and it gives all the info for my sound card. Does something else have to be configured? I don't see what I'm doing wrong here.

Thanks again.

Hi...

From the link I gave, it appears that getting your chipset to work is a hit and miss proposition. :(

Have you tried any of the drivers mentioned?

[http://www.opensound.com/download.cgi](http://www.opensound.com/download.cgi)

[http://ca.creative.com/support/downloads/download.asp?MainCategory=209&nRegionFK=&nCountryFK=&nLanguageFK=&sOSName=Linux&region=1&Product_Name=Sound+Blaster+X-Fi+Fatal1ty&Product_ID=14000&modelnumber=&driverlang=1033&OS=12&drivertype=0&x=22&y=11](http://ca.creative.com/support/downloads/download.asp?MainCategory=209&nRegionFK=&nCountryFK=&nLanguageFK=&sOSName=Linux&region=1&Product_Name=Sound+Blaster+X-Fi+Fatal1ty&Product_ID=14000&modelnumber=&driverlang=1033&OS=12&drivertype=0&x=22&y=11)

Best Regards...

---

