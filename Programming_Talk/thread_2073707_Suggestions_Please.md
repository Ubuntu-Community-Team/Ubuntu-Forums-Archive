---
title: "Suggestions Please"
date: 2012-10-20
forum: Programming Talk
---

### Post by Mohan1289 on 2012-10-20
Hi friends

i wanna write a script which helps my friends 

but i am getting lot of complications though to me it looks little easy but not

in our company my colleges are developing  various applications and deploying them Manually

1. First they are creating a **project.war.zip** file in windows using NET BEANS

2. Then they are Deploying them in CENT OS using FileZilla

3.Then they Move **.war** file to **/root/jboss-4.0.5GA/server/default/deploy**

4. Service jboss stop and check for  processes using ps ax | grep jboss 

5. if it shows more than one process then kill the remaining processes except jboss

6. service start jboss

7. serverlogs:
tail -f /root/jboss-4.0.5GA/server/default/log/serverlog[IMG]https://mail.google.com/mail/u/0/images/cleardot.gif[/IMG]


8. import the Database Structure
what i wanna do is
if i write a script and run it after downloading or uploading the package it should  do all the above processes automatically.
No manual work should be done..

How can i do this?? any suggestions??

Based on this i developed an algorithm

 After the package is uploaded from Windows to Linux  Server using FileZilla client 
1. Check weather the user has installation permissions (but i don't know how?? Can we give installation permissions to a normal user without adding him to the **sudo** group?? which is in **"/etc/group"** file)
2. if not echo Authentication Failure
3. else proceed
4. unzip the **"project.war.zip"** file and move it to the **/root/jboss-4.0.5GA/server/default/deploy **folder
5. the stop the jboss server
6. check weather there is a single process after the jboss is stopeed using **ps ax | grep jboss** 
7. If the process is just **jboss** and nothing else start the **Jboss** server again
7. else kill all the processes except Jboss and start the server again
8.  serverlogs:
tail -f /root/jboss-4.0.5GA/server/default/log/serverlog[IMG]https://mail.google.com/mail/u/0/images/cleardot.gif[/IMG]

9. then connect to database and import Database structure using **mysql -u root -p passsword > .sql**

Can you help me how to check weather there is a single process named jboss and nothing else??
how can i kill all processes except jboss??
Do i need sudo permissions to kill a process??


are there any flaws in my algorithm??
any corrections?? mistakes??

---

### Post by Lars Noodén on 2012-10-20
First do all of the above in the shell.  When you have each step working, copy that step exactly into a text file.  Then when you have collected all the steps, make that text file executable (chmod +x *somefile*) and then add "#!/bin/sh" as the very first line of the file.  

If you are wondering how to read files from a remote server using HTTP or Anonymous FTP, you can use [wget](http://manpages.ubuntu.com/manpages/precise/en/man1/wget.1.html).  The option -O will let you choose which directory and file the file will be save as.

```

wget -O google.html http://www.google.com/index.html
ls google.html

```

---

### Post by Mohan1289 on 2012-10-20
> **Lars Noodén said:**
> First do all of the above in the shell.  When you have each step working, copy that step exactly into a text file.  Then when you have collected all the steps, make that text file executable (chmod +x *somefile*) and then add "#!/bin/sh" as the very first line of the file.  

If you are wondering how to read files from a remote server using HTTP or Anonymous FTP, you can use [wget]("http://manpages.ubuntu.com/manpages/precise/en/man1/wget.1.html").  The option -O will let you choose which directory and file the file will be save as.

```

wget -O google.html http://www.google.com/index.html
ls google.html

```

ohh thank you i will inform my progress shortly

---

### Post by Mohan1289 on 2012-10-22
> **Lars Noodén said:**
> First do all of the above in the shell.  When you have each step working, copy that step exactly into a text file.  Then when you have collected all the steps, make that text file executable (chmod +x *somefile*) and then add "#!/bin/sh" as the very first line of the file.  

If you are wondering how to read files from a remote server using HTTP or Anonymous FTP, you can use [wget]("http://manpages.ubuntu.com/manpages/precise/en/man1/wget.1.html").  The option -O will let you choose which directory and file the file will be save as.

```

wget -O google.html http://www.google.com/index.html
ls google.html

```

Can i download a zip file too using **wget **command??

---

### Post by Lars Noodén on 2012-10-22
You can download any type of file that that webserver provides.  You just need the URI.

---

### Post by Mohan1289 on 2012-10-22
> **Lars Noodén said:**
> You can download any type of file that that webserver provides.  You just need the URI.

I mean if i have to download a file from a System which is in my LAN Connection

and it's IP address is let's say (10.40.70.50) 

how can get them??

wget -O 10.40.70.50 or do i have to use FTP protocol to get that??

---

### Post by Lars Noodén on 2012-10-22
Let's say the file is 'foobar.zip' in the server's top directory. You could get it like this:

```

wget http://10.40.70.50/foobar.zip

```


Wget is also fine with FTP, so you can also get files via Anonymous FTP if that is an issue.  You just have to know where the file is and wget can get it for you.

---

