---
title: "floating point error:overflow in C++"
date: 2007-02-15
forum: Programming Talk
---

### Post by lazyme on 2007-02-15
Hey
I'm trying to solve the Travelling Salesman Problem for around 100 cities using the Ant Colony Optimization algorithm.I tested it with a 52-city problem but after finding 2-3 tours i get 'floating point errorverflow' and the program terminates.
Please help me

```
#include <stdio.h>
#include <stdlib.h>
#include <math.h>
#include <iostream.h>
#include <time.h>
#include "randomc.h"
  // define classes for random number generators
#include "userintf.cpp"
#include "mersenne.cpp"
//#include <conio.h>

#define BIG 999999						//parameters
//#define NumCities 15

#define NumAnts 35
#define beta 1.9

/* learning rate */
#define RHO 0.1

/* exploitation rate */
#define q0 0.9

/* number of iterations */
#define MAXITER 8


int NumCities;
float **Tao;
int **Tour;
int *BestTour;
int *StartCity;
int **VisitedCities1;
int *AntInitInCity;
float **dist;
float *SumLen;
float MinLenTour;
float Tao0;
float *Xpos,  *Ypos;
float **argvals;
float **probvals;
struct citypos
{
  float pos;
  char spc;
};
struct citypos poscity;

int finished;
int randcity;

int i, j, k, t;
int iter;

/* predeclarations */
void calcdistance(float **dist);
float FindNewBestSolution(float MinLenTour, int **Tour, float *SumLen, int
  *BestTour);
void PrintBestPath(int *BestTour);
int ChooseNextCity(int k, int antpos, int**VisitedCities1, float **Tao,
float**dist, float **argvals, float **probvals, double r);
int NonVisitedCities1(int k, int **VisitedCities1);
void lclupdate(float **Tao, int r, int s);
void clr(int NumCities, int **VisitedCities, int **Tour);

int main()
{
  FILE *fp1,  *fp2;
  char *temp;

  double r;
  int32 seed = time(0); // random seed
  TRandomMersenne rg(seed);
  /* Initialization phase */
  //clrscr();
  /* Init random number generator */
  srand(12345);

  /* Init. Min Tour length value */

  MinLenTour = BIG;
  printf("\nEnter the number of cities");
  scanf("%d", &NumCities);
  Xpos = new float[NumCities];
  Ypos = new float[NumCities];


  Tour = new int *[NumAnts];
  VisitedCities1 = new int *[NumAnts];

  BestTour = new int[NumCities + 1];
  StartCity = new int[NumAnts];
  AntInitInCity = new int[NumCities];
  SumLen = new float[NumAnts];

  dist = new float *[NumCities];
  argvals = new float *[NumCities];
  probvals = new float *[NumCities];
  Tao = new float *[NumCities];

  for (i = 0; i < NumCities; i++)
  {
    *(dist + i) = new float[NumCities];
    *(argvals + i) = new float[NumCities];
    *(Tao + i) = new float[NumCities];
    *(probvals + i) = new float[NumCities];
  }

  for (i = 0; i < NumCities; i++)
  {
    *(VisitedCities1 + i) = new int[NumCities];
    *(Tour + i) = new int[NumCities + 1];
  }



  /*---------------------------------------*/
  if ((fp1 = fopen("xcity.txt", "r+")) == 0)
  {
    printf("File error1");
    //getch();
    exit(0);
  }
  if ((fp2 = fopen("ycity.txt", "rt+")) == 0)
  {
    printf("File error2");
    //getch();
    exit(0);
  }

  for (i = 0; i < NumCities; i++)
  {

    fscanf(fp1, "%f", &poscity.pos);
    fscanf(fp1, " ");
    Xpos[i] = poscity.pos;

    fscanf(fp2, "%f", &poscity.pos);
    fscanf(fp2, " ");
    Ypos[i] = poscity.pos;

  }
  fclose(fp1);
  fclose(fp2);
  /* Init. TSP and initial pheromone value */

  Tao0 = 2.4;

  calcdistance(dist);

  /* Init. pheromone level of each link */
  for (i = 0; i < NumCities; i++)
    for (j = 0; j < NumCities; j++)
      Tao[i][j] = Tao0;

/**************** main loop ******************/


/* place each ant in a randomly chosen city */

/* no cities visited yet */
clr(NumCities, VisitedCities1, Tour);


/* place only one ant per city */
for (j = 0; j < NumCities; j++)
  AntInitInCity[j] = 0;

for (k = 0; k < NumAnts; k++)
{
  do
  {
    randcity = rand() % NumCities;
  }
  while (AntInitInCity[randcity]); /*???????*/

  AntInitInCity[randcity] = 1;
  StartCity[k] = randcity;
  VisitedCities1[k][randcity] = 1;
  Tour[k][0] = randcity;
}

/* The ants build their tours */
for (iter = 0; iter < MAXITER; iter++)
{

  for (i = 0; i < NumAnts; i++)
    for (j = 0; j < NumCities; j++)
      VisitedCities1[i][j] = 0;

  for (i = 0; i < NumAnts; i++)
    VisitedCities1[i][StartCity[i]] = 1;


  t = 0;
  finished = 0;
  do
  {
    t = t + 1;

    /* Execute one step for each ant k */
    for (k = 0; k < NumAnts; k++)
    {

      /* choose next city */
      if (NonVisitedCities1(k, VisitedCities1))
      {

        r = rg.Random();
        Tour[k][t] = ChooseNextCity(k, Tour[k][t - 1], VisitedCities1, Tao,
          dist, argvals, probvals, r);
        VisitedCities1[k][Tour[k][t]] = 1;
        lclupdate(Tao, Tour[k][t - 1], Tour[k][t - 1]);
      }
      else
      {
        Tour[k][t] = StartCity[k]; /* ants go back to the initial city */
        finished = 1;
      }
    }

    /* update pheromone level using a local rule */

  }
  while (!finished);

  /* Compute the length of the Tour found by each ant */
  for (k = 0; k < NumAnts; k++)
  {
    SumLen[k] = 0;
    for (t = 0; t < NumCities + 1; t++)
      SumLen[k] += dist[Tour[k][t]][Tour[k][t + 1]];
  }

  MinLenTour = FindNewBestSolution(MinLenTour, Tour, SumLen, BestTour);

  printf("\n %f", MinLenTour);

  /* update pheromone level of BestTour using a global rule */
  for (i = 0; i < NumCities; i++)
  {
    Tao[BestTour[i]][BestTour[i + 1]] += (1-RHO) *Tao[BestTour[i]][BestTour[i +
      1]] + RHO *(1.0 / MinLenTour);
    //printf(" %f",Tao[BestTour[i]][BestTour[i+1]]);
  }
}

PrintBestPath(BestTour);
//media/hdc5getch();
return 0;
}

int NonVisitedCities1(int k, int **VisitedCities1)
{
  int i;

  i =  - 1;
  do
  {
    i++;
  }
  while (VisitedCities1[k][i] && i < NumCities);

  if (i == NumCities)
    return (0);
  else
    return (1);
}

int ChooseNextCity(int k, int antpos, int**VisitedCities1, float **Tao,
  float**dist, float **argvals, float **probvals, double r)
{
  int nonvisited;
  int i;
  int NextCity;
  int RndCity;
  double prob_explore; /* probability of exploration */

  float armax, prmax;
  int ArgMaxVal, probMaxVal;
  float sum;




  for (i = 0; i < NumCities; i++)
  for (j = 0; j < NumCities; j++)
  {
    argvals[i][j] = 0;
    probvals[i][j] = 0;
  }

  for (i = 0; i < NumCities; i++)
  {
    if ((!VisitedCities1[k][i]) && (antpos != i))
    {

      argvals[antpos][i] = Tao[antpos][i]*((pow(1 / dist[antpos][i], beta)));

    }
  }
  armax = 0;

  for (i = 0; i < NumCities; i++)
  {
    if (argvals[antpos][i] > armax)
    {
      armax = argvals[antpos][i];
      ArgMaxVal = i;
    }
  }

  /* exploration-exploitation */

  prob_explore = r;

  //printf("%f",r);

  if (prob_explore <= q0)
  {
    NextCity = ArgMaxVal;

  }
  else
  {

    for (i = 0; i < NumCities; i++)
    {
      if ((!VisitedCities1[k][i]) && (antpos != i))
      {
        sum += argvals[antpos][i];
      }
    }


    for (i = 0; i < NumCities; i++)
    {
      if ((!VisitedCities1[k][i]) && (antpos != i))
      {
        probvals[antpos][i] = argvals[antpos][i] / sum;
      }
    }
    prmax = 0;

    for (i = 0; i < NumCities; i++)
    {
      if (probvals[antpos][i] > prmax)
      {
        prmax = probvals[antpos][i];
        probMaxVal = i;
      }
    }
    NextCity = probMaxVal;
  }

  return (NextCity);
}



void calcdistance(float **dist)
{

  int i, j;

  long double a, b;

  for (i = 0; i < NumCities; i++)
  for (j = 0; j < NumCities; j++)
  {
    a = pow(fabs(Xpos[j] - Xpos[i]), 2);
    b = pow(fabs(Ypos[j] - Ypos[i]), 2);
    dist[i][j] = (float)sqrt(a + b);

  }


}

float FindNewBestSolution(float MinLenTour, int **Tour, float *SumLen, int
  *BestTour)
{
  float NewMinLenTour;

  NewMinLenTour = MinLenTour;
  for (k = 0; k < NumAnts; k++)
  if (SumLen[k] < NewMinLenTour)
  {
    for (i = 0; i < NumCities + 1; i++)
      BestTour[i] = Tour[k][i];
    NewMinLenTour = SumLen[k];
  }

  return (NewMinLenTour);
}

void PrintBestPath(int *BestTour)
{
  int i;

  printf("\n Best Path....\n");
  for (i = 0; i < NumCities + 1; i++)
    printf("%d - ", BestTour[i]);
  printf("\n");
}

void lclupdate(float **Tao, int r, int s)
{

  Tao[r][s] += (1-RHO) *Tao[r][s] + RHO * Tao0;
}

void clr(int NumCities, int **VisitedCities1, int **Tour)
{

  for (k = 0; k < NumAnts; k++)
  {
    for (j = 0; j < NumCities; j++)
    {
      VisitedCities1[k][j] = 0;
      Tour[k][j] = 0;
    }
    Tour[k][j + 1] = 0;
  }
}
```

---

### Post by hod139 on 2007-02-15
Some comments, but no answer to your question.  You posted a lot of code, but not enough to actually compile and debug.  This is, at least for me, not good because it is too much code for me to want to look at by hand, and not enough to use a debugger.  I would suggest you compile the code with all warnings turned on and debugging symbols
```

g++ -Wall -g blah.cpp

```and use gdb to debug it.

```

gdb ./a.out

```type 'r' at the gdb prompt to run your code, and after it crashes type 'bt' to get a backtrace and see exactly where it crashed. (without the quotes)

Some other comments, 
Why are you including .cpp files?  The system includes are being included the deprecated way, you should be including
```

#include <cstdio>
#include <cstdlib>
#include <cmath>
#include <iostream>

```At first I thought this was C code, but then I see you are using iostream and new, so I guess this is suppose to be C++ code.  If this is C++ code, why not use some of the STL containers for your variables, instead of the error prone C-style multi-dimensional arrays?

That's it for now.  I might take a closer look at your code, but I doubt it.  If you attach everything so one can build it and test it using a debugger then I bet you will get a lot more help.

---

### Post by lazyme on 2007-02-15
Hey,thanks for the suggestions.Yes this is a c++ code but i have no idea about STL containers.
Btw,I have attached everything [here]("http://d01.megashares.com/?d01=51a94ce")
Thanks again.

---

### Post by hod139 on 2007-02-15
Can you attach the zip file to the forums, I can't figure out how to get it off of the megashares site.  When posting a reply just use the attachments button.  As long as the zip is less than 976.6KB you can attach it directly into the post.

---

### Post by lazyme on 2007-02-15
Okay,attached it  here.

---

### Post by rplantz on 2007-02-16
I have not looked at your code in detail, but I notice that you're using the float data type. Try changing to double. You results may be more accurate, and that may take care of your floating point overflow problem.

Assuming you're using a relatively new x86 platform, all floating point computations are performed in the 80-bit extended mode. They are then rounded to 32 bits for float or 64 bits for double. The only advantage of using float instead of double is saving a few bytes of memory, hardly a concern these days.

---

