---
title: "Homework Help - BASH Scripting"
date: 2012-05-11
forum: Programming Talk
---

### Post by jackalope044 on 2012-05-11
Excuse me while I be very obnoxious and ask for homework help on these fine forums.

The assignment is to code a game of Mastermind with a BASH script. I'm currently having two issues:

1. Ensuring that the randomly generated number is somewhere between 1000 and 9999 (So that it has only four digits as required by the game.)

2. Figuring out how to take the individual numbers from the user and the randomly generated number and turning them into individual variables to be compared. Is there some charAt.() built-in function or something like that? I don't think I need to turn them into integers, since there's no math involved after generating the number, only comparing.

Here's the current code:

```
#!/bin/bash


#debugging
#set -x



#=======================================

#Intializing variables


userdigit=0

userdigit1=0

userdigit2=0

userdigit3=0

userdigit4=0

digit=0

digit1=0

digit2=0

digit3=0

digit4=0

wrongplace=0

rightplace=0



#========================================

#Introductory Code, welcoming the user


echo 'Welcome to Mastermind!'

echo ''

echo 'Here are the rules of the game:'

echo ''

echo 'A four digit number will be randomly generated.'

echo ''

echo 'It is your job to guess that number!'

echo ''

echo 'Every time you guess, you will be told how many'

echo ''

echo 'digits you have that are right, but in the wrong'

echo ''

echo 'spot, and how many digits you have that are right'

echo ''

echo 'and in the right spot! Use these clues to help you'

echo ''

echo 'guess the correct number! A hard but fun game!'

echo ''

echo -n 'Would you like to play? Enter Y if so: '

read want

if [ "$want" = "Y" ]
	
	then
		
		echo ''

		echo 'Alright, here we go! Good luck!'

	else
		
		echo ''
		
		echo 'Okay, then. See you later!'
		
		exit

fi



#========================================

#Setting the number to guess

digit=$RANDOM

echo $digit


#========================================

#The actual game


until [ "$userdigit" = "$digit" ]
	
do
		
#Getting the number from the player
	
		echo "Please enter your four digit number!"
	
		echo ''
	read userdigit	
	
		echo $userdigit1
	
done

echo "Congratulations, you win!"

```

Many thanks for any and all help, and apologies if this is breaking the rules, in the wrong forum, or just altogether annoying and/or aggravating.

---

### Post by sisco311 on 2012-05-11
Welcome to the forums!

From the [code of conduct](http://ubuntuforums.org/index.php?page=policy) that you agreed to when you created your account:

> 
While we are happy to serve as a resource for hints and for asking questions when you get stuck and need a little help, the Ubuntu Forums is not a homework service. Please do not post your homework assignments expecting someone else to do it for you. Any such threads will be taken offline and warnings or infractions may be issued.


HINT1: 1000 < $RANDOM % 9000 + 1000 < 9999

HINT2: [http://mywiki.wooledge.org/ArithmeticExpression](http://mywiki.wooledge.org/ArithmeticExpression)

---

### Post by Vaphell on 2012-05-11
in case you want to play with strings/substrings you can go with
${variable:start:length}, eg ${number:3:1}

---

### Post by jackalope044 on 2012-05-11
> **sisco311 said:**
> Welcome to the forums!

From the [code of conduct](http://ubuntuforums.org/index.php?page=policy) that you agreed to when you created your account:



HINT1: 1000 < $RANDOM % 9000 + 1000 < 9999

HINT2: [http://mywiki.wooledge.org/ArithmeticExpression](http://mywiki.wooledge.org/ArithmeticExpression)

Ahh, apologies for the rule breaking, but many thanks for the assistance.

> **Vaphell said:**
> in case you want to play with strings/substrings you can go with
${variable:start:length}, eg ${number:3:1}

This helps immensely, and this is exactly what I was looking for. Unfortunately the book I'm using doesn't have any stuff like this, so I've been searching in vain as to how to use substrings. Many thanks to both of you again. I should now be able to code this program.

---

### Post by steeldriver on 2012-05-11
> **jackalope044 said:**
> Unfortunately the book I'm using doesn't have any stuff like this, so I've been searching in vain as to how to use substrings.

you may find this useful 

[http://www.gnu.org/software/bash/manual/bashref.html](http://www.gnu.org/software/bash/manual/bashref.html)

---

