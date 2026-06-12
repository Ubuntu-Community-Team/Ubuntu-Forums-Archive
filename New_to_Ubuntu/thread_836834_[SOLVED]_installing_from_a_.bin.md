---
title: "[SOLVED] installing from a .bin"
date: 2008-06-21
forum: New to Ubuntu
---

### Post by 133794m3r on 2008-06-21
Yeah.... I downloaded a .bin from Plane Shift. It was the Linux version. I followed the instructions from here[http://monkeyblog.org/ubuntu/installing/]("http://monkeyblog.org/ubuntu/installing/") and yet I get this error
```
Installer payload initialization failed. This is likely due to an incomplete or corrupt downloaded file.

```
So yeah.... then I go to the site... and try to redownload... it says the file is 261 MB... my .bin is 260.8 so that pisses me off.... somehow it was stopped early by FF.... so yeah... I'd like some help w/ this problem...

---

### Post by Presto123 on 2008-06-21
Maybe you need to extract the file?

Lots of sites seem to round UP to the nearest MB...

---

### Post by 133794m3r on 2008-06-21
wait how'd I extract a binary? and then install?

---

### Post by ibutho on 2008-06-21
Have you tried downloading the file using a download manager like gwget, curl or wget? To run most bin files, you just need to do "chmod +x file.bin" and then "./file.bin" or "sh file.bin".

---

### Post by acidsolution on 2008-06-21
for installing from the bin file u need to change the permission of the file 
```

chmod 777 binfile.bin
and 
./binfile.bin


```
hope 
this may help you

---

### Post by 133794m3r on 2008-06-21
ok I did what you said and it said this
```
PlaneShift-v0.4.00-x86.bin: 1: Syntax error: "(" unexpected 
```

---

### Post by sujoy on 2008-06-21
the file looks to be really corrupt

---

### Post by acidsolution on 2008-06-21
the file must be corrupted try to re-download it and than follow the same instruction.

---

### Post by 133794m3r on 2008-06-21
ok.... well I'll try and thanks for your help thus far....

---

