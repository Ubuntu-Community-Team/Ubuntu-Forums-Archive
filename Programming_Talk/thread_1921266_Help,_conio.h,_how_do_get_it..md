---
title: "Help, conio.h, how do get it."
date: 2012-02-06
forum: Programming Talk
---

### Post by rafaelcbf on 2012-02-06
I'm taking some programming classes, and our teacher uses conio.h a lot. I use Geany to compile, build and run our little projects, but it says that conio.h is not present or something like that. What are other headers I can use in place of conio.h, or how can I get it? I've checked other forums, and I realize that conio.h is obsolete, but you know how teachers are. I really really really need the help.

---

### Post by Bachstelze on 2012-02-06
conio.h is available only on Windows nowadays. If you have to use it, compile your code on Windows.

---

### Post by korgoth28 on 2012-02-06
Curses provides similar functions. You can ask your teacher if that's acceptable. If he's a college prof he should have linux handy and won't mind.

I assume just downloading some free windows C compiler (one of my old books recommended bloodshed) and running it under wine would work.

---

### Post by rafaelcbf on 2012-02-06
Dang, guess I'm screwed then, I only work with ubuntu, I have no other OS on my netbook. All he cares about is that the programs function, not what headers we use, is there any other I can use? Or what compiler can I use with wine, I'm still not sure how to use it, some times things run some times they don't

---

### Post by Bachstelze on 2012-02-06
> **rafaelcbf said:**
> Dang, guess I'm screwed then, I only work with ubuntu, I have no other OS on my netbook. All he cares about is that the programs function, not what headers we use, is there any other I can use? Or what compiler can I use with wine, I'm still not sure how to use it, some times things run some times they don't

Apparently, Bloodshed/DevC++ wors fine in Wine

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=1178](http://appdb.winehq.org/objectManager.php?sClass=application&iId=1178)

But if you only need to provide the same functionality, depending on what your program must do, you may be able to do it with only standard C functions (i.e. without ncurses).

---

### Post by rafaelcbf on 2012-02-06
Well this is one of them, it's in Spanish, it's soused to add a number by the same number and then multiply it by 2. 

[PHP]#include <stdio.h>
#include <conio.h>
int main()
{
int num1, num2, res2, res1, res2;
printf("anote el primer numero/n");
scanf("%i",&num1);
printf("Anote el segundo numero/n");
scanf("%i",&num2");
res=num1+num2;
res2=res1*2;
printf("El resultado de la suma es: %i /n y el de la multiplicacion es: %i",res1, res2);
getch();
return 0;
}
[/PHP]

What would be another way to wright this? for use in ubuntu. it's c++

---

### Post by Zugzwang on 2012-02-06
Technically, the posters above are right: there is no replacement for conio.h in Linux, as it is Windows-only.

*However*, since you are learning and can't get around it, here is some hack that you might want to try. In [this]("http://ubuntuforums.org/showpost.php?p=8485667&postcount=3") post, there is the source code of a header file (conio.h) and a source file (conio.c). Copy them to the directory in which you compile your program, and add conio.c to your compilation command. For example, if you compiled using "g++ mycode.cpp -o myexecutable", then it would be "g++ mycode.cpp conio.h -o myexecutable" afterwards. Chanches are good that your teacher only uses basic functionality, and then this path should work.

EDIT: Don't forget to replace the reference by "gconio.h" in the "conio.c" by "conio.h" then.

---

### Post by rafaelcbf on 2012-02-06
Can you elaborate little more on the explanation, I don't understand. :S Sorry I'm really new at this.

---

### Post by rafaelcbf on 2012-02-06
Nevermind, I found out that if I use:
[PHP]#include <iostream>[/PHP]
everything works out. Now I just have some debug problems, Can you help me out, it says "trabajo2.cpp:5:1: error: expected unqualified-id before ‘{’ token"

this is the program:

[PHP]#include <stdio.h>
#include <iostream>
int main( );
{
int num1, num2, res2, res1, res2;
printf("anote el primer numero/n");
scanf("%i",&num1);
printf("Anote el segundo numero/n");
scanf("%i",&num2);
res=num1+num2;
res2=res1*2;
printf("El resultado de la suma es: %i /n y el de la multiplicacion es: %i",res1, res2);
return 0;
}
[/PHP]

I don't get why, it's all in it's place.

---

### Post by Tony Flury on 2012-02-06
Look at your int main() line ... you will find it is not exactly right.

---

### Post by rafaelcbf on 2012-02-06
";" oh, that was a newibie mistake, it had a lot of other problems, but I fixed them, but that first one was kind of dumb on my part, well thats how we learn. Thanks. So, this is solved, how do I make it say that?

---

### Post by MG&amp;TL on 2012-02-06
Under thread tools, as the top. Thanks! ;)

---

