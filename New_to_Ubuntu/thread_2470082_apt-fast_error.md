---
title: "apt-fast error"
date: 2021-12-19
forum: New to Ubuntu
---

### Post by rburkartjo on 2021-12-19
running 20.04.3

keep getting this error message when running sudo apt-get update

```
Reading package lists... Done
W: Problem unlinking the file partial (copy) - pkgAcquire::Clean (21: Is a directory)
ray@ray-HP-ProBook-640-G1:~$ 
```
this didnt work
A potential solution is to remove the directory /var/cache/apt/archives/apt-fast every time you want to run apt-get clean.

```
$ rm -r /var/cache/apt/archives/apt-fast
```

This also means you are clearing the cache for apt-fast.

---

### Post by DuckHook on 2021-12-19
Though not dealing with your specific issue, my question would be: are you sure you want to continue using apt-fast?

I've seen mirrors desync on more than one occasion. If you are doing an upgrade when that happens, could spell trouble.

I don't use apt-fast, so it's just a shot in the dark, but could this be the result of such a desync?

---

### Post by ActionParsnip on 2021-12-20
If you use apt or apt-get, is it OK?

---

### Post by rburkartjo on 2021-12-20
i can still get updates using either commands and no i dont want to use apt-fast just cant figure out how to unlink

---

### Post by ActionParsnip on 2021-12-20
[https://github.com/ilikenwf/apt-fast/issues/162](https://github.com/ilikenwf/apt-fast/issues/162)

---

### Post by DuckHook on 2021-12-20
> **rburkartjo said:**
> …no i dont want to use apt-fast just cant figure out how to unlink
Have you tried: ```
sudo apt purge apt-fast
``` You could also try ppa-purge if you installed it with a PPA and the usual methods don't work.

---

### Post by rburkartjo on 2021-12-21
tks ya'll but cant fix still get error message. will just live with untill i update to ubuntu 22.04/tks again

---

### Post by rburkartjo on 2021-12-21
figured it out
i just removed the following
 604  sudo rm -rf /var/lib/apt/lists/partial
  605  sudo rm -rf /var/lib/apt/lists/partial(copy)

---

