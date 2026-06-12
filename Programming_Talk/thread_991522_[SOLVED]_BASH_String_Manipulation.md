---
title: "[SOLVED] BASH String Manipulation"
date: 2008-11-23
forum: Programming Talk
---

### Post by blendmaster on 2008-11-23
Hello!

I'm stuck in the middle of one of my scripts. This is my code:

```
fixed_Artist=${"${album_Data[0]}"//\//-}
```

I'm trying to take the first string in the array album_Data and replace any instance of "/" with "-". However, I keep getting a "bad substitution" error.

What exactly is wrong with my code?

Thanks!

---

### Post by geirha on 2008-11-23
Try with
```
fixed_Artist=${album_Data[0]//\//-}
```

---

### Post by blendmaster on 2008-11-23
> **geirha said:**
> Try with
```
fixed_Artist=${album_Data[0]//\//-}
```

Thanks a ton! :)

I'm still learning BASH concepts, so it's still a little weird to me.

---

