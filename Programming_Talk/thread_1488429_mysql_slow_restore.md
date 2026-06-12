---
title: "mysql slow restore"
date: 2010-05-20
forum: Programming Talk
---

### Post by ernest_francis on 2010-05-20
i have a database i want to restore but it's about 90meg in size, not that big. when i use mysql admin it has a restore time of about 8 hours and i don't really want to leave my laptop on for that long - i am in cambodia and the heat/humidity would fry it.

so, any other solutions, it's just a sql text file of the dump of the database i need restored, are there any other solutions that are faster to do this ?

thanks
Ernest

---

### Post by kalaharix on 2010-05-20
Hi

Something wrong somewhere. I do a backup with:
mysqldump --add-drop-table -u root stock > /home/fred/bak/stockDump.sql
then restore using:
mysql -u root stock < /home/fred/bak/stockDump.sql
takes 10sec for 17MByte on old hardware.

rgds

---

### Post by ernest_francis on 2010-05-21
thanks, was using mysql admin not cmd line

---

