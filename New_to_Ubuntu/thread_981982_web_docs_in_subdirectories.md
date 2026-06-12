---
title: "web docs in subdirectories"
date: 2008-11-14
forum: New to Ubuntu
---

### Post by JKHinton CPBD on 2008-11-14
Hello,

I am a newbie at this Ubuntu web development.  I am converting a working Windows WAMP to Hardy 8.04 LAMP.  I can view my web pages thru localhost as long as they are all in one directory.  How do you make it allow pages to come from subdirectories under the main web page directory?  My goal is ultimately to make the subdirectory a private password protected directory.  All pointers will be greatly appreciated.

James in GA,USA

---

### Post by MenZa on 2008-11-14
I think you're just missing the permissions to allow it to.

Try running the following command on your subfolders:

```

chmod -R 755 target/

```

---

### Post by superprash2003 on 2008-11-14
could you give an example.. im not able to get what you are saying..

---

### Post by JKHinton CPBD on 2008-11-14
Here's my file tree /home/james/adweb as long as I have  all the html pages in adweb folder I can view them from localhost.  If I try to put files in a subdirectory called pwprotdata under adweb like /home/james/adweb/pwprotdata I can't view any pages in this subdirectory.  

Thank you both for your respones.

---

### Post by superprash2003 on 2008-11-15
then its mostly a permissions issue as mentioned above.. just change permissions for the pwprotdata

---

