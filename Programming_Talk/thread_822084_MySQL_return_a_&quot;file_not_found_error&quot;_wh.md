---
title: "MySQL return a &quot;file not found error&quot; when the file exists"
date: 2008-06-07
forum: Programming Talk
---

### Post by calsaverini on 2008-06-07
Hi, 

I'm having a problem with mysql.

When I try to load a file in a table like this:

```
LOAD DATA INFILE "/home/calsaverini/data.txt" INTO TABLE CMIG4;
```

It returns the error:
```
 ERROR 29 (HY000): File '/home/calsaverini/data.txt' not found (Errcode: 13)
```

But the file IS THERE!

Anyone have any clue what the problem could be?

---

### Post by HalPomeranz on 2008-06-07
Permissions problem perhaps?  The file is going to be read in with the privs of the mysqld process, not your privs.  Try this:

```

chmod o+rx /home/calsaverini
chmod o+r /home/calsaverini/data.txt

```

Then try to load your file as before.

---

### Post by calsaverini on 2008-06-09
Permissions are not the problem. 

I've granted all permissions to the file and the same error still occurs.

---

### Post by dwhitney67 on 2008-06-09
HalPomeranz recommended that you change the permissions on your user directory (that is /home/calsaverini).  Did you change it?

The other thing you could try to do is place the file in /tmp to see if that makes a difference.

---

### Post by 4partee on 2008-07-01
There is a workaround.

[https://bugs.launchpad.net/ubuntu/+source/mysql-dfsg-5.0/+bug/244406](https://bugs.launchpad.net/ubuntu/+source/mysql-dfsg-5.0/+bug/244406)

I am trying to get this classified as a bug.  

HTH;
John

---

### Post by joculi on 2011-05-29
I found that using LOAD DATA **LOCAL** INFILE worked for me.  Without the LOCAL keyword it failed with the same error described above.  

According to the MySQL doc, LOCAL causes the client to read the file and send it to the server.  This seems to eliminate the question of whether the server can read the file.

---

### Post by MattPhillips on 2011-07-04
Hey joculi, thanks!! I had exactly calverini's problem and your solution worked.

---

### Post by LaurentEdel on 2011-09-15
That's the same thing for me.
However using LOCAL isn't a solution, it's just a bypass.

The problem can be resolved by configuring AppArmor, see this thread : [http://stackoverflow.com/questions/2783313/how-can-i-get-around-mysql-errcode-13-with-select-into-outfile](http://stackoverflow.com/questions/2783313/how-can-i-get-around-mysql-errcode-13-with-select-into-outfile), or directly :

```
sudo vi /etc/apparmor.d/usr.sbin.mysqld
```

/usr/sbin/mysqld {
    ...
    /var/log/mysql/ r,
    /var/log/mysql/* rw,
    /var/run/mysqld/mysqld.pid w,
    /var/run/mysqld/mysqld.sock w,
[B]    /data/ r,
    /data/* rw,[/B]
}

```
# sudo /etc/init.d/apparmor reload
```

---

### Post by jdowdell on 2012-07-07
I had a similar case, file was /tmp/test.infile, clearly existed /tmp has 777 permissions, file had 755 permissions.  I did

sudo chown mysql:mysql /tmp/test.infile

And suddenly mysqld could see it.

(adding LOCAL didn't work in my case)

---

### Post by BoynamedSue on 2013-02-27
LaurentEdel - you are the man. Thank you to you. I can import from where ever now. 

Toda raba :):popcorn:

---

### Post by izudin-avdibasic on 2013-10-29
Try this, it worked for me:
chown mysql:mysql filename

---

### Post by vivash on 2014-04-27
[**[COLOR=#000000]LaurentEdel[/COLOR]**]("http://ubuntuforums.org/member.php?u=1251011") THANK You Thankyou Thankyou for showing us the right way to do this. WOW!

---

### Post by cppgent0@gmail.com on 2014-11-07
[FONT=arial]I had the same issue and I used the techniques laid out above to fix it. 

I just wanted to fill out the full sequence of things so others can more easily follow it.
Note: I'm working with Ubuntu 12.04 over an ssh terminal session...
 
```
 

  # work as root; no need for sudo everywhere
[/FONT][FONT=arial]  [/FONT][FONT=courier new]sudo bash[/FONT]
[FONT=arial][FONT=courier new] 
 # stop the current mysql service
 service mysql stop[/FONT][/FONT]

[FONT=arial][FONT=courier new]  # create file called /tmp/mysql-init[/FONT][/FONT]
[FONT=arial][FONT=courier new]  cat /tmp/mysql-init[/FONT]
[FONT=courier new]      UPDATE mysql.user SET Password=PASSWORD('yer_root_password') WHERE User='root';[/FONT]
[FONT=courier new]      FLUSH PRIVILEGES;[/FONT]
[/FONT] 
[FONT=arial][FONT=courier new]  # change owner of the file to mysql[/FONT][/FONT]
[FONT=arial][FONT=courier new]  # without this step, apparmor prevents mysql from seeing the file[/FONT][/FONT]
[FONT=arial][FONT=courier new]  sudo chown mysql:mysql /tmp/mysql-init
[/FONT][/FONT]
[FONT=arial][FONT=courier new]  ls -l /tmp/mysql-init [/FONT]
[FONT=courier new]      -rwxrwxrwx 1 mysql mysql 90 Nov  7 02:43 /tmp/mysql-init[/FONT]
[/FONT]
[FONT=arial][FONT=courier new] mysqld_safe --init_file=/tmp/mysql-init  &[/FONT][/FONT]
[FONT=arial][FONT=courier new]  # you must use the & at the end, otherwise it hangs the ssh session; [/FONT][/FONT]
[FONT=arial][FONT=courier new]  # ctl-c does not work; you must log in from another ssh session [/FONT][/FONT]
[FONT=arial][FONT=courier new]  # and kill -9 the processes from there[/FONT][/FONT]
[FONT=arial][FONT=courier new]
[/FONT][/FONT][FONT=arial][FONT=courier new] # try it out[/FONT][/FONT]
[FONT=arial][FONT=courier new]  mysql -u root -p[/FONT][/FONT]
[FONT=arial][FONT=courier new]    (pwd: yer_root_password)[/FONT][/FONT]
[FONT=arial][FONT=courier new]
[/FONT][/FONT][FONT=arial][FONT=courier new] # at this point: you should be able to get in.[/FONT][/FONT][FONT=arial][FONT=courier new]
 # if not, check /var/log/mysql/error.log to see what's going on[/FONT][/FONT]
[FONT=arial]
[/FONT][FONT=arial]   # kill the temporary mysql session[/FONT]
[FONT=arial][FONT=courier new]  ps aux | grep mysql[/FONT][/FONT]
[FONT=arial][FONT=courier new]  kill -9  pid # where pid is the mysql pid[/FONT][/FONT]
[FONT=arial][FONT=courier new]  # repeat ps aux and kill -9, until no more processes[/FONT][/FONT]

[FONT=arial][FONT=courier new]  # start the service the correct way[/FONT][/FONT]
[FONT=arial][FONT=courier new]  service mysql start
[/FONT][/FONT][FONT=arial][FONT=courier new]
[/FONT][/FONT][FONT=arial][FONT=courier new] # get out of root[/FONT][/FONT]
[FONT=arial][FONT=courier new]  exit[/FONT][/FONT]
[FONT=arial][FONT=courier new]  
 # now working as non-root password[/FONT][/FONT]
[FONT=arial][FONT=courier new]
 # double-check it works... [/FONT][/FONT]
[FONT=arial][FONT=courier new]  mysql -u root -p
[/FONT][/FONT]
```

---

### Post by ofnuts on 2014-11-07
.

---

### Post by farrington on 2015-03-02
This is how I solved a similar problem in Ubuntu 14.04 LTS and MySQL Server version: 5.5.41-0ubuntu0.14.04.1

I placed the .csv file in /var/lib/mysql/database-name (you may need to change the permisions of the /var/lib/mysql directory in order to access it [chmod 777 /var/lib/mysql] ).

Then I added to my .sql script:
LOAD DATA INFILE '/var/lib/mysql/database-name/file.csv'

---

### Post by Pablo_Medina on 2016-02-14
LaurentEdel: It worked for me too

---

