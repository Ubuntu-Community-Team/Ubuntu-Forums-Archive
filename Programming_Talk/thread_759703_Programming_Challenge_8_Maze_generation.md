---
title: "Programming Challenge 8: Maze generation"
date: 2008-04-19
forum: Programming Talk
---

### Post by heikaman on 2008-04-19
Hello everyone...

**The new challenge is divided into two tasks:**
[INDENT][LIST=1]
[*]Generate a 2D maze, where there is one path from start to end.
[*]Traverse the maze by drawing a line from start to end.
[/LIST][/INDENT]
	
**Note:**
[INDENT]To make this challenge more accessible, you can do either or both parts of the challenge and still win (that is if you can't generate the maze, use one of the attached mazes).[/INDENT]
	
**Rulez:**
[INDENT][LIST=1]
[*]Feel free to use any available graphics library, for example **Cairo**.
[*]If there's an algorithm/library/whatever to generate/traverse the maze **Don't use it** :)
[/LIST][/INDENT]
	
**How to increase your odds of winning:**
[INDENT]"This is only to increase your odds of winning, and **NOT** mandatory."
[LIST=1]
[*]First of all be creative.
[*]Try to animate the solution.
[*]Generate a non-rectangular maze (see the example).
[*]3D maze.
[/LIST].[/INDENT]

**Due date:**	
[INDENT]You have until next Saturday. That's all have fun coding :) .[/INDENT]

---

### Post by WW on 2008-04-19
Definitely a fun problem, but a repeat: [http://ubuntuforums.org/showthread.php?t=374760](http://ubuntuforums.org/showthread.php?t=374760)

---

### Post by heikaman on 2008-04-19
oops...

I have to change it  :(   right ?

---

### Post by WW on 2008-04-19
Not necessarily.  I'm sure there are a lot of people around who didn't try it last time. Even if they did write a program last time, they could try it again with a new algorithm, or a new language, or a new method to display the maze.

---

### Post by heikaman on 2008-04-19
:D Then I'll leave it, because I really like this challenge.
And I'm waiting for your python solution :mrgreen:

---

### Post by WW on 2008-04-19
> **heikaman said:**
> :D Then I'll leave it, because I really like this challenge.
And I'm waiting for your python solution :mrgreen:
Check out the old maze challenge.  I have continued working on that hexagonal maze since last year, to the point where it is now a game that my nieces can play.

---

### Post by nvteighen on 2008-04-19
Ouch, the same as always: I think I've the theory to do this, but when I get to write the code I get to incredible and funny disasters.

---

### Post by heikaman on 2008-04-19
> **WW said:**
> Check out the old maze challenge...

@WW I did, and it looks great !, maybe you can use the same code to generate the maze in 3D, that would be so cooool.

> **nvteighen said:**
> Ouch, the same as always: I think I've the theory to do this, but when I get to write the code I get to incredible and funny disasters.

@nvteighen Although this is not an "Elliptic Curve Challenge" :lolflag: you still have a good chance to win, and even if you don't win you still get to learn new stuff. :)

If you all agree that I better change the challenge (and that I can) I will change it just let me know, I'll check the thread again tomorrow.

---

### Post by meanburrito920 on 2008-04-19
How would the maze be input into the program? Would the program only have to solve mazes that it generated itself (which would avoid input errors and the like)?

---

### Post by heikaman on 2008-04-19
> **meanburrito920 said:**
> How would the maze be input into the program? 

The program will generate/read the maze from an image, any extension will do.

> **meanburrito920 said:**
> Would the program only have to solve mazes that it generated itself (which would avoid input errors and the like)?

Yes, that is if the program generates mazes, you don't have to generate the maze you can use one of the attached mazes.

---

### Post by nvteighen on 2008-04-20
> **heikaman said:**
> 
@nvteighen Although this is not an "Elliptic Curve Challenge" :lolflag: you still have a good chance to win, and even if you don't win you still get to learn new stuff. :)

:lolflag: (The worst: I felt ashamed and I deleted that code...)

I feel motivated! I'll try the maze-solver first. (And surely I'll get a Riemann-space generator or something strange, but let's see :p...)

---

### Post by bobdob20 on 2008-04-22
This is my first challenge so i hope my code is ok. My C isn't very good, so my code is a bit messy. I haven't worked out how it generate a maze yet, but it can solve them.

main.c
[PHP]#include <ncurses.h>

struct
{
	int col;
	int row;
} start, finish, current;

void solve_maze(char filename[])
{
	FILE * maze_file;
	maze_file = fopen (filename, "r");
	int maze_cols, maze_rows, i, j;
	if (maze_file != NULL)
	{
		fscanf (maze_file, "%d%d ", &maze_cols, &maze_rows);
		int maze[maze_cols][maze_rows];
		for (i = 0; i < maze_rows; i++)
		{
			for (j = 0; j < maze_cols; j++)
			{
				
				maze[j][i] = fgetc (maze_file);
			}
		}

		fclose (maze_file);
		for (i = 0; i < maze_rows; i++)
		{
			if (maze[0][i] == '0') 
			{
				start.row = i;
				start.col = 0;
			}
		}
		for (i = 0; i <maze_rows; i++)
		{
			if (maze[maze_cols-1][i] == '0')
			{
				finish.row = i;
				finish.col = maze_cols-1;
			}
		}

		maze[start.col][start.row] = '2';
		current = start;
		while (current.col != finish.col || current.row != finish.row)
		{
			if (maze[current.col+1][current.row] == '0') current.col++;
			else if (maze[current.col-1][current.row] == '0') current.col--;
			else if (maze[current.col][current.row+1] == '0') current.row++;
			else if (maze[current.col][current.row-1] == '0') current.row--;
			else 
			{
				maze[current.col][current.row] = '3';
				if (maze[current.col+1][current.row] == '2') current.col++;
				else if (maze[current.col-1][current.row] == '2') current.col--;
				else if (maze[current.col][current.row+1] == '2') current.row++;
				else if (maze[current.col][current.row-1] == '2') current.row--;
			}
			maze[current.col][current.row] = '2';
		}

		int ter_rows, ter_cols;
		getmaxyx (stdscr, ter_rows, ter_cols);

		if (maze_cols*2 <= ter_cols && maze_rows <= ter_rows)
		{
			for (i = 0; i < maze_rows; i++)
			{
				for (j = 0; j < maze_cols; j++)
				{
					if (maze[j][i] == '1')
					{
						attron (A_REVERSE);
						mvprintw(i, j*2, "  ");
					}
					else if (maze[j][i] == '0' || maze[j][i] == '3')
						mvprintw(i, j*2, "  ");

					else if (maze[j][i] == '2')
						mvprintw(i, j*2, "##");

					attroff (A_REVERSE);
				}
			}
		}
	}
	else
		printw ("Invalid File!");
}

int main()
{
	char option;
	char filename[50];
	initscr();
	while (option != 'q')
	{
		clear();
		printw ("Maze Challenge!\nSelect an option from below.\n\n");
		printw ("Option                                  key\n");
		printw ("1. Solve a maze.                         s\n");
		printw ("2. Exit.                                 q\n");
		refresh();
		option = getch();
		clear();
		switch (option)
		{
			case 's':
			case 'S':
				printw ("Choose a maze from the list below\n\n");
				printw ("%s\n", system("ls *.maze"));
				getstr (filename);
				clear();
				solve_maze (filename);
				getch();
				break;
		}
	}
	refresh();
	endwin();
	return 0;
}[/PHP]

Compile with:
```
 gcc -o maze main.c -lncurses 
```

test.maze
```
21 11 111111111111111111111000000100000100000001101110101110101111101101000100010001010001101111111011101010111100010001000100010101111010111010111110101100000100010001000001101111101011111011111100000001000100000000111111111111111111111

```


It read the maze from a file "test.maze" which has to be written by hand until it can generate a maze. Therefore i have only tried it with 2 mazes, but they both seem to work.

Any hints or tips how to make it better would be appreciated.

EDIT: OK, I took out the print_maze function because it didn't do anything that solve_maze did, and it was only really for me to work out how i would open and display a maze. I've tried to add a menu to display the maze files in the current directory, but system("ls") doesn't seem to want to work. The name of maze file can just be written in tho.


A screenshot of the maze above is attach so is the source file + maze file.

---

### Post by heikaman on 2008-04-22
Good work !:) here's my suggestions:

**1-** I noticed you reopen the maze file every time you call print_maze or solve_maze. So, I think it's better to open the maze once in the main function and maybe save it in a **buffer**, any data structure will do.

**2-** This is a better print_maze function, with the same result:

[PHP]
void print_maze(){       
    char next_char='0';

    while(next_char != EOF){    	
    	next_char=fgetc (maze_file);
    	switch(next_char){
    		case '0':{
	    		attroff (A_REVERSE);
    		    	printw("  ");
    			break;
    		}
    		case '1':{
	    		attron (A_REVERSE);
    		    	printw("  ");
    			break;
    		}
    		case '\n':{
	    		attroff (A_REVERSE);
    			printw("\n");
    			break;
    		}    		
    	}

    }
    attroff (A_REVERSE);
}
[/PHP]

Now you don't have to hardwire the rows and columns into the maze file, and the maze file can look like this:

```

111111111111111111111
000000100000100000001
101110101110101111101
101000100010001010001
101111111011101010111
100010001000100010101
111010111010111110101
100000100010001000001
101111101011111011111
100000001000100000000
111111111111111111111


```

which is more readable, however, I think you have to edit solve_maze too if you use it.

**3-** Edit your post and attach the source file, test file and a screen shot.

**4-** Check out **Cairo**:
[http://cairographics.org/]("http://cairographics.org/")

---

### Post by heikaman on 2008-04-22
> **bobdob20 said:**
> 
I've tried to add a menu to display the maze files in the current directory, but system("ls") doesn't seem to want to work.


use popen:

[http://ubuntuforums.org/showthread.php?t=761500]("http://ubuntuforums.org/showthread.php?t=761500")

or just make the program take command line arguments.

---

### Post by heikaman on 2008-04-26
well...
After careful examination of *ALL* the solutions :biggrin:, I've reached the logical conclusion that **bobdob20** is the winner of this challenge.

=D> =D> =D> =D> =D>

---

### Post by bobdob20 on 2008-04-26
Nice, won by default. :lolflag: 
I'll have to try some more challenges if i have some time.

---

### Post by Lux Perpetua on 2008-04-27
Congratulations. :-) It's your job to set the next challenge.

---

### Post by Lster on 2008-04-27
I nearly forgot! Congrats bobdob20. :)

---

### Post by bobdob20 on 2008-04-27
> **Lux Perpetua said:**
> Congratulations. :-) It's your job to set the next challenge.

So i have to choose the next challenge. :-k

Anyone got any ideas/suggestions, because i can't think of anything at the moment.

---

### Post by meanburrito920 on 2008-04-27
I was thinking it would be interesting to have people build their own libraries to do bitwise operations. Obvously you would have to require that predefined high level data structures be used, seeing as how it would otherwise be too easy to implement in C compared to higher level languages like Python. They would have to implement AND, OR, XOR, NOT and addition/subtraction and multiplication/division functions. For bonus points you could have them write functions to translate other variables to binary in their chosen data stucture. The resulting libraries would be more informative than useful, but knowing how low level data processing works is always a good thing to know. Thats my idea, I don't know how good it is but it sounds interesting to me.

---

### Post by bobdob20 on 2008-04-27
You seem to know more about programming than me, but it does sound quite interesting. I will have a think about some possible challenge, but if no one has any objections I will probably choose your one.

---

### Post by heikaman on 2008-04-27
No objections just another idea, **nvteighen** was talking here [**[B]_thread_**[/B]]("http://ubuntuforums.org/showthread.php?t=770990") about implementing the **Vigenère cipher** [**_wikipedia_**]("http://en.wikipedia.org/wiki/Vigen%C3%A8re_cipher")
I've actually read the wiki and it seems like alot of fun, and easy to understand and implement.

---

### Post by meanburrito920 on 2008-04-27
See [http://en.wikipedia.org/wiki/Bitwise_operation](http://en.wikipedia.org/wiki/Bitwise_operation) for more info on what I'm talking about. It actually is a pretty good article.

---

### Post by meanburrito920 on 2008-04-27
@heikaman- Good idea. Cyphers in general are fun to write (and use). It reminded me of the thread under community games, [http://ubuntuforums.org/showthread.php?t=647847](http://ubuntuforums.org/showthread.php?t=647847) where everything is written in binary. A binary/plaintext translator would be another cool idea.

---

### Post by bobdob20 on 2008-04-27
> **heikaman said:**
> No objections just another idea, **nvteighen** was talking here [**[B]_thread_**[/B]]("http://ubuntuforums.org/showthread.php?t=770990") about implementing the **Vigenère cipher** [**_wikipedia_**]("http://en.wikipedia.org/wiki/Vigen%C3%A8re_cipher")
I've actually read the wiki and it seems like alot of fun, and easy to understand and implement.

I think this is a good idea and doesn't seem to difficult. Since there was minimal participance in the last challenge and it being exam time, an easier challenge might be welcome.

Should i just start a new thread for this challenge?

---

### Post by meanburrito920 on 2008-04-27
Yessir. With the title of 'Programming Challenge 9: ' + name_of_challenge. I wish I could start the challenge now, but I have real work to do :( I'll have to wait and have playtime later...

---

### Post by mssever on 2008-04-27
My suggestion:

Design a correct floating point math algorithm. For example, in Python, 0.1 + 0.2 == 0.30000000000000004, while in Ruby, 0.1 + 0.2 == 0.3, the correct answer.

---

### Post by nvteighen on 2008-04-28
> **heikaman said:**
> No objections just another idea, **nvteighen** was talking here [**[B]_thread_**[/B]]("http://ubuntuforums.org/showthread.php?t=770990") about implementing the **Vigenère cipher** [**_wikipedia_**]("http://en.wikipedia.org/wiki/Vigen%C3%A8re_cipher")
I've actually read the wiki and it seems like alot of fun, and easy to understand and implement.
Hey, don't steal my ideas ;)

(Just kidding...)

---

