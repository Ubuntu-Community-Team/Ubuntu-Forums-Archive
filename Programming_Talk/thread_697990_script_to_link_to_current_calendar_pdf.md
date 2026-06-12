---
title: "script to link to current calendar pdf"
date: 2008-02-15
forum: Programming Talk
---

### Post by MatthewMetzger on 2008-02-15
Hello forum,

I would like to write a script that symbolic links the filename CurrentCommunique.pdf to the actual most current communique based on the date in the filename. I use the filename format Communique2008-0210-0216.pdf, where the year is first, the beginning date of the week is second (0210 = Feb 10th), and the end date of the weekly events calendar is last (0216).

I've begun to write it, but my skills are young. I can use bash scripting, but I'm also trying to learn Ruby, so tips using either are welcome.

Here's what I want to accomplish:

ln -s CurrentCommunique.pdf to the filename that contains the dates for the current week

I'm thinking that running this script as a cron job weekly would accomplish my goal.

So far, I've just been able to sort of write the filename out in a bash script. I haven't even been able to figure out how to get the second month/day pair to be seven days after the first month/day pair.

```
#!/bin/sh

year=`date "+%Y"`
month=`date "+%m"`
day=`date "+%d"`

echo Communique$year-$month$day-$month$day.pdf
```

Any suggestions on how to accomplish this would be greatly appreciated. I'm a beginner and would like to learn, so pointing me toward learning resources or documentation is also welcome.

thanks for your time,

Matthew

---

### Post by MatthewMetzger on 2008-02-15
From another recent thread on this forum, I found that this command can give me the date seven days from now:

date -d "+7 days" "+%m%d"

However, I'm not sure that this can help me solve my problem.

---

### Post by ghostdog74 on 2008-02-16
can you describe more clearly your problem. Give examples of filenames and describe how they should look like. Where did those communique files come from and so on....

---

### Post by siouzi on 2008-02-16
May be this is something like you're looking for. This must be run at the beginning of the week, since it always assumes the current date is first day of the week. Also, +7 days is the beginning of the next week, so end of the week is +6 days, right? :)
```

#!/bin/sh

# go to the directory where the files are
cd /path/to/the/files

# e.g. on Sat Feb 16 2008 this will be "Communique20080216-0222.pdf"
# use echo $filename to test! :)
filename="Communique`date '+%Y%m%d'`-`date -d '+6 days' '+%m%d'`.pdf"

# make the link (assuming both files are in the same directory)
ln -s $filename CurrentCommunique.pdf

```

---

