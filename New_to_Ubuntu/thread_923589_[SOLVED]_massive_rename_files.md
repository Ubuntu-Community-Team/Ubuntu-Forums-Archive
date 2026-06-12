---
title: "[SOLVED] massive rename files"
date: 2008-09-18
forum: New to Ubuntu
---

### Post by zetjee on 2008-09-18
Hi there,

I had my terminal resize a lot of pictures which where in medium size to thumbnails.

My medium files start with mo_ and my thumbs with th_

Now my thumbnails are starting with th_mo_filename.jpg

Is it possible to remove the mo_? 

Thanks in advance!

(i'm sorry for my english, still practicing.)

---

### Post by bikerider42 on 2008-09-18
get metamorphose from getdeb.net will do all of it....

---

### Post by vikram on 2008-09-18
Get Krename from the repos. 

[http://www.krename.net/](http://www.krename.net/)

---

### Post by jken146 on 2008-09-18
Or thunar's bulk rename... in the repos too.

---

### Post by Mornedhel on 2008-09-18
Or use rename, it's already installed.

rename -n 's/mo_//' *.jpg

Note the -n that ensures no file will actually be renamed, but instead show what files would have been renamed and how. Run the same command without -n once you are sure it does what you expect.

---

### Post by ghostdog74 on 2008-09-18
> **zetjee said:**
> Hi there,

I had my terminal resize a lot of pictures which where in medium size to thumbnails.

My medium files start with mo_ and my thumbs with th_

Now my thumbnails are starting with th_mo_filename.jpg

Is it possible to remove the mo_? 

Thanks in advance!

(i'm sorry for my english, still practicing.)

you can use the script [here](http://www.linuxquestions.org/linux/blog/ghostdog74/2008-09-17/Simple_Mass_File_Renamer_Deleter_Python)
eg usage:
```

./filerenamer.py -p "mo_" -e "" -l "th_mo*jpg" #use -l to list files to be changed only
./filerenamer.py -p "mo_" -e "" "th_mo*jpg" #remove -l to commit

```
or if you want to learn how to do it
```

for files in th_mo*
do  
   mv "$files" ${files/mo_/}
done

```

---

