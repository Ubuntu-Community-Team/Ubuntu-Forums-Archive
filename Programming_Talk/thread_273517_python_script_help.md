---
title: "python script help"
date: 2006-10-08
forum: Programming Talk
---

### Post by saracen on 2006-10-08
I made a simply python script that downloads a bunch of pdf's from a news website and then executes a local command to join them into one single pdf file.  Now I need the script to upload that generated file automatically to a remote server, but that requires a password.  Is there any way I can make that part automated without having to manually input a password each time?  And if so, how do I make a cron job that will run the script daily?

---

### Post by dabear on 2006-10-08
What kind of method do you use for uploading? FTP?

[http://66.102.9.104/search?q=cache:cJP-YMo-eFgJ:www.bigbold.com/snippets/posts/show/711+python+ftp&hl=no&gl=no&ct=clnk&cd=3&client=firefox-a](http://66.102.9.104/search?q=cache:cJP-YMo-eFgJ:www.bigbold.com/snippets/posts/show/711+python+ftp&hl=no&gl=no&ct=clnk&cd=3&client=firefox-a)

[http://docs.python.org/lib/module-ftplib.html](http://docs.python.org/lib/module-ftplib.html)

---

### Post by saracen on 2006-10-09
I'm uploading it using scp.  I created a bash script that runs the python script and then when it's done it calls scp to upload the generated pdf.  That part requires a password.

---

### Post by dabear on 2006-10-09
> **saracen said:**
> I'm uploading it using scp.  I created a bash script that runs the python script and then when it's done it calls scp to upload the generated pdf.  That part requires a password.

Do it from python instead using pxpect

[http://www.palovick.com/code/python/python-ssh-client.php](http://www.palovick.com/code/python/python-ssh-client.php)

---

### Post by saracen on 2006-10-09
Cool, thanks.  How do I make a cronjob that automatically calls my script once a day?

---

