---
title: "Can I do this with Python?"
date: 2007-01-13
forum: Programming Talk
---

### Post by Paul41 on 2007-01-13
I have never done any programming in Python, but I would like to try it out. I have something that I think it would be good for, but since I have never used it I am not sure.

I have some MySQL databases on a hosted server that I use for some my website. I would like to write a Python script that will make a back up of the databases and save the backups to my computer. 

Would this be possible? If so can someone get me pointed in the right direction? I am not asking for someone to write the code for me (I want to learn to do that myself :) ), I just need some suggestions for libraries, classes, functions, tutorials, or anything like this that would help me with this project.

---

### Post by pmasiar on 2007-01-13
> **Paul41 said:**
> I have some MySQL databases on a hosted server that I use for some my website. I would like to write a Python script that will make a back up of the databases and save the backups to my computer. 

It is not only possible - is is easy. Remember: python makes simple thing easy, and hard thing possible :-)
[URL="http://aspn.activestate.com/ASPN/Cookbook/Python/Recipe/52197"]
ASPN cookbook example[/URL] how to use python DBI API should get you started. You need to create dump file, compress it (use gzip command or python zip module), and transfer it. 

Good luck!

---

### Post by gpolo on 2007-01-13
Is there any specific reason you wanna do this in Python ? All you need is shell script and cron

---

### Post by tomchuk on 2007-01-13
Python would probably be overkill, a simple shell script using mysqldump and rsync would probably do the trick.

---

### Post by Paul41 on 2007-01-13
> Is there any specific reason you wanna do this in Python ? All you need is shell script and cron

Well, there were a couple of reasons. First I just wanted to learn Python. Also someone that I work with still uses Windows so I would like him to be able to use it also.

With that said, I would also like to learn more about shell scripts so I will also look in to that. To be honest I didn't even think about the possibility of using a shell script before.

---

### Post by jblebrun on 2007-01-13
You can execute shell scripts in windows using Cygwin.

Writing this database backup utility in Python would most likely not give you an opportunity to really learn the language.

---

### Post by Paul41 on 2007-01-13
Thanks for the info everyone. Based on everyone's suggestions I am going to try to do this with a shell script. Like I said shell scripting is also something that I want to learn so this will be just as good.

---

### Post by ghostdog74 on 2007-01-13
> **Paul41 said:**
> I have never done any programming in Python, but I would like to try it out. I have something that I think it would be good for, but since I have never used it I am not sure.

I have some MySQL databases on a hosted server that I use for some my website. I would like to write a Python script that will make a back up of the databases and save the backups to my computer. 

Would this be possible? If so can someone get me pointed in the right direction? I am not asking for someone to write the code for me (I want to learn to do that myself :) ), I just need some suggestions for libraries, classes, functions, tutorials, or anything like this that would help me with this project.

if you just want to do backups of your mysql databases, you can use mysqldump provided when you install mysql client. mysqldump can be used in your batch files ( in windows ) and shell scripts ( in unix). But if you want more control for complex operations, for example, manipulation of your data, database transactions, formatting the data to use in another application , etc...you may want to try writing in Python. You can use [this]("http://dev.mysql.com/downloads/python.html") for database connections and doing transactions...

---

### Post by Grey on 2007-01-14
Honestly, since I discovered Python, I haven't used bash for scripting anymore.  Python is easier to use and script.  So I say power to ya.

EDIT:  But I'm a C programmer, primarily.  So I prefer the syntax of Python.  I was never any good at shell scripting.  So ymmv.

---

### Post by Mirrorball on 2007-01-15
Python is great and all, but in this case, bash is just the right tool for the job. Here is my script:

```

cd /ftp/backup/dir && mysqldump --user=dbuser --password=dbpassword --default-character-set=charset database | bzip2 -z -c > database.bz2

```Then you run it as a cron job and write another bash script on your computer to connect to your ftp server and download the backup. It's really easy.

---

### Post by Paul41 on 2007-01-15
Thanks Mirrorball, I had to finish up some work on a couple of other projects so I haven't gotten started on this yet. The example you gave will be helpful.

---

