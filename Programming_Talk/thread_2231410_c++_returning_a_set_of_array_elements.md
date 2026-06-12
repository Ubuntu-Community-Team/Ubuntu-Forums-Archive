---
title: "c++ returning a set of array elements"
date: 2014-06-25
forum: Programming Talk
---

### Post by matthew13 on 2014-06-25
I have a c++ program which gives me an error triggered by a line in which I attempt to return a set of the elements of an array as a double type variable, as so:

```

dataout=(ch[0]:ch[7])*pow(10,ch[8]);

```

where ch is my array having a total of 8 elements. 

There may be a problem with my use of the 'pow' function, amongst other things, but as presently compiled, this line of code is associated with the following error message from a g++ compier

> 
integral_doss.cpp:85: error: expected `)' before ‘:’ token


I'm not sure what this is about, but I can't see any issues with my use of delimiters or otherwise syntax.


Just in case, here is the complete program, where the problem line comes from a function called 'ReadEnergy' at the bottom.


```

#include <iostream> 
#include <fstream> // Reading and writing files 
#include <string>
#include <vector>
#include <sstream>
#include <cmath>


using namespace std;

double ReadEnergy( int x , string y  );

int main ()

{
    double EFermi = -0.0702842;
    double EnergyMin = 0;
   double EnergyMax = 0;
   string dossdata;
    int steps;
   cout << "Specify number of integration steps:" << endl;
   cin >> steps;


   // Opening a file
  /*ifstream input;
  input.open(input_filename.data());
  if ( !input.is_open() ) {
    cerr << "Could not open file: " << input_filename << endl;
    cerr << "Exiting.... " << endl; 
    return 0;
  }*/

   /*for (int k=0; k < ((EFermi-EnergyMin)/interval); k++)*/

     string ch;
     vector<double> EnergyVector;
     while (ReadEnergy(steps,ch))
     {
         EnergyVector.push_back(ReadEnergy(steps,ch));
     }
     
    double sum = 0;
    double interval = 0.00332445;
     
     for (int k=0; k < EnergyVector.size(); k++)
     {
         sum = sum + 0.5*interval*(EnergyVector[k] + EnergyVector[k+1]);
       
     }
     
     cout << "Number of electrons: " << sum << endl;
         
}
  
  
  double ReadEnergy( int steps , string ch )
  { 
  int count=0;
  char t;
  int i;
  std::ifstream input;
  double dataout;
      input.open ("doss.txt" , std::ifstream::in);
  while ( !input.eof() || count<steps )
    {
      input.get(t);
      if (t=='-')
      {
        ch.push_back(t);
        i=0;
      }
      else if (t==' ')
      {
         i=0;
      }
      else if (i<7)
      {
        ch.push_back(t);
        i++;
      }
      else if (i=11)
      {
        ch.push_back(t);
        dataout=(ch[0]:ch[7])*pow(10,ch[8]);
        count++;
        return dataout;
        ch.clear();
      }
      else
      {
          i++;
      }
            
    }
  }

```

---

### Post by QIII on 2014-06-25
Moved to Programming Talk.

---

### Post by ofnuts on 2014-06-25
My C++ is rusty but I don't recognize the "(ch[0]:ch[7])" syntax. It looks like you are trying to get a slice of the array.

---

### Post by dwhitney67 on 2014-06-25
> **matthew13 said:**
> 
... I can't see any issues with my use of delimiters or otherwise syntax.


I see an issue, as does the compiler.  As ofnuts has mentioned already, the code syntax is incorrect.

I also see other issues in your code that you should check.  For example this:
```

     while (ReadEnergy(steps,ch))
     {
         EnergyVector.push_back(ReadEnergy(steps,ch));
     }

```
Why are you calling ReadEnergy() in a loop?

As I look at ReadEnergy() itself, I see other sloppy code.

Perhaps you should explain what you are attempting to accomplish, and perhaps discuss the data within 'doss.txt'.

Btw, it does appear that you are trying to build a string with data (numbers?) within it, but that's merely a guess.

---

