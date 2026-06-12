---
title: "Help sed Multi-Line, searching for sequence of lines starting with specific character"
date: 2009-11-25
forum: Programming Talk
---

### Post by john_spiral on 2009-11-25
Hi,

I've got my head round the basics of sed but I'm stumped for a solution on the below problem.

I would like sed to replace the beginning of the colored lines with two commas. In effect sed will be searching for a sequence of lines starting with specific characters.

A picture is worth a thousand words...

_Before_

[COLOR="Blue"]./[/COLOR]path/to/file/xyz
[COLOR="Blue"]File is on a network share.[/COLOR]
[COLOR="Blue"]Network Share name =[/COLOR] \\server\path\
[COLOR="Blue"]Path = [/COLOR]unique_value
[COLOR="Purple"]./[/COLOR]path/to/file/abc
[COLOR="Purple"]File is on a network share.[/COLOR]
[COLOR="Purple"]Network Share name =[/COLOR] \\server\path\
[COLOR="Purple"]Path = [/COLOR]more path info
Path = more path info
Path = more path info
[COLOR="Red"]./[/COLOR]path/to/file/efg
[COLOR="Red"]File is on a network share.[/COLOR]
[COLOR="Red"]Network Share name = [/COLOR]\\server\path\
[COLOR="Red"]Path = [/COLOR]more path info
Path = more path info
[COLOR="Sienna"]./[/COLOR]path/to/file/lmn
[COLOR="Sienna"]File is on a network share.[/COLOR]
[COLOR="Sienna"]Network Share name = [/COLOR]\\server\path\
[COLOR="Sienna"]Path = [/COLOR]more path info

_After_

[COLOR="Blue"], ,./[/COLOR]path/to/file/xyz
[COLOR="Blue"], ,File is on a network share.[/COLOR]
[COLOR="Blue"], ,Network Share name =[/COLOR] \\server\path\
[COLOR="Blue"], ,Path = [/COLOR]unique_value
[COLOR="Purple"], ,./[/COLOR]path/to/file/abc
[COLOR="Purple"], ,File is on a network share.[/COLOR]
[COLOR="Purple"], ,Network Share name =[/COLOR] \\server\path\
[COLOR="Purple"], ,Path = [/COLOR]more path info
Path = more path info
Path = more path info
[COLOR="Red"], ,./[/COLOR]path/to/file/efg
[COLOR="Red"], ,File is on a network share.[/COLOR]
[COLOR="Red"], ,Network Share name = [/COLOR]\\server\path\
[COLOR="Red"], ,Path = [/COLOR]more path info
Path = more path info
[COLOR="Sienna"], ,./[/COLOR]path/to/file/lmn
[COLOR="Sienna"], ,File is on a network share.[/COLOR]
[COLOR="Sienna"], ,Network Share name = [/COLOR]\\server\path\
[COLOR="Sienna"], ,Path = [/COLOR]more path info

any help will be greatly appreciated.

---

### Post by mo.reina on 2009-11-25
```
sed -e 's/^\(F\)/,,\1/g' -e 's/^\(N\)/,,\1/g' -e 's/^\(P\)/,,\1/g' -e 's/^\(\.\/\)/,,\1/g'

```

however this will include all lines starting with P.  in your example there are some lines with P that are not colored....

```
,,./path/to/file/xyz
,,File is on a network share.
,,Network Share name = \\server\path\
,,Path = unique_value
,,./path/to/file/abc
,,File is on a network share.
,,Network Share name = \\server\path\
,,Path = more path info
,,Path = more path info
,,Path = more path info
,,./path/to/file/efg
,,File is on a network share.
,,Network Share name = \\server\path\
,,Path = more path info
,,Path = more path info
,,./path/to/file/lmn
,,File is on a network share.
,,Network Share name = \\server\path\
,,Path = more path info

```

---

### Post by john_spiral on 2009-11-25
I would like to exclude those not colored, if possible.

---

### Post by mo.reina on 2009-11-25
need more information... are there always 4 lines one after the other that should have **,,**?  so like, first line starts with **./**, and the next 3 lines have **,,**?

---

### Post by john_spiral on 2009-11-25
**are there always 4 lines one after the other that should have ,,**

correct

The sequence is:

./$$$$
File is on a network share.
Network Share name = $$$
Path = $$$

where $$$ changes.

I would like to omit additional 'Path' lines with sed.

hope this helps clarify things.

---

### Post by mo.reina on 2009-11-25
```
 sed -e 's/^\(F\)/,,\1/g' -e 's/^\(N\)/,,\1/g' -e 's/^\(\.\/\)/,,\1/g' | sed '/,,N/{n;s/^/,,/;}'
```

sed finds lines beginning with **F**, **./**, and **N** and inserts **,,**.  then it finds the lines beginning with **,,N** and inserts **,,** at the beginning of the next line.

not the most elegant solution but it's a bit late here and this was the best i could do

output:
```
,,./path/to/file/xyz
,,File is on a network share.
,,Network Share name = \\server\path\
,,Path = unique_value
,,./path/to/file/abc
,,File is on a network share.
,,Network Share name = \\server\path\
,,Path = more path info
Path = more path info
Path = more path info
,,./path/to/file/efg
,,File is on a network share.
,,Network Share name = \\server\path\
,,Path = more path info
Path = more path info
,,./path/to/file/lmn
,,File is on a network share.
,,Network Share name = \\server\path\
,,Path = more path info

```

shoutout to Perderabo at the unix forums, one of his posts provided that last bit of code, i just modified it to fit the scenario.

---

### Post by john_spiral on 2009-11-25
looking good I'll give it a try, thank you so much for your assistance!

---

### Post by mo.reina on 2009-11-25
remember that sed doesn't write the changes to the file... you'll have to use the w option or redirect output with >

---

### Post by Arndt on 2009-11-25
> **mo.reina said:**
> remember that sed doesn't write the changes to the file... you'll have to use the w option or redirect output with >

Gnu sed does, with the option -i.

---

### Post by ghostdog74 on 2009-11-25
use sed for simple substitution. anything beyond, sed regex becomes ugly and hard to read.

here's gawk
```

awk '/^\.\//{ 
    c=3;
    print ",,"$0;next
}
c-->0 && !/^\.\// { 
    print",,"$0; next
}{print}' file

```
output
```

$ ./shell.sh
,,./path/to/file/xyz
,,File is on a network share.
,,Network Share name = \\server\path\
,,Path = unique_value
,,./path/to/file/abc
,,File is on a network share.
,,Network Share name = \\server\path\
,,Path = more path info
Path = more path info
Path = more path info
,,./path/to/file/efg
,,File is on a network share.
,,Network Share name = \\server\path\
,,Path = more path info
Path = more path info
,,./path/to/file/lmn
,,File is on a network share.
,,Network Share name = \\server\path\
,,Path = more path info


```

---

