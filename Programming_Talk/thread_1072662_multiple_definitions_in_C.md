---
title: "multiple definitions in C"
date: 2009-02-17
forum: Programming Talk
---

### Post by nahky007 on 2009-02-17
Hello everyone, 

I came across this very common problem of multiple definitions in C...I googled it found some pointers but still the bug is there...Getting frustrated, must be a simple bug but not seeing it...Any pointers, help will be really appreciated...


This is what I have in badminton.h header file...

```



extern char deuce_threshold ; //********setting up some test deuce threshold value....CHANGE!
extern char num_of_games_var; //This variable is to be configured by the player
extern char pnt_per_game_var; //This variable is to be configured by the player
extern char deuce_threshold_set; 
extern char game_in_progress_flag; //This variable/flag to be used so that if a game is in progress do not ask the user to repeat settings

extern char player1_score;
extern char player2_score; 


typedef enum 
{	
//the sequence of the list below is VERY important since it determines the value of the named integer  e.g. NUM_OF_GAMES,PNT_PER_GAME etc ...(will be added as neccessary
//this value is also used by state_table[current_state] pointer as a indexes. That's why it is very important
//The sequence of the state integer constants has to be same as state table pointer which is declared later in the program 	
	
	NUM_OF_GAMES,
	PNT_PER_GAME,
	START_GAME
}Sub_State_Type;

extern Sub_State_Type sub_badminton_state;



void DisplayNumber(int number); 

void Num_Of_Games_State (void);
void Pnt_Per_Game_State (void); 
void Start_Game_State (void);


//This table contains a pointer to the function to call each state
 void (*badminton_state_table[])() = {Num_Of_Games_State, Pnt_Per_Game_State, Start_Game_State};

```


the badminton.c has...

```


#include "badminton.h"

void Num_Of_Games_State (void)
{
	
	sub_badminton_state = NUM_OF_GAMES; 
//and other codes follows here for this state, waiting user input



}

void Pnt_Per_Game_State(void)
{
	
	sub_badminton_state = PNT_PER_GAME;
//and other codes follows here for this state, waiting for user input
	
}

void Start_Game_State (void)
{
        sub_badminton_state = START_GAME;
//and other codes follows here for this state...waiting for user
}


```

from the main.c I call...

```



#include "badminton.h"



void BadmintonState (void)
{

	badminton_state_table[NUM_OF_GAMES]();
//so it always go to the Num_Of_Games_State for user to config.

}

```



But I am getting this error no matter what. 

```
Make: The target "C:\Documents and Settings\Yaseen Khan\My Documents\My PIC uC\Winscor\MainMenu.cof" is out of date.
Executing: "C:\Program Files\Microchip\MPLAB C30\bin\pic30-gcc.exe" -mcpu=24FJ128GA010 "buttons.o" "lcd.o" "badminton.o" "MainMenu.o" -o"MainMenu.cof" -Wl,-L"C:\Program Files\Microchip\MPLAB C30\lib",--script="p24FJ128GA010.gld",--defsym=__MPLAB_BUILD=1,-Map="MainMenu.map",--report-mem
MainMenu.o(.ndata+0x0):C:\Documents and Settings\Yaseen Khan\My Documents\My PIC uC\Winscor\MainMenu.c: multiple definition of `badminton_state_table'
badminton.o(.ndata+0x0):C:\Documents and Settings\Yaseen Khan\My Documents\My PIC uC\Winscor\badminton.c: first defined here
c:\program files\microchip\mplab c30\bin\pic30-coff-ld.exe: Link terminated due to previous error(s).
Link step failed.
```

I fixed the multiple definitions for variable by using "extern" but for 

```
void (*badminton_state_table[])() = {Num_Of_Games_State, Pnt_Per_Game_State, Start_Game_State};

``` 

"extern" doesn't work...what am I doing wrong...? 

Thanks for helping me out!

---

### Post by weresheep on 2009-02-17
I think I see the problem.

You're including badminton.h in both badminton.c and main.c but badminton.h declares a variable (an array of function pointers). This means when main.c is passed to the compiler it has 'included' the contents of badminton.h, including the variable definition.

When badminton.c is passed to the compiler it also has the contents of badminton.h 'included' within it, and therefore also has a declaration of a variable with the same name.

When it comes to link time, the linker finds two variables in scope with the same name and cannot proceed.

One solution to this problem is to move the declaration of the variable from the header file into one of the source files. This would mean restructuring your code a bit.

Another solution would be to include preprocessor protections around the header file. For example add the below two lines to the START of badminton.h...

```

#ifndef BADMINTON.H
#define BADMINTON.H

```

then as the LAST line of badminton.h add...

```

#endif

```

This prevents two copies of badminton.h being compiled into object code and so prevents two variables with the same name. The linker can then stitch it all together :) Also, if you use this approach you'll need to remove the 'extern' from this line in badminton.h.

```

extern Sub_State_Type sub_badminton_state;

```

Hope that helps.

-weresheep

---

### Post by OutOfReach on 2009-02-17
Actually I posted this question a couple of days ago. Here the link to my thread, hopefully you'll find the answer:
[http://ubuntuforums.org/showthread.php?t=1069964](http://ubuntuforums.org/showthread.php?t=1069964)

---

### Post by dwhitney67 on 2009-02-17
> **weresheep said:**
> ...

Another solution would be to include preprocessor protections around the header file. For example add the below two lines to the START of badminton.h...

```

#ifndef BADMINTON.H
#define BADMINTON.H

```

then as the LAST line of badminton.h add...

```

#endif

```

This prevents two copies of badminton.h being compiled into object code and so prevents two variables with the same name.

...
This is not true; if two or more separate source (.c) files include the same header file, regardless if the inclusion guards are present, the compiler will attempt to create multiple variables, should they be initialized with a value.  This of course leads to the problem the OP is experiencing.

The best bet, as you previously mentioned, is to initialize the array of function pointers in the main module.  There are other ways to "dance" around the problem, but initializing the shared global value in the main module is probably the easiest.

Btw, the inclusion guards are worthy to have, but these merely prevent a single module from including the same header file twice.

---

### Post by nahky007 on 2009-02-17
> **weresheep said:**
> I think I see the problem.

You're including badminton.h in both badminton.c and main.c but badminton.h declares a variable (an array of function pointers). This means when main.c is passed to the compiler it has 'included' the contents of badminton.h, including the variable definition.

When badminton.c is passed to the compiler it also has the contents of badminton.h 'included' within it, and therefore also has a declaration of a variable with the same name.

When it comes to link time, the linker finds two variables in scope with the same name and cannot proceed.

One solution to this problem is to move the declaration of the variable from the header file into one of the source files. This would mean restructuring your code a bit.

Another solution would be to include preprocessor protections around the header file. For example add the below two lines to the START of badminton.h...

```

#ifndef BADMINTON.H
#define BADMINTON.H

```

then as the LAST line of badminton.h add...

```

#endif

```

This prevents two copies of badminton.h being compiled into object code and so prevents two variables with the same name. The linker can then stitch it all together :) Also, if you use this approach you'll need to remove the 'extern' from this line in badminton.h.

```

extern Sub_State_Type sub_badminton_state;

```

Hope that helps.

-weresheep





Thanks weresheep! Yes, I just tried it the way weresheep suggested...for a moment I thought it might just work...unfortunately it didn't...

After modifiying the code in the badminton.h header file it looks as below: 

```
#ifndef badminton.h
#define badminton.h

extern char deuce_threshold ; //********setting up some test deuce threshold value....CHANGE!
extern char num_of_games_var; //This variable is to be configured by the player
extern char pnt_per_game_var; //This variable is to be configured by the player
extern char deuce_threshold_set; 
extern char game_in_progress_flag; //This variable/flag to be used so that if a game is in progress do not ask the user to repeat settings

extern char player1_score;
extern char player2_score; 

typedef enum 
{	
//the sequence of the list below is VERY important since it determines the value of the named integer  e.g. NUM_OF_GAMES,PNT_PER_GAME etc ...(will be added as neccessary
//this value is also used by state_table[current_state] pointer as a indexes. That's why it is very important
//The sequence of the state integer constants has to be same as state table pointer which is declared later in the program 	
	
	NUM_OF_GAMES,
	PNT_PER_GAME,
	START_GAME
}Sub_State_Type;
Sub_State_Type sub_badminton_state;

void DisplayNumber(int number); //This function is used for Badminton state to convert game/point # to ASCII and print on LCD NOT A STATE!

void Num_Of_Games_State (void);
void Pnt_Per_Game_State (void); 
void Start_Game_State (void);


//This table contains a pointer to the function to call each state
void (*badminton_state_table[])() = {Num_Of_Games_State, Pnt_Per_Game_State, Start_Game_State};


#endif
```


```
Make: The target "C:\Documents and Settings\Yaseen Khan\My Documents\My PIC uC\Winscor Documents\Winscor Source Backup\Feb 17\Winscor [1]\Winscor\MainMenu.cof" is out of date.
Executing: "C:\Program Files\Microchip\MPLAB C30\bin\pic30-gcc.exe" -mcpu=24FJ128GA010 "buttons.o" "lcd.o" "badminton.o" "MainMenu.o" -o"MainMenu.cof" -Wl,-L"C:\Program Files\Microchip\MPLAB C30\lib",--script="p24FJ128GA010.gld",--defsym=__MPLAB_BUILD=1,-Map="MainMenu.map",--report-mem
MainMenu.o(.ndata+0x0):C:\Documents and Settings\Yaseen Khan\My Documents\My PIC uC\Winscor Documents\Winscor Source Backup\Feb 17\Winscor [1]\Winscor\MainMenu.c: multiple definition of `badminton_state_table'
badminton.o(.ndata+0x0):C:\Documents and Settings\Yaseen Khan\My Documents\My PIC uC\Winscor Documents\Winscor Source Backup\Feb 17\Winscor [1]\Winscor\badminton.c: first defined here
MainMenu.o(.nbss+0x0):C:\Documents and Settings\Yaseen Khan\My Documents\My PIC uC\Winscor Documents\Winscor Source Backup\Feb 17\Winscor [1]\Winscor\MainMenu.c: multiple definition of `sub_badminton_state'
badminton.o(.nbss+0x0):C:\Documents and Settings\Yaseen Khan\My Documents\My PIC uC\Winscor Documents\Winscor Source Backup\Feb 17\Winscor [1]\Winscor\badminton.c: first defined here
c:\program files\microchip\mplab c30\bin\pic30-coff-ld.exe: Link terminated due to previous error(s).
Link step failed.
```

I tried with/without "extern"...hmm...I am at a loss...As I really would like to have a seperature source/header for each sport i.e. badminton, basketball...I am not a big fan of putting the function pointer declaration i.e. 
```
void (*badminton_state_table[])() = {Num_Of_Games_State, Pnt_Per_Game_State, Start_Game_State};
```
in main source like the way dwhitney67  suggested...but I tried it putting the function pointer declaration there anyways and it doesn't work unless I put everything from badminton.h and badminton.c in the main source file...

---

### Post by Gordon Bennett on 2009-02-17
Enums can't be declared as extern, they are treated in a similar way to typedefs by the compiler.

---

### Post by dwhitney67 on 2009-02-17
This works for me:

Header.h:
```

#ifndef HEADER_H
#define HEADER_H

enum SubState { F1, F2, F3 };

void (*table[F3 + 1])();

void functionOne();
void functionTwo();
void functionThree();

#endif

```

Main.c:
```

#include "Header.h"

int main()
{
  table[F1] = functionOne;
  table[F2] = functionTwo;
  table[F3] = functionThree;

  table[F2]();
}

```

Other.c:
```

#include "Header.h"
#include <stdio.h>

void functionOne()
{
  printf("functionOne() has been called.\n");
}

void functionTwo()
{
  printf("functionTwo() has been called.\n");
  table[F1]();
  table[F3]();
}

void functionThree()
{
  printf("functionThree() has been called.\n");
}

```

```

gcc Main.c Other.c -o thisworks
./thisworks

```

---

### Post by nahky007 on 2009-02-18
> **dwhitney67 said:**
> This works for me:

Header.h:
```

#ifndef HEADER_H
#define HEADER_H

enum SubState { F1, F2, F3 };

void (*table[F3 + 1])();

void functionOne();
void functionTwo();
void functionThree();

#endif

```

Main.c:
```

#include "Header.h"

int main()
{
  table[F1] = functionOne;
  table[F2] = functionTwo;
  table[F3] = functionThree;

  table[F2]();
}

```

Other.c:
```

#include "Header.h"
#include <stdio.h>

void functionOne()
{
  printf("functionOne() has been called.\n");
}

void functionTwo()
{
  printf("functionTwo() has been called.\n");
  table[F1]();
  table[F3]();
}

void functionThree()
{
  printf("functionThree() has been called.\n");
}

```

```

gcc Main.c Other.c -o thisworks
./thisworks

```

Thanks for your suggestion...but I think the way I declared function pointer i.e. ```
void (*badminton_state_table[])() = {Num_Of_Games_State, Pnt_Per_Game_State, Start_Game_State};
```is causing the problem...I tried to declare the way you suggested in badminton.h```
void (*badminton_state_table[])();	
``` and in the main.c I have ```
	badminton_state_table[NUM_OF_GAMES] = Num_Of_Games_State;
	badminton_state_table[PNT_PER_GAME] = Pnt_Per_Game_State;
	badminton_state_table[START_GAME] = Start_Game_State;
while(1) {badminton_state_table[NUM_OF_GAMES]();}
``` ...but it it is giving still reporting the same multiple definition error...very weird...

---

### Post by hastur on 2009-02-18
hi,

```

void (*badminton_state_table[])() = {Num_Of_Games_State, Pnt_Per_Game_State, Start_Game_State};

```

in my opinion your problem here is, you're doing a double initialization of your table variable (from the point of view of the compiler : one in header included from main.c, another in header included from badmington.c) which is not good.

here is the way I handle this kind of conflicts (I don't know whether this should be considered "good programming practice", but it's usually clean enough for me)

header.h
```

#ifdef INIT_GLOBALS

int some_int = 0;
// or in your case
void (*badminton_state_table[])() = {Num_Of_Games_State, Pnt_Per_Game_State, Start_Game_State};

#else

extern int some_int;
extern void(*badminton_state_table[])();

#endif

```

main.c
```

#define INIT_GLOBALS
#include "header.h"

int main() {

...

}

```

prog.c
```

#include "header.h"

int prog() {

...

}

```

maybe there is another problem I didn't see whith the declaration of an array of function pointers, but if this can help...

ps : IMHO you should consider a typedef on your function pointer, which make the later declaration of arrays more readable :
```

fct_pt my_array[] = {fct_1, fct2};
// and
extern fct_pt *my_array;

```

---

### Post by dwhitney67 on 2009-02-18
> **nahky007 said:**
> ...

```

void (*badminton_state_table[])();

```
...

You didn't specify a size for the table; maybe that would help.

Also, providing all of your code would help too.  That allows another person to compile and troubleshoot it.

---

### Post by weresheep on 2009-02-18
> **dwhitney67 said:**
> 
This is not true; if two or more separate source (.c) files include the same header file, regardless if the inclusion guards are present, the compiler will attempt to create multiple variables, should they be initialized with a value.  This of course leads to the problem the OP is experiencing.


I seem to have gotten myself confused over this issue. I refreshed my memory on the subject and see what you're saying. I don't know why I though #ifndef's would have an effect with multiple source files in this situation :oops:

I normally stay clear of this whole area by never defining (or even declaring) variables in header files, that way I keep myself from getting all confused :D

Thanks for pointing out my error.

-weresheep

---

### Post by nahky007 on 2009-02-18
> **dwhitney67 said:**
> You didn't specify a size for the table; maybe that would help.

Also, providing all of your code would help too.  That allows another person to compile and troubleshoot it.

Hello, I tried an arbitrary number for the size of the table before, it didn't work either. 

but here's the full code: 

```
#ifndef BADMINTON_H
#define BADMINTON_H

extern char deuce_threshold ; //********setting up some test deuce threshold value....CHANGE!
extern char num_of_games; //This variable is to be configured by the player
extern char pnt_per_game; //This variable is to be configured by the player
extern char deuce_threshold_set; 
extern char game_in_progress_flag; //This variable/flag to be used so that if a game is in progress do not ask the user to repeat settings

extern char player1_score;
extern char player2_score; 

typedef enum 
{	
//the sequence of the list below is VERY important since it determines the value of the named integer  e.g. NUM_OF_GAMES,PNT_PER_GAME etc ...(will be added as neccessary
//this value is also used by state_table[current_state] pointer as a indexes. That's why it is very important
//The sequence of the state integer constants has to be same as state table pointer which is declared later in the program 	
	
	NUM_OF_GAMES,
	PNT_PER_GAME,
	START_GAME
}Sub_State_Type;

Sub_State_Type sub_badminton_state;

void DisplayNumber(int number); //This function is used for Badminton state to convert game/point # to ASCII and print on LCD NOT A STATE!

void Num_Of_Games_State (void);
void Pnt_Per_Game_State (void); 
void Start_Game_State (void);




//This table contains a pointer to the function to call each state
void (*badminton_state_table[])() = {Num_Of_Games_State, Pnt_Per_Game_State, Start_Game_State};

	
	
//void (*badminton_state_table[])();	






#endif
```



```

#include<p24fj128ga010.h>
#include "badminton.h"
#include"lcd.h"
#include"buttons.h"


// Sub_State_Type sub_badminton_state;

//This table contains a pointer to the function to call each state
//void (*badminton_state_table[])() = {Num_Of_Games_State, Pnt_Per_Game_State, Start_Game_State};



void DisplayNumber(int number) //This function is used for Badminton state to convert game/point # to ASCII and print on LCD NOT A STATE!
{

	//to print/display something on LCD
	
}


void Num_Of_Games_State (void) //The user have to selection number of games to played by pressing button 1, button2 to changes numbers, button 3 to accept
								//the selected number, and button 4 to go back...
{
	
	sub_badminton_state = NUM_OF_GAMES;
	num_of_games = 3; //Default

	//have to add code 
		
			
}

void Pnt_Per_Game_State(void)
{
	
	sub_badminton_state = PNT_PER_GAME;
	//have to add code so that user can set up points per game
	
	
}

void Start_Game_State (void) //Actual game algorithm, if player 1 scores, he/she presses button 1 on hardware
							//if player 2 score, he/she presses button 2 to on hardware
{

	//have to add codes
	
	
}

	
	



```

```
#include<p24fj128ga010.h> //This file is a microcontroller specific file
#include <stdio.h>
#include <stdlib.h>
#include"buttons.h"
#include"lcd.h"
#include"badminton.h"





	
// main loop
int main (void)
{
	
	//initialization of variables

	char temp; //This variable is used for debugging purpose to set up breakpoints
	
	//various initialization routines
//	LCDinit();
//	BtnInit(); 
//	MainMenuState();	
//	badminton_state_table[NUM_OF_GAMES] = Num_Of_Games_State;
//	badminton_state_table[PNT_PER_GAME] = Pnt_Per_Game_State;
//	badminton_state_table[START_GAME] = Start_Game_State;


	

	while (1)
	{
	
//		state_table[current_state]();
//		state_table[BADMINTON]();
		temp = 1; //This variable was used for debug purpose, delete it later
		
		badminton_state_table[NUM_OF_GAMES](); //I didn't really care about other states, I just wanted to test one state to make it work first, that's why I called the same state to go to all the time. 
	}	
	
	return 0;
}

```


I am using C to develop codes for a microchip PIC microcontroller, a lot of the things are hardware specific. But standard C is still applied. I just tried to compile this code as above and still giving me the same problem..:(

```
Executing: "C:\Program Files\Microchip\MPLAB C30\bin\pic30-gcc.exe" -mcpu=24FJ128GA010 -x c -c   "badminton.c" -o"badminton.o" -g -Wall
Microchip MPLAB C30 License Manager Version v3.00 (Build Date Feb 28 2007).
Copyright (c) 2005 Microchip Technology Inc. All rights reserved.
The MPLAB C30 license has expired.
pic30-coff-cc1.exe: warning: Options have been disabled due to expired license
In file included from badminton.c:3:
badminton.h:36: warning: 'badminton_state_table' initialized and declared 'extern'
In file included from badminton.c:3:
badminton.h:47:7: warning: no newline at end of file
In file included from badminton.c:4:
lcd.h:31:62: warning: no newline at end of file
Executing: "C:\Program Files\Microchip\MPLAB C30\bin\pic30-gcc.exe" -mcpu=24FJ128GA010 -x c -c   "MainMenu.c" -o"MainMenu.o" -g -Wall
Microchip MPLAB C30 License Manager Version v3.00 (Build Date Feb 28 2007).
Copyright (c) 2005 Microchip Technology Inc. All rights reserved.
The MPLAB C30 license has expired.
pic30-coff-cc1.exe: warning: Options have been disabled due to expired license
In file included from MainMenu.c:5:
lcd.h:31:62: warning: no newline at end of file
In file included from MainMenu.c:6:
badminton.h:36: warning: 'badminton_state_table' initialized and declared 'extern'
In file included from MainMenu.c:6:
badminton.h:47:7: warning: no newline at end of file
Executing: "C:\Program Files\Microchip\MPLAB C30\bin\pic30-gcc.exe" -mcpu=24FJ128GA010 "buttons.o" "lcd.o" "badminton.o" "MainMenu.o" -o"MainMenu.cof" -Wl,-L"C:\Program Files\Microchip\MPLAB C30\lib",--script="p24FJ128GA010.gld",--defsym=__MPLAB_BUILD=1,-Map="MainMenu.map",--report-mem
MainMenu.o(.ndata+0x0):C:\Documents and Settings\Yaseen Khan\My Documents\My PIC uC\Winscor Documents\Winscor Source Backup\Feb 17\Winscor [1_1]\Winscor\MainMenu.c: multiple definition of `badminton_state_table'
badminton.o(.ndata+0x0):C:\Documents and Settings\Yaseen Khan\My Documents\My PIC uC\Winscor Documents\Winscor Source Backup\Feb 17\Winscor [1_1]\Winscor\badminton.c: first defined here
MainMenu.o(.nbss+0x0):C:\Documents and Settings\Yaseen Khan\My Documents\My PIC uC\Winscor Documents\Winscor Source Backup\Feb 17\Winscor [1_1]\Winscor\MainMenu.c: multiple definition of `sub_badminton_state'
badminton.o(.nbss+0x0):C:\Documents and Settings\Yaseen Khan\My Documents\My PIC uC\Winscor Documents\Winscor Source Backup\Feb 17\Winscor [1_1]\Winscor\badminton.c: first defined here
c:\program files\microchip\mplab c30\bin\pic30-coff-ld.exe: Link terminated due to previous error(s).
Link step failed.
----------------------------------------------------------------------
Release build of project `C:\Documents and Settings\Yaseen Khan\My Documents\My PIC uC\Winscor Documents\Winscor Source Backup\Feb 17\Winscor [1_1]\Winscor\MainMenu.mcp' failed.
Wed Feb 18 22:21:29 2009
----------------------------------------------------------------------
BUILD FAILED

```

I hope this helps...

---

### Post by weresheep on 2009-02-19
Hello again,

I've restructured your code a bit and got it compiling (I've also reformatted it into my preferred style to make it easier for me. Appologies if this makes things confusing).

Basically, I've moved all declarations and definitions of variables out of the header file. The function pointer table has been moved into the main source file. The extra state variables I've moved into badminton.c.

I've also added the static scope modifier to the moved variables. This makes them visible only within the source file they are defined in.

These files now compile for me with

```
 gcc -Wall -ansi -pedantic main.c badminton.c 
```

main.c
```

#if 0
#include <p24fj128ga010.h> /* This file is a microcontroller specific file */
#endif

#include <stdio.h>
#include <stdlib.h>

#if 0
#include "buttons.h"
#include "lcd.h"
#endif

#include "badminton.h"


/* Set up a local (file scope) array of function pointers that point to
implementations in badminton.c. This table contains a pointer to the
function to call each state */
static void (*badminton_state_table[])()
  = {Num_Of_Games_State, Pnt_Per_Game_State, Start_Game_State};


int main (void) {
  /* Initialization of variables */

  /* This variable is used for debugging purpose to set up breakpoints */
  char temp;

  /* Various initialization routines */
#if 0
  LCDinit();
  BtnInit();
  MainMenuState();
#endif
  badminton_state_table[NUM_OF_GAMES] = Num_Of_Games_State;
  badminton_state_table[PNT_PER_GAME] = Pnt_Per_Game_State;
  badminton_state_table[START_GAME] = Start_Game_State;

  for (;;) {
#if 0
    state_table[current_state]();
    state_table[BADMINTON]();
#endif
    /* This variable was used for debug purpose, delete it later */
    temp = 1;

    /* I didn't really care about other states, I just wanted to test one
    state to make it work first, that's why I called the same state to go to
    all the time. */
    badminton_state_table[NUM_OF_GAMES]();
  }

  return 0;
}



```

badminton.c
```

#if 0
#include <p24fj128ga010.h>
#endif

#if 0
#include "buttons.h"
#include "lcd.h"
#endif

#include "badminton.h"

/* Define file scope variables. */
static Sub_State_Type sub_badminton_state;
static char num_of_games;



/* This function is used for Badminton state to convert game/point # to ASCII
and print on LCD NOT A STATE! */
void DisplayNumber(int number) {
  /* to print/display something on LCD */
}


/* The user have to selection number of games to played by pressing button 1,
button2 to changes numbers, button 3 to accept the selected number, and
button 4 to go back... */
void Num_Of_Games_State(void) {
  sub_badminton_state = NUM_OF_GAMES;
  num_of_games = 3; /* Default */

  /* have to add code */
}


void Pnt_Per_Game_State(void) {
  sub_badminton_state = PNT_PER_GAME;
  /* have to add code so that user can set up points per game */
}


/* Actual game algorithm, if player 1 scores, he/she presses button 1 on
hardware if player 2 score, he/she presses button 2 to on hardware */
void Start_Game_State(void) {
  /* have to add codes */
}


```

badminton.h
```

#ifndef BADMINTON_H
#define BADMINTON_H

typedef enum {
  /* The sequence of the list below is VERY important since it determines the
  value of the named integer  e.g. NUM_OF_GAMES, PNT_PER_GAME etc ...(will be
  added as neccessary this value is also used by state_table[current_state]
  pointer as a indexes. That's why it is very important The sequence of the
  state integer constants has to be same as state table pointer which is
  declared later in the program */
  NUM_OF_GAMES, PNT_PER_GAME, START_GAME
} Sub_State_Type;


/* This function is used for Badminton state to convert game/point # to ASCII
and print on LCD NOT A STATE! */
void DisplayNumber(int number);

void Num_Of_Games_State(void);

void Pnt_Per_Game_State(void);

void Start_Game_State(void);

#endif

```

-weresheep

---

### Post by dwhitney67 on 2009-02-19
@ nahky007 -

I get the strong impression that you did not reference the sample code I posted two days ago.  If you had, you probably would have resolved your application's link problem by now.

Here's your code, cleaned up a bit of course, and compilable/linkable...

badminton.h:
```

#ifndef BADMINTON_H
#define BADMINTON_H

char deuce_threshold;
char num_of_games;
char pnt_per_game;
char deuce_threshold_set;
char game_in_progress_flag;

char player1_score;
char player2_score;

typedef enum
{
  NUM_OF_GAMES,
  PNT_PER_GAME,
  START_GAME
} Sub_State_Type;

Sub_State_Type sub_badminton_state;

void Display_Number(int number);
void Num_Of_Games_State();
void Pnt_Per_Game_State();
void Start_Game_State();

void (*badminton_state_table[START_GAME + 1])();

#endif

```

badminton.c:
```

#include "badminton.h"
/*
#include<p24fj128ga010.h>
#include"lcd.h"
#include"buttons.h"
*/
#include <stdio.h>


void Display_Number(int number)
{
}


void Num_Of_Games_State()
{
  printf("Num_Of_Games_State() called.\n");
  printf("num_of_games = %c\n", num_of_games);

  sub_badminton_state = NUM_OF_GAMES;
  num_of_games = 3;
}


void Pnt_Per_Game_State()
{
  printf("Pnt_Per_Game_State() called.\n");

  sub_badminton_state = PNT_PER_GAME;
}


void Start_Game_State()
{
  printf("Start_Game_State() called.\n");
}

```

main.c:
```

#include"badminton.h"
/*
#include<p24fj128ga010.h> //This file is a microcontroller specific file
#include"buttons.h"
#include"lcd.h"
*/
#include <stdio.h>
#include <stdlib.h>

int main()
{
  /* initialize function table */
  badminton_state_table[NUM_OF_GAMES] = Num_Of_Games_State;
  badminton_state_table[PNT_PER_GAME] = Pnt_Per_Game_State;
  badminton_state_table[START_GAME]   = Start_Game_State;

  num_of_games = '3';

  /* test calling each function */
  badminton_state_table[NUM_OF_GAMES]();
  badminton_state_table[PNT_PER_GAME]();
  badminton_state_table[START_GAME]();

  return 0;
}

```

To compile/link:
```

gcc -Wall -ansi -pedantic badminton.c main.c -o badminton

```

P.S.  Please confirm if you indeed wanted to declare some of your variables in badminton.h as 'char', or if you really want to declare them as 'unsigned int'.

---

### Post by nahky007 on 2009-02-19
To dwhitney67 and weresheep: 

Hey guys, 
thanks so much! 
I am going out of town for couple of days but I will definitely try to run these codes as soon as I get home...
I really appreciate your help with this very weird error...
Talk to you guys later.

---

