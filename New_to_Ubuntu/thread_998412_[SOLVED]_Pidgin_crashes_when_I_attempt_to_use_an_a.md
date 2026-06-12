---
title: "[SOLVED] Pidgin crashes when I attempt to use an avatar. (2.5.2 in Intrepid)"
date: 2008-11-30
forum: New to Ubuntu
---

### Post by koffeinöverdos on 2008-11-30
I have tried disabling all plugins, and I even wiped all traces of pidgin from my system and re-installed.

I am still an ubuntu noob, so I'm sorry. I started pidgin from the terminal, and when pidgin crashed again, all it says is 'Aborted'. no error description or anything. I can select my avatar file in the file browser, but as soon as i click OK, pidgin immediately shuts down. It doesn't go grayscale and say it's not responding or anything like that. The process just gets immediately killed and it disappears.

I remember this also happening to me in Hardy. I dug around on google for a while and found nobody else with this problem. If somebody would be kind enough to help me, please let me know any other information i should provide. Thank you.

---

### Post by Dr Small on 2008-11-30
Try running pidgin from a terminal to have the STDERR output in the terminal. Open a terminal and run:
```
pidgin
```

Repeat the process, and when pidgin crashes, if it has an error message in the terminal, post it in your thread.

---

### Post by koffeinöverdos on 2008-11-30
> **Dr Small said:**
> Try running pidgin from a terminal to have the STDERR output in the terminal. Open a terminal and run:
```
pidgin
```

Repeat the process, and when pidgin crashes, if it has an error message in the terminal, post it in your thread.

I stated in the original post that i already did this.

It simply says 'Aborted' and nothing else. Have a look

---

### Post by koffeinöverdos on 2008-12-01
Just one 24 hour bump to see if anyone else has any ideas...

---

### Post by koffeinöverdos on 2008-12-05
For anyone who may have this same problem, it appears to be the QQ protocol. Very strange. I tried adding avatars seperately to accounts, and everything was ok until I tried to add an avatar to my QQ account. Exact same crash.

So to circumvent this, i disabled my QQ account, added my avatar (globally, didn't try independently but it might work), and re-enabled my QQ account, and it didn't crash like I was expecting it to.

---

### Post by kevdog on 2008-12-05
What version of pidgin are you using?  Have you tried compiling pidgin from source to circumnavigate the problem?

---

### Post by koffeinöverdos on 2008-12-05
> **kevdog said:**
> What version of pidgin are you using?  Have you tried compiling pidgin from source to circumnavigate the problem?
Pidgin 2.5.2, I didn't think to compile from source, that's a good idea. However, I managed to find a cheap way to fix it for this install and that is good enough for me.

When the next version of Pidgin comes out, if I still get that problem from the .deb install, I will try compiling from source to see how that turns out.

---

