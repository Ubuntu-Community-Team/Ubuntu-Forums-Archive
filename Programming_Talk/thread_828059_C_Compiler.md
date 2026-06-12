---
title: "C Compiler"
date: 2008-06-13
forum: Programming Talk
---

### Post by 2words4uready on 2008-06-13
I am going to start programming in c and i was wondering what a good c compiler for ubuntu is
also i am planning on making the most basic os is c the right language for this:confused:

---

### Post by raul_ on 2008-06-13
gcc

gcc is not a compiler, it's THE compiler :cool:

Also, read the Sticky in the Programming Talk Section here in the forums

---

### Post by Uchiha_madara on 2008-06-13
Ubuntu is already Supports C Compiler 

you want to now how Create,Compile ,And Run it from Terminal

---

### Post by KingTermite on 2008-06-13
If a very basic OS, then yes, I'd say C would be the right way to go.

If you haven't yet, you need to install the Gnu Compiler Collection (which includes gcc - gnu c compiler).

**sudo apt-get install build-essential**

---

### Post by 2words4uready on 2008-06-13
yes i wnat to know how to create and compile

---

### Post by raul_ on 2008-06-13
[http://ubuntuforums.org/forumdisplay.php?f=39]("http://ubuntuforums.org/forumdisplay.php?f=39")

Read all the stickies

---

### Post by LaRoza on 2008-06-13
The sticky in this forum has a link to a how to.

---

### Post by Kadrus on 2008-06-13
```
sudo apt-get update
```
```
sudo apt-get install build-essential
```
open gedit:
```
#include<stdio.h>
int main()
{
printf("my first c program");
return 0;
}

```
save it ex.c
open terminal and type:gcc ex.c
then:./a.out

---

### Post by Kadrus on 2008-06-13
sorry for the double post..if any mods will delete this post..it will be appreciated..

---

