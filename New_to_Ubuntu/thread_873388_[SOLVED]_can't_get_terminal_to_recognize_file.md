---
title: "[SOLVED] can't get terminal to recognize file"
date: 2008-07-28
forum: New to Ubuntu
---

### Post by harryliddic on 2008-07-28
Trying to compile a program that sits on my desktop but terminal keeps refusing to see it


harry@harry-desktop:~$ cd /dvsub-0.3
bash: cd: /dvsub-0.3: No such file or directory
harry@harry-desktop:~$ cd dvsub-0.3
bash: cd: dvsub-0.3: No such file or directory
harry@harry-desktop:~$ dvsub-0.3
bash: dvsub-0.3: command not found
harry@harry-desktop:~$ 

what am I missing?

---

### Post by wannadumpwindows on 2008-07-28
```
cd /desktop/dvsub-0.3
```

---

### Post by mgranet on 2008-07-28
Use 'ls' to list the contents of your current directory. Then you can 'cd *directory*' to move about.

---

### Post by iaculallad on 2008-07-29
On your terminal:

```
cd ~/Desktop
```

and issue ls

```
ls -l
```

---

### Post by harryliddic on 2008-07-29
harry@harry-desktop:~$ cd /desktop/dv2sub-0.3
bash: cd: /desktop/dv2sub-0.3: No such file or directory
harry@harry-desktop:~$

---

### Post by wannadumpwindows on 2008-07-29
> **harryliddic said:**
> harry@harry-desktop:~$ cd /desktop/dv2sub-0.3
bash: cd: /desktop/dv2sub-0.3: No such file or directory
harry@harry-desktop:~$

Sorry, the "D" in "desktop" should be a capital:

```
cd /Desktop/dv2sub-0.3
```

---

### Post by harryliddic on 2008-07-29
-rw-r--r--  1 harry harry     4693 2007-10-08 02:49 catalogmanager.desktop
drwxr-xr-x  3 harry harry     4096 2008-03-11 02:25 com
-rw-r--r--  1 harry harry     1223 2007-10-12 08:10 d3lphin.desktop
drwxr-xr-x  3 harry harry     4096 2005-11-24 12:15 doc
drwxrwsrwx  6 harry harry     4096 2008-01-14 01:44 dv2sub-0.3
drwxrwxrwx  4 harry harry     4096 2005-05-24 20:18 dvtitler-0.2.0
drwxr-xr-x  8 harry harry     4096 2008-04-07 09:39 easyeclipse-desktop-java-1.3.1
it shows that it is there

---

### Post by harryliddic on 2008-07-29
harry@harry-desktop:~/Desktop$ cd /Desktop/dv2sub-0.3
bash: cd: /Desktop/dv2sub-0.3: No such file or directory
harry@harry-desktop:~/Desktop$

---

### Post by Mister.Vash on 2008-07-29
```
cd ~/Desktop/dv2sub-0.3
```

---

### Post by wannadumpwindows on 2008-07-29
> **harryliddic said:**
> harry@harry-desktop:~/Desktop$ cd /Desktop/dv2sub-0.3
bash: cd: /Desktop/dv2sub-0.3: No such file or directory
harry@harry-desktop:~/Desktop$

At that prompt, you're already in the Desktop directory. Notice your prompt:

harry@harry-desktop:**~/Desktop**$

---

