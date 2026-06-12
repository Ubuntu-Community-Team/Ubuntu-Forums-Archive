---
title: "set up a cron job and notify to email"
date: 2012-05-27
forum: New to Ubuntu
---

### Post by herbert tamayo on 2012-05-27
Hi, i need to setup a cron job, the objectie is to backup my database everynight at 10 pm, with this command:

```

mysqldump -p --user=itsme database1 > database1+curdate.sql

```

then if the command was succesfully send an email to [email]itsme@itsme.com[/email] with subject database updated on date + curdate

so, I think this should be done using bash program, here it is my questions:

0. how can i get the system curdate and put it into a var?

1. in the command mysqldump how can i pass my password? in textplane? like this: mysqldump -p 1234 --user=itsme database1 > database1+curdate.sql

2. transaction can be used in bash? is there any other way to control that the command mysqldumo was successful?

3. how can i send an email to confirm the operations?

best regards

htamayo

---

### Post by matt_symes on 2012-05-28
Hi
 
> **herbert tamayo said:**
> Hi, i need to setup a cron job, the objectie is to backup my database everynight at 10 pm, with this command:
 
```

mysqldump -p --user=itsme database1 > database1+curdate.sql

```
 
then if the command was succesfully send an email to [EMAIL="itsme@itsme.com"]itsme@itsme.com[/EMAIL] with subject database updated on date + curdate
 
so, I think this should be done using bash program, here it is my questions:
 
0. how can i get the system curdate and put it into a var?
 
[http://manpages.ubuntu.com/manpages/lucid/man1/date.1.html](http://manpages.ubuntu.com/manpages/lucid/man1/date.1.html)
 
```
curdate=$(date);
```
 
> 1. in the command mysqldump how can i pass my password? in textplane? like this: mysqldump -p 1234 --user=itsme database1 > database1+curdate.sql
 
2. transaction can be used in bash? is there any other way to control that the command mysqldumo was successful?
 
```

mysqldump -p --user=itsme database1 > database1+curdate.sql
 
if [[ $? -eg 0 ]] then
    # Code to run if sucessful
fi

``` 
> 3. how can i send an email to confirm the operations?
 
Use the mail command or have a look at [http://askubuntu.com/questions/12917/how-to-send-mail-from-the-command-line](http://askubuntu.com/questions/12917/how-to-send-mail-from-the-command-line)
 
```
sudo apt-get install mailutils
```
 
Kind regards

---

