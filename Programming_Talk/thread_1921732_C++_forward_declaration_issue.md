---
title: "C++ forward declaration issue"
date: 2012-02-07
forum: Programming Talk
---

### Post by karimruan on 2012-02-07
I get an error saying that yesNo was not declared in this scope on lines 20 and 246 (when calling playAgain() which was forward declared on line 50. Here is the code:

```


/*
 * G U E S S I N G   G A M E 
 * version 3.0
 * by Matthew Ruane
 * 
 * Ultra documented beginner source code
 * for a simple console based guessing game
 * for tutorial on linux c++ programming for beginners
 * 
 * Part 1: Your First REAL Program
 * Lesson 3: Playing Another Round
 * 
 */



// We always start by #including the libraries that we will use in our programs




#include <iostream>     // the standard library, lets you use cout and cin
#include <cstdlib>      // lets you access the commands used by the OS




/* Global space: anything put outside of a function is considered
*  to be in the global space, meaning that any variables declared 
*  are usable by all functions, instead of just by the function it is 
* declared in.
*/ 

// this allows the program to use cout and cin
	
	
	using namespace std;  

// here we declared the integer variable x to equal 3


int x = 3;     

// here we declare the global lives as an integer

int lives = 5;              

// forward declare playagain()

	int playAgain(int yesNo);
	
	



//int playAgain(int yesNo);


// Function to check the users OS and clear the screen with the 
// appropriate command
// the credit for this code goes to http://www.daniweb.com/members/Narue/17893






void screenClear()
{
	#ifdef WINDOWS                       // if the user in on Windows
	std::system ( "cls");                // clear the screen with CLS command
	#else                                // else we assume the user is on a posix complaint OS (most Linux)
	std::system ( "clear");              // and clear the screen with CLEAR
	#endif
}




// her we define the function main() which all programs must have



int playAgain(int yesNo)

{
	// start a new line
	cout << endl;
	
	// ask user to play again
	cout << "Do you want to play again?" << endl;
	cout << "1 YES            2 NO  ";
	
	
	
	//ask user for input
	cin >> yesNo;
	
	// check answer for yes or a no
	if (yesNo == 1)
	{
		return yesNo;
	}
	else if (yesNo == 2)
	{
		
	}
	else
	{
		cout << "" << endl;
		cout << "Please choose either 1 for yes or 2 for no" << endl;
	}
	return yesNo;
}

int main()                  
{
	
	
	  
	
	 
	
	//  The below line of code will print "I am thinking of a number
	//  between 1 and 100" to the screen.
	//  endl; tells the compiler to start the next command on a new line
	
	
	
	cout << " I am thinking of a number between 1 and 100. " << endl;
	
	
	
	// The next command will print "Can you guess what this number is > "
	// but will not make a new line
	
	cout << " Can you guess what this number is?  > ";
	
	
	
	// Here we declared the variable y as an integer
	// so that the function main() can use it
	
	
	
	
	int y;
	
	
	
	
	// Now we use cin to get a number from the user
	// and we store that number in the variable y
	
	
	
	
	cin >> y;
	
	
	
	
	// Then we clear the screen
	// making sure that the correct system command is used
	
	
	
	
	screenClear();
	
	
	// Now we check to see what number the user input
	// if the user did not type a number that is
	//  equal to x (x = 3)
	
	
	
	if (y != x){                   
	                              
		

		// Tell the user "I'm sorry, that is wrong."
   
   

		cout << "I'm sorry, that is wrong. ";
		
		
		
		// Now we use the system command to clear the screen again
		
		
		
		screenClear();
		
		
		// since the user did not guess the number right, we will
		// take away one life, then return to main()
		
		
		
		if (lives < 1){
		
			screenClear();
			cout << "Game Over!";
			playAgain(yesNo);
			return 0;
		}
		else
		{
			
			--lives;
		}
		
		
		
		main();
		
		
	}
	
	
	
  // if the users answer is not a number besides x (x = 3)
  // (pretty much saying if the user typed 3)
  
  
  
	else
	
	{
		
		
  // clear the screen
  
  
  
		screenClear();
		
		
		
  // print "yes!" to the screen and start a new line
  
  
		 cout << "Yes! " << endl;
		 playAgain(yesNo);
	 
	}

	// all functions of type int must return something
	// in this case, 0, meaning all went well.
	
	
	return 0;  
			   
}
	

```

My son is 3 and just woke up, and is now playing Doom3. WTF????

---

### Post by ve4cib on 2012-02-07
yesNo is the parameter used by the function playAgain.  Parameters are like local variables; they exist only within that function, and cannot be used elsewhere.

When you call a function you pass it a *different* variable.  The function effectively gives the variable its own label ("yesNo" in this case).

In your program you need to read in a number from the user to pass to your function.  Inside main you would need to declare your own variable (call it anything you want) to use as the parameter.  For example:

```

int main()
{
int yesNo;

...

cout << "Game Over." << endl;
cout << "Would you like to play again? (0=no, 1=yes)" << endl;
cin >> yesNo;

playAgain(yesNo);

...

```

Here we've declared a new variable called yesNo *inside* of main.  This is a different variable than the "yesNo" variable declared inside "playAgain".  I realize this may sound confusing, and it is a little bit.  But eventually it will make sense, I promise.

When main executes we read in a value and store it in main's yesNo variable.  When we call playAgain we pass the *value* of yesNo to the function.  playAgain then saves that value in its own "yesNo" variable, and executes.

Either variable could be named something completely different; the names do NOT need to be the same.  This code would work exactly the same way:


```

int main()
{
int doesTheUserWantToPlayAgain;

...

cout << "Game Over." << endl;
cout << "Would you like to play again? (0=no, 1=yes)" << endl;
cin >> doesTheUserWantToPlayAgain;

playAgain(doesTheUserWantToPlayAgain);

...

```

Does this clear things up at all?

---

### Post by karimruan on 2012-02-07
Yes, thank you that makes perfect sense actually!
I forgot about parameters and variables only being usable within the functions that call them!

As for passing to playAgain(), I actually thought that it worked both ways. Is this a form of the infamous c++ inheritance, making playAgain() somewhat of a descendant of main() since main() is the one that called it?

I am actually creating a series of programs similar to the one above, documenting the things I have learned and once the programs are finished and cleanly written, I will make a tutorial for each explaining everything that is used. Because of this, the things that I don't fully understand, I would really like to learn more about. Would you mind if I posted the full source code to the first guessing game I wrote, so you can critique it?

I want to avoid having comments on my blog when I post it such as:

Actually, you should have done this, or declared it this way...

PLus make sure that I am learning good programming habits (I am a bit of a hacker when it comes to coding, they are almost always hacks LOL, never end up being clear, concise code.

My goal is to document everything as well.

---

### Post by muteXe on 2012-02-07
Calling main in a loop is horrible.
that screenClear() method aint working on my windows box.

And as already stated, you forward declare the method 'playAgain', but the compiler just sees a method that takes an int. It wont even look at what this variable is called, and has nothing to do with the yesNo in your main. You can verify this by changing your foward declaration to just
```

int playAgain(int);

```

to see the compiler is still happy.

p.s. nope, nothing to do with inheritence :)

---

### Post by karimruan on 2012-02-07
[QUOTE=muteXe;11670668]Calling main in a loop is horrible.
that screenClear() method aint working on my windows box.

Thanks for the heads up on the screen clear, I wonder what is wrong. Isn't the CLS command used in DOS to clear the screen?

How would you recommend I handle the function calls without looping main. I can write this program quickly and have it work, but I am trying to do things in a specific way to use for a tutorial. I was hoping to implement the playAgain() functionality without changing much of the code structure because my tutorial is part of a series which progresses through the completion of the guessing game, adding more functionality as the tut goes on.

Should I use a while loop inside main(), such as "while the answer is still wrong, ask for an answer, and break if answer is right to ask if user wants to try again?

I updated the code with what the first commenter suggested, it compiles but when run it does not function as I wanted it to. In fact, playAgain() barely works, and the result is not usable.

Here is the updated code:

```


/*
 * G U E S S I N G   G A M E 
 * version 3.0
 * by Matthew Ruane
 * 
 * Ultra documented beginner source code
 * for a simple console based guessing game
 * for tutorial on linux c++ programming for beginners
 * 
 * Part 1: Your First REAL Program
 * Lesson 3: Playing Another Round
 * 
 */



// We always start by #including the libraries that we will use in our programs




#include <iostream>     // the standard library, lets you use cout and cin
#include <cstdlib>      // lets you access the commands used by the OS




/* Global space: anything put outside of a function is considered
*  to be in the global space, meaning that any variables declared 
*  are usable by all functions, instead of just by the function it is 
* declared in.
*/ 

// this allows the program to use cout and cin
	
	
	using namespace std;  

// here we declared the integer variable x to equal 3


int x = 3;     

// here we declare the global lives as an integer

int lives = 5;              

// forward declare playagain()

	int playAgain(int yesNo);
	
	



//int playAgain(int yesNo);


// Function to check the users OS and clear the screen with the 
// appropriate command
// the credit for this code goes to http://www.daniweb.com/members/Narue/17893






void screenClear()
{
	#ifdef WINDOWS                       // if the user in on Windows
	std::system ( "cls");                // clear the screen with CLS command
	#else                                // else we assume the user is on a posix complaint OS (most Linux)
	std::system ( "clear");              // and clear the screen with CLEAR
	#endif
}








int playAgain(int yesNo)                   // this function acts quite strange

{
	// start a new line
	cout << endl;
	
	
	
	
	
	//ask user for input
	cin >> yesNo;
	
	// check answer for yes or a no
	if (yesNo == 1)
	{
		return yesNo;
		
	}
	else if (yesNo == 2)
	{
		
	}
	else
	{
		cout << " " << endl;
		cout << "Please choose either 1 for yes or 2 for no" << endl;
	}
	return yesNo;
}

int main()                  
{
	
	
	  int yesNo;                   //added this to declare the variable, hoping that
								   // cin >> yesNo would pass the value to the yesNo 
								   // variable in playAgain() but it doesn't seem to work
	
	 
	
	//  The below line of code will print "I am thinking of a number
	//  between 1 and 100" to the screen.
	//  endl; tells the compiler to start the next command on a new line
	
	
	
	cout << " I am thinking of a number between 1 and 100. " << endl;
	
	
	
	// The next command will print "Can you guess what this number is > "
	// but will not make a new line
	
	cout << " Can you guess what this number is?  > ";
	
	
	
	// Here we declared the variable y as an integer
	// so that the function main() can use it
	
	
	
	
	int y;
	
	
	
	
	// Now we use cin to get a number from the user
	// and we store that number in the variable y
	
	
	
	
	cin >> y;
	
	
	
	
	// Then we clear the screen
	// making sure that the correct system command is used
	
	
	
	
	screenClear();
	
	
	// Now we check to see what number the user input
	// if the user did not type a number that is
	//  equal to x (x = 3)
	
	
	
	if (y != x){                   
	                              
		

		// Tell the user "I'm sorry, that is wrong."
   
   

		cout << "I'm sorry, that is wrong. ";
		
		
		
		// Now we use the system command to clear the screen again
		
		
		
		screenClear();
		
		
		// since the user did not guess the number right, we will
		// take away one life, then return to main()
		
		
		
		if (lives < 1){
		
			screenClear();
			cout << "Game Over!";
			cout << "Do you want to play again?" << endl;
			cout << "1 YES            2 NO  ";
			cin >> yesNo;
			playAgain(yesNo);
			
		}
		else
		{
			
			--lives;
		}
		
		
		
		main();
		
		
	}
	
	
	
  // if the users answer is not a number besides x (x = 3)
  // (pretty much saying if the user typed 3)
  
  
  
	else
	
	{
		
		
  // clear the screen
  
  
  
		screenClear();
		
		
		
  // print "yes!" to the screen and start a new line
  
  
		 cout << "Yes! " << endl;
		 cout << "Do you want to play again?" << endl;
		 cout << "1 YES            2 NO  ";
		 
		 playAgain(yesNo);
	 
	}

	// all functions of type int must return something
	// in this case, 0, meaning all went well.
	
	
	return 0;  
			   
}
	

```

---

### Post by gateway67 on 2012-02-07
> **karimruan said:**
> 
Should I use a while loop inside main(), such as "while the answer is still wrong, ask for an answer, and break if answer is right to ask if user wants to try again?

Yes.

> **karimruan said:**
> 
I updated the code with what the first commenter suggested, it compiles but when run it does not function as I wanted it to. In fact, playAgain() barely works, and the result is not usable.

Your organizational skills are not fully developed yet.  Consider rewriting the playAgain() function to display the prompt, so that it is not done outside the function.  And if the input is incorrect in playAgain(), then keep prompting the user within that function until they get it right.  Also, in C++, it is much more common to return a bool type rather than an int when dealing with yes/no scenarios.

Consider the following...
```

#include <string>
#include <iostream>

using namespace std;

bool playAgain()
{
    char answer = 'n';
    bool validInput = false;

    do
    {
        string input;

        cout << "Do you want to play again (y or n)? ";
        getline(cin, input);

        // check to see if the user aborted input request (ie. issued ctrl-d)
        if (cin.fail() == true)
        {
            validInput = true;
        }
        else
        {
            answer = input[0];

            if (answer == 'y' || answer == 'Y' || answer == 'n' || answer == 'N')
            {
                validInput = true;
            }
            else
            {
                cout << "Invalid input; try again!\n" << endl;
            }
        }
    } while (validInput == false);

    return answer == 'y' || answer == 'Y';
}

int main()
{
    do
    {
        cout << "Game underway..." << endl;

        //...

    } while (playAgain());
}

```
P.S.  Use rand() to generate a random number between 1 and 100; don't hard-code the number 3.  And more importantly, don't use global variables!

---

### Post by karimruan on 2012-02-07
Thanks for the hint on global variables, although I never understood why to avoid them. I hardcoded the three because I was unsure if generating random numbers would add too much complexity to the code.

Also, any advice on my organizational efforts? I am used to Python, so all of the freedom with whitespace is like a whole new world to me.

And what is your opinion on 'if then else' statements verses switches? When would it be more appropriate to use one over the other?

---

### Post by ve4cib on 2012-02-07
If you're checking a single variable that could have multiple values, each of which needs to be handled differently, a switch is often a nice way to go.  If you need to check for true/false, or have multiple conditions to check for simultaneously then if statements are better.

This:
```

int state = INITIAL_STATE;

...

for(;;)
{
    switch(state)
    {
    case INITIAL_STATE:
        // do stuff
        break;
    case GATHER_INPUT_STATE:
        // do stuff
        break;
    case WRITE_OUTPUT_STATE:
        // do stuff
        break;
    case TERMINAL_STATE:
        // do stuff
        break;
    case INVALID_STATE:
    default:
        // do stuff
        break;
    }
}
```
is a good use of a switch statement.  It could be reimplemented using if/else if/else if/else if/...., but that might make it messier to read, and wouldn't gain anything efficiency-wise.

This:
```

int positionX, positionY, width, height;
...

if(positionX < 0 || positionX > MAX_X || positionY < 0 || positionY > MAX_Y || width <= 0 || height <= 0)
{
    cout << "Invalid position or size" << endl;
}
else if(height < MIN_HEIGHT || width < MIN_WIDTH)
{
    cout << "Object is too small" << endl;
}
else
{
    cout << "Object has acceptable size and position" << endl;
    // do stuff
}
```
is a good use of if statements.  We're checking multiple conditions each time using different operators (>, <, <=), something we can't do with a switch.  This would be impossible to do with a switch in fact.

As a general rule of thumb if you're not sure if you should use a switch or an if, use an if.  Everyone knows that they are, and therefore will be able to follow your code.

---

### Post by muteXe on 2012-02-08
> **karimruan said:**
> 

Also, any advice on my organizational efforts? 

Use a class to contain your game stuff. Something like this:

```

class Game()
{
	// all your game methods in here, AND:

	bool IsGameFinished();
	void GameFinished(bool finnned);
	void Init();  // initialise all your game varibles here in this method
	void Run();
private:
	bool m_bGamefinished;

};

Game::Game() :
m_bGamefinished(false)
{
	Init();
}

bool Game::IsGameFinished()
{
	return GameFinished;
}

void Game::GameFinished(bool finished)
{
	m_bGamefinished = finished;
}

void Game::Run()
{

        while(IsGameFinished()!= false)
        {
	// do you looping in here
	// when the lives have gone or the user 
	// guesses the number call:
                   GameFinished(true);
        }
}

int main()
{
	Game myGame;
	myGame.Run();

        return 0;
}


```

NOTE: i've just knocked this up in notepad and there's a lot missing, but it's just to give you an idea of how to use a class. notice main() is now tiny, which i try to do a lot.

---

