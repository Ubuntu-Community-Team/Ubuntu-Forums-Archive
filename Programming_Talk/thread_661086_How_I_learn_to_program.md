---
title: "How I learn to program"
date: 2008-01-07
forum: Programming Talk
---

### Post by snickers295 on 2008-01-07
I found the best way to program; Start a useless app.
```
#include <iostream>
#include <cstdlib>
using namespace std;
int start()
{
cout <<"Code And Number Program" << endl;
cout <<"Enter 6 then press enter and it will count up to 10." << endl;
}
int main()
{
int answer;
int code;
int flag=1;
int start0=1;
while (flag == 1)
{
if (start0 == 1)
{
start();
start0=0;
}
cout <<"Start? (1 yes, 2 no):";
cin>>answer;
if (answer == 1)
{
cout <<"Enter The Secret Code:";
cin>>code;
if (code == 6)
{
for (int x=1;x < 11; x++)
{
cin.get();
cout << x << endl;
flag=0;
}
}
else {
cout <<"Sorry, Thats Not The Code" << endl;
flag=1;
}
} else if (answer == 2)
{
flag=0;
return 0;
}
else {
cout <<"Sorry Thats Not A Option." << endl;
flag=1;
}
}
return 0;
}


``` 
this is a program that asks you if you want to use it, asks for a code (6 is the code) and then you press enter several times and it counts up to 10.
this has got me to remember the commands and to learn more commands, i add another useless part to it and just keep debugging and organizing  the code and then just doing that can teach you how to use c++.

---

### Post by ThinkBuntu on 2008-01-07
Usually I program with a goal in mind, so I'm not sure how writing a "useless app" would help me learn practical programming. But everyone has their own approach, I suppose.

---

### Post by Wybiral on 2008-01-07
Looks good, but another aspect of programming is writing readable/manageable code. I _highly_ advise indenting your code so that it's easier for other developers to read.

---

### Post by snickers295 on 2008-01-07
> Usually I program with a goal in mind, so I'm not sure how writing a "useless app" would help me learn practical programming. But everyone has their own approach, I suppose.
thats what i mean, make a  little app that does nothing, its like those "Hello, World!" Programs accept  you can app whatever you want in it to make it more complex.
> **Wybiral said:**
> Looks good, but another aspect of programming is writing readable/manageable code. I _highly_ advise indenting your code so that it's easier for other developers to read.
```
#include <iostream>
#include <cstdlib>

using namespace std;

int start() {

cout <<"Code And Number Program" << endl;
cout <<"Enter 6 then press enter and it will count up to 10." << endl;

}


int main() {

int answer;
int code;
int flag=1;
int start0=1;

while (flag == 1) {

if (start0 == 1) {

start();
start0=0;

}
cout <<"Start? (1 yes, 2 no):";
cin>>answer;

if (answer == 1) {

cout <<"Enter The Secret Code:";
cin>>code;
if (code == 6) {

for (int x=1;x < 11; x++) {

cin.get();
cout << x << endl;
flag=0;

}

}
else {

cout <<"Sorry, Thats Not The Code" << endl;
flag=1;

}

} 

else if (answer == 2) {

flag=0;
return 0;

}

else {

cout <<"Sorry Thats Not A Option." << endl;
flag=1;
}

}

return 0;

}

```
any better?

---

### Post by dwhitney67 on 2008-01-07
I'll bite... the answer is no.

---

### Post by LaRoza on 2008-01-07
[php]
#include <iostream>
#include <cstdlib>

int start() 
{
    std::cout << "Code And Number Program" << std::endl;
    std::cout << "Enter 6 then press enter and it will count up to 10." << std::endl;
}


int main(int args,char ** argv) 
{

    int answer;
    int code;
    int flag=1;
    int start0=1;

    while (flag == 1) 
    {

        if (start0 == 1) 
        {

            start();
            start0=0;

        }
        std::cout << "Start? (1 yes, 2 no):";
        std::cin>>answer;

        if (answer == 1)
        {
            std::cout << "Enter The Secret Code:";
            std::cin >> code;
            if (code == 6) 
            {
                for (int x=1;x < 11; x++) 
                {
                    std::cin.get();
                    std::cout << x << endl;
                    flag=0;
                }

            }
            else 
            {
                std::cout << "Sorry, Thats Not The Code" << std::endl;
                flag=1;

            }

        } 

        else if (answer == 2) 
        {
            flag=0;
            return 0;
        }

        else 
        {
            std::cout << "Sorry Thats Not A Option." << std::endl;
            flag=1;
        }

    }
    return 0;
}
[/php]

---

### Post by pmasiar on 2008-01-07
> **dwhitney67 said:**
> I'll bite... the answer is no.

... because it **still** shows  no proper code structure. Any free editor above notepad will do proper indent, just use it.

---

### Post by Sam on 2008-01-07
Just a quick note, use the switch statement instead of multiple if-else-if chain.
```
switch (answer) {
	case 1:
		<snip>
		break;
	case 2:
		<snip>
		break;
	default:
		<snip>
		break;
}

```is better than
```
if (answer == 1) {
	<snip>
} else if (answer == 2) 
	<snip>
} else {
	<snip>
}
```

---

### Post by LaRoza on 2008-01-07
> **Sam said:**
> Just a quick note, use the switch statement instead of multiple if-else-if chain.


It is not better, and is less flexible. I prefer if-else decisions in many cases, because it is cleaner and allows for more decision making.

---

### Post by Sam on 2008-01-07
> **LaRoza said:**
> It is not better, and is less flexible. I prefer if-else decisions in many cases, because it is cleaner and allows for more decision making.

Yes but if you're checking the value of the same var, the switch is better (and quickier, but it's not significant). Each situation has its advantages, as well as the programmer's habits.

---

### Post by LaRoza on 2008-01-07
> **Sam said:**
> Yes but if you're checking the value of the same var, the switch is better (and quickier, but it's not significant). Each situation has its advantages, as well as the programmer's habits.

How is that better?

I think the OP needs to learn how to indent and use consistant style, rather than forming a preference on switch statements.

---

### Post by essexboyracer on 2008-01-08
Whilst were on the subject of programming, is there a definitive resource for learning C++? I come from php background and that had its manual @ [www.php.net](www.php.net). 

How did I learn to program/script? Getting thrown in at the deep end i think

---

### Post by dwhitney67 on 2008-01-08
I normally use a switch() when I am comparing against enumerated constants.  I rely on if-else constructs when comparing against variable data or in cases where more than one comparison is required to yield a conditional result.

Proper indentation is important to most, if not all, programming languages.  The OP seems to know the keywords and constructs of C++, however the code presented was very "amateurish", but nevertheless a "stepping stone" into the C++ programming world.

The code, as presented by LaRoza, is much easier to read, regardless of the fact that it is enclosed in the PHP format.

I recommend that the OP spend a little more time studying code examples, paying particular attention to indentation practices, and also variable declarations.  Variables ought to be declared closest to where they are first used and defined only within the scope in which they are required.

---

### Post by dwhitney67 on 2008-01-08
> **essexboyracer said:**
> Whilst were on the subject of programming, is there a definitive resource for learning C++? I come from php background and that had its manual @ [www.php.net](www.php.net). 

How did I learn to program/script? Getting thrown in at the deep end i think

Hilarious!  I'm the opposite.  I been programming in C++ for over 10 years, but just recently I started studying PHP programming.

From what I have witnessed so far, the key constructs and the coding styles are very similar.  C++ is easy to learn.  What is difficult is OOD (object oriented design).  The implementation of a good OOD can be implemented in C++, Java, or any of the other object-oriented languages.

Here's a good resource for referencing the C++ Standard Template Library (STL) containers:  [http://www.cplusplus.com/reference/stl/](http://www.cplusplus.com/reference/stl/)

---

### Post by LaRoza on 2008-01-08
> **essexboyracer said:**
> Whilst were on the subject of programming, is there a definitive resource for learning C++? I come from php background and that had its manual @ [www.php.net](www.php.net). 

How did I learn to program/script? Getting thrown in at the deep end i think

See my wiki, which includes the mentioned title in an earlier post.

---

### Post by LaRoza on 2008-01-08
> **dwhitney67 said:**
> 
The code, as presented by LaRoza, is much easier to read, regardless of the fact that it is enclosed in the PHP format.


The PHP tags are good for syntax highlighting for many languages. I asked in the FF&H that the word "PHP Code" at the top be replaced with something generic, but I didn't get an answer.

---

### Post by snickers295 on 2008-01-08
> **pmasiar said:**
> ... because it **still** shows  no proper code structure. Any free editor above notepad will do proper indent, just use it.
I'm using gedit but can't find how to do that.
What editor do you sugguest?

> **Sam said:**
> Just a quick note, use the switch statement instead of multiple if-else-if chain.
```
switch (answer) {
    case 1:
        <snip>
        break;
    case 2:
        <snip>
        break;
    default:
        <snip>
        break;
}

```is better than
```
if (answer == 1) {
    <snip>
} else if (answer == 2) 
    <snip>
} else {
    <snip>
}
```
Like i said, I am just now starting c++ and am making this more complex as i learn how to use different syntax.  when i get to that i will probably use switch.

---

### Post by lvleph on 2008-01-08
I cannot believe that after two pages no one has said to comment out your code. This makes things more readable. Also, when you come back to it later you can figure out why you did something. Comment more than you think you need to, because even that won't be enough and you will get pissed at yourself for not using more later.

---

### Post by snickers295 on 2008-01-08
> **lvleph said:**
> I cannot believe that after two pages no one has said to comment out your code. This makes things more readable. Also, when you come back to it later you can figure out why you did something. Comment more than you think you need to, because even that won't be enough and you will get pissed at yourself for not using more later.
lol i will start doing that.
thanks.

---

### Post by snickers295 on 2008-01-08
thats what your talking about right?
i did this in emacs.

[PHP]#include <iostream>
#include <cstdlib>

using namespace std;

int start() {

  cout <<"Code And Number Program" << endl;
  cout <<"Enter 6 then press enter and it will count up to 10." << endl;

}


int main() {

  int answer;
  int code;
  int flag=1;
  int start0=1;

  while (flag == 1) {

    if (start0 == 1) {

      start();
      start0=0;

    }
    cout <<"Start? (1 yes, 2 no):";
    cin>>answer;

    if (answer == 1) {

      cout <<"Enter The Secret Code:";
      cin>>code;

      if (code == 6) {

    for (int x=1;x < 11; x++) {

      cin.get();
      cout << x << endl;
      flag=0;

    }

      }

      else {

    cout <<"Sorry, Thats Not The Code" << endl;
    flag=1;

      }

    } 

    else if (answer == 2) {

      flag=0;
      return 0;

    }

    else {

      cout <<"Sorry Thats Not A Option." << endl;
      flag=1;
    }

  }

  return 0;

}


[/PHP]

---

### Post by lvleph on 2008-01-08
If you were referring to my comment, then no.

I meant
```
#include <iostream>
#include <cstdlib>

using namespace std;

int start() { //Ask user to enter number

  cout <<"Code And Number Program" << endl;
  cout <<"Enter 6 then press enter and it will count up to 10." << endl;

}


int main() {

  int answer;
  int code;
  int flag=1;
  int start0=1;

  while (flag == 1) {

    if (start0 == 1) { //start the program

      start();
      start0=0; //reset flag so we don't come here again

    }
    cout <<"Start? (1 yes, 2 no):"; //ask user if they want to start program
    cin>>answer; //get their answer

    if (answer == 1) { //if answer is 1 ask for the secret code

      cout <<"Enter The Secret Code:"; //ask for the code
      cin>>code; //give me the code

      if (code == 6) { //user entered 6

    for (int x=1;x < 11; x++) { //loop from 1 to 10 and output x

      cin.get();
      cout << x << endl;
      flag=0;

    }

      }

      else { //didn't give me the code I was looking for

    cout <<"Sorry, Thats Not The Code" << endl;
    flag=1; //loop through again

      }

    } 

    else if (answer == 2) { //if they gave me 2

      flag=0; //kill loop
      return 0;

    }

    else { //user didn't input a proper option

      cout <<"Sorry Thats Not A Option." << endl;
      flag=1;
    }

  }

  return 0;

}  
```

EDIT: Hadn't used c++ in a while so I used # instead of //. It is fixed now.

---

### Post by snickers295 on 2008-01-08
> **lvleph said:**
> If you were referring to my comment, then no.

I meant
```
#include <iostream>
#include <cstdlib>

using namespace std;

int start() { //Ask user to enter number

  cout <<"Code And Number Program" << endl;
  cout <<"Enter 6 then press enter and it will count up to 10." << endl;

}


int main() {

  int answer;
  int code;
  int flag=1;
  int start0=1;

  while (flag == 1) {

    if (start0 == 1) { //start the program

      start();
      start0=0; //reset flag so we don't come here again

    }
    cout <<"Start? (1 yes, 2 no):"; //ask user if they want to start program
    cin>>answer; //get their answer

    if (answer == 1) { //if answer is 1 ask for the secret code

      cout <<"Enter The Secret Code:"; //ask for the code
      cin>>code; //give me the code

      if (code == 6) { //user entered 6

    for (int x=1;x < 11; x++) { //loop from 1 to 10 and output x

      cin.get();
      cout << x << endl;
      flag=0;

    }

      }

      else { //didn't give me the code I was looking for

    cout <<"Sorry, Thats Not The Code" << endl;
    flag=1; //loop through again

      }

    } 

    else if (answer == 2) { //if they gave me 2

      flag=0; //kill loop
      return 0;

    }

    else { //user didn't input a proper option

      cout <<"Sorry Thats Not A Option." << endl;
      flag=1;
    }

  }

  return 0;

}  
```EDIT: Hadn't used c++ in a while so I used # instead of //. It is fixed now.
no i was asking about the intend on it.

---

### Post by lvleph on 2008-01-08
Yeah, the indent makes reading it much easier. My personal preference would be to not have the extra line between the code and the {}, so instead of 
```
#include <iostream>
#include <cstdlib>

using namespace std;

int start() { //Ask user to enter number

  cout <<"Code And Number Program" << endl;
  cout <<"Enter 6 then press enter and it will count up to 10." << endl;

}


int main() {

  int answer;
  int code;
  int flag=1;
  int start0=1;

  while (flag == 1) {

    if (start0 == 1) { //start the program

      start();
      start0=0; //reset flag so we don't come here again

    }
    cout <<"Start? (1 yes, 2 no):"; //ask user if they want to start program
    cin>>answer; //get their answer

    if (answer == 1) { //if answer is 1 ask for the secret code

      cout <<"Enter The Secret Code:"; //ask for the code
      cin>>code; //give me the code

      if (code == 6) { //user entered 6

    for (int x=1;x < 11; x++) { //loop from 1 to 10 and output x

      cin.get();
      cout << x << endl;
      flag=0;

    }

      }

      else { //didn't give me the code I was looking for

    cout <<"Sorry, Thats Not The Code" << endl;
    flag=1; //loop through again

      }

    } 

    else if (answer == 2) { //if they gave me 2

      flag=0; //kill loop
      return 0;

    }

    else { //user didn't input a proper option

      cout <<"Sorry Thats Not A Option." << endl;
      flag=1;
    }

  }

  return 0;

}
```
You would have
```
#include <iostream>
#include <cstdlib>

using namespace std;

int start() { //Ask user to enter number
	cout <<"Code And Number Program" << endl;
	cout <<"Enter 6 then press enter and it will count up to 10." << endl;
}

int main() {
	int answer;
	int code;
	int flag=1;
	int start0=1;

	while (flag == 1) {
		if (start0 == 1) { //start the program
			start();
			start0=0; //reset flag so we don't come here again
		}

		cout <<"Start? (1 yes, 2 no):"; //ask user if they want to start program
		cin>>answer; //get their answer

		if (answer == 1) { //if answer is 1 ask for the secret code
			cout <<"Enter The Secret Code:"; //ask for the code
			cin>>code; //give me the code

			if (code == 6) { //user entered 6
				for (int x=1;x < 11; x++) { //loop from 1 to 10 and output x
					cin.get();
					cout << x << endl;
					flag=0;
				}
			}

			else { //didn't give me the code I was looking for
				cout <<"Sorry, Thats Not The Code" << endl;
				flag=1; //loop through again
			}
		} 

		else if (answer == 2) { //if they gave me 2
			flag=0; //kill loop
			return 0;
		}

		else { //user didn't input a proper option
			cout <<"Sorry Thats Not A Option." << endl;
			flag=1;
		}
	}

	return 0;
}
```
Looks cleaner to me, but this is personal preference and is what I was taught. I also fixed some of your indentation.

EDIT: Not sure why my tabs are so big, probably something to do with using a windows text editor.

---

### Post by snickers295 on 2008-01-08
hows this
[PHP]//Code And Countdown Program by Michael Smith
//This Is A Completely Useless Program Made To Practice C++

#include <iostream>

using namespace std;

//Create "Start" Function
int start() {

  cout <<"Code And Countdown Program" << endl;
  cout <<"Enter 6 then press enter and it will count up to 10." << endl;
}

//Main Function
int main() {

  //Declare Varables
  int answer;
  int code;
  int flag=1;
  int start0=1;

  //Main Loop
  while (flag == 1) {

    //Check For Start Function
    if (start0 == 1) {

      start();
      start0=0;
    }
    //Ask If Want To Start
    cout <<"Start? (1 yes, 2 no):";
    cin>>answer;
    
    //If Yes Ask For Code
    if (answer == 1) {

      cout <<"Enter The Secret Code:";
      cin>>code;

      //If Code Is Right
      if (code == 6) {

    for (int x=1;x < 11; x++) {

      cin.get();
      cout << x << endl;
      flag=0;
    }
      }

      //If Code Is Wrong
      else {

    cout <<"Sorry, Thats Not The Code" << endl;
    flag=1;
      }
    } 

    //If They Don't Want To Use The Program
    else if (answer == 2) {

      flag=0;
      return 0;
    }

    //If They Press A Wrong Button
    else {

      cout <<"Sorry Thats Not A Option." << endl;
      flag=1;
    }
  }
  
  //End Of Program
  return 0;

}

[/PHP]

---

### Post by lvleph on 2008-01-08
Looking much better.
You do have one indention problem.
```
      if (code == 6) {

    for (int x=1;x < 11; x++) {

      cin.get();
      cout << x << endl;
      flag=0;
    }
      }
```
In reality it doesn't matter, but it will make people look twice and go wtf?

Next step pointers? lol Nah, looks like you should start using strings and arrays.

---

### Post by snickers295 on 2008-01-08
> **lvleph said:**
> Looking much better.
You do have one indention problem.
```
      if (code == 6) {

    for (int x=1;x < 11; x++) {

      cin.get();
      cout << x << endl;
      flag=0;
    }
      }
```In reality it doesn't matter, but it will make people look twice and go wtf?

Next step pointers? lol Nah, looks like you should start using strings and arrays.
well.... according  to my tutorial, switch-case is next then pointers. [php]  if (code == 6) {
    for (int x=1;x < 11; x++) {

      cin.get();
      cout << x << endl;
      flag=0;
    }
      }[/php]any better?

---

### Post by lvleph on 2008-01-08
Well now your last } is indented too much, it should line up with the if. You are right though, switch case should be the next step. It is really, really easy. Almost the same as if statements. But instead of having if, else if, and else you just have case and no curly braces.

---

### Post by snickers295 on 2008-01-08
> **lvleph said:**
> Well now your last } is indented too much, it should line up with the if. You are right though, switch case should be the next step. It is really, really easy. Almost the same as if statements. But instead of having if, else if, and else you just have case and no curly braces.
[PHP]#include <iostream>

using namespace std;

int a;

int main() {

  cout <<"Enter a Number:";
  cin >> a;
  switch (a) {
  case 1:
    cout <<"one" <<endl;
    break;
  case 2:
    cout <<"two" <<endl;
    break;
  case 3:
    cout <<"three" <<endl;
    break;
  default:
    cout <<"Please Enter 1, 2 or 3" <<endl;
    break;
  }
  return 0;
}
[/PHP]
that was easy.

---

### Post by lvleph on 2008-01-08
Might want to indent the cases like this

```
#include <iostream>

using namespace std;

int a;

int main() {

		cout <<"Enter a Number:";
		cin >> a;
		switch (a) {
			case 1:
					cout <<"one" <<endl;
					break;
			case 2:
					cout <<"two" <<endl;
					break;
			case 3:
					cout <<"three" <<endl;
					break;
			default:
					cout <<"Please Enter 1, 2 or 3" <<endl;
					break;
		}
		return 0;
} 
```

Now you are starting to get the programming standard practices down. Are you starting to see the point in indention? If not do two different sets of switch case statement and you will start to see why.

Damn my tabs are huge. lol Looks weird. I hate windows.

---

### Post by lvleph on 2008-01-08
Can someone explain to me the point of having int main() instead of void main()? I was always taught void main().

---

### Post by pedro_orange on 2008-01-08
A function that has a type of void does not return anything to the environment. 

Int main() usually returns 0(an integer, aka int main) to tell the system it has completed, and to free up it's memory etc.
Functions outside of main can be of any type you like. Thats the magic of programming!

On the topic of indentation: it's all personal preference and if you wanted to you could write everything on one line. I've always been taught to do:

int main()
{
[INDENT]for(i=0;i!=10;++i)[/INDENT]
     [INDENT]{[/INDENT]
          [INDENT][INDENT]//do something[/INDENT][/INDENT]
           [INDENT][INDENT]if(condition) then[/INDENT][/INDENT]
           [INDENT][INDENT]{[/INDENT][/INDENT]
                 [INDENT][INDENT][INDENT]//do something else[/INDENT][/INDENT][/INDENT]
            [INDENT][INDENT]}[/INDENT][/INDENT]
     [INDENT]}[/INDENT]
     [INDENT]return 0;[/INDENT]
}

Only cause I like to line up the {}'s and makes it easier for me to read.

---

### Post by snickers295 on 2008-01-08
[http://www.daniweb.com/forums/thread78955.html](http://www.daniweb.com/forums/thread78955.html)

---

### Post by pmasiar on 2008-01-08
> **lvleph said:**
> Can someone explain to me the point of having int main() instead of void main()? I was always taught void main().

[http://en.wikipedia.org/wiki/Cargo_cult_programming](http://en.wikipedia.org/wiki/Cargo_cult_programming)

You should use main() as you need (with understanding what you do and why), not "as you were taught" :-)

---

### Post by chips24 on 2008-01-08
i _study_ the scripts first hand.

i hate the { and }

---

### Post by lvleph on 2008-01-08
> **pmasiar said:**
> [http://en.wikipedia.org/wiki/Cargo_cult_programming](http://en.wikipedia.org/wiki/Cargo_cult_programming)

You should use main() as you need (with understanding what you do and why), not "as you were taught" :-)

Well, I understand that but it was never explained to me why we used void. I read the link; makes sense.

---

### Post by Wybiral on 2008-01-08
> **lvleph said:**
> Well, I understand that but it was never explained to me why we used void. It seems to me that the memory allocation of using void causes memory leaks, if I understand it correctly?

Memory allocation of using void? What?

"int" is the normal way to go, we do that because (as pedro_orange mentioned) that's what modern OS's expect a program to return.

---

### Post by lvleph on 2008-01-08
There is memory allocation when any program runs. What I was saying was since the OS didn't receive the 0 it might maintain the memory allocation.

---

### Post by dwhitney67 on 2008-01-08
The OP's code has been morphed into many styles, with emphasis on indentation and readability.  Here's another spin, this time with some additional features and minor cleanup:

[PHP]#include <iostream>
#include <cstdlib>

using namespace std;

int start()
{
  cout <<"Code And Number Program" << endl;
  cout <<"Enter 6 then press enter and it will count up to 10." << endl;
}


int main()
{
  bool askAgain = true;

  start();

  while ( askAgain )
  {
    int answer = 0;
    cout <<"Start? (1 yes, 2 no): ";
    cin >> answer;

    if ( answer == 1 )
    {
      int code = 0;
      cout <<"Enter The Secret Code: ";
      cin >> code;

      if ( code == 6 )
      {
        for ( int x = 1; x < 11; x++ )
        {
          cout << x << endl;
          sleep(1);
        }
        askAgain = false;
      }
      else
      {
        cout <<"Sorry, Thats Not The Code. Try again." << endl;
      }
    } 
    else if (answer == 2)
    {
      askAgain = false;
    }
    else
    {
      cout <<"Sorry Thats Not A Option. Try again." << endl;
    }
  }

  return 0;
}[/PHP]

---

### Post by lvleph on 2008-01-08
> **dwhitney67 said:**
> The OP's code has been morphed into many styles, with emphasis on indentation and readability.  Here's another spin, this time with some additional features and minor cleanup:

[PHP]#include <iostream>
#include <cstdlib>

using namespace std;

int start()
{
  cout <<"Code And Number Program" << endl;
  cout <<"Enter 6 then press enter and it will count up to 10." << endl;
}


int main()
{
  bool askAgain = true;

  start();

  while ( askAgain )
  {
    int answer = 0;
    cout <<"Start? (1 yes, 2 no): ";
    cin >> answer;

    if ( answer == 1 )
    {
      int code = 0;
      cout <<"Enter The Secret Code: ";
      cin >> code;

      if ( code == 6 )
      {
        for ( int x = 1; x < 11; x++ )
        {
          cout << x << endl;
          sleep(1);
        }
        askAgain = false;
      }
      else
      {
        cout <<"Sorry, Thats Not The Code. Try again." << endl;
      }
    } 
    else if (answer == 2)
    {
      askAgain = false;
    }
    else
    {
      cout <<"Sorry Thats Not A Option. Try again." << endl;
    }
  }

  return 0;
}[/PHP]
One thing I have noticed is that there is an int start() but start does not pass a value. Why do that? Also, AskAgain doesn't need to be a boolean, but it is proper programming to do it that way. Also, I find it more readable to have the variable declarations at the top, it is personal preference though.

---

### Post by snickers295 on 2008-01-08
lol its funny look at my code thought the posts.
first looks like it was compressed and the last looks like real programming.

---

### Post by snickers295 on 2008-01-08
ok, i have come to pointers.
can anyone translate there use to dummy language?

---

### Post by lvleph on 2008-01-08
> **snickers295 said:**
> ok, i have come to pointers.
can anyone translate there use to dummy language?

Good luck. The only thing I can tell you is that they hold an address in the memory and not the value associated with the address. Did you cover arrays yet though? You really need to cover that first.

---

### Post by Wybiral on 2008-01-08
You are aware that variables are just labels for some address in memory that contains the data? Pointers are a means of storing that address (not the data at the address, but the address itself). Wait until you get into dealing with pointers of pointers and dereferencing them :)

---

### Post by lvleph on 2008-01-08
> **Wybiral said:**
> You are aware that variables are just labels for some address in memory that contains the data? Pointers are a means of storing that address (not the data at the address, but the address itself). Wait until you get into dealing with pointers of pointers and dereferencing them :)

And an array is a way to connect multiple addresses together. Each array index refers to an address associated with that array. So if you have an array a[] and you call a[5] it will look for the 6th address associate with that array and output what is stored in that location. Dereferencing a pointer works in a similar fashion to a[5].

EDIT1: That is a[5]=2; and *x=2; are similar because they both store 2 in some memory location.

EDIT2: But *x=2; and x=2; are completely different. x=2; will have x point to memory location 2, while *x=2 as stated earlier will store 2 in its memory location.

EDIT3: I am probably not going to be much help form here out, since I have not used pointers in 5 yrs. I remember the concept, but my syntax could be completely screwed.

---

### Post by Wybiral on 2008-01-08
> **lvleph said:**
> And an array is a way to connect multiple addresses together. Each array index refers to an address associated with that array. So if you have an array a[] and you call a[5] it will look for the 6th address associate with that array and output what is stored in that location. A dereferencing a pointer works in a similar fashion to a[5].

The actual label "a" is only one address (it IS a pointer), the other elements are allocated in series. When you dereference it or index it with "[]", you're actually saying "memory at a + x" which is why "x=0" is the first chunk of data in the array. "*(a + x)" is essentially the same as "a[x]" (though the array is a little different to the compiler since it knows the size of the array and can optimize with respect to that).

---

### Post by lvleph on 2008-01-08
> **Wybiral said:**
> The actual label "a" is only one address (it IS a pointer), the other elements are allocated in series. When you dereference it or index it with "[]", you're actually saying "memory at a + x" which is why "x=0" is the first chunk of data in the array. "*(a + x)" is essentially the same as "a[x]" (though the array is a little different to the compiler since it knows the size of the array and can optimize with respect to that).

I was pretty sure that is the way it worked. It has been a while, and I am just starting to get back into c++ and pointers (for my research). The fact that they are assigned sequentially is the reason way one has to allocate an array before one uses it. I do like perls dynamic array allocation, but I guess that is why c++ has linked lists and such.

EDIT: If we keep going like this, this will be the ultimate c++ thread. lol

---

### Post by Wybiral on 2008-01-08
> **lvleph said:**
> I was pretty sure that is the way it worked. It has been a while, and I am just starting to get back into c++ and pointers (for my research). The fact that they are assigned sequentially is the reason way one has to allocate an array before one uses it. I do like perls dynamic array allocation, but I guess that is why c++ has linked lists and such.

EDIT: If we keep going like this, this will be the ultimate c++ thread. lol

C++ has the entire Standard Template Library full of handy container types and iterators. There is also the new/delete statements which allow for dynamic memory allocation/deallocation but for new programmers... Well... Stay away from those until you know enough about memory. But I agree, not having to explicitly allocate/free memory in languages like Perl/Python is nice!

---

### Post by snickers295 on 2008-01-08
> **lvleph said:**
> I was pretty sure that is the way it worked. It has been a while, and I am just starting to get back into c++ and pointers (for my research). The fact that they are assigned sequentially is the reason way one has to allocate an array before one uses it. I do like perls dynamic array allocation, but I guess that is why c++ has linked lists and such.

EDIT: If we keep going like this, this will be the ultimate c++ thread. lol
maybe it will lol.
thanks everone for the help you have given me so far.

---

### Post by lvleph on 2008-01-08
> **Wybiral said:**
> C++ has the entire Standard Template Library full of handy container types and iterators. There is also the new/delete statements which allow for dynamic memory allocation/deallocation but for new programmers... Well... Stay away from those until you know enough about memory. But I agree, not having to explicitly allocate/free memory in languages like Perl/Python is nice!

If I recall correctly I used new and delete in Constructors and Destructors, respectively. But, now we are getting ahead of ourselves.

---

### Post by Majorix on 2008-01-08
> **Wybiral said:**
> There is also the new/delete statements which allow for dynamic memory allocation/deallocation but for new programmers... Well... Stay away from those until you know enough about memory.

If they stay away from them their scripts will end up as memory-eaters.

And why should it be dangerous to use new/delete? :confused:

---

### Post by Wybiral on 2008-01-08
> **Majorix said:**
> If they stay away from them their scripts will end up as memory-eaters.

And why should it be dangerous to use new/delete? :confused:

They should learn to use the STL since that's a large part of C++ programming. IMO new/delete have occasionally useful purposes, but 99% of the time an STL container will work great. Also, improper use of new/delete are what CAUSE code to leak memory, not using them actually ensures that your code doesn't leak. The STL containers are much safer and incredibly efficient (and they're there, so why not use them instead?)

---

### Post by dwhitney67 on 2008-01-08
Wybiral, usually you provide good input to this forum, but in your last post it seems that you are writing about "apples" and "oranges".

Memory allocation and deletion have nothing to do with STL containers.  They are separate topics, with each having their place, and usefulness, in C++.  There are cases where they both would have to be used in conjunction.  For instance:

```
std::vector< SomeObject * > ObjectCollection;
```

Managing data allocations is essential to avoid having a memory leak in an application; one should definitely be cautious to ensure that allocated memory is freed when it is no longer required.  Smart pointers, as provided with Boost, can assist one with this issue.

---

### Post by Wybiral on 2008-01-08
> **dwhitney67 said:**
> Wybiral, usually you provide good input to this forum, but in your last post it seems that you are writing about "apples" and "oranges".

Memory allocation and deletion have nothing to do with STL containers.  They are separate topics, with each having their place, and usefulness, in C++.  There are cases where they both would have to be used in conjunction.  For instance:

```
std::vector< SomeObject * > ObjectCollection;
```

Managing data allocations is essential to avoid having a memory leak in an application; one should definitely be cautious to ensure that allocated memory is freed when it is no longer required.  Smart pointers, as provided with Boost, can assist one with this issue.

I'm not saying to do away with them or anything, I'm just saying that most of the time I see them used in C++ is unjustified. If you can use a vector and the "resize" method, you should instead of trying to allocate a dynamic array (which I see a lot). But I agree that there are times when you should use them, but I disagree that a beginner should be learning them BEFORE learning to use the STL.

---

### Post by pedro_orange on 2008-01-09
Most C++ programmers use the standard library for every program, they just don't know it.

std::cout
std::cin
std::endl

Just having "using namespace std" means they can skip the std::
There are many more examples, but they're pretty selfevident.

If the OP is intending to learn Pointers, I'd suggest you craft yourself a Linked-List (Perhaps even a double linked list) that will help you grasp the concept.

It may be worth noting that the STL does include a LinkedList template but for learning's sake you might want to make your own, since it's also not a very hard thing to do. (Don't cheat by looking on the internet!) 

Read the top of this article if you are unsure of how Linked Lists behave: [http://en.wikipedia.org/wiki/Linked_list](http://en.wikipedia.org/wiki/Linked_list)

---

### Post by lvleph on 2008-01-09
In fact, a good project would be to make a huge number class (100+ digits) and write a program that can add, subtract, and maybe multiply and divide. This will teach you pointers, operator overides, classes, and structures.

---

### Post by snickers295 on 2008-01-09
> **lvleph said:**
> In fact, a good project would be to make a huge number class (100+ digits) and write a program that can add, subtract, and maybe multiply and divide. This will teach you pointers, operator overides, classes, and structures.
hmm, sounds a little like something sitting on my desk...

---

### Post by lvleph on 2008-01-09
It is a standard project for second semester cs students, at least at my *alma mater*.

---

### Post by Cappy on 2008-01-09
I wrote getlibs: [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)
as my first bash script so that I could learn bash.

I've saved every version of getlibs so it is possible to see the evolution of the script over time:
[http://www.boundlesssupremacy.com/Cappy/getlibs/](http://www.boundlesssupremacy.com/Cappy/getlibs/)
"getlibs" and "getlibs-all.deb" is always the current version.

---

