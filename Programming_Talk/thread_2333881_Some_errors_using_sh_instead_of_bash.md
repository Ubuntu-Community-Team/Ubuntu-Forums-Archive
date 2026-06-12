---
title: "Some errors using sh instead of bash"
date: 2016-08-14
forum: Programming Talk
---

### Post by alfirdaous on 2016-08-14
[COLOR=#000000][FONT=verdana]Hello everybody,[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]I upgraded from Ubuntu 12.04 to 16.04, so some of my scripts in bash does NOT work, for example:
[/FONT][/COLOR][COLOR=#170072][FONT=monospace]
[/FONT][/COLOR]```

[COLOR=#170072][FONT=monospace]#!/bin/bash

[/FONT][/COLOR][COLOR=#170072][FONT=monospace]# Some other codes
[/FONT][/COLOR]
[COLOR=#170072][FONT=monospace][/FONT][/COLOR]for ((offset=$thumbStart; offset<=$thumbEnd; offset+=10))
        do
        printf -v outfile "$filePNG"_"%03d.png" "$((++n))"



```[COLOR=#170072][FONT=monospace]

Output:

[/FONT][/COLOR]```

# sh runScript.sh 
smartCode.sh: 459: functions.sh: Syntax error: Bad for loop variable

```[COLOR=#170072][FONT=monospace]
[/FONT][/COLOR]

I tried with another example, it returns the same error

```

#!/bin/bash

for (( i=0; i<=10; i+=2 ))
do
 echo "Welcome $i times" 
done
```


Using bash:

```

# bash test.sh 
Welcome 0 times
Welcome 2 times
Welcome 4 times
Welcome 6 times
Welcome 8 times
Welcome 10 times

```

But in some other scripts I've got some more errors using bash, how can I swap back using:

```

sh test.sh

```


Some info:

```

# lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial

======


# type bash
bash is /bin/bash

-========


# bash -version
GNU bash, version 4.3.46(1)-release (x86_64-pc-linux-gnu)
Copyright (C) 2013 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>


This is free software; you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.



```

Thanks in advance

---

### Post by sudodus on 2016-08-14
You tested the following for-loop. Its syntax is correct for the shell ***bash***.

```
#!/bin/bash

for (( i=0; i<=10; i+=2 ))
do
 echo "Welcome $i times" 
done
```

If you make the shellscript file executable

```
chmod ugo+x test.sh
```

you can also run it 'directly' by

```
./test.sh
```

and it selects shell interpreter from the **#!** statement, but I would recommend no extension or the extension bash instead of the extension sh for bash shellscripts to avoid confusion.

The shell ***sh*** has another syntax, and when you run

```
sh test.sh
```

you force the shell ***sh*** (the sh interpreter) to run the script, and it does not work, because it needs another syntax.

From ```
man sh
```

```
     The syntax of the for command is

           for variable [ in [ word ... ] ]
           do   list
           done
```

I think ***bash*** is a better shell than ***sh***, and I suggest that you convert statements that are unique for sh to the corresponding bash syntax.

---

### Post by sudodus on 2016-08-14
Maybe one of the following work-arounds with while loops from [shell script “for” loop syntax](https://stackoverflow.com/questions/1445452/shell-script-for-loop-syntax) will work for you, if you want to stay with the shell sh.

> These all do {1..8} and should all be POSIX. They also will not break if you put a conditional continue in the loop. The canonical way:

```
f=
while [ $((f+=1)) -le 8 ]
do
  echo $f
done
```

Another way:

```
g=
while
  g=${g}1
  [ ${#g} -le 8 ]
do
  echo ${#g}
done
```

and another:

```
set --
while
  set $* .
  [ ${#} -le 8 ]
do
  echo ${#}
done
```

---

### Post by alfirdaous on 2016-08-15
I will try that and get back to you

---

### Post by alfirdaous on 2016-08-24
I really appreciate your help guys, now I can use both "sh" ans "bash", **if you have any references to use bash statements instead of sh**?

---

### Post by sudodus on 2016-08-24
You can search the internet for **linux shell tutorial** and for **bash tutorial**. I did and found several good links - look at them, and I think you will find some links, that will give you what you need.

You can also start from this link: [UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal), which contains many links at the end of the page.

---

### Post by alfirdaous on 2016-08-24
I appreciated that, thanks a lot

---

