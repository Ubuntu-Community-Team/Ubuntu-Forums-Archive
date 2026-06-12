---
title: "mkisofs command"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by bushu on 2008-05-13
I am working on a project that consists of creating a LiveCd from ubuntu. When I use mkisofs command I get this error message:
mkisofs: Missing pathspec.
Is there anyone with a solution?

---

### Post by Monicker on 2008-05-13
What was the exact syntax that you used?

---

### Post by Oldsoldier2003 on 2008-05-13
> **bushu said:**
> I am working on a project that consists of creating a LiveCd from ubuntu. When I use mkisofs command I get this error message:
mkisofs: Missing pathspec.
Is there anyone with a solution?

if you are following a tutorial that uses a environment variable make sure that the variable is still set. Unless you have added the variable permanently, closing the terminal or running mkisofs from a different terminal will not work because the path will be wrong. to check your environment :

```
env
```

---

### Post by bushu on 2008-05-13
The syntax I used is:
~/livecd/cd# sudo mkisofs -r -V "Ubuntu-Live-Custom" -b ./livecd/cd/isolinux/isolinux.bin -c ./livecd/cd/isolinux/boot.cat -cache-inodes -J -l -no-emul-boot -boot-load-size 4 -boot-info-table -o ./Ubuntu-Live-7.10-custom.iso

---

### Post by Oldsoldier2003 on 2008-05-13
> **bushu said:**
> The syntax I used is:
~/livecd/cd# sudo mkisofs -r -V "Ubuntu-Live-Custom" -b ./livecd/cd/isolinux/isolinux.bin -c ./livecd/cd/isolinux/boot.cat -cache-inodes -J -l -no-emul-boot -boot-load-size 4 -boot-info-table -o ./Ubuntu-Live-7.10-custom.iso

try breaking up the command with the newline delimiter (the  \ symbol) if you are getting a system beep when you paste the command.

---

### Post by bushu on 2008-05-13
I am following a tutorial on this site:
[http://www.debuntu.org/book/export/html/216](http://www.debuntu.org/book/export/html/216)
I think they have not used an env variable

---

### Post by bushu on 2008-05-13
I am going to go through the tutorial again, because I did not go through it at once. I will let you know when i complete. thank you for your support.

---

