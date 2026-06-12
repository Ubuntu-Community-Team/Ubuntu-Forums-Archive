---
title: "[c++]-Problem with getline and strings"
date: 2010-06-26
forum: Programming Talk
---

### Post by fasoulas on 2010-06-26
i created this function for a program,but i ha a problem

```
void add_entrie(int used_count)
{
	//variables
	string title , name , address ;
	char ans ;
	
	//Title
	cout << "Enter the title of the new entrie : " ;
	getline(cin , title) ;


	//name
	do
	{
		cout << "\nDoes your entrie need a name ?(y or n) : " ;
		cin >> ans ;
		cout << endl ;
		
		
		if(ans != 'y' && ans != 'Y' && ans != 'n' && ans != 'N')
		{
			cout << "\nAnswer only with y or n ,\nanything else is wrong.\n" ;
		}
		
		if(ans == 'y' || ans == 'Y')
		{
			cout << "Enter the name of the new entrie : " ;
			getline(cin , name) ;
			cout << endl ;
		}
		else
		{
			name = "Not Used" ;
		}
			
	}while(ans != 'y' && ans != 'Y' && ans != 'n' && ans != 'N') ;
	
	
	//address
	cout << "Enter the address of the new entrie : " ;
	getline(cin , address) ;
	cout << endl ;
}
```

when i execute it , i see something like this in the terminal

```
user@user-desktop:~/Desktop$ ./untitled
Enter the title of the new entrie : the title

Does your entrie need a name ?(y or n) : y

Enter the name of the new entrie : 
Enter the address of the new entrie : the address

user@user-desktop:~/Desktop$ 

```

why after the 
```
getline(cin , name) ;
```
command it doesn't wait for my feedback ??

---

### Post by trent.josephsen on 2010-06-26
You're mixing line-oriented input with character-oriented input.  Your cin >> ans takes a single character out of the stream, but because input is line-buffered, you have to press Enter to send the "y" to the program.  That puts a newline in the stream, which you don't take out.  When you call getline, it sees a newline character as the first thing in the stream, and immediately returns because it doesn't have to wait for input.  But the first getline clears out the stream, so when you call getline again it finds that it has to wait for you to press Enter again before it can read in another line.

You can turn off line buffering in any of a half dozen different ways (I think -- personally I've never done it), or you can read in the "y" or "n" as a line and parse it to determine whether it's negative or affirmative.

---

### Post by MadCow108 on 2010-06-26
changing the buffering mode will not help, you juts need to discard the newline (and anything before it) from the stream:
cin.ignore(std::numeric_limits<streamsize>::max(), '\n');

---

### Post by fasoulas on 2010-06-26
> **MadCow108 said:**
> changing the buffering mode will not help, you juts need to discard the newline (and anything before it) from the stream:
cin.ignore(std::numeric_limits<streamsize>::max(), '\n');

```
cin.ignore(std::numeric_limits<streamsize>::max(), '\n');
```

where do i have to put this ??

i tried cin.ignore('\n'); before and i did not work

i tried this

```
cin.ignore(std::numeric_limits<streamsize>::max(), '\n');
```


and i got 

g++ -Wall -o "untitled" "untitled.cpp" (in directory: /home/user/Desktop)
untitled.cpp: In function &#8216;void add_entrie(int)&#8217;:
untitled.cpp:29: error: &#8216;numeric_limits&#8217; is not a member of &#8216;std&#8217;
untitled.cpp:29: error: expected primary-expression before &#8216;>&#8217; token
untitled.cpp:29: error: no matching function for call to &#8216;max()&#8217;
Compilation failed.

---

### Post by MadCow108 on 2010-06-26
after the cin >> ans;
which extracts a word until it encounters whitespace but does not extract the last new line.

cin.ignore('\n'); will not work as wanted because it will discard 10 (=the representation of \n) characters from stream or EOF is encountered, and it will block until this happens.
So to get further input 10 characters or press ctrl+D (=EOF)

but you want to discard until a newline is encountered which requires to give 2 arguments to ignore.
That the compiler allows this typo is a drawback of the C++ default function argument system combined with the representation of ascii chars as integers, making ignore('a') a technically valid but logically invalid input

for numeric limits you have to include <limits>
you can also just use any high number, unless you expect your clients to input tons of garbage ;)

---

### Post by fasoulas on 2010-06-26
> **MadCow108 said:**
> after the cin >> ans;
which extracts a word until it encounters whitespace but does not extract the last new line.

cin.ignore('\n'); will not work as wanted because it will discard 10 (=the representation of \n) characters from stream or EOF is encountered, and it will block until this happens.
So to get further input 10 characters or press ctrl+D (=EOF)

but you want to discard until a newline is encountered which requires to give 2 arguments to ignore.
That the compiler allows this typo is a drawback of the C++ default function argument system combined with the representation of ascii chars as integers, making ignore('a') a technically valid but logically invalid input

for numeric limits you have to include <limits>
you can also just use any high number, unless you expect your clients to input tons of garbage ;)

yse but i am still getting errors when i add the 

```
cin.ignore(std::numeric_limits<streamsize>::max(), '\n');
```

in my code.
what should i do??

---

### Post by dwhitney67 on 2010-06-26
Here's some sample code you can play with...

```

#include <string>
#include <iostream>
#include <limits>

template <typename T>
T getInput(const char* prompt)
{
   using namespace std;

   T input;

   while (true) {
      // prompt user and attempt to read input
      cout << prompt;
      cin  >> input;

      // check if valid input given; break from loop if so.
      if (cin.peek() == '\n' && cin.good()) break;

      // user gave bad input; let them know about it.
      cout << "Invalid input!  Try again...\n" << endl;
      cin.clear();
      do { cin.ignore(numeric_limits<streamsize>::max(), '\n'); } while (!cin);
   }

   return input;
}

int main(void)
{
   char        ch  = getInput<char>("Enter a char: ");
   std::string str = getInput<std::string>("Enter a string: ");
   int         num = getInput<int>("Enter a number: ");

   std::cout << "Your char is  : " << ch  << std::endl;
   std::cout << "Your string is: " << str << std::endl;
   std::cout << "Your number is: " << num << std::endl;
}

```

---

### Post by fasoulas on 2010-06-26
My bad didn't read carefully this line written by madcow108

```
for numeric limits you have to include <limits>
```

Also thanks dwhitney67 for making it clear.

I have one last question.

Is my style of programming wrong ?
I shouldn't mix all those thinks with strings and chars ,or it just happens sometimes to have these kinds of problems??

---

### Post by dwhitney67 on 2010-06-26
> **fasoulas said:**
> 
I have one last question.

Is my style of programming wrong ?

Don't worry about your style or approach.  From what I have witnessed, most C++ applications developed at the professional level do not interact with a user sitting at a console.  Input is obtained either from a file, or some other communications channel, such as a socket or signal.

---

