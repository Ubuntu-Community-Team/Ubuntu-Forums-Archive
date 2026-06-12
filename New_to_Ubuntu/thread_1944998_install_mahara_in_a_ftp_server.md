---
title: "install mahara in a ftp server"
date: 2012-03-22
forum: New to Ubuntu
---

### Post by vivekpandey1991 on 2012-03-22
hi all... i am using ubuntu 10.10 ... i have ftp server [B]ftp.navriti.com         
i have to install mahara on that server from my computer(i dont have physical access to that computer. i know the username and password of th folder where i am supposed to install . but i have no idea how to do that except that i know i have to anyhow use filezilla for that.. please help .. thanx in advance
[/B][CENTER]**[B][COLOR=Black][/COLOR]**[/B]
[/CENTER]

---

### Post by Lars Noodén on 2012-03-22
Connect to your remote machine using SSH and then use apt-get to install mahara:

```

sudo apt-get update
sudo apt-get install mahara

```

It's there in the repository.

---

### Post by vivekpandey1991 on 2012-03-22
> **Lars Noodén said:**
> Connect to your remote machine using SSH and then use apt-get to install mahara:

```

sudo apt-get update
sudo apt-get install mahara

```It's there in the repository.


ok using ssh doesnt work because my username is [email]learnplate@navriti.com[/email] on the ftp server ftp.navriti.com  so ssh returns some errors as it tries to connect to navriti.com and not ftp.navriti.com.. secondly i have to upload the folders of mahara to that server . so should i update in zip format ? and how will i extract it on the server if i do that?

---

### Post by Lars Noodén on 2012-03-22
To install and configure programs on a remote server, you need some kind of shell access.  Would 'ssh [email]learnplate@ftp.navriti.com[/email]' work?  If not you need to contact the administrator and either have them install the program for you or fix the shell access issue.

---

### Post by vivekpandey1991 on 2012-03-22
> **Lars Noodén said:**
> To install and configure programs on a remote server, you need some kind of shell access.  Would 'ssh [EMAIL="learnplate@ftp.navriti.com"]learnplate@ftp.navriti.com[/EMAIL]' work?  If not you need to contact the administrator and either have them install the program for you or fix the shell access issue.
no that doesnt work .. is it not possible to upload the folder and install it directly without using ssh ? admin has akready created the database and he has told me the name etc of the database .. so installing mahara should be similar to installing it on my localhost .. ie download the zip file(on ftp upload the zip file) extract make few changes in configuration file .. thats it.. just not getting how to extract  a zip file once uploaded

---

### Post by vivekpandey1991 on 2012-03-24
ok i unzipped mahara.. though it took time... i made the changes in config.php .. but still when i am unable to get the installation window or tab.. please hellp

---

