---
title: "Floating Point Exception, C++"
date: 2010-12-17
forum: Programming Talk
---

### Post by Lolpanda on 2010-12-17
Alright, so I'm taking a class on C++ and the instructor decided to have us do the 8 Queens Problem (still fairly early on, havent done classes or pointers yet). Code's below of what I have so far. As soon as I hit Build and Run (Using Code::Blocks) I get 

```
Floating point exception

Process returned 136 (0x88)   execution time : 0.003 s
Press ENTER to continue.
```

From Gnome-Terminal. It builds fine, no errors, no warnings, so I know (or assume) its not a syntax error. I'm thinking its an issue with the array but I'm not sure how as it looks fine to me.
BoardSize is int'd for readability, and I know 2D Arrays are hell, but its a requirement for the program. If anyone can see something that I'm missing, I'm all ears.


```
// Eric
// 8 Queens Problem

#include<iostream>
#include<stdlib.h>
#include<iomanip>
#include<math.h>

using namespace std;

int BoardSize=8;
void PrintBoard(int [][8]);



int main ()
{
    int ChessBoard[8][8];

    for(int Row=0;Row<=BoardSize;Row++)
    {
       for(int Col=0;Col<=BoardSize;Col++)
       {
           ChessBoard[Row][Col] = '.';
       }
    }

    PrintBoard(ChessBoard);


    return 0;
}

void PrintBoard(int ChessBoard[][8])
{
    int count=0;
    for(int Row=0;Row<=BoardSize;Row++)
    {
       for(int Col=0;Col<=BoardSize;Col++)
       {
           if(BoardSize%count==0)
                cout << endl;

            cout << ChessBoard[Row][Col] << "\t";
            count++;
       }
    }
}
```

---

### Post by gmargo on 2010-12-17
Look at your **for** loops, you go over the end of the array because you use "<=" instead of "<".

---

### Post by Arndt on 2010-12-17
> **Lolpanda said:**
> Alright, so I'm taking a class on C++ and the instructor decided to have us do the 8 Queens Problem (still fairly early on, havent done classes or pointers yet). Code's below of what I have so far. As soon as I hit Build and Run (Using Code::Blocks) I get 

```
Floating point exception

Process returned 136 (0x88)   execution time : 0.003 s
Press ENTER to continue.
```

From Gnome-Terminal. It builds fine, no errors, no warnings, so I know (or assume) its not a syntax error. I'm thinking its an issue with the array but I'm not sure how as it looks fine to me.
BoardSize is int'd for readability, and I know 2D Arrays are hell, but its a requirement for the program. If anyone can see something that I'm missing, I'm all ears.


```
// Eric
// 8 Queens Problem

#include<iostream>
#include<stdlib.h>
#include<iomanip>
#include<math.h>

using namespace std;

int BoardSize=8;
void PrintBoard(int [][8]);



int main ()
{
    int ChessBoard[8][8];

    for(int Row=0;Row<=BoardSize;Row++)
    {
       for(int Col=0;Col<=BoardSize;Col++)
       {
           ChessBoard[Row][Col] = '.';
       }
    }

    PrintBoard(ChessBoard);


    return 0;
}

void PrintBoard(int ChessBoard[][8])
{
    int count=0;
    for(int Row=0;Row<=BoardSize;Row++)
    {
       for(int Col=0;Col<=BoardSize;Col++)
       {
           if(BoardSize%count==0)
                cout << endl;

            cout << ChessBoard[Row][Col] << "\t";
            count++;
       }
    }
}
```

What did you do so far to find the error? The program is not large; if you step through it using pen and paper, you will find the error within a minute.

Another way is to use the debugger. I highly recommend it. In this case, it points out the error wonderfully clearly.

---

### Post by Arndt on 2010-12-17
> **gmargo said:**
> Look at your **for** loops, you go over the end of the array because you use "<=" instead of "<".

That is probably the next point at which it will crash.

To the OP: It's very rare to have a for loop which includes both 0 and a length/size among the numbers it traverses. Either things are 0-based, so we go from 0 to n-1, or we go from 1 to n.

---

### Post by Lolpanda on 2010-12-17
lol.. Thanks guys, I'm such an idiot for not noticing that. And to who asked what I had done the find the error:  Gone through it line by line in my head, which prob why I didn't see it, since I knew what I was TRYING to do

---

### Post by dwhitney67 on 2010-12-18
Also, don't hard-code the value 8 when declaring your array; this would be better:
```

...
**static const** int BoardSize=8;

void PrintBoard(int [][**BoardSize**]);

...
int ChessBoard[**BoardSize**][**BoardSize**];
...

```

---

### Post by muteXe on 2010-12-18
Why would going over an array boundary throw a floating point exception??

---

### Post by dwhitney67 on 2010-12-18
> **muteXe said:**
> Why would going over an array boundary throw a floating point exception??

It is not the array boundary; it is poor math skills:
```

if (BOARD_SIZE % count == 0)

```
Initially 'count' is 0.

---

### Post by muteXe on 2010-12-18
Cheers mate. Looks like I can't see all the code on my phone!

---

