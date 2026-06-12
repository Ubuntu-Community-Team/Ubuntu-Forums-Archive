---
title: "[SOLVED] MySQL importing large tables w/ long query strings"
date: 2008-12-15
forum: Programming Talk
---

### Post by mike_g on 2008-12-15
I am trying to import a large table. The remote host uses phpMinAdmin, and I exported the data using that. 
My problem is that some of the query lines are very long ~15MB each. Originally I tried using [bigdump](http://www.ozerov.de/bigdump.php) 
which did the job for me in the past. First I ran out of memory so I expanded it in php.ini, next it threw an error saying that MySQL had gone away.
I altered the mysql wait_timeout variable, but that did no good, and according to the bigdump FAQ it cant handle very long query strings.

Next I had a crack at uploading the file to phpmin admin. minAdmin said:
> Too big POST data. Reduce the data or increase the "post_max_size" configuration directive.
So I extended post_max_size to 128M, but it still kept spouting the same BS.

So, I tried doing it through the shell:
```

C:\xampp\mysql\bin>mysql -u root -p fusion < fusion_posts.sql
Enter password:
ERROR 2006 (HY000) at line 3: MySQL server has gone away

```
But mysql has gone away again :(

Anyway I'm getting bored of this now. Does anyone know how I can import this data? Or would I be better off writing a script to split the long lines into smaller ones?

Cheers.

---

### Post by mssever on 2008-12-15
> **mike_g said:**
> So, I tried doing it through the shell:
```

C:\xampp\mysql\bin>mysql -u root -p fusion < fusion_posts.sql
Enter password:
ERROR 2006 (HY000) at line 3: MySQL server has gone away

```But mysql has gone away again :(
"Gone away" sounds to me like a euphemism for "crashed." It probably would be best, though, to write a script to reduce the size of your queries.

---

### Post by mike_g on 2008-12-16
Yeah, guess I'll do that then. Still, it seems kind of dumb for an sql admin prog to produce dumps that MySQL cant handle.

---

### Post by mssever on 2008-12-16
> **mike_g said:**
> Still, it seems kind of dumb for an sql admin prog to produce dumps that MySQL cant handle.
I agree. Since I'm not a MySQL expert, I suppose I might be missing something.

---

### Post by theDaveTheRave on 2008-12-16
Mike_g

I can honestly say that I have had no problems in exporting MySQL data using a MySQL dump, and then re-importing it into another DBase on another machine, I don't have the exact code in front of me as I speak, so I'll hunt it down. You may find you need to use the CLI monitor rather than PHP (I only have very limited experience with PHP).

I will give you more hope and a possible "solution".

I regularly dowload data from the ncbi ftp pages, and they are zipped into files that are over 1 GB in size once unpacked and will import quite happily with a <load data infile...> method. 

Performing this opperation takes the MySQL server about 6 minutes to read through all 4 million lines of tabled data, yes it is a bit big, yes it does take its time, and yes it is in txt format... Oh the joys of being into genetics :guitar:

So possible solution is to export the table into either a tab or comma separated volume. then import into your SQL DBase.

David.

ps. I currently perform this on my "geting a bit old" laptop, I hope to have the server up and ready soon, so I hope to get the data imports down to a sensible time frame (a couple of minutes would be nice), although I'm not complaining about the enforced "coffee break"  :p

---

### Post by drubin on 2008-12-16
> **mike_g said:**
> I am trying to import a large table. The remote host uses phpMinAdmin, and I exported the data using that. 
My problem is that some of the query lines are very long ~15MB each. Originally I tried using [bigdump](http://www.ozerov.de/bigdump.php) 
which did the job for me in the past. First I ran out of memory so I expanded it in php.ini, next it threw an error saying that MySQL had gone away.
I altered the mysql wait_timeout variable, but that did no good, and according to the bigdump FAQ it cant handle very long query strings.

Next I had a crack at uploading the file to phpmin admin. minAdmin said:

So I extended post_max_size to 128M, but it still kept spouting the same BS.

So, I tried doing it through the shell:
```

C:\xampp\mysql\bin>mysql -u root -p fusion < fusion_posts.sql
Enter password:
ERROR 2006 (HY000) at line 3: MySQL server has gone away

```
But mysql has gone away again :(

Anyway I'm getting bored of this now. Does anyone know how I can import this data? Or would I be better off writing a script to split the long lines into smaller ones?

Cheers.

How big is your fusion_posts.sql ?  
How was this file generated?
I take it the **server** is on your localmachine? 

also as a point it is -ppassword no space. :) 

I often restore pretty big backups as sql dumps. > 1gig so don't see how this can be an issue


[http://bugs.mysql.com/bug.php?id=32543](http://bugs.mysql.com/bug.php?id=32543) this might be a work around look at the 3rd post.
[http://lists.mysql.com/mysql/215240](http://lists.mysql.com/mysql/215240)

---

### Post by bobrocks on 2008-12-16
> **drubin said:**
> 

also as a point it is -ppassword no space. :) 


That is generally bad practice as it stores the password in your command history, as it is being run from a DOS command prompt I suppose it doesn't really matter.  The space before fusion means fusion just indicates which database to run the queries on.


As for the original problem Mysql by default will dump any query line bigger than 1 meg.  As drubin's link points out you can try setting the max_allowed_packet variable to a much bigger size.

---

### Post by drubin on 2008-12-16
> **bobrocks said:**
> That is generally bad practice as it stores the password in your command history, as it is being run from a DOS command prompt I suppose it doesn't really matter.  The space before fusion means fusion just indicates which database to run the queries on.


Personally your passwords for mysql are generally stored in plain text in your scripts any way. So if people have access to your home dir they more then likely have compromised your whole system and you have more worries...

---

### Post by mike_g on 2008-12-17
Thanks, setting max_allowed_packet worked :)

---

