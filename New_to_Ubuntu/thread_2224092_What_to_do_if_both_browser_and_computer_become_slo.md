---
title: "What to do if both browser and computer become slow while loading some webpage?"
date: 2014-05-14
forum: New to Ubuntu
---

### Post by arroy_0209 on 2014-05-14
For the first time I faced this problem in my ubuntu12.04 with firefox 29.0: while loading a particular webpage, firefox initially loaded some portion and then practically halted. As I decided to close that particular window loading the webpage, I realized that the mouse along with the desktop icons etc (perhaps the whole OS) have also become very very slow. First of all, I would like to know what might  be the reason for this and second, what should one do in such situation?

Is it possible that this is related to security threats? I have noscript, adblockplus, apparmor and ufw enabled.

---

### Post by HiImTye on 2014-05-14
it's possible that it's a security issue, but more likely a different one.
if you run into it again, go to a terminal and take a look at top or htop. see if there is anything hogging your cpu or ram

---

### Post by arroy_0209 on 2014-05-14
I tried that but opening a new terminal also took a long time, in fact the terminal opened after I succeeded in closing the window. In general I would find what application is taking up lots of cpu and do a kill -9 on that process but in this case as I said opening a terminal is also not fast.

---

### Post by HiImTye on 2014-05-14
use ctrl+alt+f1 to drop to a terminal
use ctrl+alt+f7 to return to the desktop

---

