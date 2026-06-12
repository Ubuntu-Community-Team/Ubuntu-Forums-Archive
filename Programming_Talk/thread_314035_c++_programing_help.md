---
title: "c++ programing help"
date: 2006-12-06
forum: Programming Talk
---

### Post by monolith1986 on 2006-12-06
alright im workin on a program for class and ive pretty much got it done the sad part is the class is online and i have no one who knows what there doing to ask for help some im asking yall. the program is a 5x5 matrix of randomly generated numbers.. the program needs to find the maxvalue of the diffrent coloums and the max for those values. now ive got it to were it will print out the matrix and get the max for all the coloms but i cant figure out how to do the maxvalue of those rows. heres the program.

#include <cstdlib> 
#include <ctime> 
#include <iostream> 

static const int conROWS = 5;
static const int conCOLS = conROWS;

int main(int argc, char* argv[])
{
double matrix[conROWS][conCOLS];
int maxvalue;
int r,c;

srand(clock() + time( NULL )); //seed the random number generator

//fill matrix with random values in range 1..100
for(r=0; r<conROWS; r++)
{
for(c=0; c<conCOLS; c++)
{
matrix[r][c] = (rand() % 100) + 1;
std::cout << matrix[r] << " ";
};
std::cout << std::endl;
};


//work out max row element
for(r=0; r<conROWS; r++)
{
maxvalue= 0;
for(c=0; c<conCOLS; c++)
{
if(matrix[r][c] > maxvalue)
maxvalue = matrix[r][c];
};
std::cout << " \nMax value in row " << r << " is " << maxvalue;
}; 

//todo workout max value overall and display it

return 0;
};

thanks in advance

---

### Post by Wybiral on 2006-12-06
Its pretty simple, the same way you found the max value for each row! Just make an array to hold the max row values and after you find the max value of each row, use that same routine to find the max value of that array! Here's what that would look like...

```

#include <cstdlib>
#include <ctime>
#include <iostream>

static const int conROWS = 5;
static const int conCOLS = conROWS;

int main(int argc, char* argv[])
{
double matrix[conROWS][conCOLS];

double maxvalue[conROWS];

double finalvalue;

int r,c;

srand(clock() + time( NULL )); //seed the random number generator

//fill matrix with random values in range 1..100
std::cout << "Matrix:" << std::endl;
for(r=0; r<conROWS; r++)
{
for(c=0; c<conCOLS; c++)
{
matrix[r][c] = (rand() % 100) + 1;
std::cout << matrix[r][c] << " ";
};
std::cout << std::endl;
};


//work out max row element
for(r=0; r<conROWS; r++)
{
maxvalue[r]= 0;
for(c=0; c<conCOLS; c++)
{
if(matrix[r][c] > maxvalue[r])
maxvalue[r] = matrix[r][c];
};
std::cout << " \nMax value in row " << r << " is " << maxvalue[r];
};

finalvalue = 0;
for(r=0; r<conROWS; r++)
{
if(maxvalue[r]>finalvalue)
finalvalue = maxvalue[r];
}

std::cout << " \nMax of row values is " << finalvalue << std::endl;

//todo workout max value overall and display it

return 0;
};

```

Naturally, this isn't the most efficient way to do it, but if it's for a class, you should probably stick with what you've learned.

---

### Post by amo-ej1 on 2006-12-07
a better way would be like holding one variable 'max' and only increment that  max if you find a new 'maximum' value. That way you will save memory. And this will also be the solution the teacher will (or should) advertise.

---

