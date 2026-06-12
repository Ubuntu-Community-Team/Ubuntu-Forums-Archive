---
title: "Programming Challenge 7: Displaying Trees"
date: 2008-04-06
forum: Programming Talk
---

### Post by smartbei on 2008-04-06
In short, the goal of this challenge is to create a program that displays a given tree.

**Rules**
[LIST]
[*]The input must come from a file. See below for the file's structure.
[*]You may not use any pre-written graph/tree displaying libraries (:p). 
**Clarification:**  [i]
You are allowed and encouraged to use graphic frameworks/toolkits/libraries/modules/packages (i.e. OpenGL, pyGame, GD, etc.). What you are specifically not allowed to do is use existing frameworks/toolkits/libraries/modules/packages and create a wrapper around them or something along those lines.[/i]
[/LIST]

**File Structure**
The file is organized such that each line represents a link between two nodes, where each node is identified by a number. The lowest identifier is the root node. For example:
```

1,2
1,3
1,4
2,5
2,6
6,8
6,9
5,7

```
Means:
```

    1
   /|\
  2 3 4
 / \
5   6
|  / \
7 8   9

```

**Definitions**
By tree I mean a graph with no circular references. For more information, [Wikipedia]("http://en.wikipedia.org/wiki/Tree_%28graph_theory%29").

**Output**
The output should be a visual display of the tree. Note that the identifiers of the nodes do not have to be displayed.

**Scoring**
Scoring will be based generally on 'niceness' of the display, on the creativity of the medium, etc. Bonuses will be awarded for ability to display all graphs (not just trees). Correct validation of the input file is also worth some points :).

**Good Luck!** - Winner will be chosen (EDIT - this is the previous due date, see below) Sunday April 13th.

**Challenge Due Date Change**
The challenge due date has been pushed back for personal logistic reasons to **Thursday, April 17th at 18:00 GMT +2**. I hope this will allow more people to participate - and sorry if it keeps you in suspense :d.

---

### Post by slavik on 2008-04-06
what if there is something like:
```

1,2
1,3
1,4
1,10
1,11
1,12
2,5
2,6
6,8
6,9
5,7

```

how should the children be displayed then?

---

### Post by smartbei on 2008-04-06
@slavik:
I fail to see the problem - remember the identifiers are just so the processing program knows which node is which for the linking. The input you gave just means that the root node (1) has six children, 1 of which (2) has 2 children of its own, one of which (6) has two children of its own and the other (5) has one child.

---

### Post by slavik on 2008-04-06
right, but then without using a true graphics library (opengl or similar) it becomes difficult to display the result (that node 1 has 6 children.

---

### Post by smartbei on 2008-04-06
You are allowed to use OpenGL, and other graphic libraries. What I meant was that you may not use libraries that have functions designed for displaying trees/graphs.

---

### Post by alexforcefive on 2008-04-06
You get points for niceness of the display, so it probably still counts if you do

```

     1
| | | |  |  |
2 3 4 10 11 12
```

---

### Post by smartbei on 2008-04-06
Yes, though you may want the lines to line up with the numbers . :)

(when posting, it is a variable width font but when it is displayed in code tags it is fixed width)

---

### Post by Wybiral on 2008-04-06
Interesting!

---

### Post by scragar on 2008-04-06
is it within the rules to use the GD libary to make it more graphical and easier to follow?(with the root node being the middle to make things easier to follow)

---

### Post by Wybiral on 2008-04-06
Wait... Are multiple roots possible (as in, separate trees within the data)?

---

### Post by smartbei on 2008-04-06
Since this appears unclear, I will add an explanation in the OP.

You are allowed and encouraged to use graphic frameworks/toolkits/libraries/modules/packages. What you are specifically not allowed to do is use existing frameworks/toolkits/libraries/modules/packages and create a wrapper around them or something along those lines.

@Wybiral: Well, since the root is defined as the node with the lowest identifier, I can't really see how multiple roots would work. I don't think seperate trees are allowed, since they cannot have a root - due to the mentioned definition of root.

---

### Post by nick_h on 2008-04-06
I think the challenge is probably complex enough with a single tree.  Multiple trees would be easy enough to handle once a solution for a single tree is found.

A solution for graphs in general will require a bit more thought.

---

### Post by scragar on 2008-04-06
are the files nesseseraly in order? with parents before childs all the time? Or do we have to have a sorting system first?

---

### Post by smartbei on 2008-04-06
The file is not necessarily in order.This shouldn't really matter though...

---

### Post by Wybiral on 2008-04-06
> **smartbei said:**
> @Wybiral: Well, since the root is defined as the node with the lowest identifier, I can't really see how multiple roots would work. I don't think seperate trees are allowed, since they cannot have a root - due to the mentioned definition of root.

OK, I was just wondering if it were possible to get a graph like:

```

1,2
3,4

```

(where 1 and 3 are both roots, of two separate trees).

But it's ALWAYS going to be one connected tree, right?

---

### Post by alexforcefive on 2008-04-06
> **smartbei said:**
> Yes, though you may want the lines to line up with the numbers . :)

(when posting, it is a variable width font but when it is displayed in code tags it is fixed width)

pfft, you think you're so smart! :p

I have the tricky part done I think, now I just need to prettify the output. For your example, my script outputs :

```
1 :  2 3 4
2 :  5 6 
5 :  7
6 :  8 9

```

I really hope that was the hard part! This is my first challenge :D (still in my first week of python)

---

### Post by alexforcefive on 2008-04-07
double post but whatever :p

> **smartbei said:**
> @Wybiral: Well, since the root is defined as the node with the lowest identifier, I can't really see how multiple roots would work. I don't think seperate trees are allowed, since they cannot have a root - due to the mentioned definition of root.

What about a node with multiple parent nodes? For example

```
1,3
2,3
```

is really:

```
1 2
\ /
 3
```

but my script looks at each node separately so we get:

```
1 2
| |
3 3
```

Trying to check for and arrange multiples is going to be pretty hard. Is it in the scope of this challenge?

---

### Post by smartbei on 2008-04-07
There can only be one 'root' node. In your example, that is 1 (since it has the lowest identifier). So your example has a root node (1) with a child (3). That child (3) has a link to another node (2). That node (2) therefore must be a child of (3).

Think of it this way: All the file defines is a bunch of links between nodes. Their order in the file (1,2 vs. 2,1) does not matter, since all that is defined is a link.

Similarly, the file might look like:
```

3,4
4,11
11,1
1,2

```
And this is perfectly equivalent (structure-wise) to:
```

1,2
1,3
3,4
4,5
(1 = 1, 2 = 2, 3 = 11, 4 = 4, 5 = 3)

```

---

### Post by Wybiral on 2008-04-07
So the data "1,2\n3,4" is never possible? Or does 3 have some kind of implied connection with 1? One last question: do the numbers indicate the order (as in, the tree has to be sorted), or are they just handles for the nodes?

---

### Post by smartbei on 2008-04-07
That would be considered bad data. (Which the proram should probably detect)

Numbers are just handles - the order does not matter.

---

### Post by WW on 2008-04-07
Here's an entry to get things started.  It is written in Python, and uses Pygame to display the tree.  The program is called treeplot.py; the data file is given as a command line argument.  Other command line options include:
  -s *style*
  -m *magnification*
  -c *(R,G,B)*
where *style* is either 'straight' (the default) or 'circuit', *magnification* controls the size of the graph, and *(R,G,B)* is the color. 

If I had time, there are many things I would improve:

1. I constrained the display of the tree so that all nodes of the same depth are on the same horizontal line, with a minimum horizontal spacing.  The vertical spacing between depths is also fixed.  Relaxing these constraints (and using a smarter algorithm) could lead to nicer output.

2. It doesn't reorder the nodes in any way; a smart reordering might lead to neater graphs.

3. The rules say that the labels do not have to be displayed, so I didn't show them, but if I spent more time on it, that would be the first feature I would add.

4. I haven't tried it on graphs that are not trees; it might break.

5. It doesn't check for errors in the input file.


Here are some examples.  The results are attached as png files.

**smartbei.example.dat**
> 
3,4
4,11
11,1
1,2


**bchain2.dat**
> 
1,2
1,3
2,4
2,5
4,6
4,7
6,8
6,9
8,10
8,11
10,12
10,13


**tree3.dat**
> 
1,2
1,3
1,4
1,5
1,6
2,90
3,91
6,7
5,10
5,11
5,12
5,13
5,14
10,20
10,21
10,22
20,31
20,32
32,40
32,41
32,42
32,43
32,44
7,50
7,51
7,52
52,60
60,70
70,80

The tree3 graph was created with the command
[php]
./treeplot.py -m 30 -l 1 -c '(220,100,0)'  tree3.dat 
[/php]

---

### Post by nick_h on 2008-04-07
> Here's an entry to get things started.
This looks like a good solution.  It also works with the test files I am using.
 
I think that keeping nodes at the same depth at the same level on the display is an advantage.  I agree that node numbering would be nice.

The only problem I can see is that it uses nearly 100% of my CPU after it has finished displaying the tree.

---

### Post by Lux Perpetua on 2008-04-07
This is a good challenge, since it's easy to get something functional, but it has a lot of room for creativity. Once you have the code that parses the input and builds an internal representation of the tree/graph, the rest is completely open-ended. 

I have an idea, so I'll definitely try to submit something. :-)

---

### Post by smartbei on 2008-04-07
@nick_h: The 100% CPU is just because he forgot to put a sleep in the loop that waits for the user to exit. If you have the code open, just add time.sleep(0.01) to the end of the loop (and make sure the module time is imported of course).

@WW: Very nice solution - and you cranked it out fast too :).

---

### Post by nick_h on 2008-04-07
> just add time.sleep(0.01) to the end of the loop
Thanks, that fixed it.

---

### Post by WW on 2008-04-07
> **nick_h said:**
> 
The only problem I can see is that it uses nearly 100% of my CPU after it has finished displaying the tree.
I've updated the file with smartbei's suggestion to prevent this.

---

### Post by hums07 on 2008-04-08
Using Matlab version 6.5.1, so that it would be odd :mrgreen:
The powerful **find** instruction helps much.

The program draws labels on the nodes. Data in the file do not have to be sorted, but then the drawing will not be sorted either.

Still need improvement so that the children are neatly placed under their parent.

Tested data:
> 2,6
1,2
5,7
1,4
6,9
2,5
6,8
1,3

Also tested with tree3.dat from [WW's post above]("http://ubuntuforums.org/showpost.php?p=4672270&postcount=21").

---

### Post by nvteighen on 2008-04-08
Argh! A bit stuck in C... again, but enjoying it a lot. Let's see if I can send something that works...

---

### Post by ynef on 2008-04-08
I know the point is to do this from the ground up, but just in case anyone is reading this thread thinking "wow, something that could do this would be really handy, but I can't program it myself" -- check out "dot" (part of graphviz). It reads a text file and can spit out advanced graphs. Very easy to use too.

As for the contest, it sounds like fun. Nice entries this far, too.

---

### Post by WW on 2008-04-08
I uploaded a new version of treeplot.py in my first post.  The result of plotting the graph tree9.dat (attached as tree9.txt) and similar graphs triggered an itch that I had to scratch.  In some cases, the old version didn't "compress" siblings enough (compare the two attached plots).

---

### Post by WW on 2008-04-08
> **hums07 said:**
> Using Matlab version 6.5.1, so that it would be odd :mrgreen:
The powerful **find** instruction helps much.

The program draws labels on the nodes. Data in the file do not have to be sorted, but then the drawing will not be sorted either.

Still need improvement so that the children are neatly placed under their parent.

Works for me (although I had to remove the spaces from my "tree9.txt" data file).  I like the numbered nodes--it sure helps when debugging!

---

### Post by alexforcefive on 2008-04-08
> **nvteighen said:**
> Argh! A bit stuck in C... again, but enjoying it a lot. Let's see if I can send something that works...

I'm stuck too :( in python though. I can get it to show one branch all the way through, but I can't figure out how to make it go back to the start >.<

---

### Post by hums07 on 2008-04-09
Octave version of my previous Matlab program.
I use Octave-2.9. Plotting using gnuplot-x11 which needs libplotc2c. There are several other plotting packages such as plplot and octplot but I could not get them working with octave. Several instructions and properties of plot objects are not available in Octave.

IMO, to some extent, octave is excellent.

Nodes with the same parent are now sorted even if the source data are not. But I can't still get the idea how to draw neatly, so.... .

Tested data:
> 2,6
1,2
5,9
1,4
6,7
2,5
6,8
1,3

Tested also with WW's Tree9.dat. Octave can handle those additional spaces without me having to change the code.

---

### Post by heikaman on 2008-04-09
updated...

---

### Post by WW on 2008-04-09
> **heikaman said:**
> 
this is my first "Programming Challenge" and my first opengl program, so i hope you all like it.
<snip>
Controls:
1-the tree rotates around the y axis, and you can also use the arrows to rotate the tree in a different direction.
2-press "End" to exit, or close the window.

Compile:
I've included the binary, but if you wish to compile, use the makefile and make sure you have "freeglutdev"
3D!  That should be neat to see, I'll try it when I'm back on my Ubuntu computer.

---

### Post by WW on 2008-04-09
Here's a little python program to generate random trees.  It prints the tree to stdout, so you should redirect the output to a file when you run it. E.g.:
> 
$ python random_tree.py  >  randtree.dat


---

### Post by alexforcefive on 2008-04-09
> **heikaman said:**
> Controls:
1-the tree rotates around the y axis, and you can also use the arrows to rotate the tree in a different direction.
2-press "End" to exit, or close the window.

Oooooooooh you showoff! That's awesome!

I finished mine too. Here's a screenshot, I think you'll all agree it's prettier than heikaman's:

```
alex@fredin:~/Documents/PythonStuff/treedisplay$ python displaytree.py
_ 1
   |_ 2
     |_ 5
       |_ 9
     |_ 6
       |_ 7
       |_ 8
   |_ 3
   |_ 4

```

It just takes input from an input.txt file in the same directory. Command-line only because a) I'm lazy and b) I'm still learning :D

---

### Post by heikaman on 2008-04-09
> **WW said:**
> Here's a little python program to generate random trees.  It prints the tree to stdout, so you should redirect the output to a file when you run it. E.g.:

cool thanks :p

---

### Post by heikaman on 2008-04-09
> **alexforcefive said:**
> Oooooooooh you showoff! That's awesome!

I finished mine too. Here's a screenshot, I think you'll all agree it's prettier than heikaman's:


:lolflag:

keep up the good work =D>

---

### Post by nvteighen on 2008-04-10
> **alexforcefive said:**
> I'm stuck too :( in python though. I can get it to show one branch all the way through, but I can't figure out how to make it go back to the start >.<

Well, I'm on the opposite problem: I just can't stop returning to the start so it just displays only root's children! I have devised every solution I can think of and I get anything but a tree. (including pretty often segfaults after infinite loops...)

---

### Post by alexforcefive on 2008-04-10
Now I feel a little guilty about my sloppy code, but I'll try to explain what I did :D Is this against the rules? I don't think either of us will win anyway :p

Basically for each entry (in the text file), I check to see if it matches my search term. If it does, I print the other part of the entry and then call the search function again with the number I just printed as the search term. Oh, and if an entry gets used, I delete it from the array so it doesn't keep looping infinitely.

There's more to it than that, but that's the basic principle of my script

---

### Post by nvteighen on 2008-04-10
> **alexforcefive said:**
> Now I feel a little guilty about my sloppy code, but I'll try to explain what I did :D Is this against the rules? I don't think either of us will win anyway :p

Basically for each entry (in the text file), I check to see if it matches my search term. If it does, I print the other part of the entry and then call the search function again with the number I just printed as the search term. Oh, and if an entry gets used, I delete it from the array so it doesn't keep looping infinitely.

There's more to it than that, but that's the basic principle of my script

OK... The same I was doing, but I wasn't deleting the used numbers. Let's see...

Thanks. And yes probably this is against the rules...

---

### Post by smartbei on 2008-04-10
@heikaman:
Very impressive, but you have a bit of an issue hidden in there - Apparently (this is just from running the program, and not from viewing the source code) you use random to generate part of the coordinates for placement, which is actually rather cool (you get a different cool-looking tree every time). However, some times the nodes fall too close and overlap... I think ti would be good if that was fixed :).

While your thinking about that, what happens if there are many nodes (i.e. 1000 nodes in the same level)?

BTW - the above question is legitimate for all the submitted entries.

Oh and thanks WW for the random tree python script.

**Challenge due date change**
There is a problem - I will not be able to check the submitted programs on Sunday. Therefore, the challenge due date will be pushed to Thursday 18:00 GMT +2. I hope this will allow more people to participate.

---

### Post by heikaman on 2008-04-10
> **smartbei said:**
> @heikaman:
Very impressive, but you have a bit of an issue hidden in there - Apparently
....


yeah i noticed that. and it's inevitable because i do use random coordinates for the x,y,z but within certain ranges to make sure that the tree goes in one direction instead of going all over the place. :)

> **smartbei said:**
> 
While your thinking about that, what happens if there are many nodes (i.e. 1000 nodes in the same level)?

:confused:
I will try to improve it :)

Thanks for the review.

---

### Post by alexforcefive on 2008-04-10
> **smartbei said:**
> While your thinking about that, what happens if there are many nodes (i.e. 1000 nodes in the same level)?

BTW - the above question is legitimate for all the submitted entries.

Mine works! :D You have to send the output to a text file though, otherwise it gets cut off and word-wrapped

Are there any practical uses for this program? Or was it just a fun challenge?

---

### Post by heikaman on 2008-04-11
> **alexforcefive said:**
> 
Are there any practical uses for this program? Or was it just a fun challenge?

I think it's only for fun, but maybe someone can make use of the code in a project or something.

---

### Post by heikaman on 2008-04-11
I made some modifications to the code, i hope this resolves most of the issues:

1- The node coordinates are still random, but generated in a spherical coordinates not on a circumference of a circle,
which makes the tree looks better. i think :)

2- If a child node has children of its own, the distance from its parent is increased, if not it's kept close to its parent, this and the above, makes the nodes not collide as much. 

3- child nodes take their parent color, so it's more clear.

---

### Post by WW on 2008-04-11
I made another update to treeplot.py back in my first post (as they say, "Release early, release often").  The new version has command line options that let you choose the color, linewidth, size and style of the graph.  The new 'circuit' style option draws the connections using vertical and horizontal lines.  This looks better when the number of children of a node is large or in cases where some of the children are widely separated.  The attached plots show the results of the commands
> 
$ ./treeplot.py -m 10  -l 1 -c '(200,100,80)' -s circuit tree10.txt
$ ./treeplot.py -m 10  -l 1 -c '(200,100,80)' tree10.txt 

Both use linewidth 1, color (200,100,80), and "magnification" (i.e. size) 10.  The first uses the 'circuit' style, and the second uses the default 'straight' style.

---

### Post by nvteighen on 2008-04-11
Ok... I don't know why my C implementation isn't working. I suspect it is related to the way I'm reading data from file... I've tried everything, including pointer redirections, but no way.

Here's the code. Maybe someone can explain me what's wrong? (Well, I feel a bit ashamed, but surely I'm going to learn something).

[PHP]
#include <stdio.h>
#include <stdlib.h>

void Search(int *x, int *y, int i, int n, int MaxLimit)
{		
	int j;
	for(j = 0; j < n; j++)
	{
		if((x[j] == x[i]) && (x[j] != MaxLimit))
		{
			printf("\t%d", y[j]);
			Search(y, x, j, n, MaxLimit);
			y[j] = MaxLimit;
		}
	}
}

void DeleteDupl(int *x, int i, int n, int MaxLimit)
{
	int j;
	for(j = 0; j < n; j++)	
		x[j] = ((x[j] == x[i]) && (i != j)) ? MaxLimit : x[j];
}

int CheckGreatest(int *nodes, int n)
{	
	int GreatestNodeIndex = nodes[0];
	
	int i;
	for(i = 1; i < n; i++)
		GreatestNodeIndex = (nodes[i] > nodes[GreatestNodeIndex]) ? nodes[i] : GreatestNodeIndex;

	return GreatestNodeIndex;			
}

int CheckRoot(int *nodes, int n)
{	
	int SmallestNodeIndex = 0;
	int i;
	for(i = 1; i < n; i++)
		SmallestNodeIndex = (nodes[i] < nodes[SmallestNodeIndex]) ? i : SmallestNodeIndex;

	return SmallestNodeIndex;			
}

void CheckMalloc(int *toCheck)
{
	if(toCheck == NULL)
	{
		printf("tree: Memory allocation error");
		exit(1);
	}
}

void ReadFile(char *FileName, int *n, int **x, int **y)
{	
	FILE *data = fopen(FileName, "r");
	if(data == NULL)
	{
		perror("tree");	
		exit(1);
	}	

	int c = 0;	
	while(fscanf(data, "%d,", &c) != EOF)
		(*n)++;
	*n /= 2;
	rewind(data);

	*x = malloc(*n * sizeof(int));
	CheckMalloc(*x);
	*y = malloc(*n * sizeof(int));
	CheckMalloc(*y);

	int i;
	for(i = 0; i < *n; i++)
		fscanf(data, "%d,%d", &(*x)[i], &(*y)[i]);

	fclose(data);
}

int main(int argc, char **argv)
{
	if(argc != 2)
	{
		perror("Usage: tree FILENAME");
		exit(2);
	}	

	int n = 0;
	int *x = NULL, *y = NULL;
	ReadFile(argv[1], &n, &x, &y);

	int MaxLimit = CheckGreatest(x, n) + 1;
	
	int i;
	for(i = 0; i < n; i++)
		DeleteDupl(x, i, n, MaxLimit);
	
	int RootNode = CheckRoot(x, n);
	for(i = RootNode; i < n; i++)
	{		
		if(x[i] != MaxLimit)
		{		
			printf("%d\n", x[i]);
			Search(x, y, i, n, MaxLimit);
			x[i] = MaxLimit;
		}
	}
	
	puts(" ");
	
	free(x);
	free(y);
	return 0;
}
[/PHP]

---

### Post by smartbei on 2008-04-12
Your problem is in the Search function. You are missing, at the least, a check that j != i, since what is happening is the you are recrusing whenever you get to a line where the line's x is equal to the current x, and this obviously happens in many spots (especially the line you are currently on), meaning you will forever be recursing.

I think representing the nodes as a tree would make your job easier.

BTW - you have some mistakes in your parsing. The least and greatest values could be in the y...What happens if you get a file like this:
```

2,1
3,2
3,4

```
Where 1 should be the root.

---

### Post by nvteighen on 2008-04-12
This is really funny. Look what I've done: A precious elliptic curve!!

---

### Post by Lster on 2008-04-12
:p

---

### Post by nvteighen on 2008-04-12
> **Lster said:**
> :p

:oops: (If this was an Elliptic Curve Challenge I'd probably had won...)

OK. Infinite loop fixed (@smartbei: the j != i was the solution), but find no way to output a tree... The program is checking children only one level down, so I get:

```

|_1
  |_2
  |_4
  |_5
  |_6
  |_11
  |_12
  |_13
  |_14
  |_21
  |_22
  |_32
  |_41
  |_42
  |_43
  |_44
  |_51
  |_52
  |_3
|_2
|_3
|_6
|_5
  |_90
  |_91
  |_7
  |_10
|_10
  |_20
|_20
  |_31
|_32
  |_40
|_7
  |_50
|_52
|_60
|_70

```

This is the updated C code. The parsing error smartbei has shown me has not being fixed, but I suppose priority is to make this work:
[PHP]
#include <stdio.h>
#include <stdlib.h>

void WriteTabs(int l)
{
	int i;
	for(i = 0; i <= l; i++)
		printf(" ");
}

void Search(int *x, int *y, int i, int n, int *IndLevel, int MaxLimit)
{
	int j;
	for(j = 0; j < n; j++)
	{
		if((x[j] == x[i]) && (j != i) && (y[j] != MaxLimit))
		{				
			(*IndLevel)++;			
			WriteTabs(*IndLevel);
			printf("|_%d\n", y[j]);
			Search(y, x, j, n, &(*IndLevel), MaxLimit);
			y[j] = MaxLimit;
			*IndLevel = 0;
		}
	}
}

void DeleteDupl(int *x, int i, int n, int MaxLimit)
{
	int j;
	for(j = 0; j < n; j++)
		x[j] = ((x[j] == x[i]) && (i != j)) ? MaxLimit : x[j];
}

int CheckGreatest(int *nodes, int n)
{
	int GreatestNodeIndex = nodes[0];

	int i;
	for(i = 1; i < n; i++)
		GreatestNodeIndex = (nodes[i] > nodes[GreatestNodeIndex]) ? nodes[i] : GreatestNodeIndex;

	return GreatestNodeIndex;
}

int CheckRoot(int *nodes, int n)
{
	int SmallestNodeIndex = 0;
	int i;
	for(i = 1; i < n; i++)
		SmallestNodeIndex = (nodes[i] < nodes[SmallestNodeIndex]) ? i : SmallestNodeIndex;

	return SmallestNodeIndex;
}

void CheckMalloc(int *toCheck)
{
	if(toCheck == NULL)
	{
		printf("tree: Memory allocation error");
		exit(1);
	}
}

void ReadFile(char *FileName, int *n, int **x, int **y)
{
	FILE *data = fopen(FileName, "r");
	if(data == NULL)
	{
		perror("tree");
		exit(1);
	}

	int c = 0;
	while(fscanf(data, "%d,", &c) != EOF)
		(*n)++;
	*n /= 2;
	rewind(data);

	*x = malloc(*n * sizeof(int));
	CheckMalloc(*x);
	*y = malloc(*n * sizeof(int));
	CheckMalloc(*y);

	int i;
	for(i = 0; i < *n; i++)
		fscanf(data, "%d,%d", &(*x)[i], &(*y)[i]);

	fclose(data);
}

int main(int argc, char **argv)
{
	if(argc != 2)
	{
		perror("Usage: tree FILENAME");
		exit(2);
	}

	int n = 0;
	int *x = NULL, *y = NULL;
	ReadFile(argv[1], &n, &x, &y);

	int MaxLimit = CheckGreatest(x, n) + 1;

	int i;
	for(i = 0; i < n; i++)
		DeleteDupl(x, i, n, MaxLimit);

	int RootNode = CheckRoot(x, n);
	int IndLevel = 0;
	for(i = RootNode; i < n; i++)
	{	
		if(x[i] != MaxLimit)
			printf("|_%d\n", x[i]);
		Search(x, y, i, n, &IndLevel, MaxLimit);
		x[i] = MaxLimit;
	}

	puts(" ");

	free(x);
	free(y);
	return 0;
}
[/PHP]

---

### Post by WW on 2008-04-12
I made yet another update to treeplot.py in my first post.  This version tries to adjust the children of a node between the left- and right-most siblings so they are evenly spaced, where possible.  It also alternates the plot style between straight lines and the 'circuit' style when the 's' key is pressed.

Yet another example is attached.  The command to create the graph is
[php]
./treeplot.py -m 16 -l 1 -c '(150,100,0)'  tree11.txt 
[/php]
(Hit the 's' key to switch to the circuit style.)

EDIT: Just a few minutes later, and I found a bug. I made yet another update to treeplot.py.

---

### Post by WW on 2008-04-12
> **heikaman said:**
> I made some modifications to the code [...]

I finally had a chance to run gltree.  Pretty cool 3D trees!  Maybe you have the start of a 3D molecule viewer.

---

### Post by hums07 on 2008-04-14
I managed to make a better display of the tree. Still using Octave.

Octave has an instruction to draw tree: treeplot. It is able to draw a separate tree from the same data file, its drawing is sexy :lol: Take a look at the attachments.

---

### Post by heikaman on 2008-04-14
> **WW said:**
> I finally had a chance to run gltree.  Pretty cool 3D trees!  Maybe you have the start of a 3D molecule viewer.

Thanks, I'm really glad you liked it, and I wanted to thank you again for the Very useful python script ):P 

Edit: some more modifications:

1-better static tree algorithm.

2-more command line options:
[INDENT]-s static tree
-n disable drawing nodes
-r disable drawing node numbers
-z set scale[/INDENT]

---

### Post by Wybiral on 2008-04-15
Who's the winner?

EDIT:

OK, I just read the OP. For anyone else who's interested, the winner will be announced on the 17th.

---

### Post by LaRoza on 2008-04-15
> **smartbei said:**
> 
**Challenge due date change**
There is a problem - I will not be able to check the submitted programs on Sunday. Therefore, the challenge due date will be pushed to Thursday 18:00 GMT +2. I hope this will allow more people to participate.

> **Wybiral said:**
> Who's the winner?


See above

---

### Post by smartbei on 2008-04-17
Good job to all challenge participants.

Congratulations to **heikaman** - he is the winner of this challenge.

Honorable mentions include WW and hums.

I was hoping we would get some more general-graph displayers (programs that would work for any graph, and not just trees), but that is indeed more challenging.

I am looking forward to the new challenge!

---

### Post by Wybiral on 2008-04-17
Congrats, heikaman!

---

### Post by WW on 2008-04-17
Nice job, h.

And thank you,  smartbei, for "hosting" this week's challenge.

---

### Post by heikaman on 2008-04-17
WOoow thanks everyone. :mrgreen:

:guitar:

I just have a couple of questions, I'm new to this, how do I submit the new challenge and how much time do I have :confused:

---

### Post by smartbei on 2008-04-17
There is no set time - just try to make it in the next day or two or three (soon). As for how to submit - just create a new thread, make it formatted nicely and present the problem as well-defined as you can (I could have improved quite a bit on this issue). Lster will add it to the index of programming challenges when he notices it.

---

### Post by heikaman on 2008-04-17
Ok, thanks smartbei.

---

### Post by Lux Perpetua on 2008-04-17
> **smartbei said:**
> Good job to all challenge participants.

Congratulations to **heikaman** - he is the winner of this challenge.

Honorable mentions include WW and hums.

I was hoping we would get some more general-graph displayers (programs that would work for any graph, and not just trees), but that is indeed more challenging.

I am looking forward to the new challenge!Congratulations, heikaman!

I'm actually still working on a general graph visualization program. I tried, but I couldn't finish it by today. I'll keep working on it, since I find it interesting, and if I finish in a reasonable amount of time, I'll post it here as a noncompetitive entry.

---

### Post by Lux Perpetua on 2008-04-20
I doubt anybody cares at this point, but I said I would post it, so here it is (attached). 

It displays a directed graph (tree or otherwise) "from the inside." I don't want to explain what this means; I think the best way to see is by running it. 

To compile: run 'make' after unpacking the directory. You'll need libgtkmm-2.4-dev and libcairomm-1.0-dev.

To run the examples: ```
graphdisp < graph02.dat
graphdisp < tree10.dat
```

You can select a node by clicking on it. *All* images of the selected node will be highlighted in shades of orange/brown; the other nodes will appear in shades of violet. You can select any node you can see, not just the immediate children of the current node. 

Pressing 'Enter' will move to your selected node, making the window show that node at the top level. 

Watch the terminal to keep track of what node you have selected or entered. 

Pressing 'Esc' will terminate the program.

---

### Post by smartbei on 2008-04-20
Very nice! A very unique way to do it. Too bad it's a little late :p.

---

