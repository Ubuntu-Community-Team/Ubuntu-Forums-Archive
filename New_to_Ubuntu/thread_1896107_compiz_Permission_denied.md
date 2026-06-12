---
title: "compiz Permission denied"
date: 2011-12-16
forum: New to Ubuntu
---

### Post by bogdarnet on 2011-12-16
Okay, so I wanted to play a video behind my terminal, and it didn't work when it used to and after googling a bit, I guessed maybe it was because I stopped using compiz after having some trouble with it before, so I thought I'd try compiz again... but when I put 'compiz' at the prompt, I get:

bash: /usr/bin/compiz: Permission denied

Well that's odd, but it should be something google will answer, problem was, it didn't.  I dug a little deeper with 'ls -l /usr/bin/compiz' which showed:

-rw-r--r--

Hmm... all the other programs in bin seem to have 

-rwxr-xr-x

So, is there some reason for this, or should I just change the permissions and run compiz again?

---

### Post by bogdarnet on 2011-12-16
Forgot to mention, I'm on Lucid Lynx 10.04 with dual monitors ...

---

### Post by bogdarnet on 2011-12-16
Okay, no responses, so I went ahead and tried 'chmod a+x /usr/bin/compiz' and then ran 'compiz --replace' which seems to work, although I'm getting a warning about GLX 1.3, then the screen seemed to respond slow to everything which is now better thanks to going to System > Compiz Config Settings, under General > General Options > Display Settings unchecking Detect Refresh Rate and setting the refresh rate below (which was set to 1) to 120 and turning on Sync to VBlank.

If anyone has a similar situation.

---

