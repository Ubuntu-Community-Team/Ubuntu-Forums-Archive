---
title: "I Need help"
date: 2008-07-24
forum: New to Ubuntu
---

### Post by efuzone on 2008-07-24
ih guys first i want to appologise bcoz its not a right place to discuss about my problem but i am realy in trouble about this problem.. i am windows xp user i am using xampp on it.. but i am facing one problem.. i use my website for local netwotk for users and i have installed it to c: drive but c: drive has only 10 gb space which is ok for only website pages now i want to add there songs and movies which are very big space like 200 gb and they are in different partitions like D: e: now my question is how do i join use these partitions in xampp means i wanna add multi partitions in xampp for website please help me and i hope u understand me bcoz my english is not good...

---

### Post by ApOgEEs on 2008-07-24
Thanks for asking UbuntuForums for your problem. As for Ubuntu solution, you can simply change your server to use Ubuntu instead and install LAMP Server packages (LAMP = Linux + Apache + MySQL + PHP).

Regarding the issue on pointing your website to link to your files in another drive is not a big deal in Ubuntu or linux. You can simply create a link from your web root to your other partitions or directories by this simple command in your web directory:

```
ln -s /media/myotherdrive mylinkname
```  

and then you can simply use that link which act as directory on your browser as if you copy all the files in that directory like this:
```
http://mycomputerdomain/mylinkname/mybigfile.mp3
```

As far as I know, this is not possible in Microsoft Windows environment. So, Good luck!!

---

### Post by cariboo on 2008-07-24
If you are using apache you could create virtual websites that point to those directories. The way to do it using a linux distribution is to do as the above poster said is to create symlinks to the directories in question..

It might better if you asked this question in [Other OS Talk]("/http://ubuntuforums.org/forumdisplay.php?f=147")

Jim

---

