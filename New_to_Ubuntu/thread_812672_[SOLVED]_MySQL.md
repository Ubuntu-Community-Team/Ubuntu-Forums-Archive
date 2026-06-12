---
title: "[SOLVED] MySQL"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by hungryOrb on 2008-05-30
Hello there!
Tis a shrouded day again in Shanghai.
And I was wondering if anyone could offer a word of advice for me using mysql?
Im trying to set up Joomla on a ubuntu server, and just wondering how to make the database? Is connecting to MySQL from a network laptop the best idea? Using mysql tools, like administrator? 
I have had a go at connecting, but it won't let me in :( 
I wrote down all the details that I installed MySQL with.. But I can't remember it asking me for a username, so I assumed either admin or root would be default. But it's still rejecting me.

Could it be that I need to set at least read permissions on MySQL? If so, please could someone tell me how to do that? Do I just chmod the app folder?

---

### Post by justleen on 2008-05-30
i think the for joomla you jsut need a user and passwd (root is default users on mysql, during install it aked for a passwd). Joomla provides a setup page that will create the directory.

Dont chmod anything, that will not change permisions on the actual DB's!

try to get into the mysql shell
```
mysql -u root -p 
```
this will prompt for a passwd. 
on succesfull login the cmdline prompt changes to Mysql>
(type exit to exit)

this will ensure you have the right passwd

---

### Post by hungryOrb on 2008-06-01
> **justleen said:**
> i think the for joomla you jsut need a user and passwd (root is default users on mysql, during install it aked for a passwd). Joomla provides a setup page that will create the directory.

Dont chmod anything, that will not change permisions on the actual DB's!

try to get into the mysql shell
```
mysql -u root -p 
```
this will prompt for a passwd. 
on succesfull login the cmdline prompt changes to Mysql>
(type exit to exit)

this will ensure you have the right passwd

Thankyou Justleen! Your avatar is so cool ;]
That works, thankyou, I was wondering why I had problems logging into MySQL administrator on a lan connected computer.. I use the servers IP, and then the same user and pass, but it doesn't connect. Does the 'Stored Connection' need to be entered? May I ask what that is? And If the IP doesn't work in Server Host, then do you have any idea what I can use instead?
:D

---

### Post by hungryOrb on 2008-06-01
I was thinking that I may need to change a permission somewhere because I definetly have the right IP (I enter: 192.168.1.122) username root, and password is definetly correct.. but still it won't connect, but pinging works.

---

### Post by unutbu on 2008-06-01
Run mysql on the server:
```
mysql -u root -p
```

If you haven't created a database already:
```
mysql> create database <yourdb>;
```

To give <user> access to the database <yourdb>:
```
mysql> GRANT ALL PRIVILEGES ON <yourdb>.* TO '<user>'@'<host>' IDENTIFIED BY '<password>';
```

Note that mysqld will only allow <user> to connect to the <yourdb> database from host <host> when the password <password> is given.

---

### Post by hungryOrb on 2008-06-02
Thanks unutbu! :)
I'm not sure If I want to create a database now, because Joomla tries to do that when installing. 
There has gotta be some simple reason why I cannot connect with MySQL administrator :S

---

### Post by unutbu on 2008-06-02
Suppose you want to connect to mysql from a remote computer, named asteroid. 
Then you need an entry in the user table like this:
```
+-----------+------------------+
| Host      | User             |
+-----------+------------------+
...
| localhost | root             | 
| asteroid  | root             |
+-----------+------------------+
```
With the above two entries mysql will let root connect to the mysqld server only when root tries to connect from localhost or asteroid. 

Type the following and see what entries you have in your user table. It might look something like this:
```
% mysql -u root -p
mysql> use mysql;
mysql> select Host,User from user;
+-----------+------------------+
| Host      | User             |
+-----------+------------------+
...
| localhost | debian-sys-maint | 
| localhost | root             | 
+-----------+------------------+

```

Here is how you can add root@asteroid:

```
mysql> GRANT ALL PRIVILEGES ON * TO 'root'@'asteroid' IDENTIFIED BY '<password>';
mysql> quit

```

---

### Post by hungryOrb on 2008-06-02
> **unutbu said:**
> Suppose you want to connect to mysql from a remote computer, named asteroid. 
Then you need an entry in the user table like this:
```
+-----------+------------------+
| Host      | User             |
+-----------+------------------+
...
| localhost | root             | 
| asteroid  | root             |
+-----------+------------------+
```
With the above two entries mysql will let root connect to the mysqld server only when root tries to connect from localhost or asteroid. 

Type the following and see what entries you have in your user table. It might look something like this:
```
% mysql -u root -p
mysql> use mysql;
mysql> select Host,User from user;
+-----------+------------------+
| Host      | User             |
+-----------+------------------+
...
| localhost | debian-sys-maint | 
| localhost | root             | 
+-----------+------------------+

```

Here is how you can add root@asteroid:

```
mysql> GRANT ALL PRIVILEGES ON * TO 'root'@'asteroid' IDENTIFIED BY '<password>';
mysql> quit

```

Unutbu, thankyou very much!
This makes some things a little clearer, however it doesn't seem to want to connect still. On the windows boot, I looked at computer properties, and the name of the computer is 'hadouken', so I replaced asteroid with that, and kept <password> as <password>. I assumed you meant to keep that as it was.. rather than putting an actual password in there.
But, ye, it still pings fine, but doesn't want to connect.
MySQL error number 2003
Thanks again for help though..!
Robin

---

### Post by unutbu on 2008-06-02
hungryOrb, actually, you have to substitute a real password in place of <password>. This will be the password that you will have to type into the mysql-admin window when you want to connect from hadouken.

---

### Post by unutbu on 2008-06-02
Ah, I think there is one more thing you need to do to establish a connection. 

On the server, edit /etc/mysql/my.cnf. Change 
```

bind-address		= localhost
```

to 
```
#bind-address		= localhost
```
Then restart the MySQL server:
```
sudo /etc/init.d/mysql restart
```

See [http://forge.mysql.com/wiki/Error2003-CantConnectToMySQLServer](http://forge.mysql.com/wiki/Error2003-CantConnectToMySQLServer)

---

### Post by cariboo on 2008-06-02
The first thing to do is run nmap against the computer that mysql is install on you should get a result similar to this:

```
nmap localhost

Starting Nmap 4.53 ( http://insecure.org ) at 2008-06-02 19:56 PDT
Warning: Hostname localhost resolves to 2 IPs. Using 127.0.0.1.
Interesting ports on localhost (127.0.0.1):
Not shown: 1702 closed ports
PORT      STATE SERVICE
21/tcp    open  ftp
22/tcp    open  ssh
25/tcp    open  smtp
80/tcp    open  http
139/tcp   open  netbios-ssn
443/tcp   open  https
445/tcp   open  microsoft-ds
631/tcp   open  ipp
901/tcp   open  samba-swat
3306/tcp  open  mysql
8888/tcp  open  sun-answerbook
10000/tcp open  snet-sensor-mgmt
```

note that mysql is on port 3306

The next thing to is to see what ip address mysql is bound to:

```
jimk@intrepid:~$ cat /etc/mysql/my.cnf | grep bind
bind-address		= 127.0.0.1
```

change the bind-address = 127.0.0.1 to the ip address of the computer that mysql is running on.

Next check to make sure its right

```
netstat -ln | grep 3306
tcp        0      0 192.168.1.200:3306      0.0.0.0:*               LISTEN 
```

Your ip address will be different that above.

Now you should be able to connect to your database using the following commad:

```
mysql -h 192.168.1.200 -u username -p
```

replace my ip address with your own and replace username with your own.

By the way nmap is available through synaptic.

Good Luck

Jim

---

### Post by hungryOrb on 2008-06-02
> **unutbu said:**
> Ah, I think there is one more thing you need to do to establish a connection. 

On the server, edit /etc/mysql/my.cnf. Change 
```

bind-address		= localhost
```

to 
```
#bind-address		= localhost
```
Then restart the MySQL server:
```
sudo /etc/init.d/mysql restart
```

See [http://forge.mysql.com/wiki/Error2003-CantConnectToMySQLServer](http://forge.mysql.com/wiki/Error2003-CantConnectToMySQLServer)

Thanks Unutbu!
This has definetly changed something!
Now:

```
Could not connect to the specified instance.
MySQL Error Number 1130
Host '192.168.1.119' is not allowed to connect to this MySQL server
```

Hmm.. When I see this, clouds form in my brain xD
Robin

---

### Post by unutbu on 2008-06-03
Try 

```
% mysql -u root -p
mysql> use mysql;
mysql> GRANT ALL PRIVILEGES ON *.* TO 'root'@'192.168.1.%' IDENTIFIED BY '<password>';

```

By using 192.168.1.% instead of 192.168.1.119, root should be able to connect to the mysql server from any machine on your local network. (In case you have more than one).

---

### Post by hungryOrb on 2008-06-03
> **unutbu said:**
> Try 

```
% mysql -u root -p
mysql> use mysql;
mysql> GRANT ALL PRIVILEGES ON *.* TO 'root'@'192.168.1.%' IDENTIFIED BY '<password>';

```

By using 192.168.1.% instead of 192.168.1.119, root should be able to connect to the mysql server from any machine on your local network. (In case you have more than one).

That's a good idea yes. Although probably, for the most part, will only be connecting to it via one machine. If I try to connect by the name (ubuntuserver) or IP (192.168.1.122) it still doesn't like it. 
Is there some base permission that 3306 must recognise? I don't really know the process at all of connecting :)
Robin
Thanks for all help again.. if its taking up too much of your time, then I understand completely if you cannot help further :)

---

### Post by unutbu on 2008-06-03
Hi HungryOrb, I'm sorry my advice hasn't been more efficient. I don't have a network to try this out on at the moment so I've had to just muddle through.

Perhaps try the GRANT command one more time:

```
mysql> GRANT ALL PRIVILEGES ON *.* TO 'root'@'gen-laptop.local' IDENTIFIED BY '<password>';
```

---

### Post by hungryOrb on 2008-06-04
> **unutbu said:**
> Hi HungryOrb, I'm sorry my advice hasn't been more efficient. I don't have a network to try this out on at the moment so I've had to just muddle through.

Perhaps try the GRANT command one more time:

```
mysql> GRANT ALL PRIVILEGES ON *.* TO 'root'@'gen-laptop.local' IDENTIFIED BY '<password>';
```

Thankyou Unutbu, your heart is very kind.
Let me take a picture of my user table ;]
At the moment I'm in windows, and the windows OS is called hadouken in My Computer properties. So have tried that command on hadouken to no avail.
Same 1045 error. Can connect to ubuntuserver in firefox and get the standard "It works!" apache message.. and pings work fine, as you saw in the screenshot. 
Is this abnormal perhaps?

---

### Post by cariboo on 2008-06-04
I don't know if this makes any difference but I always add the grant option to the privileges:

```
mysql> GRANT ALL PRIVILEGES ON *.* TO 'user'@localhost 
    -> IDENTIFIED BY 'password' WITH GRANT OPTION;
Query OK, 0 rows affected (0.08 sec)
mysql> GRANT ALL PRIVILEGES ON *.* TO 'user'@'%' 
    -> IDENTIFIED BY 'password' WITH GRANT OPTION;
Query OK, 0 rows affected (0.00 sec

```

By the way my host table is empty, so that maybe why I can connect remotely and you can't. I'm also using mysql 5.0 but I'm still using the same commands as far back as version 3.

Jim

---

### Post by hungryOrb on 2008-06-04
> **cariboo907 said:**
> I don't know if this makes any difference but I always add the grant option to the privileges:

```
mysql> GRANT ALL PRIVILEGES ON *.* TO 'user'@localhost 
    -> IDENTIFIED BY 'password' WITH GRANT OPTION;
Query OK, 0 rows affected (0.08 sec)
mysql> GRANT ALL PRIVILEGES ON *.* TO 'user'@'%' 
    -> IDENTIFIED BY 'password' WITH GRANT OPTION;
Query OK, 0 rows affected (0.00 sec

```

By the way my host table is empty, so that maybe why I can connect remotely and you can't. I'm also using mysql 5.0 but I'm still using the same commands as far back as version 3.

Jim

Thankyou Jim ;]
Didn't work but seemed like a good idea :D However, your "'password'" made me start, I had been encasing passwords within '<>' those brackets, and I thought only the characters within the braces would be the password, but it seems everything inside the '' was the password! It works now :)

Thanks guys for persistence in helping. I would be nowhere without you! Would you happen to know how I can delete the unimportant users from the table? Or perhaps change a password or two? :D
Robin
<3

---

### Post by unutbu on 2008-06-04
I'm glad you found the way to connect! Sorry about the <password> confusion -- I should have realized it isn't clear which parts of the commands must stay and which parts can change...

To clean up the user table, you can use the mysql-admin program: (see the attachment below)

```
gksudo mysql-admin
```
Click on "User Administration" in the upper left panel. In the lower left panel all the user accounts should appear. Click in root. Underneath that you'll see one item for each host. Right-click on the item you want to delete. Select "Remove Host". 

To change the password for a user, you click on the user and then in the big panel on the right there are text fields where you can enter a new password.

---

### Post by hungryOrb on 2008-06-04
> **unutbu said:**
> I'm glad you found the way to connect! Sorry about the <password> confusion -- I should have realized it isn't clear which parts of the commands must stay and which parts can change...

To clean up the user table, you can use the mysql-admin program: (see the attachment below)

```
gksudo mysql-admin
```
Click on "User Administration" in the upper left panel. In the lower left panel all the user accounts should appear. Click in root. Underneath that you'll see one item for each host. Right-click on the item you want to delete. Select "Remove Host". 

To change the password for a user, you click on the user and then in the big panel on the right there are text fields where you can enter a new password.

Oh thankyou Unutbu! :)
Very valuable information :D
The ubuntuserver cannot support a GUI though. So instead connect through another computer. Which is fine, however, only 3 users are recognised. I wonder how you can tell which user you are?
I've tried to change password to identify which user I am, but so far, no change! :]

---

### Post by unutbu on 2008-06-04
It is normal to have a root and debian-sys-maint user accounts. A third user account might have been created by joomla. 

Tip: The root user account in mysql has absolutely nothing to do with your root user account in Ubuntu. In particular, they do not have to have the same password. In fact, it is safer if you make sure they do not have the same password. That way, if someone somehow discovers the root password in mysql, your server is not automatically compromised as well.

What are the names of the other accounts? Maybe if we know the names we'll recognize them if they are created by standard programs.

---

### Post by hungryOrb on 2008-06-05
> **unutbu said:**
> It is normal to have a root and debian-sys-maint user accounts. A third user account might have been created by joomla. 

Tip: The root user account in mysql has absolutely nothing to do with your root user account in Ubuntu. In particular, they do not have to have the same password. In fact, it is safer if you make sure they do not have the same password. That way, if someone somehow discovers the root password in mysql, your server is not automatically compromised as well.

What are the names of the other accounts? Maybe if we know the names we'll recognize them if they are created by standard programs.

Thanks for knowledge =)
The names of the MySQL accounts, are all in the screenshot. I don't *need* to clean them up I realise, but I'd like to know which account I'm using.. When connecting to Administrator or Query Browser it doesn't seem to require a user as that of the computer name.. Just the location to connect to.. 
:)

Thanks again!

---

### Post by cariboo on 2008-06-06
If you're running a LAMP server, give phpmyadmin a try, it's a web based database administration program. It's in the repositories.

Jim

---

### Post by unutbu on 2008-06-06
HungryOrb, when you run mysql-admin and it asks for a username and password, if you leave the username blank the username is, by default, set to root.

To check this, run mysql-admin, leave the username blank and enter a wrong password. You should get a window that looks like the attachment below.

If you would like to run mysql-admin solely from hadouken, then your user table should look like this:

```
mysql> select host,user from user;
+-------------+------------------+
| host        | user             |
+-------------+------------------+
| localhost   | debian-sys-maint | 
| localhost   | root             | 
| hadouken    | root             | 
+-------------+------------------+
```

All other entries can be dropped.
To clean up the user table, run mysql-admin:

```
gksudo mysql-admin
```

Click on "User Administration" in the upper left panel. Below it, in the lower left panel you should see three users (little people icons): 'root', 'debian-sys-maint' and one that has no name. Right-click on the one that has no name and select "Remove **User**". Then you can right-click on root and select each of the @host lines that you wish to remove. Right-click and select "Remove **Host**".

---

