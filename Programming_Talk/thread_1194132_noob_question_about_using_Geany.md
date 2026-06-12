---
title: "noob question about using Geany"
date: 2009-06-22
forum: Programming Talk
---

### Post by chipppy on 2009-06-22
Good Evening

I am a noob to programming and I am trying to learn C++.  Reading through the book it is all good so far.

i am running Ubuntu 9.04 and Geany 0.17

My problem is with using Geany IDE.
I have tried to run the classic Hello World program, all compiled OK but I have run into a permission problem when I tried to execute it.

```
./geany_run_script.sh: 5 ./learning C++:Permission Denied

___________________________________
(Program exited with code: 126)
Press return to continue
```

This is my code
```
#include <iostream>

using namespace std;

int main()
{
cout << "Hello World!";
cin.get();
return 0;
}
```

I checked the permissions for the file and all looks good, both read and write permission.

Can any please tell me what permission Geany is refering to so that I can fix this up and get my simple project to work.

Any and all assistance is greatly appreciated.

Cheers
chipppy

---

### Post by xtjacob on 2009-06-22
Did you allow it to be executed?

---

### Post by credobyte on 2009-06-22
1) You are running Geany as root ( sudo geany myapp.cpp )
2) You are saving files to root folder and trying to execute it as a user ( not root ).

Anyway, this will fix your problem :
```
sudo chmod +x your_application
```

---

### Post by Zugzwang on 2009-06-22
@OP: Is it possible that you called the executable of your program "learning C++"? If so, please rename it in order not to contain any spaces. This frequently causes troubles with programs and scripts which do not add the proper escaping sequences to such names.

---

### Post by chipppy on 2009-06-22
Good morning

I have some answers and a new question

First I started a new project and this time I used underscores instead of spaces.  The program word perfectly this time.  Thanks heaps for that.
I will have to get used to the coding style of underscores instead of spaces.

When I start Geany I use Applications => Programming => Geany.
Should I change this?
If yes, what would you recommend that I do to allow Geany to start in the proper mode?

I am taking notes so that after a little while I can try to write a little HOW TO: GEANY FOR NOOBS, so that noobs like me can use it to get up and running with the least amount of mistakes.

Again thanks heaps for the assistance

Cheers
chipppy

---

### Post by cmay on 2009-06-22
> **chipppy said:**
> Good morning

I have some answers and a new question

First I started a new project and this time I used underscores instead of spaces.  The program word perfectly this time.  Thanks heaps for that.
I will have to get used to the coding style of underscores instead of spaces.

When I start Geany I use Applications => Programming => Geany.
Should I change this?
If yes, what would you recommend that I do to allow Geany to start in the proper mode?

I am taking notes so that after a little while I can try to write a little HOW TO: GEANY FOR NOOBS, so that noobs like me can use it to get up and running with the least amount of mistakes.

Again thanks heaps for the assistance

Cheers
chipppy
great idea. 

i use geany for everything. i have not experienced any trouble other than using perl it will not execute the perl interpenter in ubuntu but it does in open solaris. 

but  the ting i have been having problems with figuring out and not been solved yet is how to make a template instead if the ones there are .

 it would be nice to have more than one template in the language you use the most. so if you could figure that out fo the little how to i think it would be great.

---

### Post by Shane Little on 2009-07-13
I am having similar issues with compiling in Geany. I I have 'system("pause");, in my code it gives me a syntax error. Once removed it will compile fine, but upon execution I get:
 ./geany_run_script.sh: ./untitled: not found (program executed with code: 127)

Any suggestions on what I may have forgotten?
Thank you for  any help.

Shane Little
[email]shaneplittle74@gmail.com[/email]

---

### Post by credobyte on 2009-07-13
> **Shane Little said:**
> I am having similar issues with compiling in Geany. I I have 'system("pause");, in my code it gives me a syntax error. Once removed it will compile fine, but upon execution I get:
 ./geany_run_script.sh: ./untitled: not found (program executed with code: 127)

Any suggestions on what I may have forgotten?
Thank you for  any help.

Shane Little
[EMAIL="shaneplittle74@gmail.com"]shaneplittle74@gmail.com[/EMAIL]

```
system("PAUSE");
```Requires to include [COLOR=Blue]stdlib.h[/COLOR] ;)

For those who have problems with "Not found" or "Permission denied", open Compiler options and adjust to whatever you need ( default ones will not allow you to execute your app due to [COLOR=Blue]-c[/COLOR] argument ).

---

### Post by Shane Little on 2009-07-13
> **credobyte said:**
> ```
system("PAUSE");
```Requires to include [COLOR=Blue]stdlib.h[/COLOR] ;)

For those who have problems with "Not found" or "Permission denied", open Compiler options and adjust to whatever you need ( default ones will not allow you to execute your app due to [COLOR=Blue]-c[/COLOR] argument ).

OMG... I'm so sorry. I can't believe I forgot that... In any case it obviously cured my syntax issue but I still get the same problem and error at execution.

Shane

---

### Post by Shane Little on 2009-07-13
Found my issue for now. I wasn't 'building' my code before executing it. std::cout << "sigh";.

---

### Post by credobyte on 2009-07-13
> **Shane Little said:**
> Found my issue for now. I wasn't 'building' my code before executing it. std::cout << "sigh";.
```

using namespace std;
cout << "sigh";
```

:p

---

### Post by adamom on 2012-09-30
hello
i got the same errors like OP when i first tried geany. 
but i found a way it worked for me.

0. get the geany packages
    ```
sudo apt-get [install]("http://www.linoob.com/category/install-2/") geany
```1. save your codefile with the right ending! for c++:  example.cpp
    it can be saved where you want, i've got my codefiles in the home directory

2. since geany is only a IDE, you need to get the compiler-packages.
     for c++  ```
sudo apt-get install build-essential
```3. when you have finished coding, compile it with the compile-icon (a brick i think)

4. it should run now! (i hope for you)

i'm not a  linux-crack, i know this are basics. maybe it helps??

---

