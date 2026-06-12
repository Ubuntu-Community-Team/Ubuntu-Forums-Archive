---
title: "while loop question in C++"
date: 2007-10-10
forum: Programming Talk
---

### Post by fourthdimension on 2007-10-10
Hey All

I'm writing a word scrambler game for fun where the user has a  certain about of chances to get the word right before a game over.  After so many words the user can earn more chances.  I'm using a while loop to keep track of the chances left.  My problem is, can I set up the loop to send the user to an earlier portion of the program, or do I have to recreate that portion of the program within the loop, or maybe just have the loop encompass the entire program?

Thanks.

---

### Post by Wybiral on 2007-10-10
You can use loops within loops. Or you may be able to do what you want with a function. It would help if you posted some code.

---

### Post by fourthdimension on 2007-10-10
I didn't post any code because I'm not quite sure how to implement what I want...  the only code I have doesn't have the decreasing chances involved.  I'll try to write a really simple program with what I think it would look like and tell you what's actually supposed to happen.  I'll update in a few minutes.
Thanks.

---

### Post by fourthdimension on 2007-10-10
OK, I know this program wouldn't compile, but it gives the general idea of what I'm trying to do.  It's supposed to ask the user to input the numbers he sees.  If it's correct, he goes on, if not, he loses a chance and tries again until a game over.  The program starts with three chances.   How would I write that correctly?  I only have a vague idea that I'll show below.  Again, I know it would never compile.

```
#include <cstdio>
#include <iostream>
#include <cstdlib>

using namespace std;
int main ()

{

int CHANCES;	
CHANCES = 3;
while (CHANCES > 0)
{//while1
	cout<< "Enter the number you see.";
	cout<< endl;
	cout<< "100";
	cout<< endl;
	int NUMBER2;
	cin>> NUMBER2;
	if (NUMBER2 = 100)
	{//if1
		cout<< "Good job.";
		cout<< endl;
		cout<< "Enter the number you see";
		cout<< endl;
		cout<< "101";
		cout<< endl;
		
		cin>> NUMBER2;
		if (NUMBER2 = 101)
		{//if2
			cout<< "Winner!";
			cout<< endl;
			
		}//if2
		else 
		{//else1
			CHANCES = CHANCES - 1;
		}//else1
		
		
		
		
		
		
		
	}//if1
	
	
}//while1

cout<< "Game Over";
cout<< endl;
return 0;






}
```

Thanks a lot.  Sorry for my ignorance.  I'm teaching myself, so it's a slow process sometimes.

---

### Post by dwhitney67 on 2007-10-10
You should try to be more efficient with your use of cout.  It is possible to group phrases, values, and endl all into one cout statement.  cout is a stream.

Also note that there is a difference between "=" and "==".  The former is for assignment, the latter is for performing a boolean comparison.

Finally, here's one of perhaps dozens of solutions to your simple game:
[PHP]
#include <cstdlib>
#include <iostream>

using namespace std;

static const int MAX_NUM = 100;

bool isGoodAnswer()
{
  const int number = rand() % MAX_NUM;
  int answer = MAX_NUM;

  cout << "\nType in the number that you see:  " << number << endl;
  cin  >> answer;

  return answer == number;
}


int main( int argc, char** argv )
{
  static const int MAX_WRONG = 3;
  int badAnswers = 0;

  do
  {
    if ( isGoodAnswer() )
    {
      cout << "Good answer... You're visual recognition of numbers and keyboard skills are remarkable!" << endl;
    }
    else
    {
      cout << "Oh so sorry... You entered an incorrect response." << endl;
      ++badAnswers;
    }
  } while ( badAnswers != MAX_WRONG );

  cout << "game over" << endl;
}[/PHP]

---

### Post by fourthdimension on 2007-10-10
Thanks for the help.  I'll have to look for some info on boolean operators before I go much further, I think.

Could you explain these two lines to me, please?
```


  return answer == number;
  while ( badAnswers != MAX_WRONG ); //I don't understand what "!" means here


```

Going back to my original question, though, I wondered how to send the user back to an earlier portion of the program if they gave an incorrect answer (i.e. can't pass the question till you get it right).  While this program helped me understand how to make a more efficient program and point me in the direction of what I should learn, I'm still in the dark about that...  
Thanks a lot.

---

### Post by Wybiral on 2007-10-10
x == y
Returns true if x is equal to y.

x != y
Returns true if x is NOT equal to y.

---

### Post by fourthdimension on 2007-10-10
Ah.  Thanks.  So "return" can either starts the loop over again or exit it?

---

### Post by Wybiral on 2007-10-10
It returns from (exits) a function and may return a value (in this case it returns true or false for whether or not "answer" equals "number").

They may seem odd at first, but you will enjoy using functions as opposed to single block code when you get there, trust me.

---

### Post by fourthdimension on 2007-10-10
So I wrote a test program similar to yours to see if I understood some of what you were talking about:
```
#include <cstdlib>
#include <iostream>

using namespace std;

int main (int argc, char** argv)
{
	int chancesLeft;
	chancesLeft = 3;
	while (chancesLeft > 0)
	{static const int MAX = 100;
	const int number = rand() % MAX;
	cout<< "enter the numbers you see.  you're allowed three wrong answers" <<endl 
	<<"before the program terminates.  ";
	cout<< number << "  ";
	int userInput;
	cin>> userInput;
	if (userInput == number)
	{cout<< "correct.  keep going.  " <<endl;
		
	}
	else 
	{
		chancesLeft = chancesLeft - 1;
		
		 (chancesLeft > 1);
		cout<< "you have " << chancesLeft << "chances left" <<endl;		
		
		
		
	}	
	
		
	}
	
	
	cout<< "game over" <<endl;
	return 0;
  
} 

```

It worked, but then I added an if-else condition at the end to keep the grammar correct when chancesLeft was 1:
```
#include <cstdlib>
#include <iostream>

using namespace std;

int main (int argc, char** argv)
{
	int chancesLeft;
	chancesLeft = 3;
	while (chancesLeft > 0)
	{static const int MAX = 100;
	const int number = rand() % MAX;
	cout<< "enter the numbers you see.  you're allowed three wrong answers" <<endl 
	<<"before the program terminates.  ";
	cout<< number << "  ";
	int userInput;
	cin>> userInput;
	if (userInput == number)
	{cout<< "correct.  keep going.  " <<endl;
		
	}
	else 
	{
		chancesLeft = chancesLeft - 1;
		
		[COLOR="Red"]if (chancesLeft > 1);
		{cout<< "you have " << chancesLeft << "chances left" <<endl;
			
		}
		else 
		{
			cout<< "you have " <<chancesLeft << " chane left" <<endl;
		}	[/COLOR]	
		
		
		
	}
		
	
	
	}
	
	
	cout<< "game over" <<endl;
	return 0;
  
} 

```

Now I get this error:
```
while_chances_test.cpp:30: error: expected primary-expression before ‘else’
while_chances_test.cpp:30: error: expected `;' before ‘else’
```

I went over those lines a few times before I posted this because I know it's just another one of those infamous "What's wrong with my program?!" questions, but I couldn't find what's wrong.  Can anyone point me in the right direction?

Thanks for all the help!

---

### Post by farruinn on 2007-10-10
> **fourthdimension said:**
> 
```

		[COLOR="Red"]if (chancesLeft > 1);
		{cout<< "you have " << chancesLeft << "chances left" <<endl;
			
		}
		else 
		{
			cout<< "you have " <<chancesLeft << " chane left" <<endl;
		}	[/COLOR]	
		


```

Now I get this error:
```
while_chances_test.cpp:30: error: expected primary-expression before ‘else’
while_chances_test.cpp:30: error: expected `;' before ‘else’
```


Remove the semicolon after your if condition:
```
if (chancesLeft > 1);
```

should be

```
if (chancesLeft > 1) 
```


Learning to understand error messages can be difficult but is very important. You'll be able to debug problems much more efficiently if you understand exactly what is causing an error rather than making guesses and making random changes based on that.

Good luck with your programming!

---

### Post by dwhitney67 on 2007-10-10
Ok, it's good that you have continued to pursue your little project.  Here's my analysis.

1.  The game instructions should not be stated within the while-loop.
2.  The variable 'userInput' should be initialized to a value (any value).
3.  Although "chancesLeft = chancesLeft - 1" is correct, most programmers use either the pre-decrement or post-increment format; thus your statement could be re-written as --chancesLeft, or alternatively as chancesLeft--.
4.  The syntax error you are getting is due to the semi-colon at the end of the if-statement (that you added).
5.  Since the code you added in the if-else-block is very similar, you could try a commonly used terciary technique as follows:

```
cout << "you have " << chancesLeft << "chance"
     << (chancesLeft > 1 ? "s" : "")
     << " left"
     << endl;
```

Such a construct above would obviate the need to have the if-else-block you added because the condition you had added is performed in the second line of the code shown above.

A terciary condition checks if the result is true or false; if it is true, then the first case ("s") is used; otherwise the second case ("") is used.  The result is to force one of these mini-strings onto the cout stream depending on the value of chancesLeft.

P.S.  My last comment is about coding style; you should try to format your code in a consistent manner, and more importantly, in a manner that is readable by your peers.

---

### Post by fourthdimension on 2007-10-10
Thanks a lot, everyone!  You've been a huge help to me.
I'll probably continue to write simple programs incorperating each new thing I learn until I work my way up to the bigger ones, just for the sake of learning, so you might be seeing more of me in these forums.  (OK, you're right, *a lot* more of me.) :lolflag:
Thanks.

---

