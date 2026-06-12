---
title: "[SOLVED] install deb file"
date: 2008-09-05
forum: New to Ubuntu
---

### Post by celticbhoy on 2008-09-05
Ultra daft question, but how do you install a deb file from the terminal, only ever used package manager before

---

### Post by BGFG on 2008-09-05
I usually just double click the file and have the package manager install it but you should be able to use this command:
```

dpkg -i filename.deb

```

---

### Post by BGFG on 2008-09-05
I usually just double click the file and have the package manager install it but you should be able to use this command:
```

dpkg -i filename.deb

```

Um. could a mod do me a favour and delete this post ? :)

---

### Post by aysiu on 2008-09-05
> **BGFG said:**
> I usually just double click the file and have the package manager install it but you should be able to use this command:
```

dpkg -i filename.deb

```
Isn't it ```
**sudo** dpkg -i *nameofpackage*.deb
```? I usually do ```
sudo dpkg -i *.deb
``` since the folder probably contains only packages I want installed.

---

### Post by celticbhoy on 2008-09-05
Cheers mate

---

### Post by BGFG on 2008-09-05
> **aysiu said:**
> Isn't it ```
**sudo** dpkg -i *nameofpackage*.deb
```? I usually do ```
sudo dpkg -i *.deb
``` since the folder probably contains only packages I want installed.

Indeed it is. Thanks for correction. :)

---

