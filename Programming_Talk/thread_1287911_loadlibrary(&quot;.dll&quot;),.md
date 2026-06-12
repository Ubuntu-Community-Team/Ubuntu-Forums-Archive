---
title: "loadlibrary(&quot;.dll&quot;),"
date: 2009-10-10
forum: Programming Talk
---

### Post by 65daysofstatic on 2009-10-10
hi,

I am programming a C application, and I need to use a dll, bbut the function LoadLibrary cant find the .dll
I already installed it on both folders, system32 and system

if(hCode = LoadLibrary("name.dll")){
     ...
     ....
}
Later, I found that LoadLibraryA(".dll") exists, and it worked.
But I want  to know, why it doesnt work with the function LoadLibrary?.

thx
65dos

---

### Post by dwhitney67 on 2009-10-10
Que???

---

### Post by MadCow108 on 2009-10-10
use GetLastError to get the error LoadLibrary spits out
[http://msdn.microsoft.com/en-us/library/ms684175(VS.85).aspx](http://msdn.microsoft.com/en-us/library/ms684175(VS.85).aspx)

also this is mostly a linux programming forum, maybe you get better help in a windows specific forum

---

### Post by Can+~ on 2009-10-10
I think LoadLibrary checks the current working directory, instead of the system and system32.

> Que???

En verdad, se escribe: "¿Qué?"

---

### Post by 65daysofstatic on 2009-10-10
> **MadCow108 said:**
> use GetLastError to get the error LoadLibrary spits out
[http://msdn.microsoft.com/en-us/library/ms684175(VS.85).aspx](http://msdn.microsoft.com/en-us/library/ms684175(VS.85).aspx)

also this is mostly a linux programming forum, maybe you get better help in a windows specific forum

Since the title of the forum is : "Programming Talk
This forum is for all programming questions.
The questions do not have to be directly related to Ubuntu and any programming language is allowed. "

i wanted to give it a try :P

I dont know if GetLastError will work, since there aren't errors, it just doesnt find the .dll and returns null.
The weird thing is that LoadLibraryA finds the .dll :S

thanks

---

### Post by dwhitney67 on 2009-10-10
> **Can+~ said:**
> 
En verdad, se escribe: "¿Qué?"
How can I do that?... that is, enter non-ASCII characters in my posts?


Oops, I have hijacked a thread!

---

### Post by -grubby on 2009-10-10
> **dwhitney67 said:**
> How can I do that?... that is, enter non-ASCII characters in my posts?!

Usually by copying and pasting them, or having a special character set, or using special key combinations.

---

### Post by Can+~ on 2009-10-10
> **dwhitney67 said:**
> How can I do that?... that is, enter non-ASCII characters in my posts?


Oops, I have hijacked a thread!

Having the spanish keyboard layout :P, and input encoded in UTF-8 (Although I still prefer english Ubuntu).

¿?, ¡!, tíldes.

In the spanish layout, the key before the backspace has the ¡ and ¿.

---

