---
title: "Cannot execute binaries (No such file or directory)"
date: 2012-06-08
forum: New to Ubuntu
---

### Post by PianoManEDTA on 2012-06-08
Trying to install Super Meat Boy on a 64 bit Ubuntu (is this even possible?), but when I try to execute the downloaded file I get the following:
```
bash: ./supermeatboy-linux-06072012-bin: No such file or directory

```
I went ahead and made it +rwx for all users (why not?), so ls -lAF gives:
```
-rwxrwxrwx 1 alexander alexander 174416543 Jun  8 13:46 supermeatboy-linux-06072012-bin*
```
echo $PATH gives:
```
/home/alexander/bin:/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:.
```
but, again, we get:
```
alexander@alexander-Inspiron-1545:~/Program Files/SMB$ supermeatboy-linux-06072012-bin 
bash: ./supermeatboy-linux-06072012-bin: No such file or directory
```
Hope that was clear, and my apologies if I'm missing something obvious (is Super Meat Boy compatible with 64bit systems?). Really appreciate any help.

---

### Post by sanderj on 2012-06-08
What does

```
file supermeatboy-linux-06072012-bin

```

say?

---

### Post by PianoManEDTA on 2012-06-18
Mmm this could be the problem:

```
alexander@alexander-Inspiron-1545:~/Program Files/SMB$ file supermeatboy-linux-06072012-bin 
supermeatboy-linux-06072012-bin: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.8, stripped 
```

I downloaded the only available Linux file, maybe there's not a 64-bit version. Thanks for your reply!

---

### Post by oldos2er on 2012-06-18
You might need to install **ia32-libs-multiarch**

---

### Post by PianoManEDTA on 2012-06-19
Ahh, I should've gotten that, that was indeed the problem! Thanks!

---

