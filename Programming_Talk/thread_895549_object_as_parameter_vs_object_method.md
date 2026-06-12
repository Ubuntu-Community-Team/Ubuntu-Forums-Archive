---
title: "object as parameter vs object method"
date: 2008-08-20
forum: Programming Talk
---

### Post by monkeyking on 2008-08-20
Hi I'm doing a statistical mcmc model where I need some random numbers.
I decided to use the ranrot-w generator.

The random number only works when I call the randomnumber method directly,
and not when i give the random number as an parameter to another function.
that is

rg.Random() !=random(rg)

where random simply calls the Random method in the class.

Below is a cut-down code snippet, that illustrates the problem,
it compiles and works under the g++ compiler.

and also the output from the program, it clearly show the the randomizer returns the same value, when called indirectly.

thanks in advance

```

dddddddddddddddddddddddddddddddd:                   0.571800
dddddddddddddddddddddddddddddddd:                   0.493439
dddddddddddddddddddddddddddddddd:                   0.518434
dddddddddddddddddddddddddddddddd:                   0.322902
dddddddddddddddddddddddddddddddd:                   0.996980
dddddddddddddddddddddddddddddddd:                   0.188140
dddddddddddddddddddddddddddddddd:                   0.188140
dddddddddddddddddddddddddddddddd:                   0.188140
dddddddddddddddddddddddddddddddd:                   0.188140
dddddddddddddddddddddddddddddddd:                   0.188140

```

```

#include <iostream>

#include <math.h>

#include <stdio.h>

// Define 32 bit signed and unsigned integers.
// Change these definitions, if necessary, on 64 bit computers
typedef   signed long int32;     
typedef unsigned long uint32;     

class TRanrotWGenerator {              // encapsulate random number generator
  enum constants {                     // define parameters
    KK = 17, JJ = 10, R1 = 19, R2 =  27};
  public:
  double random_normal(double esp,double var);
  void RandomInit(uint32 seed);        // initialization
  int IRandom(int min, int max);       // get integer random number in desired interval
  long double Random();                // get floating point random number
  uint32 BRandom();                    // output random bits  
  TRanrotWGenerator(uint32 seed);      // constructor
  protected:
  int p1, p2;                          // indexes into buffer
  union {                              // used for conversion to float
    long double randp1;
    uint32 randbits[3];};  
  uint32 randbuffer[KK][2];            // history buffer
  uint32 randbufcopy[KK*2][2];         // used for self-test
  enum TArch {LITTLEENDIAN, BIGENDIAN, NONIEEE, EXTENDEDPRECISIONLITTLEENDIAN};
  TArch Architecture;                  // conversion to float depends on computer architecture
};


//these functions are randomizer relateded and used by main bamse

float FRandom(float themin,float themax,TRanrotWGenerator rg);


uint32 _lrotl (uint32 x, int r) {
  return (x << r) | (x >> (sizeof(x)*8-r));}


// constructor:
TRanrotWGenerator::TRanrotWGenerator(uint32 seed) {
  RandomInit(seed);
  // detect computer architecture
  randbits[2] = 0; randp1 = 1.0;
  if (randbits[2] == 0x3FFF) Architecture = EXTENDEDPRECISIONLITTLEENDIAN;
  else if (randbits[1] == 0x3FF00000) Architecture = LITTLEENDIAN;
  else if (randbits[0] == 0x3FF00000) Architecture = BIGENDIAN;
  else Architecture = NONIEEE;}

uint32 TRanrotWGenerator::BRandom() {
  // generate next random number
  uint32 y, z;
  // generate next number
  z = _lrotl(randbuffer[p1][0], R1) + randbuffer[p2][0];
  y = _lrotl(randbuffer[p1][1], R2) + randbuffer[p2][1];
  randbuffer[p1][0] = y; randbuffer[p1][1] = z;
  // rotate list pointers
  if (--p1 < 0) p1 = KK - 1;
  if (--p2 < 0) p2 = KK - 1;
  // perform self-test
  if (randbuffer[p1][0] == randbufcopy[0][0] &&
    memcmp(randbuffer, randbufcopy[KK-p1], 2*KK*sizeof(uint32)) == 0) {
      // self-test failed
      if ((p2 + KK - p1) % KK != JJ) {
        // note: the way of printing error messages depends on system
        // In Windows you may use FatalAppExit
        printf("Random number generator not initialized");}
      else {
        printf("Random number generator returned to initial state");}
      exit(1);}
  randbits[0] = y;
  randbits[1] = z;
  return y;
  }





int TRanrotWGenerator::IRandom(int min, int max) {
  // get integer random number in desired interval
  int retVal;
  int iinterval = max - min + 1;
  if (iinterval <= 0) return 0x80000000;  // error
  int i = int(iinterval * Random());      // truncate
  if (i >= iinterval) i = iinterval-1;
  retVal = min + i;
  //printf("iiiiiiiiiiiiiiiiiiii: \t %d\n",retVal);
  return retVal;}


void TRanrotWGenerator::RandomInit (uint32 seed) {
  // this function initializes the random number generator.
  int i, j;

  // make random numbers and put them into the buffer
  for (i=0; i<KK; i++) {
    for (j=0; j<2; j++) {
      seed = seed * 2891336453UL + 1;
      randbuffer[i][j] = seed;}}
  // set exponent of randp1
  randbits[2] = 0; randp1 = 1.0;
  // initialize pointers to circular buffer
  p1 = 0;  p2 = JJ;
  // store state for self-test
  memcpy (randbufcopy, randbuffer, 2*KK*sizeof(uint32));
  memcpy (randbufcopy[KK], randbuffer, 2*KK*sizeof(uint32));
  // randomize some more
  for (i=0; i<31; i++) BRandom();
}


long double TRanrotWGenerator::Random() {
  // returns a random number between 0 and 1.
  uint32 z = BRandom();  // generate 64 random bits
  
  switch (Architecture) {
  case EXTENDEDPRECISIONLITTLEENDIAN:
    // 80 bits floats = 63 bits resolution
    randbits[1] = z | 0x80000000;  break;
  case LITTLEENDIAN:
    // 64 bits floats = 52 bits resolution
    randbits[1] = (z & 0x000FFFFF) | 0x3FF00000;  break;
  case BIGENDIAN:
    // 64 bits floats = 52 bits resolution
    randbits[0] = (randbits[0] & 0x000FFFFF) | 0x3FF00000;  break;
  case NONIEEE: default:{
    double retVal = (double)z * (1./((double)(uint32)(-1L)+1.));
    printf("ddddddddddddddddddddddddddddddddddd:\t\t%f\n",retVal);
    // not a recognized floating point format. 32 bits resolution
    return retVal;}
  }
  return randp1 - 1.0;}




float FRandom(float themin,float themax,TRanrotWGenerator rg){
  //printf("->themin%f\tthemax%f\n",themin,themax);
  float vars = (themax-themin);
  float vars1 = rg.Random();
  //printf("->vars:%f\t\tvars1:%f\n",vars,vars1);
  return ((themax-themin)*vars1+themin);
}

using namespace std;

int main(){
  TRanrotWGenerator rg = TRanrotWGenerator(0);
  for (int i=0;i<5;i++)
    int var= rg.Random ();
  for (int i=0;i<5;i++)
    int var1= FRandom (0, 1,rg);
}





```

---

### Post by Zugzwang on 2008-08-20
Change:
```

...
float FRandom(float themin,float themax,TRanrotWGenerator rg){
...

```
to:
```

...
float FRandom(float themin,float themax,TRanrotWGenerator &rg){
...

```

This way, the object isn't **copied** every time you call FRandom. In your case the TRanrotWGenerator object it is copied when calling FRandom and the method will only change the variables of the local copy which is discarded when the FRandom function ends. Using a reference instead helps.

BTW: Whats wrong with using a method if you are dealing with objects anyway?

---

### Post by dwhitney67 on 2008-08-20
I have no idea what your question is.  I would recommend that you pass your object (rg) by reference, and not make a new copy of the object in the FRandom() function declaration/definition:
[PHP]// Pass 'rg' by reference
float FRandom(float themin,float themax,TRanrotWGenerator &rg)
{
...
}[/PHP]

---

### Post by monkeyking on 2008-08-20
Thank you!

now it works exactly as I want.

---

