---
title: "How do I know if something is a bug (to report)?"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by jsast21 on 2008-05-13
After my screensaver kicks in (or after 5 minutes of inactivity) the screen on my HP TX 1000 laptop (8.04 hardy) flickers and makes the system unusable until you log out (with ctrl-alt-bkspc). Once you log out, the system is back to normal and you can log back in. I have posted to the forums and it looks like no one had an answer. I googled it and found several similar bugs already posted - but nothing is exactly the same. 

As I am only a few months into Ubuntu (Jan 2008) - I'm unsure of how to proceed. I would hate to clog the bug queue with something that is already there - but nothing there is exactly what I am experiencing.

Should I post it? What do they need that will help them proceed?

Thanks for your time.

jsast21

---

### Post by esteckis on 2008-05-13
The first question is, are you using an ATI video card?

---

### Post by jsast21 on 2008-05-13
Could you please tell me how to check? I'm not exactly sure.

Thanks very much.

---

### Post by esteckis on 2008-05-14
Sorry for the delay. Since I am a Linux newb, your easiest way to check is click on System-Administration-Hardware Drivers.  That will show you if you are using any restricted drivers.  If you are using ATI, it will listed there showing a green light  on the right in use.

---

### Post by lswest on 2008-05-14
the output of ```
lspci
``` (lspci==list pci devices) will tell you what make your card is and ```
lshw -C display
``` (lshw=list hardware, -C searches or filters results, display= name of section where graphics cards are listed) will give you more info on your graphics card.

---

