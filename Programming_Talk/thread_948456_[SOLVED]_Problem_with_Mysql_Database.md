---
title: "[SOLVED] Problem with Mysql Database"
date: 2008-10-15
forum: Programming Talk
---

### Post by Revo___ on 2008-10-15
Hello community,

I hope you can help me with this problem:

I've few Windows computers and one server.
I've just changed the servers system to the latest Ubuntu Server Edition.
If I type [http://ubuntu/](http://ubuntu/) into a Windows computer's adress field it retrieve the Message 'It Works!'.
The server and all computers are connected with a rooter.
I can acess to the server via SSH or its console.

But if try to connect to the server's Mysql Server (via the C libary by the way) I get the following Message:
Cant connect to Mysql Server on 'ubuntu' 10061
Is use the function mysql_real_connect with the following settings:
- "ubuntu" as the host name
- "" as the database
- the username and the assicoated password.
In other words: The following code is executet on a Windows Computer:
```
mysql_real_connect(&mysql, "ubuntu", Username, Password, "", 0, NULL, 0)
```

What am I doing wrong?
Do you need more information to help me?

Greetings
Revo___

---

### Post by geirha on 2008-10-15
mysql only listens on localhost (127.0.0.1) by default, so you probably need to change bind-address in /etc/mysql/my.cnf . The default port it listens to is 3306, so this should show where it's listening ```
netstat -na | grep -w 3306
```

---

### Post by Revo___ on 2008-10-15
> you probably need to change bind-address in /etc/mysql/my.cnf

To what value should I set it, so that I can acess it from every where?

---

### Post by geirha on 2008-10-15
0.0.0.0 will make it listen on all interfaces.

---

### Post by Revo___ on 2008-10-15
Thanks, that helped a lot.
But with this came a new problem:

The server listens now, but wont allow the program to connect.
It makes the following output:
Host '[THE COMPUTER'S IP]' is not allowed to connect to this Mysql Server

I hope you can help me again.

---

### Post by geirha on 2008-10-15
You probably need to allow the user to connect from other hosts. I guess the easiest way to find out is to log in as the root user locally with
```
sudo mysql mysql
```
And then
```
select user,host from user;
```
You want to have either the hostname or ip of the windows machine there, or '%' for any host.

Check the mysql reference manual: [http://dev.mysql.com/doc/refman/5.0/en/adding-users.html](http://dev.mysql.com/doc/refman/5.0/en/adding-users.html)

---

### Post by Revo___ on 2008-10-15
Thanks again.
You've really helped me.

---

