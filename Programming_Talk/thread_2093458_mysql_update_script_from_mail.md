---
title: "mysql update script from mail"
date: 2012-12-10
forum: Programming Talk
---

### Post by alfa16vjtd on 2012-12-10
Dear all,

I'm trying to write a script who updates a database from data in a mail.
However it always skips one mail.

This is the script.

#!/bin/bash
fetchmail

while [ $? != 1 ]; do
{

mailx << EOF > /dev/shm/outfile
U
1
delete
q
EOF
if [ $? -eq 1 ]
then
tac /dev/shm/outfile > /dev/shm/outfile2
field1=`sed -n '2p' /dev/shm/outfile2`
echo $?
field2=`sed -n '3p' /dev/shm/outfile2`
echo $?
/usr/bin/mysql -h localhost -u user --password=pass <<EOF
use test;
UPDATE database set field1 = "$field1" where field2 = "$field2"
EOF

break
fi

tac /dev/shm/outfile > /dev/shm/outfile2
field1=`sed -n '3p' /dev/shm/outfile2`
echo $?
field2=`sed -n '4p' /dev/shm/outfile2`
echo $?
/usr/bin/mysql -h localhost -u user --password=pass <<EOF
use test;
UPDATE database set field1 = "$field1" where field2 = "$field2"
EOF
echo $?
} done

if I remove the complete if statement then everything works but the script stays in the loop.

Sorry for posting this question twice but the previous was in the wrong place.

thx in advance

---

### Post by Bachstelze on 2012-12-10
This looks nasty. What I would do if I were you is fetch the mail normally and pass it to procmail with a suitable rule.

---

### Post by alfa16vjtd on 2012-12-10
> **Bachstelze said:**
> This looks nasty. What I would do if I were you is fetch the mail normally and pass it to procmail with a suitable rule.

And how would you pass it to mysql then?

---

### Post by Bachstelze on 2012-12-10
What do you mean "pass it to mysql"? Just add a procmail rule that will pipe the mail to your script, except that your script only does the mysql stuff, not the dirty fetchmail+mailx.

---

### Post by SeijiSensei on 2012-12-10
+100 for procmail.

---

### Post by Bachstelze on 2012-12-10
Basically, put this in ~/.forward:

```
"|exec /usr/bin/procmail || exit 75"
```

then this in ~/.procmailrc

```
:0fw: mysqlscript.lock
* ^Subject: MYSQL
| /path/to/script.sh

```

and so any mail whose subject starts with MYSQL will be piped to your script.

---

### Post by alfa16vjtd on 2012-12-10
> **Bachstelze said:**
> Basically, put this in ~/.forward:

```
"|exec /usr/bin/procmail || exit 75"
```

then this in ~/.procmailrc

```
:0fw: mysqlscript.lock
* ^Subject: MYSQL
| /path/to/script.sh

```

and so any mail whose subject starts with MYSQL will be piped to your script.

ok thank you already, I will have to do some homework tomorrow to figure out how procmail can retreive my emails.

---

### Post by Bachstelze on 2012-12-10
It does not. It processes any mail that arrives, so you can just fecth it with fetchmail since that seems to be what you are using, procmail will process it. Just run fecthmail by itself, not inside your script.

---

### Post by alfa16vjtd on 2012-12-10
So this is what I have to do:

this in ~/.forward:
```
"|exec /usr/bin/procmail || exit 75"
```

this in ~/.procmailrc
```
:0fw: mysqlscript.lock
* ^Subject: MYSQL
| /path/to/script.sh
```

a cronjob to do the fetchmail

and
```

field1=`sed -n '3p' /dev/shm/outfile2`
field2=`sed -n '4p' /dev/shm/outfile2`
/usr/bin/mysql -h localhost -u user --password=pass <<EOF
use test;
UPDATE database set field1 = "$field1" where field2 = "$field2"
EOF

```

What variable do I use for procmail?

---

### Post by Bachstelze on 2012-12-10
You will have to modify your script a little since you are reading everything form stdin, not from /dev/shm. I can't help you with that, though, because my shell script skills are very basic.

Also, the ~/.forward part assumes Postfix since this is what I use, it might be different with other MTAs.

And also by ~ we mean the home directory of the user that receives the mail so in particular I assume it is a real user. It will probably be different with virtual users.

---

### Post by alfa16vjtd on 2012-12-10
> **Bachstelze said:**
> You will have to modify your script a little since you are reading everything form stdin, not from /dev/shm. I can't help you with that, though, because my shell script skills are very basic.

Also, the ~/.forward part assumes Postfix since this is what I use, it might be different with other MTAs.

And also by ~ we mean the home directory of the user that receives the mail so in particular I assume it is a real user. It will probably be different with virtual users.

propably it will be this then 

```
field1=`sed -n '3p' < /dev/stdin`
field2=`sed -n '4p' < /dev/stdin
/usr/bin/mysql -h localhost -u user --password=pass <<EOF
use test;
UPDATE database set field1 = "$field1" where field2 = "$field2"
EOF
```

---

### Post by alfa16vjtd on 2012-12-10
Thanks for the help already, I will try this tomorrow.

---

### Post by Bachstelze on 2012-12-10
You should probably use something like while/read to read line-by-line (but again, I am not a Bash expert). See [http://mywiki.wooledge.org/BashFAQ/001](http://mywiki.wooledge.org/BashFAQ/001)

---

### Post by Some Penguin on 2012-12-11
...and if the third line of the email contains something like

```

"; TRUNCATE database; --

```

?

---

### Post by alfa16vjtd on 2012-12-11
> **Some Penguin said:**
> ...and if the third line of the email contains something like
 
```

"; TRUNCATE database; --

```
 
?
 
It would be a problem if line 2 has that code but then line 3 has to be in the database. I would also block all email who isn't sent with one of my adresses. Furthermore I will look how to prevent this.

---

### Post by Bachstelze on 2012-12-11
> **alfa16vjtd said:**
> I would also block all email who isn't sent with one of my adresses.

That's a bad idea. The From: header (like any other header) can be spoofed.

---

### Post by alfa16vjtd on 2012-12-11
> **Bachstelze said:**
> That's a bad idea. The From: header (like any other header) can be spoofed.
 
Well actually I didn't think that far at that moment. 
The script will be used to update ip adresses in a database. Maybe it would be safer to use certificates on the router to upload a file. The problem then is when the client resets the router he knows the private key to login into the server.

---

### Post by Some Penguin on 2012-12-12
1) Preventing SQL injection attacks, as I alluded to in my earlier post:

For just about every language with a database driver, that driver will provide a way to create a prepared statement and to bind arguments to placeholders.  Such methods do exist for Python, Perl, C++, Java and PHP, for example, and they're usually more reliable than rolling your own concatenation and escaping methods.

...not that this stops major institutions from hiring people who are silly enough to write publicly accessible systems which blindly trust user input and perform string concatenation without a thought of escaping, of course.


2a) Authorization.
2b) Authentication.

Unless everybody should be able to insert things into your database, you need a reliable way to accept or reject... and you may want to identify individual contributors and log who made exactly what change.

Usually this involves a login/password system, but that doesn't necessarily mean rolling your own -- there are alternatives such as relying on Facebook Connect or Google's OAuth 2.0 implementation.

---

### Post by alfa16vjtd on 2012-12-15
We've decided to use a php updatescript in combination with 

```
wget -qO - www.domain.com/update.php?hostname=RTR000000001&password=password
```

Thanx for all the help.

---

