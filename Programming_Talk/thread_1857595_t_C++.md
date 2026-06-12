---
title: "\t? C++"
date: 2011-10-10
forum: Programming Talk
---

### Post by Carpentr on 2011-10-10
Hey all, I'd appreciate some help with a question I have.

When using: ```
\t
```

Does anyone happen to know exactly how many spaces it uses?

---

### Post by Smart Viking on 2011-10-10
On my system it's 8.

I think that's up to the system to decide, not sure though. 8 is very common.

---

### Post by karlson on 2011-10-10
> **Carpentr said:**
> Hey all, I'd appreciate some help with a question I have.

When using: ```
\t
```

Does anyone happen to know exactly how many spaces it uses?

From what I have seen it's 8 but you might want to change the tab stops using stty on your terminal and see if that changes the behavior of \t.

---

### Post by Arndt on 2011-10-10
> **Carpentr said:**
> Hey all, I'd appreciate some help with a question I have.

When using: ```
\t
```

Does anyone happen to know exactly how many spaces it uses?

The answer has nothing to do with C++, in any case.

The only value you can foist on any one else with any chance of success is 8, for traditional reasons (but there used to be terminals with other settings). For yourself, you can define it to whatever you like, in the terminal or editor.

---

### Post by MG&amp;TL on 2011-10-10
Press <TAB> in editor of choice and find out.

---

### Post by Carpentr on 2011-10-10
I didn't know that it was system defined, but it's good to know now. I was just curious as I am using it in a console application I'm making.

Thanks for the help and quick answers! Live and learn I guess. :)

---

### Post by Vaphell on 2011-10-10
in my gedit you'd get 2.
depends what you want, if you spit something out to standard output then 8 is a good assumption, but in case of human readable plain text files that people open with customized editors all bets are off.
Also tab is not necessarily putting fixed amount of spaces, more often than not it moves the cursor to the next stop at n*TAB_WIDTH+1

```
$ echo $'xxxxxxx\tx\nx\tx'
xxxxxxx	x
x	x

```

---

### Post by 11jmb on 2011-10-11
As said above it is not c++ dependent, you can change your tabs with by using 

```
tabs -n (number of spaces)
```

---

### Post by 11jmb on 2011-10-11
> **11jmb said:**
> As said above it is not c++ dependent, you can change your tabs with by using 

```
tabs -n (number of spaces)
```

Sorry, I was not clear. insert number of spaces per tab in for n, for example 

```
tabs -5
```

will make your program print 5 spaces per tab

---

### Post by Bachstelze on 2011-10-11
> **11jmb said:**
> Sorry, I was not clear. insert number of spaces per tab in for n, for example 

```
tabs -5
```

will make your program print 5 spaces per tab

More accurately, it will make the terminal display five spaces when the program prints a tab. It does not change the program in any way.

---

