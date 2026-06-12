---
title: "vector of vectors help in c++ ???"
date: 2009-10-08
forum: Programming Talk
---

### Post by MrStill on 2009-10-08
Hi,

I am an intermediate Java programmer and I am trying to learn C++ so that I can be more versatile. I am working on a function definition which returns a vector of vectors. My code looks like this:

```

vector< vector<double> > NumericalAnalysis::extrapolate(double h, double  x, double tolerance){
    vector< vector<double> > output(1, vector<double>(1));
    output[0][0] = derivative(x, h);
    int row = 1;
    do{
         output.push_back(vector<double>(row + 1));
	 output[row][0] = derivative(x, h / (row + 1));	
	 for(int column = 1; column <= row; column++){
	     output[row][column] = 1 / (pow(4, column - 1) - 1);
	     output[row][column] *= (output[row][column - 1] - output[row - 1][column - 1]);
	     output[row][column] += output[row][column - 1];
	  }
	  row++;
   }while(fabs(output[row][row] - output[row - 1][row - 1]) > tolerance );
   return output;
}

``` 

And my function header in the .h file looks like this:

```
vector< vector<double> > extrapolate(double,double, double);
```

G++ dose not like my function header:

```

NumericalAnalysis.h:9: error: ISO C++ forbids declaration of ‘vector’ with no type
NumericalAnalysis.h:9: error: expected ‘;’ before ‘<’ token

```

If anyone has any ideas on what I am doing wrong, they would be much appreciated. And though I am a Java programmer, I do understand pointers.

Thanks

---

### Post by dwhitney67 on 2009-10-08
In your header file, include <vector>.  Also, in every place in the header file where you reference the vector type, preface this type with the std:: namespace qualifier.  For example:
```

#include <vector>
...
std::vector< std::vector<double> > extrapolate(double,double, double);

```

In your .cpp file, feel free to employ either the use of "using namespace std;" or "using std::vector;" in the global space, or just continue to use the "std::" preface in front of the vector type.

---

### Post by MadCow108 on 2009-10-08
depending on the size of the vector you should consider passing a reference to the vector into the extrapolate function and fill that instead of returning it by value (this will copy the whole vector, which could be very expensive).
```

void extrapolate(std::vector< std::vector<double> > &  vec, double,double, double)

```

---

### Post by MrStill on 2009-10-08
My code now compiles using dwhitney67's advise; thank you. 


> **MadCow108 said:**
> depending on the size of the vector you should consider passing a reference to the vector into the extrapolate function and fill that instead of returning it by value (this will copy the whole vector, which could be very expensive).

I know that passing data structures by value gets expensive in terms of time and space. I am using the philosophy "get it working, then make it better." Out of curiosity, 

```
void extrapolate(std::vector< std::vector<double> > &  vec, double,double, double)
```

what does the code &  vec do? (Though I understand what pointers do, I have a minor amount of experience with addressing).

---

### Post by Habbit on 2009-10-08
A "reference", which is what the T& syntax declares, is nothing but an alias, another name for an object which is stored somewhere else. The effect is similar to having a pointer or, if this is more familiar to you, a Java object reference/handle. In fact, most compilers implement references with hidden pointers, but they can sometimes optimize them away too.

However, when using references, you have to bear in mind that, except for the fact that passing them around is way cheaper than passing the whole object, they behave _exactly_ the same as the object variable. That is, unlike Java object references, C++ references cannot be "rebound" (made to point to another object): assigning something to a reference will assign it to the original variable ```
MyClass myObject("abc"), anotherObject("def");
MyClass& myRef = myObject;
myRef = anotherObject; // This _will_ modify myObject!
```

---

### Post by MadCow108 on 2009-10-08
the & in that context indicates a reference (has nothing to do with the adress operator which also uses & but in different context)
its quite similar to a pointer with a few differences:
a reference cannot be null
a reference cannot be changed to point to something else after declaration (kind of like a * const pointer in C)
you access references just like normal objects with the . instead of ->

---

### Post by MrStill on 2009-10-08
> **MadCow108 said:**
> depending on the size of the vector you should consider passing a reference to the vector into the extrapolate function and fill that instead of returning it by value (this will copy the whole vector, which could be very expensive).
```

void extrapolate(std::vector< std::vector<double> > &  vec, double,double, double)

```

I changed my code to use this method. I get a segmentation fault if I try to add another vector to the vector of vectors. 

```

void NumericalAnalysis::extrapolate(vector< vector<double> >&  out, double x,double h, double tolerance){
	vector< vector <double> > output(1, vector<double>(1));
	output[0][0] = derivative(x, h);
	int row = 1;
	do{
		output.push_back(vector<double>(row + 1));
		output[row][0] = derivative(x, h / (row + 1));	
		for(int column = 1; column <= row; column++){
			output[row][column] = 1 / (pow(4, column - 1) - );
			output[row][column] *= (output[row][column - 1] - output[row - 1][column - 1]);
			output[row][column] += output[row][column - 1];
		}
		row++;
	}while(fabs(output[row][row] - output[row - 1][row - 1]) > tolerance );
	out.swap(output);
}

``` 

If I comment out everything relying on
```
output.push_back(vector<double>(row + 1));
```
I get no error.

My calling function uses this code:
```

	vector< vector <double> > out;
	ext.extrapolate(out, 2, .2, .000001);

```

---

### Post by MadCow108 on 2009-10-08
the problem is not the change but the code logic.
This line is wrong
```

  row++;
}while(fabs(output[row][row] - output[row - 1][row - 1]) > tolerance );

```
you're overrunning the vector with the row index

you should also write floating point values with a dot or f behind (1.0 or 1f) so that you don't end up with unwanted integer divisions. Its not the case here because pow returns a float, but its good style.

---

### Post by MrStill on 2009-10-09
Thanks for all of your help. I reworked is so that I am not going out of bounds. So, if anyone finds this in the future and is looking for this sort of solution, here it is. It fills a lower triangular matrix with values at different stages of derivative estimation. 

```

void NumericalAnalysis::extrapolate(vector< vector<double> >&  out, double x,double h, double tolerance){
	int column = 0;
	int row = 0;
	vector< vector <double> > output(1, vector<double>(1));
	output[row][column] = derivative(x, h);
	do{
		row++;
		output.push_back(vector<double>(row + 1));
		output[row][0] = derivative(x, h / (pow(2, row)));	
		for(column = 1; column < output[row].size(); column++){
			output[row][column] = output[row][column - 1];
	     		output[row][column] += 
               	          ((output[row][column - 1] - output[row - 1][column - 1])/(pow(4, column) - 1));
		}
	}while(fabs(output[row][row] - output[row - 1][row - 1]) > tolerance);
	out.swap(output);
}
```

---

