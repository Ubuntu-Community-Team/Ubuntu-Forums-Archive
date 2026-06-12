---
title: "C question(noobish c question)"
date: 2007-11-30
forum: Programming Talk
---

### Post by fedex1993 on 2007-11-30
okay i just started learning the programming langauge and i am having problems compiling hello world ```
#include <stdio.h>
main(){
printf("Hello World\n");
}

```
and when try to compile it using GCR -o hello ./hello.c it comes up with ```
./hello.c:1:19: error: stdio.h: No such file or directory
./hello.c: In function ‘main’:
./hello.c:3: warning: incompatible implicit declaration of built-in function ‘printf’

```
do i need to to download some repos or something or is there just something wrong with my script

---

### Post by Wybiral on 2007-11-30
Install build essential:
```

sudo apt-get install build-essential

```

And main() should be "int main()" or better yet, "int main(int argc, char *argv[]"

---

### Post by fedex1993 on 2007-11-30
sorry i had build-essentials installed i guess since reformatted i forgot to install it >_> thanks wybiral

---

### Post by Majorix on 2007-12-01
> **Wybiral said:**
> Install build essential:
And main() should be "int main()" or better yet, "int main(int argc, char *argv[]"

You forgot the ending parenthesis. It should read
[PHP]int main(int argc, char *argv[])[/PHP]

Even though including those parameters (or is it called arguments in this case? I always mix up the two :p) is only necessary if you plan on getting command line arguments (which the OP doesn't intend to); it is a good practice to make a habit of including them for more complex programs in the future.

---

### Post by Kadrus on 2007-12-01
Ok..so I am going to try to help you..like you want to compile something for the first time...
First off type this in Terminal(I am assuming that you haven't done this)
```
sudo apt-get install build-essential
```
Then type 
```
sudo apt-get install g++

```
Then type Hello World in C programming language in Gedit:
```
#include<stdio.h>
main()
{
printf("Hello World!\n");
}

```
Save the file ex.c
Then Open terminal and type:
```
g++ ex.c
```
It should compile bug free...and when type:
./a.out...

You should see "Hello World!";

Hope it helped :)

---

### Post by Compyx on 2007-12-01
> **Kadrus said:**
> Ok..so I am going to try to help you..like you want to compile something for the first time...
First off type this in Terminal(I am assuming that you haven't done this)
```
sudo apt-get install build-essential
```
Then type 
```
sudo apt-get install g++

```
Then type Hello World in C programming language in Gedit:
```
#include<stdio.h>
main()
{
printf("Hello World!\n");
}

```
Save the file ex.c
Then Open terminal and type:
```
g++ ex.c
```
It should compile bug free...and when type:
./a.out...

You should see "Hello World!";

Hope it helped :)

Bad advice, don't compile C programs with a C++ compiler.
And the code you posted is horrible.

---

### Post by geirha on 2007-12-01
> **fedex1993 said:**
> okay i just started learning the programming language and i am having problems compiling hello world ```
#include <stdio.h>
main(){
printf("Hello World\n");
}

```
Your main method should return an int (though it is optional, it's good practice)```
#include <stdio.h>
int main(){
  printf("Hello, World!\n");
  return 0; // success
}
```
> **fedex1993 said:**
> 
and when try to compile it using GCR -o hello ./hello.c it comes up with ```
./hello.c:1:19: error: stdio.h: No such file or directory
./hello.c: In function &#8216;main&#8217;:
./hello.c:3: warning: incompatible implicit declaration of built-in function &#8216;printf&#8217;

```
GCR? the compile-line should be something like ```
gcc -Wall -o hello hello.c
``` (-Wall just shows some extra warnings)
> **fedex1993 said:**
> 
do i need to to download some repos or something or is there just something wrong with my script

the build-essential package should be enough. It should've installed libc6-dev which contain stdio.h. Does the following command give any output? ```
dpkg -S stdio.h
```

EDIT: ok, I have to read closer before I post, your problem was fixed by installing the build-essential package apparently. Could you add the [SOLVED] tag?

---

### Post by Kadrus on 2007-12-01
> **Compyx said:**
> Bad advice, don't compile C programs with a C++ compiler.
And the code you posted is horrible.

So since you want a good code...here you go
```
  #include<stdio.h>

int main()
{
  printf( "Hello World!\n" );
  getchar();
  return 0;
}
```
Happy?

---

### Post by fedex1993 on 2007-12-01
wow i am new at this also i am not doing C++ i just started learning so dont please say my code is horible

---

### Post by smartbei on 2007-12-01
@fedex: He was referring to Kadrus' code, not yours.

---

### Post by Kadrus on 2007-12-01
> **smartbei said:**
> @fedex: He was referring to Kadrus' code, not yours.
I rewrote it in a good way by the way...check the reply above...

---

### Post by Vadi on 2007-12-01
Hehe why the getchar()? :D

And everyone learns, have fun with C.

---

### Post by Kadrus on 2007-12-01
> **Vadi said:**
> Hehe why the getchar()? :D

And everyone learns, have fun with C.

Don't know..just want it to write :p

---

### Post by fedex1993 on 2007-12-01
> **smartbei said:**
> @fedex: He was referring to Kadrus' code, not yours.

woops sorry thanks for telling my mistake

---

### Post by LaRoza on 2007-12-01
> **Vadi said:**
> Hehe why the getchar()? :D

And everyone learns, have fun with C.

If you double click the program and it runs, it will close upon completion. The getchar() lets you see the results.

If you are running the program through the terminal, this is not needed.

---

### Post by Vadi on 2007-12-01
Ah yes, true. I remember the terminal in windows doing that (quitting asap) - ugh how I hated that.

---

### Post by j_g on 2007-12-01
> **Vadi said:**
> I remember the terminal in windows doing that (quitting asap)

There is a property that can be set to modify that behavior.

---

### Post by LaRoza on 2007-12-01
> **j_g said:**
> There is a property that can be set to modify that behavior.

What property?

Programs usually close when they are finished.

---

