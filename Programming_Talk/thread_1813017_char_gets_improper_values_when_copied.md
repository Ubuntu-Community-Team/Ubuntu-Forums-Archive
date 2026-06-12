---
title: "char** gets improper values when copied"
date: 2011-07-27
forum: Programming Talk
---

### Post by skytreader on 2011-07-27
I need to implement tic tac toe minimax in C. In brief, the way I understand minimax is, look-ahead to endgame, see if pursuing this branch is any good; if yes, pursue, else chose another branch. I resorted to recursion in my implementation.

Since, I resorted to recursion, I had to make copies of the board state for the recursive calls to work on. However, in my debugging printfs, I see the board getting corrupted, displaying weird characters.

printf snapshot:
```

original board==================-1x

 x  -  x 
 -  o  x 
 o  x  o 

================================
Copying board...done!
original board==================-1x

 &#65533;  9  &#65533; 
 -  -  - 
 o  x  o 

================================
Copying board...done!
original board==================-1x

 x  -  x 
 -  -  - 
 -  -  o 

================================
Copying board...done!
original board==================0o

 h    &#65533; 
 &#65533;    &#65533; 
 &#65533;    &#65533; 

================================
Copying board...done!

 h    &#65533; 
 &#65533;    &#65533; 
 &#65533;    &#65533; 


```
(Those aren't whitespaces---all should display a 3x3 something. Those that became whitespaces actually display on the terminal as a 2x2 matrix containing '0 0 1 1' enclosed in a box.)

All the relevant code (yep this is minimax in all its exhaustive glory---no pruning yet):
```

//teacher's code
void displayboard(char *board[]) {
   int i,j;
   
   printf("\n");
   for (i=0; i<3; i++) {
      for (j=0; j<3; j++)
	     printf(" %c ",board[i][j]);
	  printf("\n");
   }
   printf("\n");
}

//Everything else is mine

void copyboard(char **original, char **copy){
  printf("Copying board...");
  int i, j;
  for(i = 0; i < 3; i++){
    for(j = 0; j < 3; j++){
      copy[i][j] = original[i][j];
    }
  }
  printf("done!\n");
}

int blankcounter(char **board){
   int i,j;
   int blankcount = 0;
   
   for(i = 0; i < 3; i++){
     for(j = 0; j < 3; j++){
       if(board[i][j] == BLANK){
         blankcount++;
       }
     }
   }
   
   return blankcount;
}

int computer_move(char **board,char piece1,char piece2) {
   char winner1 = checkwin(board, PLAYER1);
   char winner2 = checkwin(board, PLAYER2);
   
   printf("Computing===================\n");
   displayboard(board);
   printf("============================\n");
   
   if(winner1 == PLAYER1){
      return -1;
   }
   
   if(winner2 == PLAYER2){
      return 1;
   } else if (winner1 == ' ' || winner2 == ' '){
      return 0;
   }
   
   int blankcount = blankcounter(board);
   char*** children = (char***) malloc(sizeof(char**) * 3);
   int childrenIndex = 0;
   int i, j;
   
   for(i = 0; i < 3; i++){
      for(j = 0; j < 3; j++){
         if(board[i][j] == BLANK){
            char** boardcopy = (char**) malloc(sizeof(char*)*3);
            int x;
            for(x = 0; x < 3; x++){
               boardcopy[x] = (char*) malloc(sizeof(char)*3);
            }
            copyboard(board, boardcopy);
            boardcopy[i][j] = piece1;
            children[childrenIndex] = boardcopy;
            childrenIndex++;
         }
      }
   }
   
   int theindex = -1;
   int max = -1;
   int min = 1;
   
   for(i = 0; i < blankcount; i++){
      char** clonechild = (char**) malloc(sizeof(char*) * 3);
      int j;
      for(j = 0; j < 3; j++){
         clonechild[j] = (char*) malloc(sizeof(char) * 3);
      }
      copyboard(children[i], clonechild);
      int nextmove = computer_move(clonechild, piece2, piece1);
      
      if(piece1 == PLAYER1 && nextmove < min){
         min = nextmove;
         theindex = i;
      } else if(piece1 == PLAYER2 && nextmove > max){
         max = nextmove;
         theindex = i;
      }
   }
   
   if(theindex != -1){
      printf("original board==================%d%c\n", max, piece1);
      displayboard(children[theindex]);
      printf("================================\n");
      copyboard(children[theindex], board);
   }
   return max;
}

```

I've thought of other ways implementing minimax but the template/function sig of computer_move was specified (by my teacher, yes). The best guess I can give as to where I went wrong is in how I malloc to my copied char**'s---I don't really use the ** declaration. Had it been up to me I'd represent the board as char[3][3]. But even with a guess, I still can't get what's wrong.

Any help will be appreciated. Thanks!

---

### Post by GeneralZod on 2011-07-27
At a guess: what kind of values does childrenIndex take? You've only allocated 3 slots in children.

Also, the finicky board allocation logic is duplicated: I'd probably do something like e.g.:

```

char** cloneboard(char** original)

```

rather than 

```

void copyboard(char **original, char **copy)

```

and have the cloneboard allocate the memory for the new board, copy the contents, and return it.

Edit:

A completely self-contained example that we can compile and execute would be very helpful.

---

### Post by skytreader on 2011-07-27
Thanks GeneralZod. Apparently, I copy-pasted some mallocs a few times too many when I declared the children array. It should've been of size blankcount. Case closed. Thanks! :D

---

