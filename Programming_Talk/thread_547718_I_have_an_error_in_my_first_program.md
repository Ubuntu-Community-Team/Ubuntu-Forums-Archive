---
title: "I have an error in my first program"
date: 2007-09-10
forum: Programming Talk
---

### Post by fourthdimension on 2007-09-10
Hey All

I just wrote my first, very simple program, and I get an error when compiling it.

Here's the source:

```
//This is an original test program made to add any given number to 10
#include <cstdio>
#include <cstdlib>
#include <iostream>
using namespace std;
int main(int nNumberofArgs, char* pszArgs[])

{


	cout<< "this program adds ten to any value you enter.  please enter a number";


	//define the input variable
	int inputNumber;

	cin>> inputNumber;
	

	//define the output
	int outputNumber

	//now add ten to the value
	outputNumber = inputNumber + 10

	//now give the output...

	cout<< "the new value is"
	cout<< outputNumber
}	
```

...and here's the error:

```
mymachine:~$ g++ -o TestAddingProgram '/home/secondgenesis/Desktop/Programming/Test Programs and source/Original test adding program.cpp' /home/secondgenesis/Desktop/Programming/Test Programs and source/Original test adding program.cpp: In function ‘int main(int, char**)’:
/home/secondgenesis/Desktop/Programming/Test Programs and source/Original test adding program.cpp:24: error: expected initializer before ‘outputNumber’

```

Also, I've seen this line in nearly every C++ source I've looked at so far; can anyone tell me what it does?  It looks like it initializes the variable "main" and includes certain libraries, but I don't entirely understand what all of it means.

```
 #include <cstdio>
#include <cstdlib>
#include <iostream>
using namespace std;
int main(int nNumberofArgs, char* pszArgs[])
```

Thanks a lot!  I probably wouldn't even have gotten this far on my journey into coding if it weren't for the Ubuntu community.:)

---

### Post by LaRoza on 2007-09-10
You are missing a lot of semi colons.

[php]

#include <iostream>
using namespace std;
int main(int argc, char ** argv)
{
	int inputNumber;
	int outputNumber;

	cout<< "this program adds ten to any value you enter.  please enter a number";


	cin>> inputNumber;
	
	outputNumber = inputNumber + 10;

	cout<< "the new value is ";
	cout<< outputNumber << endl;
             return 0;
}
[/php]

---

### Post by fourthdimension on 2007-09-10
Ah!  Thanks! :-)

---

### Post by gnusci on 2007-09-10
Here your program with some corrections:

[PHP]
//This is an original test program made to add any given number to 10
#include <cstdio>
#include <cstdlib>
#include <iostream>
using namespace std;

int main(int nNumberofArgs, char* pszArgs[])
{
        cout<<endl<<"this program adds ten to any value you enter.  please enter a number? ";

        //define the input variable
        int inputNumber;

        cin>> inputNumber;

        //define the output
        int outputNumber;

        //now add ten to the value
        outputNumber = inputNumber + 10;

        //now give the output...

        cout<< "the new value is ";
        cout<< outputNumber<< endl; // don't forget ";" at the end of a line

        return 0;
}

[/PHP]

---

### Post by fourthdimension on 2007-09-10
Thanks a lot.  Can you tell me what ```
return 0
``` and ```
#include <cstdio>
#include <cstdlib>
#include <iostream>
using namespace std;

int main(int nNumberofArgs, char* pszArgs[])
``` mean?
I appreciate all your help!

---

### Post by gnusci on 2007-09-10
Linux can receive a output form the program is a function "main", normaly the program can say to the shell whether the finish properly "0" or there was a problem. You can see this with one example type:

**> cat hello**

and then:

**> echo $?**

**$?** give the output of the last command executed. If you see a "1" it is mean somethig was wrong. Now type:

**> echo hello**

and then once again:

**> echo $?**

Now you will see "0", it is mean the last command finished successfully.

Ok now lets see the second question, I will explain by parts:

1) included libraries that allow you to use the functions declared inside them:

[PHP]#include <cstdio>
#include <cstdlib>
#include <iostream>
[/PHP]

This tell to the compiler that you will use function defined under the standard namespace:

[PHP]using namespace std;[/PHP]

and this one is the main function:

[PHP]int main(int nNumberofArgs, char* pszArgs[])[/PHP]

[COLOR="Red"]int[/COLOR]: the funtion return an integer number "e.g. return 0;".
[COLOR="Red"]nNumberofArgs[/COLOR]: number or arguments. 
[COLOR="Red"]pszArgs[][/COLOR]: this is an string with the input given to the program.

In your program you are not using the last two parameters so you can also use:

[PHP]int main(void)[/PHP]

which mean that you won't use the input parameters.

Here there is a nice introduction:

[http://www.cplusplus.com/doc/tutorial/program_structure.html](http://www.cplusplus.com/doc/tutorial/program_structure.html)

---

### Post by rplantz on 2007-09-10
> **gnusci said:**
> 
1) included libraries that allow you to use the functions declared inside them:

[PHP]#include <cstdio>
#include <cstdlib>
#include <iostream>
[/PHP]


This is not completely correct. From the tutorial cited by gnusci
> 
Lines beginning with a pound sign (#) are directives for the preprocessor. They are not regular code lines with expressions but indications for the compiler's preprocessor. In this case the directive #include <iostream> tells the preprocessor to include the iostream standard file. This specific file (iostream) includes the declarations of the basic standard input-output library in C++, and it is included because its functionality is going to be used later in the program.

After your source code file is preprocessed, it is then compiled to produce machine code. The iostream file tells the compiler how to compile any statments in your program that call functions in the iostream library. For example, your program has the statement:
```

cout<<endl<<"this program adds ten to any value you enter.  please enter a number? ";

```
which calls a function in the iostream library.

After compiling, the machine code of your program is linked with the functions that were called in the various libraries.

My point may seem like a minor distinction. I was a computer science professor for over 20 years, and I've seen this slightly mistaken explanation given many times, even in textbooks. Unfortunately, I think it leads to misunderstandings when you get into more advanced programming later.

---

