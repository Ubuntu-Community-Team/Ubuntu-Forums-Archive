---
title: "what's the best to recover accidentially deleted data from NTFS external harddisk...?"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by taekr on 2008-05-19
Hi, 

Well, I just couldn't believe that his has happened. This is totally disaster..

I have an external harddisk attached to my laptop. There was a folder called 'movies' which had about 30 ~ 40 movies. I don't know what happend.. I just don't understand..  I deleted a folder on the internal harddrisk.. but somehow the movie folder was deleted. 

I really need to recover the data..  I spent so many hours to collect them.. 

They are all AVI files..  HOw can I recover them? 

Can I???  

External harddisk is fomated as NTFS... 250GB..

I'm using Ubuntu hardy

---

### Post by johnn1949 on 2008-05-19
If you are dual booting or can plug drive into windows machine try Glary utilities.  It's a simple program that has a file undelete under "privacy and security".

---

### Post by quelx on 2008-05-19
try ```
sudo apt-get install ntfsprogs
```

it includes ntfsundelete

[http://man.linux-ntfs.org/ntfsundelete.8.html](http://man.linux-ntfs.org/ntfsundelete.8.html)

---

