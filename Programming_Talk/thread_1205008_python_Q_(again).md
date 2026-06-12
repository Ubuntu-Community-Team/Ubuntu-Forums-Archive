---
title: "python Q (again)"
date: 2009-07-05
forum: Programming Talk
---

### Post by flyingsliverfin on 2009-07-05
if i want to have python read an input that is 18:00 and the input is all on one line how do i do that? 
im trying to do this challenge: [saving-time]("http://codegolf.com/saving-time") but cant even get the input!

---

### Post by unutbu on 2009-07-05
[PHP]#!/usr/bin/env python
import sys
print(sys.argv[1])
[/PHP]

LOL, according to [Code Golf rules ]("http://codegolf.com/help")> 

**You will be unable to import/require/include any modules** or files in your solution. You have to write all the code yourself, and it has to be in the code file you upload.

I don't know how you are expected to read from stdin if you aren't allowed to import sys. :)

Apparently there is a way however, since there is a python leader board... :-k

---

### Post by croto on 2009-07-05
You can get the input using python's built-in function raw_input.

---

### Post by unutbu on 2009-07-05
Ah yes. That's right. The challenge says "18:00" will be supplied on stdin, not as an argument.

Thanks, croto. :)

---

### Post by flyingsliverfin on 2009-07-05
whats stdin???? im confused...
whats the difference between stdin and just normal x = input()

---

### Post by Bodsda on 2009-07-05
> **flyingsliverfin said:**
> whats stdin???? im confused...
whats the difference between stdin and just normal x = input()

stdin is standard input, or the terminal.

```
time = raw_input("Enter time: ")
```

---

### Post by croto on 2009-07-05
This is my 279 bytes solution:
```

b,Q,O,s=' ','o\n\n','o',raw_input()
h,m,c,i=int(s[:2]),int(s[-2:]),list(b*8+O+'\n    o'+b*7+Q+' o'+b*13+Q+O+b*15+Q+' o'+b*13+Q+b*4+O+b*7+'o\n'+b*8+O),[8,22,40,59,77,92,102,84,63,43,26,14]
h%=12;m//=5
if h-m:c[i[h]],c[i[m]]='h','m'
else:c[i[h]]='x'
print reduce(lambda x,y:x+y,c)

```
still far from the 127 bytes winner!

---

### Post by flyingsliverfin on 2009-07-05
holy cow

---

### Post by snova on 2009-07-05
> **flyingsliverfin said:**
> whats stdin???? im confused...
whats the difference between stdin and just normal x = input()

stdin refers to STanDare INput, which is usually a terminal (but can be redirected from a file from the shell).

**input()** is not the same as **raw_input()**. **input()** is equivalent to **eval(raw_input())**, and you should avoid its use.

---

### Post by flyingsliverfin on 2009-07-06
oh... for the last couple months ive been using x = iinput()... ill start using raw_input


strange, just input() sounds more standard than raw_input

---

### Post by Can+~ on 2009-07-06
> **flyingsliverfin said:**
> oh... for the last couple months ive been using x = iinput()... ill start using raw_input


strange, just input() sounds more standard than raw_input

In python3 raw_input() was dropped, and input() behaves like raw_input (only accepts strings). Same thing happened to xrange() and range().

---

### Post by flyingsliverfin on 2009-07-06
ok good...whens python3 coming out?
or is it already out?

---

### Post by snova on 2009-07-06
> **flyingsliverfin said:**
> ok good...whens python3 coming out?
or is it already out?

It's already released. Depending on the version of Ubuntu you're running, you can install it from the **python3** package.

That isn't to say you should use it yet- there is very little third party support, so it's best to stick with 2.x for now.

---

### Post by flyingsliverfin on 2009-07-08
ok good!

---

