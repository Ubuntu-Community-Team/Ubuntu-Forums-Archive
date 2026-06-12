---
title: "Wine + Hardy error"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by piratesmack on 2008-04-25
Hi I just compiled Wine on hardy and I noticed a new error I never got on gutsy
```

steven@steven-desktop:/media/cdrom$ wine setup.exe
preloader: Warning: failed to reserve range 00000000-00010000
preloader: Warning: failed to reserve range 00000000-00010000
preloader: Warning: failed to reserve range 00000000-00010000
preloader: Warning: failed to reserve range 00000000-00010000
preloader: Warning: failed to reserve range 00000000-00010000

```


I have no idea what it means, but is it anything I should worry about?

---

### Post by Saya on 2008-04-25
Usually you don't have to worry about warning or debug messages. It's first when you get "Error" or things don't work you have to start worrying.

---

### Post by piratesmack on 2008-04-25
> **Saya said:**
> Usually you don't have to worry about warning or debug messages. It's first when you get "Error" or things don't work you have to start worrying.

yeah I usually do just ignore them. I was just wondering since I never got this error until I upgraded to gutsy

Thanks

---

### Post by apienk01 on 2008-04-25
Why are you compiling? There is a Wine Ubuntu repo at winehq.org, with packages for 386 and amd64. Look [here]("http://www.winehq.org/site/download-deb").

---

### Post by Google Spider on 2008-04-25
> **apienk01 said:**
> Why are you compiling? There is a Wine Ubuntu repo at winehq.org, with packages for 386 and amd64. Look [here]("http://www.winehq.org/site/download-deb").
He is a damn geek. He must be compiling the latest version not available in the repo.;)

---

### Post by piratesmack on 2008-04-25
> **Google Spider said:**
> He is a damn geek. He must be compiling the latest version not available in the repo.;)

lol no

I compile because I have to apply a patch to the source code to get one of my games working.


I'm one of the maintainers:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=10429]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=10429")

I guess that makes me a damn geek :(

---

### Post by Pete Smith on 2008-04-25
I'm having problems with this. I can't install AutoCAD r14; which is a necessary bit of software for my work. Wine fails with:
```
preloader: Warning: failed to reserve range 00000000-00010000
winevdm: unable to exec 'C:\acad\setup.exe': DOS memory range unavailable
```
I expect this will be fixed with the next release of Wine. But if anyone can offer a work around I'd be most appreciative.

Cheers!

---

### Post by d-mart on 2008-04-26
[http://bugs.winehq.org/show_bug.cgi?id=12516](http://bugs.winehq.org/show_bug.cgi?id=12516)

i followed the steps here it got wine to work.

---

### Post by piratesmack on 2008-04-26
> **d-mart said:**
> [http://bugs.winehq.org/show_bug.cgi?id=12516](http://bugs.winehq.org/show_bug.cgi?id=12516)

i followed the steps here it got wine to work.

awesome thanks

---

