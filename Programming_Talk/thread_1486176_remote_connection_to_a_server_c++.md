---
title: "remote connection to a server c++"
date: 2010-05-17
forum: Programming Talk
---

### Post by korvirlol on 2010-05-17
Hello,

This is a branch of programming i've never delved into before, and im not sure where to begin. Basically, what i need to do, is, on regular intervals (cron) i need to send data from a piece of software running on a machine somewhere to an online database. The program running on each machine is written in c++ and exports the files I need. What i need is a way to send those files to the database housed online.

Ive looked into a few thing like cURL, but that seems like it is only one way (get data from a place online, not put it there). Another option is to shell exec the data using something like scp, but that just seems like a really hacky solution.

Does anyone have any advice about how one could go about this?

Any tips appreciated.

---

### Post by januzi on 2010-05-17
Is that database open for the internet connections ? If yes, then You should look for the proper library (like mysql++). If no, then You have to write Your own "application" that will connect to the database and insert data. In that case it could be simple php script and www server running in the background (apache, lighttpd).

As for curl, You can use it to put data as regular internet browser (**CURLOPT_POST, ****CURLOPT_POSTFIELDS)**/ 
> 
Post a simple "name" and "phone" guestbook.
 
        curl -d "name=Rafael%20Sagula&phone=3320780"                 [http://www.where.com/guest.cgi](http://www.where.com/guest.cgi)

Upload data from a specified file, login with user and password:
 
        curl -T uploadfile -u user:passwd [ftp://ftp.upload.com/myfile](ftp://ftp.upload.com/myfile)
 etc.

Edit:
What kind of the database it is ?

---

### Post by emakichi on 2011-08-01
that's called socket programming...be ready, be aware

---

