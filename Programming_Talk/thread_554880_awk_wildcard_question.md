---
title: "awk wildcard question"
date: 2007-09-19
forum: Programming Talk
---

### Post by Krijk on 2007-09-19
I want to output all fields after a certain number (in sample field 6).  The problem is that I don't know how many fields there are until the end of the line.

```

File format
1 2 3 4 5 6 -> X /n

File sample
1 2 3 4 5 6 7 8 9 
1 2 3 4 5 6 7
1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 
1 2 3 4 5 6 7 8 9 10
1 2 3 4 5 6 
```

How can I use a wildcard in awk to achieve this?


 ```
awk ' { print $6 to endofline }'

```

---

### Post by stylishpants on 2007-09-19
Awk has a fairly limited set of wildcards, and I don't think any of them are right for you.  Here's a non-wildcard solution:

```
fhanson@fhanson:/tmp$  awk '{for (i=7; i<=NF; i++) printf("%s ",i);printf ("\n")}' file
7 8 9 
7 
7 8 9 10 11 12 13 14 15 
7 8 9 10 


```

Note that it will print a blank line if the line has less than 7 columns.

---

### Post by Krijk on 2007-09-19
> **stylishpants said:**
> Awk has a fairly limited set of wildcards, and I don't think any of them are right for you.  Here's a non-wildcard solution:

```
fhanson@fhanson:/tmp$  awk '{for (i=7; i<=NF; i++) printf("%s ",i);printf ("\n")}' file
7 8 9 
7 
7 8 9 10 11 12 13 14 15 
7 8 9 10 


```

Note that it will print a blank line if the line has less than 7 columns.

This works but I don't understand the command :confused: It gives the number of fields in numbers.

In the file that is going to be used as input the fields after 6 are a word or multiple words which are seperated by spaces. These spaces cause me problems with the fieldnumbers.

I think I can use this as input in awk if I precede these with $ to create 
the awk command I need.

```
awk ' { print $6 $7 $8 etc }'
```

I've tried with 
```
awk '{for (i=6; i<=NF; i++) printf("%s $",i);printf ("\n")}' file
```

but I get the wrong output:
```
6 $7 $8 $9 $10 $11 $12 $13 $
```

This manipulations of strings cause me a lot of headaches, but who wants to learn has to work for it. No pain, no gain.

---

### Post by stylishpants on 2007-09-19
Oh, I see what you mean.  My solution was wrong and only appeared correct because of the input data.  The problem is that the field number was being printed out by my solution, instead of the field content.

OK, so then I think this is what you're trying to do:

```

awk '{for (i=6; i<=NF; i++) printf("%s ",$i);printf ("\n")}' file

```

You were right except for a misplaced $.

One problem still remains with this solution though.  It will throw away the spacing between the columns and replace it with a single space.

Here is an example:

```
fhanson@fhanson:/tmp$ cat file
1 2 3 4 5 F G H I 
1 2 3 4 5 F G
1 2 3 4 5 F G H I J K L           M N O
1 2 3 4 5 F G H I J
1 2 3 4 5 F
fhanson@fhanson:/tmp$ awk '{for (i=6; i<=NF; i++) printf("%s ",$i);printf ("\n")}' file
F G H I 
F G 
F G H I J K L M N O 
F G H I J 
F 

```

I don't know if this matters to you.  If so, it might be time to move up to perl.

---

### Post by ghostdog74 on 2007-09-19
In awk, to get the value of last field, you use $NF. To get number of fields, you use NF.
here's how you can do it
```

 awk '{ 
             for(x=6;x<=NF;x++) {
                printf "%s%s",$x,OFS
              } 
              {printf "\n"}
' file

```

---

### Post by starscalling on 2009-01-03
> **ghostdog74 said:**
> In awk, to get the value of last field, you use $NF. To get number of fields, you use NF.
here's how you can do it
```

 awk '{ 
             for(x=6;x<=NF;x++) {
                printf "%s%s",$x,OFS
              } 
              {printf "\n"}
' file

```

yeah that's the ticket
i needed to remove the first field of a file b/c the only avaliable copy was html so had to c/p from the displayed page to a file and then remove the line numbers as so:

```
cat /path/to/file |awk '{ for(x=2;x<-NF;x++) {printf "%s%s" ,$x,OFS } {printf "\n"}'}
```

good ups on ya ^^

---

### Post by ghostdog74 on 2009-01-03
> **starscalling said:**
> 

```
cat /path/to/file |awk '{ for(x=2;x<-NF;x++) {printf "%s%s" ,$x,OFS } {printf "\n"}'}
```


no need cat.

---

