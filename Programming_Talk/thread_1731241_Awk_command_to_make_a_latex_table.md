---
title: "Awk command to make a latex table"
date: 2011-04-16
forum: Programming Talk
---

### Post by rickcjmac on 2011-04-16
I frequently make latex tables from simple data files. For example I turn this output file

1.0  3.1  5.1  3.3
2.1  5.4  6.5  3.1
4.5  6.7  9.0  2.1

into a latex type table of the following format

1.0 & 3.1 & 5.1 & 3.3 \\
2.1 & 5.4 & 6.5 & 3.1 \\
4.5 & 6.7 & 9.0 & 2.1 \\

etc. I want to use an awk command to make file two given file one. Something like this might work:

```
awk '{print $1," & ", $2, " & ", $3, " \\\ "}' output.dat>table.dat

```

given the file "output.dat" to create "table.dat"

The problem I have is that the number of columns changes with each file. Is there a universal command that I could use as an alias to convert any shape of data file into a table format?

Thank you for your help :)

Richard

---

### Post by iponeverything on 2011-04-16
I think a small perl script could be made to handle it.

---

### Post by iponeverything on 2011-04-17
```
cat input | sed 's/[0-9+].[0-9+] /&\& /g' |sed 's/$/& \\\\/' >  table.dat
```

---

### Post by Vaphell on 2011-04-17
check this out
```
echo $'A B C\nD E F' | awk '$1=$1' OFS=' & ' ORS=' \\\\\n'

A & B & C \\
D & E & F \\

```

cool thing about awk is that it allows to configure field and record separators, both for input and output. As you may guess OFS is used to separate fields/columns in output, ORS separates lines/records
[http://www.math.utah.edu/docs/info/gawk_11.html](http://www.math.utah.edu/docs/info/gawk_11.html)

---

### Post by iponeverything on 2011-04-17
> **Vaphell said:**
> check this out
```
echo $'A B C\nD E F' | awk '$1=$1' OFS=' & ' ORS=' \\\\\n'

A & B & C \\
D & E & F \\

```

cool thing about awk is that it allows to configure field and record separators, both for input and output. As you may guess OFS is used to separate fields/columns in output, ORS separates lines/records
[http://www.math.utah.edu/docs/info/gawk_11.html](http://www.math.utah.edu/docs/info/gawk_11.html)

that is cool and handy.

---

### Post by kurum! on 2011-04-17
```

$ ruby -ne '$_=$_.chomp.split.join(" & ")+" \\\\\n";print'  file
1.0 & 3.1 & 5.1 & 3.3 \\
2.1 & 5.4 & 6.5 & 3.1 \\
4.5 & 6.7 & 9.0 & 2.1 \\


```

---

### Post by rickcjmac on 2011-04-17
Thank you for all of the quick responses! All of the code suggested works fine. For my purposes I think the best would be:

> cat output.dat | sed 's/[0-9+].[0-9+] /&\& /g' |sed 's/$/& \\\\/' >  table.dat

But when I run it I get the following "table.dat":

```

1 2 & 3 4 & 5 \\
2 3 & 4 5 & 6 \\
3 4 & 5 6 & 7 \\
4 5 & 6 7 & 8 \\
5 6 & 7 8 & 9 \\

```

That is the result given "output.dat" is:

```

1 2 3 4 5
2 3 4 5 6
3 4 5 6 7
4 5 6 7 8
5 6 7 8 9

```

How can this code be modified to put the "&" sign between each column?

Thank you again for all of your input :)

Richard

---

### Post by Vaphell on 2011-04-17
your sed doesn't work too well because you target [any digit,+][any char][any digit,+] and replace it with '&match &'. If you feed it with digit, space, digit, space, digit it will consume (digit, space, digit)

```
echo $'1 2 3\n1.1 2.2 3.3'
1 2 3
1.1 2.2 3.3

echo $'1 2 3\n1.1 2.2 3.3' | sed 's/[0-9+].[0-9+] /&\& /g' |sed 's/$/& \\\\/'
1 2 & 3 \\
1.1 & 2.2 & 3.3 \\

```

just target continuous blocks of whitespaces (\s+) and replace them with ' & ' to make sed replace whitespace separators of any width and composition (space, tab)
```
echo $'1 2 3\n1.1 2.2 3.3\n1    2\t\t3'
1 2 3
1.1 2.2 3.3
1    2		3


echo $'1 2 3\n1.1 2.2 3.3\n1    2\t\t3' | sed -r 's/\s+/ \& /g' | sed 's/$/ \\\\/g'
1 & 2 & 3 \\
1.1 & 2.2 & 3.3 \\
1 & 2 & 3 \\


```

also explain what you wanted to achieve with your original regex
[0-9+].[0-9+] is supposed to be 1-or-more digits, dot, 1-or-more digits? if so, there are 2 things wrong with it
. = any char (space included), escape it or put it in [ ] to mean literal dot
+ inside [ ] means literal + not 1-or-more, [0-9]+ is more like it

---

### Post by rickcjmac on 2011-04-17
I'm not going to lie, I didn't understand your last post, Vaphell. I am somewhat new to programming, and only as a hobby at best :)

I got the results with the following two terminal commands:

```
sed 's/ / \& /g' output.dat > table.dat
```
and
```
sed 's/$/ \\\\/g' table.dat > newtable.dat
```

This takes any number of columns in "output.dat" and inserts a "&" between them and inserts "\\" at the end of each line, which is perfect for what I need. 

Thank you all for your quick responses and help. The Ubuntu Community is AWESOME!!!

Richard

---

### Post by Vaphell on 2011-04-17
damn it, i spent quite some time to write the post and you didn't understand it >_<
:)


your regex [0-9].[0-9]
if your input is 1_2_3_4 (_ = space) it will get sliced to (1_2)(3_4) because . doesn't mean literal dot but any_char, space included - that's why you got 1_2 & 3_4

i suggested that you should replace \s+ with &
**\s+** stands for 1-or-more whitespace, \s - whitespace, + one-or-more

your version works too of course and is adequate in your case but it's a subset of my suggestion (single space fits in \s+) which is more flexible - it won't fail if you use tabs instead of spaces or put more tabs/spaces to separate data columns for clarity reasons or whatever. You should always aim at more robust solutions not baseline ones to have some overhead for unforeseen cases :)

---

