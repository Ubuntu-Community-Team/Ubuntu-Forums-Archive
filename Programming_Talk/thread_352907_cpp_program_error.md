---
title: "cpp program error"
date: 2007-02-03
forum: Programming Talk
---

### Post by sauravbhaumik on 2007-02-03
Dear friends, I've copy-pasted this program from Lippman's book:```
#include <iostream>

    int main()

    {

        int sum = 0, val = 1;

        // keep executing the while until val is greater than 10

        while (val <= 10) {

            sum += val;  // assigns sum + val to sum

            ++val;       // add 1 to val

        }

        std::cout << "Sum of 1 to 10 inclusive is "

                  << sum << std::endl;

        return 0;

    }


```
I saved it with the name 1.cpp and then I go to the terminal, type gcc command, and it gives the error```
gcc: error trying to exec 'cc1plus': execvp: No such file or directory
```
What is the problem?
Standard C programs are running without problems.

---

### Post by Paerez on 2007-02-03
Thats C++ not C. GCC is a C compiler. Use g++.

"g++ 1.cpp"

then run ./a.out to run it.

---

### Post by sauravbhaumik on 2007-02-03
g++ command not found --that's the error now. What to do now?

---

### Post by po0f on 2007-02-03
sauravbhaumik,

```
[FONT="Courier New"]$ sudo aptitude install build-essential[/FONT]
```

---

### Post by g3k0 on 2007-02-03
I think getting it is 
sudo apt-get install build-essential

or something like that search synaptic if thats wrong

haha I lost the reply quickest game

---

### Post by sauravbhaumik on 2007-02-03
Thanks, it ran!
Could you kindly tell me why it makes problem with sin in the following C program:```
#include <stdio.h>
 #include<curses.h>
 #include<math.h>

    double main()

    {double x,y;
    printf("number=");scanf("%lf",&x);getchar();
    y= sin(x) ;
    printf("\nexponent=%lf",y);
    getchar();
    return(0);          

   }
```
It tells me something: ```
/home/saurav/1.c:7: undefined reference to `sin'

```

---

### Post by phossal on 2007-02-04
I compiled this without any errors:

```
#include <stdio.h>
#include <math.h>

**[COLOR="SlateGray"]int[/COLOR]** main() {
	double x,y;
	printf("number=");scanf("%lf",&x);getchar();
	y= sin(x) ;
    	printf("\nexponent=%lf",y);
    	getchar();
    	**[COLOR="SlateGray"]return(0);[/COLOR]**          
};
```
What is this: *#include <curses.h>*?

---

### Post by po0f on 2007-02-04
sauravbhaumik,

When you include headers like that, you need to link your program with the associated libraries.

```
[FONT="Courier New"]$ g++ -Wall -g source.cpp -o my_binary -lcurses -lm[/FONT]
```

**-l** lets g++ know that it should link the following library in.  The library you need to link in was 'm'.  Since you also included curses.h, I added that as well.

---

### Post by sauravbhaumik on 2007-02-04
curses.h is a header file, to which it may require the program to be linked; but I dropped the cursed header file; only with stdio and math is it now.
The same error prevails. The program is now```
#include <stdio.h>
 #include<math.h>

    double main()

    {double x,y;
    printf("number=");scanf("%lf",&x);getchar();
    y= sin(x) ;
    printf("\nexponent=%lf",y);
    getchar();
    return(0);          

   }


```
It is a C program; I save it as 1.c and use the gcc command

---

### Post by g3k0 on 2007-02-04
Read phossals post.  He changed it to **int main** and it worked

---

### Post by sauravbhaumik on 2007-02-04
I also changed it to **int main()** and it doesn't work.
May be some packages are yet to be installed. Kindly tell me which package may be missing.

---

### Post by phossal on 2007-02-04
Wait, my source looks like this:
```
#include <stdio.h>
#include <math.h>

int main() {
	double x,y;
	printf("number=");
	scanf("%lf",&x);
	getchar();
	y= sin(x) ;
    	printf("\nexponent=%lf",y);
    	getchar();
    	return(0);          
};
//File Saved As c.cpp

```
I compile it like this:
```
g++ c.cpp
```

I don't get the sin error unless I'm compiling with gcc.

---

### Post by Wybiral on 2007-02-04
You only need to link the math library with C, not C++

if you are using c, compile with "gcc -lm program.c"
if you are using c++, compile with "g++ program.cpp"

---

### Post by phossal on 2007-02-04
Right, Wyb:

This (c.c):
```
#include <stdio.h>

int main() {
	double x,y;
	printf("number=");
	scanf("%lf",&x);
	getchar();
	y= sin(x) ;
    	printf("\nexponent=%lf",y);
    	getchar();
    	return(0);          
};
```

Compiled like this:
```
bash 3.1:gcc -lm c.c
c.c: In function ‘main’:
c.c:8: warning: incompatible implicit declaration of built-in function ‘sin’
bash 3.1:

```

Or this (c.cpp):
```
#include <stdio.h>
#include <math.h>

int main() {
	double x,y;
	printf("number=");
	scanf("%lf",&x);
	getchar();
	y= sin(x) ;
    	printf("\nexponent=%lf",y);
    	getchar();
    	return(0);          
};
```

Compiled like this:
```
bash 3.1:g++ c.cpp
bash 3.1:

```

---

### Post by phossal on 2007-02-04
If he's going to call it source.c, and he's using gcc and -lm, he *needs* to include the math.h or he'll get the error.

---

### Post by sauravbhaumik on 2007-02-04
Oh right! When I treat it as a cpp program, it doesn't make any wrong; but in gcc command, sin is not welcomed at all! But as is in the above post, I made gcc -lm command and it has run well.
Kindly tell me why the linking is necessary and what it means by the "-lm" part.

---

### Post by po0f on 2007-02-04
blar.c, compile with `gcc blar.c -o cblar -lm`
```
[FONT="Courier New"]#include <stdio.h>
#include <math.h>

int main() {
    double x;
    double y;

    printf("enter number: ");
    scanf("%lf", &x);

    y = sin(x);

    printf("exponent = %lf\n", y);

    return 0;
}
[/FONT]
```


blar.cpp, compile with `g++ blar.cpp -o cxxblar -lm`
```
[FONT="Courier New"]#include <iostream>
#include <cmath>

int main() {
    double x;
    double y;

    std::cout << "enter number: ";
    std::cin >> x;

    y = sin(x);

    std::cout << "exponent = " << y << std::endl;

    return 0;
}
[/FONT]
```


Both work, what's your guys' problems?

---

### Post by phossal on 2007-02-04
I don't have a problem. With both headers, using g++ and source.cpp, you don't need the -lm argument. That's all.

---

### Post by sauravbhaumik on 2007-02-04
But would you kindly explain what the "-lm" part  is about?
Yes, it seems that with math.h or cmath included, the "-lm" (still enigmatic to me) may not do something greater than gcc or g++

---

### Post by Wybiral on 2007-02-04
Linking includes a library when your executable is compiled.

The header only contains the function declarations, not their actual implementation.

So, "math.h" tells C that the functions exist so you can use them in your source, while "-lm" tells it to include the math library which contains the actual functions.

---

### Post by sauravbhaumik on 2007-02-04
So, for other header files, say xxx.h, is "-lx" or sth like needed?

---

### Post by phossal on 2007-02-04
> **po0f said:**
> 
blar.cpp, compile with `g++ blar.cpp -o cxxblar -lm`
```
[FONT="Courier New"]#include <iostream>
#include <cmath>

int main() {
    double x;
    double y;

    std::cout << "enter number: ";
    std::cin >> x;

    y = sin(x);

    std::cout << "exponent = " << y << std::endl;

    return 0;
}
[/FONT]
```
Both work, what's your guys' problems?

lol I do think that's *funny,* poOF. I was just considering the source written in "c" style, as all my examples show. My trick was simply changing the file extension from c to cpp. If you compile it as .cpp with g++, you don't need -lm. Plus, I could reproduce his error directly by compling it as source.c with gcc -lm (leaving out the math header). That's all. I tried a few combinations to see if I could get his *error.* Never, though, did my code *change into* the *c++ style* above. :)

---

### Post by po0f on 2007-02-04
phossal,

Yeah, I didn't know you could omit '-lm' for C++ programs.  And it *was* kinda stupid of me to rewrite the program in C++  :), it's just a habit, I guess.

---

### Post by Wybiral on 2007-02-04
> **sauravbhaumik said:**
> So, for other header files, say xxx.h, is "-lx" or sth like needed?

Actually... No. It depends on the library. You can see all of the libraries in your default library path by going to "/usr/lib"

Any file that starts with a "lib" and ends in a ".a" is a library.

If you look, you will find "libm.a"

Thats your math library.

But not all of them are the first letter (in fact, math.h is the only one I can think of that is)

Its something you usually just have to look up or memorize.

---

### Post by maddog39 on 2007-02-10
Using g++ is probably your best bet and I believe to be the most likely cause of your problem. Just install it from the repositories.

---

### Post by slavik on 2007-02-10
for some weird reason, the math library is separated from the header, hence the -lm ... this is the only standard library that is built like this and is only like this with gcc ... no idea why.

---

### Post by Wybiral on 2007-02-10
> **maddog39 said:**
> Using g++ is probably your best bet and I believe to be the most likely cause of your problem. Just install it from the repositories.

Not if they intend to use C... Sometimes you have to use C (like when you need to generate assembly or use it in a pre-existing C project)

---

### Post by Bobtheknight on 2007-02-13
I remember you may have to do the linking with the socket class as well.  Sockets are used to connect to the internet.  I don't know if that's the same case or not, tho, because I think even with g++ you need the linking.

---

