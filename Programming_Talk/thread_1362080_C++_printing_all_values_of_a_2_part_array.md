---
title: "C++ printing all values of a 2 part array"
date: 2009-12-22
forum: Programming Talk
---

### Post by Logan513 on 2009-12-22
What in the world am I doing wrong here? :confused:

```
#include <iostream>
using namespace std;

int main(){
    
    int x = 0;
    int y = 0;
    char grid[10][10] = {
        {'#','#','#','#','#','#','#','#','#','#'},
        {'#','.','.','.','.','.','.','.','.','#'},
        {'#','.','.','.','.','.','.','.','.','#'},
        {'#','.','.','.','.','.','.','.','.','#'},
        {'#','.','.','.','.','.','.','.','.','#'},
        {'#','.','.','.','.','.','.','.','.','#'},
        {'#','.','.','.','.','.','.','.','.','#'},
        {'#','.','.','.','.','.','.','.','.','#'},
        {'#','.','.','.','.','.','.','.','.','#'},
        {'#','#','#','#','#','#','#','#','#','#'}
    };

    while (y < 10){
        cout << grid[y][x];
        x++;
        if (x = 9){
            x = 0;
            cout << endl;            
            y++;
        }
    }
    while (y >= 10){
        return 0;
    }
}
```

I am trying to get it to print out all the values of the array. But I can't figure out what I am doing wrong. Can someone help, please?

---

### Post by lisati on 2009-12-22
I would suggest using nested for loops, it might make it easier and clearer.

BTW, you probably don't need the "while (Y>=10)" to enclose your return statement.

---

### Post by Muffinabus on 2009-12-22
if (x = 9)

should be

if (x == 9)

EDIT:  had a typo in my corrections, sorry!

---

### Post by Logan513 on 2009-12-22
for loops...#-o dammit I forgot what those were! *runs off to google*

@ Muffinabus = Let's try it!

EDIT: It's not printing that final line of #'s if I try that.

---

### Post by PeniWize on 2009-12-22
using namespace std;

for (y = 0; 10 > y; ++y)
{[INDENT]      for (x = 0; 10 > x; ++x)
    {[INDENT]         cout << grid[y][x];
[/INDENT]}
    cout << endl;
[/INDENT]}


Alternatively:


#define DIM(ary) (sizeof(ary) / sizeof(*(ary)))

using namespace std;
char *pGrid = grid;
for (x = 0; DIM(grid) > x; ++x)
{[INDENT]     if (0 != x && 0 == x % 10) cout << endl;
    cout << pGrid[x];
[/INDENT]}
cout << endl;


Or even:
 

#define DIM(ary) (sizeof(ary) / sizeof(*(ary)))

using namespace std;
for (char *pIter = grid; grid + DIM(grid) > pIter; ++pIter)
{[INDENT]     if (pIter != grid && 0 == (pIter - grid) % 10) cout << endl;
    cout << *pIter;
[/INDENT]}
cout << endl;

---

### Post by Muffinabus on 2009-12-22
Then change the 9 to a 10.

Should look like this:

```
#include <iostream>
using namespace std;

int main(){
    
    int x = 0;
    int y = 0;
    char grid[10][10] = {
        {'#','#','#','#','#','#','#','#','#','#'},
        {'#','.','.','.','.','.','.','.','.','#'},
        {'#','.','.','.','.','.','.','.','.','#'},
        {'#','.','.','.','.','.','.','.','.','#'},
        {'#','.','.','.','.','.','.','.','.','#'},
        {'#','.','.','.','.','.','.','.','.','#'},
        {'#','.','.','.','.','.','.','.','.','#'},
        {'#','.','.','.','.','.','.','.','.','#'},
        {'#','.','.','.','.','.','.','.','.','#'},
        {'#','#','#','#','#','#','#','#','#','#'}
    };

    while (y < 10){
        cout << grid[y][x];
        x++;
        if (x == 10){
            x = 0;
            cout << endl;            
            y++;
        }
    }
return 0;
}
```

---

### Post by Logan513 on 2009-12-22
Thanks guys! I am really out of it today! :-D

---

### Post by kwyto on 2009-12-22
> **Logan513 said:**
> What in the world am I doing wrong here? :confused:

```
#include <iostream>
using namespace std;

int main(){
    
    int x = 0;
    int y = 0;
    char grid[10][10] = {
        {'#','#','#','#','#','#','#','#','#','#'},
        {'#','.','.','.','.','.','.','.','.','#'},
        {'#','.','.','.','.','.','.','.','.','#'},
        {'#','.','.','.','.','.','.','.','.','#'},
        {'#','.','.','.','.','.','.','.','.','#'},
        {'#','.','.','.','.','.','.','.','.','#'},
        {'#','.','.','.','.','.','.','.','.','#'},
        {'#','.','.','.','.','.','.','.','.','#'},
        {'#','.','.','.','.','.','.','.','.','#'},
        {'#','#','#','#','#','#','#','#','#','#'}
    };

    while (y < 10){
        cout << grid[y][x];
        x++;
        if (x = 9){
            x = 0;
            cout << endl;            
            y++;
        }
    }
    while (y >= 10){
        return 0;
    }
}
```I am trying to get it to print out all the values of the array. But I can't figure out what I am doing wrong. Can someone help, please?

1- change **x = 9, **you want to compare **x **to **9**, not assign **9 **to **x**
2- you don't need to do the last while. once you do just one **return **the function main exits and the program terminates
3- you could have done the same with **for loops**, but whatever you can do with **for** you can do it with **while**.

---

### Post by Logan513 on 2009-12-22
Thanks, but it's all been worked out. :)

---

### Post by kwyto on 2009-12-22
get in the use of marking the thread solved, that avoids people wasting time in continuing to think in the problem. thank you

---

### Post by Queue29 on 2009-12-22
> **PeniWize said:**
> 
for (y = 0; 10 > y; ++y)
{[INDENT]      for (x = 0; 10 > x; ++x)

[/INDENT]}





My brain twitched a little when I read these :(

---

### Post by Logan513 on 2009-12-22
> **kwyto said:**
> get in the use of marking the thread solved, that avoids people wasting time in continuing to think in the problem. thank you

How? :(

---

### Post by kwyto on 2009-12-23
under **thread tools->mark thread as SOLVED**

---

### Post by TheStatsMan on 2009-12-23
The approach used by the OP is not a good one as it is overly complicated and requires 100 unnecessary if statement evaluations. A better approach was put forward earlier that was along the lines of

```

for(int x=0; x < 10; x++){
    for(int y=0; y<10; y++){
        cout<<grid[y][x];
    }
    cout<<endl;
}

```

This solution is simpler and more efficient. Obviously, the efficiency is not an issue here, but it is still good programming practice.

---

### Post by Logan513 on 2009-12-23
@Statsman - Maybe this topic isn't solved after all... ;)

I am looking for the quickest and most efficient way of going about this...

---

