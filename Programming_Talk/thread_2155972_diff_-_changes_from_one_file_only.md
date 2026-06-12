---
title: "diff - changes from one file only"
date: 2013-06-20
forum: Programming Talk
---

### Post by cbillson on 2013-06-20
Me again! i'm using diff to compare two files, output the differences to a third file and work from that. 

file1 = original file (syslog in this case)
file2 = last view of original file

My problem is syslog gets rolled over to a new file, when this happens i get a load of repeat changes. is there any way i can output the changes against one file rather than both directions - ie take file2 as my constant and i'm only interested in additional lines from file1, not missing stuff?

Hope that makes sense.. i had a look at the man page, but cant see anything that does what i need.

---

### Post by ofnuts on 2013-06-20
Why are you using diff for this. Syslog has timestamps at the beginning of each line, so each line is unique. Write a small script that obtains the last line of the previous log ("tail -1"), searches it in the new log ("grep -n" for the line number) and copies everything from there ("tail -n +N" to copy from line N)....

---

### Post by cbillson on 2013-06-20
Mostly because i didnt know how to do what you describe :oops::oops:

however i find what you put really interesting and i'll have a stab at getting it working :)

---

### Post by cbillson on 2013-06-20
hmm, fallen at about the second hurdle.. 

echo test > test

tail -1 test | grep test

returns: test

tail -1 /var/log/syslog | grep /var/log/syslog

returns nothing.

I assume this is because of redirection etc as tail -1 /var/log/syslog returns:[INDENT]
Jun 20 14:39:01 myserver CRON[214]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)



[/INDENT]
i tried "" and '' round both instances of /var/log/syslog without much result. i also tried:

curr=$(tail -1 syslog)

echo $curr
[INDENT]Jun 20 14:39:01 myserver CRON[214]: (root) CMD (  [ -x  /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] &&  find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin  +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \;  -delete)[/INDENT]

cat /var/log/syslog | grep $curr
cat /var/log/syslog | grep "$curr"
cat /var/log/syslog | grep '$curr'

all return blank..

---

### Post by steeldriver on 2013-06-20
I'm not sure exactly what you are trying to do - are you looking for all lines in currfile that do not appear anywhere in oldfile? or are you looking for lines that have been appended to the file since some point?

It's confusing because when my syslogs roll over there are no duplicates as far as I can see - the new log takes over right where the last log stops

---

### Post by cbillson on 2013-06-20
if you take a copy of syslog at 1pm (old) and a copy at 2pm (new) and compare using diff, you will get an output of all the additions to the file between 1pm and 2pm.

The 'old' file remains constant (ie its not added to) - the new file gets added to by the syslog process.

if your roll-over is scheduled for 1:59pm, you now have an 'old' file that contains stuff that the 'new' file doesnt, a diff now shows results from 'old' - ie stuff you've seen before.

Without going into too much detail, what i'm trying to do is take a copy of syslog at the start of the day, then at periodic intervals during the day, take further copies of it, each time i'm only interested in new data (ie whats changed since i last took it). i take a copy because i want to be able to manipulate the data using sed and other tools, and dont want to mess with the actual syslog.

---

### Post by ofnuts on 2013-06-20
```

# Get text of the last line extracted from syslog in previous run
last_line_seen=$(tail -1 your_old_extract_file)

# Obtain line number of that line in curret syslog (mind the double quotes)
line_number=$(grep -F -n "$last_line_seen" | cut -d ':' -f 1)

# Copy syslog to your new extract starting at that line number
tail -n +$line_number /var/log/syslog >your_new_extract_file

```

---

### Post by cbillson on 2013-06-20
second command, should that have some reference to /var/log/syslog ?

---

### Post by steeldriver on 2013-06-20
... or how about

```
grep -A$(wc -l < /var/log/syslog)  "$(tail -1 your_old_extract_file)" /var/log/syslog
```

(finds the last line of the old file in the current file, plus a number of lines of 'after context' that's guaranteed to be large enough to include everything to the end of the file)

---

### Post by cbillson on 2013-06-20
> **ofnuts said:**
> ```

# Get text of the last line extracted from syslog in previous run
last_line_seen=$(tail -1 your_old_extract_file)

# Obtain line number of that line in curret syslog (mind the double quotes)
line_number=$(grep -F -n "$last_line_seen" | cut -d ':' -f 1)

# Copy syslog to your new extract starting at that line number
tail -n +$line_number /var/log/syslog >your_new_extract_file

```

I managed to get a variation of this to do what i needed, i'm unsure why what i did first off was different to this, but i was missing something :S

Thanks to everyone who stuck with me and provided pointers :)

---

### Post by ofnuts on 2013-06-20
> **cbillson said:**
> second command, should that have some reference to /var/log/syslog ?

Yes :)

---

