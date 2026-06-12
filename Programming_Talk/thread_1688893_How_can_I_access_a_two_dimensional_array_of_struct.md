---
title: "How can I access a two dimensional array of structures?"
date: 2011-02-15
forum: Programming Talk
---

### Post by smdawson on 2011-02-15
I am writing an assignment in C where I have a structure that contains integers and I want to make a two dimensional array of those structures. The matrix needs to be created dynamically based on the input. The matrix will represent a maze and the size of the maze will change based on the dimensions read in from a file.

The last function I wrote was ```
cell **new_grid(data *maze_data)
``` which is in the "cell_struct.c" file. That is where I am trying to dynamically allocate memory for this matrix. In main.c I don't have a problem until I try to access the matrix. After I added the line ```
grid[0][0].south_wall = 1;
``` I am getting these errors.

main.c:46 error: invalid use of undefined type 'struct data_cell'
main.c:46: error: dereferencing pointer to incomplete type

I don't want anyone to write me any code, but I would appreciate it if someone could explain to me what I am doing wrong and how to correct it.


main.c
```
#include <stdio.h>
#include <stdlib.h>
#include "maze.h"



int main(int argc, char *argv[])
{
  // Create new "data" structure.
  data *maze_data;
  maze_data = new_data();
  
  // Read the file and read all integers into the vector.
  read_file(argc, argv, maze_data);

  // Print the dimensions.
  int x;  
  for(x = 0; x < PAIR; x++)
    fprintf(stdout, "%d\n", get_dimensions(maze_data, x));
  
  // Print the start coordinates.
  for(x = 0; x < PAIR; x++)
    fprintf(stdout, "%d\n", get_start(maze_data, x));

  // Print the finish coordinates.
  for(x = 0; x < PAIR; x++)
    fprintf(stdout, "%d\n", get_finish(maze_data, x));

  // Print all binary integers representing walls and total.
  for(x = 0; x < total_binary(get_dimensions(maze_data, 0), get_dimensions(maze_data, 1)) ; x++)
    fprintf(stdout, "%d, ", get_walls(maze_data, x));

  fprintf(stdout, "\n");
  fprintf(stdout, "%d\n", x);

  // Create the matrix.
  cell **grid;
  grid = new_grid(maze_data);

  // Access an item in one of the structures.
  grid[0][0].south_wall = 1;



  return 0;
}
```

maze.h
```
#ifndef maze_h
#define maze_h


#include <stdio.h>
#include <stdlib.h>
#define PAIR 2
#define DATA_ITEMS 4
#define CELL_ITEMS 6


typedef struct data_cell cell;
typedef struct maze_data data;


// Parameters: Nothing.
// Returns: A "data" structure that contains dimensions, start, and finish. All three
// are arrays of the "data" structure that will hold pairs of integers.
data *new_data(void);


// Parameters: The number of arguments, the array of arguments, and three empty arrays with.
// Returns: A pointer to the binary array representing the maze walls.
// The function below checks for the correct number of command line arguments, if incorrect, 
// the program exits and displays an error message. The input file is then opened, 
// and if it cannot be opened the program exits and displays an error message. The file
// is read and the information is copied into the dimensions, finish,
// start, and walls arrays.
void read_file(int argc, char *argv[], data *maze_data);


// Parameters: The "data" structure and the index of walls to be returned.
// Returns: An integer from the "data" item walls.
// The function below returns an integer from the "data" structure item
// walls at the specified index. 
int get_walls(data *maze_data, int index);


// Parameters: The "data" structure and the index of dimensions to be returned.
// Returns: An integer from the "data" item dimensions.
// The function below returns an integer from the "data" structure item
// dimensions at the specified index. 
int get_dimensions(data *maze_data, int index);


// Parameters: The "data" structure and the index of start to be returned.
// Returns: An integer from the "data" item start.
// The function below returns an integer from the "data" structure item
// start at the specified index. 
int get_start(data *maze_data, int index);


// Parameters: The "data" structure and the index of finish to be returned.
// Returns: An integer from the "data" item finish.
// The function below returns an integer from the "data" structure item
// finish at the specified index. 
int get_finish(data *maze_data, int index);


// Parameters: An array containing the dimesions of the maze.
// Returns: The total number of binary integers in the input file.
// The function below calculates the total number of binary integers in
// the input file based on the dimensions of the maze.
int total_binary(int rows, int columns);


// Parameters: A "data" structure.
// Returns: A pointer to a two dimensional cell matrix.
// The function below dynamically creates a two dimensional cell matrix 
// using the dimensions from the "data" structure.
cell **new_grid(data *maze_data);


#endif
```

data_struct.c
```
#include <stdio.h>
#include <stdlib.h>
#include "maze.h"


// The structure below defines maze_data as containing the pointers dimensions,
// start, finish, and walls.
struct maze_data
{
  int *dimensions;
  int *start;
  int *finish;
  int *walls;
};


// The function below creates an instance of the "data" structure and then returns a pointer
// to the new instance.
data *new_data(void)
{
  data *data_box;
  data_box = (data *) malloc(DATA_ITEMS * sizeof(int));
  data_box->dimensions = (int *) malloc(PAIR * sizeof(int)); 
  data_box->start = (int *) malloc(PAIR * sizeof(int));
  data_box->finish = (int *) malloc(PAIR * sizeof(int));

  return data_box;
}


// The function below returns an integer from walls at the specified index.
int get_walls(data *maze_data, int index)
{
  if(index < 0 || index >= total_binary(get_dimensions(maze_data, 0), get_dimensions(maze_data, 1)))
  {
    fprintf(stderr, "Error! Invalid wall index. Exiting.");
    exit(1);
  }
  
  return maze_data->walls[index];  
}


// The function below returns an integer from dimensions at the specified index.
int get_dimensions(data *maze_data, int index)
{
  if(index < 0 || index >= PAIR)
  {
    fprintf(stderr, "Error! Invalid dimension index. Exiting.");
    exit(1);
  }
  
  return maze_data->dimensions[index];  
}


// The function below returns an integer from start at the specified index.
int get_start(data *maze_data, int index)
{
  if(index < 0 || index >= PAIR)
  {
    fprintf(stderr, "Error! Invalid start index. Exiting.");
    exit(1);
  }
  
  return maze_data->start[index]; 
}


// The function below returns an integer from finish at the specified index.
int get_finish(data *maze_data, int index)
{
  if(index < 0 || index >= PAIR)
  {
    fprintf(stderr, "Error! Invalid finish index. Exiting.");
    exit(1);
  }
  
  return maze_data->finish[index];
}


// The function below returns the total number of binary numbers in the input file.
int total_binary(int rows, int columns)
{
  return (((rows * columns) * 2) + (rows + columns));
}


// The function below reads from the input file and returns a binary array.
void read_file(int argc, char *argv[], data *maze_data)
{

  FILE *input_file;

  // Check for correct number of arguments, if not, display error message.
  if(argc != PAIR) 
  {
    fprintf(stderr, "Error! Invalid number of arguments. Exiting.\n");
    exit(1);
  }

  // Check that file opens, if not, display error message.   
  if((input_file = fopen(argv[1], "r")) == NULL)
  {
    fprintf(stderr, "Error! Cannot open input file. Exiting.\n");
    exit(1);
  }

  // Read the dimensions into an array.
  int x = 0;
  while(x < PAIR)
    fscanf(input_file, "%d", &maze_data->dimensions[x++]);

  // Read the start coordinates into an array.
  x = 0;
  while(x < PAIR)
    fscanf(input_file, "%d", &maze_data->start[x++]);

  // Read the finish coordinates into an array.
  x = 0;
  while(x < PAIR)
    fscanf(input_file, "%d", &maze_data->finish[x++]);

  // Create an array and dynamically allocate space (based on the dimensions)
  // for the binary list. Read the binary file into the array.
  maze_data->walls = (int *) malloc(sizeof(int) * total_binary(get_dimensions(maze_data, 0), get_dimensions(maze_data, 1)));

  x = 0;
  while(!feof(input_file))
    fscanf(input_file, "%d", &maze_data->walls[x++]);

  // Close the file.
  fclose(input_file);
}
```

cell_struct.c
```
#include <stdio.h>
#include <stdlib.h>
#include "maze.h"


// The structure below is defined has having 6 items that represent the walls of
// the cell and if the cell has been walked through or backed through.
struct data_cell
{
  int north_wall;
  int east_wall;
  int south_wall;
  int west_wall;
  int walked_through;
  int backed_through;
};


// The function below creates a new grid, or a two dimensional matrix of cells.
// The memory is dynamically allocated based on the dimensions given in the file. 
cell **new_grid(data *maze_data)
{
  
  cell **new_grid = (cell **) malloc(sizeof(cell) * get_dimensions(maze_data, 0));
  
  if(new_grid == NULL)
  {
    fprintf(stderr, "Error! New_grid memory allocation failed.");
    exit(1);
  }

  int x;
  for(x = 0; x < get_dimensions(maze_data, 0); x++)
    new_grid[x] = (cell *) malloc(sizeof(cell) * get_dimensions(maze_data, 1));

  return new_grid;
}
```

---

### Post by Some Penguin on 2011-02-16
You've put the struct data_cell where main.c knows nothing about it.   Header files exist for a reason.

---

### Post by smdawson on 2011-02-16
I did? But I typedef'd both structures in my header file and I included the header file in main.c. I don't see the problem...

---

### Post by smdawson on 2011-02-16
Hm...so it works when I put my two structure definitions into my header file. I am confused about why I need to define them there...

---

### Post by Arndt on 2011-02-16
> **smdawson said:**
> Hm...so it works when I put my two structure definitions into my header file. I am confused about why I need to define them there...

Because in main.c, the compiler sees ".south_wall". How is the compiler supposed to know what that is?

---

### Post by smdawson on 2011-02-16
Ohhh. Ok. I see. Early I couldn't access my other "data" structure in main and I just wrote a get function to bypass having to access the elements. Apparently my problem there was that I needed to define my structure in the header.

I'm glad it was a simple mistake. Thanks for the help!

---

### Post by new2C on 2011-02-22
Hello smdawson,
 
I am really interested in your program, and was wondering if you could explain something to me.
In your "cell_struct.c" file, how are you planning to save the start & finish position ?
 
thanks!

---

### Post by smdawson on 2011-02-23
I finished this project and will go ahead and post the code for you. The input file should be entered at the command line when you execute the program (i.e. "./a.out input"). The maze can be any dimensions, but the input file has to be laid out in a specific order. Maze dimensions first, then start coordinates, then finish coordinates, then the binary representing the walls. Each vertical and horizontal wall is represented with a 1 if it is there and a 0 if it is not there.

To answer your question, I made two arrays (containing two integers each) inside my data struct that are the start and finish coordinates for the maze. Then in the cell_struct.c file I have a function, set_start_and_finish(), that accesses the coordinates specified in the input file and marks those cells as the start and finish points respectively. 

In hindsight I realize my code would be shorter and simpler if I would have represented the cell statuses (empty, walked through, backed through, start, finish, etc.) with different characters in one status variable. As you can see in my code, I essentially used true and false values (1 and 0) to represent if a cell was empty, start, finish, walked through, or backed through. 

cell_struct.c
```
//
// Shawn Dawson
//
// Project 3 COP3411, Feb 18 2011
//
// This file contains all of the functions related to the cell structure.
//


#include <stdio.h>
#include <stdlib.h>
#include "maze.h"


// The function below creates a new grid, or a two dimensional matrix of cells.
// The memory is dynamically allocated based on the dimensions given in the file. 
cell **new_grid(data *maze_data)
{
  // Dynamically allocate an array of cells.
  cell **new_grid = (cell **) malloc(sizeof(cell) * maze_data->dimensions[ROWS]);
  
  // Check if memory allocation fails, if so, print an error message.
  if(new_grid == NULL)
  {
    fprintf(stderr, "Error! New_grid memory allocation failed.");
    exit(1);
  }

  // Dynamically allocate arrays of cells that are each pointed to by one of the 
  // cells in the first dynamically allocated array.
  int x;
  for(x = 0; x < maze_data->dimensions[ROWS]; x++)
    new_grid[x] = (cell *) malloc(sizeof(cell) * maze_data->dimensions[COLUMNS]);

  return new_grid;
}


// The function below uses the binary in the "data" structure item walls to fill
// all of the walls of every cell in the grid matrix.
void fill_grid(cell **grid, data *maze_data)
{
  // Set the north, east, south, and west walls of every cell to it's corresponding binary representation.
  int x, y;
  for(x = 0; x < maze_data->dimensions[ROWS]; x++)
    for(y = 0; y < maze_data->dimensions[COLUMNS]; y++)
    {
      grid[x][y].north_wall = maze_data->walls[y + (x * (maze_data->dimensions[COLUMNS] + maze_data->dimensions[COLUMNS] + 1))];
      grid[x][y].east_wall = maze_data->walls[y + maze_data->dimensions[COLUMNS] + 1 + (x * (maze_data->dimensions[COLUMNS] + maze_data->dimensions[COLUMNS] + 1))];
      grid[x][y].west_wall = maze_data->walls[y + maze_data->dimensions[COLUMNS] + (x * (maze_data->dimensions[COLUMNS] + maze_data->dimensions[COLUMNS] + 1))];
      grid[x][y].south_wall = maze_data->walls[y + maze_data->dimensions[COLUMNS] + maze_data->dimensions[COLUMNS] + 1 + (x * (maze_data->dimensions[COLUMNS] + maze_data->dimensions[COLUMNS] + 1))];

      // Initialize these items for every cell.
      grid[x][y].finish_here = 0;
      grid[x][y].start_here = 0;
      grid[x][y].walked_through = 0;
      grid[x][y].backed_through = 0;
      grid[x][y].is_empty = 1; 
      grid[x][y].cannot_move = 'a';
    }
}


// The function below prints the maze including the conditoin of every cell.
void print_maze(cell **grid, data *maze_data)
{
  // Print a horizontal row of walls if they are there.
  int x = 0, y = 0;
  for(x = 0; x < (maze_data->dimensions[ROWS]); x++)
  {
    for(y = 0; y < (maze_data->dimensions[COLUMNS]); y++)
    {
      fprintf(stdout, "+");
      if(grid[x][y].north_wall == 1)
        fprintf(stdout, "---");
      else if(grid[x][y].north_wall == 0)
        fprintf(stdout, "   ");
    }
    fprintf(stdout, "+\n"); 

    // Print a vertical row of walls and/or statuses.
    for(y = 0; y < maze_data->dimensions[COLUMNS]; y++)
    {
      if(grid[x][y].west_wall == 1 && grid[x][y].start_here == 1)
        fprintf(stdout, "| S ");
      else if(grid[x][y].west_wall == 1 && grid[x][y].finish_here == 1)
        fprintf(stdout, "| F ");
      else if(grid[x][y].west_wall == 0 && grid[x][y].start_here == 1)
        fprintf(stdout, "  S ");
      else if(grid[x][y].west_wall == 0 && grid[x][y].finish_here == 1)
        fprintf(stdout, "  F ");
      else if(grid[x][y].west_wall == 0 && grid[x][y].walked_through == 1)
        fprintf(stdout, "  O ");
      else if(grid[x][y].west_wall == 0 && grid[x][y].backed_through == 1)
        fprintf(stdout, "  X "); 
      else if(grid[x][y].west_wall == 1 && grid[x][y].walked_through == 1)
        fprintf(stdout, "| O ");
      else if(grid[x][y].west_wall == 1 && grid[x][y].backed_through == 1)
        fprintf(stdout, "| X ");
      else if(grid[x][y].west_wall == 1 && grid[x][y].is_empty == 1)
        fprintf(stdout, "|   ");
      else if(grid[x][y].west_wall == 0 && grid[x][y].is_empty == 1)
        fprintf(stdout, "    ");
    }
    if(grid[x][y - 1].east_wall == 1)
    fprintf(stdout, "|\n");    
    else if(grid[x][y - 1].east_wall == 0)
    fprintf(stdout, " \n");

  }

  // Print the final horizontal row of walls.
  for(y = 0; y < maze_data->dimensions[COLUMNS]; y++)
    {
      fprintf(stdout, "+");
      if(grid[x - 1][y].south_wall == 1)
        fprintf(stdout, "---");
      else if(grid[x - 1][y].south_wall == 0)
        fprintf(stdout, "   ");
    }
    fprintf(stdout, "+\n");
}


// The function below sets changes the start_here and finish_here items in the cells 
// specified in the "data" structure. The is_empty items are alos changed for both
// the start and finish cells.
void set_start_and_finish(cell **grid, data *maze_data)
{
  // Set the start and finish coordinates to their unique cells.
  grid[maze_data->start[0]][maze_data->start[1]].start_here = 1;
  grid[maze_data->finish[0]][maze_data->finish[1]].finish_here = 1;
  grid[maze_data->finish[0]][maze_data->finish[1]].is_empty = 0;
  grid[maze_data->start[0]][maze_data->start[1]].is_empty = 0;
}


// The function checks to see where it can move and moves through the maze recursively
// to find the finish point. 
int solve_the_maze(cell **grid, data *maze_data)
{

  // Check if the current cell location is the finish point.
  int count = 0;
  if(grid[maze_data->location[0]][maze_data->location[1]].finish_here == 1)
  {
    maze_data->done = 't';
    system("clear");
    print_maze(grid, maze_data);
    pause2(DELAY);
    return 0;
  }

  // Check if a step north can be taken by checking the north wall and status.
  if(grid[maze_data->location[0]][maze_data->location[1]].north_wall == 0 && grid[maze_data->location[0]][maze_data->location[1]].cannot_move != 'n' && maze_data->done != 't' && grid[maze_data->location[0] - 1][maze_data->location[1]].walked_through != 1 && grid[maze_data->location[0] - 1][maze_data->location[1]].backed_through != 1)
  {
    // Change the "previous" (technically current) cell's status. Then change the location
    // and set the new location that cannot be stepped towards.
    grid[maze_data->location[0]][maze_data->location[1]].is_empty = 0;
    grid[maze_data->location[0]][maze_data->location[1]].walked_through = 1;
    maze_data->location[0] = (maze_data->location[0] - 1);
    grid[maze_data->location[0]][maze_data->location[1]].cannot_move = 's';

    // Clear the screen, print the maze, pause the screen, and recursively call solve_the_maze.
    system("clear");
    print_maze(grid, maze_data);
    pause2(DELAY);
    count = solve_the_maze(grid, maze_data);

    // If the finish cell is found, return count + 1;
    if(maze_data->done == 't') return count + 1;

    // Change the status of the current cell to "backed through".
    grid[maze_data->location[0]][maze_data->location[1]].walked_through = 0;
    grid[maze_data->location[0]][maze_data->location[1]].backed_through = 1;

    // Clear the screen, print the maze, pause the screen, and move backwards a step.
    system("clear");
    print_maze(grid, maze_data);
    pause2(DELAY);
    maze_data->location[0] = (maze_data->location[0] + 1); 
 
  }  

  // Check if a step east can be taken by checking the east wall and status.
  if(grid[maze_data->location[0]][maze_data->location[1]].east_wall == 0 && grid[maze_data->location[0]][maze_data->location[1]].cannot_move != 'e'  && maze_data->done != 't' && grid[maze_data->location[0]][maze_data->location[1] + 1].walked_through != 1 && grid[maze_data->location[0]][maze_data->location[1] + 1].backed_through != 1)
  {
    // Change the "previous" (technically current) cell's status. Then change the location
    // and set the new location that cannot be stepped towards.
    grid[maze_data->location[0]][maze_data->location[1]].is_empty = 0;
    grid[maze_data->location[0]][maze_data->location[1]].walked_through = 1;
    maze_data->location[1] = (maze_data->location[1] + 1);
    grid[maze_data->location[0]][maze_data->location[1]].cannot_move = 'w';

    // Clear the screen, print the maze, pause the screen, and recursively call solve_the_maze.
    system("clear");
    print_maze(grid, maze_data);
    pause2(DELAY);
    count = solve_the_maze(grid, maze_data);

    // If the finish cell is found, return count + 1;
    if(maze_data->done == 't') return count + 1;

    // Change the status of the current cell to "backed through".
    grid[maze_data->location[0]][maze_data->location[1]].walked_through = 0;
    grid[maze_data->location[0]][maze_data->location[1]].backed_through = 1;

    // Clear the screen, print the maze, pause the screen, and move backwards a step.
    system("clear");
    print_maze(grid, maze_data);
    pause2(DELAY);
    maze_data->location[1] = (maze_data->location[1] - 1); 

  }


  if(grid[maze_data->location[0]][maze_data->location[1]].south_wall == 0 && grid[maze_data->location[0]][maze_data->location[1]].cannot_move != 's' && maze_data->done != 't' && grid[maze_data->location[0] + 1][maze_data->location[1]].walked_through != 1 && grid[maze_data->location[0] + 1][maze_data->location[1]].backed_through != 1)
  {
    // Change the "previous" (technically current) cell's status. Then change the location
    // and set the new location that cannot be stepped towards.
    grid[maze_data->location[0]][maze_data->location[1]].is_empty = 0;
    grid[maze_data->location[0]][maze_data->location[1]].walked_through = 1;
    maze_data->location[0] = (maze_data->location[0] + 1);
    grid[maze_data->location[0]][maze_data->location[1]].cannot_move = 'n';

    // Clear the screen, print the maze, pause the screen, and recursively call solve_the_maze.
    system("clear");
    print_maze(grid, maze_data);
    pause2(DELAY);
    count = solve_the_maze(grid, maze_data);

    // If the finish cell is found, return count + 1;
    if(maze_data->done == 't') return count + 1;

    // Change the status of the current cell to "backed through".
    grid[maze_data->location[0]][maze_data->location[1]].walked_through = 0;
    grid[maze_data->location[0]][maze_data->location[1]].backed_through = 1;

    // Clear the screen, print the maze, pause the screen, and move backwards a step.
    system("clear");
    print_maze(grid, maze_data);
    pause2(DELAY);
    maze_data->location[0] = (maze_data->location[0] - 1); 

  }


  if(grid[maze_data->location[0]][maze_data->location[1]].west_wall == 0 && grid[maze_data->location[0]][maze_data->location[1]].cannot_move != 'w' && maze_data->done != 't' && grid[maze_data->location[0]][maze_data->location[1] - 1].walked_through != 1 && grid[maze_data->location[0]][maze_data->location[1] - 1].backed_through != 1)
  {
    // Change the "previous" (technically current) cell's status. Then change the location
    // and set the new location that cannot be stepped towards.
    grid[maze_data->location[0]][maze_data->location[1]].is_empty = 0;
    grid[maze_data->location[0]][maze_data->location[1]].walked_through = 1;
    maze_data->location[1] = (maze_data->location[1] - 1);
    grid[maze_data->location[0]][maze_data->location[1]].cannot_move = 'e';

    // Clear the screen, print the maze, pause the screen, and recursively call solve_the_maze.
    system("clear");
    print_maze(grid, maze_data);
    pause2(DELAY);
    count = solve_the_maze(grid, maze_data);

    // If the finish cell is found, return count + 1;
    if(maze_data->done == 't') return count + 1;

    // Change the status of the current cell to "backed through".
    grid[maze_data->location[0]][maze_data->location[1]].walked_through = 0;
    grid[maze_data->location[0]][maze_data->location[1]].backed_through = 1;

    // Clear the screen, print the maze, pause the screen, and move backwards a step.
    system("clear");
    print_maze(grid, maze_data);
    pause2(DELAY);
    maze_data->location[1] = (maze_data->location[1] + 1); 

  }

  // Clear the screen, print the maze, and return.
  system("clear");
  print_maze(grid, maze_data);
  return 0;
}


// This function "pauses" operations for a specified milisecond amount.
void pause2(unsigned long milsecs)
{
    unsigned long finish = 0L, start = 0L;
    start = clock();
    while( finish < milsecs )
    {
        finish = clock() - start;
        finish = finish / (CLOCKS_PER_SEC / 1000);
    }
}


```

data_struct.c
```
//
// Shawn Dawson
//
// Project 3 COP3411, Feb 18 2011
//
// This file contains all of the functions related to the "data" struct.
//


#include <stdio.h>
#include <stdlib.h>
#include "maze.h"


// The function below creates an instance of the "data" structure and then returns a pointer
// to the new instance.
data *new_data(void)
{
  data *data_box;
  data_box = (data *) malloc(DATA_ITEMS * sizeof(int));
  data_box->dimensions = (int *) malloc(PAIR * sizeof(int)); 
  data_box->start = (int *) malloc(PAIR * sizeof(int));
  data_box->finish = (int *) malloc(PAIR * sizeof(int));
  data_box->location = (int *) malloc(PAIR * sizeof(int));
  data_box->done = 'f';
  data_box->end = 0;
  return data_box;
}


// The function below returns the total number of binary numbers in the input file.
int total_binary(int rows, int columns)
{
  return (((rows * columns) * PAIR) + (rows + columns));
}


// The function below reads from the input file and returns a binary array.
void read_file(int argc, char *argv[], data *maze_data)
{

  FILE *input_file;

  // Check for correct number of arguments, if not, display error message.
  if(argc != PAIR) 
  {
    fprintf(stderr, "Error! Invalid number of arguments. Exiting.\n");
    exit(1);
  }

  // Check that file opens, if not, display error message.   
  if((input_file = fopen(argv[1], "r")) == NULL)
  {
    fprintf(stderr, "Error! Cannot open input file. Exiting.\n");
    exit(1);
  }

  // Read the dimensions into an array.
  int x = 0;
  while(x < PAIR)
    fscanf(input_file, "%d", &maze_data->dimensions[x++]);

  // Read the start coordinates into an array.
  x = 0;
  while(x < PAIR)
    fscanf(input_file, "%d", &maze_data->start[x++]);

  // Set the location to the start coordinates.
  maze_data->location[0] = maze_data->start[0];
  maze_data->location[1] = maze_data->start[1];

  // Read the finish coordinates into an array.
  x = 0;
  while(x < PAIR)
    fscanf(input_file, "%d", &maze_data->finish[x++]);

  // Create an array and dynamically allocate space (based on the dimensions)
  // for the binary list. Read the binary file into the array.
  maze_data->walls = (int *) malloc(sizeof(int) * total_binary(maze_data->dimensions[ROWS], maze_data->dimensions[COLUMNS]));

  x = 0;
  while(!feof(input_file))
    fscanf(input_file, "%d", &maze_data->walls[x++]);

  // Close the file.
  fclose(input_file);
}


```

maze.h
```
//
// Shawn Dawson
//
// Project 3 COP3411, Feb 18 2011
//
// This file contains the prototyped functions for the 
// "cell_struct.c" and "data_struct.c" file.
//

#ifndef maze_h
#define maze_h


#include <unistd.h>
#include <time.h>
#include <stdio.h>
#include <stdlib.h>
#define PAIR 2
#define DATA_ITEMS 4
#define CELL_ITEMS 6
#define ROWS 0
#define COLUMNS 1
#define DELAY 500


// In the structure below north_wall, east_wall, south_wall, and west_wall hold
// a 1 or 0 to represent a wall (or lack thereof). Walked_through and backed_through hold
// a 1 or 0 to indicate if the cell has been walked or backed through. Start_here and
// finish_here hold a 1 or 0 to indicate if the cell is the start or finish point, respectively.
typedef struct 
{
  int north_wall;
  int east_wall;
  int south_wall;
  int west_wall;
  int walked_through;
  int backed_through;
  int start_here;
  int finish_here;
  int is_empty;
  char cannot_move;
}cell;


// In the structure below dimensions holds the number of rows and columns on the maze.
// Start holds the coordinates for the start cell. Finish holds the coordinates for the 
// finish cell. Walls holds the binary representation of every wall (or lack thereof).
// Location holds the coordinates for the current cell location. Done holds the direction
// that the solve_the_maze function cannot take a step in after each step. Steps_taken 
// holds the total number of steps taken for the solution. End holds an integer indicating
// if the end of the maze has been reached or not.  
typedef struct
{
  int *dimensions;
  int *start;
  int *finish;
  int *walls;
  int *location;
  char done;
  int end;
}data;


// Preconditions: Nothing.
// Postconditions: The function will create a "data" structure, allocate space for
// each array that holds a pair of integers (dimensions, start, finish, location), set
// steps_taken and end to 0 (or false), and set done to 'f' (i.e. false).
// Space is not allocated for walls until the file is read, because the dimensions are
// needed for that operation. The function then returns a pointer to this "data" structure.
data *new_data(void);


// Preconditions: The pointer to maze_data, the "data" structure, is expected to
// have memory allocated for all elements and initialized (by the new_data() function).
// Postconditions: The elements of the pointer to the "data" structure maze_data 
// dimensions, start, finish, and location all have their respective pairs of data
// assigned to them from the file.
void read_file(int argc, char *argv[], data *maze_data);


// Preconditions: The parameters rows and columns cannot be an number less than 0.
// Postconditions: The function returns the total number of binary integers, which
// represent walls.
int total_binary(int rows, int columns);


// Preconditions: The pointer to maze_data, the "data" structure, is expected to
// have memory allocated, and be initialized and filled.
// Postconditions: A new 2 dimensional array of cell structures has memory dynamically
// allocated for it, and a double pointer to the 2 dimensional array is returned.
cell **new_grid(data *maze_data);


// Preconditions: The pointer to a 2 dimensional array of cell structures is
// expected to have memory allocated for it already. The pointer to maze_data, the "data"
// structure is expected to have memory allocated for it, and be initialized and filled.
// Postconditions: Each wall of every cell in the 2 dimensional array grid is set
// according to the binary integers which represent walls. Finish_here, start_here,
// walked_through, and backed_through are all initialized to 0 (or false).
// Is_empty is set to 1 (or true) and cannot_move is set to 'a'.
void fill_grid(cell **grid, data *data_maze); 


// Preconditions: The pointer to a 2 dimensional array of cell structures is
// expected to have memory allocated for it already. The pointer to maze_data, the "data"
// structure is expected to have memory allocated for it, and be initialized and filled. 
// Postconditions: Every wall and the status of every cell is printed on the screen.
void print_maze(cell **grid, data *data_maze);

  
// Preconditions: The pointer to a 2 dimensional array of cell structures is
// expected to have memory allocated for it already. The pointer to maze_data, the "data"
// structure is expected to have memory allocated for it, and be initialized and filled.
// Postconditions: The function sets the start and finish coordinates of the "data" structure
// to a specific cell inside the grid by changing the start_here and finish_here items. 
// The is_empty item is also altered for both cells that are marked as the start and finish.
void set_start_and_finish(cell **grid, data *maze_data);


// Preconditions: The pointer to a 2 dimensional array of cell structures is
// expected to have memory allocated for it already. The pointer to maze_data, the "data"
// structure is expected to have memory allocated for it, and be initialized and filled.
// Postconditions: The function changes the location item if it moves to another cell. The 
// function will also change the status of the cell if it moves to another cell. The function
// returns a the nunmber of steps a solution took.
int solve_the_maze(cell **grid, data *maze_data);


// Preconditions: An unsigned long in miliseconds is passed.
// Postconditions: The display is "paused" for some amount of time.
void pause2(unsigned long milsecs);


#endif
```

main.c
```
//
// Shawn Dawson
//
// Project 3 COP3411, Feb 18 2011
//
// This file is the main that runs the program.
//


#include <stdio.h>
#include <stdlib.h>
#include "maze.h"



int main(int argc, char *argv[])
{
  // Create new "data" structure.
  data *maze_data;
  maze_data = new_data();
  

  // Read the file and read all integers into the vector.
  read_file(argc, argv, maze_data);
 

  // Create new grid.
  cell **grid;
  grid = new_grid(maze_data);


  // Fill the grid walls with the corresponding binary.
  fill_grid(grid, maze_data);  


  // Fill in the start and finish coordinates.
  set_start_and_finish(grid, maze_data);


  // Solve the maze
  int x; 
  x = solve_the_maze(grid, maze_data);


  fprintf(stdout, "This solution path takes %d step(s) to complete.\n", x);
 

  return 0;
}
```

input.txt
```
4 10
0 3
3 5

 1 1 1 1 1 1 1 1 1 1
1 1 1 1 1 0 0 0 0 0 1
 1 0 1 0 0 1 1 0 0 1
1 0 0 1 1 0 1 0 0 1 1
 1 1 1 0 0 0 1 1 0 1
1 0 0 1 1 1 1 0 1 0 1
 1 1 0 0 0 1 1 1 1 0
1 0 0 0 0 1 0 0 0 0 1
 1 1 1 1 1 1 1 1 1 1

```

makefile
```
Testfile : cell_struct.o data_struct.o main.o
	gcc cell_struct.o data_struct.o main.o

cell_struct.o: cell_struct.c
	gcc -c cell_struct.c
data_struct.o: data_struct.c
	gcc -c data_struct.c
main.o: main.c
	gcc -c main.c
```

---

