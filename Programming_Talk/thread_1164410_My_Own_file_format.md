---
title: "My Own file format"
date: 2009-05-19
forum: Programming Talk
---

### Post by rulk88 on 2009-05-19
I'm a game developer and I have custom file format for in-game animation, also i have editor for it. Is there a way to assosiate this file format with the editor?

---

### Post by simeon87 on 2009-05-19
Right-click the file > Properties > Open With. Then add the editor here.

---

### Post by rulk88 on 2009-05-19
Is there a way to do it not using GUI? From a program or command line?

---

### Post by nvteighen on 2009-05-19
Hmm... I guess there has to be a way to set this through some script executed while installing a .deb package... or your target DE's API should have some way to do it?

---

### Post by Ferrat on 2009-05-20
> **rulk88 said:**
> Is there a way to do it not using GUI? From a program or command line?

```
cd /proc/sys/fs/binfmt_misc

echo ‘:MyFileExtentionName:E::MyFileExtention::/the/path/to/theprogram/Iwantto/registeritWith:’ > register
```



You have to sudo it possibly. 

So ex. if you want text files to register with vim you would do 

```
echo ":text:E::txt::/bin/vi:" > register
```

---

