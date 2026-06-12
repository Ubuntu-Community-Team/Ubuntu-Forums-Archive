---
title: "Grep Terminal Command Help"
date: 2013-06-05
forum: New to Ubuntu
---

### Post by Keiren on 2013-06-05
Hey this will be my first post to Ubuntu forms so i hope i am in the right place anyway here i go.

I am wanting to use the "grep" command to search and return the amount of times "G" occurs in the .txt file. (example below)

Name|Name_2|Address_1|Address_2|Address_3|Postcode|Phone_number

what i am trying to do is just search the column where all the postcodes are in (eg column 6). 


grep 'G' filename.txt -c

i understand that the command above will display every single "G" in the text file which is useless. What i am looking for is something like what is below 

grep 'G' column6 separated by | filename.txt -c 




would really appreciate if someone could help.

---

### Post by steeldriver on 2013-06-05
Hello and welcome to the forum

Are the entries literally formatted as shown in your example (i.e. exactly 5 fields ahead of the postal code, separated with pipe (|) characters)? if so you could do something with grep's extended regular expression (-E) mode e.g.

 ```
grep -E '([^|]*|){5}([^|]*G[^|]*)' *yourfile*
```

Alternatively, you could look at other tools like 'awk' which are often better for 'structured' input

```
awk -F"|" '$6 ~ /G/ {print}' *yourfile*
```

For the count using awk, the easiest way imho is just to pipe the output to the 'wc' program

```
awk -F"|" '$6 ~ /G/ {print}' *yourfile *| wc -l
```

however you *could* do the counting in awk if you wanted to

```
awk -F"|" 'BEGIN{n=0}; $6 ~ /G/ {n=n+1}; END {print n}' *yourfile*
```

---

### Post by sanderj on 2013-06-05
What I always do, is this: step by step, build a one-liner with filters in it.

My example input is in blabla.txt. See the end for content.

First print the file

```
cat blabla.txt 
```

Then use | as the seperator and get element 6 from each line:

```
cat blabla.txt | awk -F\| '{ print $6 }' 
```

Then find the letter G, and ignore case:

```
cat blabla.txt | awk -F\| '{ print $6 }' | grep -i G 
```

Then count the occurences:

```
cat blabla.txt | awk -F\| '{ print $6 }' | grep -i G | wc -l
```

Result:

```
sander@hapee:~$ cat blabla.txt | awk -F\| '{ print $6 }' | grep -i G | wc -l
2
sander@hapee:~$ 
```

Ah, that's correct!

blabla.txt:

```
Name|Name_2|Address_1|Address_2|Address_3|Postcode |Phone_number
Name|Name_2|Address_1|Address_2|Address_3|12345G|Phone_number
Name|Name_2|Address_1|Address_2|Address_3|Eg4444 |Phone_number
Name|Name_2|Address_1|Address_2|Address_3|abCDF |Phone_number

```

---

### Post by sandyd on 2013-06-05
moved to absolute beginners section

---

