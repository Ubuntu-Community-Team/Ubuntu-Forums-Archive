---
title: "Linking Apache and MySQL from Windows and Ubuntu"
date: 2007-07-01
forum: Programming Talk
---

### Post by turezky on 2007-07-01
Heya everyone!
Got the following question regarding linking the web-servers from Windows and Ubuntu:
_Preambula:_
I was using MySQL under Windows as a part of Denwer Project (russian-tailored PHP-Apache-MySQL bundle). It was using the 4th version of MySQL.
After installing Ubuntu I downloaded a newer, 5th version of MySQL.
_Ambula:_
Now, when I'm using both OS, I'm concerned about continuing my work with the websites. However the files for sites and DBs remain on NTFS partitions. The last thing I want to do is to copy the database and PHP files from Windows partitions and thus duplicating both the code and DB.
_Question:_
Is there any way to mount these folders under Ubuntu, so that Apache and MySQL both from Windows and Ubuntu would use the same files.

Hope my question would is understandably clear :)

---

### Post by brooksbp on 2007-07-01
You can only boot into one OS.  You can't boot into Ubuntu and use a mysql database in your windows partition.

To make your job much simpler... copy the apache configuration files to your Ubuntu apache and same with mysql.

---

### Post by turezky on 2007-07-01
Why not?
Isn't it that everything is just a file...
And it is not a configuration I'm talking about.(It would be really simple..). I just want to use the same DB and code under the Ubuntu. It is much easier with PHP codes, since the folder with the codes can simply be mounted. The problem consists with the database... I just want to mount the folder with the data from Windows server to MySQL installed on Ubuntu. Is this somehow possible?

---

### Post by brooksbp on 2007-07-01
you want to run a MySQL daemon under Unbuntu using configs, data, etc from a windows partition?

If so, unlikely... just transfer the windows DB to your ubuntu DB... keep it simple... work with something you know works

---

### Post by turezky on 2007-07-01
Hmmm, that is not what I was actually talking about.. This copy-paste stuff becomes a kind of disturbing with time... I use both OS for developing sites (I just can't give up Dreamweaver..), but most of the time I use Ubuntu. So in order to avoid every-time copying of the DB from Windows to Ubuntu and vice-versa i just want both OS to **share** it. Yes, it is not the way I know it works.. Well,actually this is basically why I turned to this forum :D

---

### Post by brooksbp on 2007-07-02
It seems like you're seeking out a much more complicated solution than need be.  It *might* be possible to mount database files from other partitions like you'd want to, but there are a lot of issues with that in terms of cross-platform issues and I'm not positive you can copy databases by mounting files like that.

Why don't you just install Dreamweaver under Wine and all problems are solved?  Or you could use two machines, Ubuntu machine as a server and Windows machine as a dev machine.

---

### Post by pmasiar on 2007-07-02
ntfs is readable under Linux, but write support is only experimental. you know, no documentation, so it's not like Ubuntu is against sharing, but to share you need to parties. :-)

IMHO you are much safer off to copy files under Linux if you want to write to them.

---

