---
title: "bash AWK highlight if a () is present"
date: 2012-05-29
forum: Programming Talk
---

### Post by thatdamkid on 2012-05-29
Better question, I'm just going to pipe in a new awk but I would like to know how to use awk to color certain characters. I know its going to be a IF THEN case but my awk skills are terrible and any help will be useful.

```

Hello
I have an awk script that reads a file. and spits text out in this format.

 [CODE]    AB_CDEFGHI
    b123456789
    2018905 is in the office

    AB_CDEFGHI
    b23456789
    (BOSS) 2027805 is in the office.

    AB_CDEFGHI
    b7890234
    (CFO) 2072243 is away.
```

This is the line of code that I am using in oder to print out the above.

```
awk "/$dep/"'{print; getline; print; getline; print; getline; print}' ~/office/atten
```

$dep refers to/reads the AB_CDEFGHI line and then it prints out the next two lines

What I want to be able to do is highlight any occurrence of parenthesis ()

So that the output looks some what like this


    AB_CDEFGHI
    b123456789
    2018905 is in the office

    AB_CDEFGHI
    b23456789
    [COLOR="Red"](BOSS)[/COLOR] 2027805 is in the office.

    AB_CDEFGHI
    b7890234
    [COLOR="red"](CFO)[/COLOR] 2072243 is away.

Not that (CFO) (BOSS) are only two of many strings that can appear in parenthesis. The contents within do not have to be highlighted just the parenthesis would do too.

I know that in itself that that's some pretty ugly code that I have but it works for what i am doing.
[/code]

---

### Post by codemaniac on 2012-05-29
You need to use ANSI escape sequence in your awklet .
[http://en.wikipedia.org/wiki/ANSI_escape_code](http://en.wikipedia.org/wiki/ANSI_escape_code)
Something like below .

```
awk "/$dep/"'{print "\033[1;31m" $0 "\033[0m"; getline; print; getline; print; getline; print}' ~/office/atten
```

---

### Post by Vaphell on 2012-05-29
what about piping the awk output to grep?

```
awk ... | grep -E '[(].*[)]|$'
```
it will print all lines thanks to $ and (.*) will be in color.

---

### Post by thatdamkid on 2012-05-31
Both of you guys helped out a lot. I ended up using a combination of both of your suggestions and everything is now working as is intended.

---

### Post by codemaniac on 2012-05-31
> **thatdamkid said:**
> Both of you guys helped out a lot. I ended up using a combination of both of your suggestions and everything is now working as is intended.

thatdamkid great .That is really a good news .

---

