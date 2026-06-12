---
title: "naming files same as folder name"
date: 2016-01-20
forum: Programming Talk
---

### Post by kervansoft on 2016-01-20
Hi,
I have an ftp folder and people uploading directories included files. I want to write a script that names files same as folder name
example;

folder name is : 800_D1_TOC
file name : 800-d1-tocaree.xcf

I want to change file to 800_D1_TOC with a script

is there any way to do this.

but there are a lot of folders and su folders I want to change names of files with specified folders like

if script see a folder named 800_D1_TOC script will rename the file with the same name of folder

the folders names like;
800_D1_TOC
800_D1_ATA
800_D1_MTN
1800_D2_TOC
1800_D1_ATA
1800_D1_MTN

---

### Post by Vaphell on 2016-01-24
*800_D1_TOC/800-d1-tocaree.xcf* is supposed to become *800_D1_TOC/800_D1_TOC*?

assuming there is only 1 item in a relevant dir

```
dirs=( 800_D1_TOC
         800_D1_ATA
         800_D1_MTN
         1800_D2_TOC
         1800_D1_ATA
         1800_D1_MTN )

for d in "${dirs[@]}"
do
   echo mv "$d"/* "$d/$d"
done
```

---

