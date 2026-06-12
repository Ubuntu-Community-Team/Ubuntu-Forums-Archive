---
title: "Uncought Error1 in Makefile"
date: 2011-02-01
forum: Programming Talk
---

### Post by fibo.kowalsky on 2011-02-01
I have a Makefile:
```
SHELL = /bin/bash
URL = "http://google.com"

all : T1 T2

T1 : 
    wget -O web_page $(URL)  

T2 : T1
    egrep -ic '<p>' web_page
```

Simple make file, download page in file and count <p> tags there.
The error is raised only when there is no <p> tags in file (e.g. in google.com page).
```
2011-01-18 18:16:57 (738 KB/s) - `web_page' saved [9928]

egrep -ic '<p>' web_page
0
make: *** [T2] Error 1

```
so when output is 0, but the command
```
egrep -ic '<p>' web_page
```
is ok and working in shell.
-
I do not understand what make does't like?

---

### Post by Arndt on 2011-02-02
> **fibo.kowalsky said:**
> I have a Makefile:
```
SHELL = /bin/bash
URL = "http://google.com"

all : T1 T2

T1 : 
    wget -O web_page $(URL)  

T2 : T1
    egrep -ic '<p>' web_page
```

Simple make file, download page in file and count <p> tags there.
The error is raised only when there is no <p> tags in file (e.g. in google.com page).
```
2011-01-18 18:16:57 (738 KB/s) - `web_page' saved [9928]

egrep -ic '<p>' web_page
0
make: *** [T2] Error 1

```
so when output is 0, but the command
```
egrep -ic '<p>' web_page
```
is ok and working in shell.
-
I do not understand what make does't like?

When 'egrep' doesn't find anything, it returns a non-zero status, and 'make' interprets that as an error.

---

### Post by Vox754 on 2011-02-02
> **Arndt said:**
> When 'egrep' doesn't find anything, it returns a non-zero status, and 'make' interprets that as an error.

Exactly. That's not a real error, because the command was executed successfully.

If you want "make" to ignore the return value, and perhaps continue with further rules, you can add a hyphen before the command to be executed.
```

T2 : T1
	- egrep -ic '<p>' web_page

```

You can use this when you operate on files that may or may not be present.
```

clean :
	- rm *.bak *.loc

```

---

