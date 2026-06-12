---
title: "Skipped &quot;Install third-party software&quot; during installation, can I go back and do it?"
date: 2018-10-16
forum: New to Ubuntu
---

### Post by greda2 on 2018-10-16
As far as I'm aware it would have taken care of graphics and WiFi hardware for me. I skipped it because the guide I was looking at didn't mention it. Any way I can have Ubuntu do this for me after installation?

---

### Post by ajgreeny on 2018-10-16
You may not need to do anything at all because, depending on your hardware, there may be nothing to add.

I use machines with no really newly released hardware, and have always found that the integrated graphics are fully working from the start; similarly the wifi has always been found and connects without a problem.

Are you having any difficulties with either graphics or wifi?
What hardware do you have?
Show us the output of terminal command ```
inxi -F
``` which will give us a lot of info about your hardware specs.
Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

---

### Post by oldos2er on 2018-10-16
Check 'Additional Drivers' to see if any proprietary software is available for your devices.

---

