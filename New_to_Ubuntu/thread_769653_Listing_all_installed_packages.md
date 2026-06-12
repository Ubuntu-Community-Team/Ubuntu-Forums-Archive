---
title: "Listing all installed packages?"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by Jim Shunamon on 2008-04-26
Does anyone know how I can generate a list of all the packages that I have installed and then save it into a text file? I know how to do it in openSUSE, but as that uses RPM as its package management system the commands will not work here in Ubuntu.
Any help will be appreciated. :) :)

---

### Post by LaRoza on 2008-04-26
```

dpkg --get-selections > saveas.text

```

---

### Post by hackle577 on 2008-04-26
```
dpkg --get-selections > ~/packages.txt
```

EDIT: Bwahaha, I beat LaRoza to it! I feel so.... leet!

EDIT 2: Oh that is cheating!

---

### Post by Jim Shunamon on 2008-04-26
Wow! That was quick :)
Thank you both so much, it worked perfectly.

---

### Post by LaRoza on 2008-04-26
> **hackle577 said:**
> ```
dpkg --get-selections > ~/packages.txt
```

EDIT: Bwahaha, I beat LaRoza to it! I feel so.... leet!

EDIT 2: Oh that is cheating!

I didn't see your post when I edited, sorry.

---

### Post by hackle577 on 2008-04-26
I don't blame you, it's a hectic night in ABT. :)

---

### Post by LaRoza on 2008-04-26
> **hackle577 said:**
> I don't blame you, it's a hectic night in ABT. :)

I feel guilty. Everything works fine for me!

(Or at least, I knew exactly what to do and it didn't matter configuring...)

---

