---
title: "[C++] getting multiple arguments"
date: 2008-04-13
forum: Programming Talk
---

### Post by yun4 on 2008-04-13
Hi, i'm creating a c++ program that needs to take in multiple arguments. the arguments are 2 doubles and a string (double double string)  but it gets worst, i need to save those arguments for later manipulation but the program needs to take multiple lines of arguments until indicated by an empty line(meaning the end of input).

542.001 54.231 name1
456.23 -32.3221 name2
4545.01 23.02 name3

i'm preparing to save the arguments in lists 

List<double> x, y;
List<String> name;

but i don't know how to extract the arguments. i've look at get() and getline() but not sure how to implement it. 
i understand this is not a place for homeworks but i've got the manipulation part worked out i just don't know how to extract these arguments
Thanks in advance.

---

### Post by SledgeHammer_999 on 2008-04-13
maybe this lesson might help you [link](http://cplusplus.com/doc/tutorial/basic_io.html). If you want more help, just ask.

---

### Post by mike_g on 2008-04-13
Why not pass a list containing structs, or classes in? Your data fields would then be kept together in a container.

---

### Post by yun4 on 2008-04-13
doesn't cin take whatever user input as one whole argument? and getline will take a line as one argument.

the program basically will calculate the distance of a place.

Eg:

when i start my program
./myProg

it will wait for user to input the arguments say:

542.001 54.231 name1
456.23 -32.3221 name2
4545.01 23.02 name3

the two double will be their position where i will calculate their distance
the problem is i don't know how many lines or coordinates they will put in and they can put as much as they like and once they finish they just enter an empty line then the program will do its thing.

my question is how can i take each double and string and save it in a variable or some sort

---

### Post by yun4 on 2008-04-13
@mike_g

the program basically just calculates distances do i really need to use struct?

---

### Post by SledgeHammer_999 on 2008-04-13
If you look at the link I gave earlier, you'll notice that it makes use of getline and cin the form "getline(cin, mystr)".

---

### Post by yun4 on 2008-04-14
i wrote a simple program to see if it works

```

#include <iostream>
#include <string>
#include <list>
using namespace std;

int main() {
	string arguments;
	list<double> x,y;
	list<string> name;
	
	while(getline(cin,arguments)) {
		istringstream iss(arguments);
		while(iss) {
			x.push_back(iss);
			y.push_back(iss);
			name.push_back(iss);
		}
	}
	
	cout << x;
	cout << y;
	cout << name;
}

```

I keep getting long error msg when i compile am i doing it wrong ?

---

### Post by SledgeHammer_999 on 2008-04-14
what kind of error do you get? also I think you don't use the "while" right. It is:

```
while (expressions){
*do something here*}
```

the "expression" needs to be evaluated in "true" or "false". I don't think that you can evaluate "getline(cin,arguments)" to true or false.

---

### Post by pedro_orange on 2008-04-14
> **yun4 said:**
> @mike_g

the program basically just calculates distances do i really need to use struct?

Well if you're planning on sorting any of these lists you're going to have a nightmare trying to keep stuff together.
Since you've got 3 seperate containers for the 3 arguments.
It will only work ok if you do not sort or move any elements in any of the lists, since the only way you can relate to them would be through an indicies.

I would strongly suggest that you use a class or struct. Just something simple like:

```
struct fred{
double x,y;
string name;
};
```

Then at least all your items will be in a single container. 

> I keep getting long error msg when i compile am i doing it wrong ?

Well for a start, you're using istringstream but not including <sstream>

---

### Post by kknd on 2008-04-14
Its better to pass the multiple args as a data structure. But you can also use
varargs (void myfunc(char* first, ...)). Take care, this is evil.

---

### Post by dwhitney67 on 2008-04-14
> **yun4 said:**
> i wrote a simple program to see if it works

```

#include <iostream>
#include <string>
#include <list>
using namespace std;

int main() {
	string arguments;
	list<double> x,y;
	list<string> name;
	
	while(getline(cin,arguments)) {
		istringstream iss(arguments);
		while(iss) {
			x.push_back(iss);
			y.push_back(iss);
			name.push_back(iss);
		}
	}
	
	cout << x;
	cout << y;
	cout << name;
}

```

I keep getting long error msg when i compile am i doing it wrong ?
Yep, your program does generate a lot of compile errors.  Here's a little program I threw together the other day when I first read your post.  I'm sure it could be done better!  Take a look at how I use the istringstream.  That will at least explain why your program is generating compile errors.

[PHP]#include <string>
#include <vector>
#include <sstream>
#include <iostream>

using namespace std;


struct Data
{
  double value1;
  double value2;
  string name;
};


int main()
{
  vector< Data > dataVec;

  cout << "Enter your data, and then a blank line to mark the end..." << endl;

  while ( true )
  {
    string input;
    getline( cin, input );

    if ( input == "" )
    {
      break;
    }
    else
    {
      istringstream istr( input );

      Data d;

      istr >> d.value1 >> d.value2;

      // allow for multiple-word phrases (i.e. strings)
      while ( !istr.eof() )
      {
        string temp;
        istr >> temp;
        d.name += (temp + " ");
      }

      dataVec.push_back( d );
    }
  }

  for ( int i = 0; i < dataVec.size(); ++i )
  {
    const Data &d = dataVec[i];

    cout << "value 1 = " << d.value1 << ", value2 = " << d.value2 << ", name = " << d.name << endl;
  }

  return 0;
}[/PHP]

P.S.  This program will parse inputs such as:
2.2 4.4 string
5.6 7.8 string1 string2

---

