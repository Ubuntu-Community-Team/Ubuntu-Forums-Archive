---
title: "c++ creating a dynamic 2d array"
date: 2009-04-21
forum: Programming Talk
---

### Post by psycho5 on 2009-04-21
Hi guys..

suppose I have a character array that's suppose to represent a chess board except the size is user defined.

```

int main (int argc, char* argv[]){

int i,j;
char board[i][j];
int XMAX, YMAX; //suppose these values are taken from user 


for (i=0; i<XMAX; i++){
for (j=0; j<YMAX; j++){

board[i][j]= ( 'O','O' ); //fill up with O's
}};

.
.
.

```

I get 2 errors at the line where I initialize the array :

board[i][j]
expected constant expression
cannot allocate an array of constant size 0

What does that mean? How can I make the array depend on the values of i j? 

Also, in the same program I have :

```

switch (board[i][j]=='*'){

//if there is a * at a certain i row and j column, and the following lines are also true then change the * to X

case "board[i][j+1]=='*'" : 
case "board[i][j-1]=='*'" : 
case "board[i+1][j]=='*'" :
case "board[i-1][j]=='*'" :
case "board[i-1][j+1]=='*'" :
case "board[i-1][j-1]=='*'" :
case "board[i+1][j+1]=='*'" :
case "board[i+1][j-1]=='*'" :
board[i][j]='X';
break;
}
```

I get this error:
 
case expression not constant

What does that mean? what can I do to make this work?

---

### Post by Jiraiya_sama on 2009-04-21
You have to allocate memory for the array.

ex:
```

char** board = new char*[i];
for(int iter = 0; iter != i; ++iter)
  board[iter] = new char[j];

```

When you are done with it, you must delete it or you'll leak memory.

```

for(int iter = 0; iter != i; ++iter)
  delete [] board[iter];
delete [] board;

```

There might be a cleaner way to do it though.

---

### Post by psycho5 on 2009-04-21
Jiraya-sama

can you please explain the code you wrote? In slow simple terms cause I'm still a genin..


-naruto



thanks

---

### Post by Jiraiya_sama on 2009-04-21
You have to know the size of a normal array when you compile the program in C++. That means in order to initialize an array of elements you need a constant value.

example:
```

const int i = 10;
int j = 10;

int array[10]; //Works, 10 is a literal constant
int array[i];   //Works, i is a constant int.
int array[j];   //Does not work. j's value may change after compilation.

```

If you want to create an array of varying size (for example, letting the user decide how big it is) you need to dynamically allocate memory for it.

```

int i = 10;
int* j; //creates an int pointer named j. Will point to the beginning of our array.
j = new int[i]; //creates a new int array in memory of size 10 and assigns the address of the first value to j.

delete [] j; //deletes the array j is pointing to so our program doesn't leak memory.

```

As for the code I gave you, "char**" means a char pointer pointer, or a pointer that points to char pointers. Then I assigned an array of char pointers (new char*[i]) to the char** board. Finally I went inside the array, and assigned to each char* an array of chars.

Does that clear it up a bit?

---

### Post by hessiess on 2009-04-21
Just use std::vector(google it), it is a lot easier than manually allocating(and deleting) an array.

---

### Post by psycho5 on 2009-04-22
Ty for the replies, also can someone please suggest a solution for my switch case problem? It's mentioned on the first post on this thread.

---

### Post by Pollox on 2009-04-22
Switches are used in the following manner:
switch( var )
case "a": if var == a, do stuff
case "b": if var == b , do other stuff
etc.

It looks like from your comments that you only want to execute board[i][j]='X'; if all the "cases" are satisfied? In which case just use one if statement (if( (thing1 == *) && (thing 2 == *) && etc. ) ) ).

---

### Post by psycho5 on 2009-04-22
Pollox, you are correct, if all conditions are satisfied. The thing is, if else statements will be quite long and tedious since there are alot of cases that need to be checked. I'm not sure if "ifelse" statements will make it less time consuming for the program or not..

I have round 470 lines of switch case: conditions and I prefer a quick fix rather than replacing them with if else statements.

---

### Post by tneva82 on 2009-04-22
> **psycho5 said:**
> I have round 470 lines of switch case: conditions and I prefer a quick fix rather than replacing them with if else statements.

Sorry but I don't think switch is going to work.

However you could just try:

```

if(index1==true) {
   if(index2==true) {
      if(index3==true) {(and so on for all indexes)
         do your stuff
      }
   }
}

```

Atleast that way there's no else's there. If even one if clause is false it will skip the rest and not do anything. Just one if claus per case.

Right now it would do it if even one case happens. And that without concidering that your case statements are totally wrong...

You could however cut down if clauses by using for loop like:

```

int targetX=xindex, targetY=yindex; //xindex and yindex are indexes for the spot you would like to change
bool switch=true;

for(int y=targetY-1;y<=targetY+1;y++) {
   for(int x=targetX-1;x<=targetX+1;x++) {
      if(x>=0 && < width && y>0&&y<height) {  // remember to check the array boundaries.
         if(board[x][y]!='*') { // not sure could you compare it like this.
            switch=false;
         }
      }
   }
}

if(switch) {
   board[targetX][targetY]='X';
}

```

Above code assumes you wanted to check every surrounding index and if all are * then switch the target location to X.

---

### Post by Pollox on 2009-04-22
> **psycho5 said:**
> Pollox, you are correct, if all conditions are satisfied. The thing is, if else statements will be quite long and tedious since there are alot of cases that need to be checked. I'm not sure if "ifelse" statements will make it less time consuming for the program or not..

I have round 470 lines of switch case: conditions and I prefer a quick fix rather than replacing them with if else statements.

You only want to execute the thing at the end if ever single condition is satisfied, and not execute if any one isn't.  So, it wouldn't be a bunch of if else statements, it would just be one if statement (with a bunch of &&).  Your syntax is off on the switch ([http://www.cplusplus.com/forum/beginner/5152/](http://www.cplusplus.com/forum/beginner/5152/) has a nice example), which is why you're getting an error.  A switch just takes one variable, and then compares it to a bunch of other variables.  Maybe you could figure out some way to make a switch work for this, but it seems like a bad solution for what you are trying to do.

---

### Post by Jiraiya_sama on 2009-04-22
> **hessiess said:**
> Just use std::vector(google it), it is a lot easier than manually allocating(and deleting) an array.

For this case a vector would be perfect, but if he ever wants to create containers of his own or numerous other things he has to get used to allocating and freeing arrays manually.

---

### Post by psycho5 on 2009-04-22
Okay I made one mistake, I found out that I don't have to check each and every neighbor around [i][j] , I just need to count if a certain number of neighbors are also *, then change the current * to X. 

If I have 

* * *
* * *
* * *

and the center * is [i][j] , if there are 4 or more * surrounding it, it turns into X. Doesn't have to be all possible combinations. 

Previously I was trying to check if there are eight * around [i][j], then check for 7,6,5,and finally 4. for each case turn the current * into a X.

---

### Post by tneva82 on 2009-04-22
> **psycho5 said:**
> Okay I made one mistake, I found out that I don't have to check each and every neighbor around [i][j] , I just need to count if a certain number of neighbors are also *, then change the current * to X. 

If I have 

* * *
* * *
* * *

and the center * is [i][j] , if there are 4 or more * surrounding it, it turns into X. Doesn't have to be all possible combinations. 

Previously I was trying to check if there are eight * around [i][j], then check for 7,6,5,and finally 4. for each case turn the current * into a X.

Well my for loop should be able to do it without too much of change. Instead of bool switch=true; have it int count=0; and then inside nested for loop if(array[x][y]=='*') count++. Finally if(count>=4) then do the change.

That's how I would do it though maybe there's even better way to do it.

Edit: You need also add specific check that x and y aren't i and j(or rather  how to deal if it is). Right now it would count that as one of neighbours.

---

### Post by psycho5 on 2009-04-22
> **tneva82 said:**
> Sorry but I don't think switch is going to work.

However you could just try:

```

if(index1==true) {
   if(index2==true) {
      if(index3==true) {(and so on for all indexes)
         do your stuff
      }
   }
}

```

Atleast that way there's no else's there. If even one if clause is false it will skip the rest and not do anything. Just one if claus per case.

Right now it would do it if even one case happens. And that without concidering that your case statements are totally wrong...

You could however cut down if clauses by using for loop like:

```

int targetX=xindex, targetY=yindex; //xindex and yindex are indexes for the spot you would like to change
bool switch=true;

for(int y=targetY-1;y<=targetY+1;y++) {
   for(int x=targetX-1;x<=targetX+1;x++) {
      if(x>=0 && < width && y>0&&y<height) {  // remember to check the array boundaries.
         if(board[x][y]!='*') { // not sure could you compare it like this.
            switch=false;
         }
      }
   }
}

if(switch) {
   board[targetX][targetY]='X';
}

```

Above code assumes you wanted to check every surrounding index and if all are * then switch the target location to X.

Can you please explain the second part of ur code (psudocode?) in a simpler way? By switch do you refer to changing * to X ? What do you mean by bool switch?

---

### Post by tneva82 on 2009-04-22
> **psycho5 said:**
> Can you please explain the second part of ur code (psudocode?) in a simpler way? By switch do you refer to changing * to X ? What do you mean by bool switch?

Yeah the switch I refered to change(sorry. Tried to type it fast since I have own code to work on as well). bool switch was just variable type bool since I assumed change to X was supposed to happen only if all neighbours are *. Since it's count specific...Howabout this:

```


int count=0;
if(array[i][j]=='*') { 
  for(int y=j-1;y<=j+1;y++) {
    for(int x=i-1;x<=i+1;x++) {
      if(x>=0 && x<width && y>=0 && y<height) {
	if(array[x][y]=='*' && (i!=x && j!=y)) { //if array index has specified character and we aren't on the index we would be changing)
	  count++;
	}
      }
    }
  }
}

if(count>=4) {
  array[i][j]='X';
}

```

You need to supply width and height(maximum size of indexes) to prevent array boundary exceeding but otherwise that should do it. Assuming array[x][y]=='*' comparison works(if not time to dig out strncmp).

---

### Post by psycho5 on 2009-04-22
Here's how the code looks now, when compiling, I get two errors on the first line. can't convert from int* to int


```

int targetX=board[i], targetY=board[j]; //xindex and yindex are indexes for the spot I would like to change

int count=0;

for( w=targetY-1; w<=targetY+1; w++) {
   for( q=targetX-1; q<=targetX+1; q++) {
	   if( q >= 0 && q < XEND && w > 0 && w < YEND ) {  // remember to check the array boundaries.
		  if(board[q][w]!='1') {// not sure could I can compare it like this. 
            count++; //keep counting if cell is dead, look for alive cells. can this work?
         }
      }
   }
}

if(count >= 4) //overpopulation dies 
{
   board[targetX][targetY]='0';
}

if (count < 4 && count > 1 ) // 2-3 neighbors, if the cell is  1  cell lives = 1. if cell is dead (0) then it gives birth = 1.
{
board[targetX][targetY]='1';
}

if (count == 0) // if cell is isolated, it dies = 0. 
{
board[targetX][targetY]='0';
}

```

this is a snipplet of the early code in the program 

```

int** board = new int* [i];

//generate the grid
printf("Creating grid\n");
for (i=XMIN; i!=XEND; ++i) 
{
	for (j=YMIN; j!=YEND; ++j)
                {
		board[i]= new int [j];
                }
}

```

the values for YEND and XEND are provided by the user, the int targetX targetY are not pointers is that why I am having those errors?

---

### Post by tneva82 on 2009-04-22
> **psycho5 said:**
> the values for YEND and XEND are provided by the user, the int targetX targetY are not pointers is that why I am having those errors?

Yeah though why would you want to store array of int pointers? Not quite sure on that one. I thought you were looking at char array and the targetX and targetY would contain index for the char array.

---

