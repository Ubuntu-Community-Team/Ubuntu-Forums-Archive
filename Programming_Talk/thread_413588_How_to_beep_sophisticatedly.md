---
title: "How to beep sophisticatedly?"
date: 2007-04-19
forum: Programming Talk
---

### Post by flostre on 2007-04-19
Hi.

I am looking for a possibility to beep at different pitches. I know the 'beep' shell command, which issues one beep at a fixed pitch. I remember (back in the good old days :) ) when programming with Pascal under Windows 3.11, I could specify length and pitch. (I even wrote a program which played "Under the sea" by the Beatles *pats own sholder*.) Is this possible somehow under Linux too? Does this depend on the motherboard?

Thanks for your help,

flostre

---

### Post by heimo on 2007-04-19
Maybe you should coordinate with this guy (seems to have similar question)? ;)
[http://ubuntuforums.org/showthread.php?t=412727](http://ubuntuforums.org/showthread.php?t=412727)

Or just:
```
sudo aptitude install beep
man beep

```

---

### Post by ibanezix on 2007-04-19
The beep man page shows that beep does not accept any arguments/parameters, so it's probably not possible to do that with beep.

---

### Post by heimo on 2007-04-19
[http://packages.ubuntulinux.org/edgy/sound/beep](http://packages.ubuntulinux.org/edgy/sound/beep)
>  beep does what you'd expect: it beeps. But unlike printf "\a" beep allows you to control pitch, duration, and repetitions.


---

