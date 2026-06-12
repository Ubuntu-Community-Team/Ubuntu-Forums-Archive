---
title: "adding content"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by ub007 on 2008-06-23
Hiya,

I installed the LAMP server on my PC.How do i add content to it.i found the default directory to be /var/www,its got one html file index.html which opens when i test on the local host.n i could create more html files in the directory.

Now,i've got images n html content on my windows laptop,how do i add it to the ubuntu server?could any1 tell me what steps to follow?Thanks in advance..

Cheers
David

---

### Post by hyper_ch on 2008-06-23
you just put them into the /var/www folder of your server.

---

### Post by ub007 on 2008-06-23
guess i would look really stupid asking this,but anyways...

How do i put it onto /var/www folder ?i'n using linux for the first time and do not know how to preform this task using the command line....

Cheers

---

### Post by hyper_ch on 2008-06-23
(1) I'd chown the /var/www folder to your user (so that you can copy stuff into it):
```

sudo chown <USER>:<USER> /var/www

```
Replace <USER> with your username

(2) I'd use SFTP/SCP to upload stuff so

(2a) Install openssh server
```

sudo apt-get install openssh-server

```

(2b) Make it a bit more secure with auto-banning of brute-force attacks
```

sudo apt-get install denyhosts

```

(2c) Now connect to it using your username / passwort on the server

- Windows: Get WinSCP - [http://www.winscp.com](http://www.winscp.com)
- Linux: Use a SFTP/SCP capable filemanager (e.g. Konqueror)

Enter as target the server's IP and use your username and password on the server.

(3) Now you can easily copy the stuff onto the server.

[(4) You might need to delete the existing index file in /var/www
```

sudo rm -f /var/www/index.htm

```

or

```

sudo rm -f /var/www/index.html

```
]
[/code]

---

