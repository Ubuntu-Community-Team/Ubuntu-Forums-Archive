---
title: "installing fonts"
date: 2008-10-06
forum: New to Ubuntu
---

### Post by ja660k on 2008-10-06
hey guys, is there any way to install fonts on ubuntu?
can someone please tell me  which directory the fonts go in?

can anyone help?

---

### Post by talsemgeest on 2008-10-06
It depends what kind of fonts you want. There are msttfonts in the repositories ( the fonts you would get for windows).

---

### Post by Elfy on 2008-10-06
I put my fonts into a directory in my home - it has to be hidden

```
mkdir .fonts
```

The . makes it a hidden folder, in nautilus Ctrl+H to view hidden files/folders. Once fonts have benn installed ot the folder run

```
sudo fc-cache -fv
```

As talsemgeest says you can install from the repo - but if you have windows, you can do as I did and copy the fonts from windows onto a stick and then into the .fonts

---

### Post by Idefix82 on 2008-10-06
If you open Synaptic and search for "fonts" you will be able to get thousands and thousands of fonts within a couple of minutes (depending on your download speed).

---

### Post by halitech on 2008-10-06
> **forestpixie said:**
> I put my fonts into a directory in my home - it has to be hidden

```
mkdir .fonts
```

The . makes it a hidden folder, in nautilus Ctrl+H to view hidden files/folders. Once fonts have benn installed ot the folder run

+1 this is the way I do it as well so it gets included in any backups I do

> ```
sudo fc-cache -fv
```

never had to do that in order to get mine to show up, not saying its not the correct thing to do, just haven't had to myself

---

### Post by Elfy on 2008-10-06
> just haven't had to myselfIt might well be that you don't need to - it's something I always did :)

---

### Post by halitech on 2008-10-06
probably better to be safe then sorry :)

---

