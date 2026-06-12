---
title: "Programming challenge 15: connect four"
date: 2008-06-24
forum: Programming Talk
---

### Post by red_Marvin on 2008-06-24
Sorry for the wait, had to figure out a topic;

Construct a connect four playing machine.
The two players in the game will take turns to place a mark on a grid with the goal of connecting four of their marks while prohibiting the opponent from doing the same.

The program should be able to take instructions from stdin and output their moves on stdout:
**GRID:#,#.** *start a game with a grid of the given size.*
**MARK:#,#.** *the opponent puts their mark on the coordinates given.*
**MOVE.** put *down a mark somewhere (your program should return a **MARK:#,#.** string)*
**QUIT.** *exit gracefully*

To determine a winner I plan to pit the programs against each other, (scoring 0 for loss, 1 for draw, 2 for win), but extra features, like a nice game mode made for human interaction, will count if two entries get a close enough score.

I'm considering running the game for two weeks instead of one, to enable people with little time now at summertime to participate, so when replying, write what you prefer and I'll try to make a fair desicion.

The competition will close on July 1st 22.00 GMT or July 7th, based on your preferences.

---

### Post by CptPicard on 2008-06-24
What are the dimensions of the playing field? IMO it would be interesting if this were extended to connect-n on a reasonably large playing field -- otherwise you will see trivial brute-force machines laying waste to the fanciest heuristic or search...

---

### Post by red_Marvin on 2008-06-24
I'm thinking 32x32 or bigger. The thought of having no bounds at all has struck me too (0,0 being centre and accepting both positive and negative numbers), and then having the game end in a draw if N markers have been put without a winner emerging.

---

### Post by Alasdair on 2008-06-24
From reading around on the internet, I get the impression that connect 4 is one of those games that can be played perfectly, but it's not particularly easy to do so (read: it would take some time). That said, connect-n on a x by y board might not be so much harder... (famous last words :)).

If we have 2 weeks, I'm pretty sure I would be able to submit an entry for everyone else to beat.

Edit: Also, if you are going to have programs playing each other, you need to be really precise about the input and output.

---

### Post by |{urse on 2008-06-24
```
/*sudoku*/



#include <stdio.h>

#include <time.h>

#include <stdlib.h>



void fillinline1(int line[])

{

	int i;





	for (i=1; i<90; i++)

		line[i] = 0;



	for (i=1; i<10; i++)

	{

		do{line[i] = rand()%9+1;}

		while( (line[i] == line[i==1? 0:1]) || (line[i] == line[i==2? 0:2]) || (line[i] == line[i==3? 0:3]) ||

			   (line[i] == line[i==4? 0:4]) || (line[i] == line[i==5? 0:5]) || (line[i] == line[i==6? 0:6]) ||

			   (line[i] == line[i==7? 0:7])	|| (line[i] == line[i==8? 0:8]));

	}



}



void fillnumb(int line[])

{

	line[14] = line[1];   line[28] = line[1];   line[32] = line[1];   line[66] = line[1];

	line[45] = line[1];   line[57] = line[1];   line[83] = line[1];   line[79] = line[1];





	line[24] = line[2];   line[17] = line[2];   line[41] = line[2];   line[35] = line[2];

	line[58] = line[2];   line[63] = line[2];   line[76] = line[2];   line[89] = line[2];





	line[16] = line[3];   line[27] = line[3];   line[52] = line[3];   line[44] = line[3];

	line[39] = line[3];   line[61] = line[3];   line[75] = line[3];   line[88] = line[3];





	line[13] = line[4];   line[29] = line[4];   line[51] = line[4];   line[36] = line[4];

	line[48] = line[4];   line[72] = line[4];   line[65] = line[4];   line[87] = line[4];





	line[22] = line[5];   line[18] = line[5];   line[33] = line[5];   line[46] = line[5];

	line[59] = line[5];   line[81] = line[5];   line[74] = line[5];   line[67] = line[5];





	line[21] = line[6];   line[19] = line[6];   line[42] = line[6];   line[55] = line[6];

	line[37] = line[6];   line[73] = line[6];   line[84] = line[6];   line[68] = line[6];





	line[12] = line[7];   line[26] = line[7];   line[43] = line[7];   line[38] = line[7];

	line[71] = line[7];   line[85] = line[7];   line[54] = line[7];   line[69] = line[7];





	line[23] = line[8];   line[15] = line[8];   line[31] = line[8];   line[56] = line[8];

	line[49] = line[8];   line[82] = line[8];   line[64] = line[8];   line[77] = line[8];





	line[11] = line[9];   line[25] = line[9];   line[53] = line[9];   line[34] = line[9];

	line[47] = line[9];   line[62] = line[9];   line[86] = line[9];   line[78] = line[9];



}



void populateinput(int *line, int *input, int *mirror)

{

	int i, x;

	for (i=1; i<90; i++)

	{	input[i] = 0;

		mirror[i]= 0;

	}

	for (i=1; i<90; i++)

	{

		x = rand()%88+1;

		input[x] = line[x];

		mirror[x] = line[x];

	}

}





void printsudu(int *input)

{	int i;



	printf("\n\n\n\n\n\n\n\n\n\n\n\n\n\n");

	printf("x->1     2     3     4     5     6     7     8     9      y down\n");

	printf("#######################################################\n");

	printf("#     |     |     #     |     |     #     |     |     #   1\n");



	for(i=1; i<10; i++)

	if(input[i] == 0) printf("|     ");

		else printf("|  %d  ", input[i]);

		printf("|\n");





	printf("#_____|_____|_____#_____|_____|_____#_____|_____|_____#\n");

	printf("#     |     |     #     |     |     #     |     |     #   2\n");



	for(i=11; i<20; i++)

	if(input[i] == 0) printf("|     ");

		else printf("|  %d  ", input[i]);

		printf("|\n");





	printf("#_____|_____|_____#_____|_____|_____#_____|_____|_____#\n");

	printf("#     |     |     #     |     |     #     |     |     #   3\n");



	for(i=21; i<30; i++)

	if(input[i] == 0) printf("|     ");

		else printf("|  %d  ", input[i]);

		printf("|\n");





	printf("#     |     |     #     |     |     #     |     |     #\n");

	printf("######|#####|###########|#####|###########|#####|######\n");

	printf("#     |     |     #     |     |     #     |     |     #   4\n");



	for(i=31; i<40; i++)

		if(input[i] == 0) printf("|     ");

		else printf("|  %d  ", input[i]);

		printf("|\n");



	printf("#_____|_____|_____#_____|_____|_____#_____|_____|_____#\n");

	printf("#     |     |     #     |     |     #     |     |     #   5\n");



	for(i=41; i<50; i++)

		if(input[i] == 0) printf("|     ");

		else printf("|  %d  ", input[i]);

		printf("|\n");



	printf("#_____|_____|_____#_____|_____|_____#_____|_____|_____#\n");

	printf("#     |     |     #     |     |     #     |     |     #   6\n");



	for(i=51; i<60; i++)

		if(input[i] == 0) printf("|     ");

		else printf("|  %d  ", input[i]);

		printf("|\n");



	printf("#     |     |     #     |     |     #     |     |     #\n");

	printf("######|#####|###########|#####|###########|#####|######\n");

	printf("#     |     |     #     |     |     #     |     |     #   7\n");



	for(i=61; i<70; i++)

		if(input[i] == 0) printf("|     ");

		else printf("|  %d  ", input[i]);

		printf("|\n");



	printf("#_____|_____|_____#_____|_____|_____#_____|_____|_____#\n");

	printf("#     |     |     #     |     |     #     |     |     #   8\n");



	for(i=71; i<80; i++)

		if(input[i] == 0) printf("|     ");

		else printf("|  %d  ", input[i]);

		printf("|\n");



	printf("#_____|_____|_____#_____|_____|_____#_____|_____|_____#\n");

	printf("#     |     |     #     |     |     #     |     |     #   9\n");



	for(i=81; i<90; i++)

		if(input[i] == 0) printf("|     ");

		else printf("|  %d  ", input[i]);

		printf("|\n");



	printf("#     |     |     #     |     |     #     |     |     #\n");

	printf("#######################################################\n");

}





int checksolution(int *line, int *input)

{

	int i;



	for (i = 1; i<90; i++)

		if(input[i] != line[i])

			return 0;



	return 1;

}







void restartgame(int *input, int *mirror)

{

	int i;

	for(i=1; i<90; i++)

		input[i]=mirror[i];



}



void printresult(int line[])

{

	int i;



	printf("#######################################################\n");

	printf("#     |     |     #     |     |     #     |     |     #\n");



	for(i=1; i<10; i++)

		printf("|  %d  ", line[i]);

		printf("|\n");



	printf("#_____|_____|_____#_____|_____|_____#_____|_____|_____#\n");

	printf("#     |     |     #     |     |     #     |     |     #\n");



	for(i=11; i<20; i++)

		printf("|  %d  ", line[i]);

		printf("|\n");



	printf("#_____|_____|_____#_____|_____|_____#_____|_____|_____#\n");

	printf("#     |     |     #     |     |     #     |     |     #\n");



	for(i=21; i<30; i++)

		printf("|  %d  ", line[i]);

		printf("|\n");



	printf("#     |     |     #     |     |     #     |     |     #\n");

	printf("######|#####|###########|#####|###########|#####|######\n");

	printf("#     |     |     #     |     |     #     |     |     #\n");



	for(i=31; i<40; i++)

		printf("|  %d  ", line[i]);

		printf("|\n");



	printf("#_____|_____|_____#_____|_____|_____#_____|_____|_____#\n");

	printf("#     |     |     #     |     |     #     |     |     #\n");



	for(i=41; i<50; i++)

		printf("|  %d  ", line[i]);

		printf("|\n");



	printf("#_____|_____|_____#_____|_____|_____#_____|_____|_____#\n");

	printf("#     |     |     #     |     |     #     |     |     #\n");



	for(i=51; i<60; i++)

		printf("|  %d  ", line[i]);

		printf("|\n");



	printf("#     |     |     #     |     |     #     |     |     #\n");

	printf("######|#####|###########|#####|###########|#####|######\n");

	printf("#     |     |     #     |     |     #     |     |     #\n");



	for(i=61; i<70; i++)

		printf("|  %d  ", line[i]);

		printf("|\n");



	printf("#_____|_____|_____#_____|_____|_____#_____|_____|_____#\n");

	printf("#     |     |     #     |     |     #     |     |     #\n");



	for(i=71; i<80; i++)

		printf("|  %d  ", line[i]);

		printf("|\n");



	printf("#_____|_____|_____#_____|_____|_____#_____|_____|_____#\n");

	printf("#     |     |     #     |     |     #     |     |     #\n");



	for(i=81; i<90; i++)

		printf("|  %d  ", line[i]);

		printf("|\n");



	printf("#     |     |     #     |     |     #     |     |     #\n");

	printf("#######################################################\n");

}



int rev (int n1)

{

	int result=0;

	while ( n1 !=0 )

		{

			int output = n1 % 10;

			n1 = n1 / 10;

			result = result * 10 + output;

		}

	return result;

}







int main(void)

{

	int line[90], input[90], mirror[90], numb, x, a ;







	do{

		srand(time (NULL) );



		fillinline1(line);

		fillnumb(line);

		populateinput(line, input, mirror);



		do{

			restartgame(input, mirror);

			do{

				printsudu(input);

				do{

					printf("Enter your number, Elizabeth ( xy number ) (enter 10 1 if you are done with the puzzle): \n");

					scanf("%d %d", &x, &numb);

				}while( (x <10) || (x>99) || (numb<0) || (numb>11) );

					input[rev(x)-10] = numb;

			} while( x != 10);





			if (checksolution(line, input) == 1)

				printf("Correct!\nEnter 2 to fill out another puzzle\nEnter 3 to quit\n");

			else printf("Sorry, its wrong!\nEnter 1 to try again\nEnter 2 to fill out another puzzle\nEnter 3 to quit\n");



			scanf("%d", &a);





		}while(a == 1);

	}while(a == 2);



	return 0;

}

```

like that. THis is for a sudoku program but if you compile and run it you'll see you have the basics right here, it would be fairly easy to do.

---

### Post by red_Marvin on 2008-06-24
> **Alasdair said:**
> Edit: Also, if you are going to have programs playing each other, you need to be really precise about the input and output.

Is this what you mean?: 
Each command will consist of the following:

- A four letter command, commands listed in first post
- Colon (if parameters follow)
- Numerical parameter1 (if existing)
- Comma (if >1 parameters)
- Numerical parameter2 (if existing)
- Dot
- Newline

---

### Post by red_Marvin on 2008-07-11
No entries, and I'm not really surprised, summer and all.
Competition closed, with no winner anybody who wants to can start a new challenge.

---

