---
title: "[SOLVED] Eclipse"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by Inxsible on 2008-06-16
I downloaded and extracted the x_86 version of the latest Eclipse from their website on my Debian.

However, when I try to start eclipse it gives me permission errors. So I tried to start it being root. Still the same error. Then I tried changing the permissions on the file using chmod 775 and when that didn't work i tried chmod 777. 

Still, I get the same errors. Unfortunately, I am at work now, so I don't remember the exact error but it simply gave the path of the executable and then permission denied
```
/media/WD500/Eclipse/eclipse: Permission denied
```Can someone point out if I am doing anything wrong?

I extracted it to my external hard drive..so I could use the same profile and workspace from my fluxbox or xfce dual boot.

---

### Post by Joeb454 on 2008-06-16
Do you have to compile and install it, or is it like Firefox where you just run the file?

---

### Post by Sinkingships7 on 2008-06-16
Try giving yourself 755 permissions on that external drive. That said, I don't know for sure if you can install and run things on external drives as easily as you can from the filesystem.

---

### Post by Inxsible on 2008-06-16
> **Joeb454 said:**
> Do you have to compile and install it, or is it like Firefox where you just run the file?No. Its just a tar.gz which we have to extract. 

> **Sinkingships7 said:**
> Try giving yourself 755 permissions on that external drive. That said, I don't know for sure if you can install and run things on external drives as easily as you can from the filesystem.I do have 755 on that drive as well.

I have done this before in an Ubuntu Gnome install. All I did was extract it and use the file to start it. Now it doesn't seem to wanna work.

---

