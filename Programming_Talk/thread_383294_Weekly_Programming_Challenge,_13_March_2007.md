---
title: "Weekly Programming Challenge, 13 March 2007"
date: 2007-03-13
forum: Programming Talk
---

### Post by po0f on 2007-03-13
This week's missions, should you choose to accept, will be to code a sudoku solver ([Wikipedia entry](http://en.wikipedia.org/wiki/Sudoku)).  As with last week's challenge, you will be able to use libraries to develop a solution.  A solution will be considered complete if, given a puzzle, the program correctly solves it.  How the puzzle will be input to the program will be left as an exercise to the reader.  (Wait a minute..  :))

Bonus points:
[list]
[*]Create a GUI for it
[*]Create/use graphics
[/list]

---

### Post by Jmccaffrey on 2007-03-21
Probably too late but heres one way to do it, in C.
```

#include <stdio.h>
#include <fcntl.h>

short board[9][9];

int 
is_sure(short n)
{
  size_t ones = 0, i;
  
  for (i = 0; i < 9 && ones < 2; ++i)
    ones += (n & 1 << i ? 1 : 0);

  return (ones == 1);
}

int
solve(void)
{
  size_t i, j, x, y;

  // Horizontal pass
  for(i = 0; i < 9; ++i) {
    short mask = 0;
    
    //Collect all solved terms
    for(j = 0; j < 9; ++j) {
      if (is_sure(board[i][j])) {
	mask |= board[i][j];
	board[i][j] |= 0x200; // flag for sure status
      }else
	board[i][j] &= 0x1FF;
    }

    mask ^= 0x1FF;
    //Eliminate those terms from the possibilities mask
    for(j = 0; j < 9; ++j) {
      if ((board[i][j] & 0x200) == 0)
	board[i][j] &= mask;
    }
  }

  //Vertical pass
  for(j = 0; j < 9; ++j) {
    short mask = 0;
    
    //Collect all solved terms
    for(i = 0; i < 9; ++i) {
      if (is_sure(board[i][j])) {
	mask |= board[i][j];
	board[i][j] |= 0x200; // flag for sure status
      }else
	board[i][j] &= 0x1FF;
    }

    mask ^= 0x1FF;
    //Eliminate those terms from the possibilities mask
    for(i = 0; i < 9; ++i) {
      if ((board[i][j] & 0x200) == 0)
	board[i][j] &= mask;
    }
  }

  //Area pass
  for(x = 0; x < 3; ++x) {
    for(y = 0; y < 3; ++y) {
      short mask = 0;

      //Collect all solved terms
      for(i = 0; i < 3; ++i) {
	for (j = 0; j < 3; ++j) {
	  short val = board[i + 3 * x][j + 3 * y];
	  if (is_sure(board[i + 3 * x][j + 3 * y])) {
	    mask |= board[i + 3 * x][j + 3 * y];
	    board[i + 3 * x][j + 3 * y] |= 0x200; // flag for sure status
	  }else
	    board[i + 3 * x][j + 3 * y] &= 0x1FF;
	}
      }

      mask ^= 0x1FF;
      //Removed solved terms from possibilities
      for(i = 0; i < 3; ++i) {
	for (j = 0; j < 3; ++j) {
	  if ((board[i + 3 * x][j + 3 * y] & 0x200) == 0)
	    board[i + 3 * x][j + 3 * y] &= mask;
	}
      }
    }
  }

  // Check for solved
  for(i = 0; i < 9; ++i) {
    for(j = 0; j < 9; ++j) {
      if (!is_sure(board[i][j]))
	return 0;
    }
  }

  return 1;
}

void 
display_board(void)
{
  size_t i, j;
  for(i = 0; i < 19; ++i)
    printf("#");
  printf("\n");

  for(i = 0; i < 9; ++i) {
    int is_bold = (i + 1) % 3 == 0;
    
    printf("#");
    for (j = 0; j < 9; ++j) {
      short val = board[i][j];
      if (is_sure(val)) {
	char ch;
	for (ch = '1'; (val & 1) == 0; val >>= 1)
	  ch++;

	printf("%c", ch);
      } else
	printf(" ");

      if ((j + 1) % 3)
	printf("|");
      else
	printf("#");
    }
    printf("\n");

    if (is_bold) {
      for (j = 0; j < 19; ++j)
	printf("#");
      printf("\n");
    }else {
      for(j = 0; j < 9; ++j) {
	if (j % 3)
	  printf("+-");
	else
	  printf("#-");
      }

      printf("#\n");
    }
  }  
}

int
main(int argc, char *argv[])
{
  size_t i, j;
  char buffer[90], *p;
  int fd = open("puzzle.puz", O_RDONLY);

  if (fd < 0) {
    fprintf(stderr, "Unable to open puzzle file\n");
    return 1;
  }
  
  p = buffer;
  read(fd, buffer, 90);
  for(i = 0; i < 9; ++i) {
    for(j = 0; j < 9; ++j) {
      short packed = 0x1FF;
      if (*p >= '0' && *p <= '9')
	packed = 1 << (*p - '1');

      board[i][j] = packed;
      ++p;
    }

    ++p;
  }

  close(fd);
  display_board();
  
  printf("Processing puzzle...");
  while (!solve())
    printf(".");

  printf("SOLVED!\n");
  display_board();

  return 0;
}

```

It takes a file called "puzzle.puz" like this:
```

53--7----
6--195---
-98----6-
8---6---3
4--8-3--1
7---2---6
-6----28-
---419--5
----8--79

```

It runs like this:
```

jmccaffrey@windy:~/mywork/sudoku-solve$ ./sudoku-solve 
###################
#5|3| # |7| # | | #
#-+-+-#-+-+-#-+-+-#
#6| | #1|9|5# | | #
#-+-+-#-+-+-#-+-+-#
# |9|8# | | # |6| #
###################
#8| | # |6| # | |3#
#-+-+-#-+-+-#-+-+-#
#4| | #8| |3# | |1#
#-+-+-#-+-+-#-+-+-#
#7| | # |2| # | |6#
###################
# |6| # | | #2|8| #
#-+-+-#-+-+-#-+-+-#
# | | #4|1|9# | |5#
#-+-+-#-+-+-#-+-+-#
# | | # |8| # |7|9#
###################
Processing puzzle.........SOLVED!
###################
#5|3|4#6|7|8#9|1|2#
#-+-+-#-+-+-#-+-+-#
#6|7|2#1|9|5#3|4|8#
#-+-+-#-+-+-#-+-+-#
#1|9|8#3|4|2#5|6|7#
###################
#8|5|9#7|6|1#4|2|3#
#-+-+-#-+-+-#-+-+-#
#4|2|6#8|5|3#7|9|1#
#-+-+-#-+-+-#-+-+-#
#7|1|3#9|2|4#8|5|6#
###################
#9|6|1#5|3|7#2|8|4#
#-+-+-#-+-+-#-+-+-#
#2|8|7#4|1|9#6|3|5#
#-+-+-#-+-+-#-+-+-#
#3|4|5#2|8|6#1|7|9#
###################

```

My algorithm is pretty brute force, but fast enough for this purpose.  Read the file into a 9x9 array of bitmasks.  Each mask represents all the possible numbers for that square in the following format:
```

001000101
  ^   ^ ^
123456789

```
In this example 3,7,and 9 are the possible numbers for that square. For each pass I make through the board, I take all the "solved" squares, OR them together, and then mask those values off of the rest to remove the possibilities from the unsolved squares.  Once every square is solved, I can assume the puzzle is finished.

---

### Post by Wybiral on 2007-03-21
Thats a really nice solution, it even draws the board nicely!

I don't think these challenges are meant to have deadlines, they are just challenges... You know... To challenge you!

---

