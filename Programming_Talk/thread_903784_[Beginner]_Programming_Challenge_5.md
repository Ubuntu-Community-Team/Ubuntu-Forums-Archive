---
title: "[Beginner] Programming Challenge: 5"
date: 2008-08-28
forum: Programming Talk
---

### Post by LaRoza on 2008-08-28
After a bigger gap, we are resuming.

Here is the last challenge: [http://ubuntuforums.org/showthread.php?t=889710](http://ubuntuforums.org/showthread.php?t=889710)

From now on, there will be no final grading (actually, it has been like that before). Anyone can comment whenever they wish on submissions. This is for learning and getting/giving advice.

[size=+1]The Challenge:[/size]
We will focus on a small "game" and [Structured Programming]("http://en.wikipedia.org/wiki/Structured_programming").

In addition to the small task, you should pay careful attention to the code itself.

You will have to do the following:

[list]
[*] Write a program that will emulate a common guessing game.
[*] The game should randomly set a number which the user will have to guess and will get "higher" or "lower" hints as it goes. Only integers will be used for the target number.
[*] The target number should be 1 to 100 (although this "game" is harldy a game. Anybody will get it in 7-8 tries without even "guessing", by using logic)
[*] The game will end with a note of the win when the correct number is guessed.
[*] The program should tell the number of guesses it took to get it as well.
[/list]

In addition, these are also part of the challenge:

[list]
[*] The code should be well formatted.
[*] The code layout should be structured and logical. 
[*] The use of logical design is a big part of this, so keep a consistant format, and use logical variable and function names.
[/list]

[size=+1]Rules:[/size]
Do not copy code, but you can obviously read it :-)

Try to comment on other submissions if you are not a beginner. If you are not a beginner, don't post solutions for commenting, although you can show off skills as the thread progresses if you want to showcase something you are learning.

[size=+1]Hints:[/size]
[list]
[*] Most languages contain standard library functions (or even inbuilt) for getting random numbers.
[*] This is a good time to learn about the modulus operator if you haven't done so already ;)
[/list]


[size=+1]How it will be judged:[/size]
[list]
[*] It has to do what it is specified.
[*] It has to be structured.
[/list]

As before, try to follow the following:
[list]
[*] Clean code. Readable code is a must for being a programmer who wishes to possibly interact with others. Some languages can be more readable than others, so it will be judged on the effort of writing clean code, not which language is easier to read by design.
[*] Logical code. Be a programmer, not a code monkey :-)
[*] Commented code. If something is possibly unclear (like an obscure use of math), let the readers know. Do not over comment, and let the code speak for itself whenever you can. Have logical variable names and function names. (Excessive commenting is a minus factor)
[*] Working code. It has to work as it is posted. The codw will be read on the forum, so remember to use this guide to paste code if you don't know how: [http://ubuntuforums.org/showthread.php?t=606009](http://ubuntuforums.org/showthread.php?t=606009)
[/list]

---

### Post by Alasdair on 2008-08-28
I'm currently learning Haskell, so I'm pretty sure that makes me a valid beginner. To run it save the script and mark it executable, provided you have ghc and libghc6-regex-posix-dev it should work like any other script.

```
#!/usr/bin/env runhaskell
module Main where
import System.Random
import Text.Regex.Posix

main :: IO Int
main = getStdRandom (randomR (0,100)) >>=
       (\r -> guessGame r >> return r)

-- Get a number from the player, making sure it is between 1 and 100
getGuess :: IO Int
getGuess = do
  guessStr <- getLine
  if guessStr =~ "^([1-9][0-9]?|100)$"
     then return $ read guessStr
     else putStrLn "That's not a number between 1 and 100" >> 
          getGuess

checkNumber :: Int -> Int -> String
checkNumber guess n
    | guess > n = "Too high!"
    | guess < n = "Too low!"
    | otherwise = "Correct!"
  
guessGame :: Int -> IO ()
guessGame r = do
  putStrLn "Guess a number between 0 and 100"
  guess <- getGuess
  let result = checkNumber guess r
  if result == "Correct!"
     then putStrLn result
     else putStrLn result >> guessGame r
```

---

### Post by cpetercarter on 2008-08-28
[PHP]<?php
#we execute this bit the first time only
if(!isset($_POST['target']))
	{
	$target = (int)rand(0,100);
	echo "<p>OK, sucker, guess the number I am thinking of.</p>";
	the_form($target);
	}
#and this bit every other time
else
	{
	$target = $_POST['target'];
	$myguess = $_POST['myguess'];
	if (the_test($myguess) == false)
		{
		echo "<p>Listen Stupid - you have to enter a whole number between 0 and 100!</p>";
		the_form($target);
		}
	else
		{
		if ($myguess == $target)
			{
			echo "<p>Yes - my number was ".$target."</p>";
			}
		if ($myguess > $target)
			{
			echo "<p>".$myguess." is too high.</p>";
			the_form($target);
			}
		if ($myguess < $target)
			{
			echo "<p>".$myguess." is too low.</p>";
			the_form($target);
			}
		}
	}	

function the_form($target) {
	echo "<p>Go on - have a guess!</p>";	
	echo "<form action=\"game.php\" method=\"POST\">";
	echo "<input type=\"text\" name=\"myguess\" />";
	#we use a hidden input to pass the value of $target to the next iteration
	echo "<input type=\"hidden\" name=\"target\" value=\"".$target."\" />";
	echo "<input type=\"submit\" value=\"Guess!\" />";
        echo "</form>";
}
function the_test($input) {
	#test that the input is a whole number between 0 and 100
	if ((ereg("^[0-9]{1,3}$",$input)) && ($input >=0) && ($input <=100))
	{
	return true;
	}
	else 
	{
	return false;
	}
}
	

?>[/PHP]

---

### Post by Alasdair on 2008-08-28
I don't know PHP, but wouldn't the following the_test function work just as well as the one you have? The if statement seems superfluous, if the expression is true you return true, if the expression is false you return false, so why not return just the result of the expression? :)

[PHP]function the_test($input) {
    #test that the input is a whole number between 0 and 100
    return ((ereg("^[0-9]{1,3}$",$input)) && ($input >=0) && ($input <=100));
} [/PHP]

---

### Post by bruce89 on 2008-08-28
Vala:

```

public class Game
{
	int target;
	int guess;

	construct
	{
		target = Random.int_range (0, 100);
	}

	private void get_guess ()
	{
		do
		{
			stdout.printf ("Guess a number between 0 and 100 ");
			stdin.scanf ("%d", out guess);	
		} while (guess < 0 || guess > 100);
	}

	public void run ()
	{
		get_guess ();

		if (guess < target)
		{
			stdout.printf ("Too low\n");
			run ();
		}
		else if (guess > target)
		{
			stdout.printf ("Too high\n");
			run ();
		}
		else
			stdout.printf ("Correct\n");
	}

	static void main (string[] args)
	{
		var game = new Game ();
		game.run ();
	}
}

```

Use [FONT="Mono"]valac game.vala[/FONT] to compile. You may need to add [FONT="Mono"]using GLib;[/FONT] at the top, depending on which version of [FONT="Mono"]valac[/FONT] you are using.

---

### Post by jimi_hendrix on 2008-08-28
my answer

```

sudo apt-get install 4digits

4digits

```

joking...

heres mine...it includes the ability for you to adjust the range of the random integer it generates

[PHP]
//headers needed
#include <iostream>
#include "string"
#include <cstdlib>

using namespace std;

int random(int Range) //method for generating random ints
{
	int random_integer = (rand()%Range)+1; 
	
	return random_integer;
}

int main(int argc, char** argv)//main program
{
        //varialbes
	int target_num;
	int guess;
	int range;
	
	cout << "what is the highest possible number you would like the answer to be?" << endl;
	
	cin >> range;
	
        //generate random number
	target_num = random(range);
	
	while (1) //game loop
	{
	cout << "please enter a guess" << endl;
	
	cin >> guess;
	

        //output depending on answer
	if (guess > target_num)
	{
		cout << "guess is too high" << endl;
	}
	
	else if (guess < target_num)
	{
		cout << "guess too low" << endl;
	}
	
	else
	{
		bool answered = false;
		
		while (answered == false)
		{
			
			string answer;
			cout << "you got it! \n play again [y/n]" << endl;
			cin >> answer;
			
			if (answer == "y")
			{
				target_num = random(range);
				answered = true;
			}
			
			else if (answer == "n")
			{
				return 0;
			}
			
			else
			{
				cout << "invalid input";
			}
		}
		
	}
	
	}
	return 0;
}
[/PHP]

---

### Post by snova on 2008-08-28
This is C. It should therefore be very readable.

[php]

char*m[]={"small","big"};t,g;main(int i){i?srand(time(0))+(t=rand()
%100):1;printf("What is your guess? ");return scanf("%i",&g)+g-2==
t?puts("You win!")&0:(i-=printf("Too %s.\n",m[g>t]))&0||main(0);}

[/php]I think this breaks most of the rules, but it plays correctly. At least, it did before I noticed the rules were a little different from what I thought they were... I fixed it, but possibly not correctly. It *should* still work...

Expect several compilation warnings.

EDIT: It didn't work. It does now.

---

### Post by mosty friedman on 2008-08-28
one question..i dont get this..if the program should set a random integer for the user to guess then howcome the target integer should be 100...can someone explain what does that mean??

---

### Post by cardboardtoast on 2008-08-28
[quote=snova](snip!)
I think this breaks most of the rules(snip!)[/quote]

What exactly ARE the rules??? I read the "structured programming" link, but that left me confused...:(  Do we just make a number guessing program, or do we have to do it a special way?

mosty friedman asked my other question...

---

### Post by LaRoza on 2008-08-28
> **mosty friedman said:**
> one question..i dont get this..if the program should set a random integer for the user to guess then howcome the target integer should be 100...can someone explain what does that mean??

It should be 1 to 100.

> **cardboardtoast said:**
> What exactly ARE the rules??? I read the "structured programming" link, but that left me confused...:(  Do we just make a number guessing program, or do we have to do it a special way?

mosty friedman asked my other question...

Write a number guessing game. The number is 1 to 100. Write clean structured code.

---

### Post by ghostdog74 on 2008-08-28
just bored
```

awk 'BEGIN{srand();target=int(rand()*100)+1}
{
 printf "Number: ";getline NUM < "-"
 if ( NUM==target ) { print "Correct"; exit }
 print (NUM < target) ?  "Choose higher" :  "Choose lower"  
}END { print "Number of guess: " NR }' /var/log/messages

```

---

### Post by cardboardtoast on 2008-08-28
[QUOTE=LaRoza]Write a number guessing game. The number is 1 to 100. Write clean structured code. [/QUOTE]
ah, thanks!

Here's mine:
[PHP]#!/usr/bin/env python
import random
Tries = 0
myGuess = -1
Randomnum = random.choice(range(1,101))

while myGuess != Randomnum:
    try:
        myGuess = int(raw_input("Guess a number: "))
    except:
        print "Must be a NUMBER"
        ### not a number = wrong!
        myGuess = -1
    if myGuess < Randomnum and myGuess != -1:
        print "Too low"
    elif myGuess > Randomnum:
        print "Too high"
    Tries += 1
print "Got it in %i tries" %Tries
raw_input()[/PHP]

EDIT: changed to meet new criteria
EDIT: changed to be better (thanks LaRoza)

---

### Post by signifer123 on 2008-08-28
Good ol' bash. Just because nobody else had, honestly took 20 minutes longer than I expected. I really need to learn more about bash. Those comparisons caused me too much trouble.

```

#!/bin/bash


Won="0"
NumToGuess=$[ ( $RANDOM % 100  ) + 1 ] #Use built in random variable, with modulus operator and 100. Then add 1 for 1 - 100.

while [ $Won -gt "-1" ]; do
	echo "Number between 1 and 100:"
	read UserNum
	if [ "$UserNum" = "$NumToGuess" ]; then
		Won=$[$Won+1]
		echo "You Win! It took $Won tries."
		Won="-1"
	elif [ "$UserNum" -lt "$NumToGuess" ]; then
		Won=$[$Won+1]
		echo "Your number: $UserNum was too low"
	elif [ "$UserNum" -gt "$NumToGuess" ];then
		Won=$[$Won+1]
		echo "Your number: $UserNum was too high"
	fi
done

```

---

### Post by LaRoza on 2008-08-28
> **cardboardtoast said:**
> 
Here's mine:
[PHP]#!/usr/bin/env python
import random
Gotit = False
Randomnum = random.choice(range(1,101))

while Gotit == False:
    try:
        myGuess = int(raw_input("Guess a number: "))
    except:
        print "Must be a NUMBER"
        ### not a number = wrong!
        myGuess = -1
    ###Find out if it is right or wrong
    if myGuess == Randomnum:
        Gotit = True
        print "Got it!!"
    elif myGuess < Randomnum and myGuess != -1:
        print "Too low"
    elif myGuess > Randomnum:
        print "Too high"
raw_input()[/PHP]

Interesting code.

The program exits when the current number is entered, so the loop structure is redundant.

[PHP]#!/usr/bin/env python
import random
randomNum = random.choice(range(1,101))

while myGuess != randonNum:
    try:
        myGuess = int(raw_input("Guess a number: "))
    except:
        print "Must be a NUMBER"
        ### not a number = wrong!
        myGuess = -1
    if myGuess < Randomnum and myGuess != -1:
        print "Too low"
    elif myGuess > Randomnum:
        print "Too high"
print "Got it!"
raw_input()[/PHP]

---

### Post by LaRoza on 2008-08-28
I forgot a part of the criteria, sorry. The program should also give the number of guesses it took at the end.

---

### Post by gfa on 2008-08-29
Hi!!

I'm starting with Python, so here is mine:

[PHP]#!/usr/bin/env python

#
# Programming Challenge #5 (game)
#

import random

if __name__ == "__main__":
    #Generate a random number between 1 and 100
    the_number = random.randint(1,100)
    #Our initial values
    guess = -1
    tries = 0
    
    print " ** Welcome to: \"Find the number\" game **"
    print "    http://ubuntuforums.org/showthread.php?t=903784"
    print ""
    
    #Do a cycle until the number is guessed
    while the_number != guess:
        try:
            #Read the input from user (only a integer is accepted)
            guess = int(raw_input("Guess the number: "))
        except:
            print "Please introduce an integer!"
            continue
        
        #Determinate if the number is > or <
        if guess > the_number:
            print "Less!!!"
        elif guess < the_number:
            print "More!!!"
            
        #Increase attempt count
        tries += 1
    
    print "-----------------------------------------------------------"
    print 
    print "  Congratulations!! you've found the correct number:", the_number
    print
    print 'You needed',tries, tries==1 and 'try' or 'tries'
    #Exit succesfully[/PHP]

I know someone has posted in the same language, but as I'm learning, I **would like to hear your suggestions**...

PS. another better way to insert extra line breaks??

Thanks!
gFa

---

### Post by cpetercarter on 2008-08-29
OK - I forgot the bit about recording the number of tries. Please can I have another go?

[PHP]<?php
#we execute this bit the first time only
if(!isset($_POST['target']))
	{
	$target = (int)rand(0,100);
	echo "<p>OK, sucker, guess the number I am thinking of.</p>";
	the_form($target,0);
	}
#and this bit every other time
else
	{
	$target = $_POST['target'];
	$myguess = $_POST['myguess'];
	$tries = $_POST['tries']+1;
	if (the_test($myguess) == false)
		{
		echo "<p>Listen Stupid - you have to enter a whole number between 0 and 100!</p>";
		the_form($target,$tries);
		}
	else
		{
		if ($myguess == $target)
			{
			echo "<p>Yes - my number was ".$target."</p>";
			echo "<p>You took ".$tries." tries to get the right answer.</p>";
			}
		if ($myguess > $target)
			{
			echo "<p>".$myguess." is too high.</p>";
			the_form($target,$tries);
			}
		if ($myguess < $target)
			{
			echo "<p>".$myguess." is too low.</p>";
			the_form($target,$tries);
			}
		}
	}	

function the_form($target, $tries) {
	echo "<p>Go on - have a guess!</p>";	
	echo "<form action=\"game.php\" method=\"POST\">";
	echo "<input type=\"text\" name=\"myguess\" />";
	#we use a hidden input to pass the value of $target to the next iteration
	echo "<input type=\"hidden\" name=\"target\" value=\"".$target."\" />";
	# and another one to pass the number of tries
	echo "<input type=\"hidden\" name=\"tries\" value=\"".$tries."\" />";
	echo "<input type=\"submit\" value=\"Guess!\" />";
	echo "</form>";
}
function the_test($input) {
	#test that the input is a whole number between 0 and 100
	if ((ereg("^[0-9]{1,3}$",$input)) && ($input >=0) && ($input <=100))
	{
	return true;
	}
	else 
	{
	return false;
	}
}
	

?>[/PHP]

@Alasdair - you are right, of course. but I am a literal sort of chap, who likes to spell things out!

---

### Post by jinksys on 2008-08-29
I thought I'd take a break from my Physics homework and whip this up...

[PHP]
#Guessing Game by Steve Melvin <jinksys@gmail.com>
#Variables
msg_welcome:
	.asciz "I'm thinking of a number between 1 and 100.  Take a guess.\n"

msg_high:
	.asciz "Too high, guess again.\n"

msg_low:
	.asciz "Too low, guess again.\n"

msg_win:
	.asciz "You got it! Tries: %u\n"

format:
	.asciz "%u"

.bss
	.lcomm secret,4
	.lcomm guess, 4
	.lcomm tries, 4
.text
.globl _start
_start:
#RANDOM LOOP - Grab a number between 0 and 100
call rand  
cmp $100, %eax
jg _start
movl %eax, secret
#RANDOM LOOP END

pushl $msg_welcome
call printf
add $4, %esp

movl $0, tries

guessloop:
incl tries
pushl $guess
pushl $format
call scanf
add $8, %esp

movl guess, %eax
cmp secret, %eax
jg toobig
jl toosmall
je yougotit

toobig:
pushl $msg_high
call printf
add $8, %esp
jmp guessloop

toosmall:
pushl $msg_low
call printf
add $8, %esp
jmp guessloop

yougotit:
pushl tries
pushl $msg_win
call printf
add $8, %esp

movl $1, %eax
movl $0, %ebx
int $0x80

[/PHP]

---

### Post by Reiger on 2008-08-29
> **Alasdair said:**
> I'm currently learning Haskell, so I'm pretty sure that makes me a valid beginner. To run it save the script and mark it executable, provided you have ghc and libghc6-regex-posix-dev it should work like any other script.

```
#!/usr/bin/env runhaskell
module Main where
import System.Random
import Text.Regex.Posix

main :: IO Int
main = getStdRandom (randomR (0,100)) >>=
       (\r -> guessGame r >> return r)

-- Get a number from the player, making sure it is between 1 and 100
getGuess :: IO Int
getGuess = do
  guessStr <- getLine
  if guessStr =~ "^([1-9][0-9]?|100)$"
     then return $ read guessStr
     else putStrLn "That's not a number between 1 and 100" >> 
          getGuess

checkNumber :: Int -> Int -> String
checkNumber guess n
    | guess > n = "Too high!"
    | guess < n = "Too low!"
    | otherwise = "Correct!"
  
guessGame :: Int -> IO ()
guessGame r = do
  putStrLn "Guess a number between 0 and 100"
  guess <- getGuess
  let result = checkNumber guess r
  if result == "Correct!"
     then putStrLn result
     else putStrLn result >> guessGame r
```

Have you tested that code? In proper Haskell main **has to be** of type *main :: IO ()* !

Also your code never returns the number of guesses it took to get the random number correct. (It just returns the random number you 'feed' to your game.)

So you may want to rewrite those 2 functions:
```

main :: IO ()
main = getStdRandom (randomR (0,100)) >>=
       (\r -> putStrLn ("It took you " ++ (guessGame r 0) ++ " tries to guess it."))

guessGame :: Int -> Int -> IO Int
guessGame r k= do
  putStrLn "Guess a number between 0 and 100"
  guess <- getGuess
  let result = checkNumber guess r
  if result == "Correct!"
     then putStrLn result >> return k
     else putStrLn result >> guessGame r (k+1)
```

---

### Post by Sinkingships7 on 2008-08-29
First attempted it in Python for the nice, built-in functionality:
[php]
#!/usr/bin/env python
import random

random_number = random.randrange(1, 100)
guesses = 0

while True:
	guess = int(raw_input("Guess a number: "))
	guesses = guesses + 1
	if guess == random_number:
		print "YOU WIN!"
		break
	if guess < random_number:
		print "Higher..."
	if guess > random_number:
		print "Lower..."

print "Amount of guesses:", guesses
[/php]
Then hacked it in C, for the sake of practice with something that's not quite as built-in. LaRoza, feel free to remove my C entry if you see fit, as it's not my 'beginner' entry. I'm new to Python, but certainly not to C.
[php]
#include <stdio.h>
#include <stdlib.h>
#include <time.h>

int main(int argc, char* argv[]){
	srand(time(NULL));	// Seed from the system time (always different).
	int random_number = rand() % (100 - 1 + 1) + 1;
	int guess, guesses = 0;

	while (1){
		printf("Guess a number: ");
		scanf("%i", &guess); guesses++;

		if (guess == random_number){
			printf("YOU WIN!\n"); break;
		}
		if (guess < random_number){
			printf("Higher...\n"); continue;
		}
		printf("Lower...\n");
	}

	printf("Guesses: %i", guesses);

	return 0;
}
[/php]

---

### Post by artir on 2008-08-29
Here is my code, with score saving to a file :)
[PHP]# -*- coding: utf-8 -*-
def juego():
    import random
    number=random.randint(1,100)
    bien=0
    fail=0
    print number
    
    

    
    while bien==0:
        try:
         adiv=input("Number: ")
         if adiv < number:
            print "Higher"
            fail=fail+1
         elif adiv > number:
            print "Lower"
            fail=fail+1
         elif adiv == number:
            if fail == 0:
                print "One shot one Kill"
                bien=1
                nom=raw_input("Your name: ")
                archivo=open("test.txt","a")
                dirty=[]
                dirty2=[]
                fail=str(fail)
                dirty.append(nom)
                dirty2.append(fail)
                archivo.write("Name   Score"+"\n")
                archivo.write(dirty[0]+" "+dirty2[0])
                archivo.write("\n")
                archivo.close() 
            elif fail < 6:
               print "Correct!"
               print "You've tried ", fail, "times"
               bien=1
               nom=raw_input("Your name: ")
               archivo=open("test.txt","w")
             
               dirty=[]
               dirty2=[]
               fail=str(fail)
               dirty.append(nom)
               dirty2.append(fail)
               archivo.write("Name   Score"+"\n")
               archivo.write(dirty[0]+" "+dirty2[0])
               archivo.write("\n")
               archivo.close() 
            elif fail >= 10:
                print "Correct!"
                print "You've tried ", fail, "times"
                print "It was difficult, eh?"
                bien=1
                nom=raw_input("Your name: ")
                archivo=open("test.txt","w")
                dirty=[]
                dirty2=[]
                fail=str(fail)
                dirty.append(nom)
                dirty2.append(fail)
                archivo.write("Name   Score"+"\n")
                archivo.write(dirty[0]+" "+dirty2[0])
                archivo.write("\n")
                archivo.close() 
        except:
            print

def menu():
   elegir=0
   while elegir != 2: 
    print "1. Play"
    print "2. Exit"
    try:
     elegir=input("Choose: ")
    except:
        print
    if elegir ==1:
        
        juego()

menu()[/PHP]

---

### Post by Alasdair on 2008-08-29
> **Reiger said:**
> Have you tested that code? In proper Haskell main **has to be** of type *main :: IO ()* !

Also your code never returns the number of guesses it took to get the random number correct. (It just returns the random number you 'feed' to your game.)
...
Thanks - GHC didn't complain so I thought it was ok, I'll remember to make sure main has type IO () in future. The requirement to return the number of guesses was added after I wrote it so that's why it doesn't do that.

---

### Post by rjack on 2008-08-29
Lisp newbie here.
Not commented as it should be self-esplicative.
Structured because it's lisp :D
```
(defun ask-number (message)
  (format *query-io* "~a: " message)
  (force-output *query-io*)
  (parse-integer (read-line *query-io*)))

(do ((secret (+ 1 (random 100)))
     (tries 1 (incf tries))
     (guess (ask-number "Guess a number between 1 and 100")
            (if (< guess secret)
              (ask-number "Too low, try again")
              (ask-number "Too high, try again"))))
  ((= guess secret) (format *query-io* "You got it in ~d tries!" tries)))
```

---

### Post by jimi_hendrix on 2008-08-29
> **LaRoza said:**
> I forgot a part of the criteria, sorry. The program should also give the number of guesses it took at the end.

does it have to be fool proof too...like if they enter "a" instead of a number do we have to catch it?

---

### Post by happysmileman on 2008-08-29
> **Sinkingships7 said:**
> 
Then hacked it in C, for the sake of practice with something that's not quite as built-in. LaRoza, feel free to remove my C entry if you see fit, as it's not my 'beginner' entry. I'm new to Python, but certainly not to C.
[php]
...
	int random_number = rand() % int random_number = rand() % (100 - 1 + 1) + 1; + 1;
...
[/php]

Any particular reason you use (100 - 1 + 1), since that just comes out as 100 anyway?

Also I did this problem as a KDE app before but can't find the code, probably got deleted (Think I did it before installing Hardy), wasn't a great program but it was probably the first KDE app I wrote by myself (as in, not basing it off a tutorial)

---

### Post by cmay on 2008-08-29
here is my first game in c then. actually i only used c in a month so its kinda my first large application. i am very there will be bugs in it also :) i have had a long break from anything computer related for some time so i took the challenge as an opportunity to try write a little program.

[PHP]/*
 *      game.c
 *      
 *      Copyright 2008 cmay <ihaveno@emails>
 * 
 *      This program is free software; you can redistribute it and/or modify
 *      it under the terms of the GNU General Public License as published by
 *      the Free Software Foundation; either version 2 of the License, or
 *      (at your option) any later version.
 *      
 *      This program is distributed in the hope that it will be useful,
 *      but WITHOUT ANY WARRANTY; without even the implied warranty of
 *      MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
 *      GNU General Public License for more details.
 *      
 *      You should have received a copy of the GNU General Public License
 *      along with this program; if not, write to the Free Software
 *      Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston,
 *      MA 02110-1301, USA.
 */

#include <stdio.h>
#include <stdlib.h>
#include <time.h>

char *progname;
void play();
void license();
void help();
void print_menu();

/* main menu function*/
void select_menu()
{
	int in;
	 print_menu();
	while((in=getchar()))
	{      
			switch(in)
		   {
			case 'p':play();break;
			case 'h':help();break;
			case 'l':license();break;
			case 'q':abort();break;
		   } 
	}
	
}
    /* the game play*/
	void play()
    { 
    	 int count_guess=0;
    	 srand((unsigned)time(NULL));
         int correct=rand()%100;
/* okay honest i cant understand a word of the manual rand should be max 100 ? */
    	 int input;
    	puts("ok then !!! guess this :)");
		while(scanf("%d",&input)==1)
		{
		    count_guess++;
		      		 
		if(input < correct)
		   printf("higher\n[guesses used[%d]\n",count_guess);
		if(input > correct)
		   printf("lower\n[guesses used[%d]",count_guess);
		if(input == correct)
		   printf("you win \n[%d]guesses usesd\n",count_guess);
		   printf("press [q] to quit any key to continue\n");
		  }

	}
	  /* my help menu*/
		void help()
		{
			printf("%s helpmenu\n",progname);
			printf("minimal version of the high low game\n");
			printf("[q] quit program\n");
			printf("[h]this menu\n");
			printf("[p] play game\n");
			
		}
		/* my license*/
		void license()
		{
			char notice[]="a free GPLed version of high-low game\n"
			"author:cmay\n2008\nhave fun\n";
			printf("%s",notice);
		}
		/* my menu */
		void print_menu()
		{
			char text[]="[p]play gamel\n"
			            "[l]license\n"
			           "[q] quit\n";
			printf("%s",text);
		}
		           
int main(int argc, char** argv)
{
	
        while(1)
        {     
		select_menu();
	    }
	   
	exit(0);
}
[/PHP]

---

### Post by fifth on 2008-08-29
My quick attempt ...
```
#!/usr/bin/env python
from sys import argv
from random import randrange

class RandomGame:
        
    def newGame(self):
        self.number = randrange(1, 100, 1)
        self.guessCount = 0
        
        print "Guess a number between 1 and 100 ..."
        
        success = False
        while success == False:
            playerInput = raw_input("Please enter your guess [1-100]: ")
            playerInput = playerInput.strip()
            if not playerInput.isdigit():
                print "You did not enter a valid number, please try again"
            else:
                success = self.guess(int(playerInput))
        
    def guess(self, number):
        self.guessCount  += 1
        if number == self.number:
            print "CONGRATULATIONS, you got the number in %i guesses! " % self.guessCount
            return True
        else:
            if number >self.number:
                print "Sorry, thats not the number, try guessing lower"
                return False
            else:
                print "Sorry,thats not the number, try guessing higher"
                return False
    
game = RandomGame()
game.newGame()
```

---

### Post by Sinkingships7 on 2008-08-29
> **happysmileman said:**
> Any particular reason you use (100 - 1 + 1), since that just comes out as 100 anyway?

Only to stick to the formula. It's usually
```

rand() % (HIGH - LOW + 1) + LOW

```
If you're looking for a number between 1 and another number, inclusive, then yes, it could just be
```

rand() % HIGH + LOW   // just HIGH + 1

```
But that can only be the case if it's a number from 1 to HIGH. Of course, in all cases, you could just figure out the number in the parenthesis before hand and just plug it in manually, though I don't think that's generally practiced...

---

### Post by jimi_hendrix on 2008-08-29
> **cmay said:**
> h
[PHP] 
#include <stdio.h>
#include <stdlib.h>
#include <time.h>


    	 srand((unsigned)time(NULL));
         
[/PHP]

whats the time thing for...all online help for that code snippit is very bad

---

### Post by nvteighen on 2008-08-29
Ok, here's a MIT/GNU Scheme implementation. It's quite extensible, I think, thanks to the "signals" that determine the output. So, we achieve a complete separation between interface and output.

EDIT: Reviewed code. It was utterly broken. Now works.

```

;; UF PT Beginners Challenge 5: Guess a number.
;; Written in MIT/GNU Scheme. This may not work in other Scheme implementations.
;;
;; Copyright (c) 2008 Eugenio M. Vigo (aka "nvteighen")
;;
;; This program is free software: you can redistribute it and/or modify it 
;; under the terms of the GNU General Public License as published by the Free 
;; Software Foundation, either version 3 of the License, or (at your option) 
;; any later version.
;;
;; This program is distributed in the hope that it will be useful, but WITHOUT 
;; ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS
;; FOR A PARTICULAR PURPOSE. See the GNU General Public License for more 
;; details.
;;
;; You should have received a copy of the GNU General Public License along with 
;; this program. If not, see <http://www.gnu.org/licenses/>.

(load-option 'format)
 
(define make-signal cons)
(define sig-name car)
(define sig-cont cdr)

(define (output signal)
  (display
   (cond ((eq? (sig-name signal) 'win) 
          (format #f "Win in ~S tries!" (sig-cont signal)))
         ((eq? (sig-name signal) 'low)
          "Too low!")
         ((eq? (sig-name signal) 'high)
          "Too high!")
         ((eq? (sig-name signal) 'ask)
          "Type a number between 1-100:")
         ((eq? (sig-name signal) 'nan)
          (format #f "~S not a number" (sig-cont signal)))
         (else
          "Some weird thing is happening...?"))))

(define (game)
  (let loop ((i 1)
             (secret (+ 1 (random 100))))
    (begin
      (output (make-signal 'ask '()))
      (let ((guess (read)))
        (cond ((not (number? guess))
               (begin 
                 (output (make-signal 'nan guess))
                 (newline)
                 (loop i secret)))
              ((= guess secret) 
               (output (make-signal 'win i)))
              (else
               (begin
                 (cond ((< guess secret) 
                        (output (make-signal 'low '())))
                       ((> guess secret)
                        (output (make-signal 'high '()))))
                 (newline)
                 (loop (+ 1 i) secret))))))))

(game)

```

---

### Post by mike_g on 2008-08-29
> whats the time thing for...all online help for that code snippit is very bad 
Its to seed the randomisation. You need to seed the randomisation with a variable, so you get a different set of numbers each time your program runs. Seeding randomisation based on the time is a common and easy way to do this, which is what that line of code does. You should only call srand once in your program.

Heres a version I knocked up. Its ugly obfuscated and does not do any input validation. I was trying to make it as short as possible in C:
```
#include <stdio.h>
#include <stdlib.h>
#include <time.h>

int main()
{
    srand(time(0));
    unsigned g,t=rand()%100+1;
    for(;;)
    {
        scanf("%d",&g);
        if(g==t) break; 
        printf(g>t?"Lower\n":"Higher\n");
    }
    printf("U WIN!\n");
}
```

---

### Post by Sinkingships7 on 2008-08-29
> **jimi_hendrix said:**
> whats the time thing for...all online help for that code snippit is very bad

The srand() function can be thought of as short for seed_random(). When a program is run in which the computer is to generate a random number, it generates that number from numbers plugged into a mathematical equation. Not really random, correct? Every time the program is ran, the program will use the same set of numbers to plug into the equation to come up with our 'random' number, which will therefore always be the same number.

In order to force the computer to come up with a truly 'random' number, we must seed (give) it a new set of numbers to use in it's little equation every time the program is run. That is where the srand() function comes into play. srand(time(NULL)) seeds a number taken from the system time. The reason we use this method is because the system time is always guaranteed to be different. Only a nano second must pass before the time that is generated from time(NULL) is completely different, therefore allowing us to come across what we call a pseudorandom number.

[This page]("http://en.wikipedia.org/wiki/Pseudorandomness") may help you understand in a greater detail, if my explanation didn't quite hit the spot.

---

### Post by swappo1 on 2008-08-29
Here is my entry.
[PHP]#! /usr/bin/env python
# random_game.py

import random

guesses = []
guess = 0
number = random.randint(1, 100)

print "Guessing Game"
print

while guess != number:
	guess = input("Pick a number between 1 - 100: ")
	if guess == number:
		guesses.append(guess)
		print "You guessed the number,", number, "in", len(guesses), "guesses."'\n'"Congratulations!"
	elif guess < number:
		print "Your guess is too low."
		guesses.append(guess)
	else:
		print "Your guess is too high."
		guesses.append(guess)
[/PHP]

---

### Post by jimi_hendrix on 2008-08-29
[PHP]//headers needed
#include <iostream>
#include "string"
#include <cstdlib>

using namespace std;

int random(int Range) //method for generating random ints
{
	int random_integer = (rand()%Range)+1; 
	
	return random_integer;
}

int main(int argc, char** argv)//main program
{
	//variables
	int target_num;
	int guess;
	int range;
	int guess_num = 0;
	
	srand((unsigned)time(0)); //seeding the random 

	
	cout << "what is the highest possible number you would like the answer to be?" << endl;
	
	cin >> range;
	
	target_num = random(range);
	
	while (1) //game loop
	{
		
	guess_num++;
	
	cout << "please enter a guess" << endl;
	
	cin >> guess;
	
	if (guess > target_num)
	{
		cout << "guess is too high" << endl;
	}
	
	else if (guess < target_num)
	{
		cout << "guess too low" << endl;
	}
	
	else
	{
		bool answered = false;//makes sure decision is recieved
		
		while (answered == false)
		{
			
			string answer;
			cout << "you got it in " << guess_num << " number of tries!" << endl <<"play again [y/n]" << endl;
			cin >> answer;
			
			if (answer == "y")
			{
				target_num = random(range);
				answered = true;
				guess_num = 0;
			}
			
			else if (answer == "n")
			{
				return 0;
			}
			
			else
			{
				cout << "invalid input";
			}
		}
		
	}
	
	}
	return 0;
}


[/PHP]

updated

---

### Post by scragar on 2008-08-29
for a bit of a laugh I whipped up this javascript version, it took about 20 secs, so no complainging about how terrible it's written, k?

PHP tags used part way through for pretty colours bonus:
[html]<html>
<head>
<script type="text/javascript">[/html]
[php]/* <![CDATA[
  Guess a number game
  change the bits under here for fun
*/
var wrongMSG = "PHail, you need to go {dir}";
var rightMSG = "Hurray, it only took you {guess} guess(es)";
var errorMSG = "Oh come on, enter a valid guess.";
var MaxNum = 100;
var MinNum = 1;

// please don't edit under here

var GuessThis, GuessCount, Uinput, ended = true;
function Ngame(){
  GuessThis = Math.floor(Math.random() * (MaxNum-MinNum))+MinNum;
  GuessCount = 1;
  ended = false;
  ClearMSG();
};
function Guess(){
  if(ended){
    if(confirm('play a new game?')){
      var tmp = Uinput.value;
      Ngame();
      Uinput.value = tmp;
    }else
      return;
  };

  var YourGuess = parseInt(Uinput.value, 10);
  if(isValidGuess(YourGuess)){
    if(YourGuess == GuessThis){
      ClearMSG();
      setMSG(rightMSG);
      ended = 1;
    }else{
      GuessCount++;
      if(YourGuess < GuessThis){
        ClearMSG();
        setMSG(wrongMSG, 'higher');
      }else{
        ClearMSG();
        setMSG(wrongMSG, 'lower');
      };
    };
  }else{
    ClearMSG();
    setMSG(errorMSG);
  };
};
function isValidGuess(num){
  if(isNaN(num) || num < MinNum || num > MaxNum)
    return false;
  return true;
};
function ClearMSG(){
  if(document.body.lastChild.nodeType == 3){
    document.body.removeChild(document.body.lastChild);
  };
  Uinput.value = '';
};
function setMSG(msg, dir){
  document.body.appendChild(document.createTextNode(
           msg.replace(/\{guess\}/, GuessCount).replace(/\{dir\}/, dir)
  ));
};
window.onload = function(){
  Uinput = document.getElementById('YourGuess');
  Ngame();
};
// ]]>[/php]
[html]</script>
</head>
<body>
<form action='#' onsubmit='Guess()'>
<input type='text' id='YourGuess'>
<button onclick='Guess(); return false;'>Well?</button>
</form>
</body>
</html>[/html]

---

### Post by jimi_hendrix on 2008-08-29
> **scragar said:**
> for a bit of a laugh I whipped up this javascript version, it took about 20 secs, so no complainging about how terrible it's written, k?

PHP tags used part way through for pretty colours bonus:
[html]<html>
<head>
<script type="text/javascript">[/html]
[php]/* <![CDATA[
  Guess a number game
  change the bits under here for fun
*/
var wrongMSG = "PHail, you need to go {dir}";
var rightMSG = "Hurray, it only took you {guess} guess(es)";
var errorMSG = "Oh come on, enter a valid guess.";
var MaxNum = 100;
var MinNum = 1;

// please don't edit under here

var GuessThis, GuessCount, Uinput, ended = true;
function Ngame(){
  GuessThis = Math.floor(Math.random() * (MaxNum-MinNum))+MinNum;
  GuessCount = 1;
  ended = false;
  ClearMSG();
};
function Guess(){
  if(ended){
    if(confirm('play a new game?')){
      var tmp = Uinput.value;
      Ngame();
      Uinput.value = tmp;
    }else
      return;
  };

  var YourGuess = parseInt(Uinput.value, 10);
  if(isValidGuess(YourGuess)){
    if(YourGuess == GuessThis){
      ClearMSG();
      setMSG(rightMSG);
      ended = 1;
    }else{
      GuessCount++;
      if(YourGuess < GuessThis){
        ClearMSG();
        setMSG(wrongMSG, 'higher');
      }else{
        ClearMSG();
        setMSG(wrongMSG, 'lower');
      };
    };
  }else{
    ClearMSG();
    setMSG(errorMSG);
  };
};
function isValidGuess(num){
  if(isNaN(num) || num < MinNum || num > MaxNum)
    return false;
  return true;
};
function ClearMSG(){
  if(document.body.lastChild.nodeType == 3){
    document.body.removeChild(document.body.lastChild);
  };
  Uinput.value = '';
};
function setMSG(msg, dir){
  document.body.appendChild(document.createTextNode(
           msg.replace(/\{guess\}/, GuessCount).replace(/\{dir\}/, dir)
  ));
};
window.onload = function(){
  Uinput = document.getElementById('YourGuess');
  Ngame();
};
// ]]>[/php]
[html]</script>
</head>
<body>
<form action='#' onsubmit='Guess()'>
<input type='text' id='YourGuess'>
<button onclick='Guess(); return false;'>Well?</button>
</form>
</body>
</html>[/html]

ahhh i should have done that...i recently learned javascript

---

### Post by scragar on 2008-08-29
> **jimi_hendrix said:**
> ahhh i should have done that...i recently learned javascript

ooh, erk, I hate these forums and their stupid "no left slashes outside of quotes in PHP code" idea's, what's the deal?

section of code that was messed up reposted in code tags below:
```

function setMSG(msg, dir){
  document.body.appendChild(document.createTextNode(
           msg.replace(/\{guess\}/g, GuessCount).replace(/\{dir\}/g, dir)
  ));
}; 

```

---

### Post by snova on 2008-08-29
New and improved.

[PHP]
char*m[]={"small","big"};t,g;main(int d){return d>0?((t=srand(time(0))& 0|rand
()%100)|printf("You won in %i tries!\n",-main(-1)))&0:printf("What is your gu"
"ess? ")&0|scanf("%i",&g)+g-1==t?d:printf("Too %s.\n",m[g>t])&0|main(d-1);}
[/PHP]

Small is beautiful!

---

### Post by scragar on 2008-08-29
> **snova said:**
> New and improved.

[PHP]
char*m[]={"small","big"};t,g;main(int d){return d>0?((t=srand(time(0))& 0|rand
()%100)|printf("You won in %i tries!\n",-main(-1)))&0:printf("What is your gu"
"ess? ")&0|scanf("%i",&g)+g-1==t?d:printf("Too %s.\n",m[g>t])&0|main(d-1);}
[/PHP]

Small is beautiful!

You should rewrite that with correct spacing etc, just see how it looks spaced out, I think it'd be a pretty small thing still.

---

### Post by kk0sse54 on 2008-08-29
Here's my entry I'll try and clean it up later but any feedback is appreciated :)
[PHP]#!/usr/bin/env python

from random import randrange
import sys

numtimes = 1
guess = randrange(1, 100)

print "Welcome to the Guessing game!\n"

while 1: 
    answer = raw_input("Try to guess the random number(type quit to exit): ")
    try:
        answer = int(answer)
        if answer == guess:
            print "Correct, the answer was %s and it took you  %s tries." % (answer, numtimes)
            break
        elif answer < guess:
            print "Try again, your number was too small"
        elif answer > guess:
            print "Try again, your number was too large"
    except:
        if answer == "quit":
            print "Goodbye"
            exit()
        else:
            print "Please enter an integer next time"
    numtimes = numtimes + 1
print "\nGoodbye"
exit()

[/PHP]

---

### Post by happysmileman on 2008-08-29
> **jimi_hendrix said:**
> whats the time thing for...all online help for that code snippit is very bad

srand() initialises the random number generator, passing the time as an argument is a good way to get it reasonably random without too much effort. If you used something like srand(0) it would mean that every time your program runs you get the same random numbers.

---

### Post by snova on 2008-08-29
> **scragar said:**
> You should rewrite that with correct spacing etc, just see how it looks spaced out, I think it'd be a pretty small thing still.

That would be writing it a third time. I certainly didn't write it that way originally! It looked quite reasonable when I began. All I did was apply one obfuscation after another, using various tricks to combine statements.

But as for actually doing it, how on earth would *you* format it? It's one big return statement.

Oh, and the rule I think I'm breaking is the one for "structured" code. (Do nested ternary operators count as structure?) Regardless, I almost certainly broke the rule for "clean" code.

---

### Post by Jessehk on 2008-08-30
A little verbose for my personal taste, but it works. :)

```

;;;; A number guessing game.
;;;; Run MAIN-LOOP to run the game.
;;;;
;;;; By Jessehk, Fri. August 29 2008

(defun make-guess-reader (limit &optional (prompt "Enter a number: "))
  (let ((count 0))
    (lambda ()
      (loop
         (format t prompt)
         (let ((input (parse-integer (read-line) :junk-allowed t)))
           (when (and (not (null input))
                      (> input 0)
                      (<= input limit))
             (return (values input (incf count))))
           (format t "Invalid input. Try again.~%"))))))

(defun compare-guess (guess goal)
  (cond ((> goal guess) :greater)
        ((< goal guess) :lesser)
        (t :equal)))

(defun print-response (status &optional (stream *standard-output*))
  (format stream "~A~%"
          (case status
            (:greater "Too small...")
            (:lesser "Too large...")
            (:equal "You got it!"))))

(defun main-loop ()
  (let* ((limit 100)
         (goal (+ (random limit) 1))
         (reader (make-guess-reader limit)))
    (format t "You guessed the number in ~A attempt~:P!~%"
            (loop
               for (guess attempts) = (multiple-value-list (funcall reader))
               for status = (compare-guess guess goal)
               do (print-response status)
               until (equal status :equal)
               finally (return attempts)))))


```

---

### Post by samjh on 2008-08-30
Just trying to re-learn C++ these days.

No very idiomatic, but anyway, this is a recursive version:

```
#include <iostream>
#include <cstdlib>
#include <ctime>

using namespace std;

// Maximum value of random number.
const int rmax = 100;

int init_random()
{
	srand(time(NULL));
	return rand() % 100 + 1;
}

// The game loop:
// If the guess is wrong, increment counter and recursively call this function.
// If the guess is right, simply flow back to the main function.
void game_loop(int &counter, int bullseye)
{
	int guess;
	
	cout << "What's your guess? ";
	cin >> guess;
	
	if (guess != bullseye)
	{
		if (guess > bullseye)
		{
			cout << "Your guess was too high!" << endl;
		}
		else if (guess < bullseye)
		{
			cout << "Your guess was too low!" << endl;
		}
		++counter;
		game_loop(counter, bullseye);
	}
}

int main()
{
 	int counter;
 	int target;
 	
 	counter = 1;
 	target = init_random();
 	
 	cout << "Guess the random number between 1 to " << rmax << "." << endl;
 	game_loop(counter, target);
 	cout << "Right guess! You got it in " << counter << " attempts. :)" << endl;
 	
 	return 0;
}
```

---

### Post by nvteighen on 2008-08-30
The only really structured implementations I can see here are:
> **jinksys said:**
> (Assembly)
> **scragar said:**
> (Javascript)
> **Jessehk said:**
> (Common Lisp)

And possibly mine:
> **nvteighen said:**
> (Scheme Lisp)

Structured code is about splitting the problem into functions of which each one performs one task. "One function = One task"; as you see it's very related to the concept of modularity (if it's not actually the same?).

Most of you are using this pattern:
```

1. Generate the random
2. Loop where user's input is compared to guess and output is performed.

```

The error is that while you correctly separated the random generation, you don't separate the game flow from output. You're integrating the user interface to the game itself... so, what if you want to change your command line to a GUI? You'll have to change the whole program just to change the "external appearance"!

The "ideal" solution is jinksys's in Assembly. Notice how all output strings are grouped into one place and code is in another one; of course, this due Assembly's way to do things and the programmer hasn't there a choice. But I think it's a good example to show what's meant with structured programming.

scragar's Javascript is IMO the nicest entry. As in jinksys's, each possible output is declared before and the code just has to call to output something, without caring what kind of output it turns out to be. He decided to use document.write(), but it could be easily changed into an alert box or something else; notice how he uses parameters to tell the output function setMSG() what message to pick.

Jessehk's is a typical structured Lisp-ish code with abstraction... His code not only will work for this game in particular but for anything, thanks to the make-guess-reader which is in charge of defining... Compared to my Scheme Lisp implementation, this is way much superior because it also allows to customize *input* by just modifying the (make-guess-reader) procedure/closure... which by the way isn't the real validator: it's a function that dynamically creates and returns a function to validate input... (yes, self-modifying code is daily bread in Lisp!). But that's not the point (and clearly not a beginner's way to do things... :D). Instead, look at the (print-response): even if you don't know Lisp, you'll understand what's going on there: the output is defined there and called by convenience from the (compare-guess) function... the (main-loop) just cares for control-flow, not a single piece of the game's implementation.

Mine is not as sophisticated as Jessehk's, because I created a procedure called (game), whose goal is to represent the game... You may say that's not structured; well, Lisp languages have a little feature called lexical scoping that allow you to define sub-structures... In my case, nested instead of written aside: (let loop...) is Jehssek's (main-loop) and the "unnamed let" that lives inside (let ((guess (read)))... ) is his (compare-guess). Actually, Scheme forces me to do such a construct because it lacks of looping-constructs (all is recursion).

I hope these examples and my comments help people to understand better what structured programming is about.

---

### Post by scragar on 2008-08-30
EDIT: bah, missed something, doesn't matter.

ANOTHER EDIT: And my code doesn't use document.write, it uses valid, standards compliant, DOM editing. (besides, document.write for adding a single line in would be hundreds of times harder than my method, since you'd need to write the form out again with each call)

---

### Post by scragar on 2008-08-30
I decided to rewrite some of my code and place it in a class to completely avoid global vars, see it below, the javascript code is best placed in an external file, that way the code looks much cleaner(I'm assuming it, but if you didn't want that you can copy/paste the contents of the first code tags here into the <script> tag with the bold bit and delete the bold bit, and it should work)
External code, **RandNumGame.js**
[php]/* <![CDATA[
  :P you can play multiple games at the same time as well.
  Don't know why anyone would want to though...
*/
function RandNumGame(){
  this.guessThis = 0;
  this.guessCount = 1;
  this.ended = true;
  this.minNum = 0;
  this.maxNum = 1000;
  this.wrongMSG = "{dir}";
  this.rightMSG = "{guess}";
  this.errorMSG = "bad";
  this.InputEle = null;// must be assigned!
  this.OutputEle = null;// and this
};

RandNumGame.prototype.NewGame = function(){
  this.guessThis = Math.floor(Math.random() * (this.maxNum-this.minNum))+this.minNum;
  this.guessCount = 1;
  this.ended = false;
  this.ClearMSG();
};

RandNumGame.prototype.Guess = function(){
  var yourGuess;
  if(this.ended){
    if(confirm('play a new game?')){
      yourGuess = this.InputEle.value;
      this.NewGame();
      this.InputEle.value = yourGuess;
    }else
      return;
  };

  yourGuess = parseInt(this.InputEle.value, 10);
  this.ClearMSG();// we're going to be sending a message soon
  if(this.IsValidGuess(yourGuess)){
    if(yourGuess == this.guessThis){
      this.SetMSG(this.rightMSG);
      this.ended = true;
    }else{
      if(yourGuess < this.guessThis){
        this.SetMSG(this.wrongMSG, 'higher');
      }else{
        this.SetMSG(this.wrongMSG, 'lower');
      };
      this.guessCount++;
    };
  }else{
    this.SetMSG(this.errorMSG);
  };
};

RandNumGame.prototype.IsValidGuess = function(num){
  if(isNaN(num) || num < this.minNum || num > this.maxNum)
    return false;
  else
    return true;
};

RandNumGame.prototype.ClearMSG = function(){
  while(this.OutputEle.hasChildNodes()){
    this.OutputEle.removeChild(this.OutputEle.firstChild);
  };
  this.InputEle.value = '';
};

RandNumGame.prototype.BindToForm = function(frm){
  // empty and destroy the form to make way for our contents
  while(frm.hasChildNodes()){
    frm.removeChild(frm.firstChild);
  };
  this.InputEle = document.createElement('input');
  frm.appendChild(this.InputEle);
  var submitBTN = document.createElement('input');
  submitBTN.type = 'submit';
  submitBTN.value = 'Guess';
  frm.appendChild(submitBTN);
  this.OutputEle = document.createElement('div');
  frm.appendChild(this.OutputEle);
  
  frm.action = 'javascript: '+FindWrapper(this)+'.Guess();';

};[/php]
**RandNumGame.js** cont
```
RandNumGame.prototype.SetMSG = function(msg, dir){
  this.OutputEle.appendChild(document.createTextNode(
           msg.replace(/\{guess\}/g, this.guessCount).replace(/\{dir\}/g, dir)
  ));
};

// another function I call, ignore it:
function FindWrapper(){
  for(var x in window){
    if(window[x] == arguments[0])
      return x;
  };
  return null;
};
// ]]>
```

and a page to use it:
```

<html>
<head>
<title>Random Number Game :P</title>
<script type="text/javascript"** src="RandNumGame.js"**></script>
<script type='text/javascript'>
/* <![CDATA[
  SAMPLE USAGE HERE, normaly you just want to bind it to an empty form,
  it does well like that
*/

var game1 = new RandNumGame();
game1.minNum = 1;
game1.maxNum = 100;
game1.wrongMSG = "Go {dir}";
game1.rightMSG = "Yeah, and it only took {guess} tries";
game1.errorMSG = "bad input :(";

var game2 = new RandNumGame();
game2.minNum = 100;
game2.maxNum = 1000;
game2.wrongMSG = "Nope, that's try {guess}, you still need to go {dir}";
game2.rightMSG = "Yeah, that right, and in only {guess} guesses";
game2.errorMSG = "bad input :(";

window.onload = function(){
  game1.BindToForm(document.forms[0]);
  game1.NewGame();
  game2.BindToForm(document.forms[1]);
  game2.NewGame();
};

// ]]>
</script>
</head><body>
<p>let's play a couple of random number games.</p>
<form></form>
<form></form>
</body>
</html>

```

---

### Post by mike_g on 2008-08-30
Well I managed to shave an extra 15 characters off mine. Its not stuctured, but then its meant to be ugly.
```
#include <stdio.h>
#include <stdlib.h>
#include <time.h>

int main()
{
    srand(time(0));
    unsigned g,n=0,t=rand()%100+1;
    for(;g!=t;++n)
        scanf("%d",&g),printf(g==t?"%d GUESS\n":g>t?"Lower\n":"Higher\n",n);
}
```
Edit: Make that 16.

---

### Post by scragar on 2008-08-30
> **mike_g said:**
> Well I managed to shave an extra 15 characters off mine. Its not stuctured, but then its meant to be ugly.
```
#include <stdio.h>
#include <stdlib.h>
#include <time.h>

int main()
{
    srand(time(0));
    unsigned g,t=rand()%100+1;
    while(g!=t)
        scanf("%d",&g),printf(g==t?"U WIN!\n":g>t?"Lower\n":"Higher\n");
}
```
Edit: Make that 16.

your not printing number of guesses when you win.

---

### Post by mike_g on 2008-08-30
Ok, that added another 9 chars. Above post edited.

---

### Post by battlebrowz on 2008-08-30
> **cardboardtoast said:**
> What exactly ARE the rules??? I read the "structured programming" link, but that left me confused...:(  Do we just make a number guessing program, or do we have to do it a special way?

mosty friedman asked my other question...

Ok... all languages have layman-term structure (for the most part...)

But when they say "structured" it's a term to distinguish the language from an *object oriented* language.  For example, Fortran, Perl, and C are all structured languages*.  

C++,[COLOR="DarkRed"] Ruby[/COLOR] and others are Object Oriented languages. I like to think of the difference between a structured program and OO type would be like the difference between reading a novel and reading hypertext (or a hypercard stack). Think of the difference between an array and an open ended hash.

They call them 'structured' because, like a novel, there's a beginning, a middle and an end in there somewhere, but it doesn't always have to be in chronological order. For a good example for non-chronological, think
about "Cryptonomicon". (Novel by Neil Stephenson) There are a LOT of threads, it's freaking huge, but the story has a natural order to it
that is, ultimately linear through time. 

Just to clarify that "structured" does NOT mean chronologically written.
That would be a painful limitation.

The latter has a more... well, amorphous blob or klein-bottle kind of structure if you were to visualize the program's execution flow as a 3D object. And no, Finnigan's Wake is not like this, since while it does repeat itself (basically a big loop) it's still ultimately linear.

EDIT: Or better yet, it's the difference between building a house with prefabricated units or building it "from scratch". You learn more about how a house is classically structured by designing it from ground-up with wood, plaster and so on in mind, than you would by slapping together the prefabricated units as per the assembly instructions you got from the factory.
   
Of course, I could be completely off here and they just used the word to say, "Don't make a mess of it, fellas; you are practicing good style sense, too..." 

Except for SNova.  Snova is obviously an experienced programmer and is having fun. (As well as demonstrating powerful lessons with obfuscated C. That is... "if you are new, Don't hack this at home. YET. Oh, and this is what you get to do later! Can *you* read it?" )


**[FONT="Courier New"]Perl (and some others) is a mutant. Though it doesn't *need* layman's structure to work... it's known to be a Bad Idea not to use it. Also, it can be used as an Object Oriented language as well as a structured language, but that's another show. And unless the beginner is a virtual Mozart of programming, we won't see that here.  Furthermore, PHP and a few others [I]can* be Object Oriented, which is why I suspect that they put in the "structured" caveat, so that newbies (Like me) trying to make objects in Perl, PHP and Ruby won't hurt themselves.

One of the reasons why they limit object oriented stuff early on is that it is strongly advantageous to understand how structured programs work before doing object oriented stuff. After all, they are very different animals and knowing how they interact (or not) will help you later on.

EDIT:  Oops, I forgot to mention that ruby is an object oriented language. Many people do not recommend that one start with Object Oriented programming, for complex reasons even beyond what I mentioned here.[/FONT]
[/I]
:KS

---

### Post by scragar on 2008-08-30
I figured I'd do one last upgrade to my code, then call it quits, presenting upgraded version of my RandNumGame class(as an attachment for the sake of all those that value being able to see the code).

I've also updated usage based on my edits:
```
<html>
<head>
<title>Random Number Game :P</title>
<script type="text/javascript" src="RandNumGame.js"></script>
<script type='text/javascript'>
/* <![CDATA[
  SAMPLE USAGE HERE, normaly you just want to bind it to an empty form,
  it does well like that
*/

var game1 = new RandNumGame();
game1.minNum = 1;
game1.maxNum = 100;
game1.wrongMSG = "{num} - Go {dir}";
game1.rightMSG = "Yeah, it was {num}! and it only took {guess} tries";
game1.errorMSG = "bad input :(";

var game2 = new RandNumGame();
game2.minNum = 100;
game2.maxNum = 1000;
game2.wrongMSG = "{guess} = {num} - go {dir}";
game2.rightMSG = "{guess} = {num} - SPOT ON!";
game2.errorMSG = "bad input :(";

window.onload = function(){
  game1.BindToForm(document.forms[0]);
  game1.NewGame();
  game2.BindToForm(document.forms[1]);
  game2.NewGame();
};

// ]]>
</script>
</head><body>
<p>let's play a couple of random number games.</p>
<form></form>
<form></form>
</body>
</html>

```

what's new in the update then?
A couple of comments that arn't needed removed, and one or 2 more added.
The wrapper function got integrated.
When you win or lose you get a link to play again, instead of having to try to continue playing and then clicking OK on a confirmation.
it logs messages, meaning that you can look at past results if you get lost. Handy.

Erm that's about it.

---

### Post by cardboardtoast on 2008-08-30
[QUOTE=battlebrowz]Ok... all languages have layman-term structure (for the most part...)

But when they say "structured" it's a term to distinguish the language from an object oriented language. For example, Fortran, Perl, and C are all structured languages*.

C++, Ruby and others are Object Oriented languages. I like to think of the difference between a structured program and OO type would be like the difference between reading a novel and reading hypertext (or a hypercard stack). Think of the difference between an array and an open ended hash.

They call them 'structured' because, like a novel, there's a beginning, a middle and an end in there somewhere, but it doesn't always have to be in chronological order. For a good example for non-chronological, think
about "Cryptonomicon". (Novel by Neil Stephenson) There are a LOT of threads, it's freaking huge, but the story has a natural order to it
that is, ultimately linear through time.

Just to clarify that "structured" does NOT mean chronologically written.
That would be a painful limitation.

The latter has a more... well, amorphous blob or klein-bottle kind of structure if you were to visualize the program's execution flow as a 3D object. And no, Finnigan's Wake is not like this, since while it does repeat itself (basically a big loop) it's still ultimately linear.

EDIT: Or better yet, it's the difference between building a house with prefabricated units or building it "from scratch". You learn more about how a house is classically structured by designing it from ground-up with wood, plaster and so on in mind, than you would by slapping together the prefabricated units as per the assembly instructions you got from the factory.[/QUOTE]

Thanks for the explanation.  So, a "structured" programing language is linear? (I think that is what is being said)  What makes OOP non-linear? Sorry, but I don't know much about either..:(

hope that isn't pulling the thread OT

---

### Post by snova on 2008-08-30
> **mike_g said:**
> Well I managed to shave an extra 15 characters off mine. Its not stuctured, but then its meant to be ugly.
```
#include <stdio.h>
#include <stdlib.h>
#include <time.h>

int main()
{
    srand(time(0));
    unsigned g,n=0,t=rand()%100+1;
    for(;g!=t;++n)
        scanf("%d",&g),printf(g==t?"%d GUESS\n":g>t?"Lower\n":"Higher\n",n);
}
```Edit: Make that 16.

Ha! Mine is worse! :p

> Except for SNova. Snova is obviously an experienced programmer and is having fun. (As well as demonstrating powerful lessons with obfuscated C. That is... "if you are new, Don't hack this at home. YET. Oh, and this is what you get to do later!

Experienced? Not really. Only a few years... I think? (Mom has clarified- a year and a half since I got my laptop. But I think I started with C++ a bit before that.) I guess that might count as experienced... Oh well. At least I'm not helping anybody cheat. I think it would be obvious if anybody copied from it.

The IOCCC (International Obfuscated C Code Contest - [http://www.ioccc.org/](http://www.ioccc.org/)) has some really nice examples of obfuscated code. *"This program calculates the value of PI by looking at it's own area..."*. I take my inspiration from them.

I like the flight simulator that's shaped like a top view of a plane. Oh, and the one that plays tic-tac-toe with it's own source code.

> Can *you* read it?" )

I can read it! But then again, I wrote it... I might even be able to explain how it works.

Anyway... My definition of "structured" is "Broken into logical pieces".

Well, since I'm apparently an "experienced" programmer, I'll have to comment on other entries...

Unfortunately, I don't understand Lisp, Haskell, or Javascript, so I can't comment on anybody who wrote one of those. Nor can I say anything for PHP. But some of the Python ones look neat and simple, so yay for them. Of course, it's *hard* to write incomprehensible code in Python... Or at least difficult.

> The "ideal" solution is jinksys's in Assembly. Notice how all output strings are grouped into one place and code is in another one; of course, this due Assembly's way to do things and the programmer hasn't there a choice. But I think it's a good example to show what's meant with structured programming.

How is assembly code *ideal*? :) But yes, it does look nice. And as far as assembly goes, this is quite understandable. Except for the system calls, anyway. And I hate AT&T syntax!

---

### Post by mosty friedman on 2008-08-30
[php]
import java.io.*;

     public class Guess {
	 public static void main(String[]args)throws IOException
	{
	  BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
	  int y = (int)(Math.random()*100)+1;       //function to generate a random number from 1-100
	  int x = Integer.parseInt(br.readLine());//takes integer input from the user
	  int guesses =1;                        //number of guesses
	  while(x!=y)
	{
	  if(x>y)
	  System.out.println("go lower");
	  if(x<y)
	  System.out.println("go higher");
	  x=Integer.parseInt(br.readLine());
	  guesses++;
	}
	  System.out.println("true");
	  System.out.println("you have taken "+guesses+" guesses");
    }
	}
[/php]
comment on my code please :D

---

### Post by alesianlarken on 2008-08-30
I am a java programmer i can understand you programs well.I want to know how the hashmap in java is iteratable using iterator.
=============================
alesianlarken

[Wisconsin Alcohol Addiction Treatment]("http://www.alcoholaddiction.org/wisconsin")

---

### Post by snova on 2008-08-30
> **mosty friedman said:**
> [php]
import java.io.*;

     public class Guess {
     public static void main(String[]args)throws IOException
    {
      BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
      int y = (int)(Math.random()*100)+1;       //function to generate a random number from 1-100
      int x = Integer.parseInt(br.readLine());//takes integer input from the user
      int guesses =1;                        //number of guesses
      while(x!=y)
    {
      if(x>y)
      System.out.println("go lower");
      if(x<y)
      System.out.println("go higher");
      x=Integer.parseInt(br.readLine());
      guesses++;
    }
      System.out.println("true");
      System.out.println("you have taken "+guesses+" guesses");
    }
    }
[/php]comment on my code please :D

If you insist.

Now, I only know the basics of Java, but this is simple enough for me. My primary complaint is that you duplicate the input line. Why not put it at the start of the loop? Just set x to 0, since y will always be larger than this.

Secondly, you could be printing more helpful messages. "true" isn't exactly self-explanatory.

Third, I suggest you catch the exception. I don't know where it's thrown, but if it signals an EOF, you could perhaps print some kind of "Good bye!" message.

Finally, what's with the weird indentation?

Otherwise, very nice. A good example of the kind of Java I can read.

---

### Post by OutOfReach on 2008-08-30
Here's mine :), written in Python of course
[PHP]import random

x = True
random_number = random.randint(0,100)
guesses_made = 0

while x:
    try:
        guess = int(raw_input("Enter your guess: "))
        if guess > random_number:
            print "You guessed to high!"
            guesses_made += 1
        if guess < random_number:
            print "You guessed to low!"
            guesses_made += 1
        if guess == random_number:
            print "You are correct, the answer is %s!" % random_number
            guesses_made += 1
            print "You got the answer in %s tries" % guesses_made
            x = False
    except ValueError, e:
        print "You did not input a valid number!"[/PHP]

---

### Post by Reiger on 2008-08-30
> **snova said:**
> If you insist.

Now, I only know the basics of Java, but this is simple enough for me. My primary complaint is that you duplicate the input line. Why not put it at the start of the loop? Just set x to 0, since y will always be larger than this.

My primary complaint would be with the cast. (The other thing is propably his standard way of doing readLine() unitl the stream closes.) You should only cast when you really don't care anymore about the truncated part of your value. And in this case the random number generator will spit out values of 1 - 10**1** inclusive. (For what interseting situation arises when Math.random() == 1.0 ...?)
> 
Secondly, you could be printing more helpful messages. "true" isn't exactly self-explanatory.

Third, I suggest you catch the exception. I don't know where it's thrown, but if it signals an EOF, you could perhaps print some kind of "Good bye!" message.


For graceful exception handling I would suggest taking the prompting/readLine() call out of the main method; and make that a method of it's own.

> 
Finally, what's with the weird indentation?


Likely an IDE being picky on tabs etc. ;)

---

### Post by DaymItzJack on 2008-08-30
```
public class guess{
 public static void main(String[] args) {java.util.Scanner k=new java.util.Scanner(System.in);
  int g=-1,t=1,r=new java.util.Random().nextInt(100);
  
  for(;g!=r;t++){System.out.print("Enter a number ==> ");
   try{g=Integer.parseInt(k.nextLine());
    if(g>r){System.out.println("You need to guess lower!");}
    else if(g<r){System.out.println("You need to guess higher!");}
    else{System.out.println("You got the number ("+r+"), it only took you "+t+" tries!");}}
   catch(java.lang.NumberFormatException e){System.out.println("Try entering a number.");}}}}
```

Java is not the easiest language to write small code in :(

---

### Post by mosty friedman on 2008-08-30
but the Math.random() functions generates doubles..so i had to cast

---

### Post by mosty friedman on 2008-08-30
> **Reiger said:**
> My primary complaint would be with the cast.

this function generates random double numbers not integers...that's why i casted..i didnt really understand what u meant

---

### Post by mosty friedman on 2008-08-30
ah ok, i got it...i found this method nextInt(int value); which returns a random integer number from 0 inclusive to value(exclusive)...so i should have used this method with 101 as the specified value..thanks for the tip :)

---

### Post by cmay on 2008-08-31
here is one in Freepascal.
compile whit fpc in turbo pascal 7.0 mode.
and dont input any characters since it will crash then. i have not used pascal in 3 years so its a from the begin again newbie point program.i had one version i written whit a menu and a window using unit crt i did on windows but i cant find it again:( 
[PHP]
{ author cmay 2008 : }
program guess_number;
uses sysutils,crt;
var 
count_guess:integer;
guess:integer;
secret_number:integer;

{main start here }
begin
count_guess:=0;
secret_number:=random(100);
guess:=0;
while guess <> secret_number do
begin
count_guess:=count_guess + 1;
writeln(' guess my number');
readln(guess);
if secret_number < guess then begin
writeln('too high');
end;

if secret_number > guess then 
begin
writeln('too low');
end;

if guess = secret_number then
 begin
writeln('you win');
writeln('number of guesses used was',count_guess);
end;
end;
end.
[/PHP]

---

### Post by HotCupOfJava on 2008-08-31
> **mosty friedman said:**
> this function generates random double numbers not integers...that's why i casted..i didnt really understand what u meant

Actually when you use the Math.random method you typically do use a cast for integers. The method generates a double that is LESS than 1, so you must use a SCALING value and a SHIFTING factor in addition to a cast. The SHIFTING value is the first number in the desired range of integers. The SCALING factor is the width of the desired range of consecutive integers. Example:

int result = 1 + (int) (Math.random() * 100);

In this case, "1" is the Shifting value and "100" the scaling factor.

This is a perfectly legitimate way to select a random number.

---

### Post by mosty friedman on 2008-08-31
> **HotCupOfJava said:**
> 
int result = 1 + (int) (Math.random() * 100);

In this case, "1" is the Shifting value and "100" the scaling factor.

This is a perfectly legitimate way to select a random number.

that is exactly what i did...the other dude complained about the cast..

---

### Post by -grubby on 2008-08-31
> **cmay said:**
> here is one in Freepascal.
compile whit fpc in turbo pascal 7.0 mode.


Eh just a question.. where is the indentation? Makes it billions of times easier to read, and pretty much required if you want to share code with anybody

---

### Post by cmay on 2008-08-31
> Eh just a question.. where is the indentation? Makes it billions of times easier to read, and pretty much required if you want to share code with anybody
i like it this way.you should see my perl script in the 99 bottle challenge.
i indent c but not pascal since i like to read it like a book simply.
i cant see that good so indention is my worst.pascal lets me do this exactly this way and i can it read still. in other stuff i can miss a { or ; i also already had an entry in c. whit better game play and a menu. i only posted this pascal version since i got carried away :)

ps 
i can go back and fix it if it really bother people to look at
i did not expect anyone to pay much attention to it anyway.

---

### Post by nvteighen on 2008-09-01
> **cmay said:**
> 
i did not expect anyone to pay much attention to it anyway.

You never know... :)

---

### Post by Bodsda on 2008-09-05
[php]#! /usr/bin/env python

# number_guess.py
# A guess the number game, written in python by Bodsda.
# "foo += 1" is the same as "foo = foo + 1"
# This works as stated by LaRoza. It doesnt have any try/excepts
# or checks because that wasnt asked for, if il get more brownie points
# for them let me know and il add them.

import random
import os

def main():
    os.system("clear")
    raw_input("Welcome to 'Guess the number'. Press enter to start")
    number = random.randrange(101)
    print "\n I have calculated the random number.\nPlease make your guess now.\n"
    correct = 0
    guesses = 0
    while correct == 0:
        guess = int(raw_input("Guess: "))
        if guess == number:
            guesses += 1
            print "**Congratulations you win**\n\nIt took you", guesses, "guesses."
            correct = 1
        if guess < number:
            guesses += 1
            print "Sorry. A little higher this time."
        if guess > number:
            guesses += 1
            print "Sorry. A little lower this time."

main()[/php]

Anyone else noticed the strange way in which alot of python entries are using a different way of generating a random number?

---

### Post by LaRoza on 2008-09-05
> **Bodsda said:**
> 
Anyone else noticed the strange way in which alot of python entries are using a different way of generating a random number?

No, that module is quite handy and there is more than one way to do it (I am sure there is an optimal way to do it, but perfection is only possible if you are Linus)

---

### Post by SteelDragon on 2008-09-07
Late to the party, I am, but here's mine nonetheless. It looks like it's longer than the other python entries, but I think I did more input checking than most (since I was disqualified from the first challenge for that very reason) and I used a function unnecessarily just because it looks better to me. I trust that this still constitutes functional programming, right? It's only classes and objects and such that would knock me out of that category?

Anyway, here we go:

[PHP]#!/usr/bin/python

# ---------------- guessgame.py -----------------------
# The program picks a random number between 1 and n, where
# n is specified by the user or 100 by default, and the
# user tries to guess the number. The program answers 
# each guess with a 'too high' or 'too low' message.
# ------------------------------------------------------

import random
import sys

# Get the user's guess and make sure it's valid. Invalid entries aren't counted as 'tries'.
def get_guess( maxNum ):
        guess = raw_input( 'What is your guess? ' )
        while True:
                try:
                        if int( guess ) not in range( 1, maxNum + 1 ):
                                raise ValueError( 'Out of range' )
                except ( ValueError, TypeError ):
                        guess = raw_input( 'You must enter an integer between 1 and %d. Try again. ' % maxNum )
                else:
                        break

        return int( guess )


# The user can specify the upper bound of the game on
# with command line arguments.
# Default is 100.
maxNum = 100
if len( sys.argv ) > 1:
        try:
                maxNum = int( sys.argv[1] )
                if int( sys.argv[1] ) < 1:
                        raise ValueError( 'Out of range' )
        except ( TypeError, ValueError ):
                print 'This game only understands positive integers.\nPlaying to 100.'


# Initialize the game
secretNum = random.choice( range( 1, maxNum + 1) )
print secretNum
print 'I am thinking of a number between 1 and %d. If you can guess it, you win. Won\'t that be nice?\n' % maxNum
counter = 0
userGuess = -1

# Playing the game
while userGuess is not secretNum:
        userGuess = get_guess( maxNum )
        counter += 1

        if userGuess > secretNum: 
                print 'Too high. Try again.'
        elif userGuess < secretNum: 
                print 'Too low. Try again.'
        elif userGuess is secretNum:
                print '\nYou win!\nIt took you %d tries to guess the number %d!' % ( counter, secretNum )

sys.exit(0)
[/PHP]

---

### Post by kk0sse54 on 2008-09-08
Just wondering when's the next challenge coming up? I've learned a lot by doing these and I'm always looking forward to the next one :)

---

### Post by akbeancounter on 2008-09-08
> **C!oud said:**
> I've learned a lot by doing these and I'm always looking forward to the next one :)

I agree.  I'm starting with 99 Bottles and working my way forward, but hopefully I'll be caught up enough to participate in the next one.

-- A.

---

### Post by cmay on 2008-09-15
[PHP]#!/usr/bin/perl -w
my $range = 100; my $minimum = 0; my $number = int(rand($range)) + $minimum; my $guess; my $used_guess=0;while($guess=<stdin>){$used_guess++; if($guess < $number){ print "too low\n";}if($guess > $number){print "too high\n";}if($guess == $number){print "you win \n";}print "your guess used total[",$used_guess,"]\n";}[/PHP]
here is a  one line version  in perl. :)

---

### Post by Thesuperchang on 2008-09-16
My C implementation, complete with error handling.

[PHP]#include <stdio.h>

#define MAX_VAL 0x63

int main(void)
{
	int rNum, gNum;
	int icount = 0;

	/* Generate a random number between 1 and 100 */
	rNum = (rand() & MAX_VAL) + 1;

	/* Get user to guess value */
	do
	{
		printf("Guess the number: ");
		if(scanf("%d", &gNum) != 1)
		{
			printf("Sorry pal, you messed up the input...\n");
			scanf("%*1[\n]");
			scanf("%*[^\n]");
		}
		else
		{
			if(gNum > rNum)
			{
				printf("Guess lower...\n");		
			}
			if(gNum < rNum)
			{
				printf("Guess higher...\n");				
			}
		icount++;
		}
	} while(rNum != gNum);

	printf("Correct, it took you %d attepts\n", icount);

	return 0;
}[/PHP]

---

### Post by pp. on 2008-09-16
I see a bit of confusion here concerning the term 'structured'.

Historically, that term was introduced to describe programs which employed only three kinds of 'flow of execution': the sequence, the iteration (aka repetition) and the case. In order to be 'structured', the executable statements of a program had to use those three building blocks, and every one had to be completely executed or not at all.

In that vein, many modern languages support non-structured or at least poorly structured code by adding some escape clauses to the iteration constructs. 

By that definition, you can say that most object oriented languages are 'structured languages' as well since their verbs clearly allow you to code sequences, iterations and selections.

If, on the other hand, you mean by 'structured code' merely 'clearly organised', then object oriented designs certainly qualify because they allow you to organise your ideas and hence your code by some additional criteria.

---

### Post by pp. on 2008-09-16
After a very brief inspection of the solutions submitted here, I can suggest an enhancement to the logic of the program.

Those solutions which I can at least partially understand have in common:
- Reading of the user's guess takes place at the start of the main loop
- congratulating the user for finding the solution takes place within the loop

In addition, some solutions need additional flags or spurious values (for the guess) in order to support the program 'logic' of 'flow'.

By introducing a technique which is called 'read-ahead', you arrive at a more robust and flexible overall structure for your program.

This is a Pseudo code for many of the submitted solutions

set number_to_guess to some random number in {1..100}
set number_guessed to some number not in {1..100}
set number_of_guesses to 0
while number_guessed not = number_to_guess do
. increment number_of_guesses by 1
. prompt user for a number
. read number_guessed
. case
. . when number_guessed is not a number
. . .  set number_guessed to some number not in {1..100}
. . .  tell user that it's not a number
. . .  (decrement number of guesses by 1?)
. . when number_guessed = number_to
. . .  congratulate user
. . .  print number_of_guesses
. . when number_guessed < number_to_guess
. . .  print 'too low'
. . when number_guessed > number_to_guess
. . .  print 'too high'

While a version with read-ahead produces

set number_to_guess to some random number in {1..100}
set number_of_guesses to 0
print greeting, rules, first prompt
read number_guessed
while number_guessed not = number_to_guess do
. case
. . when number_guessed is not a number
. . . print 'is not a number'
. . else [number_guessed is a number]
. . . increment number_of_guesses by 1
. . . case
. . . . when number_guessed > number_to_guess
. . . . . print 'too high'
. . . . else
. . . . . print 'too low'
. prompt for next guess
. read number_guessed
print congratulation
print number_of_guesses

---

### Post by SteelDragon on 2008-09-16
Thanks pp.

I think I understand why you removed the congratulation from the loop but I don't see the advantage in using a do...while as opposed to just a while or of reading the guess at the end instead of the beginning of the loop? Any elaboration would be appreciated. Meanwhile, I'll look into read-ahead and see what I find. 

Thanks again.

---

### Post by pp. on 2008-09-16
@dragon

It's just pseudo code. In pseudo code you are supposed to remain very informal. The actual coding in a real programming language comes later, when you're satisfied with the overall structure of your program and with the correctness of the algorhitm (such as it is).

The line reading 'while (condition) do' does nothing but indicate that the following block of code is to be executed while the stated condition holds true. That implies, of course, that the condition is tested before the block of statements is executed.

The reading is done at two places: once at the very beginning of the program and once after each (failed) guess is processed.

The intention of this technique is that you can assign responsibilities to each part of your code in a very unambiguous manner.

There are parts of the code which are responsible for the processing of
- an invalid guess (not a number)
- any valid but not succesful guess (any number but the wanted one)
- a number which is too large
- a number which is too small
- the wanted number

Hence, you can alter the specifications for your program in nearly every conceivable way and still use the same program structure. 

Does this help in any way?

---

### Post by bobbocanfly on 2008-09-16
Quick attempt in Python. I really should learn a new language to try these challenges out with.

```
#!/usr/bin/env python

import random

def get_int(message):
    try:
        return int(raw_input("%s " % message))
    except ValueError:
        return get_int("Enter a number!") #Not ideal
            
if __name__ == "__main__":
    tries = 1 #Count the one we are about to make
    rand = random.choice(range(1,101))
    attempt = get_int("Enter a number between 1 and 100")
    
    while attempt != rand:
        tries += 1
        if attempt < rand:
            attempt = get_int("Too Low!")
        else:
            attempt = get_int("Too High!")
    
    print "You got it in %i tries!" % tries
```

---

### Post by SteelDragon on 2008-09-16
> **pp. said:**
> @dragon

Does this help in any way?

Indeed it does, thanks. I can see how this is very beneficial. I'll look into it some more in anticipation of the next challenge.:razz:

---

### Post by krzysz00 on 2008-09-18
This is my C++ version. I haven't checked if there is one already, but here it goes

C++ Code:
```
#include<iostream>
#include<cstdlib>
#include<ctime>
using namespace std;

int main()
{
    srand (time(NULL));
    int guess;
    int number;
    number = rand() % 100 + 1;
    cout << "This is a number guessing game. When asked please guess what the mystery number is. The number will be beetween 1 and 100\n";
    int guesses = 0;
    while(guess != number)
    {
        cout << "Type your guess: ";
        cin >> guess;
        if (guess < number)
        {
            cout << "Guess is too low\n";
            guesses++;
        }
        if (guess > number)
        {
            cout << "Guess is too high\n";
            guesses++;
        }
        if (guess < 1 || guess > 100)
        {
            cout << "Guess must be beetween 1 and 100\n";
        }
    }
    guesses++;
    cout << "Yes the number is " << number << ".\n You win!\n It took you " << guesses << " guesses.\n";
    return 0;
}
```


Try it out. Trust me it's really fun (the first time).

---

### Post by scragar on 2008-09-18
here's a question, when does this one end? I'm sure the other competeitions didn't last this long, and I'm sure there arn't going to be many more submissions now(and if you say it ends in 1week or whatever you'll get those last responses in quicker).

---

### Post by LaRoza on 2008-09-18
> **scragar said:**
> here's a question, when does this one end? I'm sure the other competeitions didn't last this long, and I'm sure there arn't going to be many more submissions now(and if you say it ends in 1week or whatever you'll get those last responses in quicker).

None of them end. 

And I am sorry for not getting another one up. There will be as soon as I can.

---

### Post by kk0sse54 on 2008-09-18
> **LaRoza said:**
> None of them end. 

And I am sorry for not getting another one up. There will be as soon as I can.

No rush, you have really done a fantastic job in making these beginner challenges :)

---

### Post by jimi_hendrix on 2008-09-19
my attempt in pascal...this should compile on linux but i havnt checked

[PHP]program Project1;

var (*here is where we define variables*)
  answer : integer;
  guess : integer;
  tries : integer;
  input : integer; (*will be used for input in the game*)
begin
  randomize; (*needs to becalled for the random function to return true randoms*)
  writeln('enter the maximum number to guess');
  read(input);
  answer := random(input);(*:= is like = in most languages*)
  repeat(*game loop*)
    writeln('please enter your guess');
    read(input);
    tries := tries + 1;
    if input > answer then
      writeln('too high');
    if input < answer then
      writeln('too low');
    if input = answer then
      writeln('you win in ',tries,'tries');
  until input = answer;
end.
[/PHP]

---

### Post by cmay on 2008-09-19
```
my attempt in pascal...this should compile on linux but i havnt checked
```
what compiler do you use ?. i only know turbo pascal 5.5 or 7.0 on Freedos and the Free pascal compiler on linux. but it is nice to see another version in pascal :).

---

### Post by davidcaiazzo on 2008-09-19
My submission:
```

#include <iostream>
#include <ctime>
using namespace std;
int generaterandomnum();
void game(int&,int&);
void setupgame();

int main()
{
	setupgame();
}

int generaterandomnum(){
	//grabs the users current time
	srand(time(NULL));
	// returns a interger between 100 and 1
       return rand()%100+1;
}
void setupgame(){
	int number(generaterandomnum()), count(1);
	string playagain;
	game(number,count);
	
	if(count==1){
		cout<<"Congradulations! You guessed, " << number <<" which is\nthe right number!"
			<<" It only took you " << count <<" try! "<<endl;
	}
	else{
		cout<<"Congradulations! You guessed, " << number <<" which is\nthe right number!"
			<<" It only took you " << count <<" tries! "<<endl;
	}
	cout<<"Play again?";
	cin>>playagain;
	if(playagain=="Yes"||playagain=="yes"){
		system("clear");
		setupgame();
	}
	else{
		cout<<"GOOD BYE!";
		cin.get();
		return;
	}
}
void game(int& correctnum,int& count){
	int guess(0);
	cout<<"Please guess a number between 1-100: ";
	cin>>guess;
	if(guess==correctnum){
		return;
	}
	while(guess!=correctnum){
		count++;
		if(guess<correctnum){
			cout<<"Sorry you guessed too low!\nTry again:";
			cin>>guess;
		}
		else{
			cout<<"Sorry you guessed too high!\nTry again:";
			cin>>guess;
		}
	}
}

```

---

### Post by jimi_hendrix on 2008-09-19
> **cmay said:**
> what compiler do you use ?. i only know turbo pascal 5.5 or 7.0 on Freedos and the Free pascal compiler on linux. but it is nice to see another version in pascal

[GNU Pascal]("http://www.gnu-pascal.de/gpc/h-index.html")

i would love input on my pascal code if anyone knows the language well

---

### Post by Abras on 2008-09-20
> **LaRoza said:**
> And I am sorry for not getting another one up. There will be as soon as I can. Oh please do. I've been teaching myself Python through various books off and on for months. But this is really the first I've ever felt like I wrote a program --ya know, all by myself without any help from a book.  It was fun and definitely very rewarding. I can't wait to try out the other challenges. Thanks.

---

### Post by LaRoza on 2008-09-20
> **Abras said:**
> Oh please do. I've been teaching myself Python through various books off and on for months. But this is really the first I've ever felt like I wrote a program --ya know, all by myself without any help from a book.  It was fun and definitely very rewarding. I can't wait to try out the other challenges. Thanks.

Maybe I can con a bunch of newbs into doing the debugging on sysres...

Would that be ethical :-)?

Oh well. I have an idea for the next one. I will try to get it up tomorrow (or rather, today technically)

---

### Post by davidcaiazzo on 2008-09-20
My python submission for this one, figured I could use the practice:

```

#!/usr/bin/env python
import random
def generaterandomnum():
	return random.randint(1,100)
def game(correctnum,count):
	print "Please guess a number between 1-100: "
	guess=int(raw_input())
	if guess==correctnum:
		return
	while guess!=correctnum:
		count+=1
		if guess<correctnum:
			print "Sorry you guessed too low!\nTry again: "
			guess=int(raw_input())
		if guess>correctnum:
			print "Sorry you guessed too high!\nTry again: "
			guess=int(raw_input())
	return count
def setupgame():
	count=1
	correctnum=generaterandomnum()
	count=game(correctnum,count)
	if count==1:
		print "Congradulations! You guessed, ",correctnum," which is"
		print "the right number! It only took you ",count," try!"
	else:
		print "Congradulations! You guessed, ",correctnum, "which is"
		print "the right number! It only took you ",count," tries!"
	print "Play again? "
	playagain=raw_input()
	if(playagain=="Yes" or playagain=="yes"):
		setupgame()
	else:
		print "GOOD BYE!"

setupgame()

```

---

### Post by cmay on 2008-09-20
> 
i would love input on my pascal code if anyone knows the language well 
i have tested it on free pascal when i got home just now. there was two errors or rather warning messages i have fixed. i do not know if they would have been present on gnu pascal as i have never tried that compiler. 
its just been too long since i used pascal so i cant comment much more on it since i really do not remember much pascal.
i commented the error messages i got when compiling ands also where i fixed it in delfhi style comments.
[PHP]program Project1;
// i used delfhi comments to point out my changes in code.
var (*here is where we define variables*)
  answer : integer;
  guess : integer;// error message local variable "guess" is not used 
  tries : integer; // error message local variable tries does not seem to be intialized
  input : integer; (*will be used for input in the game*) 
  begin
    tries:=0;// fixed by initialize the tries set to 0 as start count value
    randomize; (*needs to becalled for the random function to return true randoms*)
    writeln('enter the maximum number to guess');
    read(guess);// fixed  by using the guess var this way :)
    answer := random(guess);(*:= is like = in most languages*)
  repeat(*game loop*)
    writeln('please enter your guess');
    read(input);
    tries := tries + 1;
  if input > answer then
      writeln('too high');
  if input < answer then
      writeln('too low');
  if input = answer then
      writeln('you win in ',tries,'tries');
  until input = answer;
end.[/PHP]

---

### Post by jimi_hendrix on 2008-09-20
@cmay

thanks for pointing those out

the guess thing was because i did it late at night and was tired

the other one was because when i put the post up i didnt check it on linux box and basically after the loopended the program exited in my IDE (i cant stand cmd prompt compiling in windows) without displaying the end text so i didnt notice it not doing guess count right

EDIT: also, would you recommend me pascal as something to keep looking into (i know you havnt used it in a long time)?

> 
Oh well. I have an idea for the next one. I will try to get it up tomorrow (or rather, today technically)

great...these help me use what i learn until i figure out my own projects to begin

---

### Post by MacUntu on 2008-09-20
Better late than never:

```
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.Random;

/**
 * Challenge 5.
 * @author MacUntu
 *
 */
public class C5 {

    /**
     * Used to retrieve user input.
     */
    private BufferedReader br;

    /**
     * The number to guess.
     */
    private int guessMe;

    /**
     * The user's guess.
     */
    private int guess;

    /**
     * Count of guesses made.
     */
    private int used;

    /**
     * Constructor. Initializes the buffered input stream reader, 
     * the number to guess and the count of guesses. 
     */
    public C5() {
	br = new BufferedReader(new InputStreamReader(System.in));
	guessMe = new Random().nextInt(100) + 1;
	used = 0;
    }

    /**
     * Main loop.
     */
    public void run() {

	System.out.println("=== Guess a number between 1 and 100! ===\n");

	while (true) {

	    System.out.print("Enter guess: ");

	    try {
		checkGuess(getGuess());
	    } catch (NumberFormatException nfe) {
		System.out
		.println("Invalid number! Input must be a number between 1 and 100.");
	    } catch (IOException ioe) {
		ioe.printStackTrace();
		System.exit(1);
	    }
	}
    }

    /**
     * Get guessed number.
     * @return The guessed number.
     * @throws IOException
     * @throws NumberFormatException
     */
    private int getGuess() throws IOException, NumberFormatException {
	guess = Integer.parseInt(br.readLine());
	// no exception thrown => increase guess count
	used++;
	return guess;
    }

    /**
     * Checks if the given guess is the number to find.
     * Exits on success.
     * @param guess The number to check
     */
    private void checkGuess(int guess) {
	switch (Integer.signum(guess - guessMe)) {
	case 0: // success, end game
	    System.out.println("Number found after " + used
		    + " guesses!\n\nBye!");
	    System.exit(0);
	case 1:
	    System.out.println("Too big.");
	    break;
	case -1:
	    System.out.println("Too small.");
	}
    }

    /**
     * Main method.
     * @param args
     */
    public static void main(String[] args) {
	new C5().run();
    }
}
```

Yes, it IS doable in 100+ lines. :lolflag:

---

### Post by cmay on 2008-09-20
> EDIT: also, would you recommend me pascal as something to keep looking into (i know you havnt used it in a long time)?
yes i would.not as the main language but as a language you just can say you know. why i think this is maybe since it was my first language and i also see some things as advantages that others may not thinks of as such.other than learning it just to learn a language it is a good teaching language but its also been used by proffesionals.i do not think there not much production code done in pascal no more but it has been a de-facto standard.there is still people that uses the lazarus IDE to make games using free pascal. there is lots of books on pascal . it has been used widely in schools for teaching programing so its relative easy to find books examples source code for pascal. there is also still borland object pascal used by hobbyist and professionals but just not so much as it has been. the most downloaded open source c++ IDE dev-cpp  was written in borlands object pascal. other than that pascal can be used for many things as example the lazarus ide has many delfhi like units so one can use it to create database systems pretty easy.lazarus is a development enviroment where you have a gui designer so one needs to know some pascal to make the gui work but the design is just drag and drop. i have not done something like that but just read about it in a case story on the lazarus site.  it is an older language but one can argue that it is good to know a older language like cobol fortran pascal just for the sake of knowing about it.in Denmark where i live we have used pascal up to 2005 i think in university as i found a lot of notes on the net from 2006 as the last year before it was replaced by c . i do not have any education or studied but i look for tutorials and education on the internet and i found many tutorials and free source code , even five entire operative systems written in pascal on source forge. so if you could find a popular ide like dev cpp or one of the many games that has been written in pascal and port it to linux i would be happy that you know pascal. i liked pascal very much but i cant remember many things so i forget the language i am not learning at the moment .

---

### Post by jimi_hendrix on 2008-09-20
thanks for the input...

was just curious because my uncle swears by it...

---

### Post by cmay on 2008-09-20
> thanks for the input...

was just curious because my uncle swears by it... 

[http://www.bsdg.org/SWAG/index.html](http://www.bsdg.org/SWAG/index.html)

i found a link for you to a lot of turbo pascal free sources and links.if you want to study the examples then you should try the free pascal compiler and compile in turbo pascal 7.0 mode .many of these examples just compiles and run.i think maybe a windows computer or dos system is better for many of these examples but you can maybe learn from it. i have and old computer with free dos and turbo pascal on it where i plan to relearn pascal again and write some small games for free dos. could be a  great hobby activity but i need some time to go trough my old pascal books again.

---

### Post by jimi_hendrix on 2008-09-20
thanks again

---

### Post by cmay on 2008-09-20
no prob.
i will recommend the free pascal compiler as i think it is the best choice for a compiler being free and having over 18000 pages of documentation. so if one knows the pascal language everything is there to start with and its in a linux ,mac ,dos ,and windows version. lazarus is the delfhi like ide where you greate gui by dragging and dropping objects on a form write a procedure and then design your projects just like delfhi works. i would be happy to see someone use it since its a good project and there ís really done a lot of work on it other than that i am always happy to help.  good luck with it.

---

### Post by jimi_hendrix on 2008-09-21
> **cmay said:**
> no prob.
lazarus is the delfhi like ide where you greate gui by dragging and dropping objects on a form write a procedure and then design your projects just like delfhi works

ya i use lazarus in windows because it compiles object and regular pascal...but in linux i would just use a CLI compiler

---

### Post by pp. on 2008-09-21
> **davidcaiazzo said:**
> 

```

def game(correctnum,count):
	print "Please guess a number between 1-100: "
	guess=int(raw_input())
	[B]if guess==correctnum:
		return[/B]
	while guess!=correctnum:
		count+=1
		if guess<correctnum:
			print "Sorry you guessed too low!\nTry again: "
			**guess=int(raw_input())**
		if guess>correctnum:
			print "Sorry you guessed too high!\nTry again: "
			**guess=int(raw_input())**
	return count

```

I wonder if you actually ran your program.

I might be mistaken as I have yet to code any Python code. However, at a first glance I appear to find two problem areas:

The ***if*** statement just in front of the ***while*** does not return a value if the condition is met. Also, it is perfectly redundant since the ***while*** statement would fall through in that case anyway.

Also, you might want to check the placement of the statements which read the next guess within the ***while***. I would think that your program outputs a wrong count if you enter first a low and then a high guess.

The structure of your program is very clean and easy to follow. I would not have been able to spot those two issues at a glance if that was not the case. You'd get points on that count, anyway.

---

### Post by cybermacro on 2008-09-30
Aswell better late than never, here is my entry using C++, which i've just started. :-)

```
#include <iostream>
#include <cstdlib>
#include <ctime>
using namespace std;
void startguess(int num);
int main()
{
	srand((unsigned)time(0));
	startguess((rand()%100)+1);
	return 0;
}
void startguess(int num)
{
	int guess=0, guesses=0;
	while(guess != num && guesses++ != -1){	
		cout << "Guess the number, 1-100: ";
		cin >> guess;
		if(guess > num) cout << "Not so high!\n";
		else if(guess < num) cout << "That's too low!\n";
	}
	cout << "You're damn right. It took you " << guesses << " guesses.\n";
}
```

---

### Post by Canis familiaris on 2008-10-07
I suppose I am involving in necromancy now. But Here We Go then:

```
[color=#408080]*#!/usr/bin/python*[/color]
[color=#008000]**print**[/color][color=#BA2121]"""#################
# Guessing Game #
#################"""[/color], [color=#BA2121]'[/color][color=#BB6622]**\n\n**[/color][color=#BA2121]'[/color]

[color=#008000]**import**[/color] [color=#0000FF]**random**[/color]

numGuess [color=#666666]=[/color] [color=#666666]0[/color]
tries [color=#666666]=[/color] [color=#666666]0[/color]

RandomNum [color=#666666]=[/color] random[color=#666666].[/color]choice([color=#008000]range[/color]([color=#666666]1[/color],[color=#666666]101[/color]))


[color=#008000]**print**[/color] [color=#BA2121]"Random Number Generated[/color][color=#BB6622]**\n\n**[/color][color=#BA2121]"[/color]

[color=#008000]**while**[/color] [color=#008000]True[/color]:
	numGuess [color=#666666]=[/color] [color=#008000]input[/color]([color=#BA2121]"Enter the number which you think the computer has selected: "[/color])
	tries[color=#666666]+=[/color][color=#666666]1[/color]
	
	[color=#008000]**if**[/color] numGuess [color=#666666]==[/color] RandomNum:
		[color=#008000]**print**[/color] [color=#BA2121]'[/color][color=#BB6622]**\n**[/color][color=#BA2121]Congratulations. You selected the right number'[/color]
		[color=#008000]**break**[/color]
	[color=#008000]**elif**[/color] numGuess [color=#666666]>[/color] RandomNum:
		[color=#008000]**print**[/color] [color=#BA2121]'[/color][color=#BB6622]**\n**[/color][color=#BA2121]You guessed higher than the number actually is...'[/color]
	[color=#008000]**else**[/color]:
		[color=#008000]**print**[/color] [color=#BA2121]'[/color][color=#BB6622]**\n**[/color][color=#BA2121]You guessed lower than than the number actually is...'[/color]
		
	
[color=#008000]**print**[/color] [color=#BA2121]"You guessed the number"[/color], RandomNum, [color=#BA2121]" in "[/color], tries, [color=#BA2121]" attempts."[/color]
		
		

```

I must mention I did not know how to randomize and I took the idea from cardboardtoast. I guess random.choice(range(1,101) will randomly give a number b/w 1 and 100 and its second argument is exclusive.

BTW It's interesting that we don't need to randomize the timer. Cool.

---

### Post by Bichromat on 2008-10-07
> **Anurag_panda said:**
> I must mention I did not know how to randomize and I took the idea from cardboardtoast. I guess random.choice(range(1,101)) will randomly give a number b/w 1 and 100 and its second argument is exclusive.

python has random.randint(1,100).

Here's the official module documentation index: [http://docs.python.org/modindex.html]("http://docs.python.org/modindex.html")

---

### Post by jimi_hendrix on 2009-01-18
i love scheme

[PHP]
(define (getmax)
  (begin
    (flush-output)
    (display "hello, pick a number that will be top of the guessing range\n")
    (flush-output)
    (newline)
    (read)))

(define (check number)
  (define input 0)
  (display "what is your guess?")
  (newline)
  (flush-output)
  (set! input (read))
    (cond ((< input number) (display "too low!") (newline) (check number))
	  ((= input number) (display "you win!") (newline))
	  ((> input number) (display "too high!") (newline) (check number))))

(define (game) (define input 0) (check (random (getmax))) (display "play again"))

;this is a comment - this part simply calls the game method
(begin (game))
[/PHP]

---

### Post by TheAxeR on 2009-01-18
Using python3 .

[PHP]
#!/usr/bin/python3

import random



target = random.randint(1,100)
test = -1
attempts = 0



def check_int(user_num):
    ''' Verify that the input is an integer'''
    try:
        user_num = int(user_num)
        return True
    except TypeError:
        print(' Please input an integer.')
        return False
    except ValueError:
        print(' Please input an integer.')
        return False
        
def check_range(user_num):
    ''' Verify that the input is between 1 and 100'''
    good_guess = True
           
    if user_num <= 0:
        print(' Please input an integer between 1 and 100.')
        good_guess = False
           
    if user_num > 100:
        print(' Please input an integer between 1 and 100.')
        good_guess = False
    
    return good_guess

def check_guess(user_num):
    '''Test the user guess and provide feed back'''
    if check_range(user_num):
        if user_num < target:
            print('Guess Higher:')
            
        if user_num > target:
            print('Guess Lower:')
            
        if user_num == target:
            print(' Congrats you guessed the correct number ' + str(target) +'.')
            
            if attempts > 1:
                print(' It took you ' + str(attempts) +' attempts.')
            else:
                print( 'It took you one try!')
            
    return user_num

# The actual game takes place below.

print(' In this game you must guess the randomly selected number between 1 and 100.')
print(' Only input integers between 1 and 100.\n The game will stop after you \
have made a correct guess.\n \n Make a guess:')

    
while test != target:
    guess = input()
    attempts = attempts + 1
    if check_int(guess):
        test = check_guess(int(guess))

[/PHP]

---

### Post by module0000 on 2009-01-18
Better late than never I suppose, did it in C.
Use "gcc game.c -o game", then "./game" to run

[PHP]#include <stdio.h>
#include <stdlib.h>

int main(int argc, char** agv)
{
	time_t seconds;
	time(&seconds);
	srand((unsigned int) seconds);
	int correctNum = rand() % (100 - 1);
	int uinput;
	int tries;

printf("\nYour objective is to guess a random number between 1 and 100.\n(our seed is %d by the way)\n\n", seconds);
	for(tries=1;tries <= 10;tries++)
	{
		printf("Enter a number: ");
		scanf("%d", &uinput);
		if (uinput < correctNum) printf("too low, %d guesses left\n\n", (10 - tries));
		if (uinput > correctNum) printf("too high, %d guesses left\n\n", (10 - tries));
		if (uinput == correctNum)
		{
			printf("Correct!  You used %d guesses\n", tries);
			return 0;
		}	
	}
	printf("You fail!  The number was %d!", correctNum);
	return 0;
}
[/PHP]

---

### Post by HotCupOfJava on 2009-01-18
A bit of irony: it looks like LaRosa wants you to write code to make the USER do the binary search! <chuckle>

---

### Post by bgs100 on 2009-01-24
Comments/Advice Welcome

[PHP]#!/usr/bin/python
import random
guess='0'
tries=0
num=random.randrange(1,100)
#the whole guessing part
while guess != 'quit' and int(guess) != num:
	guess=raw_input("Try to guess the number: ")
	if int(guess) > num:
		print "Too high"
	if int(guess) < num:
		print "Too low"
	tries=tries+1
#if they get it
if guess != 'quit':
	print "\nYou got it in %i tries\n" % (tries)[/PHP]

---

### Post by bgs100 on 2009-01-24
Update:
[PHP]#!/usr/bin/python
import random
guess='0'
tries=0
range1=int(raw_input("Enter the first part of the range: "))
range2=int(raw_input("Enter the second part of the range: "))
num=random.randrange(range1,range2)
#the whole guessing part
while guess != 'quit' and int(guess) != num:
	guess=raw_input("Try to guess the number: ")
	if int(guess) > num:
		print "Too high"
	if int(guess) < num:
		print "Too low"
	tries=tries+1
#if they get it
if guess != 'quit':
	if tries != 1:
		print "\nYou got it in %i tries\n" % (tries)
		exit()	
	print "\nYou got it in 1 try\n"[/PHP]

---

### Post by pp. on 2009-01-25
> **bgs100 said:**
> Comments/Advice Welcome

You seem to take it for granted that int('quit') is valid and evaluates to zero. I don't know if this holds true for Python. It certainly does not work in many other languages and can cause lots of grief.

---

### Post by nvteighen on 2009-01-25
> **bgs100 said:**
> Comments/Advice Welcome

[PHP]#!/usr/bin/python
import random
guess='0'
tries=0
num=random.randrange(1,100)
#the whole guessing part
while guess != 'quit' and int(guess) != num:
	guess=raw_input("Try to guess the number: ")
	if int(guess) > num:
		print "Too high"
	if int(guess) < num:
		print "Too low"
	tries=tries+1
#if they get it
if guess != 'quit':
	print "\nYou got it in %i tries\n" % (tries)[/PHP]

Good. Though you could make it a bit more concise: notice that you're checking twice for the same condition (guess != 'quit')... that can be changed.

---

### Post by eightmillion on 2009-01-25
I realize that this isn't following most, if any of the guidelines, but I just wrote this for my own entertainment. I really like writing these ridiculous lambda functions. This one is even recursive.

```

#!/usr/bin/env python
import sys,random
guess=lambda x,num=random.randrange(1,100),f=[1]: (lambda y,g=lambda t:sys.stdout.write(t): map(eval,["g(\"Too high\\n\")",
"f.__setitem__(0,f[0]+1)","guess(int(raw_input(\"Guess: \")))"]) if y > num else map(eval,["g(\"Too low\\n\")",
"f.__setitem__(0,f[0]+1)","guess(int(raw_input(\"Guess: \")))"]) if y < num else g("You guessed it in %d %s!\n" %
(f[0],["tries","try"][f[0]==1])))(x);guess(int(raw_input("Guess: ")))

```

Edit: or just paste in a terminal:
```

python -c 'import sys,random;guess=lambda x,num=random.randint(1,100),f=[1]: (lambda y,g=lambda t:sys.stdout.write(t): map(eval,
["g(\"Lower\\n\")","f.__setitem__(0,f[0]+1)","guess(int(raw_input(\"Guess: \")))"]) if y > num else map(eval,["g(\"Higher\\n\")",
"f.__setitem__(0,f[0]+1)","guess(int(raw_input(\"Guess: \")))"]) if y < num else g("You guessed it in %d %s!\n" % (f[0],["tries",
"try"][f[0]==1])))(x);guess(int(raw_input("Guess: ")))'

```

---

### Post by scragar on 2009-01-25
> **bgs100 said:**
> Update:
[PHP]#!/usr/bin/python
import random
guess='0'
tries=0
range1=int(raw_input("Enter the first part of the range: "))
range2=int(raw_input("Enter the second part of the range: "))
num=random.randrange(range1,range2)
#the whole guessing part
while guess != 'quit' and int(guess) != num:
	guess=raw_input("Try to guess the number: ")
	if int(guess) > num:
		print "Too high"
	if int(guess) < num:
		print "Too low"
	tries=tries+1
#if they get it
if guess != 'quit':
	if tries != 1:
		print "\nYou got it in %i tries\n" % (tries)
		exit()	
	print "\nYou got it in 1 try\n"[/PHP]

Can I recommend you use a few functions and break up the content, Part of the idea for structured code is to put the things you are most likely to want to change separate from the rest of the code, that is why in my first try version ( [http://ubuntuforums.org/showpost.php?p=5689328&postcount=35](http://ubuntuforums.org/showpost.php?p=5689328&postcount=35) ) I used a function for writing output, this would be easy to change in future if need be, How would you easily edit that code if you, for example, wanted to build a gui? print would not be your source of presenting information, and I doubt very much raw_input would be either, although a lot of the logic would remain the same.

---

### Post by bruce89 on 2009-01-25
Just for fun, JavaScript using [Seed]("http://live.gnome.org/Seed"):

[PHP]Seed.import_namespace("GLib");
Seed.import_namespace("readline");

var target = GLib.random_int_range(0, 100);

while (true)
{
	var guess = readline.readline("Guess a number between 0 and 100 ");

	if (guess < target)
		Seed.print("Too low");
	else if (guess > target)
		Seed.print("Too high");
	else
	{
		Seed.print("Correct");
		break;
	}
}[/PHP]

---

### Post by hanniph on 2009-01-30
'Diving into python' at the moment, so decided to write some snippets. Not as simple as it could be :KS ```
 
#!/usr/bin/python

import sys
from random import randrange

# main
upper = 100  #random number is generated from range of 1 .. upper
tries = 0    #how many guesses the client has made so far
guess = -1       # users guess
 
#checking whether command line arguments were supplied
if len(sys.argv) > 1:
    if sys.argv[1].isdigit() and int(sys.argv[1]) > 1:
        upper = int(sys.argv[1])
        print "OK, upper limit is set, now let's start the game"
    elif sys.argv[1] == '--help' or sys.argv[1] == '-h':
        print "Number guessing game. v0.1a Made by Hanniph\nDefault upper limit for guessing is set to 100, however you can set it to antoher number (higher than 1) by passing it as a command line argument:\n\tpython game.py 1000"
        sys.exit()
    else:
        print "Unknow command line argument. See -h for explanation"
        sys.exit()

#------ The Game ----------
answer = randrange(1, upper+1)  #get random number
print "Guess number in range from 1 to {0}".format(upper)
while answer != guess:
    guess = input("Enter your guess\t")
    tries = tries + 1
    if guess > answer:
        print "Wow! Too high"
    elif guess < answer:
        print "To low.."
    elif guess == answer and tries == 1:
            print "OMG! You made it from the first guess!"
    else:
        print "Grats! You Won!"
        print "It took {0} guesses for You to make".format(tries)


```

---

### Post by Buuntu on 2009-08-30
I could have probably added code to give an error if the input wasn't an integer, or if it was out of the range.  I didn't think it was really necessary though.
```
#!/usr/bin/python
import random

print '''Guessing Game
------------------------------------------------------------------------------

Number has been set... Guess a number(integer) between 1 and 100.
'''  
x = 0 #Condition for while loop
rand_number = random.randint(1, 100) 
count = 0  #Keeps track of the number of guesses
while x == 0:
    number = int(raw_input("> "))
    if number > rand_number:
        print "Lower."
        count += 1
    elif number < rand_number:
        print "Higher."
        count += 1
    else:
        count += 1
        print "Congratulations, the number was " + str(rand_number) + "!"
        if count == 1:
            print "Wow, you guessed it correctly on your first try!!!!"
        else:
            print "It took you " + str(count) + " guesses. "
        x = 1 # Exits while loop

raw_input("\n(Press <Enter> to exit...)")
```

---

### Post by Bodsda on 2009-08-31
> **hanniph said:**
> 'Diving into python' at the moment, so decided to write some snippets. Not as simple as it could be :KS ```
 
#!/usr/bin/python

import sys
from random import randrange

# main
upper = 100  #random number is generated from range of 1 .. upper
tries = 0    #how many guesses the client has made so far
guess = -1       # users guess
 
#checking whether command line arguments were supplied
if len(sys.argv) > 1:
    if sys.argv[1].isdigit() and int(sys.argv[1]) > 1:
        upper = int(sys.argv[1])
        print "OK, upper limit is set, now let's start the game"
    elif sys.argv[1] == '--help' or sys.argv[1] == '-h':
        print "Number guessing game. v0.1a Made by Hanniph\nDefault upper limit for guessing is set to 100, however you can set it to antoher number (higher than 1) by passing it as a command line argument:\n\tpython game.py 1000"
        sys.exit()
    else:
        print "Unknow command line argument. See -h for explanation"
        sys.exit()

#------ The Game ----------
answer = randrange(1, upper+1)  #get random number
print "Guess number in range from 1 to {0}".format(upper)
while answer != guess:
    guess = input("Enter your guess\t")
    tries = tries + 1
    if guess > answer:
        print "Wow! Too high"
    elif guess < answer:
        print "To low.."
    elif guess == answer and tries == 1:
            print "OMG! You made it from the first guess!"
    else:
        print "Grats! You Won!"
        print "It took {0} guesses for You to make".format(tries)


```

I have not had a chance to test this out yet, but your code has intrigued me. I have never seen the use of {0}, 

What does this do? 
What is it called?
How does it know which variable it should be referencing?

Thanks,
Bodsda

---

### Post by veda87 on 2009-08-31
Here is my C++ program..... ```
#include <iostream>
#include <cstdio>
#include <cstdlib>
#include <ctime>

using namespace std;

/*program starts here */
int main(void)
{
        srand(time(0));
        int RandNumber = (rand()%(100-1)) + 1; /* random number generation */
        char Input[10];
        int UserInput;
        int Guesses = 0;

        while(1) {
                /* get the user input */
                cout << "Enter the input between (1-100): ";
                fgets(Input, 10, stdin);

                Guesses++;

                if(!(UserInput = atoi(Input)) | UserInput < 1 | UserInput > 100) {
                        cout << " Enter the correct input" << endl;
                        Guesses = 0;
                        continue;
                }

                if(UserInput == RandNumber) {
                        cout << " Correct guess... U win.." << endl;
                        cout << " No of Guesses: " << Guesses << endl;
                        return 0;
                } else if (UserInput > RandNumber) {
                        cout << "    HIGHER " << endl;
                } else if (UserInput < RandNumber) {
                        cout << "    LOWER " << endl;
                }

        }
        return 1;
}  /* end of main */

```

---

### Post by hanniph on 2009-08-31
> **Bodsda said:**
> I have not had a chance to test this out yet, but your code has intrigued me. I have never seen the use of {0}, 

What does this do? 
What is it called?
How does it know which variable it should be referencing?

Thanks,
Bodsda

That's just a new way of string formatting. You should take a look at the [_str.format_]("http://docs.python.org/library/stdtypes.html#str.format") method.

---

### Post by flyingsliverfin on 2009-12-31
bit out of date but:

```
#! /bin/python
again = 'y'

import random
while again != 'n':
	guess = 0
	num_to_guess = random.randint(1,100)
		
	counter = 0
	while guess != num_to_guess:
		guess = raw_input('guess between 1 and 100 (inclusive): ')
		guess = int(guess)
		if guess < num_to_guess:
			print('higher')
			counter = counter +1
			continue

		if guess > num_to_guess:
			print('lower')
			continue
			counter = counter +1
		else:
			counter = counter +1
		break
	
	print('you WIN!!! You took',counter,'turns to guess it')
	again = raw_input('play again (y/n): ')




```

---

### Post by caelestis2 on 2010-01-01
Heh. I wrote this for school a while back, and as such, of course the school uses java.

[PHP]import java.util.Random;
import java.util.Scanner;
import static java.lang.System.out;

public class NumberGuessing {
	public static void main(String [] args) {
		Scanner jin = new Scanner(System.in);

		int number = (new Random()).nextInt(100)+1;
		int guess, numGuesses = 1;

		while(true) {
			out.print("Guess a number: ");
			guess = jin.nextInt();
			if (guess > number) out.println("Too high");
			else if (guess < number) out.println("Too low");
			else break;
			++numGuesses;
		}
		out.println("You took " + numGuesses + " tries to guess the number " + number);
	}
}[/PHP]


And it's inverse problem (making the computer guess your number) with a maximum of 7 attempts.

[PHP]import java.util.Scanner;
import static java.lang.System.out;

public class NumberGuessing {
	public static void main(String [] args) {
		Scanner jin = new Scanner(System.in);
		out.print("Think of a number between 1-100,\nthen enter h for too high, l for too low and e for equal\n\n");

		int number = 50, numGuesses = 1;
		int lowBound = 0, highBound = 101;
		while(true) {
			out.print("Is " + number + " higher or lower than your number, or equal? ");
			char g = (jin.next()).charAt(0);

			if (g == 'h') {
				highBound = number;
				number -= (highBound-lowBound)/2;
			}
			if (g == 'l') {
				lowBound = number;
				number += (highBound-lowBound)/2;
			}
			if (g == 'e') break;
			++numGuesses;
		}
		out.println("It took me " + numGuesses + " tries to guess the number " + number);
	}
}
[/PHP]

Edit: oh, and comments are more than welcome. If you could make your own version of the second, without looking to much at mine, I would be interested. In C, C++, javascript, php, python, java I will understand.

---

### Post by lopho on 2010-06-08
hope this isnt necro, but here comes mine, in php:

[PHP]
<!--
- random number guessing game
- © Philipp Kleinhenz, 2010
- licensed under GPL v3
-->
<?php
if(!isset($_POST['try'])){
    $try=0;
    echo "<br /><br />";
}
else{
    $try=$_POST['try']+1;
    echo "Number of tries: ".$try."<br />";
    if($_POST['rand']>$_POST['number']){echo "Higher than ".$_POST['number']."!";}
    elseif($_POST['rand']==$_POST['number']){echo "";}
    else{echo "Lower than ".$_POST['number']."!";}
}
if(!isset($_POST['rand'])){
    $rand=rand(1,100);
}
else{$rand=$_POST['rand'];}
if((isset($_POST['number']))&&($_POST['number']==$_POST['rand'])){
    echo "You have guessed the number! It was ".$_POST['rand']."!
    <br /><br /><a href=''>Play Again!</a>";
}
else{
    echo "<form method='post'>Guess the Number (1 - 100):
    <input type='text' name='number' maxlength='3' size='3' />
    <input type='hidden' name='rand' value='".$rand."' />
    <input type='hidden' name='try' value='".$try."' />
    <input type='submit' value='Guess' /></form>";
}
?>
[/PHP]

---

### Post by texaswriter on 2010-08-23
Haha, really late entry in C#. I use MonoDevelop. Should compile fine in an empty console project. This should work in Visual Studio as well. 

[PHP]using System;

class guessNumber
{
    /*
     * guess_main creates a random number from 1 to 100 and iteratively takes input from the user, giving regular feedback of higher/lower. 
     */
    public static void guess_main()
    {
         string[] positions = new string[10] {"first", "second", "third", "fourth", "fifth", "sixth", "seventh", "eighth", "ninth", "tenth"}; //Text array for printing
        Random random = new Random(); //initializes random generator
        int i=0,j=0,k=0; // i = loop / counter; j = guess; k = random;
        
        while(k==0) k = random.Next(100); // 1<=k<=100
        
        //Console.WriteLine("DEBUG MESSAGE: {0}",k);
        
        while(j != k && i<11) //processes input; maximum of 10 tries
        {
            Console.WriteLine("");
            Console.Write("Enter your {0} guess :", positions[i]);
            j=0;
            while(j==0) j = input_Number(Console.ReadLine());
            i++;
            
            if(j<k)
            {
                Console.WriteLine("");
                Console.WriteLine("Your guess is less than the blind number.");
            }
            else if(j>k)
            {
                Console.WriteLine("");
                Console.WriteLine("Your guess is higher than the blind number.");
            }
                
        }
        
        if(i==11) 
        {
            Console.WriteLine("");
            Console.WriteLine("Challenge yourself to guessing the next one in 10 guesses or less. Please try another number."); //Friendly kick in the butt
        }
        else if(j==k)
        {
            Console.WriteLine("");
            Console.WriteLine("Congratulations on guessing the number on your {0} try. The blind number is {1}.", positions[i-1], k);
        }
    }
    
    /*
     * input_number takes a string and returns a value. By design, a return value of 0 means a non numerical input, though a value of 0 is genuinely possible
     */
    public static int input_Number(string processMe)
    {
        if(processMe!=""&&char.IsDigit(processMe,0))
            return int.Parse(processMe);
        else
            return 0;
    }
}



class MainClass
{
    public static void Main (string[] args)
    {
        int i=0;
        
        while(i == 0) //loops until user enters some number other than 0
        {
            guessNumber.guess_main();
            Console.WriteLine("");
            Console.Write("Type 0 <Enter> to continue, any other number <Enter> to Exit :");
            i=guessNumber.input_Number(Console.ReadLine());
        }
    }
}


 [/PHP]

---

### Post by JackDarkStone on 2011-06-08
```


#include <cstdlib>
#include <iostream>
#include <ctime>

using namespace std;


int main(int argc, char *argv[])
{
    int numTries = 0;
    int guess;
    int randNumber;
       
    cout << "Welcome to guess my number.\n\n";
    system("PAUSE");
    system("CLS");
    
    cout << "The game is simple. The computer will think of a number from one to 100 and you\n";
    cout << "will try guessing what the number is. If the number you gave is too high or too low,";
    cout << "we will tell you so and you can try again. Let's begin\n\n";
    system("PAUSE");
    system("CLS");
    
    srand(time(0));
    randNumber = rand() % 100 + 1;
    
    while(guess != randNumber){
                
    cout << "Your guess: ";
    cin >> guess;
    
        if(guess > randNumber){
             cout << "Too high.\n\n";
             system("PAUSE");
             system("CLS");
             
        }
        if(guess == randNumber){
            cout << "THAT'S IT! YOU GUESSED!\n\n";
            system("PAUSE");
            system("CLS");
            cout << "Good bye.\n\n";
            system("PAUSE");
            return 0;
        
             
        }
        if(guess < randNumber){
            cout << "Too low.\n\n";
            system("PAUSE");
            system("CLS");
                 
        }
                
                
    }
    
    
    system("PAUSE");
    return 0;
}

    



```

---

### Post by Elfy on 2011-06-09
closed - old thread - old challenge

---

### Post by bapoumba on 2011-06-10
[http://ubuntuforums.org/showthread.php?t=1778728](http://ubuntuforums.org/showthread.php?t=1778728)
[http://ubuntuforums.org/showthread.php?t=1778936](http://ubuntuforums.org/showthread.php?t=1778936)

Sounds reasonable to reopen. Sorry Mr. Piskie :)

---

### Post by Elfy on 2011-06-11
> **bapoumba said:**
> [url] Sorry Mr. Piskie :)

Welcome :)

---

### Post by Thewhistlingwind on 2011-06-11
Ten lines. Common Lisp.

```
; Don't count comments. Don't count whitespace.

; Set's the number to guess.


(set 'ran_num1 (random 100)) (set 'count1 0)

(defun mainloop () "Plays a guessing game"
(set 'input1 (read))

; Checks for a win
(cond
((< input1 ran_num1) (print "Too low"))
((> input1 ran_num1) (print "Too high"))
((eql input1 ran_num1) (print "You guessed it!!!")))

(set 'count1 (+ count1 1)) (print count1)
(mainloop))

(mainloop)

```PS. The first comment isn't bragging (It's not that good.......), it's "Don't tell me it's not ten lines cause I formatted."

---

### Post by CuracaoThe on 2011-07-10
I know, I'm late, but you didn't close the thread, so here's my solution, written in Ruby:

[PHP]
puts "Guess the secret number (from 1 to 100):"
  secret_number = rand(100) + 1
  number_of_attempts = 0
  loop do
    prediction = gets.to_i
    number_of_attempts += 1
    case prediction <=> secret_number
    when -1 then puts "The secret number is higher."
    when  0 then puts "You win! Yes, it was #{secret_number}.",
                      "It took you only #{number_of_attempts} attempts!"
                 break
    when  1 then puts "The secret number is lower."
  end
end
[/PHP]

---

### Post by jerenept on 2011-09-19
This is my entry, written in Pascal. I don't have the compiler with me now, as I'm on my brother's computer, but I believe it will compile and run corrently in [FreePascal]('http://freepascal.org')

```

program randomgame;
uses crt;
var
   tries, num, input: integer;

begin
randomize; {Apparently it is necessary to do this to use random numbers}
tries:=0; num:=0; input:=0;
num:=random(100)+1;
writeln('Number Guessing Game');
repeat begin
      writeln('Guess my number');
      readln(input);
      if num < input then
         writeln ('Too High');
      if num > input then
         writeln('Too Low');
tries:=tries+1; end;
until num=input;
writeln('Correct! You took ',tries,' attempts.');
readkey;
end.
```

Sorry for being so late :P .

---

### Post by dasjew on 2012-04-24
I'm sure I'm late, but I've only been programming for three weeks.... Sooo here's my submission is Python.

#Guess the number game
#
#Guess a number between 1 and 100 and record and state the amount of tries.
#
#Dasjew 4/24/12

import random
import sys
import time

if __name__ == "__main__":
    #get random number and initial variables
    global num
    global guess
    global tries
    num = random.randint(1, 100)
    guess = 0
    tries = 0
    
    #Gives the user the basic instructions to the game
    def instructions():
        print "\n\nIn this game you will be guessing a number between 1 and \
100.  You will receive 'higher' and 'lower' hints. Try to guess the number in \
as few tries as possible! Enjoy!\n\n"

    #Set up the while loop, and get an int from the user
    def main():
        global num
        global guess
        global tries
        while num != guess:
            try:
                guess = int(raw_input("\nGuess a number: \n"))
            except:
                print "Integers only please!"
                continue
        #Determine if guess is higher or lower and increases tries count
            if guess > num:
                print "Lower..."
            elif guess < num:
                print "Higher..."
            tries += 1
        
    #Tells the user they've won, and in how many tries, and either slightly
    #chastises the user or congratulates them, depending on the # of tries
    def end():
        global tries
        print "\nCongrats, you guessed the number! it was ", num
        print "\n\nIt took you ", tries, "to guess the number\n"
        time.sleep(3)
        if tries > 7: 
            print "\nCome on, you can do better than that.\n"
        if tries < 7:
            print "\nYou're a quick one, good job.\n"
        sys.exit(0)
        
        
    #Actual program
    instructions()
    main()
    end()

---

### Post by schauerlich on 2012-04-24
Since whitespace is important syntactically in python, you need to post it in [noparse][code][/noparse] tags. Otherwise, the post won't show up with whitespace and no one will be able to run it without reindenting it themselves (which might not even be correct, since we don't know how you did it).

---

### Post by dasjew on 2012-05-02
> **schauerlich said:**
> Since whitespace is important syntactically in python, you need to post it in [noparse][code][/noparse] tags. Otherwise, the post won't show up with whitespace and no one will be able to run it without reindenting it themselves (which might not even be correct, since we don't know how you did it).


Ya know, it was my first post, and I was kind of in a hurry, and I didn't even notice. You're right though, most definitely. I'll keep my eye on it in the future.

---

### Post by radhakrishnan on 2012-05-04
Guessomania
I tried this using Shell script.:guitar:

#!/bin/bash
while(true)
do
	valid=1
	counter=0	
	echo "Welcome to Guessomania"
	echo "Enter the number between 1 to 100"
	read unumber
	if [ $unumber -lt 0 -a $unumber -gt 100 ]
	then
		clear
		echo "SORRY!!! INVALID NUMBER"
		echo "TRY AGAIN!!!"
		valid=0
	fi	 
	if [ $valid = 1 ]
	then
	uran=$(($RANDOM%100+1))
	while(true)
	do
		if [ $unumber -gt $uran ]
		then
			clear
			let counter++
			echo "Try Lesser than $unumber"
			echo "Enter the number between 1 to 100"
			read unumber
		elif [ $unumber -lt $uran ]
		then
			clear
			let counter++
			echo "Try Higher than $unumber"
			echo "Enter the number between 1 to 100"
			read unumber
		else
			echo "CONGRATS U WON!!!"
			echo "U have attempted $counter times" 
			exit 0
		fi
	done
	fi 
done

---

### Post by CoyleTrydan on 2013-01-03
Here is my submission for Challenge 5. I have the same question here as Challenge 4 (which I just posted as well) - regarding my usage of functions, and if that's proper form or not. I like how it breaks things up into segments, but I'm very new to Python and not sure yet if I'm doing something silly. :)

[php]
from __future__ import print_function
import random

def generateTarget():
    target = random.randint(1,100)
    return(target)

def getGuess():
    while True:
        try:    
            guess = int(raw_input("Guess a number from 1 to 100 inclusive:"))
            assert guess > 0 and guess < 101
            return(guess)
        except (ValueError, AssertionError):
            print("That was not a valid guess. Please try again.")
    
def checkGuess(guess, target):
    if guess == target:
        print("That's correct! You win!")
        return(1)
    elif guess < target:
        print("That guess is too low.")
        return(0)
    elif guess > target:
        print("That guess is too high.")
        return(0)

def main():
    target = generateTarget()
    tries = 0
    while True:
        guess = getGuess()    
        print("Your guess is", guess)
        tries = tries + 1
        check = checkGuess(guess, target)

        if check == 1:
            break
    print("It took you", tries, "guesses.")

main()
[/php]

---

### Post by shinook on 2013-02-03
Hi all.
I did some programming 5 years ago using Matlab, then I forgot almost everything.
I've just installed Ubuntu, so I'm starting with Python.

Here is my attempt in _Python 3_, I hope you like it.

```

# Beginner programming challenge 5

import random
 
tries = 1
guess = 0
num = random.randrange(1,101)

print("This is the game: I choose a number between 1 and 100.\nYou try to guess it.\n")

while guess != num:
    try:
        guess = int(input("Guess: "))
        
        if guess > num and guess < 101:
            print("Too high, retry.")
            tries += 1
        elif guess < num and guess > 0:
            print("Too low, retry.")
            tries += 1
        elif guess < 1 or guess > 100:
            print("Don't be stupid, you have to type an integer between 1 and 100!")

    except:
        print("Are you crazy? Type an integer!")
        
print("\nCongratulations! The correct number was: ",num,"\n")

if tries == 1:
    print("You got it on the first try, what luck!")
else:
    print("It took you",tries,"tries.")

```

---

### Post by Spae on 2013-02-04
In python 3.
```
#guessing game by spae
import random
a = random.randrange(1,101)
			
print('''I'm thinking of a number 1 to 100''')
print('Can you guess it? You have over 9000 guesses''')

for gn in range(1,9001): #range here as
                         #an easy way to count guesses. 
    guess = input('--->')	
    guess = int(guess)	
    
    if guess == a:		
         print('Wow, you got it!')	
         print('It only took you',gn,'guesses')
         exit()

    elif guess < a:	
         print('too low, try again')
                
    elif guess > a:
            print('too high, try again')
exit()
```
Thanks for people who have posted code. This is my first language, i don't know much so I like to see the methods others have used. :)

---

### Post by Bachstelze on 2013-02-04
Technically, the user here only has 9000 tries, not over 9000. ;)

---

### Post by Tony Flury on 2013-02-04
> **CoyleTrydan said:**
> Here is my submission for Challenge 5. I have the same question here as Challenge 4 (which I just posted as well) - regarding my usage of functions, and if that's proper form or not. I like how it breaks things up into segments, but I'm very new to Python and not sure yet if I'm doing something silly. :)

Splitting code up into self contained segments with a clear task and clear inputs and results is exactly what functions are designed to do - so I would say you are using them in exactly the right way.

---

### Post by Bachstelze on 2013-02-04
This function should be named something like isCorrect and return True or False. Also, return is not a function, no parentheses are needed.

```
def checkGuess(guess, target):
    if guess == target:
        print("That's correct! You win!")
        return(1)
    elif guess < target:
        print("That guess is too low.")
        return(0)
    elif guess > target:
        print("That guess is too high.")
        return(0)
```

---

### Post by Bachstelze on 2013-02-04
```


while guess != num:
    try:
        guess = int(input("Guess: "))
        
        if guess > num and guess < 101:
            print("Too high, retry.")
            tries += 1
        elif guess < num and guess > 0:
            print("Too low, retry.")
            tries += 1
        elif guess < 1 or guess > 100:
            print("Don't be stupid, you have to type an integer between 1 and 100!")

    except:
        print("Are you crazy? Type an integer!")
```

"Catch all" except's are very bad. Suppose any other exception is thrown, for example the user presses Ctrl+C, you will still get "Type an integer". Also, try/except should only cover what is relevant. If an exception is thrown by anything after the first line, you will get "type an integer" also. This is correct:

```


while guess != num:
    try:
        guess = int(input("Guess: "))
    except ValueError:
        print("Are you crazy? Type an integer!")
        continue
        
    if guess > num and guess < 101:
        print("Too high, retry.")
        tries += 1
    elif guess < num and guess > 0:
        print("Too low, retry.")
        tries += 1
    elif guess < 1 or guess > 100:
        print("Don't be stupid, you have to type an integer between 1 and 100!")

```

---

### Post by shinook on 2013-02-05
Ok, thank you Bachstelze for the feedback.

---

