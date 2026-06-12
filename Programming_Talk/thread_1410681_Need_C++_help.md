---
title: "Need C++ help"
date: 2010-02-19
forum: Programming Talk
---

### Post by tauman5263 on 2010-02-19
Hello,

I'm working on a project for a class I'm taking and I'm stuck.

I'm having troubles with the enumerations of the array indices. For some reason, all of the array elements equal 0.002.

Here's my code:
```

#include <iostream>
using namespace std;

enum region_t {urban, suburban, exurban};

int main(void)
{
  region_t b;
  double a[b][b];
  int cur_sub = 1400000,
      cur_ex = 900000,
      cur_urb = 2100000,
      temp_urb = 0,
      temp_sub = 0,
      temp_ex = 0,
      year = 0;
  int test;

  a[urban][urban] = .011;
  a[urban][suburban] = .003;
  a[urban][exurban] = .007;

  a[suburban][urban] = .001;
  a[suburban][suburban] = .012;
  a[suburban][exurban] = .003;

  a[exurban][urban] = .002;
  a[exurban][suburban] = .006;
  a[exurban][exurban] = .013;

  for(int i = 0; i <= 50; i++)
  {
      temp_urb = cur_urb + (cur_urb*(a[urban][urban])) + (cur_sub*(a[suburban][urban])) + (cur_ex*(a[exurban][urban]));

      temp_sub = (cur_urb*a[urban][suburban]) + ((cur_sub*a[suburban][suburban]) + cur_sub) + (cur_ex*a[exurban][suburban]);

      temp_ex = (cur_urb*a[urban][exurban]) + (cur_sub*a[suburban][exurban]) + (cur_ex*a[exurban][exurban]) + cur_ex;

      cur_sub = temp_sub;
      cur_urb = temp_urb;
      cur_ex = temp_ex;

      if ((i%10) == 0)
      {   
          year = i;

          cout << "Year: " << year << endl
               << "Urban Population   : " << cur_urb << endl
               << "Suburban Population: " << cur_sub << endl
               << "Exurban Population : " << cur_ex << endl << endl; 
      }
  }

  return 0;
}
```

Here's the project description:

A demographic study of the metropolitan area around Dogpatch divided it into three regions -
urban, suburban, and exurban - and published the following table showing annual migration from
one region to another (the numbers represent percentages):
__________Urban___Suburban___Exurban
Urban______1.1______0.3________0.7
Suburban___0.1______1.2________0.3
Exurban____0.2______0.6________1.3

For example, 0.3 percent of the urbanites (0.003 times the current population) move to the
suburbs each year. The diagonal entries represent internal growth rates. Using a two
dimensional array with an enumerated data type for the indices to store this table, write a
program to determine the population after 10, 20, 30, 40, and 50 years. Assume that the
initial populations of the urban, suburban, and exurban regions are 2.1 million, 1.4 million, and
0.9 million respectively.
Let's begin a hand calculated example. In year one, the urban population in urban area will
internally grow by 1.1% (that is population net of births and deaths). Since the beginning urban
population is 2,100,000, a growth by 1.1% yields 2,123,100. In addition, 0.1% of the
suburbanites move into the city. With a suburban population of 1,400,000, 1400 move into the
city. Finally, 0.2% of the exurbanites move into the city, so with an exurban population of
900,000, 1800 move into the city. Thus, at the end of the first year, the urban population is the
sum of 2,123,000 (urbanites) + 1400 who emigrated from the suburbs + 1800 who emigrated
from the hinterlands, for a total of 2,126,300 (incorrect on in-class handout; corrected here).
Similar calculations need to be done to find out the suburban and exurban population at the end
of this first year. The populations at the end of the first year become the starting values for the
populations for the second year. You should hand-calculate the first year results and check your
program to insure that you are getting correct answers.
The output from your program must display the population of the urban, suburban, and
exurban areas at the end of each ten year interval from the tenth through the fiftieth years.
Your code MUST use an enumerated data type for the indices.

---

### Post by Simon17 on 2010-02-19
```

  region_t b;
  double a[b][b];

```

1. b is uninitialize, so using it is wrong.
2. b is not an integer type, so you shouldn't use it to allocate an array.

You have a few more problems, but let's focus on this first.

---

### Post by tauman5263 on 2010-02-19
I think I got it to work.

Is this right?

```
#include <iostream>
using namespace std;

enum region_t {URBAN, SUBURBAN, EXURBAN, NUM_REGIONS};

int main(void)
{
  region_t urban = URBAN;
  region_t suburban = SUBURBAN;
  region_t exurban = EXURBAN;
  double a[NUM_REGIONS][NUM_REGIONS];
  int cur_sub = 1400000,
      cur_ex = 900000,
      cur_urb = 2100000,
      temp_urb = 0,
      temp_sub = 0,
      temp_ex = 0,
      year = 0,
      i;

  a[urban][urban] = .011;
  a[urban][suburban] = .003;
  a[urban][exurban] = .007;

  a[suburban][urban] = .001;
  a[suburban][suburban] = .012;
  a[suburban][exurban] = .003;

  a[exurban][urban] = .002;
  a[exurban][suburban] = .006;
  a[exurban][exurban] = .013;

  for(i = 0; i <= 50; i++)
  {
      temp_urb = cur_urb + (cur_urb*(a[urban][urban])) + (cur_sub*(a[suburban][urban])) + (cur_ex*(a[exurban][urban]));

      temp_sub = (cur_urb*a[urban][suburban]) + ((cur_sub*a[suburban][suburban]) + cur_sub) + (cur_ex*a[exurban][suburban]);

      temp_ex = (cur_urb*a[urban][exurban]) + (cur_sub*a[suburban][exurban]) + (cur_ex*a[exurban][exurban]) + cur_ex;

      cur_sub = temp_sub;
      cur_urb = temp_urb;
      cur_ex = temp_ex;

      if ((i%10) == 0)
      {   
          year = i;

          cout << "Year: " << year << endl
               << "Urban Population   : " << cur_urb << endl
               << "Suburban Population: " << cur_sub << endl
               << "Exurban Population : " << cur_ex << endl << endl; 
      }
  }

  return 0;
}
```

Thanks for the help so far.

---

### Post by Simon17 on 2010-02-19
It looks okay to me. Does it give you the correct output?

---

### Post by tauman5263 on 2010-02-19
I'm pretty sure the output is correct. The numbers after the first year are correct so I'm assuming that the rest is correct. I'm going to do the math myself to make sure.

Thanks for the help.

---

