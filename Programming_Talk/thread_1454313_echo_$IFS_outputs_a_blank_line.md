---
title: "echo $IFS outputs a blank line"
date: 2010-04-14
forum: Programming Talk
---

### Post by adit on 2010-04-14
What is the problem with this shell script?
```
#!/bin/bash
echo $IFS
```I expect the output
```
$' \t\n'
```but it actually outputs a blank line.

---

### Post by Penguin Guy on 2010-04-14
Maybe you have an alias or setting that is affecting it, perhaps [FONT="Courier New"]echo -E $IFS[/FONT] will work.

**[FONT="Courier New"]man echo[/FONT]**:
> 
       -E     disable interpretation of backslash escapes (default)


---

### Post by Bachstelze on 2010-04-14
> **adit said:**
> What is the problem with this shell script?
```
#!/bin/bash
echo $IFS
```I expect the output
```
$' \t\n'
```but it actually outputs a blank line.

Why would you expect that output? When the shell encouters a newline character, it starts a new line, it doesn't output '\n'.

---

### Post by adit on 2010-04-14
I want to print the value of IFS exactly as it is written.  How to do that?

---

### Post by Bachstelze on 2010-04-14
> **adit said:**
> I want to print the value of IFS exactly as it is written.  How to do that?

Define "as it is written".

---

### Post by adit on 2010-04-14
> Define "as it is written"As it is written means writing it down on a paper using a pen. If I am asked to write the value of IFS, I will write (in a paper)
$' \t\n'

---

### Post by Bachstelze on 2010-04-14
> **adit said:**
> As it is written means writing it down on a paper using a pen. If I am asked to write the value of IFS, I will write (in a paper)
$' \t\n'

Right, then you can use od:

```
firas@momiji ~ % echo $IFS | od -c   
0000000      \t  \n  \0  \n
0000005

```

It will print nothing for the leading space though. If you know your ASCII table, you can just print the hex values of the characters:

```
firas@momiji ~ % echo $IFS | od -t x1
0000000 20 09 0a 00 0a
0000005
```

---

### Post by geirha on 2010-04-14
In bash, «echo $IFS» will never output the content of the IFS variable, no matter what you set IFS to. (Well, unless you set it to an empty string, in which case it will output an empty string ;) ) 
```

$ IFS=test; echo $IFS
   
$

```

Why? Because after the variable is expanded, word-splitting occurs, and the splitting is done using each character of the IFS variable as delimiter, and since $IFS only expands to characters in the IFS (duh), it gets split into empty word(s). So in the case above,
```
IFS=test; echo $IFS
# is equivalent to
echo '' '' '' ''

```
echo outputs each argument with a space between them, and ends with a newline, so the output becomes three spaces and a newline.

```
$ echo $IFS | hd
00000000  20 20 20 0a                                       |   .|
00000004

```

If you double-quote the parameter expansion however, you are telling bash to treat everything inside the quotes as one word, and it won't change anything inside the quotes.

```
$ IFS=test; echo "$IFS"
test
$

```
This is why you should always quote parameter expansions. "$foo", "$(command)", "`command`", "${file%.mp3}" etc...

EDIT: Oh, and if you want to see the tab as the two characters \ and t, rather than a literal tab, you can use bash's builtin printf command. It has a special format; 

```
$ help printf | grep %q
      %q	quote the argument in a way that can be reused as shell input

```

So, with IFS at its default value:
```

$ printf "%q\n" "$IFS"
$' \t\n'

```

---

