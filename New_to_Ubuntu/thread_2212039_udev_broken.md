---
title: "udev broken"
date: 2014-03-19
forum: New to Ubuntu
---

### Post by ali14 on 2014-03-19
so, i just linked somethings with each other by force(now that i think i dont reall find a reason :mrgreen:)and now my chromium wont load, here's the command i executed

```
sudo ln -sf /lib/x86_64-linux-gnu/libudev.so.1 /lib/x86_64-linux-gnu/libudev.so.0
```

so now when i run chromium (from the terminal) i get this message

"/usr/lib/chromium-browser/chromium-browser: error while loading shared libraries: libudev.so.0: cannot open shared object file: No such file or directory"

so ehm, i googled and well somehow concluded that the problem wont fix by re installing chromium ( even if i am wrong i rather not to ) so, help!!!!!!! ](*,)

---

### Post by sandyd on 2014-03-19
try
```

sudo rm /lib/x86_64-linux-gnu/libudev.so.0
sudo apt-get install --reinstall libudev-dev
```

---

### Post by ali14 on 2014-03-19
nope, didnt work :icon_frown:
i think the file i force linked was linked to something else, and maybe that link is broken?

---

### Post by ali14 on 2014-03-19
just for anyone who ever see's this thread, i solved it, instead of reinstalling libudev-dev i reinstalled libudev0 and everything went back to normal\\:D/
but i dont think we lose anything if we reinstall libudev--dev as well :D

```


sudo rm /lib/x86_64-linux-gnu/libudev.so.0

sudo apt-get install --reinstall libudev0

sudo apt-get install --reinstall libudev-dev


```

---

