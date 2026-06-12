---
title: "Beginner programming challange #8"
date: 2010-01-20
forum: Programming Talk
---

### Post by Bodsda on 2010-01-20
_[SIZE=5][COLOR=Red]Beginner Programming Challenge #8[/COLOR][/SIZE]_

Welcome to the 8th beginner programming challenge. First, please let me apologise for the un-judged [challenge 7]("http://ubuntuforums.org/showthread.php?t=1240305"). Unfortunately, due to time constraints, the OP of the thread was unable to judge it and the challenges therefore did not progress. However, I am now resuming them with this challenge. 

First, please allow me to make a special announcement. As you may be aware, these challenges are sponsored by the [Ubuntu Beginners Team Development Focus Group]("https://wiki.ubuntu.com/BeginnersTeam/FocusGroups/Development"). This focus group has now created a [projects page]("https://wiki.ubuntu.com/BeginnersTeam/FocusGroups/Development/Projects") where you can see what we are working on. You can also request for tutoring on programming topics related to these projects by contacting the programmer responsible for it. [The Ubuntu Beginners Team]("https://wiki.ubuntu.com/BeginnersTeam/") is always looking for new members to join and the development focus group is assimilating also. 

Now, lets get onto the challenge!

*_**Task:**_*

Create a guess the number game as in [Challenge 1]("http://ubuntuforums.org/showthread.php?t=1097136"). However, this version must be able to have Human vs Human, AI vs Human and AI vs AI. 

Human vs Human should take user input for the number, then Human input for the guesses. 

Human vs AI should ask the user for a number and then the computer should guess what the number is. 

AI vs AI should randomly generate a number and then have the computer guess that number.

_***Extra Cookies:***_

Extra cookie points will be awarded for:

[LIST]
[*]The use of an input file for funny too low, too high messages
[*]The ability to specify Human vs Human, Human vs AI and AI vs AI via a command line switch
[*]The ability to change the range of the random number via a command line switch
[*]The ability to display an ascii representation of a cookie when answer is gained in less then 3 guesses (negative cookie points will occur if this ascii representation does not closely resemble a cookie)
[/LIST]
_***Disqualified Entries:***_

Any overly obfuscated code will be immediately disqualified without account for programmers skill. Please remember that these challenges are for beginners and therefore the code should be easily readable and well commented.

Any non-beginner entries will not be judged. Please use common sense when posting code examples. Please do not give beginners a copy paste solution before they have had a chance to try this for themselves.

_***Assistance:***_

If you require any help with this challenge please do not hesitate to come and chat to the development focus group. We have a channel on irc.freenode.net #ubuntu-beginners-dev

_***Last but not least:***_

[SIZE=2]**HAVE FUN!**[/SIZE]

Bodsda

---

### Post by Sinkingships7 on 2010-01-23
This, children, is why friends don't let friends use C++. :p
Hopefully someone does this in Python to demonstrate the difference.

Does everything except reading messages from a file. I'll probably implement that later, when I'm done with my composition essay.

EDIT: Pasting here is doing weird things to the formatting. Guess you're just going to have to believe that the code WAS in perfect condition. I don't generally use eight space tabs...

main.cpp
```

// Standard Headers
#include <iostream>
#include <limits>
#include <cstdio>

// Custom Headers
#include "player.h"


// Global Variables
enum e_GameMode {HH, HA, AA, NUL} GAME_MODE = NUL; 
bool customNumbers	= false;
unsigned int LOW	= 1;
unsigned int HIGH	= 100;


// Function Declarations
void processCommandLineSwitches(int, char**);
void printSwitchInstructions();
void askForGameMode();
void printCookie();


// ************
// *** MAIN *** 
// ************

int main(int argc, char** argv){
    if (argc > 1) processCommandLineSwitches(argc, argv);

    Player playerOne;
    Player playerTwo;
    unsigned int numberToGuess		= 0;
    unsigned int guess			= 0;
    unsigned int numberOfGuesses	= 0;

    // Create players based on the GAME_MODE.
    while (true){
        if (GAME_MODE == HH){
            playerOne = Player(HUMAN);
            playerTwo = Player(HUMAN);
            break;
        }else if (GAME_MODE == HA){
            playerOne = Player(HUMAN);
            playerTwo = Player(AI);
            break;
        }else if (GAME_MODE == AA){
            playerOne = Player(AI);
            playerTwo = Player(AI);
            break;
        }else{
            askForGameMode();
        }
    }

    // Get the number to be guessed.
    std::cout << "Enter the number for the other player to guess: ";
    numberToGuess = playerOne.getNumber(LOW, HIGH);

    // Eighty newlines to "clear" the console.
    for (int i = 1; i <= 80; i++) std::cout << '\n'; 

    // Game Loop
    do{ 
        numberOfGuesses++;

        std::cout << "Take a guess: ";
        guess = playerTwo.getNumber(LOW, HIGH);

        if (guess == numberToGuess) 
            break;

        playerOne.giveHint(guess, numberToGuess);
    }while (true);

    std::cout << \
        "\nWIN!\n" << \
        "It took " << numberOfGuesses << " guesses to complete this game.\n\n";

    if (numberOfGuesses <= 3)
        printCookie();

    system("pause");
    return 0;
}



// *****************
// *** FUNCTIONS *** 
// *****************

void processCommandLineSwitches(int Ac, char** Av){

    // Switch structure to set game variables based on switches.
    switch (Ac){
        case 1:
            break;
        case 2:
            if (strcmp(Av[1], "-hh") == 0) GAME_MODE = HH;
            if (strcmp(Av[1], "-ha") == 0) GAME_MODE = HA;
            if (strcmp(Av[1], "-aa") == 0) GAME_MODE = AA;
            if (strcmp(Av[1], "-c") == 0) customNumbers = true;
            break;
        case 3:
            for (int n = 1; n < Ac; n++){
                if (strcmp(Av[n], "-hh") == 0) GAME_MODE = HH;
                if (strcmp(Av[n], "-ha") == 0) GAME_MODE = HA;
                if (strcmp(Av[n], "-aa") == 0) GAME_MODE = AA;
            }

            if (strcmp(Av[1], "-c") == 0 || strcmp(Av[2], "-c") == 0)
                customNumbers = true;
            
            break;
        default:
            printSwitchInstructions();
            exit(-1);
    }

    // Error-safe; gets valid input for the desired high and low numbers.
    while (true){
        if (customNumbers == true){
            try{
                std::cout << " Lowest Number: "; std::cin >> LOW;
                std::cout << "Highest Number: "; std::cin >> HIGH;
                std::cout << "\n\n";

                if (std::cin.good() == false || LOW < 1 || HIGH < 1 || LOW > HIGH){
                    std::cin.clear();
                    std::cin.ignore(std::numeric_limits<std::streamsize>::max(), '\n');
                    throw -1;
                }

                break;
            }catch (int E){
                std::cerr << "Invalid Input. Choose positive integers only." << \
                    "Low must be lower than High.\n\n";
                continue;
            }
        }
        break;
    }
}


void printSwitchInstructions(){
    std::cout << "\n\n" << \
        "		*** SWITCH INSTRUCTIONS ***\n" << \
        "GAME MODE SWITCH\n"		<< \
        "	-hh = Human vs Human\n" << \
        "	-ha = Human vs AI\n"	<< \
        "	-aa = AI vs AI\n\n"	<< \
        "CUSTOM NUMBERS SWITCH\n"	<< \
        "	-c\n\n\n";
}


void askForGameMode(){
    short choice;

    // Get the desired choice from the user.
    while (true){
        try{
            std::cout << \
                "[1] Human vs Human\n" << \
                "[2] Human vs AI\n" << \
                "[3] AI vs AI\n\n>> ";
            std::cin >> choice;

            if (std::cin.good() == false || choice < 1 || choice > 3){
                std::cin.clear();
                std::cin.ignore(std::numeric_limits<std::streamsize>::max(), '\n');
                throw -1;
            }

            break;
        }catch (int E){
            std::cerr << "Invalid choice. Try again.\n\n";
            continue;
        }
        break;
    }

    // Set GAME_MODE based on the users' choice.
    switch (choice){
        case 1:
            GAME_MODE = HH;
            break;
        case 2:
            GAME_MODE = HA;
            break;
        case 3:
            GAME_MODE = AA;
            break;
    }
}


// An English cookie for the winner!
// Blatantly stolen from this site: http://www.cgarbs.de/ascii-art-misc.en.html
void printCookie(){
    std::cout << \
        " Here's an English COOKIE!!!\n" << \
        "	 .-.-.-.-.-.-.-.-.-.-.-.-.-. \n" << \
        "	(   .   .   .   .   .   .   )\n" << \
        "	(                           )\n" << \
        "	( .   .   .   .   .   .   . )\n" << \
        "	(                           )\n" << \
        "	(   .   .   .   .   .   .   )\n" << \
        "	(                           )\n" << \
        "	( .   .   .   .   .   .   . )\n" << \
        "	(                           )\n" << \
        "	 '-'-'-'-'-'-'-'-'-'-'-'-'-' \n\n\n";
}

```

player.h
```

#ifndef PLAYER_H
#define PLAYER_H



// This is a simple type to help clarify the type of Player.
enum e_IntelligenceLevel	{HUMAN, AI}; 

// Default values; these are used if the default constructor is called.
const e_IntelligenceLevel	DEFAULT_INTELLIGENCE = HUMAN;
const unsigned int		DEFAULT_LOW	     = 1;
const unsigned int		DEFAULT_HIGH         = 100;



class Player{
/* This class represents a Player in the game. 
 * The Player object can be either a HUMAN or AI. The functions of the 
 * methods change depending on what type of Player is instantiated. 
 */
public:
	// CONSTRUCTORS
	Player(); 
	Player(e_IntelligenceLevel);

	// METHODS
	unsigned int getNumber(unsigned int, unsigned int);
	void giveHint(unsigned int, unsigned int);

	// DATA MEMBERS
	e_IntelligenceLevel	intelligence;

private:
	// DATA MEMBERS
	unsigned int lowestNumber, highestNumber;
};



#endif

```

player.cpp
```

#include "player.h"

// These macros are in place to make the sleep() function more or less
// universal -- independent of the operating system.
#ifdef _WIN32
    #include <windows.h>
    inline void sleep(unsigned int milliseconds){
        Sleep(milliseconds);
    }
	#undef max
#else
    #include <unistd.h>
    inline void sleep(unsigned int milliseconds){
        usleep(milliseconds * 1000); // Multiply by 1000 because 1000 milliseconds == 1 second.
    }
#endif

#include <iostream>
#include <limits>
#include <ctime>



// Small helper function to clean std::cin.
void cleanInputStream(){
	std::cin.clear();
	std::cin.ignore(std::numeric_limits<std::streamsize>::max(), '\n');
}



// ********************
// *** CONSTRUCTORS ***
// ********************


Player::Player(){
	intelligence = DEFAULT_INTELLIGENCE;
}


Player::Player(e_IntelligenceLevel N){
	intelligence = N;
}



// ***********************
// *** Player::METHODS ***
// ***********************


/* NAME: Player::getNumber
 * ARGS: None
 * DESCRIPTION:
 *	Gets an unsigned integer guess from the calling object.
 *
 *	IF calling object is AI:
 *		The number is generated randomly.
 *
 *	IF calling object is HUMAN:
 *		std::cin stream is opened for input. 
 *
 *	This method is error-checked and won't return without valid input.
 */
unsigned int Player::getNumber(unsigned int lowestNumber, unsigned int highestNumber){

	// Holds the guess to be returned to the caller.
	unsigned int guess; 

	switch (intelligence){
		case AI: 
			// Very simple: seed the system time and generate a random number.
			srand((unsigned int)time(0));
			guess = (rand() % highestNumber) + lowestNumber;

			// Show the number so it looks like it's being typed and pause the 
			// program to make the effect of guessing seem more realistic.
			std::cout << guess << std::endl; 
			sleep(2000); 
			break;

		case HUMAN: 
			// Here, we throw ourselves into an "infinite" loop, meant to keep 
			// trying to get valid input. Once valid input is received, the 
			// loop is broken and the input is returned.
			while (true){
				try{
					std::cin >> guess;

					if (std::cin.good() == false || guess < lowestNumber || guess > highestNumber){
						cleanInputStream();
						throw -1; 
					}else{
						break; 
					}
				}catch (int E){
					std::cerr << "ERR: Invalid input. Try again. [" \
						<< lowestNumber << " - " << highestNumber << "]\n";

					continue; 
				}
				break; 
			}
			break; 
	}

	return guess;
}	


void Player::giveHint(unsigned int guess, unsigned int toGuess){
	if (guess < toGuess){
		std::cout << "HIGHER!\n\n";
	}else{
		std::cout << "LOWER!\n\n";
	}
}

```

---

### Post by Bodsda on 2010-01-27
Im aware of at least two other people currently coding for this challenge. I aim to judge this on the 31st, or the 7th of February depending on entries.

Get coding,

Bodsda

---

### Post by Bodsda on 2010-02-14
Ok, disappointing turn out to this challenge, but the winner is

........
........
........

_**Sinkingships7**_

Congratulations. 

I hope to see the next challenge up soon :)

Happy coding.
Bodsda

---

### Post by tgm4883 on 2011-07-11
Better late than never. This doesn't follow the instructions exactly, and it could be cleaned up a bit.

Differences listed here

> Create a guess the number game as in Challenge 1. However, this version must be able to have Human vs Human, AI vs Human and AI vs AI. 


Yep it does this

> 
Human vs Human should take user input for the number, then Human input for the guesses. 


Here I deviate a bit. Instead of 1 user selecting the number and another user guessing, the computer still pulls a random number and then both users take turns guessing.

> 
Human vs AI should ask the user for a number and then the computer should guess what the number is. 


This deviates as well. Same as Human vs Human. (Human directly against AI)

> 
AI vs AI should randomly generate a number and then have the computer guess that number.

Deviates again, same as above. Computer generates random int, then AI vs AI. 

Here is the code, comments welcome.

```
#!/usr/bin/env python

import random
import sys

def runGame(MIN, MAX):
    ## Make ANSWER available to everything
    global ANSWER
    ANSWER = random.randint(MIN,MAX)

    P1, P1T = setupPlayer(1)
    P2, P2T = setupPlayer(2)

    ## Track player guesses in a dict
    GUESSES={
    "1":0,
    "2":0
    }

    ## Set initial player turn
    TURN="1"
    NAME=P1
    TYPE=P1T

    ## SET AI High and low guesses
    P1H=MAX
    P1L=MIN
    P2H=MAX
    P2L=MIN

    ## Run game
    GUESSEDCORRECTLY=False
    while GUESSEDCORRECTLY == False:
      if TYPE == "Human":
        GUESS = raw_input(NAME+" please pick a number between "+str(MIN)+" and "+str(MAX)+": ")
      elif TYPE == "AI":
        if TURN=="1":
          GUESS = random.randint(P1L,P1H)
        elif TURN=="2":
          GUESS = random.randint(P2L,P2H)
      GUESSES[TURN]=GUESSES[TURN]+1
      print NAME+" picked "+str(GUESS)
      result=checkGuess(GUESS)
      if result == "INVALID":
        print "Invalid guess entered. Skipping turn"
      elif result == "HIGHER":
        if TYPE == "AI":
          if TURN == "1":
            P1L=GUESS+1
          else:
            P2L=GUESS+1
        else:
          print "You guessed too low"
      elif result == "LOWER":
        if TYPE == "AI":
          if TURN == "1":
            P1H=GUESS-1
          else:
            P2H=GUESS-1
        else:
          print "You guessed too high"
      elif result == "CORRECT":
        GUESSEDCORRECTLY = True
        print NAME+" guessed the correct answer ("+str(ANSWER)+") in "+str(GUESSES[TURN])+" guesses!"
      elif result == "ERROR":
        print "An error occured"
        sys.exit(1)
      if TURN=="1":
        TURN="2"
        NAME=P2
        TYPE=P2T
      else:
        TURN="1"
        NAME=P1
        TYPE=P1T

def checkGuess(GUESS):
  ## Check guess is valid
  try:
    FORMATTEDGUESS = int(GUESS)
    if FORMATTEDGUESS < MIN or FORMATTEDGUESS > MAX:
      return "INVALID"
    elif FORMATTEDGUESS < ANSWER:
      return "HIGHER"
    elif FORMATTEDGUESS > ANSWER:
      return "LOWER"
    elif FORMATTEDGUESS == ANSWER:
      return "CORRECT"
  except:
    return "ERROR"

def setupPlayer(NUM):
  ## Set player type and name
  PType = ""
  PName = ""
  while PType == "":
    PType = raw_input("Is Player "+str(NUM)+" a Human or AI? ")
    if PType == "AI":
      PName = "AI-"+str(NUM)
    elif PType == "Human":
      pass
    else:
      PType = ""
  while PName == "":
    PName = raw_input("Enter a name for player "+str(NUM)+": ")
    if PName == "":
      print "Invalid name, try again"
  return PName, PType

## Set global variables and start up game
global MIN
MIN = 1
global MAX
MAX = 100
runGame(MIN, MAX)
```

---

### Post by CuracaoThe on 2011-07-16
Written in Ruby:
[PHP]
class AdvancedGuesser
  module Message
    class << self
      def welcome_message
        puts "+---------------------------------------+",
             "| Welcome to the Advanced Guesser game. |",
             "| List of possible gametypes:           |",
             "|   1. Human versus Human               |",
             "|   2. Human versus AI                  |",
             "|   3. AI versus AI                     |",
             "|   4. Exit                             |",
             "+---------------------------------------+"
      end
      
      def interrogator #=> &#1044;&#1086;&#1087;&#1088;&#1072;&#1096;&#1080;&#1074;&#1072;&#1102;&#1097;&#1080;&#1081;
        print "Please, choose your gametype: "
      end

      def human_vs_human_message
        puts  "You have chosen a Human vs. Human gametype.",
              "The rules are straightforward:",
              "  1. The first person enters a secret number;",
              "  2. The second person tries to guess this number."
      end

      def human_vs_ai_message
        puts "You have chosen a Human vs. AI gametype.",
             "The rules are straightforward: ",
             "  1. The first person enters a secret number;",
             "  2. The AI tries to guess this number."
      end

      def ai_vs_ai_message
        puts "You have chosen a AI vs. AI gametype.",
             "There are no rules for you: just enjoy",
             "performance! :-)"
      end

      def incorrect_input_message
        puts "Incorrect input. You have to enter a number from 1 to 3."
      end

      def secret_number_lower
        puts "The secret number is lower. Try again:"
      end

      def secret_number_higher
        puts "The secret number is higher. Try again:"
      end

      def secret_number_win(secret_number)
        puts "You win! Yes, it was #{secret_number}."
      end

      def first_player_enter
        puts "First player, enter your secret number:"
      end

      def second_player_guess
        puts "Second player, try to guess a secret number:"
      end

      def computer_thinking
        puts "Generating an answer..."
      end

      def computer_prediction(prediction)
        puts "The AI says #{prediction}\n\n"
      end

      def invalid_number
        puts "Invalid number! The number must be from 1 to 100.",
             "Try again:"
      end
    end
  end

  def initialize
    loop do
      Message.welcome_message
      Message.interrogator
      choose_gametype gets.to_i
    end
  end

  private

  def win?(secret_number, prediction)
    case prediction <=> secret_number
      when -1 then Message.secret_number_higher
      when  0 then Message.secret_number_win(secret_number); true
      when  1 then Message.secret_number_lower
    end
  end

  def valid_number?(number)
    if (1..100).member?(number)
      true
    else
      Message.invalid_number
    end
  end

  def human_input
    loop do
      number = gets.to_i
      break number if valid_number?(number)
    end
  end
  
  def choose_gametype(gametype)
    case gametype
      when 1 then play_human_vs_human
      when 2 then play_human_vs_ai
      when 3 then play_ai_vs_ai
      when 4 then exit
      else Message.incorrect_input_message
    end
  end

  def play_game(&block)
    loop do
      yield
    end
  end

  def random
    Random.new.rand(100) + 1
  end

  def play_human_vs_human
    Message.human_vs_human_message
    Message.first_player_enter
    secret_number = human_input
    Message.second_player_guess

    play_game do
      prediction = gets.to_i
      break if win?(secret_number, prediction)
    end
  end

  def play_human_vs_ai
    Message.human_vs_ai_message
    Message.first_player_enter
    secret_number = human_input

    play_game do
      Message.computer_thinking
      prediction = random
      sleep 2
      Message.computer_prediction(prediction)
      break if win?(secret_number, prediction)
    end
  end

  def play_ai_vs_ai
    Message.ai_vs_ai_message
    Message.first_player_enter
    secret_number = random
    Message.second_player_guess

    play_game do
      prediction = random
      sleep 2
      Message.computer_prediction(prediction)
      break if win?(secret_number, prediction)
    end
  end

end

game = AdvancedGuesser.new

[/PHP]

---

### Post by debd on 2012-08-20
I know its very late.
But I found this one funny and attempted it.
My program is written in C and doesn't follow the instructions.

It has only AI vs AI which is - computer decides a random no. , two AIs try to guess.
AI vs AI has two modes.
Intelli - one AI takes note of other AI's previous try - whether it was bigger or smaller and tries a number accordingly, like when two humans playing side by side 'd do.
Blind - AIs are not aware of each other's inputs.

Running it without any argument or with 0 as the argument runs it in Intelli mode.
Specifyig a non-zero arg runs it in Blind mode.
Successfully guessing within 5 turns fetches an ascii art on sceen :)

```
#include <stdio.h>
#include <stdlib.h>
#include <time.h>
#include <ctype.h>

#define SMALLER 0
#define BIGGER 1

void congo(void);

void congo(void)
{
  puts("   ______                        __");
  puts("  / ____/___  ____  ____ _____  / /");
  puts(" / /   / __ \\/ __ \\/ __ `/ __ \\/ / ");
  puts("/ /___/ /_/ / / / / /_/ / /_/ /_/  ");
  puts("\\____/\\____/_/ /_/\\__, /\\____(_)   ");
  puts("                 /____/            ");

}

int main(int argc, char *argv[])
{
  int ai1, ai2, rnd, tryai1=1, tryai2=1, ai1prev, ai2prev;
  int ai1flag, ai2flag, blind=0, ai1done=0, ai2done=0;
  
  if(argc == 2 && isdigit(*argv[1]))
  {
    blind = atoi(argv[1]);
  }

  if(blind) puts("\nBlind mode.\n");
  else puts("\nIntelli mode.\n");

  puts("We are in a guessing game!\nAIs try to guess the number!\n");
  /*printf("\nGuess what number!\n> ");
  scanf("%i", &ai);*/
  
  srand( time(NULL) );
  rnd = rand() % 100;
  
  ai1prev = ai1 = rand() % 100;
  printf("AI-1 guessed %i\n", ai1);

  ai2prev = ai2 = rand() % 100;
  printf("AI-2 guessed %i\n\n", ai2);

  if(ai1 < rnd)
    ai1flag = SMALLER;
  else
    ai1flag = BIGGER;
  
  if(ai2 < rnd)
    ai2flag = SMALLER;
  else
    ai2flag = BIGGER;

  do{
      ai1done = ai2done = 0;
      if(ai1 == rnd || ai2 == rnd)
      {
        if(ai1 == rnd && ai2 == rnd)
        {
          printf("Both AIs took %i tries.\nRight value is %i\n.", tryai1, rnd);
          if(tryai1 <=5)
            congo();
          else
            puts("Congo!!");
          exit(0);
        }

        if(ai1 == rnd)
        {
          puts("AI-1 won!");
          printf("AI-1 took %i tries!\nRight value is %i.\n", tryai1, rnd);
          if(tryai1 <= 5)
            congo();
          exit(0);
        }

        if(ai2 == rnd)
        {
          puts("AI-2 won!");
          printf("AI-2 took %i tries!\nRight value is %i.\n", tryai2, rnd);
          if(tryai2 <= 5)
             congo();
          exit(0);
        }
      }

      
      if(ai1 > rnd)
      {
        puts("AI-1 guessed bigger.");
        if(blind)
        {
          ai1 = ai1 - (rand() % 10);
        }
        else
        {
          ai1flag=BIGGER;
          ai1prev=ai1;
          
          if(ai1flag == ai2flag && ai1 > ai2prev)
              ai1 = ai2prev - ((ai1 - ai2prev)/2);
          
          else
            ai1 = ai1 - (rand() % 10);

        }
        printf("AI-1 guessing %i\n\n", ai1);
        tryai1++;
        ai1done=1;
      }
      

      if(!ai1done)
      {
      if(ai1 < rnd)
      {
        puts("AI-1 guessed smaller.");
        if(blind)
        {
          ai1 = ai1 + (rand() % 10);
        }

        else
        {
          ai1flag=SMALLER;
          ai1prev=ai1;

          if(ai1flag == ai2flag && ai1 < ai2prev)
              ai1 = ai2prev + ((ai2prev-ai1)/2);
          
          else
            ai1 = ai1 + (rand() % 10);

        }
        printf("AI-1 guessing %i\n\n", ai1);
        tryai1++;
      }
      }

      
      if(ai2 > rnd)
      {
        puts("AI-2 guessed bigger.");
        if(blind)
        {
        ai2 = ai2 - (rand() % 10);
        }

        else
        {
          ai2flag=BIGGER;
          ai2prev=ai2;
         
          if(ai1flag == ai2flag && ai2 > ai1prev)
              ai2 = ai1prev - ((ai2 - ai1prev)/2);
          
          else
            ai2 = ai2 - (rand() % 10);
        }
        printf("AI-2 guessing %i\n\n", ai2);
        tryai2++;
        ai2done=1;
      }

      if(!ai2done)
      {
      if(ai2 < rnd)
      {
        puts("AI-2 guessed smaller.");
        if(blind)
        {
          ai2 = ai2 + (rand() % 10);
        }

        else
        {
          ai2flag=SMALLER;
          ai2prev=ai2;
          
          if(ai1flag == ai2flag && ai2 < ai1prev)
              ai2 = ai1prev + ((ai1prev -ai2)/2);
          
          else
            ai2 = ai2 + (rand() % 10);
        }
          printf("AI-2 guessing %i\n\n", ai2);
        tryai2++;
      }
      }

    } while(1);

#undef SMALLER
#undef BIGGER

  return 0;

}
```

---

