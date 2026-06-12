---
title: "Weird Python Error"
date: 2005-07-03
forum: Programming Talk
---

### Post by Zatani on 2005-07-03
hey guys,

ok, probably a very noobish problem, but im out of ideas...i'm using python 2.4.1 with PyScripter as an IDE...ok, now the problem;

when i run this exact code;

number = input("Enter a number: ")
print number

i get this exact error in the interpretor window; 

Enter a number: Traceback (most recent call last):
  File "<string>", line 65, in run_nodebug
  File "<Module1>", line 1, in ?
EOFError: EOF when reading a line

anybody have any suggestions? thanks in advance,
Zan

---

### Post by crashtest on 2005-07-03
[QUOTE=Zatani]hey guys,

ok, probably a very noobish problem, but im out of ideas...i'm using python 2.4.1 with PyScripter as an IDE...ok, now the problem;

when i run this exact code;

number = input("Enter a number: ")
print number

i get this exact error in the interpretor window; 

Enter a number: Traceback (most recent call last):
  File "<string>", line 65, in run_nodebug
  File "<Module1>", line 1, in ?
EOFError: EOF when reading a line

anybody have any suggestions? thanks in advance,
Zan[/QUOTE]

I would suggest something like: number=raw_input("Enter a number: ") or you could do number=int(raw_input("Enter a number: "))

---

### Post by Zatani on 2005-07-03
i get the same problem with;

input()
raw_input()
int(raw_input())
eval(raw_input())

all of these give me the same error...any other suggestions?

thanks,
Zan

---

### Post by crashtest on 2005-07-03
[QUOTE=Zatani]i get the same problem with;

input()
raw_input()
int(raw_input())
eval(raw_input())

all of these give me the same error...any other suggestions?

thanks,
Zan[/QUOTE]

That is strange.  Try doing this at the python interactive prompt:

boone@disorder:~$ python
Python 2.4.1 (#2, Mar 30 2005, 21:51:10)
[GCC 3.3.5 (Debian 1:3.3.5-8ubuntu2)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> number=input("Enter a number: ")
Enter a number: 2
>>> print number
2
>>>

I wonder if the problem you're having is actually coming from pyscripter?  Let's find out if python itself is working.

---

### Post by buffbikedude on 2005-07-04
I'm confuzzled as well.

---

### Post by Zatani on 2005-07-05
you guys are right...when i went to the python promt, it worked fine...but in PyScripter it dosnt work, nor does it work in the interactive pyscripter promt...think it is my IDE?

thanks for all the help,
Zan

---

