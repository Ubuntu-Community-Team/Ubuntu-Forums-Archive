---
title: "ubuntu 12 no sound"
date: 2012-07-28
forum: New to Ubuntu
---

### Post by harun3d on 2012-07-28
I have read and done many instructions to get sound working in ubuntu 12 but no result.  I turn back to ubuntu 10.  I hope new updates will make an ubuntu operating system with automatic sound card software finder.

---

### Post by dodo3773 on 2012-07-28
> **harun3d said:**
> I have read and done many instructions to get sound working in ubuntu 12 but no result.  I turn back to ubuntu 10.  I hope new updates will make an ubuntu operating system with automatic sound card software finder.

Do you still have 12.04 installed? Are you asking for help with this post or just complaining? Anyways, I use "alsamixer" to see if my sound card is found. Never really needed much more than that. Are you sure your card wasn't just muted or something? 

Did you try:
```

dmesg | grep -i sound

```
or
```

lspci | grep -i Audio

```

In your post you said that you tried a few things to get your sound working. Could you tell us what they were so maybe we can try and point you in the right direction? Do you know what kind of sound card you have? etc..etc..

---

