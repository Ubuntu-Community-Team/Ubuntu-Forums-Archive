---
title: "[HOW-TO]Access MySQL Server within network via phpMyAdmin"
date: 2008-06-24
forum: New to Ubuntu
---

### Post by balagosa on 2008-06-24
It began when I was searching for a good front-end for MySQL, and I found a liking to PHPMyAdmin(It's look and feel were close to what I wanted). I created this How-To because I have a network MySQL Server that I wanted to access but PHPMyAdmin's default connection was localhost. **hyper_ch** replied to my thread stating I can change my connection to any host, I just had to find PHPMyAdmin's config.

1) Get the needed stuff:
```
sudo apt-get install mysql-server mysql-client libmysqlclient15-dev phpmyadmin
```

You will be asked to provide a password for the MySQL root user - this password is valid for the user root@localhost as well as [email]root@server1.example.com[/email], so we don't have to specify a MySQL root password manually later on (as was the case with previous Ubuntu versions):

New password for the MySQL "root" user: <-- yourrootsqlpassword
Repeat password for the MySQL "root" user: <-- yourrootsqlpassword

We want MySQL to listen on all interfaces, not just localhost, therefore we edit /etc/mysql/my.cnf and **comment out the line bind-address = 127.0.0.1**:

```
vi /etc/mysql/my.cnf
```

find these lines: [b]
[...]
# Instead of skip-networking the default is now to listen only on
# localhost which is more compatible and is not less secure.
#bind-address           = 127.0.0.1
[...][/b]

Then we restart MySQL:
```
/etc/init.d/mysql restart
```

Now check that networking is enabled. Run 
```
netstat -tap | grep mysql
```

The output should look like this: [I]root@server1:~# netstat -tap | grep mysql
tcp        0      0 *:mysql                 *:*                     LISTEN      5869/mysqld
root@server1:~#[/I]

2) Edit **/etc/phpmyadmin/config.inc.php**
```
sudo gedit /etc/phpmyadmin/config.inc.php
```
Note: Use your own editors, my default editor is "gedit". I think KDE has "kate"

3) Insert at bottom of file:

```
    
    $cfg['Servers'][$i]['host']     = '<IP of MYSQL Server>';
    $cfg['Servers'][$i]['port']     = '3306'; //3306 is default port
    $cfg['Servers'][$i]['socket']   = '';
    $cfg['Servers'][$i]['connect_type']     = 'tcp';
    $cfg['Servers'][$i]['extension']        = 'mysql';
    $cfg['Servers'][$i]['compress'] = FALSE;
    $cfg['Servers'][$i]['controluser']      = 'pma';
    $cfg['Servers'][$i]['controlpass']      = 'pmapass';
    $cfg['Servers'][$i]['auth_type']        = 'cookie';
    $cfg['Servers'][$i]['user']     = '';
    $cfg['Servers'][$i]['password'] = '';
    $cfg['Servers'][$i]['only_db']  = '';
    $cfg['Servers'][$i]['verbose']  = '';
    $cfg['Servers'][$i]['pmadb']    = 'phpmyadmin';
    $cfg['Servers'][$i]['bookmarktable']    = 'pma_bookmark';
    $cfg['Servers'][$i]['relation'] = 'pma_relation';
    $cfg['Servers'][$i]['table_info']       = 'pma_table_info';
    $cfg['Servers'][$i]['table_coords']     = 'pma_table_coords';
    $cfg['Servers'][$i]['pdf_pages']        = 'pma_pdf_pages';
    $cfg['Servers'][$i]['column_info']      = 'pma_column_info';
    $cfg['Servers'][$i]['history']  = 'pma_history';
    $cfg['Servers'][$i]['designer_coords'] = 'pma_designer_coords';
```
Note: The lines that I changed in my config were lines: 1 and 2. Everything else, i leave it as is. Only change other stuffs if you know what you are doing; in my case, I had no idead about the other items. I left username and password **blank** for security purposes.

4) Connect to MySQL Network Server:
Open Firefox and type in the URL adress: **localhost/phpmyadmin**. Enter username and password. At this point, you should be seeing the tables on the network server.

--Fin--

Troubleshooting:
1) Can't connect to server. One possiblity could be Network Server downtime. Try to ping the Network Server and see if you receive a reply. 

[i]daniel@daniel-laptop:/usr/share/phpmyadmin/libraries$ ping 192.168.100.221
PING 192.168.100.221 (192.168.100.221) 56(84) bytes of data.
64 bytes from 192.168.100.221: icmp_seq=1 ttl=64 time=2.47 ms
64 bytes from 192.168.100.221: icmp_seq=2 ttl=64 time=2.31 ms
64 bytes from 192.168.100.221: icmp_seq=3 ttl=64 time=2.08 ms
64 bytes from 192.168.100.221: icmp_seq=4 ttl=64 time=2.10 ms
64 bytes from 192.168.100.221: icmp_seq=5 ttl=64 time=2.86 ms
[/i]

References: 
a)[The Perfect Server]('http://www.howtoforge.com/perfect-server-ubuntu8.04-lts-p4')
b)[PHPMyAdmin Wiki]('http://wiki.cihar.com/pma/Config')

---

