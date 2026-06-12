---
title: "Replace command"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by markbusu on 2008-05-10
Hi Guys,

I have a document, which contains a series of numbers such as:

0
21
551
1
1
2
1
1
5
0

Now, i would like to find a method of parsing the entire document, and replacing any 0s with 1s, therefore the example above would become:

1
21
551
1
1
2
1
1
5
1

Any idea of a command to achieve this?

Thanks!

---

### Post by dorkdork777 on 2008-05-10
I don't know of any command, but you could open it with Gedit, then press Control-H (or click the "Replace" button), and search for "0", replacing it with "1".

---

### Post by spydon on 2008-05-10
Can the code be in python or perl or something? :P
I know how to do this in java but you want it in some scripting language don't you?

---

### Post by sdennie on 2008-05-10
Try:

```

sed -e s/0/1/g input > output

```

---

### Post by mister_pink on 2008-05-10
Do what he said, or you can use sed, for example:
```
sed s/0/1/g yourfile > newfile
```

Edit: Woah, this forums fast.

---

### Post by markbusu on 2008-05-10
That did the trick!!

Thanks!

sed 's/string1/string2/g'

---

### Post by markbusu on 2008-05-10
Hi once again, hit a bump here...

If you run the following:

sed s/0/1/g yourfile > newfile

If the number has a 10, this will change to 11... :S

I need to change 0 to 1, only if it is a whole 0 not 10, 100, 101 etc....

I tried sed s/"0"/1/g, however no luck...

Is there any way around this???

thanks!

---

### Post by sdennie on 2008-05-10
Try:

```

sed -e s/^0$/1/ in > out

```

---

### Post by markbusu on 2008-05-10
Uz a star m8! ;)

Worked like a charm!

---

### Post by markbusu on 2008-05-10
Ok, this is rather strange.... When running the command on its own... so

cat file.txt | sed -e s/^0$/1

This worked correctly,

However when try to execute it in the command below, it appears that the command is taken.... (Unless i remove the ^ and $)

cat file.txt |grep "exec"|cut -c 38-50|sed -e s/^0$/1/ > a.txt

Any ideas m8?

---

### Post by sdennie on 2008-05-10
You'll have to put the sed argument in double quotes or it will interpret the $ as the start of a variable:

```

cat file.txt |grep "exec"|cut -c 38-50|sed -e "s/^0$/1/" > a.txt

```

---

### Post by markbusu on 2008-05-10
Strangley enough it works when you execute the command directly in the shell... however when you include the command in a script... it doesn't work...

Any thoughts?

Thanks!

---

### Post by unutbu on 2008-05-10
Could you post a snippet of file.txt and what your script looks like?

---

### Post by markbusu on 2008-05-10
The Script is as follows:

================================================

#!/bin/bash

rm -rf Final.txt
rm -rf Result.txt

TotExec="Total execution time (sec.ms)"
NoExec="Number of executions"
Query="Statement text"


cat /root/ryan/sql1.txt |grep "$NoExec"|cut -c 38-50|sed -e s/^0$/1/> NoExec.txt
cat /root/ryan/sql1.txt |grep "$TotExec"|cut -c 38-50 > TotExec.txt
cat /root/ryan/sql1.txt |grep "$Query" > query.txt




printf "%.10f\n" $(paste -d\/ TotExec.txt NoExec.txt|bc -l)>Final.txt


for i in `seq -w 1 1300`;do for a in Final.txt query.txt;do cat $a | sed -n "$i p" >> Result.txt;done;done

======================

FYI... the reason why im doing the replace is because BC has a problem performing the division 0/0 therefore i need to replace the 0 with 1 to generate the result 0 (which is the same)

Thanks for any feedback you can give m8!

---

