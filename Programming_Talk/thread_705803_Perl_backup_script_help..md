---
title: "Perl backup script help."
date: 2008-02-23
forum: Programming Talk
---

### Post by maxding on 2008-02-23
Hello all I am working on a simple backup script.  I have created it and simply tars the contents of a several directories and creates the file.  I have setup the cron to run daily.  However, my issue is that i do not know enough about perl to have daily unique file names.  I have been looking on google for about 30 minutes and can't find anything really helpful.  

My code looks like this:

system "tar -cvvf /home/mdinges/backup/sitebackup.tar /var/www";

anything that you can provide would be helpful.

Thanks,
Max

---

### Post by LaRoza on 2008-02-23
For making "random" names, you can add the date or time to the backup name.

---

### Post by maxding on 2008-02-23
I seemed to have figured out my own issue.


here's what i did.

mdinges@ubuntu:~/backup$ cat /root/scripts/backupsite.pl
#!/usr/bin/perl
#lets add the date:
($sec,$min,$hour,$mday,$mon,$year,$wday,$yday,$isdst)=localtime(time);
$mon = $mon+1;
$year = $year-100;
#backs up the /var/www dir and places it in the /home/mdinges/backup dir.
system "tar -cvvf /home/mdinges/backup/sitebackup0$year-$mon-$mday.tar /var/www";

---

### Post by ghostdog74 on 2008-02-23
learn to write "portable code" at least. In Perl, you can use modules like Archive::tar ( or others ) to do archiving. You are not dependent on whether they have "tar" utility if you one day decides to port your script to other platforms.

---

### Post by slavik on 2008-02-23
question ... why use -v -v for tar when you are running it through system() and not even capturing the output?

---

### Post by maxding on 2008-02-24
i am brand new to this perl thing and only to know to take commands from shell.  I'm sure there are better ways of doing it.  But, I am still learning.

I've been going through some tutorials so i can learn this language.

Max

---

### Post by slavik on 2008-02-24
my point is that you don't need -v -v because any output tar gives is dropped anyway ...

---

### Post by LaRoza on 2008-02-24
> **slavik said:**
> my point is that you don't need -v -v because any output tar gives is dropped anyway ...

I think it was a reference to ghostdog's comment.

@OP You will find that Perl (Python, Ruby, etc) have modules for many tasks, and may be more efficient and more flexible than system(). Don't worry, we all start somewhere.

---

### Post by slavik on 2008-02-24
sorry, should've made that clear. :)

another way of doing shell calls is by surrounding a command you want with backticks (the one on the tilda key).

ie:
```
$ouput = `date`;
```

if you use variables inside the function call, double quote string replacement rules apply, for example:
```
$somedir = "/home/";
$output = `ls $somedir`;
```

---

