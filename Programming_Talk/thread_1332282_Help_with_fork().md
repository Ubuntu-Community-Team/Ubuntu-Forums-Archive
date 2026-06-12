---
title: "Help with fork()"
date: 2009-11-20
forum: Programming Talk
---

### Post by Dark-Byte on 2009-11-20
Hi I am trying to write a program that uses a fork system call and then have the parent process display the odd numbers and the child display the even numbers
Can someone please tell me if the "myArr" array will be shared by bothe the processes or if each one the parent and the child will have a copy of "myArr."
The odd numbers are displayed but I get a segmentation fault on entering the parent.

Here is the code:

```
#include<stdio.h>
#include<string.h>
#include<sys/types.h>
#include<unistd.h>


int main()
{
  int i;
  int myArr[10];
  int num;
  
  for(i=0; i<10; i++)
  {
    scanf("%d", &myArr[i]);
  }
  int id = fork();
  if(id==0)
  {
    int count;
    count = 0;
    printf("%s","This is the child process\n");
    while(count!=10)
    {
      
      if((myArr[count]%2)==0)
      {
    printf("%d",myArr[count]);
      }
      count++;
    }
    printf("\n");
  }
  else
  {
    int count;
    printf("%s","This is the parent process\n");
    while(count!=10)
    {
    
      if((myArr[count]%2)==1)
      {    
    printf("%d",myArr[count]);
      }
      count++;
    }
    printf("\n");
  }
  return 0;
}
```

---

### Post by Arndt on 2009-11-20
> **Dark-Byte said:**
> Hi I am trying to write a program that uses a fork system call and then have the parent process display the odd numbers and the child display the even numbers
Can someone please tell me if the "myArr" array will be shared by bothe the processes or if each one the parent and the child will have a copy of "myArr."
The odd numbers are displayed but I get a segmentation fault on entering the parent.

Here is the code:

```
#include<stdio.h>
#include<string.h>
#include<sys/types.h>
#include<unistd.h>


int main()
{
  int i;
  int myArr[10];
  int num;
  
  for(i=0; i<10; i++)
  {
    scanf("%d", &myArr[i]);
  }
  int id = fork();
  if(id==0)
  {
    int count;
    count = 0;
    printf("%s","This is the child process\n");
    while(count!=10)
    {
      
      if((myArr[count]%2)==0)
      {
    printf("%d",myArr[count]);
      }
      count++;
    }
    printf("\n");
  }
  else
  {
    int count;
    printf("%s","This is the parent process\n");
    while(count!=10)
    {
    
      if((myArr[count]%2)==1)
      {    
    printf("%d",myArr[count]);
      }
      count++;
    }
    printf("\n");
  }
  return 0;
}
```

It looks OK to me (no, see below), and when I run it, it behaves as it should.

'fork' makes a copy, so the two processes don't share any memory.

Where is the crash? What do you mean by "entering the parent"? Debugging forking processes can be somewhat complicated, but if the crash is in the parent, you ought to see in gdb where something goes wrong.

Now I do see what is wrong: the parent doesn't set count=0. It just happens to be 0 anyway when I run it.

Much of the code is the same, so I suggest making one loop, and only letting the parity test depend on whether it's the child or the parent.

---

### Post by Dark-Byte on 2009-11-20
Hmmm here is the new code that works with a sleep in the if and one in the else; this gives me a cleaner output but I am not sure what the exact difference is when I include and don't include the sleep calls.

Here is the code

```
#include<stdio.h>
#include<string.h>
#include<sys/types.h>
#include<unistd.h>


int main()
{
  int i;
  int myArr[10];
  int num;
  
  for(i=0; i<10; i++)
  {
    scanf("%d", &myArr[i]);
  }
  int id = fork();
  if(id==0)
  {
    sleep(4);
    int count;
    count = 0;
    printf("%s","This is the child process\n");
    while(count!=10)
    {
      
      if((myArr[count]%2)==0)
      {
    printf("%d",myArr[count]);
      }
      count++;
    }
    printf("\n");
  }
  else
  {
    sleep(4);
    int count;
    count = 0;
    printf("%s","This is the parent process\n");
    while(count!=10)
    {
    
      if((myArr[count]%2)==1)
      {    
    printf("%d",myArr[count]);
      }
      count++;
    }
    printf("\n");
  }
  return 0;
}
```

---

### Post by dwhitney67 on 2009-11-20
I cleaned up your code a bit; took out the sleep() statements.  It works fine (as expected) for me.
```

#include <stdio.h>
#include <unistd.h>

int main()
{
  int myArr[10] = {1,2,3,4,5,6,7,8,9,10};
  int count     = 0;

  if (fork() == 0)
  {
    printf("%s","This is the child process\n");

    while (count < 10)
    {
      if ((myArr[count] % 2) == 0)
      {
        printf("%d ", myArr[count]);
      }
      ++count;
    }
    printf("\n");
  }
  else
  {
    printf("%s","This is the parent process\n");

    while (count < 10)
    {
      if((myArr[count] % 2) == 1)
      {
        printf("%d ",myArr[count]);
      }
      ++count;
    }
    printf("\n");
  }

  return 0;
}

```
Output:
```

This is the parent process
1 3 5 7 9 
This is the child process
2 4 6 8 10 

```

---

### Post by dwhitney67 on 2009-11-20
Another working version:
```

#include <stdio.h>
#include <unistd.h>

enum ValType { EVEN, ODD };

void displayArray(const int* array, const size_t arrSize, enum ValType vt)
{
  int remainder = (vt == EVEN ? 0 : 1);
  int count     = 0;

  while (count < arrSize)
  {
    if ((array[count] % 2) == remainder)
    {
      printf("%d ", array[count]);
    }
    ++count;
  }
  printf("\n");
}

int main()
{
  int myArr[10] = {1,2,3,4,5,6,7,8,9,10};
  enum ValType vt = ODD;

  if (fork() == 0)
  {
    printf("%s","This is the child process\n");

    vt = EVEN;
  }
  else
  {
    printf("%s","This is the parent process\n");
  }

  displayArray(myArr, sizeof(myArr)/sizeof(int), vt);

  return 0;
}

```

---

