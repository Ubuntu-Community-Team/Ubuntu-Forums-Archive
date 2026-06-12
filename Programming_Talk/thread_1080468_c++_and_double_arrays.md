---
title: "c++ and double arrays"
date: 2009-02-25
forum: Programming Talk
---

### Post by LasherHN on 2009-02-25
I'm trying to use some double arrays, one approach that works is this:

```
#include <iostream>
#include <cstdlib>

using namespace std;

int main() {
   int **a;
   //get memory
   a=new int*[5];
   for(int i=0; i<5; i++)
      a[i]=new int[5];
   //assign
   int k=0;
   for(int i=0; i<x; i++)
      for(int j=0; j<y; j++){
	 a[i][j]=k;
	 k++;
      }
   //print
   for(int i=0; i<5; i++){
      for(int j=0; j<5; j++){
	 cout<<a[i][j]<<" ";
      }
      cout<<endl;
   }
return 0;
}
```

That prints a matrix-like array of 5x5 without any problems.

In another program im doing i need to do that in a separete function like this:

```
#include <iostream>
#include <cstdlib>

using namespace std;

void arraytest(int ***);

int main() {
   int **a;
   arraytest(&a);
   //print
   for(int i=0; i<5; i++){
      for(int j=0; j<5; j++){
	 cout<<a[i][j]<<" ";
      }
      cout<<endl;
   }
   return 0;
}

void arraytest(int ***a){
   //get memory
   *a=new int*[5];
   for(int i=0; i<5; i++)
      *a[i]=new int[5];
   //assign
   int k=0;
   for(int i=0; i<5; i++)
      for(int j=0; j<5; j++){
	 *a[i][j]=k;
	 k++;
      }
}
```

But the second code gives me a segmentation error. Could you tell me please what's wrong with it?

---

### Post by smani on 2009-02-25
Pass the pointer by reference:

```
#include <iostream>
#include <cstdlib>

using namespace std;

void arraytest(int**&);

int main() {
   int **a;
   arraytest(a);
   //print
   for(int i=0; i<5; i++)
      for(int j=0; j<5; j++){
	 cout<<a[i][j]<<" ";
      }
      cout<<endl;

   return 0;
}

void arraytest(int**&a){
   //get memory
   a=new int*[5];
   for(int i=0; i<5; i++)
      a[i]=new int[5];
   //assign
   int k=0;
   for(int i=0; i<5; i++)
      for(int j=0; j<5; j++){
	 a[i][j]=k;
	 k++;
      }
}
```

---

### Post by LasherHN on 2009-02-25
Great that worked perfectly!

I get too confused with pointers/references. Java made me too lazy too care about when I learned :p

Thanks a lot smani.

---

### Post by dwhitney67 on 2009-02-25
There's another way... and you should consider adopting it versus tinkering with the C-style "nuts 'n' bolts".

Here's a simple example using the std::tr1::array, which is similar (if not identical) to Boost's array:
```

#include <tr1/array>
#include <iostream>
#include <iomanip>

static const unsigned int ROWS = 5;
static const unsigned int COLS = 5;

typedef std::tr1::array< std::tr1::array<int, COLS>, ROWS > MyArray;


int main()
{
  MyArray a;

  // initialize array
  for (unsigned int i = 0; i < ROWS; ++i)
  {
    for (unsigned int j = 0; j < COLS; ++j)
    {
      a[i][j] = (j + i + 1) * 2;
    }
  }

  // print array contents
  for (unsigned int i = 0; i < ROWS; ++i)
  {
    for (unsigned int j = 0; j < COLS; ++j)
    {
      std::cout << std::setw(3) << std::setfill(' ') << a[i][j] << " ";
    }
    std::cout << std::endl;
  }
}

```

---

### Post by LasherHN on 2009-02-25
That looks good too, I'll save it aside for the future, for the class I'm taking I think it's better the 'c-style' way.

Thanks for the replies.

---

### Post by Martin Witte on 2009-02-25
If you don't want to use non stl stuff you can go with
```
#include <iostream>
#include <vector>
#include <iomanip>

using namespace std;

typedef vector<int> intvector;
typedef vector< vector<int> > int2dmatrix;

void arraytest(int2dmatrix& matrix, const int& dimension)
{
	int k(0);

	for(int i=0; i < dimension; ++i)
	{
		for(int j=0; j < dimension; ++j)
		{
			matrix[i][j]=k++;
		}
	}
}
int main() {
	const int dimension(5);
	int2dmatrix matrix(dimension, intvector(dimension,0));

	arraytest(matrix, dimension);
	//print
	for(int i = 0; i < dimension; ++i)
	{
		for(int j = 0; j < dimension; ++j)
		{
			cout<< setw(3) << setfill(' ') << matrix[i][j];
		}
		cout<<endl;
	}
	return 0;
}
```

---

