---
title: "Trying To Enable Laptop Mode"
date: 2012-01-12
forum: New to Ubuntu
---

### Post by controlled_chaos on 2012-01-12
Hello Ubuntu World! I am new and in need of help!

I just installed Ubuntu on a Lenovo Z470, and I was getting much better battery life with windows 7.
So I have been trying to enable Laptop Mode. Here is what I have been experiencing 

funky@funky-Rev-1-0:~$  /etc/default/acpi-support
bash: /etc/default/acpi-support: Permission denied
funky@funky-Rev-1-0:~$ /etc/laptop-mode/laptop-mode.conf.
bash: /etc/laptop-mode/laptop-mode.conf.: No such file or directory
 Yesterday I was able to get into there and it actually worked but instead of finding
ENABLE_LAPTOP_MODE=false

It said that I needed to install laptop-mode-tools, which I was having trouble doing. But now i can't even get there.
Any Help would be Greatly Appreciated. Other than this I gotta say I am Loving Ubuntu and am Glad to be apart of this Community!

---

### Post by skompier on 2012-01-12
I'm assuming that you want to edit these files. All you're doing is just typing in the PATH to files and not doing anything.

If you want to edit them...try:

```
sudo gedit /etc/default/acpi-support
```

No idea on the Laptop Tools. Someone else will be along shortly, I'm sure.

---

