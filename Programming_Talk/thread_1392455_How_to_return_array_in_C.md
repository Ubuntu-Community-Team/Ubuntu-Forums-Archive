---
title: "How to return array in C"
date: 2010-01-28
forum: Programming Talk
---

### Post by Gaurip on 2010-01-28
int *binary(int num)
{
    int i;
    int *a;
    
    do
    {
     for(i=0;i<9;i++)
        {

          a[i] = num%2;
          num=num/2;
          }
     }while((num % 2)!=0);
   return a;
}
int main()
{
    int *arr;
    int i;
    int num;
    int binary(int num);
    printf("enter num : ");
    scanf("%d", &num);
    arr = binary(num);

    for(i=8;i>=0;i--)
    {
     cout << arr[i];
    } 
    getch();
}


This program is of conversion from decimal to binary.
The code is correct but my problem is , I want to print binary output from main().
For that I have to return the array from function which is not working?
can anyone help me?:([-o<

---

### Post by djurny on 2010-01-28
hi,
well i have had a look at the code you posted and some things are not quite ok (or you have a very forgiving compiler)..

binary() does not allocate memory for 'a' in which it is putting integers.. this should have generated a segmentation fault of some sorts..!
binary() returns a pointer to a locally declared variable, that looses scope when binary() is returning to its caller.. 

furthermore, the code is mixing iostreams with stdio functions like printf() and scanf()..

if you allocate some memory prior to calling binary() and pass the pointer to the array to binary(), the function itself can (de)reference the array and put the binary results in it..

```

#include <stdio.h>
#include <iostream>
#include <curses.h>

using namespace std;

int *binary(int num, int a[])
{
  int i;

  do
  {
    for(i=0;i<9;i++)
    {
      a[i] = num % 2;
      num=num/2;
    }
  } while((num % 2)!=0);
  return a;
}

int main()
{
  int arr[10];
  int i;
  int num;

  printf("enter num : ");
  scanf("%d", &num);
  (void)binary(num, arr);

  for(i=8;i>=0;i--)
  {
    cout << arr[i];
  }
}

```

---

### Post by shilpaworld01 on 2010-01-28
I think the only way to do it is to pass in the array as a pointer or reference and let the function do its thing. I don't think you can explicitly return an array.

So you could have your function take in both arrays in the arguments, or (I'm not sure about this one), have it return the address or a pointer to a new array which was created on the heap.

---

### Post by sm_here on 2010-01-28
> **Gaurip said:**
> int *binary(int num)
{
    int i;
    int *a;
    
    do
    {
     for(i=0;i<9;i++)
        {

          a[i] = num%2;
          num=num/2;
          }
     }while((num % 2)!=0);
   return a;
}
int main()
{
    int *arr;
    int i;
    int num;
    int binary(int num);
    printf("enter num : ");
    scanf("%d", &num);
    arr = binary(num);

    for(i=8;i>=0;i--)
    {
     cout << arr[i];
    } 
    getch();
}


This program is of conversion from decimal to binary.
The code is correct but my problem is , I want to print binary output from main().
For that I have to return the array from function which is not working?
can anyone help me?:([-o<
I think the following changes should be enough:
1) In function 'binary', allocate storage to pointer variable 'a' as
int *a=(int*)malloc(9*sizeof(int));
2) The function binary needs to be declared to return a pointer to int 
i.e. int * binary(int);

---

### Post by Arndt on 2010-01-28
> **Gaurip said:**
> int *binary(int num)
{
    int i;
    int *a;
    
    do
    {
     for(i=0;i<9;i++)
        {

          a[i] = num%2;
          num=num/2;
          }
     }while((num % 2)!=0);
   return a;
}
int main()
{
    int *arr;
    int i;
    int num;
    int binary(int num);
    printf("enter num : ");
    scanf("%d", &num);
    arr = binary(num);

    for(i=8;i>=0;i--)
    {
     cout << arr[i];
    } 
    getch();
}


This program is of conversion from decimal to binary.
The code is correct but my problem is , I want to print binary output from main().
For that I have to return the array from function which is not working?
can anyone help me?:([-o<

"cout <<" looks more like C++ than C. But the answers you were given still apply.

---

### Post by DGortze380 on 2010-01-28
Disclaimer: Haven't read the whole thread.

My experience is in C++. You don't return an array, but rather a pointer to an array. You can then access the elements through that pointer.

---

### Post by dwhitney67 on 2010-01-28
My experience is in C++, and C, although I prefer the former.

Here's my take on the solution, where I have attempted my best to avoid anything C-like:
```

#include <iostream>
#include <sstream>
#include <vector>
#include <iterator>

typedef std::vector<unsigned int> BinaryValue;

BinaryValue toBinary(unsigned int num)
{
   BinaryValue bv;

   if (num == 0)
   {
      bv.push_back(num);
   }
   else
   {
      while (num > 0)
      {
         bv.push_back(num % 2);
         num >>= 1;
      }
   }

   return bv;
}

int main(int argc, char** argv)
{
   using namespace std;

   if (argc < 2)
   {
      cerr << "Usage: " << argv[0] << " <number>" << endl;
      return -1;
   }

   unsigned int num = 0;
   stringstream iss(argv[1]);

   iss >> num;

   BinaryValue bv = toBinary(num);

   cout << "The number " << num << " in binary is %";
   copy(bv.rbegin(), bv.rend(), ostream_iterator<unsigned int>(cout, ""));
   cout << endl;
}

```

---

