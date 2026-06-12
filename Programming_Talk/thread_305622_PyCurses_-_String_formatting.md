---
title: "PyCurses - String formatting"
date: 2006-11-23
forum: Programming Talk
---

### Post by ironfistchamp on 2006-11-23
Hey all

I decided to take the plunge into curses. So far so good. Apart from one thing that I just haven't been able to work out. Say I have an int and I want to print a string containing it. In regular Python I would do this:

```

print "Integer a:", inta

```

I realised quickly that you can't do that so I have been concatenating strings with the + operator. That won't work with int's sadly. I have tried formatting the string like this:

```

stdscr.addstr("Integer a: %d") % (inta)

```

This causes my code to fail giving me the error " TypeError: unsupported operand type(s) for %: 'NoneType' and 'int'"

Can anyone help me work out what I am doing wrong and how I should be doing it instead.

Thanks

Ironfistchamp

---

### Post by ghostdog74 on 2006-11-23
how does ths whole code like? did you define inta?

---

### Post by po0f on 2006-11-23
ironfistchamp,

This is an off-the-wall response, but it also might be right.  Have you tried:
```
stdscr.addstr("Integer a: %d" % (inta))
```
Look at your position of parentheses and mine.  I'm guessing addstr() returns void, which is why Python is returning NoneType.

---

### Post by ironfistchamp on 2006-11-24
@po0f: You are a legend. Thanks that works perfectly.

---

### Post by DaveBorealis on 2006-11-24
> **ironfistchamp said:**
> I have been concatenating strings with the + operator. That won't work with int's sadly.

Hello,

If you caste the the integer to a string, it'll work.
```
inta = 3
print "integer a: " + str(inta)
```
Another possiblity, if you want...

Best regards,
Dave

---

### Post by ironfistchamp on 2006-11-24
That is another way I had thought about but I don't like converting ints to strings and the such like. I would much prefer to insert the variables with string formatting. Thankfully it works now.

Ironfistchamp

---

