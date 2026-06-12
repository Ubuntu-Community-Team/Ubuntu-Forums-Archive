---
title: "Syndaemon in terminal; &quot;goes away&quot;"
date: 2019-01-06
forum: New to Ubuntu
---

### Post by kiers on 2019-01-06
Hello
how am i supposed to use the "syndaemon" command?

I am trying to get my laptop configured to deactivate the touchpad whilst typing
using > syndaemon -1 1 -m -d -K

in the terminal

However, i find the terminal command prompt "goes away" running syndaemon....the home directory prompt doesn't come back till I "ctrl-C".

is this how it's supposed to work?  how do i get syndaemon settings to stick?

---

### Post by mc4man on 2019-01-07
What version & release of *buntu are you using? (- newer Ubuntu releases are probably using libinput..
If syndaemon is being used it's already running, starting a new process is generally ineffective.

After booting up/logging in run this to see
```
ps axu | grep synd
```

( to use syndaemon without keeping a terminal open you'd need to create a startup app or use a run command (alt+F2

---

