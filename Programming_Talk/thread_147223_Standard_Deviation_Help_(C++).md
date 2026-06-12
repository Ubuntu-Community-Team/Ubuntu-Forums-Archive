---
title: "Standard Deviation Help (C++)"
date: 2006-03-19
forum: Programming Talk
---

### Post by Joshuwa on 2006-03-19
Hi,

I wrote a small program that takes a file consisting of 2 columns, puts each column into it's own array, and then calculates the sum, average, and standard deviation of each column.

My sums and average come out accurate in comparison to a control, but for some reason, my standard deviation is just a tiny bit off, and I cannot figure out why :-k 

The formula I'm using for the standard deviation is
```
	for(z=0;z<=count;z++)
		{	x += pow(colx[z]-avgx,2);
			y += pow(coly[z]-avgy,2);
		}
		
	stdx = sqrt(x/count);
	stdy = sqrt(y/count);
```

Any ideas?? Thanks in advance for any advice/pointers.

Here is the entire program for reference to what I'm doing:
```

#include <iostream>
#include <iomanip>
#include <fstream>
#include <string>
#include <cmath>
using namespace std;

#define MAX 100

int main ()
{ float colx[MAX],coly[MAX]; // x and y columns
	double sumx,sumy; // sums of each column
	float avgx,avgy; // avg of each column
	float stdx,stdy; // standard deviation of each column
	float x,y; // used in stdev calculation
	int count; // number of lines in the file
	int i,z; // misc counters
	string in; // name of the input file
	fstream infile;
	
// set counts/sums/arrays to 0
	
	sumx,sumy,avgx,avgy,x,y,count = 0;
	
	for(i=0;i<MAX;i++)
		colx[i],coly[i] = 0.0;
		
// begin and prompt user
	
	cout << "Array Program\n\n"
			 << "Input file: ";
	cin >> in;
	
// open the file

	infile.open(in.data(),ios::in);
	
// count lines, store data, compute sums

	while(!infile.eof())
		{ infile >> colx[count];
			infile >> coly[count];
			
			if(!infile.fail())
				{	sumx += colx[count];
					sumy += coly[count];
			
					count++;
				}
		}
		
// close the file
	
	infile.close();
	
// calculate averages

	avgx = sumx/count;
	avgy = sumy/count;
	
// calculate stdev

	for(z=0;z<=count;z++)
		{	x += pow(colx[z]-avgx,2);
			y += pow(coly[z]-avgy,2);
		}
		
	stdx = sqrt(x/count);
	stdy = sqrt(y/count);
	
// output the results

	cout << endl << count << " lines in the file.\n\n";
	cout << "                    X"
			 << "                    Y" << endl;
	cout << "        -------------"
			 << "        -------------" << endl;
				 
	cout << "Sum " << fixed << setprecision(2) << setw(17) << right
			 << sumx << setw(21) << sumy
			 << "\nAvg " << fixed << setprecision(2) << setw(17) << right
			 << avgx << setw(21) << avgy
	     << "\nStdev " << fixed << setprecision(2) << setw(15) << right
			 << stdx << setw(21) << stdy << endl;
	
	return 0;
}

```

---

### Post by hod139 on 2006-03-19
> **Joshuwa]
My sums and average come out accurate in comparison to a control, but for some reason, my standard deviation is just a tiny bit off, and I cannot figure out why :-k 

The formula I'm using for the standard deviation is
```
    for(z=0 said:**
> -avgx,2);
            y += pow(coly[z]-avgy,2);
        }
        
    stdx = sqrt(x/count);
    stdy = sqrt(y/count);
``` 
Any ideas?? Thanks in advance for any advice/pointers.
 
It's been a while for me, but aren't you suppose to divide by count -1?

---

### Post by hod139 on 2006-03-19
Oh, also found another mistake.  In your for loop, you should only go to z < count, not z <= count
```

for(z=0;z<=count;z++)
        {    x += pow(colx[z]-avgx,2);
            y += pow(coly[z]-avgy,2);
        }
        
    stdx = sqrt(x/count);
    stdy = sqrt(y/count); 
``` 
Below is a version that I think should work
```

 for(z=0;z<count;z++)
         {    x += pow(colx[z]-avgx,2);
             y += pow(coly[z]-avgy,2);
         }
         
     stdx = sqrt(x/(count-1));
     stdy = sqrt(y/(count-1));

```

---

### Post by engla on 2006-03-19
Some general suggestions, if you don't mind:

Use longer, more descriptive variable names; you do actually have a lot of counters in that short code, and some variables named like counters (x,y) that aren't. Also, why not define the variables closer to where they are used? You can't do that if you have some kind of course that says you shouldn't, but I think it's a good idea.. makes it easier to break out an independent block of code later too (refactoring)

Also, since you do C++, you could:
use std::vector or something instead of the arrays. No static maxsize, and you can use iterators. The C-ish #define wouldn't be needed, but you should really use the C++ const specifier if you need constants.

Also, some people would like you to not do "using namespace ..", rather list all things you will use "using std::cout, std::ifstream .."

---

### Post by Joshuwa on 2006-03-19
> **hod139]Oh, also found another mistake.  In your for loop, you should only go to z < count, not z <= count
```

for(z=0 said:**
> -avgx,2);
            y += pow(coly[z]-avgy,2);
        }
        
    stdx = sqrt(x/count);
    stdy = sqrt(y/count); 
``` 
Below is a version that I think should work
```

 for(z=0;z<count;z++)
         {    x += pow(colx[z]-avgx,2);
             y += pow(coly[z]-avgy,2);
         }
         
     stdx = sqrt(x/(count-1));
     stdy = sqrt(y/(count-1));

```

Thanks a lot! The (count-1) was my mistake. Weird though - I cound't remember the formula for standard deviation, so I looked it up on Wikipedia, and got this:
[(Click to view image)]("http://upload.wikimedia.org/math/5/c/3/5c3c0e2a4a7cdb91fa08f54dc2e43722.png")
They list that as the "prefered" formula, but also show one using n-1 :confused: 

Thanks for the help, I really appreciate it.

[QUOTE=engla]Some general suggestions, if you don't mind:

Use longer, more descriptive variable names; you do actually have a lot of counters in that short code, and some variables named like counters (x,y) that aren't. Also, why not define the variables closer to where they are used? You can't do that if you have some kind of course that says you shouldn't, but I think it's a good idea.. makes it easier to break out an independent block of code later too (refactoring)

Also, since you do C++, you could:
use std::vector or something instead of the arrays. No static maxsize, and you can use iterators. The C-ish #define wouldn't be needed, but you should really use the C++ const specifier if you need constants.

Also, some people would like you to not do "using namespace ..", rather list all things you will use "using std::cout, std::ifstream .."[/QUOTE]
Thanks for the advice, I'll keep that in mind for sure.

Declaring variables at the beginning, and using the standard namespace is soemthing I have to do for this course :evil: 

This is a second version of an earlier project that we did that computed the same stuff, only it was longer since we hadn't learned arrays then and were creating another file, then reading from it, and we needed to re-write the program using arrays instead this time.

Thanks again for all the help, as a new programmer, I definitely appreciate any advice/tips given.

---

