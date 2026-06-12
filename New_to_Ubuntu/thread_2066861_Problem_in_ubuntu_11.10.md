---
title: "Problem in ubuntu 11.10"
date: 2012-10-05
forum: New to Ubuntu
---

### Post by Raafat1991 on 2012-10-05
Hi my problem is as following:

I have been deleted a video file...the problem is : when i search for any file the video flie have been deleted appears in search results !!!


what can I do about this problem ?


Note:my english language  is very weak ,so i'm sorry if you exist any error(i expect that;))*_*.

Raafat;)

---

### Post by NikTh on 2012-10-05
Hi , 
you can check the trash and see if file is there. 

Thanks

---

### Post by getThem_robots on 2012-10-05
Raafat,

Not sure what your problem is :(. Sorry.
Can you answer the following questions:

Did you delete the video file yourself?
(yes/no)

Are you looking for the file (do you need it)?
(yes/no)

Did you delete it and you still see it in search results?
(yes/no). If yes, how did you delete it (command line or just moved to trash)?

Thanks,
-MO

---

### Post by newb85 on 2012-10-05
Have you rebooted since deleting the file?  It's a known bug in zeitgeist that the file isn't removed from the log until reboot.

---

### Post by Raafat1991 on 2012-10-06
My brother newb85: yes i reboot my laptop multiple times but the same problem is still existing.



My brother getThem_robots for your questions:

the first : yes

the second : no

the third : yes, i deleted it the way right-click on  a video file and i go to delete option and i click on it and after that i go to trash and empty the trash

---

### Post by Raafat1991 on 2012-10-07
Please help me *_*

---

### Post by The Cog on 2012-10-07
As I understand it, Raafat1991 has deleted a file, but the file still appears in search results. Raafat1991, pleaase correct me if I am wrong.

What you expect to happen is that the file no longer appears in search results, because it no longer exists.

I know there is a database of all files, that is used by search programs because this is faster than actually searching through the disks. I am guessing that whatever search method you are using is looking in this database. This database is normally updated daily, so the file probably no longer appears in the search results now. But if it stull does, try this command, and then try the search again:
```
sudo updatedb
```

---

### Post by Raafat1991 on 2012-10-21
[CENTER][COLOR=Indigo]> **The Cog said:**
> As I understand it, Raafat1991 has deleted a file, but the file still appears in search results. Raafat1991, pleaase correct me if I am wrong.

What you expect to happen is that the file no longer appears in search results, because it no longer exists.

I know there is a database of all files, that is used by search programs because this is faster than actually searching through the disks. I am guessing that whatever search method you are using is looking in this database. This database is normally updated daily, so the file probably no longer appears in the search results now. But if it stull does, try this command, and then try the search again:
```
sudo updatedb
```

[COLOR=Blue]
Hi ,I did what you was posted but the same problem appears

Thank you for interaction 
[/COLOR][/COLOR][/CENTER]

---

### Post by Raafat1991 on 2012-11-24
Any solutions guys ....thanks

---

