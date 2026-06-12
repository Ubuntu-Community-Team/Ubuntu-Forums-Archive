---
title: "Gui Ftp Server"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by Troca on 2008-06-07
Hi iam looking for a GUI ftp server for Ubuntu, i have googeld like a mad man without any good results so iam posting a post here where i hopefully will get some help. I tried console based ftp clients after a lack of finding and gui based one. My problem is iam to stupid to figure out how everything works on a Console based one where i have to manually edit config files etc. All i basically want to do is add 2-5 users assign some directory's for them to c and be abel to download from them as well. User account and password and ofc i want it to be safe not super NASA pentagon safe where i have to sit hours just to config safety but safe so not anyone can jump in to it. sorry for the long post and crappy english 



Oh and iam running 64bit 8.04 ubuntu hardy if that makes any difrens.

---

### Post by Monicker on 2008-06-07
You could install gproftpd, which is a gui frontend to the proftpd ftp server.

---

### Post by DBrocks on 2008-06-07
[http://ubuntuforums.org/showthread.php?t=79588](http://ubuntuforums.org/showthread.php?t=79588)

That should help. He has a section for GUI

---

### Post by Troca on 2008-06-07
iam sorry but this ftp server is so complicated :( i know iam stupid but to give you an idea what iam used to

Bulletproof ftp server. where i could set the login dir for anyone and then just link outer directory's to that dir. yes i know it was in windows but it was just so simple. is there nothing out there similar to that ?

---

### Post by hyper_ch on 2008-06-07
setting up ftp on linux is not complicated... it's just different...

have a look at howtoforge.com .... there's a ftp section with many many guides and options and stuff.

---

### Post by DBrocks on 2008-06-07
Its easy. Read the article I posted. He teaches you GUI for FTP.

---

### Post by Monicker on 2008-06-07
> **Troca said:**
> iam sorry but this ftp server is so complicated :( i know iam stupid but to give you an idea what iam used to

Bulletproof ftp server. where i could set the login dir for anyone and then just link outer directory's to that dir. yes i know it was in windows but it was just so simple. is there nothing out there similar to that ?


Did you look at the information for gproftpd?  It can do the things you mention.


[http://85.214.17.244/gadmintools/index.php?option=com_content&task=view&id=15&Itemid=29](http://85.214.17.244/gadmintools/index.php?option=com_content&task=view&id=15&Itemid=29)

---

### Post by Troca on 2008-06-07
> **DBrocks said:**
> Its easy. Read the article I posted. He teaches you GUI for FTP.

the first 2 lines says install the server install the gui play with it then a comment like "took me 2 minutes to setup a server". The rest of it is how to config files manually or am i missing something ? :)

---

### Post by DBrocks on 2008-06-07
Yes. Just ignore the config files. There are 2 ways he teaches how to do it in the tutorial. easy (gproftp) or hard (config files). just use gproftpd

---

### Post by Monicker on 2008-06-07
> **Troca said:**
> the first 2 lines says install the server install the gui play with it then a comment like "took me 2 minutes to setup a server". The rest of it is how to config files manually or am i missing something ? :)

Just before the line with the comment you referenced......


A- The GUI way (for beginners only)

For those who are new to linux and don't want to use a FTP server without GUI, or just for those who don't use often their FTP server and wish to set it quickly without a high level of security, there is a GTK GUI for proftpd.
Be careful, it's less secure than configuring yourself your server.

1- Install proftpd and gproftpd with synaptic or with this command :
Code:

sudo apt-get install proftpd gproftpd

2-Play with the GUI and set up quickly your server.

---

### Post by Troca on 2008-06-07
> **Monicker said:**
> Just before the line with the comment you referenced......


A- The GUI way (for beginners only)

For those who are new to linux and don't want to use a FTP server without GUI, or just for those who don't use often their FTP server and wish to set it quickly without a high level of security, there is a GTK GUI for proftpd.
Be careful, it's less secure than configuring yourself your server.

1- Install proftpd and gproftpd with synaptic or with this command :
Code:

sudo apt-get install proftpd gproftpd

2-Play with the GUI and set up quickly your server.


thats my point his tutorial on how to use the Gui is Play with the GUI and set up quickly your server 

well i cant get it to work settings like /var/etc..... on user accounts and so on dont know how to set that up. anyway i think i wont try ftp server in linux yet :) thanks for all the help guys :) sorry for wasting your time.

---

