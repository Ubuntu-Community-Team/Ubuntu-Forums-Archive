---
title: "Find out the address of bin/sh?"
date: 2010-04-01
forum: Programming Talk
---

### Post by yasokrish on 2010-04-01
Hi,

How to put the string "/bin/sh" into the memory, and get its address. ???
I read this can be done with the help of Environment variables?
Am new to linux ,please do explain step by step by procedure...
Very urgent..pl do help..


Thank you,
yasokrish.:confused:

---

### Post by yasokrish on 2010-04-01
Hi,

How to put the string "/bin/sh" into the memory, and get its address. ???
I read this can be done with the help of Environment variables?
Am new to linux ,please do explain step by step by procedure...
Very urgent..pl do help..


Thank you,
yasokrish.:confused:

---

### Post by DrMelon on 2010-04-01
First things first, what is this for? Is it a programming problem? If it's a programming issue, which language are you using?

Please give us more information! :KS

---

### Post by yasokrish on 2010-04-01
Hi,

How to put the string "/bin/sh" into the memory, and get its address. ???
I read this can be done with the help of Environment variables?
Am new to linux ,please do explain step by step by procedure...
Very urgent..pl do help..for my project?


Thank you,
yasokrish.:confused:

---

### Post by yasokrish on 2010-04-01
Hi,

How to put the string "/bin/sh" into the memory, and get its address. ???
I read this can be done with the help of Environment variables?
Am new to linux ,please do explain step by step by procedure...
Very urgent..pl do help..


Thank you,
yasokrish.:confused:

---

### Post by yasokrish on 2010-04-01
Hi,
Am doing the project "return to libc attacks"
I am doing it in C language.
 :)

Thank u,
yasokrish.

---

### Post by yasokrish on 2010-04-01
Hi,
Am doing a project "Return to libc attacks"
Am doing the project in C programming.

Thanks,
Yasokrish

---

### Post by Chesamo on 2010-04-01
Create an array of eight characters and set its value equal to "/bin/sh\0".

Print the address by casting the array as an unsigned int and using printf. (Remember that the name A of an array A[] is the same as &A[0].)

[I'm not going to give you the code](http://catb.org/~esr/faqs/smart-questions.html#homework), but there's the logic.

---

### Post by HellBoz on 2010-04-01
```
string sh = "/bin/sh";
string * shPointer = &sh;
```

```
Memory address of < /bin/sh >: 0x22ff30
```

---

### Post by lisati on 2010-04-01
Multiple threads with the same question. Not cool.

---

### Post by cubeist on 2010-04-01
This sort of sounds like a homework problem and we don't complete other people's homework on these forums; however, we are always happy to offer hints.

Edit - provided a solution to a different thread...oops!

---

### Post by lisati on 2010-04-01
Edit: see below
> **cariboo907 said:**
> Please don't create multiple threads on the same subject. I have merged your 4 threads.

---

### Post by cariboo on 2010-04-01
Please don't create multiple threads on the same subject. I have merged your 4 threads.

---

### Post by Cracauer on 2010-04-01
The OP makes it very clear that his assignment is writing a break-in into some software package, presumably starting out from minimal code inserted via a buffer overflow. 

Specifically he has been instructed to use the current techniques to get around newish OSes improved page protection schemes that block straight buffer overflow exploits (place code, then overwrite function return address to jump there).

So help him already, you slackers :)

---

### Post by yasokrish on 2010-04-02
HI,
Am doing a project on "return to libc attacks"
To put the string "/bin/sh" in the memory and find out the address,
this code is being used.
Can anyone explain on this?
Why do we use export? and use of export should be done inside the porgram or in terminal?
am new user of linux and c programming.
Pl do explain?

Thanks,
Yasokrish

---------------------------------------------
$ export MYSHELL=/bin/sh

void main(){
  char* shell = getenv("MYSHELL");
  if (shell)
     printf("%x\n", (unsigned int)shell);
}
-------------------------------------------------

---

### Post by gnometorule on 2010-04-02
Export is a command of the Unix shell. What you see in the same line right after it; defines a (temporary) Unix shell variable. 'Export' makes the scope of that variable global, so you can use it later as you see.

---

### Post by yasokrish on 2010-04-02
Thanks a lot :)

---

### Post by bapoumba on 2010-04-03
One additional thread merged..

---

### Post by yasokrish on 2010-04-03
Can anyone explain me the usage of export with examples.
To find the address of "/bin/sh" in c programming.


Thank u,
yasokrish

---

### Post by Sef on 2010-04-03
Merged threads.  Please do not open up a new thread on the same topic.  Thank you.

---

### Post by cubeist on 2010-04-03
> **yasokrish said:**
> Can anyone explain me the usage of export with examples.
To find the address of "/bin/sh" in c programming.


Thank u,
yasokrish

Go Away, go use Google like the rest of us.
[URL="http://www.lmgtfy.com/?q=export+bash"]
http://www.lmgtfy.com/?q=export+bash[/URL]

---

