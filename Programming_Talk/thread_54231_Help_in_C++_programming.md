---
title: "Help in C++ programming"
date: 2005-08-03
forum: Programming Talk
---

### Post by arcanistherogue on 2005-08-03
[SIZE=2]Well, I started learning C++ after having an average knowledge of python.  My friend offered to help me out.  He said I shouldn't use "cout" and "cin" because I have to include programs with them, which makes the file larger when compiled.  He told me about printf and scanf.  

I have been learning from a "For Dummies" book, and it says to include those programs and to use cout and cin.  I have been working on changing the programs to use the functions my friend told me about, but I am getting some errors.

Here are two versions  of a program in the current chapter I'm on, the first is from windows and the second is my (poorly) translated one.

> [SIZE=1]// WhileDemo - input a loop count. Loop while
//             outputting astring arg number of times.
#include <cstdio>
#include <cstdlib>
#include <iostream>
using namespace std;

int main(int nNumberofArgs, char* pszArgs[])
{
    // input the loop count
    int loopCount;
    cout << "Enter loopCount: ";
    cin  >> loopCount;

    // now loop that many times
    while (loopCount > 0)
    {
        loopCount = loopCount - 1;
        cout << "Only " << loopCount << " loops to go\n";
    }

    // wait until user is ready before terminating program
    // to allow the user to see the program results
    system("PAUSE");
    return 0; 
}[/SIZE]
And here is my version:
> [SIZE=1]#include <stdio.h>

int main()
{
	int stop;
	int loop;
	printf("How many times do you want to loop? ");
	scanf("%d", &loop);

	while (loop > 0)
	{
		loop = loop - 1;
		printf("Only ");
		printf(loop);
		printf(" loops to go!");
	}
        
        printf("Press Enter to Quit");
	scanf("%d", &stop);
}[/SIZE]
Well, when I tried to run the program with g++, I got this error:
> [SIZE=1]
john@ubuntu:~/Desktop/Programs/C++$ g++ whileloop.cpp
whileloop.cpp: In function `int main()':
whileloop.cpp:16: error: invalid conversion from `int' to `const char*'
whileloop.cpp:24:1: warning: no newline at end of file[/SIZE]
I don't know what to do with these errors, I haven't seen them before.  How do I go about fixing these?[/SIZE]

---

### Post by Retrix on 2005-08-03
[QUOTE=arcanistherogue][SIZE=2]Well, I started learning C++ after having an average knowledge of python.  My friend offered to help me out.  He said I shouldn't use "cout" and "cin" because I have to include programs with them, which makes the file larger when compiled.  He told me about printf and scanf.  
[/SIZE][/QUOTE]

Ignore your friend. cout and cin are part of the c++ standard library which will be installed on any Linux system you use. printf/scanf are part of the c standard library, which will also be available on any Linux system.

If you are writing c++, stick with cin/cout.

-Sam

---

### Post by Retrix on 2005-08-03
While I'm here, I may as well help you with your second listing problem.

The problem is with the line:
 printf(loop);

C is a lot less flexible than the equivalent c++ functions. printf needs to take a char* type (a string) first, then any optional parameters.

Therefore, to print out the value of loop using printf, you need:
 printf("%i", loop);

The %i tells to substitute the loop parameter into the string and format it as an integer.

That should get you started. As I stated before though, I strongly suggest you stick with the C++ way of doing things.

-Sam

---

### Post by arcanistherogue on 2005-08-03
Ehhh... A bit more problems... I changed to:
> 
[SIZE=1]#include <stdio.h>

int main()
{
	int stop;
	int loop;
	cout << "How many times do you want to loop? ";
	cin  >> loop;

	while (loop > 0)
	{
		loop = loop - 1;
		cout << "Only " << loop << " loops to go!";
	}

	cout << "Press Enter to Quit";
	cin >> stop;
}[/SIZE]
And I get the following error:
j[SIZE=1]> ohn@ubuntu:~/Desktop/Programs/C++$ g++ whileloop.cpp
whileloop.cpp: In function `int main()':
whileloop.cpp:9: error: `cout' undeclared (first use this function)
whileloop.cpp:9: error: (Each undeclared identifier is reported only once for
   each function it appears in.)
whileloop.cpp:10: error: `cin' undeclared (first use this function)
whileloop.cpp:20:2: warning: no newline at end of file

[/SIZE]

---

### Post by Retrix on 2005-08-03
[QUOTE=arcanistherogue]Ehhh... A bit more problems... I changed to:

And I get the following error:
j[SIZE=1]
[/SIZE][/QUOTE]

Ok, to use cin/cout, you'll need to #include <iostream> rather than <stdio.h>. You'll also need to put the line:
using namespace std;
somewhere before you call cin/cout. (Although some would consider that bad style).

-Sam

---

### Post by arcanistherogue on 2005-08-04
Sweet, that fixed all the errors except for this one real odd one:

no newline at end of file

O_o  I've never gotten this before using Dev-C++ on windows, but I just use Kate and  the gcc for linux... how do I solve this one last error?

Thanks alot for all of your help dude.

---

### Post by Luggy on 2005-08-04
ok to remove errors the code will look like this
```
int main()
{
	int stop;
	int loop;
	cout << "How many times do you want to loop? ";
	cin >> loop;

	while (loop > 0)
	{
		loop = loop - 1;
		cout << "Only " << loop << " loops to go!";
	}

	cout << "Press Enter to Quit";
	cin >> stop;int main()
{
	int stop;
	int loop;
	cout << "How many times do you want to loop? ";
	cin >> loop;

	while (loop > 0)
	{
		loop = loop - 1;
		cout << "Only " << loop << " loops to go!";
	}

	cout << "Press Enter to Quit"; // ENTER wont quit the program
	cin >> stop;                             //entering any character will

	return 0;  //this was forgotten
}

``` 

The problem that remained was that the function main was of type int but didn't return anything. Put in a return 0 (or any integer) and the error will be fixed.

printf and scanf are more powerful but for newbs (or lazy people like me) cout and cin make it much easier.

Another way you could have done this is as follows:
```
#include<iostream>
using namespace std;


int main()
{
	int loop;
	cout << "How many times do you want to loop? ";
	cin >> loop;

	for(loop;loop>0;loop--)
		cout << "Only " << loop << " loops to go!"<<endl;

	return 0;
}
``` 

This is a for loop and I'm sure that if you will read up on it soon enough.
Also due to the nature of the compiler(ish) you don't need to worry about putting in a "press any key to quit" function into your programs because after they have completed the output is displayed in the terminal.

---

### Post by Retrix on 2005-08-04
[QUOTE=arcanistherogue]Sweet, that fixed all the errors except for this one real odd one:

no newline at end of file

O_o  I've never gotten this before using Dev-C++ on windows, but I just use Kate and  the gcc for linux... how do I solve this one last error?

Thanks alot for all of your help dude.[/QUOTE]

Add a new line at the end of your file  :) .
No idea why its required, it just is.

-Sam

---

### Post by cwaldbieser on 2005-08-04
[QUOTE=Luggy]
printf and scanf are more powerful but for newbs (or lazy people like me) cout and cin make it much easier.
[/QUOTE]
How are printf / scanf more powerful?

---

### Post by Luggy on 2005-08-04
Err, me saying it was more powerfull was probably a mistake.
What I ment to imply was that there is a greater amount of control in using printf and scanf then in cin/cout. You need to keep track of what type of data is being put in and the address of the data.

---

### Post by arcanistherogue on 2005-08-04
err... when I tried adding \n a while ago it made an error... 

I'll try again with the return 0 command.  I can't believe I forgot that, I have to get used to the whole program being a function.

lemme try it now...

well, I added a \n before and after the closing bracket thing (I tried multiple times) but both times said I had a stray "\" and a stray "n".  How to I make a new line here?

And I want to have the confirm ending things, because I have friends who use windows and whatnot, where the crappy command line closes after the program is executed.

---

### Post by Retrix on 2005-08-04
Sorry, what I meant was add a new blank line at the end of your source file (After the closing } ). Not try to print one. Having return 0; is advisable but not strictly necessary.

-Sam

---

### Post by arcanistherogue on 2005-08-04
Oh, ok.  Thanks alot!

errr.... how do i run the compiled program >_<

---

### Post by Retrix on 2005-08-04
[QUOTE=arcanistherogue]Oh, ok.  Thanks alot!

errr.... how do i run the compiled program >_<[/QUOTE]

# g++ first.c -o first
# ./first

-o specifies the output file.

-Sam

---

### Post by Stuka on 2005-08-04
A couple of minor rants: 
1) In non-trivial programs, you should NOT have a "using namespace std;" statement in many (if any) files. If you're using cin/cout a lot, then "using std::cin;" and "using std::cout;" might be advisable.

2) Having main() return an int is a good idea, and is the recommended (but not enforced) way of doing things. In particular it's super-handy for command line tools that might be scripted, as a 0 is presumed to mean successful completion, while other numbers indicate errors.

---

### Post by LordHunter317 on 2005-08-04
[QUOTE=Luggy]
What I ment to imply was that there is a greater amount of control in using printf and scanf then in cin/cout.[/quote]Nope, there's actually quite less.

>  You need to keep track of what type of data is being put in and the address of the data.Which is dumb.  This kind of thing is what the compiler is meant for.

---

### Post by arcanistherogue on 2005-08-04
[QUOTE=Stuka]A couple of minor rants: 
1) In non-trivial programs, you should NOT have a "using namespace std;" statement in many (if any) files. If you're using cin/cout a lot, then "using std::cin;" and "using std::cout;" might be advisable.

2) Having main() return an int is a good idea, and is the recommended (but not enforced) way of doing things. In particular it's super-handy for command line tools that might be scripted, as a 0 is presumed to mean successful completion, while other numbers indicate errors.[/QUOTE]

Could you explain to me the differences?  I want to know both how and why these things work.

---

### Post by LordHunter317 on 2005-08-04
The issue with using 'using namespace std' at some global scope (e.g., in an include-file, at file-scope) is that now all functions within that scope now see all the functions in the standard namespace.

Consider if I wanted to create a function named 'sort' in my C++ file.  If the file starts with 'using namespace std;', doing this will create a conflict when I go to use my sort function, as the compiler won't necessarily know which sort function I meant. 

As for the second.  main() is always supposed to return an int.  It's non-standard to have it not return an int.  Moreover, the value returned from main is passed back to whatever program called yours.  '0' means success, anything else means error.

---

