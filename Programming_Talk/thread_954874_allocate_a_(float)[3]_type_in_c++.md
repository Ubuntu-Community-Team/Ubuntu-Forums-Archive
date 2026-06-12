---
title: "allocate a (**float)[3] type in c++"
date: 2008-10-21
forum: Programming Talk
---

### Post by monkeyking on 2008-10-21
I need to pass a datastructure of type (**float)[3], to another object. I haven't made this object, and I'm not allowed to change it. 

How do I allocate a type like pointerpointer array.


If I wanted to allocate a **int I would do the following.
[PHP]
int **allocIntMatrix(int x, int y){
  try{
    int **ppi = new int*[x];
    int  *curPtr = new int [x * y];
    
    for( int i = 0; i < x; ++i) {
      *(ppi + i) = curPtr;
      curPtr += y;
    }
  }catch(std::exception & e){
    printf("\t-> Allocation failed, likely cause: need more memory, will exit.\n");
    exit(0);
  }
[/PHP]
I can't really find a solution myself.

thanks in advance

---

### Post by StOoZ on 2008-10-21
have you considered using a vector instead of pure pointers?

---

### Post by monkeyking on 2008-10-21
Thanks for your response,
but as I wrote in my original post.

I need to pass this structure to another program.

So I need it to have this type.

---

### Post by dribeas on 2008-10-21
> **monkeyking said:**
> I need to pass a datastructure of type (**float)[3], to another object. I haven't made this object, and I'm not allowed to change it. 

How do I allocate a type like pointerpointer array.


If I wanted to allocate a **int I would do the following.
[PHP]
int **allocIntMatrix(int x, int y){
  try{
    int **ppi = new int*[x];
    int  *curPtr = new int [x * y];
    
    for( int i = 0; i < x; ++i) {
      *(ppi + i) = curPtr;
      curPtr += y;
    }
  }catch(std::exception & e){
    printf("\t-> Allocation failed, likely cause: need more memory, will exit.\n");
    exit(0);
  }
[/PHP]
I can't really find a solution myself.

thanks in advance

What is exactly the problem (besides the forgotten return statement and that you are returning a 'pointer to pointer to type' instead of a 'pointer to pointer to pointer' to type)?

---

### Post by monkeyking on 2008-10-21
hey, thanks for your reply.

I'm having more than one problem with this datastructure.
It's apparently not possible to return a type pointer to pointer to array. As the return value of a function call.

But right now I'm just trying to allocate the **[3] type.

this code snippet

[PHP]
  //alloc [4][5][3] tri-dim matrix.
  float **tmp[3] = new float*[5][3];
  for(int i=0 ; i<5 ;i++)
    tmp[i] = new float[4];
[/PHP]

gives me this error msg.

```

g++ test.cpp
test.cpp: In function ‘int main(int, char**)’:
test.cpp:14: error: cannot convert ‘float* (*)[3]’ to ‘float (**)[3]’ in initialization
test.cpp:16: error: cannot convert ‘float*’ to ‘float (*)[3]’ in assignment

```

thanks again

---

### Post by dwhitney67 on 2008-10-21
Is there a reason you MUST allocate the three-dimensional array?  If you know the size of the array up-front, then just declare it as a normal variable.  For example, for a 3x4x5 array:
[php]
float tmp[3][4][5];
[/php]
If later you need to pass this array to a library function, I believe all you would require is to pass the (address of) the array.  Something like:
[php]
SomeLibraryFunction(tmp, 3, 4, 5);
[/php]
If you insist in dealing with pointers, memory allocation and the such, then good luck because this is where a lot of newbies shoot themselves in the foot, and then bitch about the language rather than their competence level (wrt pointers).

Anyhow, without further adieu, here's an example that allocates a 3D array:
[php]
#include <iostream>

void SomeLibraryFunction(float*** array3D, size_t depth, size_t rows, size_t cols)
{
}


int main()
{
  float **array[3] = {0};

  for (size_t i = 0; i < 3; ++i)
  {
    array[i] = new float*[4];            // rows (height)

    for (size_t j = 0; j < 4; ++j)
    {
      array[i][j] = new float[5];        // columns (width)
    }
  }

  // ...

  SomeLibraryFunction(array, 3, 4, 5);

  // ...

  // cleanup
  for (size_t i = 0; i < 3; ++i)
  {
    for (size_t j = 0; j < 4; ++j)
    {
      delete [] array[i][j];
    }
    delete [] array[i];
  }

  return 0;
}
[/php]

P.S.  In your earlier post, I assumed that you meant to say you need to send the array to a library function, not another program.  If indeed you need to send the data to another program, then how you declare your array is really irrelevant.  You will need to send the data to the other program in either ASCII or in binary format, via a pipe, socket, or file.

---

### Post by dribeas on 2008-10-22
> **monkeyking said:**
> But right now I'm just trying to allocate the **[3] type.

[PHP]
  //alloc [4][5][3] tri-dim matrix.
  float **tmp[3] = new float*[5][3];
  for(int i=0 ; i<5 ;i++)
    tmp[i] = new float[4];
[/PHP]

Try this, which is just a rewrite of yours:
```

    float ***tmp = new float**[3];
    for ( int j = 0; j < 3; ++j )
    {
        tmp[j] = new float*[5];
        for(int i=0 ; i<5 ;i++)
        {
            tmp[j][i] = new float[4];
        }
    }

```

Of course, you can do all optimizations you did in the first place (allocate just one big 3x5x4 float array and build pointers to the elements).

---

