---
title: "Dual monitor not recognised"
date: 2012-06-09
forum: New to Ubuntu
---

### Post by freshminted on 2012-06-09
I am sure that someone else may have experienced this but I am unable to identify my second monitor. This was fine on 11.10 but isn't operational 12.04lts. My system comprises: HP Pavilion entertainment Entertainment Laptop dv9000 running Ubuntu 12.04 (gnome). The system is hardwired to the modem/router (I cannot get wireless to work) and the monitor is an HP LP2465 using standard monitor cable although both computer and monitor have HDMI connections.
Can any one please suggest a solution? In view of my non technical lack of skill,s a simple non tech response would be helpful.

---

### Post by Senior_Buckethead on 2012-06-11
Have you seen this article?

[http://www.ehow.com/how_5965373_do-work-hp-pavilion-laptop_.html](http://www.ehow.com/how_5965373_do-work-hp-pavilion-laptop_.html)

---

### Post by freshminted on 2012-06-13
Thank you for that tip. Sadly all I succeeded in doing was jumping out of Google and because of my security system, spent an age getting back here!

I do note that it appears as if there simply isn't another monitor plugged in. I should add too that 12.04 is the sole operating system on my laptop - I have no patience with Windows and won't have it anywhere on my machine.

Strangely it was so simple with 11.04 and 11.10 although the HDMI connection never worked!

---

### Post by Jonny87 on 2012-06-19
I to am having this issue, running on an HP Pavilion dv6000. Worked fine from the live CD but not from the actual install. Have tried both varients of the nvidia drivers available in the additional drivers. either one, it still appears that there is no monitor connected. Any help on this would be hugely appreciated.

---

### Post by Nanur on 2012-06-19
What graphics card do you have? (nvidia or amd?)

---

### Post by Jonny87 on 2012-06-19
> **Nanur said:**
> What graphics card do you have? (nvidia or amd?)

I'm using nVidia GeForce 8400M.

---

### Post by cortman on 2012-06-19
You may need the proprietary drivers. First, however, have you tried fixing it with xrandr? If not please post the results of 

```
xrandr
```

Thanks!

---

