---
title: "Writing tic-tac-toe in C++"
date: 2014-04-13
forum: Programming Talk
---

### Post by spacerocket on 2014-04-13
Hello!

I decided to get more knowledge about C++ and this seems like a suitable first project.

I have started from this tutorial: [http://www.codeproject.com/Articles/678078/Cplusplus-is-fun-Writing-a-Tic-Tac-Toe-Game](http://www.codeproject.com/Articles/678078/Cplusplus-is-fun-Writing-a-Tic-Tac-Toe-Game) but then I came to the conclusion that this interface is only build for windows.

[http://www.cplusplus.com/forum/beginner/3041/](http://www.cplusplus.com/forum/beginner/3041/)

This seems more suitable choice for [COLOR=#0000cd]UNIX[/COLOR]-based systems?. [COLOR=#0000cd]Now in this one we are creating tic-tac-toe interface program with computer opponent against the player[/COLOR][COLOR=#000000]?  The parameters should be simpler than writing a chess engine.

If someone is interested in teaching this tic-tac-toe program to me it would be cool. We could go through it in parts:[/COLOR] like first part and what each symbol means:

#include <iostream>
using namespace std;

// This defines who we have playing:
enum players { draw, player1, player2 };

int main()
  {
  // This will only display when the program is first run
  cout << "You, are about to witness the program of the century.\n\n";

  // This tracks the number of times each player has won.
  int number_of_wins[ sizeof( players ) ] = {0};

  // And this tells us whether or not to play again.
  bool done = false;

  while (!done)
    {
    // This will display before each game
    cout << "COMMENCE TIC TAC TOE!!!!\n\n"
            "Ladies first, please pick the row then the column (1 through 3).\n\n";

    // Play a game and remember who won (if anyone)
    int winner = playgame();

    // Update it
    number_of_wins[ winner ]++;

    // Display it
    display_winner_stats( number_of_wins, winner );

    done = ask_to_play_again();
    }

  // Finish
  cout << "\n\nThank you for playing!\n";
  return 0;
  }

---

### Post by dwhitney67 on 2014-04-13
> **spacerocket said:**
> Hello!

We could go through it in parts:[/COLOR] like first part and what each symbol means:

I do not want to come across as being condescending, but if you require basic assistance for merely understanding the syntax of C++, then perhaps pursuing a Tic-Tac-Toe game should not be your first endeavor.  In fact, I would not recommend that you pursue any application that weighs heavily on graphics, much less something that relates to a game.  Start with something simple, and then work your way up (and no, you will not be able to learn C++ in 21 days like some people have indicated).

Here's an [online C++ tutorial]("http://www.cplusplus.com/doc/tutorial/") that might assist you to understand the basics of the language, and more importantly, the syntax.

---

### Post by spacerocket on 2014-04-13
Hi!

Thanks for your reply. I thought about buying this book: [http://www.cprogramming.com/c++book/?inl=sb](http://www.cprogramming.com/c++book/?inl=sb)  but before that it could be useful to learn Structure of a Program and Variables and Types + Basics of C++. I have already written some simple programs like "HELLO WORLD".

Would it be possible that you assist me on the issue eg. understanding [http://www.cplusplus.com/doc/tutorial/variables/](http://www.cplusplus.com/doc/tutorial/variables/)  because even if I read it twice I have to say that I don`t understand!

So step by step guidance by you on this issue Variables and Types so that I understand something (free or not).

---

### Post by dwhitney67 on 2014-04-13
> **spacerocket said:**
> Hi!

Thanks for your reply. I thought about buying this book: [http://www.cprogramming.com/c++book/?inl=sb](http://www.cprogramming.com/c++book/?inl=sb)  but before that it could be useful to learn Structure of a Program and Variables and Types + Basics of C++. I have already written some simple programs like "HELLO WORLD".

Would it be possible that you assist me on the issue eg. understanding [http://www.cplusplus.com/doc/tutorial/variables/](http://www.cplusplus.com/doc/tutorial/variables/)  because even if I read it twice I have to say that I don`t understand!

So step by step guidance by you on this issue Variables and Types so that I understand something (free or not).

A variable is used to store a value so that the value may be referenced (examined) at a later time.  Depending on the type of value that needs to be stored, a variable of that appropriate type is declared.  It is good practice to name variable using a descriptive name versus using a single-character.  For example 'numOfChickens' is better than 'n' or 'noc'.  Of course, when it obvious that the variable is a number, the rule can be relaxed (such as when declaring an index in a for-loop).

Basic (native) types include:  char, unsigned char, short, unsigned short, int, unsigned int, long, unsigned long, float, double and bool.

In C++, other (complex) types are available, and these are part of the Standard Template Library (STL); for example, string, list, vector, map, etc.  These all reside in the std namespace, and hence when using these types, it is good practice to preface the type with the "std::" namespace designation.  Optionally, you can employ the use of a "using namespace std" directive, but this not always desirable (especially in header files) and can lead to compiling errors when dealing with large projects in which there might be a type (class) name clash.

In C++ (and other object-oriented languages), you are also free to define your own classes (types).  For example:
```

struct Person
{
    std::string name;
    int age;
};

Person p;

p.name = "Jolly Rancher"
p.age = 40;

```

If you still don't quite understand these basic concepts, you may want to procure a C++ book written by a good author.  I cannot recommend any in particular, because frankly I have not held one in my hands in over 12 years.

---

### Post by spacerocket on 2014-04-13
Ok so **string** is for letters and **int** for numbers? 

[TABLE="class: snippet"]
[TR]
[TD="class: rownum"]1
2
[/TD]
 [TD="class: source"]int a;
float mynumber;[/TD]
[/TR]
[/TABLE]
 

These are two valid declarations of variables. The first one declares a variable of type int with the identifier a. The second one declares a variable of type float with the identifier mynumber. Once declared, the variables a and mynumber can be used within the rest of their scope in the program. ??

**"Each variable needs a name that identifies it and distinguishes it from the others**" Ok so in this case the variables were **p.name** which presents the value "Jolly Rancher" and **p.age** with value 40. In both cases variable is used to store data.

If you look at tic-tac-toe code I posted above what are the **variables **of this function? So in other words all applications eg. tic-tac-toe need to store data to memorize it during the game?

[COLOR=#ff0000]Basic (native) types include:  char, unsigned char, short, unsigned  short, int, unsigned int, long, unsigned long, float, double and char*[/COLOR]

Do you mean this:


[LIST]
[*]**Character types:** They can represent a single character, such as 'A' or '$'. The most basic type is char, which is a one-byte character. Other types are also provided for wider characters. 
[*]**Numerical integer types:** They can store a whole number value, such as 7 or 1024. They exist in a variety of sizes, and can either be *signed* or *unsigned*, depending on whether they support negative values or not. 
[*]**Floating-point types:** They can represent real values, such as 3.14 or 0.01, with different levels of precision, depending on which of the three floating-point types is used. 
[*]**Boolean type:** The boolean type, known in C++ as bool, can only represent one of two states, true or false. 
[/LIST]
 
Here is the complete list of fundamental types in C++:
 [TABLE="class: boxed"]
[TR]
[TH]Group[/TH]
[TH]Type names*[/TH]
[TH]Notes on size / precision[/TH]
[/TR]
[TR]
[TD]Character types[/TD]
[TD]**char**[/TD]
[TD]Exactly one byte in size. At least 8 bits.[/TD]
[/TR]
[TR]
[TD]**char16_t**[/TD]
[TD]Not smaller than char. At least 16 bits.[/TD]
[/TR]
[TR]
[TD]**char32_t**[/TD]
[TD]Not smaller than char16_t. At least 32 bits.[/TD]
[/TR]
[TR]
[TD]**wchar_t**[/TD]
[TD]Can represent the largest supported character set.[/TD]
[/TR]
[TR]
[TD]Integer types (signed)[/TD]
[TD]**signed char**[/TD]
[TD]Same size as char. At least 8 bits.[/TD]
[/TR]
[TR]
[TD]*signed* **short** *int*[/TD]
[TD]Not smaller than char. At least 16 bits.[/TD]
[/TR]
[TR]
[TD]*signed* **int**[/TD]
[TD]Not smaller than short. At least 16 bits.[/TD]
[/TR]
[TR]
[TD]*signed* **long** *int*[/TD]
[TD]Not smaller than int. At least 32 bits.[/TD]
[/TR]
[TR]
[TD]*signed* **long long** *int*[/TD]
[TD]Not smaller than long. At least 64 bits.[/TD]
[/TR]
[TR]
[TD]Integer types (unsigned)[/TD]
[TD]**unsigned char**[/TD]
[TD](same size as their signed counterparts)[/TD]
[/TR]
[TR]
[TD]**unsigned short** *int*[/TD]
[/TR]
[TR]
[TD]**unsigned** *int*[/TD]
[/TR]
[TR]
[TD]**unsigned long** *int*[/TD]
[/TR]
[TR]
[TD]**unsigned long long** *int*[/TD]
[/TR]
[TR]
[TD]Floating-point types[/TD]
[TD]**float**[/TD]
[TD][/TD]
[/TR]
[TR]
[TD]**double**[/TD]
[TD]Precision not less than float[/TD]
[/TR]
[TR]
[TD]**long double**[/TD]
[TD]Precision not less than double[/TD]
[/TR]
[TR]
[TD]Boolean type[/TD]
[TD]**bool**[/TD]
[TD][/TD]
[/TR]
[TR]
[TD]Void type[/TD]
[TD]**void**[/TD]
[TD]no storage[/TD]
[/TR]
[TR]
[TD]Null pointer[/TD]
[TD]**decltype(nullptr)**[/TD]
[TD][/TD]
[/TR]
[/TABLE]


In your example, what is the function of int? how does it differ form char? or is this the answer:

[COLOR=#0000cd]"Within each of the groups above, the difference between types is only their size (i.e., how much they occupy in memory)"[/COLOR]

How do I know how much each tic-tac-toe needs memory?

[COLOR=#0000cd]"each compiler implementation may specify the sizes for these types that  fit the best the architecture where the program is going to run."[/COLOR]    I don`t understand.

---

### Post by dwhitney67 on 2014-04-13
As a beginner, should not dwell upon how much memory an application will need.  If you want to determine the size of a particular type, you can employ the use of the sizeof() macro.  For example:
```

#include <iostream>
int main()
{
    std::cout << "The size of an int on my system is: " << sizeof(int) << " bytes." << std::endl;
}

```

Rather than analyze complex applications, you would serve yourself better if you wrote simple applications from the ground up.  Do not take someone else's effort to try to comprehend what's going on.  Learn on your own, with your own trivial applications.

If you want to dole around with TTT (Tic-Tac-Toe), then sit back to think about what the game entails, and what variables you will require to keep state of the game.  Below are some subtle hints...

1.  You have a 3x3 board, which is initially empty.
2.  You have two players, designated by an X and an O.
3.  Players take turns making moves.
4.  Player moves must be legal (ie. must be within the board space, and must be within an available space on the board).
5.  After each player has moved (or perhaps after a player has moved at least 3 times), check if he is a winner.
6.  Only a total of 9 (3x3) moves are permitted.
7.  After all moves have been played, and there is no winner, then it must be a tie.

P.S.  Earlier I forgot to include 'bool' as one of the system native types in my earlier post.  I have amended that post, and also removed the 'char*' type.  One can declare a pointer of any type, not just to a char type.

---

### Post by spacerocket on 2014-04-13
Ok the first step is that I need to write 3x3 board representation...?  It should look something like this?

#include <iostream>
using namespace std; 

char square[10] = {'o','1','2','3','4','5','6','7','8','9'};
int checkwin();
void board();

int main()
{
int player = 1,i,choice;
char mark;

	do
{
	board();
	player=(player%2)?1:2;
	cout << "Player " << player << ", enter a number: ";
	cin >> choice;
	mark=(player == 1) ? 'X' : 'O';
		if (choice == 1 && square[1] == '1')
			square[1] = mark;
		else if (choice == 2 && square[2] == '2')
			square[2] = mark;
		else if (choice == 3 && square[3] == '3')
			square[3] = mark;
		else if (choice == 4 && square[4] == '4')
			square[4] = mark;
		else if (choice == 5 && square[5] == '5')
			square[5] = mark;
		else if (choice == 6 && square[6] == '6')
			square[6] = mark;
		else if (choice == 7 && square[7] == '7')
			square[7] = mark;
		else if (choice == 8 && square[8] == '8')
			square[8] = mark;
		else if (choice == 9 && square[9] == '9')
			square[9] = mark;
		else
	{
			cout<<"Invalid move ";
			player--;
	}
	
	i=checkwin();
	player++;
	}while(i==-1);
		board();
	if(i==1)
		cout<<"==>\aPlayer "<<--player<<" win ";
	else
		cout<<"==>\aGame draw";
	
	return 0;
	}
	
	
	int checkwin()
{
	if (square[1] == square[2] && square[2] == square[3])
		return 1;
	else if (square[4] == square[5] && square[5] == square[6])
		return 1;
	else if (square[7] == square[8] && square[8] == square[9])
		return 1;
	else if (square[1] == square[4] && square[4] == square[7])
		return 1;
	else if (square[2] == square[5] && square[5] == square[8])
		return 1;
	else if (square[3] == square[6] && square[6] == square[9])
		return 1;
	else if (square[1] == square[5] && square[5] == square[9])
		return 1;
	else if (square[3] == square[5] && square[5] == square[7])
		return 1;
	else if (square[1] != '1' && square[2] != '2' &&  square[3] != '3' && square[4] != '4' && square[5] != '5'  && square[6] != '6' && square[7] != '7' &&  square[8] != '8' && square[9] != '9')
		return 0;
	else
		return -1;
}


void board()
{
	cout << "\n\n\tTic Tac Toe\n\n";
	cout << "Player 1 (X) - Player 2 (O)" << endl << endl;
	cout << endl;
	cout << " " << square[1] << " | " << square[2] << " | " << square[3] << endl;
	cout << "_____|_____|" << endl;
	cout << " " << square[4] << " | " << square[5] << " | " << square[6] << endl;
	cout << "_____|_____|" << endl;
	cout << " " << square[7] << " | " << square[8] << " | " << square[9] << endl;
}

---

### Post by dwhitney67 on 2014-04-13
Place code within CODE tags.

Also, if you require a board to be 3x3, then why have you declared it as 26x26?

---

### Post by spacerocket on 2014-04-13
I changed the code above.

---

### Post by dwhitney67 on 2014-04-13
It seems that you are on the right path.  There are a few things you could have done better.  For instance, you should employ the use of for-loops when checking for the win.  You could also isolate that algorithm that checks for a valid move.

Here's something I threw together.  Compare this with yours.
```

#include <iostream>

class TicTacToe
{
public:
	enum { PLAYER_X = 'X', PLAYER_O = 'O', AVAILABLE = ' '};

	void newGame()
	{
		for (int r = 0; r < 3; ++r)
		{
			for (int c = 0; c < 3; ++c)
			{
				board[r][c] = AVAILABLE;
			}
		}
	}

	void play()
	{
		for (int turns = 0; turns < 9; ++turns)
		{
			char player = (turns % 2 == 0 ? PLAYER_X : PLAYER_O);
			bool legal = false;
			do
			{
				int row = -1;
				int col = -1;

				std::cout << "\nPlayer " << player << " -- Choose a move..." << std::endl;
				std::cout << "Enter row and col (e.g. 1 2): ";
				std::cin  >> row >> col;

				legal = isLegalMove(row-1, col-1);

				if (!legal)
				{
					std::cout << "Illegal move!  Try again...\n" << std::endl;
				}
				else
				{
					board[row-1][col-1] = player;

					displayBoard();

					if (checkForWin(player))
					{
						std::cout << "Player " << player << " has won!" << std::endl;
						exit(0);
					}
				}
			} while (!legal);
		} 
		std::cout << "The game ended in a tie!" << std::endl;
	}

private:
	void displayBoard()
	{
		std::cout << "+-----+-----+-----+\n";
		for (int r = 0; r < 3; ++r)
		{
			std::cout << "|";
			for (int c = 0; c < 3; ++c)
			{
				std::cout << "  " << board[r][c] << "  |";
			}
			std::cout << "\n+-----+-----+-----+\n";
		}
		std::cout << std::endl;
	}

	bool isLegalMove(int row, int col)
	{
		if (row < 0 || row > 2 || col < 0 || col > 2)
			return false;

		// return true if cell in board is available, false otherwise
		return board[row][col] == AVAILABLE;
	}

	bool checkForWin(char player)
	{
		for (int r = 0; r < 3; ++r)
		{
			if (board[r][0] == player && board[r][1] == player && board[r][2] == player)
				return true;
		}
		for (int c = 0; c < 3; ++c)
		{
			if (board[0][c] == player && board[1][c] == player && board[2][c] == player)
				return true;
		}
		if ((board[0][0] == player && board[1][1] == player && board[2][2] == player) ||
		    (board[0][2] == player && board[1][1] == player && board[2][0] == player))
		{
			return true;
		}
		return false;
	}

	char board[3][3];
};

int main()
{
	TicTacToe ttt;

	ttt.newGame();
	ttt.play();
}

```

---

### Post by spacerocket on 2014-04-13
Hello

Now if I copy this to text editor and save as tic-tac-toe.c then type:

> ./a.out

It should launch the program?

To be honest I don`t really understand those functions, or to be more precise what is the function of each of them. 
enum { PLAYER_X = 'X', PLAYER_O = 'O', AVAILABLE = ' '};    is enum enumeration?

for (int r = 0; r < 3; ++r)  should write the board representation where int r generates the board arrays from 0 to 3 and ++r is some compiler to implement that?

---

### Post by dwhitney67 on 2014-04-13
> **spacerocket said:**
> Hello

Now if I copy this to text editor and save as tic-tac-toe.c then type:



It should launch the program?

To be honest I don`t really understand those functions, or to be more precise what is the function of each of them. 
enum { PLAYER_X = 'X', PLAYER_O = 'O', AVAILABLE = ' '};    is enum enumeration?

for (int r = 0; r < 3; ++r)  should write the board representation where int r generates the board arrays from 0 to 3 and ++r is some compiler to implement that?

Wow!  It looks like you are going to need a lot more help than I can offer.

But to get you off on the right foot, as per the thread topic, I provided a C++ program, not a C program.  Thus the file should have an extension of .cpp, not .c.

Secondly, whether you are programming in C++ or in C (btw, these are considered distinct languages), you need to compile the source code into an executable program that can be launched.  I thought that someone else had covered this detail with you in another thread (yep, right [here]("http://ubuntuforums.org/showthread.php?t=2216144&p=12983309#post12983309").)

In summary, if you want to execute the code I provided, you need to copy it to a file ending in .cpp (for example, TicTacToe.cpp).  Then, do the following:
```

g++ TicTacToe.cpp -o ttt    # note, for C++ we use g++ and for C, we use gcc

./ttt    # execute the program

```

---

### Post by spacerocket on 2014-04-14
I have the current code in text editor:

>  g++ Documents/TicTacToe.cpp -o ttt
Documents/TicTacToe.cpp: In member function &#8216;void TicTacToe::play()&#8217;:
Documents/TicTacToe.cpp:49:13: error: &#8216;exit&#8217; was not declared in this scope
       exit(0);
             ^


---

### Post by spjackson on 2014-04-14
> **spacerocket said:**
> [COLOR=#000000]*error: ‘exit’ was not declared in this scope*[/COLOR]
You need near the top of your source file
```

#include <cstdlib>

```

---

### Post by spacerocket on 2014-04-14
> user@user-MS-7817:~$ g++ Documents/TicTacToe.cpp -o ttt
user@user-MS-7817:~$ ./ttt    # execute the program

Player X -- Choose a move...
Enter row and col (e.g. 1 2): 

So this is the program how am I supposed to play it? Is it possible to make source code out of it?

---

### Post by spjackson on 2014-04-14
> **spacerocket said:**
> Player X -- Choose a move...
Enter row and col (e.g. 1 2): 

So this is the program how am I supposed to play it?

Like this:
```

 ./ttt


Player X -- Choose a move...
Enter row and col (e.g. 1 2): 1 1
+-----+-----+-----+
|  X  |     |     |
+-----+-----+-----+
|     |     |     |
+-----+-----+-----+
|     |     |     |
+-----+-----+-----+




Player O -- Choose a move...
Enter row and col (e.g. 1 2): 2 2
+-----+-----+-----+
|  X  |     |     |
+-----+-----+-----+
|     |  O  |     |
+-----+-----+-----+
|     |     |     |
+-----+-----+-----+




Player X -- Choose a move...
Enter row and col (e.g. 1 2): 1 3
+-----+-----+-----+
|  X  |     |  X  |
+-----+-----+-----+
|     |  O  |     |
+-----+-----+-----+
|     |     |     |
+-----+-----+-----+




Player O -- Choose a move...
Enter row and col (e.g. 1 2):

```
> Is it possible to make source code out of it?
??? TicTacToe.cpp **is **the source code. I don't understand this question.

---

### Post by spacerocket on 2014-04-14
Hi,

I thought the whole idea was that a computer plays against me tic-tac-toe, a computer that can calculate what it should play.

For example: computer vs player. 

I meant [artificial intelligence ]("http://www.sanakirja.org/search.php?id=87605&l2=17")

is it possible to change the C++ code so that there is a computer? Just like "search" and "evaluation" are the intelligence of a chess engine.

---

### Post by ofnuts on 2014-04-15
For Tic-Tac-Toe you don't need artificial intelligence since there are [quite simple algorithms]("http://en.wikipedia.org/wiki/Tic-tac-toe#Strategy").

---

### Post by spacerocket on 2014-04-15
[LIST=1]
[*]**Win**: If the player has two in a row, they can place a third to get three in a row.
[*]**Block**: If the opponent has two in a row, the player must play the third themself to block the opponent.
[*]**Fork**: Create an opportunity where the player has two threats to win (two non-blocked lines of 2).
[*]**Blocking an opponent's fork**:
[LIST]
[*]**Option 1**: The player should create two in a row to force the  opponent into defending, as long as it doesn't result in them creating a  fork. For example, if "X" has a corner, "O" has the center, and "X" has  the opposite corner as well, "O" must not play a corner in order to  win. (Playing a corner in this scenario creates a fork for "X" to win.)
[*]**Option 2**: If there is a configuration where the opponent can fork, the player should block that fork.
[/LIST]

[*]**Center**: A player marks the center. (If it is the first move  of the game, playing on a corner gives "O" more opportunities to make a  mistake and may therefore be the better choice; however, it makes no  difference between perfect players.)
[*]**Opposite corner**: If the opponent is in the corner, the player plays the opposite corner.
[*]**Empty corner**: The player plays in a corner square.
[*]**Empty side**: The player plays in a middle square on any of the 4 sides.
[/LIST]

Is it possible to use the algorithms in the C++ source code? This too seems too challenging I maybe continue my project with python...

---

### Post by ofnuts on 2014-04-16
All programming language have equal powers. With C++ you have to take care of more details (like memory allocation) but the resulting program has better performance. With Python you can focus more on the algorithm. But the algorithm above is fairly simple.

---

### Post by tux3do on 2014-04-16
> Is it possible to use the algorithms in the C++ source code? This too  seems too challenging I maybe continue my project with python...

yes, it is possible, no need to rewrite in Python.  
Go step by step. Try different algorithms :) The most simple would be the computer putting the dice (?) at random position. A slightly more complicated one would be to put the positions in the opposite position of your position. A more tactical strategy might be to always put the dice next to your dice.

---

