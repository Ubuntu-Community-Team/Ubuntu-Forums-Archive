---
title: "Shell Script Parsing Pipe Feed"
date: 2012-01-05
forum: Programming Talk
---

### Post by CrusaderAD on 2012-01-05
I'm doing a bit of shell scripting and I have a pipe feed like so...

```
value1|value2|value3
```

How do I parse this out and get each value into it's own variable?

---

### Post by gnometorule on 2012-01-05
Could you clarify? Are those values you feed as command line parameters? If yes, you can read them in as follows (assuming you have no options for your command/script name):

```

#!/bin/bash
value1=$1
value2=$2
value3=$3

```This is probably not what you want as you pipe value1 into value 2 etc, but so far, I'm not quite sure what exactly you try to do. If instead you have 3 commands, and you want to pipe the result of command 1 into 2 (etc), then you would probably be better off to make them functions (if it's your script), or use the command line directly, as in:

```

#!/bin/bash
value1=0
value2=0
value3=0

function1() {
...
echo $value1
#note: this echo should be last line
}

function2() {
# for f, insert your calculation(s) using value1
value2=f($1)
echo $value2
}

(similar for function3())

#this assumes you do not hand on a value to function1
value1=`function1`
value2=`function2 $value1`
value3=`function3 $value2`

```Notation and use of local/global vars could be improved, but that's the gist.

---

### Post by erind on 2012-01-05
> **CerealCypher said:**
> I'm doing a bit of shell scripting and I have a pipe feed like so...

```
value1|value2|value3
```How do I parse this out and get each value into it's own variable?


Having each value extracted into variables could prove very difficult. The easiest way would be using temporary files with **tee**, then process each output file. For instance:

   ```
 ls | tee ls_out | grep f | tee grep_out | xargs file | tee xargs_out
``````
$ ls -1
f1
f2
f3
k1
k2
k3

$ ls | tee ls_out | grep f | tee grep_out | xargs file | tee xargs_out
f1: ASCII text
f2: ASCII text
f3: ASCII text

$ head *_out
==> ls_out <==
f1
f2
f3
k1
k2
k3

==> grep_out <==
f1
f2
f3

==> xargs_out <==
f1: ASCII text
f2: ASCII text
f3: ASCII text

```P.S. In case you need the individual pipeline *exit statuses* take a look at the *bash *variable **PIPESTATUS**, ( [I]echo ${PIPESTATUS
[*]}[/I] ).

[http://tldp.org/LDP/abs/html/internalvariables.html](http://tldp.org/LDP/abs/html/internalvariables.html)

---

### Post by CrusaderAD on 2012-01-06
Figured it out, this is what worked for me.

```
#! /bin/bash
### GRAB THE FILE
file="/home/user/mysqldump.txt"
### LOOP THE FILE
while read -r line
do
echo -e "\033[32m \033[1m Sorting Feed... \033[0m"
### CREATE A TEMP FILE TO EXCHANGE DATA IN
echo ${line} >> /home/user/mysqldumptest.txt
### STORE THE VALUES IN A VARIABLE
value1=`awk -F'|' '{ print $1 }' /home/user/mysqldumptest.txt`
value2=`awk -F'|' '{ print $2 }' /home/user/mysqldumptest.txt`
value3=`awk -F'|' '{ print $3 }' /home/user/mysqldumptest.txt`
value4=`awk -F'|' '{ print $4 }' /home/user/mysqldumptest.txt`
### WRITE TO SCREEN IF YOU WANT UNCOMMENT
#echo -e $value1
#echo -e $value2
#echo -e $value3
#echo -e $value4
### STORE IN MYSQL
mysql --host=localhost --user=username --password=password databasename << EOF
insert into table (1,2,3,4) values('$value1','$value2','$value3','$value4');
EOF

#echo -e "\033[32m \033[1m Ending Test... \033[0m"
### DELETE TEMP FILE
rm /home/user/mysqldumptest.txt
done < "$file"
```

---

### Post by sisco311 on 2012-01-06
Check out BashFAQ 001 (link in my signature).

I think, you could do something like:
```


while IFS='|' read -r v1 v2 v3 v4; do
    printf  '%s\n' "$v1" "$v2" "$v3" "$v4"
done < /home/user/mysqldump.txt


```

---

