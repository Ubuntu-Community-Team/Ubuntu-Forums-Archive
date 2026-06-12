---
title: "Adobe- can't download it"
date: 2013-01-18
forum: New to Ubuntu
---

### Post by Mayasilal on 2013-01-18
why I can't download adobe flash player? I can not watch one tv show,  what the PROBLEM?? I need a solution as soon as possible. thanks dudes :D

---

### Post by BlinkinCat on 2013-01-18
Hi,

I assume you have taken note of info in this guide -

[https://help.ubuntu.com/community/RestrictedFormats/Flash](https://help.ubuntu.com/community/RestrictedFormats/Flash)

No need to swear by the way.

Cheers - :)

---

### Post by squakie on 2013-01-18
Read the forum rules of conduct - your language is not allowed nor appreciated.  As for your problem, please remember it's a volunteer forum and while everyone needs "a solution as soon as possible", it will only come in it's time.  

As for your problem:

- did you install the ubuntu-restricted-extras package?

Trying to download directly from Adobe would probably be, at best, an "experience".

---

### Post by ibjsb4 on 2013-01-18
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by Mayasilal on 2013-01-29
> **squakie said:**
> Read the forum rules of conduct - your language is not allowed nor appreciated.  As for your problem, please remember it's a volunteer forum and while everyone needs "a solution as soon as possible", it will only come in it's time.  

As for your problem:

- did you install the ubuntu-restricted-extras package?

Trying to download directly from Adobe would probably be, at best, an "experience".

hey i installed ubuntu-restricted-extras package. now what should I do  ?:)

---

### Post by frank604 on 2013-01-29
Does flash work now?

If not:
Which browser are you using?
What is the website you are trying to watch video in flash?

---

### Post by Mayasilal on 2013-02-02
> **frank604 said:**
> Does flash work now?

If not:
Which browser are you using?
What is the website you are trying to watch video in flash?


---> flash doesn't work... I am using firefox.
[www.natabanu.com](www.natabanu.com)
and some others for watching online movies.

---

### Post by arpanaut on 2013-02-02
If you have an old processor that does not support sse2 then the newer flash will not work.

In a terminal (ctrl+alt+t)  copy and paste ```
cat /proc/cpuinfo
```and then post the output of that command here.

If your cpu does not support sse2 then you may need to install an older version of flash for it to work.

---

