---
title: "How to disable compiz...?"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by AstralliS on 2008-05-18
I have problem with compiz and I decided to disable that for a while, so could you say me how to do that? I want completely disable it (remove from start-up list).

---

### Post by diablo75 on 2008-05-18
Open System>Preferences>Appearence

Then click on the Effects tab, and select None.

---

### Post by Tomatz on 2008-05-18
Just disabling it in *system, preferences, appearence* should do the trick.

You could uninstall it with this command:

```
sudo apt-get remove compiz
```

---

### Post by Joeb454 on 2008-05-18
> **Tomatz said:**
> Just disabling it in *system, preferences, appearence* should do the trick.

You could uninstall it with this command:

```
sudo apt-get remove compiz
```

Both true, though if you really want to rid yourself of it, then ```
sudo apt-get purge compiz
``` might be more your style ;)

---

### Post by AstralliS on 2008-05-18
> **Tomatz said:**
> Just disabling it in *system, preferences, appearence* should do the trick.

You could uninstall it with this command:

```
sudo apt-get remove compiz
```

I don't wanna to remove that, just to disable. But I don't see the way how to do that in system >> preferences >> appearance...

---

### Post by AstralliS on 2008-05-18
> **Joeb454 said:**
> Both true, though if you really want to rid yourself of it, then ```
sudo apt-get purge compiz
``` might be more your style ;)

Here's what I got:

```
astrallis@astrallis-desktop:~$ sudo apt-get purge compiz
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package compiz is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 130 not upgraded.
```

---

### Post by Tomatz on 2008-05-18
> **AstralliS said:**
> Here's what I got:

```
astrallis@astrallis-desktop:~$ sudo apt-get purge compiz
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package compiz is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 130 not upgraded.
```

Its not installed?

Did you have desktop effects? E.g. minimise effect, nice viewport switching or a cube

---

### Post by AstralliS on 2008-05-18
> **Tomatz said:**
> Its not installed?

Did you have desktop effects? E.g. minimise effect, nice viewport switching or a cube

I cannot see my Title bar and window-borders. Yes, I have some of effects, including minimize/cube effect...

---

### Post by steveneddy on 2008-05-18
> **diablo75 said:**
> Open System>Preferences>Appearence

Then click on the [COLOR="Red"]**Visual Effects**[/COLOR] tab, and select None.

This will disable it and it won't startup.

If it starts when you boot, go into 

System --> Preferences --> Sessions

and un-check it from the list.

---

### Post by AstralliS on 2008-05-18
Thanks.

I don't know is there someone which has not problems with Compiz or Emerald, but my opinion is that that simply cannot work properly.

---

### Post by aznpower8 on 2008-05-18
> **diablo75 said:**
> Open System>Preferences>Appearence

Then click on the Effects tab, and select None.

yea but that will totally erase my effects i (me and him have the same problem) just want the title bar back, but i still want the effects

---

