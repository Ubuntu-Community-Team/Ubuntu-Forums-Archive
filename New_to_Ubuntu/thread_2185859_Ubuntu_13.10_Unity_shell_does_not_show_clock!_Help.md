---
title: "Ubuntu 13.10 Unity shell does not show clock! Help!"
date: 2013-11-04
forum: New to Ubuntu
---

### Post by MrAutumn on 2013-11-04
Hi.
Im running Ubuntu 13.10 64bit and in Unity the clock doesn't appear in the Desktop upper bar. I tried tweaking the Time  & Date menu in System Settings but it wont let my change anything.
(My god, I feel like my grandmother post this!)

---

### Post by dvdhudson33 on 2013-11-04
Several other threads already about this - sometimes best to look around before posting a question.

I had the problem too - found the fix in [this thread]("http://ubuntuforums.org/showthread.php?t=2183988&highlight=menu+bar+date+time").

David

---

### Post by MrAutumn on 2013-11-05
Got it! 

```
setsid unity
```

Works in Unity, but now I'm having weird issues with Gnome!! :p

---

