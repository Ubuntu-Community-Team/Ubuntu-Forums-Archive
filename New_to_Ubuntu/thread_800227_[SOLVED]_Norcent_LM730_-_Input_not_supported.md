---
title: "[SOLVED] Norcent LM730 - Input not supported"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by pirabu on 2008-05-19
I have a Norcent LM 730 LCD monitor. When I start Ubuntu, the Monitor displays an error message showing "Input not Supported". But when I start in Ubuntu recovery mode it is fine. Any help? I am a beginner.

---

### Post by pirabu on 2008-05-20
thanks a lot for ur help. I figured it out. simply logging in rewcovery mode and chagning the boot resdolution thru Start upo mgr helped.

---

### Post by Maestro23 on 2008-05-20
Please post what you did to resolve the issue(might help someone else) and mark this thread solved.

Thanks. :smile:

---

### Post by pirabu on 2008-05-21
1) Installed the Start up Manger thru Recovery mode. 
2) Changed the Boot Resloution to 10 1024 * 1024

This solved the "Input not supported" issue.

For some reason, the ubuntu installation picked a low resolution in 600s, which was not supported by this SiS Video card.

---

