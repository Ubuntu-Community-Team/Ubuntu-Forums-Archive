---
title: "Beginner programming challenge #3"
date: 2009-04-28
forum: Programming Talk
---

### Post by Le-Froid on 2009-04-28
for winning the last challenge i was the lucky one to think of something. so here we go!

**[SIZE="5"]CHALLENGE[/SIZE]**:

create a game of rock paper scissors using any language you want.
make a human player and computer player and get the computer to pick rock paper or scissors at random.

**Rules**: Rock beats scissors, scissors beats paper, paper beats rock. if its two of the same its a tie

be sure to use comments when coding to make your program _easy to understand_.

this can be somewhat tricky to code but I think its doable ;)

Good luck!

---

### Post by gtr32 on 2009-04-28
Here's a quick Windows Form application written in C#. No comments but it's quite simple.

Compile either in MonoDevelop (add references to System, System.Drawing & System.Windows.Forms), or 

gmcs -r:/usr/lib/mono/2.0/System.Windows.Forms.dll,/usr/lib/mono/2.0/System.Drawing.dll filename.cs

```

using System;
using System.Drawing;
using System.Windows.Forms;

namespace rock_scissor_paper
{
    public enum SelectionType : short
    {
        ROCK, PAPER, SCISSORS
    }
    public enum Result : short
    {
        TIE, WIN, LOSE
    }

    static class Program
    {
        /// <summary>
        /// The main entry point for the application.
        /// </summary>
        [STAThread]
        static void Main()
        {
            Application.EnableVisualStyles();
            Application.SetCompatibleTextRenderingDefault(false);
            Application.Run(new Form1());
        }
    }

    public class Form1 : Form
    {
        private System.Windows.Forms.Button m_BtnRock;
        private System.Windows.Forms.Button m_BtnPaper;
        private System.Windows.Forms.Button m_BtnScissors;
        private System.Windows.Forms.Button m_BtnExit;
        private System.Windows.Forms.TextBox textBox1;

        public Form1()
        {
            InitializeComponent();
        }

        private System.ComponentModel.IContainer components = null;

        protected override void Dispose(bool disposing)
        {
            if (disposing && (components != null))
            {
                components.Dispose();
            }
            base.Dispose(disposing);
        }

        private void InitializeComponent()
        {
            this.m_BtnRock = new System.Windows.Forms.Button();
            this.m_BtnPaper = new System.Windows.Forms.Button();
            this.m_BtnScissors = new System.Windows.Forms.Button();
            this.m_BtnExit = new System.Windows.Forms.Button();
            this.textBox1 = new System.Windows.Forms.TextBox();
            this.SuspendLayout();
            // 
            // m_BtnRock
            // 
            this.m_BtnRock.Location = new System.Drawing.Point(29, 72);
            this.m_BtnRock.Name = "m_BtnRock";
            this.m_BtnRock.Size = new System.Drawing.Size(73, 23);
            this.m_BtnRock.TabIndex = 0;
            this.m_BtnRock.Text = "Rock";
            this.m_BtnRock.UseVisualStyleBackColor = true;
            this.m_BtnRock.Click += new System.EventHandler(this.m_BtnRock_Click);
            // 
            // m_BtnPaper
            // 
            this.m_BtnPaper.Location = new System.Drawing.Point(110, 72);
            this.m_BtnPaper.Name = "m_BtnPaper";
            this.m_BtnPaper.Size = new System.Drawing.Size(73, 23);
            this.m_BtnPaper.TabIndex = 1;
            this.m_BtnPaper.Text = "Paper";
            this.m_BtnPaper.UseVisualStyleBackColor = true;
            this.m_BtnPaper.Click += new System.EventHandler(this.m_BtnPaper_Click);
            // 
            // m_BtnScissors
            // 
            this.m_BtnScissors.Location = new System.Drawing.Point(191, 72);
            this.m_BtnScissors.Name = "m_BtnScissors";
            this.m_BtnScissors.Size = new System.Drawing.Size(73, 23);
            this.m_BtnScissors.TabIndex = 2;
            this.m_BtnScissors.Text = "Scissors";
            this.m_BtnScissors.UseVisualStyleBackColor = true;
            this.m_BtnScissors.Click += new System.EventHandler(this.m_BtnScissors_Click);
            // 
            // m_BtnExit
            // 
            this.m_BtnExit.Location = new System.Drawing.Point(300, 72);
            this.m_BtnExit.Name = "m_BtnExit";
            this.m_BtnExit.Size = new System.Drawing.Size(73, 23);
            this.m_BtnExit.TabIndex = 3;
            this.m_BtnExit.Text = "Exit";
            this.m_BtnExit.UseVisualStyleBackColor = true;
            this.m_BtnExit.Click += new System.EventHandler(this.m_BtnExit_Click);
            // 
            // textBox1
            // 
            this.textBox1.Location = new System.Drawing.Point(29, 13);
            this.textBox1.Multiline = true;
            this.textBox1.Name = "textBox1";
            this.textBox1.Size = new System.Drawing.Size(235, 53);
            this.textBox1.TabIndex = 4;
            // 
            // Form1
            // 
            this.AutoScaleDimensions = new System.Drawing.SizeF(6F, 13F);
            this.AutoScaleMode = System.Windows.Forms.AutoScaleMode.Font;
            this.ClientSize = new System.Drawing.Size(387, 111);
            this.Controls.Add(this.textBox1);
            this.Controls.Add(this.m_BtnExit);
            this.Controls.Add(this.m_BtnScissors);
            this.Controls.Add(this.m_BtnPaper);
            this.Controls.Add(this.m_BtnRock);
            this.Name = "Form1";
            this.Text = "Form1";
            this.ResumeLayout(false);
            this.PerformLayout();

        }

        private void MakeSelection(SelectionType _type)
        {

            SelectionType _comp_selection = GetComputerSelection();

            Result _res = (_type >= _comp_selection) ? (Result)(_type - _comp_selection) :
                (_comp_selection - _type == 1) ? Result.LOSE : Result.WIN;

            textBox1.AppendText(String.Format("You picked {0} vs. {1}, you {2}\r\n",
                _type, _comp_selection, _res));
			
	    textBox1.Refresh();

        }

        private SelectionType GetComputerSelection()
        {
            Random _rand = new Random();
            return (SelectionType)_rand.Next(3);
        }

        private void m_BtnExit_Click(object sender, EventArgs e)
        {
            Close();
        }

        private void m_BtnRock_Click(object sender, EventArgs e)
        {
            MakeSelection(SelectionType.ROCK);
        }

        private void m_BtnPaper_Click(object sender, EventArgs e)
        {
            MakeSelection(SelectionType.PAPER);
        }

        private void m_BtnScissors_Click(object sender, EventArgs e)
        {
            MakeSelection(SelectionType.SCISSORS);
        }
    }
}

```

---

### Post by soltanis on 2009-04-29
Thought of this in the shower. The to-string function makes me sad, but thinking around it is too difficult tonight.

```

(defvar rock 0)
(defvar paper 1)
(defvar scissors 2)

; Pick a new state
(defmacro pick-rps nil `(random 3))

; The compliment - what must I have to beat this?
(defun compliment (he-has)
	(cond ((= he-has rock) paper)
		((= he-has scissors) rock)
		((= he-has paper) scissors)))

; To string
(defun to-string (item)
	(cond ((= item rock) "rock")
		((= item scissors) "scissors")
		(t "paper")))

; Decide who wins
(defun winner (human computer)
	(if (= human computer) (progn (format t "tie!~%") (return-from winner)))
	(if (= human (compliment computer))
		(format t "you won! ~a beats ~a!~%" (to-string human) (to-string computer))
		(format t "you lost! ~a beats ~a!~%" (to-string computer) (to-string human))))
	
; Get input from the user
(defun get-user-input nil
	(format t "your move, sir? ")
	(force-output)
	(eval (read))) ; acceptable answers are 'rock', 'paper', or 'scissors'
	
; Finish
(defun finish nil
	(format t "thanks for playing!~%")
	(quit))

; Do you want to continue?
(defun continue-yes-no nil
	(format t "do you wish to continue [Y/n]? ")
	(force-output)
	(if (equalp (read-line) "n") (finish)))

; Run the game loop
(defun run-game-until-stop nil
	(winner (get-user-input) (pick-rps))
	(continue-yes-no)
	(run-game-until-stop))

```

Run by loading into your favorite interpreter then hitting (run-game-until-stop).

EDIT. Sorry, I should mention, this is ANSI Common Lisp.

---

### Post by Bodsda on 2009-04-29
Heres my entry, in python, seems to work, let me know what you think :)

[php]
# Rock paper scissors game

import random           # Used for randomly selecting the computers choice
import os               # Used for clearing the terminal
import time             # Used for pausing the program
import string           # needed for the .lower() function

choices = ['rock', 'paper', 'scissors']

def clear():
    os.system('clear')          # Defines a function to clear the terminal screen

def result(one, two):
    if one == 'rock' and two == 'rock':
        return "Tie"
    elif one == 'rock' and two == 'paper':
        return "Lose"
    elif one == 'rock' and two == 'scissors':
        return "Win"
    ####^^^#### Rock ####^^^####

    elif one == 'paper' and two == 'rock':
        return "Win"
    elif one == 'paper' and two == 'paper':
        return "Tie"
    elif one == 'paper' and two == 'scissors':
        return "Lose"

    ####^^^#### Paper ####^^^####

    elif one == 'scissors' and two == 'rock':
        return "Lose"
    elif one == 'scissors' and two == 'paper':
        return "Win"
    elif one == 'scissors' and two == 'scissors':
        return "Tie"

    ####^^^#### Scissors ####^^^####

    else:
        return "%s, %s" % (one, two)

def one():
    clear()
    comp_choice = random.choice(choices)

    print "\nPlease make a selection from the list"
    print "\n\t1) Rock\n\t2) Paper\n\t3) Scissors\n"
    choice = int(raw_input("Please choose; 1, 2 or 3: "))

    print "Computer chose %s, the result is %s\n" % (comp_choice, result(choices[choice - 1], comp_choice))

def two():
    clear()
    print "\nPlayer 1, please make a selection from the list"
    print "\n\t1) Rock\n\t2) Paper\n\t3) Scissors\n"
    choice = int(raw_input("Please choose; 1, 2 or 3: "))

    print "\nPlayer 2, please make a selection from the list"
    print "\n\t1) Rock\n\t2) Paper\n\t3) Scissors\n"
    choice2 = int(raw_input("Please choose; 1, 2 or 3: "))

    print "Player one chose %s, player two chose %s. The result for player 1 is %s!" % (choices[choice - 1], choices[choice2 - 1], result(choices[choice -1], choices[choice2 - 1]))


def main():             # This function mainly just prints the menu and calls the appropriate functions
    
    clear()
    print "Welcome to Bodsda's solution to\n Le-Froid's programming challenge #3\n"
    
    print "\t1) One Player\n\t2) Two Players\n\t3) Help\n\t4) Quit"
    choice = int(raw_input("Please make a selection: "))

    if choice == 1:
        one()           # If the users choice is one player, run function one()
    elif choice == 2:
        two()           # If the users choice is two player, run function two()
    elif choice == 3:
        print "\nPlease make a selection of 1, 2, 3 or 4\n"     # If the user asks for help, tell him what to do
    elif choice == 4:
        print "\nThanks for playing"
        time.sleep(2)           # Pause to let the user read the sentence, then quit
        quit()





main()
[/php]

---

### Post by viljun on 2009-04-29
How to win rock, paper & scissors when playing against other people.
(Maybe a bit offtopic but hope you'll find this interesting and useful. This game is usually played with big bets! (Have to empty the trash can etc))

---

1) Start with paper and try to start game quickly.

Explanation: If your opponent doesn't have much time to think what she should start with she'll probably start with a rock. Her hand is already on fist and it's easiest to keep it on fist when she has to think fast. At least don't start with scissors!

---

2) Use the item your opponent would have beaten if you have had it.

Explanation: Many players don't use same item twice in a row. That's why You can safely play paper if last time your opponent had scissors. You should play slowly with these players to give them enough time to change their next draw.

Also, minority players draw the same item many times in a row. With those players You should play fast and use the item that would have won them in a last round.

---

3) Examine patterns in your opponents play

Explanation: Many players have similar patterns as stated in rule 1 and 2. Patterns include some players tend draw always scissors after paper etc. When you notice a pattern it's easy to draw the winning item on the next round.

---

Have you found some other rules?

---

### Post by Le-Froid on 2009-04-29
> **Bodsda said:**
> Heres my entry, in python, seems to work, let me know what you think :)


im getting this error when i try your code
[php]
tim@linux:~/Desktop$ python rpc.py

Welcome to Bodsda's solution to
 Le-Froid's programming challenge #3

	1) One Player
	2) Two Players
	3) Help
	4) Quit
Please make a selection: 1

















Please make a selection from the list

	1) Rock
	2) Paper
	3) Scissors

Please choose; 1, 2 or 3: 2
Traceback (most recent call last):
  File "rpc.py", line 90, in <module>
    main()  
  File "rpc.py", line 76, in main
    one()           # If the users choice is one player, run function one()
  File "rpc.py", line 52, in one
    print "Computer chose %s, the result is %s\n" % (comp_choice, result(choices[choice - 1], choices[comp_choice -1]))
TypeError: unsupported operand type(s) for -: 'str' and 'int'
[/php]

---

### Post by soltanis on 2009-04-29
Cast "choice" to an int inside the list lookup expression, should fix the problem.

---

### Post by gtr32 on 2009-04-30
> **Bodsda said:**
> Heres my entry, in python, seems to work, let me know what you think :)

Lots of if-else statements. I also wouldn't use strings as parameters if it isn't necessary. I made my selection a pretty hard to read in the code on my first post to make it a one line solution, but lets make something easy to read and understand here.

Define the choices by enum like I did. The added = 1 etc are optional but I added them to make it easy to understand. (Syntax is C#)

```

    public enum SelectionType : short
    {
        ROCK = 0, PAPER = 1, SCISSORS = 2
    }
    public enum Result : short
    {
        TIE = 0, WIN = 1, LOSE = 2
    }

```

Make a matrix of the selections and substract the comp selection from user selection.
  
```

      R        P       S
R | 0-0=0 |  0-1=-1 |  0-2=-2
P | 1-0=1 |  1-1= 0 |  1-2=-1
S | 2-0=2 |  2-1= 1 |  2-2= 0

```

0 is always a tie. Rock vs Paper is a -1, Paper vs Scissor is also -1. Both are losses. When we analyze them all, our switch case would be:

```

            switch (USER - COMP)
            {
                case 0:
                    return TIE;
                case 1:
                case -2:
                    return WIN;
                case 2:
                case -1:
                    return LOSE;
            }

```

Does that make sense?

---

### Post by Bodsda on 2009-04-30
Ok, i edited my code, should work now, sorry about that.

@ gtr32

Thanks for the info, i havent really got into enumeration yet, still working through my C++ book and i stopped the python tutorial before it mentioned it, I suppose my way is much more code then yours, but unless you know about enumerations its hard to figure out how your code works, (although the matrix explanation helps a lot) so i kept it as if-elif-else statements for understandability for any newbies who read my code -- I will however be making an enum version in C++ sometime next week just for my own learning purposes, 

Thanks guys,

Bodsda

---

### Post by geirha on 2009-04-30
Using modulus will make it even prettier. 
```

outcome= ["tie", "b wins", "a wins"]
print outcome[(a - b) % 3]

```

---

### Post by krazyd on 2009-04-30
c++ version, fairly quickly hacked together so constructive criticism welcome ;)
[PHP]#include <iostream>
#include <cstdlib>
#include <ctime>
#include <limits>
#include <ios>

using std::cout;
using std::cin;
using std::endl;
using std::numeric_limits;
using std::streamsize;

bool startGame();
void findWinner(int, int);
bool displayChoice(int);
bool replay();

int main()
{
  srand ( time(NULL) );
  cout << endl << "Welcome to ROCK-PAPER-SCISSORS" << endl;
  while (startGame()) ;

  return 0;
}

bool startGame() {
  bool restart = true;
  int choice, compChoice;
  compChoice = rand() % 3 + 1;

  // print the menu
  cout << "\nEnter a number corresponding to your choice:" << endl;
  cout << "\t1. ROCK\n\t2. PAPER\n\t3. SCISSORS" << endl;

  // get the user's choice
  cin >> choice;

  // display both player's choices
  cout << "You ";
  // if the choice isn't valid, restart the game
  if (displayChoice(choice)) {
    cout << "I ";
    displayChoice(compChoice);

    // find & display the winner
    cout << "\nThat means that ";
    findWinner(choice, compChoice);
    return replay();
  }
  else
    return restart;  
}

void findWinner(int choice, int compChoice) {
  if (choice == compChoice)
    cout << "we drew!" << endl;
  else if (compChoice == choice + 1 || (compChoice == 1 && choice == 3))
    cout << "I won!" << endl;
  else
    cout << "you won!" << endl;
}

bool displayChoice(int choice) {
  bool validChoice = true;
  switch (choice)
  {
    case 1:
      cout << "chose ROCK." << endl;
      break;

    case 2:
      cout << "chose PAPER." << endl;
      break;

    case 3:
      cout << "chose SCISSORS." << endl;
      break;

    default:
      cout << "made an invalid choice." << endl;
      // reset stream state to 'good', discard any garbage and flag bad choice
      cin.clear();
      cin.ignore(numeric_limits<streamsize>::max(), '\n');
      validChoice = false;
  }

  return validChoice;
}

bool replay() {
  bool replay = false;
  char yn;

  cout << "Play again? (y/n)" << endl;
  cin >> yn;

  if (yn == 'y')
    replay = true;

  return replay;
}[/PHP]

---

### Post by gtr32 on 2009-04-30
> **geirha said:**
> Using modulus will make it even prettier. 
```

outcome= ["tie", "b wins", "a wins"]
print outcome[(a - b) % 3]

```

Have you tested that it works? Modulus will give negative return values when b is larger than a, and if you use unsigned vales you get wrong answers.

---

### Post by Yacoby on 2009-04-30
C++ 
[PHP]#include <iostream>
#include <string>

//used for the rand function
#include <cstdlib>

//included to allow us to seed the rand function
#include <ctime>


/**
* @brief class holds the error when we have an exception
*/
class GuessException{
public:
	GuessException(std::string des) : mDescription(des){}
    /** @return the human written description of the error. A hint about why it occured */
	inline std::string getDescription()const {
		return mDescription;
	}
private:
	const std::string mDescription;
	
};

/**
* @brief class to allow comparision between guesses
*/
class Guess{
	enum Comparison { CMP_EQUAL, CMP_GREATER, CMP_LESS };
public:

	enum GuessType { GT_ROCK = 1, GT_PAPER = 2, GT_SISSORS = 3 };

	/**
	* @brief sets the guess to a random number
	*/
	inline void getRandom(){set(rand() % 3 + 1); }
	inline GuessType get() const{
		return mGuess;
	}
	inline void set(GuessType gt){
		mGuess = gt;
	}
	/**
	* @brief sets the guess. It also preforms bounds checking
	*/
	void set(int gt){
		if ( gt >= 0 && gt <= 3 )
			mGuess = (GuessType)gt;
		else
			throw GuessException("Invalid input");
	}

	/**
	* @return the user selection as a string
	*/
	std::string toString() const{
		switch(mGuess){
			case GT_ROCK: return "Rock";
			case GT_PAPER: return "Paper";
			case GT_SISSORS: return "Sissors";
			throw GuessException("Invalid guess passed to function");
		}
	}



	inline bool operator < (const Guess& rhs) const{	return ( cmp(rhs) == CMP_LESS);	} 
	inline bool operator > (const Guess& rhs) const{	return ( cmp(rhs) == CMP_GREATER );	} 
	inline bool operator == (const Guess& rhs) const{	return ( cmp(rhs) == CMP_EQUAL );	}


	/**
	* @brief Writes the guess as a string
	*/
	friend  std::ostream &operator<<(std::ostream &stream, const Guess& g){
		stream << g.toString();
		return stream;
	}

	/**
	* @brief gets the guess as a number (1 - 3)
	*/
	friend std::istream &operator>>(std::istream &stream, Guess& g){
		int gt;
		stream >> gt;
		g.set(gt);
		return stream;
	}

private:
	GuessType mGuess;

	/**
	* @brief compares two guesses, the one held in the class, and arg1
	* @return the result of the comparison
	*/
	inline Comparison cmp(const Guess& g) const{
		return (Comparison)((3 + (int)get() - (int)g.get()) % 3);
	}

};




int main(){
	try{
		//guess uses random variables, so we have to seed the starting point
		srand(time(0));

		//hold how many times we have won or lost
		int wins = 0;
		int draws = 0;
		int losses = 0;

		while ( true ){

			//get the user guess
			Guess user;
			std::cout << "Enter your guess (Rock:1, Paper:2, Sissors:3)\n";
			std::cin >> user;

			Guess computer;
			computer.getRandom();

			//write the guesses
			std::cout << "You guessed:" << user << "\n";
			std::cout << "Computer guessed:" <<	computer << "\n";

			//check who has won
			if ( user > computer ){
				std::cout << "You WIN!\n";
				++wins;
			}else if ( user == computer ){
				std::cout << "Draw\n";
				++draws;
			}else if ( user < computer ){
				std::cout << "You lose\n";
				++losses;
			}else{
				throw GuessException("Error in comparison code");
			}

			std::string doContinue;
			std::cout << "Do you want to play again (y/n)";
			std::cin >> doContinue;
			
			//only contiune if the user has explicitly entered y.
			if ( doContinue == "y" )
				continue;
			
			//anything other than y, exit the loop
			break;
		}

		//write out the wins and losses
		std::cout 	<< "Wins:   "	<< wins << "\n"
					<< "Draws:  " 	<< draws << "\n"	
					<< "Losses: " 	<< losses << "\n";				

	}catch(GuessException& e){
		std::cout << "There was an error (" << e.getDescription() << ")";
		return 1;
	}
	return 0; 
}[/PHP]

---

### Post by geirha on 2009-04-30
> **gtr32 said:**
> Have you tested that it works? Modulus will give negative return values when b is larger than a, and if you use unsigned vales you get wrong answers.

Yes, in python at least, the modulus operator will return a number with the same signedness as the right hand value. If it doesn't in other languages, then adding 3 before doing the modulus should ensure a positive value.

---

### Post by baizon on 2009-04-30
Java
```
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.Random;

public class RockPaperScissors {

	// The Game Method
	private static void RPSGame() throws NumberFormatException, IOException {
		Random randGen = new Random();					 		// A random number generator.
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in)); // Keyboardreader...
		int computer = randGen.nextInt(3)+1;
		int player = 0;
		int rock = 1;
		int paper = 2;
		int scissors = 3;
		while (true) { 											// while picked wrong argument repeat.
			System.out.print("Pick rock paper or scissors [1-3]: ");
			player = Integer.valueOf(br.readLine());
			if (player == 1 || player == 2 || player == 3) {	// if picked rock, paper & scissors exit while
				break;
			} else if (player == 0) {							// if pressed 0 exit game
				System.out.println("Thank you for playing.");
				System.exit(0);
			} else {
				System.out.println();
				System.out.println("Illegal Argument picked. Pick a number from 1 to 3 or 0.");
			}
		}
		switch (player) {
		case 1 : System.out.println("You picked: Rock"); break;
		case 2 : System.out.println("You picked: Paper"); break;
		case 3 : System.out.println("You picked: Scissors"); break;
		}
		switch (computer) {
		case 1 : System.out.println("Computer picked: Rock"); break; 
		case 2 : System.out.println("Computer picked: Paper"); break;
		case 3 : System.out.println("Computer picked: Scissors"); break;
		}
		if (player == 1 && computer == 1 || player == 2 && computer == 2 || player == 3 && computer == 3) {
			System.out.println("DRAW.");
		} else if (player == 1 && computer == 2 || player == 2 && computer == 3 || player == 3 && computer == 1) {
			System.out.println("Computer wins.");
		} else {
			System.out.println("Player wins.");
		} 
		// Repeat that method again.
		RPSGame();
	}
	
	//The Main method of a Java class
	public static void main(String[] args) {
		// Need that try for catching a illegal input argument.
		try {
			System.out.println("Welcome to Rock-Paper-Scissors");
			System.out.println("Choose a number 1: Rock, 2: Paper, 3: Scissors, or 0 for exit.");
			RPSGame();
		} catch (NumberFormatException e) {
			e.printStackTrace();
		} catch (IOException e) {
			e.printStackTrace();
		}
	}
}
```
Paste that in the RockPaperScissors.java file.

Compile ```
javac RockPaperScissors.java
```
Run ```
java RockPaperScissors.class
```

---

### Post by gtr32 on 2009-04-30
> **geirha said:**
> adding 3 before doing the modulus should ensure a positive value.

That fixed it. 

```

        public enum Outcome : byte
        {
            TIE, WIN, LOSE
        }

        public enum Type : byte
        {
            ROCK, PAPER, SCISSOR
        }

        for (Type n = Type.ROCK; n <= Type.SCISSOR; n++)
            for (Type x = Type.ROCK; x <= Type.SCISSOR; x++)
                 Console.WriteLine(String.Format("{0} vs {1} = {2}", n, x, (Outcome)((3 + n - x) % 3)));


```

Output:

ROCK vs ROCK = TIE
ROCK vs PAPER = LOSE
ROCK vs SCISSOR = WIN
PAPER vs ROCK = WIN
PAPER vs PAPER = TIE
PAPER vs SCISSOR = LOSE
SCISSOR vs ROCK = LOSE
SCISSOR vs PAPER = WIN
SCISSOR vs SCISSOR = TIE

---

### Post by sekinto on 2009-04-30
[http://dl.getdropbox.com/u/470842/RPS.py](http://dl.getdropbox.com/u/470842/RPS.py)

```

#!/usr/bin/env python
##########################################
##        ####        ####        ####  ##
##  ####  ####  ####  ####  ##########  ##
##  ####  ####  ####  ####  ##########  ##
##        ####        ####        ####  ##
##  ##  ######  ################  ########
##  ###  #####  ################  ########
##  ####  ####  ##########        ####  ##
##########################################

       ####  ####  ####  ####  ####       
       #  Rock! Paper! Scissors!  #
       #  By: Anthony Sinnott     #
       #  Date: 2009 - April 30   #
       ####  ####  ####  ####  ####

#### Chapter 1: "Importation is really just another word for teleportation." -- teh alienz
from random import choice

#### Chapter 2: Three simple rules (!SUPEROFFICIAL)
rules = 'Rock beats scissors.\nScissors beats paper.\nPaper beats rock.\n\n\nVolcano beats... jk!'

#### Chapter 3: Who came up with these sucky phrases?
phraseWin = [
	'You won, stop trying so hard.',
	'First is the worst, second is the best! Good thing I lost!',
	'I think you cheated. >_>']
phraseLuz = [
	'HAHAHA, VICTORY IS MINE!',
	'Yay, I win! Now where\'s my $20?',
	'Ha! You suck! I won and you lost! I bet a cow could beat you at this game! (and cows don\'t even have fingers)']
phraseTie = [
	'A staaaaaalemate? How BORING!',
	'Don\'t press the power button yet, we need to redo this!',
	'Oh gawd, A TIE! A TIE!!!']

#### Chapter 4: **** ain't cool if it don't involve numbers!
win = [2,3,7]
luz = [1,5,6]
wins = 0
luzs = 0

#### Chapter 5: A menu! *le gasp*
print '\n'
def mainmenu():
	while True:
		print '\nPress 1 for game, 2 for rules or 3 for Spanish.'
		try:
			option = input(':> ')
		except:
			option = 4
		if option == 1:
			return 0
		elif option == 2:
			print '\n' + rules
		elif option == 3:
			print '\nOur translators left yesterday.'
		else:
			print '\nInvalid input moron!'

#### Chapter 6: Every computer must make a choice.
def generatemove():
	dataset = choice([(-3,'Rock'), (-2,'Paper'), (-1,'Scissors')])
	print 'My choice: ' + dataset[1]
	return dataset[0]

#### Chapter 7: To win, or not to win?
def scoreboard(moveHuman, moveComputer):
	global wins, luzs
	if (moveHuman + moveComputer) in win:
		print choice(phraseWin)
		wins += 1
	elif (moveHuman + moveComputer) in luz:
		print choice(phraseLuz)
		luzs += 1
	else:
		print choice(phraseTie)
	print 'Wins\tLuzs\n' + str(wins) + '\t' + str(luzs)

#### Chapter 8: Are we finally ready to do something serious?
mainmenu()
while True:
	print '\nMake your move! (r,p,s,exit)'
	option = raw_input(':> ')[0].lower()
	if option == 'r':
		print '\nYour choice: Rock'
		moveHuman = 3
	elif option == 'p':
		print '\nYour choice: Paper'
		moveHuman = 6
	elif option == 's':
		print '\nYour choice: Scissors'
		moveHuman = 9
	elif option == 'e':
		print '\nGoodbye!'
		exit()
	if option in ['r','p','s']:
		moveComputer = generatemove()
		scoreboard(moveHuman, moveComputer)
	else:
		print '\nInvalid input moron!'

```

---

### Post by ZuLuuuuuu on 2009-04-30
In Tcl:

**file: rps.tcl**
```
# Procedure to read the graphical hands from hand_signs.txt.
proc read_hand_signs {} {
    # This is the global array variable to hold the hand graphics.
    global hand_signs

    set hand_signs_file [open "[file dirname [info script]]/hand_signs.txt"]

    # There are three hand signs which occupy 14 lines each.
    for {set i 0} {$i < 3} {incr i} {
        for {set j 0} {$j < 14} {incr j} {
            set line [gets $hand_signs_file]
            for {set k [string length $line]} {$k < 35} {incr k} {
                set line "$line "
            }
            lappend hand_signs($i) $line
        }
    }

    close $hand_signs_file
}

# Procedure to select a hand sign for a player. It selects a hand sign
# automatically by default but if an option other than -auto is given
# then the hand sign is selected manually, that means it asks player
# to choose the hand sign.
proc select_sign {{type -auto}} {
    if {$type == "-auto"} {
        # Select a number between 0 and 2, inclusively and randomly.
        set player_s_choice [expr (round((rand() * 10)) % 3)]

        return $player_s_choice
    } else {
        set player_s_choice 99

        # Check if the player's choice is valid. If not then ask
        # him/her again.
        while {$player_s_choice != -1
               && $player_s_choice != 1
               && $player_s_choice != 2
               && $player_s_choice != 3} {
            # Print the valid choices.
            puts "\n==================="
            puts "Select your sign!\n"
            puts " (1) Rock"
            puts " (2) Paper"
            puts " (3) Scissors"
            puts "===================\n"

            # Read the player's sign from standard input.
            gets stdin player_s_choice
        }

        # Decrease player's choice by 1 before returning. So that the
        # choice's number is in sync with array indexing mechanism
        # which starts from 0.
        return [expr $player_s_choice - 1]
    }
}

# This is the procedure where the winner is decided. Also where the
# hand graphics are displayed.
proc fight {player_1_s_sign player_2_s_sign} {
    global hand_signs

    # Display hand graphics line by line. Every line will actually be composed
    # of two hands.
    for {set i 0} {$i < 15} {incr i} {
        # Display the first hand's part.
        set hand_1 [lindex $hand_signs($player_1_s_sign) $i]

        # Display the second hand's part. Before displaying take the
        # mirror image.
        set hand_2 [string reverse [lindex $hand_signs($player_2_s_sign) $i]]
        set hand_2 [regsub -all {/} $hand_2 "%"]
        set hand_2 [regsub -all {\\} $hand_2 "/"]
        set hand_2 [regsub -all {%} $hand_2 "\\"]
        
        puts "$hand_1 $hand_2"
    }

    # This is an algorithm to determine the winner in a short
    # way instead of writing all the possible combinations.
    if {$player_1_s_sign == $player_2_s_sign} {
        puts "Tie..."
    } elseif {(($player_1_s_sign - 1) % 3) == $player_2_s_sign} {
        puts "You won. [deny]"
    } else {
        puts "I WON! [humiliate]"
    }
}

# This is a procedure for computer to select one of the humiliations
# randomly after winning a game.
proc humiliate {} {
    set humiliations {"HAHAHAH!" "LOSER!" "N00B!" "PWNAGE!" "YOU ARE MISERABLE HAHAHAH!"}
    return [lindex $humiliations [expr (round((rand() * 10)) % [llength $humiliations])]]
}

# And this is a procedure to select one of the denials randomly after
# loosing a game.
proc deny {} {
    set denials {"Don't cheat next time!" "Big deal!" "Re!" "Pure luck!"}
    return [lindex $denials [expr (round((rand() * 10)) % [llength $denials])]]
}

# Here the main program begins.

# First, call the procedure to read the hand graphics into a global variable.
read_hand_signs

# Then start the game and don't stop until the human player enters -1.
while {1} {
    # Player 1 is a human player so it selects the sign manually.
    set player_1_s_sign [select_sign -manual]

    # Here it checks -2 because in select_sign procedure the selection
    # of the player is decreased by 1 so that the player's choice is
    # in sync with array's indexing mechanism which starts from 0 not 1.
    if {$player_1_s_sign == -2} {
        break
    }

    # Then select player 2's sign automatically.
    set player_2_s_sign [select_sign]

    # Finally, determine the winner and show the result.
    fight $player_1_s_sign $player_2_s_sign 
}
```

**file: hand_signs.txt** (Writing a Tcl program without graphics would be a shame :))
```
                                  
                                  
        ________                  
       /        \____             
______/          \   \            
            __   _\___\           
             \\_/  \ \            
              \_\__/__\           
              \       |           
               \______|           
_______        \     /            
       \________\___/             
                                  
                                  
                                  
                                  
              _______             
        _____/       \            
       /       ______/_____       
______/                    \      
                   ________|___   
                               \  
                    ___________/  
                              |   
                   __________/    
_______                   |       
       \_________________/        
                                  
                                  
                                  
        ________       _____      
       /        \____==     \     
______/          \      ____/     
            __   _\___==_         
             \\_/  \     ===___   
              \_\__/__         \  
              \       |===_____/  
               \______|           
_______        \     /            
       \________\___/             
```

Just create both files (rps.tcl and hand_signs.txt) in a folder. And execute the script with:

```
tclsh ./rps.tcl
```

Enter **1** for rock **2** for paper **3** for scissors. Enter **-1** or press **ctrl+z** to exit.

*** The spaces in hand_signs.txt are important! Be careful while copying/pasting.**

---

### Post by bruce2000 on 2009-05-01
```

import random

def printGameMenu():
    print
    print "1 Rock"
    print "2 Paper"
    print "3 Scissors"

def printMainMenu():
    print
    print "Welcome to bruce2000's rock paper scissors game"
    print "1 Play a game"
    print "2 Show scores"
    print "3 Quit"

def num2name(handNumber):
    if handNumber==1:
        return "ROCK"
    if handNumber==2:
        return "PAPER"    
    if handNumber==3:
        return "SCISSORS"

#Returns 0 for a draw, 1 for a player win, and 2 for a computer win        
def playGame():
    printGameMenu()
    intPlayerHand=input("Enter 1, 2 or 3: ")
    
    print "You chose...",
    print num2name(intPlayerHand),"..."
    
    #Get a random number between 1 and 3 inclusive
    intComputerHand=random.randint(1, 3)

    print "The computer chose...",
    print num2name(intComputerHand),"..."
   
    #When both players have same hand, game is drawn
    if intPlayerHand==intComputerHand:
       print "Game is drawn"
       return 0 
   
    #Check against player having hand 1 (Rock)
    if intPlayerHand==1:
        if intComputerHand==2:
            return 2
        else:
            return 1
    #Check against player having hand 2 (Paper)
    elif intPlayerHand==2:
        if intComputerHand==1:
            return 1
        else:
            return 2
    #Check against player having hand 3 (Scissors)
    elif intPlayerHand==3:
        if intComputerHand==1:
            return 2
        else:
            return 1
      
def showScores():
    print "Player Score:",intPlayerScore
    print "Computer Score:",intComputerScore

intPlayerScore=0
intComputerScore=0

while True:
    printMainMenu()
    
    intMenuInput=input("Enter 1, 2 or 3: ")
    
    if intMenuInput==1:
        intWinner=playGame()
        if intWinner==1:
            print "Player wins"
            intPlayerScore+=1
        if intWinner==2:
            print "Computer wins"
            intComputerScore+=1            
    elif intMenuInput==2:
        showScores()
    elif intMenuInput==3:
        break

print
print "Thank you for playing!"

```

Here's my solution in Python

---

### Post by jimi_hendrix on 2009-05-01
@Zuluuuuuuuuu

did you draw those hands?!?!

---

### Post by ZuLuuuuuu on 2009-05-01
> **jimi_hendrix said:**
> @Zuluuuuuuuuu

did you draw those hands?!?!

Yes. Don't ask how many minutes I wasted :D

---

### Post by Christmas on 2009-05-01
In C:
```
/* A game of rock/paper/scissors. Rock beats scissors, scissors beats paper, paper beats rock. */

#include <stdio.h>
#include <stdlib.h>
#include <time.h>

int main ()
{
  int ai, my; /* computer value, my value */
  printf ("Enter your value (0 - rock, 1 scissors, 2 - paper, negative to exit): ");
  scanf ("%i", &my);
  while (my >= 0) /* play this until a negative value is typed */
    {
      //      srand (time (NULL));
      ai = rand () % 3; /* 0 - rock, 1 - scissors, 2 - paper */
      if (ai == 0) /* ai has rock */
	{
	  if (my == 1)
	    {
	      printf ("Computer has rock, you have scissors. You lose :(\n");
	    }
	  if (my == 2)
	    {
	      printf ("Computer has rock, you have paper. Congrats, you won!\n");
	    }
	  if (my == 0)
	    {
	      printf ("Both of you have rock. No winner.\n");
	    }
	}
      if (ai == 1)
	{
	  if (my == 0)
	    {
	      printf ("Computer has scissors, you have rock. Congrats, you won!\n");
	    }
	  if (my == 1)
	    {
	      printf ("Both of you have scissors. No winner.\n");
	    }
	  if (my == 2)
	    {
	      printf ("Computer has scissors, you have paper. You lose :(\n");
	    }
	}
      if (ai == 2)
	{
	  if (my == 0)
	    {
	      printf ("Computer has paper, you have rock. You lose :(\n");
	    }
	  if (my == 1)
	    {
	      printf ("Computer has paper, you have scissors. You won!\n");
	    }
	  if (my == 2)
	    {
	      printf ("Computer has paper, you have paper. No winner.\n");
	    }
	}
      printf ("Enter your value (0 - rock, 1 scissors, 2 - paper, negative to exit): ");
      scanf ("%i", &my);
    }
  return 0;
}

```
See [here](http://pastebin.com/f42716a1e) for syntax highlighting. It seems to work, but I commented out the srand (time (NULL)); and the stdlib.h and time.h directives are not needed anymore. Is this right? I mean the rand function seems to work without using it with srand.

---

### Post by ZuLuuuuuu on 2009-05-01
You should use srand() so that rand() function gives random values everytime you restart your application. If you don't put it, you can observe that rand() function generates the exact same sequence everytime you restart your program.

For example, start your program and follow the sequence 1, 1, 1, 1, 1 then close the application and start it again and enter the same sequence, you will see that the won/lose/tie messages will appear in exactly the same order as before.

Though, I don't know why GCC allows to compile without stdlib when you remove srand() because still rand() depends on stdlib.

---

### Post by Christmas on 2009-05-01
Thanks for the explanation ZuLuuuuuu, it behaved that way so it looks like the srand is needed. Well, I did not comment out the stdlib directive in the first place. Otherwise I get a warning (only with the -Wall switch enabled):
```
$ gcc -Wall rps.c
rps.c: In function ‘main’:
rps.c:15: warning: implicit declaration of function ‘rand’
```

---

### Post by originalsynthesis on 2009-05-02
I'm thinking its overkill for a game like this, but I just started learning how to do OOP, so I figured this would be a fun way to practice. 

Python
```

import random

#these will be checked by Judge() to check the games.
TIE = [['r','r'],['p','p'],['s','s']]
WIN = [['r','s'],['p','r'],['s','p']]
LOSE = [['s','r'],['r','p'],['p','s']]


#gotta have a cool title screen right?
print \
 """
 ROCK!!!!!!!!!
	      PAPER!!!!!!!!!
			    SCISSORS!!!!!!!!!
			    
	    The Ultimate Challenge.
 
 
 
 
 """
name = raw_input('Enter your name :')
 
class Player(object):
	"""The human element"""
        def __init__(self):
                self.name = name        
                self.win = 0
		print '\nHello, ',self.name,'!\n'
		
	def throwR(self,judge):
	    """attack with rock!"""
	    print '\nplayer throws rock!'
	    judge.addthrow('r',0)

        def throwP(self,judge):
	    """attack with paper!"""
	    print '\nplayer throws paper!'
	    judge.addthrow('p',0)

        def throwS(self,judge):
	    """attack with scissors"""
	    print '\nplayer throws scissors!'
	    judge.addthrow('s',0)
        
class Judge(object):
	"""Catches all throws, declares the winner"""
        def __init__(self):
	    self.game = [0,0]
                
        def addthrow(self,throw, index): #pairs each throw into a list, player gets index[0], comp gets index[1]
	    self.game[index] = throw
                
	def winner(self,player,opponent): #compares the list game with those in WIN LOSE and TIE,
                                                                        #and adjusts players' win counter appropriately
	    if self.game in WIN:
		player.win += 1
		print '\n\n\t*****game goes to :', player.name,"*****"

	    elif self.game in LOSE:
		opponent.win += 1
		print '\n\n\t*****game goes to :', opponent.name,"*****"
	    
	    elif self.game in TIE:
		print '\n\n\t*****Game is a tie.*****'
                
class Opponent(object):
	"""The cold silicon enemy"""
        def __init__(self):
                
                self.win = (0) 
                self.name = "CPU"
                
        def throw(self,judge):
        	"""generates a random throw"""
                THROWS = ('r','p','s')
                throw = random.choice(THROWS)
                if throw == 'r':
                        th = 'rock!'
                elif throw == 'p':
                        th = 'paper!'
                else:
                        th = 'scissors!'
                print 'Computer throws ',th
                judge.addthrow(throw,1)
                
def gamemenu():
        print '\n1. Throw a Rock!'
        print '2. Throw some Paper!'
        print '3. Throw your scissors!'
        print '4. Exit/Surrender'
        print 'choose from the above.'          

def getInt(prompt):
    """get an integer value"""
    try:
	i = int(raw_input(prompt))
	return i
	
    except(ValueError):
	print "\n\nhey! I need numbers here!\n"
	i = getInt(prompt)
	return i
  
def getYesNo(prompt):
    answer = raw_input(prompt)
    if answer in ('y','yes','yeah','sure','si','affirmative'):
	return 'y'
    elif answer in ('n','no','nah','never','niet','why?'):
	return 'n'

def main():
    player= Player()
    opponent = Opponent()
    judge = Judge()
    
    again = True
    
    
    raw_input('\nPrepare yourself!!!!')
    print "Beat the computer twice to win."
    
    ch = 0
    while again: 
	
	while player.win < 2 and opponent.win < 2 and ch != 4:
			
	    gamemenu()
	    ch = getInt('\nyour move :')

	    if ch == 1:
		    player.throwR(judge)
		    opponent.throw(judge)
		    judge.winner(player,opponent)

	    elif ch == 2:
		    player.throwP(judge)
		    opponent.throw(judge)
		    judge.winner(player,opponent)
					    
	    elif ch == 3:
		    player.throwS(judge)
		    opponent.throw(judge)
		    judge.winner(player,opponent)

	    elif ch == 4:
		    again = False
		    print "\nbye bye!"
					    
	    if player.win == 2:
	      print player.name," wins!"
	      
	    elif opponent.win == 2:
		print "The machine has won....."
	
	if ch != 4:      
	    again = getYesNo('\nAnother round? (y/n) \n')
	else:
	    again = raw_input('Ahh, to heck with you then! Vaminos!')
	
	if again == 'y':
		again = True
		player.win = 0
		opponent.win = 0
	
	elif again == 'n':
		again = False    
                
main()

raw_input('Mash a key to exit.')
                
        


```

---

### Post by Jiraiya_sama on 2009-05-02
Here's my entry:

[PHP]
#include <ctime>
#include <cstdlib>
#include <cstring>
#include <iostream>
using namespace std;

int main(int argc, char** argv)
{
  const char* hand[] = {"rock", "paper", "scissors"}; //allows us to easily print the winner.
  srand(time(NULL));  //seed rand so we actually get a random rand;
  unsigned int com = rand() % 3; //limits random to 0-2
  unsigned int player, result; 

  if(argc < 2 || strlen(argv[1]) > 1 || !isdigit(argv[1][0]) || (player = atoi(argv[1])) > 2) //detect errors such as not enough arguments,
  {                                                                                           //too many digits, and out of range,
    cerr << "Invalid argument. Please use '0' for rock, '1' for paper, and '2' for scissors." << endl; //while also assigning a value to player
    return 1;
  }

  if(!(result = (3+(com - player)) %3)) // if result is 0, you tied.
    cout << "You and the computer tied. (You and Computer: " << hand[com] << ")" << endl; //prints the corresponding hand for the comp value.
  else
    cout << (result == 1?"The computer":"You") << " won. (You: " << hand[player]  //tests if result is -2 or 1, and if so prints 
      << ", Computer: " << hand[com] << ")" << endl;                              //"The computer won". Else it prints "you won."
  return 0;
}
[/PHP]

I did my best to make a tiny program. This one weighs in at 26 loc, and I have commented it.

The only thing I did not bother explaining in the comments was "result = (3+(com - player)) %3" since that's already been discussed in this thread.

It works by feeding 0-2(rock,paper,scissors) to it as a command line argument.

---

### Post by Luggy on 2009-05-02
Here is my entry in python. It just runs once but I think the logic used is pretty simple.

Also has error checking :D

[PHP]
# import random function so computer can pick random items
import random

# setup constants for rock paper and scissor
ROCK, PAPER, SCISSOR = range(3)

# a little function to create the string of the throw
def getThrowString(throwInt):
	if(throwInt == ROCK):
		return "Rock"
	elif(throwInt == PAPER):
		return "Paper"
	elif(throwInt == SCISSOR):
		return "Scissor"
	else:
		return ""

# show the user all available picks
print("1: Rock")
print("2: Paper")
print("3: Scissor")

# some error handling to double check the user input
try:
	# let the user make his pick
	userThrow = raw_input("What do you want to throw? ")
	# change that value so it corolated with the values of ROCK PAPER and SCISSOR
	userThrow = int(userThrow) - 1
	# raise an exception if the value entered was a number but out of bounds
	if( userThrow < ROCK or userThrow > SCISSOR):
		raise
except:	
	# if there was an error, inform the user
	print("Invalid input entered.")
	print("Goodbye :)")
else:
	# if there was no error keep on going

	# the CPU generates its pick
	cpuThrow = random.randint(ROCK,SCISSOR)

	# print what both throws were
	print "User throws ", getThrowString(userThrow)
	print "CPU throws ", getThrowString(cpuThrow)

	# calculate who wins and who looses
	
	# check if there was a tie
	if( userThrow == cpuThrow ):
		print("It's a tie!")
	#check all situations where the user could have won
	elif( (userThrow == ROCK and cpuThrow == SCISSOR) or (userThrow == cpuThrow + 1) ):
		print("You Win :)")
	#if the user didn't win or tie then he lost
	else:
		print("you lose :(")
[/PHP]

---

### Post by Sinkingships7 on 2009-05-03
Here's my Python hack. It's exception-safe. The only way to exit is to close the terminal or Ctrl-C.

EDIT: Here's v0.2. The changes were aesthetics. The program is designed to be very easy to read by beginners, as long as there's an elementary understanding of classes.
[php]
def main():
    import random
    
    available_weapons = ['rock', 'paper', 'scissors']
    
    print "\tROCK | PAPER | SCISSORS\nChoices: rock, paper, scissors\n"
    
    while True:  # Play forever >:]
        while True:
            try:
                player = Weapon(raw_input("Choose your weapon: "))
                computer = Weapon(random.choice(available_weapons))
                
                if player.weapon not in available_weapons:
                    raise Exception
                    
                break  # Everything checked out. Let's go.
                
            except Exception:
                print "Invalid input. Try again.\n"
        
        # Print out the choices made by each player.
        print "\nYOU: %s" % player.weapon
        print "NPC: %s" % computer.weapon
        
        result = fight(player, computer)
        
        if result != 'tie' : print "%s wins!\n" % result
        else               : print "Tie!\n"

class Weapon:
    weapon      = None
    weakness    = None
    
    def __init__(self, W):
        self.weapon = W
        if self.weapon == 'rock'    : self.weakness = 'paper'
        if self.weapon == 'paper'   : self.weakness = 'scissors'
        if self.weapon == 'scissors': self.weakness = 'rock'
        
def fight(p1, p2):
    if p1.weapon == p2.weapon   : return 'tie'  
    if p1.weakness != p2.weapon : return 'player'
    else                        : return 'computer'

if __name__ == "__main__":
    main()
[/php]

---

### Post by Bodsda on 2009-05-05
Any clues as to when this will be judged?

---

### Post by asm_Coty on 2009-05-05
Must in run on Linux or can I write in in DOS?

---

### Post by Bodsda on 2009-05-05
I suppose, as long as you could emulate dos with dosbox or something -- lol, 

should be interesting

---

### Post by asm_Coty on 2009-05-05
Cool, I'll see what I can do *grabs a cup of Ubuntu*

---

### Post by gtr32 on 2009-05-05
This is cleaned up version of my previous code, with some minor changes. It has **comments** now so if someone wants to create a GUI application with mono and C#, this is a simple example.

---

### Post by cobolt01 on 2009-05-05
I wrote this in Java, I hope i didnt over complicate the challenge:

[PHP]
import java.io.*;
public class RockPaperScissors
{
	BufferedReader br;
	public RockPaperScissors()throws IOException
	{	
		//Player makes a Selection
		br = new BufferedReader(new InputStreamReader(System.in));
		System.out.println("Rock, Paper or Scissors?");
		System.out.println("1 = Rock");
		System.out.println("2 = Paper");
		System.out.println("3 = Scissors\n");
		int pSelection = Integer.parseInt(br.readLine());
		System.out.println("You chose :"+sayIt(pSelection)+"\n");
		
		//CPU makes a Selection
		int cpuSelection = cpuSelection();
		System.out.println("CPU chose :"+sayIt(cpuSelection)+"\n\n");
		
		if(pSelection != cpuSelection)//If there is a winner
		{
		  System.out.println("The winner is "+whoWins(pSelection,cpuSelection));
		}
		else//If there is a draw
			System.out.println("draw!");
	}

	public int cpuSelection()
	{
		int ret = 0;
		//ret must be given a value in case it does not match any of the 
		//below criteria.
		double rand = Math.random();
		if(rand >= 0 && rand < 0.3)//Rock
			ret = 1;
			
		else if(rand >= 0.3 && rand < 0.6)//Paper
			ret = 2;
			
		else if(rand >=0.6 && rand <= 1)//Scissors
			ret = 3;
			
		return ret;
	}
	public String sayIt(int n)//Which letter corresponds to which word
	{
		String retS = "";
		if(n == 1)
			retS = "Rock";
			
		else if(n == 2)
			retS = "Paper";
			
		else if(n == 3)
			retS = "Scissors";
		
		return retS;
			
	}
	public String whoWins(int a, int b)
	{
		String winner = "";
		if(a == 1 && b == 2)
			winner = sayIt(b);
		else if(a == 2 && b == 3)
			winner = sayIt(b);
		else if(a == 3 && b == 1)
			winner = sayIt(b);
		else
			winner = sayIt(a);
			
		return winner;
			
	}
	public static void main(String[]args)throws IOException
	{
		RockPaperScissors rps = new RockPaperScissors();
	}
}
[/PHP]

I'm sure I made some mistakes, but I need to go to bed now.

---

### Post by gtr32 on 2009-05-05
> **cobolt01 said:**
> I'm sure I made some mistakes, but I need to go to bed now.

Have a good sleep! I didn't test your code but one thing caught my eye:

```

        if(rand >= 0 && rand < 0.3)//Rock
            ret = 1;
            
        else if(rand >= 0.3 && rand < 0.6)//Paper
            ret = 2;
            
        else if(rand >=0.6 && rand <= 1)//Scissors
            ret = 3;

```

Seems like the computer favours a certain selection in your implementation. ;)

---

### Post by Le-Froid on 2009-05-05
> **Bodsda said:**
> Any clues as to when this will be judged?

Im thinking about waiting another day or two then I'll judge everything

---

### Post by baizon on 2009-05-05
> **cobolt01 said:**
> 
[PHP]
public int cpuSelection()
	{
		int ret = 0;
		//ret must be given a value in case it does not match any of the 
		//below criteria.
		double rand = Math.random();
		if(rand >= 0 && rand < 0.3)//Rock
			ret = 1;
			
		else if(rand >= 0.3 && rand < 0.6)//Paper
			ret = 2;
			
		else if(rand >=0.6 && rand <= 1)//Scissors
			ret = 3;
			
		return ret;
	}
[/PHP]

I'm sure I made some mistakes, but I need to go to bed now.
Why double? There is the Java random Integer generator ;)
```

Random randGen = new Random();
int ret = randGen.nextInt(3)+1; //to set the limit to 3.

```

---

### Post by Froodolt on 2009-05-05
Hello, 

Here's an other Java contribution.
I'm learning Java, and the beginner challenges are a nice change between the boring course assignments.
Just finished the basic swing graphical user interface chapter of the course, so I made it a bit fancy with a (very)simple swing gui.
Hope there are not to much mistakes or typo's in there (English is not my first language).

Please shoot at my code! 
I can always use a critical eye to get better in coding Java.

Thanks in advance!

EDIT:
I put the gamelogic as first method, for the people who are not interested in the swing gui code.

[PHP]import java.awt.*; /*Some imports*/
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.awt.event.ItemEvent;
import java.awt.event.ItemListener;
import javax.swing.*;

public class Rps {
	private int pwins; /*Some empty instance variables*/
	private int cwins;
	private int tie;
	private int uinput;
	private boolean debug=false;
	private JButton rockB;
	private JButton paperB;
	private JButton scissorsB;
	private JCheckBox debugCB;
	private JFrame frame;
	private JPanel panel;
	private JPanel bPanel;
	private JLabel label;
	private JLabel scoreLabel;

	public Rps(){ /*constructor(not very necessary here), calling the graphical user interface*/
		gui();
		}
	/*actual game logic*/
	public void game(){
		String winner="";
		int cinput = (int) (Math.random()*3); /*random number (0, 1 or 2 as Rock, paper, scissors)*/
		if(debug==true){ /* To check if the gui output is what it should be */
			System.out.println("Computer guesses: "+cinput);
			}
		String cHand=hand(cinput); /* sending the random number to the hand method to convert it to readable string (rock, paper or scissors) */
		String pHand=hand(getUinput()); /* Same, only now for user input */
	/* Look if its a tie */
		if(getUinput()==cinput){
			setTie(1);
			winner="Tie";
	/* look if the player wins */
		}else if((getUinput()==0 && cinput==2) || (getUinput()==1 && cinput==0)||(getUinput()==2 && cinput==1) ){
			setPwins(1);
			winner="Player!";
	/* look if computer wins */
		}else if((getUinput()==2 && cinput==0) || (getUinput()==0 && cinput==1)||(getUinput()==1 && cinput==2) ){
			setCwins(1);
			winner="Computer";
			}
	/* Set the font bigger */
		Font bigFont=new Font("serif", Font.BOLD, 16);
		label.setFont(bigFont);
	/* show the outcome */
		label.setText("Computer: "+cHand+"  You: "+pHand+"  Winner: "+winner);
		}
	/* convert numbers 0, 1 and 3 to readable string outputs for the gui */
	public String hand(int hand){
		String x="";
		if(hand==0){
			x="Rock";
		}else if(hand==1){
			x= "Paper";
		}else if(hand==2){
			x="Scissors";
		}else{
			x="Error";}
		return x;
		}
	/* update the score on the gui */
	public void showScore(){
		scoreLabel.setText("Score:  Computer: "+getCwins()+"   Tie: "+getTie()+"   Player: "+getPwins());	
		}
	/* set up the swing gui */
	public void gui(){
		 frame=new JFrame();
		 panel=new JPanel();
		 bPanel=new JPanel();
		 label=new JLabel();
		 scoreLabel=new JLabel();

		 rockB=new JButton("Rock");
		 paperB=new JButton("Paper");
		 scissorsB=new JButton("Sciccors");
		 debugCB=new JCheckBox("Debug off");

		 BorderLayout b=new BorderLayout();
		 panel.setLayout(b);
		 panel.add(b.NORTH, scoreLabel);
		 panel.add(b.CENTER, label);

		 bPanel.add(b.WEST, rockB); /* locate the "rock" button on the panel */
		 /* add an action listener to the button, that reacts when button is clicked */
		 rockB.addActionListener(new RockListener());
		 bPanel.add(b.CENTER, paperB);
		 paperB.addActionListener(new PaperListener());
		 bPanel.add(b.EAST, scissorsB);
		 scissorsB.addActionListener(new ScissorsListener());
		 bPanel.add(b.SOUTH, debugCB);
		 debugCB.addItemListener(new DebugListener());

		 frame.getContentPane().add(b.CENTER, panel);
		 frame.getContentPane().add(b.SOUTH, bPanel);
		 frame.setSize(400,300);
		 frame.setVisible(true);
		 frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);

		 label.setText("Take your guess by clicking one of the buttons below");
		 scoreLabel.setText("Score:  Computer: 0   Tie:0   Player:0");	
		 }
	/* Actionlistener inner classes, to set what happens when a button is clicked */
	public class RockListener implements ActionListener{
		public void actionPerformed(ActionEvent event){
			setUinput(0);
			if(debug==true){
				System.out.println("You input: "+getUinput());	
				}
			game();	
			}	
		}
	public class PaperListener implements ActionListener{
		public void actionPerformed(ActionEvent event){
			setUinput(1);
			if(debug==true){
				System.out.println("Your input: "+getUinput());		
				}
			game();	
			}	
		}
	public class ScissorsListener implements ActionListener{
		public void actionPerformed(ActionEvent event){
			setUinput(2);
			if(debug==true){
				System.out.println("Your input: "+getUinput());	
				}
			game();	
			}	
		}
	public class DebugListener implements ItemListener{
		public void itemStateChanged(ItemEvent ev){
			if (getDebug()==true){
				setDebug(false);
				debugCB.setText("Debug off");
			}else{
				setDebug(true);
				debugCB.setText("Debug on");
				}	
			}	
		}
	/* getters and setters */
	public int getCwins() {
		return cwins;	
		}
	public void setCwins(int cwins) {
		cwins=cwins+getCwins();
		this.cwins = cwins;
		showScore();	
		}
	public int getPwins() {
		return pwins;	
		}
	public void setPwins(int pwins) {
		pwins=pwins+getPwins();
		this.pwins = pwins;
		showScore();	
		}
	public int getTie() {
		return tie;	
		}
	public void setTie(int tie) {
		tie=tie+getTie();
		this.tie = tie;
		showScore();	
		}
	public int getUinput() {
		return uinput;	
		}
	public void setUinput(int uinput) {
		if (debug == true){
			System.out.println("Userinput="+uinput);	
			}
		if (uinput <= 2 & uinput >= 0){
			this.uinput = uinput;			
			}
		else{
			System.out.println("Error in the userinput"+uinput);	
			}	
		}
	public void setDebug(boolean debug){
		this.debug=debug;	
		}
	public boolean getDebug(){
		return debug;	
		}
	/* main methode that calls the constructor */
	public static void main(String[] args) {
		Rps rps = new Rps();
		}	
	}

[/PHP]

EDIT:
Must have pressed ctrl+v twice when posting my code...
Corrected the double code in the code block...
Sorry...

---

### Post by soltanis on 2009-05-05
Holy cow, between the hand-drawn ASCII art and the Java GUIs, my poor little CL implementation looks downright meager.

---

### Post by cobolt01 on 2009-05-06
> **baizon said:**
> Why double? There is the Java random Integer generator ;)
```

Random randGen = new Random();
int ret = randGen.nextInt(3)+1; //to set the limit to 3.

```

Thank you. Haha, I did need sleep. I normally use 0.333 to make it slightly better, but I didn't know about the nextInt() method. Thanks!

---

### Post by jinksys on 2009-05-08
No error checking, but it works.

```

#import <Foundation/Foundation.h>

@interface Pawn : NSObject
{
	int type;
}
-(id)initWithType:(int)t;

@property (readwrite) int type;
@end

@implementation Pawn
@synthesize type;

-(id)initWithType:(int)t
{
	if([super init])
	{
		self.type = t;
		return self;
	}
	
	return nil;
}
@end 

void main()
{
int player, cpu;
NSAutoreleasePool *pool = [[NSAutoreleasePool alloc] init];

//Rock = 1, Paper = 3, Scissors = 2
Pawn *rock = [[Pawn alloc] initWithType:1];
Pawn *paper = [[Pawn alloc] initWithType:3];
Pawn *scissors = [[Pawn alloc] initWithType:2];

NSArray *pawns = [NSArray arrayWithObjects: paper, rock, scissors, paper, rock, nil];

printf("Choose: Rock (1) Scissors (2) Paper (3) \n");
scanf("%d", &player);

srand(time(NULL));
cpu = rand () % 3 + 1;

if(player == 1)
	printf("You chose Rock.\n");
if(player == 2)
	printf("You chose Scissors.\n");
if(player == 3)
	printf("You chose Paper.\n");
if(cpu == 1)
	printf("CPU chose Rock.\n");
if(cpu == 2)
	printf("CPU chose Scissors.\n");
if(cpu == 3)
	printf("CPU chose Paper.\n");

if([[pawns objectAtIndex:player+1] type] == cpu)
	printf("YOU WIN\n\n");

if([[pawns objectAtIndex:player-1] type] == cpu)
	printf("YOU LOSE\n\n");

if(player==cpu)
	printf("TIE\n\n");

[rock release];
[paper release];
[scissors release];
[pool release];
}

```

---

### Post by jinksys on 2009-05-09
Rewritten in pure C.

```

#include <stdio.h>
void main()
{
int player, cpu, pawn[]={3,1,2,3,1};

printf("Choose: Rock (1) Scissors (2) Paper (3) \n");
scanf("%d", &player);

srand(time(NULL));
cpu = rand () % 3 + 1;

if(cpu == 1)
        printf("CPU chose Rock.\n");
if(cpu == 2)
        printf("CPU chose Scissors.\n");
if(cpu == 3)
        printf("CPU chose Paper.\n");

if(pawn[player+1] == cpu)
        printf("YOU WIN\n\n");

if(pawn[player-1] == cpu)
        printf("YOU LOSE\n\n");

if(player==cpu)
        printf("TIE\n\n");
}

```

---

### Post by Le-Froid on 2009-05-10
Alright, I'm gonna come up with a winner tomorrow. I didn't have any time before and I'm going over everything now. There's some pretty cool apps here, its gonna be a tough one!

---

### Post by ZuLuuuuuu on 2009-05-10
Updated my program to add comments for easy reading.

---

### Post by Le-Froid on 2009-05-10
Alright, there were so many interesting entrys and it was really hard to choose from, but I finally picked a winner!

And congratulations to [SIZE="5"]**ZuLuuuuuu**[/SIZE]! :)

Your tcl program was interesting and had good comments so it was easy for me to pick up on what the program was doing.
I have never seen any tcl programs before but I was able to understand what was going on.
The hand signs and different responses were really cool features and made your program fun to use. :)

Now, ZuLuuuuuu, you get the honor to create the next programming challenge! 

When you think of something create a thread titled "Beginner programming challenge #4" and let the entries roll in

Thanks for your submissions everyone this was a real close one

---

### Post by Bodsda on 2009-05-11
Congratulations Zuluuuuuu! 

I look forward to your challenge :)

Bodsda

---

### Post by ZuLuuuuuu on 2009-05-11
Yay! I WON! PWNAGE! :D :D

Thanks for this honor. I'm gonna post the next challenge in 2 or 3 days.

---

### Post by exutable on 2009-08-23
Kind of just posting for fun but also because I have a question, is my method of handling invalid input bad because of it's recursive nature?

Also is everything formatted correctly and written somewhat efficient?

```
#! /usr/bin/python3

import os, random, time

choices = ["Rock", "Paper", "Scissors"]

def clear():
	os.system('clear')

def menu():
	print("Please choose what you want to use:")
	print("1. Rock")
	print("2. Paper")
	print("3. Scissors")
	
	try:
		humanchoice = int(input("? "))
		humanchoice = choices[humanchoice-1]
	except:
		main()
	
	return humanchoice

def compcalc():
	return random.choice(choices)
	
def main():
	while True:
		clear()
		humanchoice = menu()
		compchoice = compcalc()
		
		if((humanchoice == "Rock" and compchoice == "Scissors") or (humanchoice == "Paper" and compchoice == "Rock") or (humanchoice == "Scissors" and compchoice == "Paper")):
			winningstring = "You won! {0} beats {1} everytime"
			print(winningstring.format(humanchoice, compchoice))
		elif((compchoice == "Rock" and humanchoice == "Scissors") or (compchoice == "Paper" and humanchoice == "Rock") or (compchoice == "Scissors" and humanchoice == "Paper")):
			winningstring = "Computer won! {0} beats {1} everytime"
			print(winningstring.format(compchoice, humanchoice))
		else:
			winningstring = "Tie between {0} and {1}"
			print(winningstring.format(compchoice, humanchoice))
		
		time.sleep(3)
			
main()


```

---

