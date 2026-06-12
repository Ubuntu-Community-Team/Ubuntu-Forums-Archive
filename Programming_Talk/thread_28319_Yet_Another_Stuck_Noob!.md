---
title: "Yet Another Stuck Noob!"
date: 2005-04-19
forum: Programming Talk
---

### Post by N'Jal on 2005-04-19
Ok here's the deal, i wanna learn C, i AM learning C. I have a basic grasp on programming and i need to learn more. NOT C++ NOR C# Just C for the time being.

I had to learn VB at College and found the IDE a distraction to what i really needed to learn IE the code. Now i read up an tutorials on the web copy the examples change the examples i even go as far as writing my own tutorial for myself. Here's my laters endevour. I need to create a Nought's and Crosses Game then a battleships game. Slowly teaching myself the steps to get good enough. My plan is to get into kernel hacking. However i need a base, this is it.

So here's my O's and X's code thus far...

```
/****************************************************************************
**    Author: Neil Munro
**    Name: TicTacToe
**    Purpose: An ASCII-based TicTacToe
**    Started: 9/4/05 @ 11:50AM
**    Notes: Error 1 = Error on X axis, Error 2 = Error on Y axis
**    To Do: Only allow 0, 1 or 2 to be entered at the prompt: Done (14/04/05 : 22:03)
**    To Do: Take X and Y and enter them into the grid: Pending
****************************************************************************/

//Include standard headers
#include <stdio.h>
#include <string.h>

int rules(void);
int game(void);
int playerX(void);
int playerO(void);
int end(void);

int main()
{

	rules();
	game();
	end();

return 0;
}
   
int rules()
{
	printf("Please enter X and Y Co-Ordinates 0,0 being the top left\n");
	//create grid as string
	char grid0[] = "   0 1 2";
	char grid1[] = "0 |_|_|_|";
	char grid2[] = "1 |_|_|_|";
	char grid3[] = "2 |_|_|_|";

	//display pgrid
	puts(grid0);
	puts(grid1);
	puts(grid2);
	puts(grid3);

return 0;
}

int game()
{
	playerX();
	playerO();

	return 0;
}

int playerX()
{

	//X and Y coordinates
	int x = 0;
	int y = 0;

	//User input for X

	printf("\nPlayer X\n");
	
	for (;;)
 	{
		printf("\nPlease enter either 0, 1 or 2 for the X axis: ");
    		scanf("%d", &x);
    		if (x >= 0 && x <= 2)
         break;   // valid answer   
         
     		printf("\nError 1: You have entered an Invalid Number on the X axis.");
        }

	//User input for Y
	
	for (;;) //infinite loop is broken by the "break;" function
	{
		printf("\nPlease enter either 0, 1 or 2 for the Y axis: ");
		scanf("%d", &y);
		if (y >= 0 && y <= 2)
	        break;   // valid answer   
         
		printf("\nError 2: You have entered an Invalid Number on the Y axis.");
        }
	
	//Print User input
	printf("You entered %d for X.\n", x);
	printf("You entered %d for Y.\n", y);

return 0;
}

int playerO()
{

	//X and Y coordinates
	int x = 0;
	int y = 0;

	//User input for X
	
	printf("\nPlayer O\n");

	for (;;)
 	{
		printf("\nPlease enter either 0, 1 or 2 for the X axis: ");
    		scanf("%d", &x);
    		if (x >= 0 && x <= 2)
         break;   // valid answer   
         
     		printf("\nError 1: You have entered an Invalid Number on the X axis.");
        }

	//User input for Y
	
	for (;;) //infinite loop is broken by the "break;" function
	{
		printf("\nPlease enter either 0, 1 or 2 for the Y axis: ");
		scanf("%d", &y);
		if (y >= 0 && y <= 2)
	        break;   // valid answer   
         
		printf("\nError 2: You have entered an Invalid Number on the Y axis.");
        }
	
	//Print User input
	printf("You entered %d for X.\n", x);
	printf("You entered %d for Y.\n", y);

	return 0;
}

int end()
{
	printf("Game Over\n");

return 0;
}
```

---

### Post by toojays on 2005-04-19
You didn't tell us what exactly you were stuck on! But after looking at it, I can tell it is not finished. At least these things are missing:

  1) Collision detection.

  2) Having enough turns to finish the game.

The main thing at this stage is that you need a data structure to keep track of the state of the board. A multidimensional array would do the trick.

Does that help? Do you need more clues?

---

### Post by N'Jal on 2005-04-20
I do appologise. I am createing a tictactoe game. I don't know much about C yet. Here what you see is what i have learned.

I am vaguely aware that multi-dementional arrays exits i really dont know how to use them.

I wanna work most of this out myself, but i will need maybe some seemigly obvious clues to start with. 

Thank you for your quick reply

What i really need is to learn how to take the input of the user and place the entered co-ordinate into the grid. I cannot think of how to do this.

---

### Post by Leif on 2005-04-20
It's great that you want to learn programming, but if you are not familiar with things such as multi-dimensional arrays, I think you would really benefit from sitting down with a good introductory book on the topic before diving in like this. I'm sure you can get plenty of great advice from the folks here at the forums, but a book will probably give you better grounding. There's a nice one, that's even free : [http://www.mindview.net/Books/TICPP/ThinkingInCPP2e.html](http://www.mindview.net/Books/TICPP/ThinkingInCPP2e.html)

---

### Post by sas on 2005-04-20
Yeah just use a multi dimensional array.... [http://home.twcny.rr.com/amantoan/cweb/dimary.htm](http://home.twcny.rr.com/amantoan/cweb/dimary.htm) has the perfect example to help you on your way I think....

Does it help?

---

### Post by N'Jal on 2005-04-20
Well i now understand the CONCEPT of MDA's just cant seem to implement them

My sources```
//attempting multi-dimentional array
int array[3][3] = {1, 2, 3,
		    4, 5, 6,
		    7, 8, 9 };

printf("%s\n", array);

return 0;
}
``` 

That come's between the rules and game functions a have also defined array where its needed, i am aware there's an extra } in there that is a problem however i cannot seem to workout WHY the example gave me that. I will try the example on the page 2moro as its late in England right now. But simply here's where i am at right now.

Also i will download that book 2moro again, winding down for the night.

Thank you all for your reply's and help, much appriciate

---

### Post by sas on 2005-04-20
You can't just print out a whole mda like that... you have to loop through each cell...like

```
//attempting multi-dimentional array

int array[3][3] = {1, 2, 3,
		    4, 5, 6,
		    7, 8, 9 };
// loop around the first array index, remembering arrays start at 0
for (i= 0; i < 3; i++)
{
     //loop around the second index, remember arrays start at 0
     for (j=0; j < 3; j++)
    {
          printf("%s\n", array[i][j]);
     }
     // reset j ready for the next row
     j = 0;
}
return 0;
}
```

---

### Post by N'Jal on 2005-04-22
This also fails to work

 >_<

ARgh

```
/****************************************************************************
**    Author: Neil Munro
**    Name: TicTacToe
**    Purpose: An ASCII-based TicTacToe
**    Started: 9/4/05 @ 11:50AM
**    Notes: Error 1 = Error on X axis, Error 2 = Error on Y axis
**    To Do: Only allow 0, 1 or 2 to be entered at the prompt: Done (14/04/05 : 22:03)
**    To Do: Take X and Y and enter them into the grid: Pending
****************************************************************************/

//Include standard headers
#include <stdio.h>
#include <string.h>

int rules(void);
int array(void);
int game(void);
int end(void);

int main()
{

	rules();
	array();
	game();
	end();

return 0;
}
   
int rules()
{
	
printf("Please enter X and Y Co-Ordinates 0,0 being the top left\n");
	//Uncomment the following block of code if the multi-demintional array fails
	//{
	//create grid as string
	//char grid0[] = "   0 1 2";
	//char grid1[] = "0 |_|_|_|";
	//char grid2[] = "1 |_|_|_|";
	//char grid3[] = "2 |_|_|_|";

	//display pgrid
	//puts(grid0);
	//puts(grid1);
	//puts(grid2);
	//puts(grid3);
	//}

return 0;
}

//attempting multi-dimentional array
int array[3][3] = {1, 2, 3,
		    4, 5, 6,
		    7, 8, 9 }
// loop around the first array index, remembering arrays start at 0
for (i= 0; i < 3; i++)
{
     //loop around the second index, remember arrays start at 0
     for (j=0; j < 3; j++)
    {
          printf("%s\n", array[i][j]);
     }
     // reset j ready for the next row
     j = 0;
}
return 0;
}


int game()
{
	//Player O
	//X and Y coordinates
	int x = 0;
	int y = 0;

	//User input for X

	printf("\nPlayer O\n");
	
	for (;;)
 	{
		printf("\nPlease enter either 0, 1 or 2 for the X axis: ");
    		scanf("%d", &x);
    		if (x >= 0 && x <= 2)
         break;   // valid answer   
         
     		printf("\nError 1: You have entered an Invalid Number on the X axis.");
        }

	//User input for Y
	
	for (;;) //infinite loop is broken by the "break;" function
	{
		printf("\nPlease enter either 0, 1 or 2 for the Y axis: ");
		scanf("%d", &y);
		if (y >= 0 && y <= 2)
	        break;   // valid answer   
         
		printf("\nError 2: You have entered an Invalid Number on the Y axis.");
        }
	
	//Print User input
	printf("You entered %d for X.\n", x);
	printf("You entered %d for Y.\n", y);

	//Player X
	//User input for X
	
	printf("\nPlayer X\n");

	for (;;)
 	{
		printf("\nPlease enter either 0, 1 or 2 for the X axis: ");
    		scanf("%d", &x);
    		if (x >= 0 && x <= 2)
         break;   // valid answer   
         
     		printf("\nError 1: You have entered an Invalid Number on the X axis.");
        }

	//User input for Y
	
	for (;;) //infinite loop is broken by the "break;" function
	{
		printf("\nPlease enter either 0, 1 or 2 for the Y axis: ");
		scanf("%d", &y);
		if (y >= 0 && y <= 2)
	        break;   // valid answer   
         
		printf("\nError 2: You have entered an Invalid Number on the Y axis.");
        }
	
	//Print User input
	printf("You entered %d for X.\n", x);
	printf("You entered %d for Y.\n", y);

	return 0;
}

int end()
{
	printf("Game Over\n");

return 0;
}
``` 


Will have to start reading when i have time

---

### Post by sas on 2005-04-22
[QUOTE=N'Jal]This also fails to work

 >_<

ARgh


Will have to start reading when i have time[/QUOTE]
 first things first there was an error in the code I gave you..I put printf("%s"blablah instead of %d besides that, thinking about it the j= 0 assignment is superflous as the for loop construct does that..

The other thing is that the array[3][3] decloration isn't inside a function...so you need to put int array(){ above that and also declare i and j inside that function...It should compile then..

---

### Post by N'Jal on 2005-04-26
Thank you! It works

```
//attempting multi-dimentional array
int array()
{
	int array[3][3] = { 1, 2, 3,
	       	    	4, 5, 6,
		    	7, 8, 9 };
	int i;
	int j;
	i = 0;
	j = 0;
// loop around the first array index, remembering arrays start at 0
for (i= 0; i < 3; i++)
{
     //loop around the second index, remember arrays start at 0
     for (j=0; j < 3; j++)
    {
          printf("%d\n", array[i][j]);
     }
     // reset j ready for the next row
     int j = 0;
     

}
return 0;
}
``` 

Took a lil bit to debug and understand what you were saying but, i got there. Now that prints this: -
```
1
2
3
4
5
6
7
8
9
```

How do i get it to print this: -

```
1      2     3
4      5     6
7      8     9
```



I tryed \n but i didnt think that would work

---

### Post by sas on 2005-04-26
Change the \n for a \t (tab character) this will put all characters tabbed out onto one line. So you need to break it up after the third digit. To do this you'll want to do a printf("\n"); each time a row is finished to force it to the next line 

(basically: put printf("\n"); after the j loop)

---

### Post by -Rick- on 2005-04-26
There you go... :)

```

int array[3][3] = { { 1, 2, 3 }, { 4, 5, 6 }, { 7, 8, 9 } };
for (int i=0;i<3;i++)
{
    for (int j=0;j<3;j++)
    {
        printf("%d\t", array[i][j]); // \t == tab
    }
    printf("\n"); // \n == new line
}

```

---

### Post by N'Jal on 2005-04-26
I *really* should have been able to work that one out myself :$

Now here is where i have to tie the user input X/Y to the grid I/J

I will give it a go myself at a more reasonable hour, and see where i am.

Thank you all for posting all your tips and comment etc. They are all much appriciated. 

What i am doing might seem a little insignificant but i need to learn C as almost my second language in the next four years, for various bits and pieces (kernel hacking, program design etc)

---

### Post by jerome bettis on 2005-04-26
a possible optimization you could do to get the code size down is eliminate one of the player functions since they are so similar.  just have one with an extra parameter which you could print as needed.

take a class on C programming.  you'll be glad you did.

visual basic lol ](*,)

---

### Post by N'Jal on 2005-04-28
Yeah i know visual basic was terrible. >_<

Um i will be taking a 4 year class on C starting in September at Uni however i figure the more i know before i go the more time i will have on learning the harder stuff. IE pointers ARGH!!!!

I will create that game function now.

---

### Post by N'Jal on 2005-04-28
This what you meant?

```
int game()
{
	//Player O
	//X and Y coordinates
	int x = 0;
	int y = 0;

	//User input for X

	printf("\nPlayer O\n");
	
	for (;;)
 	{
		printf("\nPlease enter either 0, 1 or 2 for the X axis: ");
    		scanf("%d", &x);
    		if (x >= 0 && x <= 2)
         break;   // valid answer   
         
     		printf("\nError 1: You have entered an Invalid Number on the X axis.");
        }

	//User input for Y
	
	for (;;) //infinite loop is broken by the "break;" function
	{
		printf("\nPlease enter either 0, 1 or 2 for the Y axis: ");
		scanf("%d", &y);
		if (y >= 0 && y <= 2)
	        break;   // valid answer   
         
		printf("\nError 2: You have entered an Invalid Number on the Y axis.");
        }
	
	//Print User input
	printf("You entered %d for X.\n", x);
	printf("You entered %d for Y.\n", y);

	//Player X
	//User input for X
	
	printf("\nPlayer X\n");

	for (;;)
 	{
		printf("\nPlease enter either 0, 1 or 2 for the X axis: ");
    		scanf("%d", &x);
    		if (x >= 0 && x <= 2)
         break;   // valid answer   
         
     		printf("\nError 1: You have entered an Invalid Number on the X axis.");
        }

	//User input for Y
	
	for (;;) //infinite loop is broken by the "break;" function
	{
		printf("\nPlease enter either 0, 1 or 2 for the Y axis: ");
		scanf("%d", &y);
		if (y >= 0 && y <= 2)
	        break;   // valid answer   
         
		printf("\nError 2: You have entered an Invalid Number on the Y axis.");
        }
	
	//Print User input
	printf("You entered %d for X.\n", x);
	printf("You entered %d for Y.\n", y);

	return 0;
}

int end()

```

---

### Post by jerome bettis on 2005-04-28
no, you still have repeated code.

put one copy of that into a function, and just call it twice.  you could passs X or o to it if you want, or just print out x or o before you call it.

think about it, you'll get it.

---

### Post by N'Jal on 2005-04-29
Like this?

```
int game()
{
	//Player O
	//X and Y coordinates
	int x = 0;
	int y = 0;

	//User input for X

	printf("\nPlayer O\n");
	
	for (;;)
 	{
		printf("\nPlease enter either 0, 1 or 2 for the X axis: ");
    		scanf("%d", &x);
    		if (x >= 0 && x <= 2)
		printf("\nPlease enter either 0, 1 or 2 for the Y axis: ");
    		scanf("%d", &y);
    		if (y >= 0 && y <= 2)
         break;   // valid answer   
         
     		printf("\nError 1: You have entered an Invalid Number on the X axis.");
        }

	//User input for Y
	
         //Commented out second loop
	/*for (;;) //infinite loop is broken by the "break;" function
	{
		printf("\nPlease enter either 0, 1 or 2 for the Y axis: ");
		scanf("%d", &y);
		if (y >= 0 && y <= 2)
	        break;   // valid answer   
         
		printf("\nError 2: You have entered an Invalid Number on the Y axis.");
        }*/
	
	//Print User input
	printf("You entered %d for X.\n", x);
	printf("You entered %d for Y.\n", y);

	//Player X
	//User input for X
	
	printf("\nPlayer X\n");

	for (;;)
 	{
		printf("\nPlease enter either 0, 1 or 2 for the X axis: ");
    		scanf("%d", &x);
    		if (x >= 0 && x <= 2)
         break;   // valid answer   
         
     		printf("\nError 1: You have entered an Invalid Number on the X axis.");
        }

	//User input for Y
	
	for (;;) //infinite loop is broken by the "break;" function
	{
		printf("\nPlease enter either 0, 1 or 2 for the Y axis: ");
		scanf("%d", &y);
		if (y >= 0 && y <= 2)
	        break;   // valid answer   
         
		printf("\nError 2: You have entered an Invalid Number on the Y axis.");
        }
	
	//Print User input
	printf("You entered %d for X.\n", x);
	printf("You entered %d for Y.\n", y);

	return 0;
}

```

I compiled it and it works as i did previously so i assume its right

---

