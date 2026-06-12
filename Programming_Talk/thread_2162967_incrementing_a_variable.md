---
title: "incrementing a variable"
date: 2013-07-16
forum: Programming Talk
---

### Post by cbillson on 2013-07-16
In Dos i could do the following: i need help translating this into linux shell.
[INDENT]
test1=bob
test2=joe
test3=ken
test4=none

set var=0

:start
set var+=1
(Line below sets test to the value of test%var% - test1, test2 etc)
CALL SET test=%%test%var%%%
if %test% == none goto end
echo %test%
goto start

:end

[/INDENT]
this should:

echo bob
echo joe
echo ken

exit.

Apologies if what i've actually typed contains errors, what I'm trying to achieve is, a script that can repeat a number of tasks until it see's 'none' - but everything i want it to do will be based around a number.

I can easily work out how to increment a number, i need help repeating the bunch of tasks (for loop?) and breaking out of the routine.

as an example, lets use the loop to download files:

file1=test.zip
file2=winzip.exe
file3=none

file=$filex
wget http://8.8.8.8/$file
if [ -e $file ]; then filexresult=success; fi
echo $file $filexresult

(repeat)



How achievable is this, or am i going at this all wrong? 

Thanks in advance.

[INDENT][/INDENT]

---

### Post by zero2xiii on 2013-07-16
```
count=1
count=$((count+1))
```

Actually, a even better option would be bash arrays:
[http://www.cyberciti.biz/faq/bash-for-loop-array/](http://www.cyberciti.biz/faq/bash-for-loop-array/)

---

### Post by Majorix on 2013-07-16
You are looking for arrays. Pretty suitable for the job.

---

### Post by ofnuts on 2013-07-16
> **Majorix said:**
> You are looking for arrays. Pretty suitable for the job.
+1

The Unix shell is much more powerful that Windows .BAT files. Don't translate directly, think of the problem in new terms.

Actually, not even arrays... just a good old "for" with list:g
```

for file in test.zip winzip.exe
do 
     wget http://8.8.8.8/$file
done

```

With some error notification:

```

for file in test.zip winzip.exe
do 
     wget http://8.8.8.8/$file || echo "$file didn't download, Wget rc=$?"
done

```

---

