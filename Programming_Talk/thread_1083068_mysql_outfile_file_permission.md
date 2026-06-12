---
title: "mysql outfile file permission"
date: 2009-02-28
forum: Programming Talk
---

### Post by badperson on 2009-02-28
Hi,
I was trying to write a search query to an outfile, but got this message:

> ERROR 1 (HY000): Can't create/write to file '/home/jason/test.csv' (Errcode: 13

I can write to /tmp/filename, but no other directory. 
I did a chmod to 777 for the dir I wanted to write to, but it still didn't work. 

Do you know how to do that? 
thanks, 
bp

---

### Post by badperson on 2009-03-02
bump?? ...hope that's ok...

---

### Post by unutbu on 2009-03-02
Ubuntu's mysql ships with apparmor. This means that the directories that mysql can read and write to are restricted. To get it to write to /home/jason, you'll need to edit /etc/apparmor.d/usr.sbin.mysqld and perhaps add something like
```

  /home/jason/ r,
  /home/jason/** rwk,
```

(See [http://ubuntuforums.org/showthread.php?p=6353900#post6353900](http://ubuntuforums.org/showthread.php?p=6353900#post6353900) for info on apparmor)

---

### Post by badperson on 2009-03-02
thanks!
bp

---

