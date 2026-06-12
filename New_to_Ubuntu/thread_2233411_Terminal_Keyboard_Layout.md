---
title: "Terminal Keyboard Layout"
date: 2014-07-08
forum: New to Ubuntu
---

### Post by noah9 on 2014-07-08
Is there a way that I can change my keyboard input so that when Im normally using Ubuntu its interpreted as cp1251 but when I use terminal the keyboard input is interpreted as UTF 8?

---

### Post by brw2 on 2014-07-08
I remember using the 'loadkeys' command years ago to change the keyboard I was using temporarily.  I haven't used it in a long time but I believe you would simply need to type the following when you started a terminal session: loadkeys -u. To reset it to the default keymap you would type the following: loadkeys -d. I don't remember if this would make a system wide change or if it would limit the change to the terminal window.  My best suggestion would be to give it a try.

---

### Post by noah9 on 2014-07-08
Worked excellently, thank you!

---

