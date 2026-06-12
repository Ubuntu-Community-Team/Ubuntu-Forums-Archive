---
title: "CVS and MySQL"
date: 2008-08-16
forum: Programming Talk
---

### Post by K7522 on 2008-08-16
I have over 1000 csv formatted files that need to go into seperate tables in a mysql db. These tables would be named by the cvs file name. I have an example of these cvs files listed below. 

These files are generally about 600,000 lines long each, so automation is a requirement in this instance.

File Name: 08-16-2008.csv
```

columnname01, columnname02, columnname03, columnname04, columnname05, columnname06, columnname07, columnname08, columnname09, columnname10, columnname11, columnname12, columnname13, columnname14, columnname15
607473114 , 10000064 , 30004969 , 60011917 , 1826 , 0 , 124.82 , 1 , 1156 , 1158 , 2007-12-30 00:00:00.00 , 30:00:00:00.00 , 32767 , 0 , 2008-01-01 00:00:20.07 ,
603977756 , 10000064 , 30004969 , 60011917 , 1826 , 0 , 125.0 , 1 , 100 , 100 , 2007-12-27 00:00:00.00 , 30:00:00:00.00 , 32767 , 0 , 2008-01-01 00:00:20.10 ,
569763001 , 10000064 , 30004969 , 60011740 , 1826 , 0 , 210.0 , 1 , 111697 , 150000 , 2007-12-31 00:00:00.00 , 90:00:00:00.00 , 32767 , 0 , 2008-01-01 00:00:20.11 ,


```

What I am trying to do here goes a bit beyond me, but it is something I'm trying to learn.

What I'd like to do is create a .sh that will handle these files and future files as I receive these daily.

This .sh would do the following:
[LIST]
[*]Check specified folder for new cvs files against a log.
[*]Define in a log what files we have sourced, we don't want to try sourcing every file every time we add one new file to the folder.
[*]Create a mysql table for the new cvs file, named by the cvs file name and using the first line as the row names.
[*]Source the cvs file into the new table.
[/LIST]

As far as finding what files are in the folder against what has been put into the database, I was thinking of having the script do an ls > ls.txt for the file directory, and at the end of sourcing a file to the cvs have it append the filename to sourced.txt, then diff the two to see what it needs to source.

Anyway, there may be a much easier way of going about this, but I would like it to be completely automated, by the file being in cron.hourly.

Thanks for all your time in advance for reading this and posting possible solutions, even small bits suggested help as I continue to drudge along figuring this out on my own.

---

### Post by K7522 on 2008-08-16
I went way off topic in this post. I've figured out almost everything I need on here.

The only thing I haven't figured out is how to get the aforementioned csv files to MySQL tables named their csv filename and data inputted into it.

---

### Post by K7522 on 2008-08-17
I figured out how to remove the junk from the DIFF file, I had to make a few seperate files then delete them, the command doesn't seem to like to overwrite the old file, instead it will be empty.

```
diff $OLD $CLEAN > $DIFF1
sed '1d' $DIFF1 > $DIFF2
sed -e "s|> ||" $DIFF2 > $DIFF
rm $DIFF1
rm $DIFF2
```

I suppose I got a bit off track from my primary topic and needs.

---

### Post by odyniec on 2008-08-17
Here's a simple Perl script that you can use to produce the SQL file that creates a table and populates it with data.
```
#!/usr/bin/perl -na -F/\s*,\s*/

if ($. == 1) {
    # first line
    print "CREATE TABLE $ARGV (" . join(" varchar(100), ", @F) . " varchar(100));\n";
}
else {
    print "INSERT INTO $ARGV VALUES ('" . join("','", @F) . "');\n";
}
```

The CSV file name is passed to the script as a parameter. To have the SQL commands executed, you can pipe the script's output to the MySQL command line client:
```
./create_table.pl [csvfile] | mysql [database_name]
```

I assumed all the columns would have the same "universal" type (varchar(100)), which might not be what you need, as apparently your data is either numbers or date/time values. If you need more appropriate data types (eg. int or datetime), you might try identifying them based on the actual data (for example -- if there is a colon in the data, use datetime). This is slightly more complicated, but definitely doable with a few more lines of Perl code.

---

### Post by K7522 on 2008-08-17
Thanks for the reply, I tried running this through and received this error:

```

ERROR 1064 (42000) at line 1: You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '2008-06-21.csv (columnname01 varchar(100), columnname02 varchar(100), columnname03 varchar(1' at line 1

```

```

$ mysql -V
mysql  Ver 14.12 Distrib 5.0.51a, for debian-linux-gnu (i486) using readline 5.2

```

---

### Post by odyniec on 2008-08-17
That's because the script tries to create a table named after the file, but "2008-06-21.csv" is not a valid MySQL table name. Here's a modified version that strips off the ".csv" part, and puts the table name in quotes (otherwise, MySQL won't accept "2008-06-21" as a proper name).
```
#!/usr/bin/perl -na -F/\s*,\s*/

$ARGV =~ s/\.csv$//;

if ($. == 1) {
    # first line
    print "CREATE TABLE `$ARGV` (" . join(" varchar(100), ", @F) . " varchar(100));\n";
}
else {
    print "INSERT INTO `$ARGV` VALUES ('" . join("','", @F) . "');\n";
}
```

---

### Post by K7522 on 2008-08-17
That's what I thought the error might be, I didn't see any syntax problems with the file. I wasn't sure if it would allow the period or not, I just ran the new script, works flawlessly. Thank you very much.

---

