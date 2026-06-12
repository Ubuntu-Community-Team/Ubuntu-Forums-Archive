---
title: "Derren Brown Heads or Tails"
date: 2009-12-09
forum: Programming Talk
---

### Post by whoop on 2009-12-09
Did anybody see Derren Brown perform the Heads or Tails trick in his tv show?
[http://derrenbrown.channel4.com/derren-brown-penney-ante-game.shtml](http://derrenbrown.channel4.com/derren-brown-penney-ante-game.shtml)

After I read the article I wanted to see if it really worked, instead of flipping a coin I started up my editor and did a quick and dirty hack:
```

/* -*- Mode: C; indent-tabs-mode: t; c-basic-offset: 4; tab-width: 4 -*- */
/*
 * main.cc
 * Copyright (C) Whoop 2009 <whoop@>
 * 
 * HeadsAndTails is free software: you can redistribute it and/or modify it
 * under the terms of the GNU General Public License as published by the
 * Free Software Foundation, either version 3 of the License, or
 * (at your option) any later version.
 * 
 * HeadsAndTails is distributed in the hope that it will be useful, but
 * WITHOUT ANY WARRANTY; without even the implied warranty of
 * MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
 * See the GNU General Public License for more details.
 * 
 * You should have received a copy of the GNU General Public License along
 * with this program.  If not, see <http://www.gnu.org/licenses/>.
 */

#include <iostream>
#include <ctime>
#include <cstdlib>


bool compareSets(int test[3],int combo)
{
	int comboSet[3];
	bool returnVal = false;
	switch(combo)
	{
		case 1: comboSet[0]=0;
				comboSet[1]=0;
				comboSet[2]=0;
				break;
		case 2: comboSet[0]=1;
				comboSet[1]=1;
				comboSet[2]=1;
				break;
		case 3: comboSet[0]=0;
				comboSet[1]=0;
				comboSet[2]=1;
				break;
		case 4: comboSet[0]=1;
				comboSet[1]=1;
				comboSet[2]=0;
				break;
		case 5: comboSet[0]=0;
				comboSet[1]=1;
				comboSet[2]=0;
				break;
		case 6: comboSet[0]=1;
				comboSet[1]=0;
				comboSet[2]=1;
				break;
		case 7: comboSet[0]=0;
				comboSet[1]=1;
				comboSet[2]=1;
				break;
		case 8: comboSet[0]=1;
				comboSet[1]=0;
				comboSet[2]=0;
				break;
	}
	if(test[0]==comboSet[0])
		if(test[1]==comboSet[1])
			if(test[2]==comboSet[2])
				returnVal=true;
	return returnVal;	
}

int main()
{
	const int minAttempts = 10;
	int attempts;
	int playerCombo;
	int computerCombo;	
	int playerScore=0;
	int computerScore=0;
	int checkSet [3] = {-1,-1,-1};
	srand((unsigned)time(0));
	
	std::cout << "Select your lucky combination:"  <<  std::endl;
	std::cout << "1: HHH\t\t2: TTT\n";
	std::cout << "3: HHT\t\t4: TTH\n";
	std::cout << "5: HTH\t\t6: THT\n";
	std::cout << "7: HTT\t\t8: THH\n";
	std::cin >> playerCombo;
	if(playerCombo>8)
		playerCombo=8;

	switch(playerCombo)
	{
		case 1: computerCombo=8;
				break;
		case 2: computerCombo=7;
				break;
		case 3: computerCombo=8;
				break;
		case 4: computerCombo=7;
				break;
		case 5: computerCombo=3;
				break;
		case 6: computerCombo=4;
				break;
		case 7: computerCombo=3;
				break;
		case 8: computerCombo=4;
				break;
	}
			
	std::cout << "The computer has selected: "  << computerCombo << std::endl;

	std::cout << "Enter high-score score (" << minAttempts << " or higher):" << std::endl;
	std::cin >> attempts;
	if(attempts<minAttempts)
		attempts = minAttempts;
	
	for(;;)
	{
		for(;;)
		{
			bool blnWinner = false;
			checkSet[0]=checkSet[1];
			checkSet[1]=checkSet[2];
			checkSet[2]=(rand()%(2));
			if(checkSet[2] == 0)
				std::cout << "H";
			else
				std::cout << "T";
			if(compareSets(checkSet,playerCombo))
			{
				blnWinner=true;
				playerScore++;
				std::cout << std::endl << "You win!" << std::endl;
			}
			else if(compareSets(checkSet,computerCombo))
			{
				blnWinner=true;
				computerScore++;
				std::cout << std::endl << "Computer wins!" << std::endl;
			}
			if(blnWinner)
			{
				checkSet[0]=-1;
				checkSet[1]=-1;
				checkSet[2]=-1;
				std::cout << std::endl;
				break;
			}
		}

		std::cout << "Player score:" << playerScore << "\tComputer score:" << computerScore << std::endl;
		if(playerScore>=attempts || computerScore>=attempts)
			break;		
	}
	if(computerScore>playerScore)
		std::cout << "You lost the game!" << std::endl;
	else
		std::cout << "You won the game!" << std::endl;
	return 0;
}

```

Well, it seems to work :lolflag:, the computer wins just about every time...
Program output example:
```

Select your lucky combination:
1: HHH		2: TTT
3: HHT		4: TTH
5: HTH		6: THT
7: HTT		8: THH
5
The computer has selected: 3
Enter high-score score (10 or higher):
10
HTH
You win!

Player score:1	Computer score:0
HTTTHTH
You win!

Player score:2	Computer score:0
THHHHHT
Computer wins!

Player score:2	Computer score:1
TTHHT
Computer wins!

Player score:2	Computer score:2
TTTTHTH
You win!

Player score:3	Computer score:2
HHHT
Computer wins!

Player score:3	Computer score:3
THHHT
Computer wins!

Player score:3	Computer score:4
HTTHHHHHHT
Computer wins!

Player score:3	Computer score:5
TTTTHTH
You win!

Player score:4	Computer score:5
HHT
Computer wins!

Player score:4	Computer score:6
THTH
You win!

Player score:5	Computer score:6
HTTHTTTHHHHHHHHT
Computer wins!

Player score:5	Computer score:7
TTHTTTHTTHHHHHHHT
Computer wins!

Player score:5	Computer score:8
THHHT
Computer wins!

Player score:5	Computer score:9
HTTHTH
You win!

Player score:6	Computer score:9
HHT
Computer wins!

Player score:6	Computer score:10
You lost the game!

```
On his show he claims it has to do with "deep maths" ooooooowww.
The reason this trick works is really obvious once you get it (or maybe I still don't get it, no I'm sure I do, probably :D), I won't spoil it for you just yet ;)

---

### Post by Can+~ on 2009-12-09
> **whoop said:**
> I started up my editor and did a quick and dirty hack:

There's a lot of dirty, but nothing quite quick. The algorithm is clearly detailed:

> You ask the other person to make their choice first. This isn’t courtesy, it’s vital. From what he says, you work out what you’ll say. You do this by taking the middle one of his three, reversing it and putting it at the start. So if he says HHH, you say THH, and ignore the last one.

So why not just do:

[PHP]void derrenbrown(char *sequence)
{
	char t;
	
	t = sequence[1];
	sequence[1] = sequence[0];
	sequence[0] = (t == 'H') ? 'T' : 'H'; 
}

int main(int argc, char **argv)
{
	char sequence[4];
	
	printf("Input your sequence: ");
	fgets(sequence, 4, stdin);
	
	derrenbrown(sequence);
	
	printf("The resulting sequence is: %s \n", sequence);
	
	return 0;
}[/PHP]

---

### Post by whoop on 2009-12-09
There are probably countless ways to do it, that wasn't really my concern. I did your part like this:
[php]
#include <iostream>
int main()
{
	int playerCombo;
	int computerCombo;	
	
	std::cout << "1: HHH\t\t2: TTT\n";
	std::cout << "3: HHT\t\t4: TTH\n";
	std::cout << "5: HTH\t\t6: THT\n";
	std::cout << "7: HTT\t\t8: THH\n";
	std::cin >> playerCombo;
	switch(playerCombo)
	{
		case 1: computerCombo=8;
				break;
		case 2: computerCombo=7;
				break;
		case 3: computerCombo=8;
				break;
		case 4: computerCombo=7;
				break;
		case 5: computerCombo=3;
				break;
		case 6: computerCombo=4;
				break;
		case 7: computerCombo=3;
				break;
		case 8: computerCombo=4;
				break;
	}
	std::cout << "The computer has selected: "  << computerCombo << std::endl;
	return 0;
}
[/php]
The method to pick the winning combination was clear to me. It just didn't immediately occur to me why the combination would (nearly) always win.

---

