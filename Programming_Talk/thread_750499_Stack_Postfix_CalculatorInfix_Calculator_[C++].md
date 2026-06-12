---
title: "Stack Postfix Calculator/Infix Calculator [C++]"
date: 2008-04-09
forum: Programming Talk
---

### Post by baumgc on 2008-04-09
The title should have been "**Stack Postfix Calculator/Infix _*Converter*_**." Sorry for any confusion this creates.

So I'm making a stack based post fix calculator. It's pretty basic, but I'm having some problems. My stack header is fine..., it's a template that has been proven to work in many other programs I've made, so that isn't the problem.

I am reading the file where lines are something like this:
5 4 +   
11 2 -
3 3 *
18 2 /
etc.

My problem is trying to make it work for numbers that are larger than one digit (thus all the loops). Also, for whatever reason, my program captures spaces, and misc text within the files. I figured that since I used my or's (0 || 1 || 2 || 3 || 4 etc., or * || + || - || / etc.), it would ignore everything else, but it doesn't.

The help I've got elsewhere (from friends, various programming professionals, etc.) says that the logic behind my code makes sense, and that it should work, but they don't know why it doesn't.

Here is my code:
```
#include <cstdlib>
#include <iostream>
#include <fstream>
#include <string>

#include "Stack.h"

using namespace std;

//Global Stuff
ifstream infile;
ofstream outfile;

int main(int argc, char *argv[])
{
	Stack<string> ss;
	char file[45];
	string line;
	string k;
	
		
	cout << "What is the file name, including extension (ex ex1.txt): ";
	cin >> file;
	
	infile.open(file);
	if (!infile)
	{
		cout << "The file does not exist." << endl;
		exit(0);
	}
	
	else
	{
		cout << "Opening file..";
		while(!infile.eof())
		{
			getline(infile,line);
			string hold = "";
			string operators = "";
			
			for(int i = 0; i < line.length(); i++)
			{
				for (;i < line.length(); i++)
					{
						if (line[i] == '0' || '1'|| '2' || '3' || '4' || '5' || '6' || '7' || '8' || '9')
						hold = hold + line[i];
						cout << hold;							
					}
						ss.push(hold);
												
						
						for (; i < line.length(); i++)
						{
							if (line[i] == '+' || '-' || '*' || '/')
							operators = hold + line[i];
							
						}
							ss.push(operators);
			}			
		}
	}
	
	//This is for test purposes to check what's in my stack
	while (!ss.isEmpty())
      {
         if (!ss.pop(k))
            cout << "Failed to pop!!" << endl;
         else
            cout << "Popped: " << k << endl;
		}
}
```

If you -really- want my stack.h, I could include it.  It's an array based stack for ease. I know linked stacks are better, but I've got this one and it works, so I might as well use it. Heck, I can always come back and change it later.
Thanks for your assistance.

PS: Once I get this working, then I'l start popping, re-arranging stuff in infix form, and finally calculation.

---

### Post by WW on 2008-04-09
This
[php]
if (line[i] == '0' || '1'|| '2' || '3' || '4' || '5' || '6' || '7' || '8' || '9')
[/php]
does not do what you want it to do.  I think you mean
[php]
if (line[i] == '0' || line[i] == '1'|| line[i] == '2' || line[i] == '3' || line[i] == '4' || line[i] == '5' || line[i] == '6' || line[i] == '7' || line[i] == '8' || line[i] == '9')
[/php]
Same comment for the other if statement that checks the operator.

---

### Post by baumgc on 2008-04-09
thanks, I'll give this a whirl and see what happens.

---

### Post by baumgc on 2008-04-09
Okay, well. My pop pops =something= this time. Before it was popping nothing.
[IMG]http://gallery.mac.com/clark.baumgartner/100085/Picture-201/web.jpg[/IMG]
This is what I'm getting.

BTW:
How did you get colors in your embedded code?

---

### Post by WW on 2008-04-09
> **baumgc said:**
> 
BTW:
How did you get colors in your embedded code?
Use the **php** tag.  (It's a little annoying that it says "PHP Code" above the code--the first time I saw that, I wondered why someone was submitting php in a thread about C++.)

---

### Post by baumgc on 2008-04-09
Darnit.
I just realized, that I have no way of managing decimal numbers...

That pretty much means I have the throw everything out..., but how do I fix this? grrrrrrrr

---

### Post by dwhitney67 on 2008-04-09
Can you post a worst-case scenario of what your data file could look like?

If the worst you have is what you have posted before (i.e. 2 numbers followed by an operator), then why don't consider using an input string stream to parse the line read from the file?

Here's a simple example:
[PHP]#include <iostream>
#include <sstream>

using namespace std;

int main()
{
  string line( "7 8 *" );
  istringstream istr( line );

  int  val1 = 0;
  int  val2 = 0;
  char op;

  istr >> val1 >> val2 >> op;

  cout << "val1 = " << val1 << ", val2 = " << val2 << ", op = " << op << endl;

  return 0;
}[/PHP]

If you plan to have entries in your file such as "3 4 5 * +", then the code above surely will not work.

---

### Post by baumgc on 2008-04-09
I decided to throw out using getline at all, and switch to using peek instead.

One tiny change and everything works ---perfectly---. Things push without fail and anything else the document may have doesn't get pushed. I'm super excited.
_**Here's what I got:**_
[PHP]#include <cstdlib>
#include <iostream>
#include <fstream>
#include <string>

#include "Stack.h"

using namespace std;

//Global Stuff
ifstream infile;
ofstream outfile;

int main(int argc, char *argv[])
{
	Stack<string> ss;
	char file[45];
	string hold;
	string operators;
	string popme;
	int numnum = 0;
	int opnum = 0;
	char ch;
	
	cout << "What is the file name, including extension (ex ex1.txt): ";
	cin >> file;
	
	infile.open(file);
	if (!infile)
	{
		cout << "The file does not exist." << endl;
		exit(0);
	}
	
	else
	{
		cout << "Opening file.." << endl;
		while(!infile.eof())
		{
			ch = infile.peek();
			if (ch != ' ')
			if ((ch >= '0') && (ch <= '9'))
				{
					infile >> hold;
					ss.push(hold);
					numnum++;
				}
			if (ch == '+' || ch == '-' || ch == '*' || ch == '/')
				{
					infile >> operators;
					ss.push(operators);
					opnum++;
				}
			else
				infile.ignore(1);
				
		}	
	}
	
	//This is for test purposes to check what's in my stack
	while (!ss.isEmpty())
      {
         if (!ss.pop(popme))
            cout << "Failed to pop!!" << endl;
         else
            cout << "Popped: " << popme << endl;
		}
		cout << "Total Operators: " << opnum << endl;
		cout << "Total Numbers: " << numnum << endl;

}
[/PHP]

Here are some examples of the input files:
```
3 4 5 + *           % 27

12 6 / 4 *            % 8

5 4 3 2 1 + / + *     % 25

18 4 3 * 2 / /        % 3

22 7 / 2 *            % ~6.285

2 3.14159 *           % approximate area of a circle of radius 2
```
and
```
 % Some more...

2 3 4 + * 6 1 + 2 4 - 3 3 * + / *

11 1 2 * - 3 * 9 3 / / 1 12 14 -  + 1 + *
```
"%" represent comments in the input files.

---

