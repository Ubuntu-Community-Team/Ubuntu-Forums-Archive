---
title: "shell script to mv lines from log file to other file"
date: 2008-10-06
forum: Programming Talk
---

### Post by depele on 2008-10-06
Hello, 

I am looking for a shell script to move all lines from a log file starting with date before1/7/2008 to another file and then gzip it.

any suggestions.

thanks

---

### Post by Greyed on 2008-10-06
Your sentence is unclear.  Do the lines start with the date or the file?  If the lines, what is the format of the line?

---

### Post by depele on 2008-10-06
1 file
multiple lines starting with date

mv all lines date before 1/7/2008

I am looking for a preview now. 

grtz...

---

### Post by depele on 2008-10-06
will this line do to cp all files? 

cat logfile.log | grep "2008-07-*" >> test.txt


thanks in advance ?

---

### Post by ghostdog74 on 2008-10-06
show a sample of your file.

---

### Post by depele on 2008-10-06
```

2007-12-08 13:07:44,887 ************************OK
2007-12-08 13:07:44,887 *****************************************************************************************************
2007-12-08 13:07:44,928 DEBUG **************************************************************
2007-12-08 13:07:44,928 DEBUG ******************************************************************
  <Destination>***************</Destination>
  <Origin Role="DEFAULT_ROLE" OrgUnit="***************">*************</Origin>
  *****************

2007-12-08 13:07:44,929 ***************************************************


```...... and so on.

==> all dates has to be all dates until 2008-07-01

```
grep "2008-[0-7]-*" > text.txt
``` ==> will not work.

---

### Post by ghostdog74 on 2008-10-06
describe what you want clearly. It obviously did not work because you are grepping for 2008

---

### Post by depele on 2008-10-06
There are also 2008 entries in the file. So that is not the problem.

I have a file (structured as above).
I need to add all lines starting with 2008-01-01 till 2008-07-01 to old.log
and I need to do the same 
with all lines 2008-07-02 to new.log



is it clear now?

thank you

---

### Post by geirha on 2008-10-06
Try with ```
egrep '^(2008-0[1-6]-|2008-07-01).*'
```

---

### Post by Greyed on 2008-10-06
> **depele said:**
> I have a file (structured as above).
I need to add all lines starting with 2008-01-01 till 2008-07-01 to old.log
and I need to do the same 
with all lines 2008-07-02 to new.log


A file?

[php]
from datetime import date

infile = 'filename'
oldfile = 'filename.old'
newfile = 'filename.new'
div = date(2008,7,2)
log = open(infile,'r')
new = open(newfile,'w')
old = open(oldfile,'w')

for line in log:
    words = line.split()
    stamp = words[0].split('-')
    filedate = date(stamp[0], stamp[1], stamp[2])
    if filedate < div:
        old.write(line)
    else:
        new.write(line)
[/php]Off-the-hip and untested but the gist is there.  Python, of course, not shell.  Basically, open the files needed, set a date object to the dividing line, read the lines in, parse out the date, construct a date object from it, compare the timestamp of the line to the dividing line, older than it write it to the old file, newer write to the new file.  Could be shorter but wouldn't be as clear.  

However if you're really needing it in shell for who-knows-what reason I defer to ghostdog74.  My answer to "shell script" is Python.  ;)

---

### Post by depele on 2008-10-06
thanks a lot. 

I'm working on it.

grtz

---

### Post by ghostdog74 on 2008-10-06
> **Greyed said:**
> 
However if you're really needing it in shell for who-knows-what reason  

[quote=geirha]
egrep '^(2008-0[1-6]-|2008-07-01).*'
[/quote]

there's the reason : short and simple vs long winded. :)

---

### Post by skotos on 2008-10-06
If you used **logrotate** even with the files you are generating, the system would simply manage the rotation for you.:guitar:

Thus you might simply set a **cron job** - a bash one might be good enough - and complete the work, day by day, by taking away the rotated files, automatically compressed, if you need them to be compressed, gzipped, tarred or whatever.
:popcorn:

---

### Post by depele on 2008-10-06
> **skotos said:**
> If you used **logrotate** even with the files you are generating, the system would simply manage the rotation for you.:guitar:

Thus you might simply set a **cron job** - a bash one might be good enough - and complete the work, day by day, by taking away the rotated files, automatically compressed, if you need them to be compressed, gzipped, tarred or whatever.
:popcorn:

==> software not in my power to change logs everything in 1 file so the file keep on growing. 
I already requested a change. But.........

it keeps on going

---

### Post by Greyed on 2008-10-06
> **ghostdog74 said:**
> there's the reason : short and simple vs long winded. :)

I could have used regex as well.  I decided against it since split was perfectly servicable.  Also that egrep magic isn't splitting like he requested.

---

### Post by ghostdog74 on 2008-10-06
> **Greyed said:**
>  Also that egrep magic isn't splitting like he requested.

yes it sure does. Mind showing why it doesn't?

---

### Post by Greyed on 2008-10-06
Ye requested lines to go into TWO files.  The egrep line, on its own, can only extract either lines that do match or do not match.  Therefore you need two passes across the file to get the same results that my script does in a single pass.  Also a single regex compile.

---

### Post by ghostdog74 on 2008-10-06
> **Greyed said:**
> Ye requested lines to go into TWO files.  The egrep line, on its own, can only extract either lines that do match or do not match.  Therefore you need two passes across the file to get the same results that my script does in a single pass.  Also a single regex compile.
i see what you mean.
```

awk '/^(2008-0[1-6]-|2008-07-01)/{print >"testfile"}
     /2008-07-02/{print> "nextfile"}' file

```

---

