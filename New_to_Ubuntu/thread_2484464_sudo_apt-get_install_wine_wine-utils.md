---
title: "sudo apt-get install wine wine-utils"
date: 2023-02-27
forum: New to Ubuntu
---

### Post by thegeicogecko on 2023-02-27
I did sudo apt-get install wine wine-utils, and it gave the error message "E: Unable to locate package wine-utils". How do I fix this?

---

### Post by guiverc on 2023-02-27
We have no idea what OS/product/release you're using, thus are very limited to how we respond.

A quick look at what packages it's available on my own system shows

```
guiverc@d7050-next:~/uwn/issues/776$   rmadison wine-utils
guiverc@d7050-next:~/uwn/issues/776$   apt-cache search wine-utils
guiverc@d7050-next:~/uwn/issues/776$
```

no results, but as I don't know what you're actually looking for, and particularly not your OS/product/release details I can't explore further or provide specific advice anyway.

*ps:  I'm using Ubuntu lunar (Lubuntu actually), which is why I used `rmadison` which will look at releases beyond my own, you didn't provide release details so I can't narrow search to your specific release.*

Maybe this is useful; alas I don't know what you're looking for...

```
guiverc@d7050-next:~/uwn/issues/776$   apt-cache search wine |grep utils
winpr-utils - Windows Portable Runtime library command line utilities
```

---

### Post by Impavidus on 2023-02-28
According to [https://packages.ubuntu.com/](https://packages.ubuntu.com/), there's no package named wine-utils in any official and supported Ubuntu repository. Are you using some guide that tells you to install that package? It could be outdated or wrong. I never used wine myself.

---

### Post by ActionParsnip on 2023-02-28
What are you trying to do? There is no "wine-utils" package which is why you can't find it :)

---

### Post by MAFoElffen on 2023-02-28
The only thing I see for 'wine-utils' is this (which is not an Ubuntu Package at all): [https://github.com/scivision/wine-utils](https://github.com/scivision/wine-utils)

...which is short-cuts for MS Office installed in Wine (Linux).

---

