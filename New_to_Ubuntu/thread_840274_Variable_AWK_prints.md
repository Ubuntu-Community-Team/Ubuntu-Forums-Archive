---
title: "Variable AWK prints ???"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by M.Kalavera on 2008-06-25
Hi people,
is it possible to make the print commands ($2 and $12) in this AWK script variable, so that I can control it with and config.file ???
Thx for your help,
M.Kalavera

grep "^ENERGY:" /usr/people/log.file \
| awk {'print $2,$12'} \
> /usr/people/temp.dat

---

### Post by _sphinx_ on 2008-06-25
I am not getting you. Can you please explain your problem in a bit more detail. 
The script that you have mentioned should give you the $1 and $12 in you /usr/people/temp.dat file.

---

### Post by Cypher on 2008-06-25
If I understand the OP, he wants to control WHICH field he prints, i.e., $1 and $12 or $2 and $4 from a config file. 

There is no way of feeding that variable into the variable directly. So the only hack'ish way I know to make this work is to have seperate commands based on various permuations you concieve on having..

---

### Post by webofunni on 2008-06-25
> awk {'print $2,$12'}

That will give syntax error. Correct syntax is 

```
awk '{print $2, $12}'
```

---

### Post by _sphinx_ on 2008-06-25
To control with bash?
I mean, does he want $1 etc.. in bash?

---

### Post by _sphinx_ on 2008-06-25
> **webofunni said:**
> That will give syntax error. Correct syntax is 

```
awk '{print $2, $12}'
```

That is no problem.

---

### Post by webofunni on 2008-06-25
> That is no problem.

```
$ cat test.txt | awk {'print $2,$12'}
awk: print $2,$12
awk: ^ syntax error

```

[http://www.gnu.org/manual/gawk/html_node/Print-Examples.html](http://www.gnu.org/manual/gawk/html_node/Print-Examples.html)

---

### Post by Cypher on 2008-06-25
> **_sphinx_ said:**
> To control with bash?
I mean, does he want $1 etc.. in bash?
Yeah..that would be my guess..so a config file would have, F1=1 and F2=12 for the 2 fields and he wants to do '{print $F1,$F2}'..

---

### Post by _sphinx_ on 2008-06-25
> **webofunni said:**
> ```
$ cat test.txt | awk {'print $2,$12'}
awk: print $2,$12
awk: ^ syntax error

```
yup I know it's not the convention but before posting I checked and the following command runs fine.
```

awk {'print $1'} <filename>

```

---

### Post by webofunni on 2008-06-25
Hi sphinx,

  Yes, that will work. But you need to place a space before the second variable, is you have more than one variable to print in awk. 

  Also the actual syntax of awk is :

```
awk '{print $num}'
```

  You will get syntax error from some Linux systems if you are using 

```
awk {'print $num'}
```

---

### Post by M.Kalavera on 2008-06-26
Hey buddy's, thx for all the replies so far.
I will explain my problem in more detail, but Cypher got my problem very well:

1.) my script is working fine with the syntax shown in my first post <pre>| awk {'print $2,$12'}</pre> 

2.) I want to do a lot of plotting with gnuplot and control it with a central config data or a menu. For this step the $2,$12 would have to be "variables" like $x_data,$y_data e.g. , but I don't have any idea how to solve this problem, because all I tried didn't work. 
Is it possible to make this function variable or not ?? Otherwise I have to produce 14 scripts, which seems to be a noobish solution :D

MFG M.Kalavera

---

### Post by ghostdog74 on 2008-06-27
> **M.Kalavera said:**
> Hi people,
is it possible to make the print commands ($2 and $12) in this AWK script variable, so that I can control it with and config.file ???
Thx for your help,
M.Kalavera

grep "^ENERGY:" /usr/people/log.file \
| awk {'print $2,$12'} \
> /usr/people/temp.dat

whenever you want to use awk, there is no need to use grep anymore
```

awk '/^ENERGY/{print $2,$12}' /usr/people/log.file > outputfile

```

as for your problem, 2 possible ways
1) since you know that $2 and $12 are what you need, then use them as you process the file
2) store your $2, $12 results in associative arrays . eg x_data[$2], y_data[$12]. If you want counteres, then x_data[++x]=$2, y_data[++y]=$12

for more information see the gawk/awk manual

---

