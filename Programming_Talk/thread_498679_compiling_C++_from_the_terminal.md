---
title: "compiling C++ from the terminal"
date: 2007-07-11
forum: Programming Talk
---

### Post by S15_88 on 2007-07-11
Now that i have ubuntu set up nicely and feel fairly comfortable i would like to start doing some programming. I did a year of C++ and 2 years of Java at school and i'm taking computer science at university so i'd like to go into next year feeling confident with my programming skills.

I have a very simple program i wrote several years ago in microsoft visual using C++ that calculates the area or perimeter of a given object chosen by the user. I read a little how to that says all you need to do is g++ filename.cpp and it'll compile. When i do this i get several errors!

Most are with regard to the header files, i know when programming with an IDE for java you need JDK profiles and then there's libraries and stuff, do i need to load these somewhere when compiling from the terminal? again with the header files there's one: windows.h is that necessary since i am using ubuntu?

and silly question about my code, it says main() must return int, but i know this program runs fine when compiled in visual studio, and i remember in both C++ and Java out teacher told us to delete the contents within main(), i believe it's string args[], that might be Java i'm getting mixed up now haha

if anyone could answer these questions i would greatly appreciate aswell if anyone knows of any good tutorials send them this way! I've attached my program if you need to reference it.

Thanks in advance, Alain

ps. sorry about the length!

---

### Post by kknd on 2007-07-11
To compile a C++ source:

g++ source.cpp -o executableName

Other flags.: 

-O[1..n] : Set the optimization level (for relesases, not for debug)
-g : Extra debugging information

---

### Post by WebDrake on 2007-07-11
> **S15_88 said:**
> Now that i have ubuntu set up nicely and feel fairly comfortable i would like to start doing some programming. I did a year of C++ and 2 years of Java at school and i'm taking computer science at university so i'd like to go into next year feeling confident with my programming skills.

I have a very simple program i wrote several years ago in microsoft visual using C++ that calculates the area or perimeter of a given object chosen by the user. I read a little how to that says all you need to do is g++ filename.cpp and it'll compile. When i do this i get several errors!

Most are with regard to the header files, i know when programming with an IDE for java you need JDK profiles and then there's libraries and stuff, do i need to load these somewhere when compiling from the terminal? again with the header files there's one: windows.h is that necessary since i am using ubuntu?

and silly question about my code, it says main() must return int, but i know this program runs fine when compiled in visual studio, and i remember in both C++ and Java out teacher told us to delete the contents within main(), i believe it's string args[], that might be Java i'm getting mixed up now haha

if anyone could answer these questions i would greatly appreciate aswell if anyone knows of any good tutorials send them this way! I've attached my program if you need to reference it.

Thanks in advance, Alain

ps. sorry about the length!

Have you installed the basic tools required for building code?

```
sudo apt-get install build-essential
```

windows.h is certainly not necessary on Linux. ;-)  In fact looking at your program I don't think it needs anything other than iostream.  Incidentally with C++ I don't believe you need the .h.  Just #include <iostream> should do it.

You *will* run into trouble because of namespaces, you assume the standard namespace is being used but don't declare it.  Place the line,

```

using namespace std;

```

after the header include requests.

The convention with the main() function is that it returns an int and takes no input.  i.e.,

```

int main()
{
    // Your program
}

```

although it *can* take input, reading the extra details of what is typed on the command line.

I hope that will solve your problems but can't be sure because right now I'm on Windows (shock horror) and don't have my lovely Ubuntu development tools handy. ;-)

---

### Post by S15_88 on 2007-07-11
I installed the build-essential and removed the files that were'nt needed anymore, fixed up my header files and added: using namespace std;  got rid of all the errors but it still wants main() to return an int, i thought if nothin was in the brackets it defaults to return 0, but since it's empty and i'm getting an error what should i put in,  void main(int, return 0)??  and that leads to my next question what are the benefits/detriments of using void main() as oppose to int main()??

Thanks, Alain

---

### Post by Wybiral on 2007-07-11
> **S15_88 said:**
> I installed the build-essential and removed the files that were'nt needed anymore, fixed up my header files and added: using namespace std;  got rid of all the errors but it still wants main() to return an int, i thought if nothin was in the brackets it defaults to return 0, but since it's empty and i'm getting an error what should i put in,  void main(int, return 0)??  and that leads to my next question what are the benefits/detriments of using void main() as oppose to int main()??

Thanks, Alain

Don't use "void main()" it's not proper.

It should be...

```

int main()
{
    // Some code
    return 0;
}

```

---

### Post by S15_88 on 2007-07-11
sweet deal no more errors but jus a total newb question remaining, where's my program hahaha should it pop up in a console window or will it run right in the terminal as it's text based no frames or nuthin.

Thanks, Alain

---

### Post by Wybiral on 2007-07-11
It should generate a file "a.out"

(unless you specify a different output file)

Execute it from the command line with "./a.out"

---

### Post by WebDrake on 2007-07-11
> **S15_88 said:**
> it still wants main() to return an int, i thought if nothin was in the brackets it defaults to return 0, but since it's empty and i'm getting an error what should i put in,  void main(int, return 0)??  and that leads to my next question what are the benefits/detriments of using void main() as oppose to int main()??

I think you misunderstand how functions are declared.

The variable type *before* the function name tells you what the function returns.  The list in the regular brackets () tells you what *input* the function takes (in this case, none).

So, main returns an integer variable and in this case takes no input:

```

int main()
{
}

```

Now, if you declare,

```

void main()
{
}

```

... you're trying to make it so that main() will not return a value and the compiler won't like this because the main function is supposed to return a number indicating the program's exit status.

---

### Post by S15_88 on 2007-07-11
ok i'm pretty sure i'm doing this wrong, i'm typing into the terminal: g++ Functions.cpp -o Functions   and i'm getting a bunch of hababaloooo!
> 
Functions.cpp:62: error: stray &#8216;@&#8217; in program
Functions.cpp:62: error: stray &#8216;@&#8217; in program
Functions.cpp:62:1157: warning: null character(s) ignored
Functions.cpp:62:1176: warning: null character(s) ignored
Functions.cpp:62:1199: warning: null character(s) ignored
Functions.cpp:62:1204: warning: null character(s) ignored
Functions.cpp:62:1210: warning: null character(s) ignored
Functions.cpp:62:1211: warning: no newline at end of file
Functions.cpp:1: error: expected constructor, destructor, or type conversion before numeric constant
Functions.cpp:8: error: expected declaration before &#8216;}&#8217; token


i get all those errors from Functions.cpp:62 down to Functions.cpp:48 which is visible but i'm guessing it goes down till 1.  

does this executeable filename need an extension on it?
it was so nice using an IDE jus click compile then execute haha but i feel like i'm going to learn alot this way! which was my intent when i installed ubuntu was to broaden my horizons!

Thanks, Alain

---

### Post by WebDrake on 2007-07-11
> **S15_88 said:**
> ok i'm pretty sure i'm doing this wrong, i'm typing into the terminal: g++ Functions.cpp -o Functions   and i'm getting a bunch of hababaloooo!


Post the code you have now?

---

### Post by S15_88 on 2007-07-11
i've attached it for you,

Thanks, Alain

---

### Post by WebDrake on 2007-07-11
> **S15_88 said:**
> i've attached it for you,

Thanks, Alain

It compiles fine for me.

```
g++ Functions.cpp -o Func
```

I took the opportunity of indenting the code for you so you can see its structure better (see also attachment):

```

// Functions.cpp : Defines the entry point for the console application. 
// 

#include <iostream>  

using namespace std;

const double PI=3.14159; 

double rectangleArea(){ 
	double length,width; 
	
	cout<<"Please enter the length and width of the rectangle.\n"; 
	cin>>length; 
	cin>>width; 
	
	return length*width; 
	
} 
double rectanglePerimeter(){ 
	double length,width; 
	
	cout<<"Please enter the length and width of a rectangle.\n"; 
	cin>>length; 
	cin>>width; 
	
	return (2*length)+(2*width); 
	
} 

double triangleArea(){ 
	double base,height; 
	
	cout<<"Please enter the base and the height of a triangle.\n"; 
	cin>>base; 
	cin>>height; 
	
	return base*height/2; 
	
} 
double trianglePerimeter(){ 
	double side1,side2,side3; 
	
	cout<<"Please enter the measurments of three sides of a triangle.\n"; 
	cin>>side1; 
	cin>>side2; 
	cin>>side3; 
	
	return side1+side2+side3; 
	
} 
double circleArea(){ 
	double radius; 
	
	cout<<"Please enter the radius of a circle.\n"; 
	cin>>radius; 
	
	return PI*(radius*radius); 
	
} 

int main(){ 
	
	int selection; 
	double output; 
	
	cout<<"Welcome to the Geomatry Program!\n\n"; 
	cout<<"What would you like to calculate?\n"; 
	cout<<"(1)Area of a rectangle\n"; 
	cout<<"(2)Perimeter of a rectangle\n"; 
	cout<<"(3)Area of a triangle\n"; 
	cout<<"(4)Perimeter of a triangle\n"; 
	cout<<"(5)Area of a circle\n"; 
	
	cin>>selection; 
	
	if (selection==1){ 
		output=rectangleArea(); 
		cout<<"The rectangles area is "<<output<<" square units.\n"; 
	}else if(selection==2){ 
		output=rectanglePerimeter(); 
		cout<<"The rectangles perimeter is "<<output<<" square units\n"; 
	}else if(selection==3){ 
		output=triangleArea(); 
		cout<<"The triangles area is "<<output<<" square units.\n"; 
	}else if(selection==4){ 
		output=trianglePerimeter(); 
		cout<<"The triangles perimeter is "<<output<<" square units.\n"; 
	}else if(selection==5){ 
		output=circleArea(); 
		cout<<"The circles area is "<<output<<" square units.\n"; 
	}else{ 
		cout<<"Invalid Input\n"; 
	} 
	
	cout<<"\n\n Thank you for using my program.\n\n"; 
	
	return 0;
} 

```

I wonder if it's simply the encoding on the file?  Did you write it in Windows, for example?

---

### Post by S15_88 on 2007-07-11
yes you are correct it was the encoding, but just another quick question i have the executable in a folder now i double click on it and get nothing, right click open nothing?  is there a way to launch from the terminal and any ideas why i can't open it??

Thanks, Alain

---

### Post by Wybiral on 2007-07-11
> **S15_88 said:**
> yes you are correct it was the encoding, but just another quick question i have the executable in a folder now i double click on it and get nothing, right click open nothing?  is there a way to launch from the terminal and any ideas why i can't open it??

Thanks, Alain

Yes, assuming it's a terminal-based program you will have to use the terminal. Navigate to the folder it's in and use "./some_program" (where "some_program" is the actual file name).

---

