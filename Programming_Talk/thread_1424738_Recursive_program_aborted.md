---
title: "Recursive program aborted"
date: 2010-03-08
forum: Programming Talk
---

### Post by kcode on 2010-03-08
This is the message I received when recursive program aborted. Is this stack overflow?
```

 (0avgtext+0avgdata 0maxresident)k0inputs+0outputs (0major+270minor)pagefaults 0swaps 
```

Thanks

---

### Post by Zugzwang on 2010-03-08
Never seen such a message. Where does it come from?

Note that page faults (the only number >0) are not really bad (only for performance). See the wikipedia entry on page faults for details.

---

### Post by kcode on 2010-03-08
I guess this is not a stack overflow problem. Checkout this : 
These are 3 instances of program, solution to k-knights problem, with first k = 5 on 5x5 board, second k = 8 on 8x8 board, and third k = 2 on 2x2 board.
```

~/sem/AI/programs$ g++ knights.cpp
~/sem/AI/programs$ /usr/bin/time ./a.out
Solution count = 9386
0.00user 0.00system 0:00.00elapsed 88%CPU (0avgtext+0avgdata 0maxresident)k
0inputs+0outputs (0major+270minor)pagefaults 0swaps

~/sem/AI/programs$ g++ knights.cpp
~/sem/AI/programs$ /usr/bin/time ./a.out
Solution count = 379978716
150.24user 0.10system 2:31.66elapsed 99%CPU (0avgtext+0avgdata 0maxresident)k
0inputs+0outputs (0major+270minor)pagefaults 0swaps

~/sem/AI/programs$ g++ knights.cpp
~/sem/AI/programs$ /usr/bin/time ./a.out
Solution count = 6
0.00user 0.00system 0:00.00elapsed 200%CPU (0avgtext+0avgdata 0maxresident)k
0inputs+0outputs (0major+269minor)pagefaults 0swaps
```
There cannot be stack overflow for k = 2 or k = 5, lest k = 8.

---

### Post by Zugzwang on 2010-03-08
Note that the "time" utility is incapable to detecting stack overflows in Linux. I suggest running your program using valgrind to check if it reports anything suspicious:
```

valgrind --tool=memcheck ./a.out

```

---

### Post by kcode on 2010-03-08
Problem seems to be with /usr/bin/time, as when I ran the program without it, above referred message never occurred.

---

### Post by azagaros on 2010-03-08
Could you post the recursive code for knight.cpp? Not just the call for the recursive stuff.

Recursive structures have tendency to have problems in the way variables are passed.  A page fault generally happen when your program access something that it doesn't own.  Generally you tried access a pointer that wasn't null, or wasn't defined by your standards.  Recursive structures need tight variable control.

Unless I see the offending code I wouldn't know how to attack the issue.

---

### Post by kcode on 2010-03-08
> **Zugzwang said:**
> Note that the "time" utility is incapable to detecting stack overflows in Linux. I suggest running your program using valgrind to check if it reports anything suspicious:
```

valgrind --tool=memcheck ./a.out

```

Oops, was just reading about valrind...

Thanks

---

### Post by kcode on 2010-03-08
Here is the code, unable to attach, therefore, pasting.```
#include <vector>
#include <iostream>
#include <algorithm>
#include <iterator>
#include <bitset>

using namespace std;

#define all(c) c.begin(), c.end()
#define N 8 // Number of knights
#define M 8  // Board size (square)
#define RL 3
#define CL

const unsigned int MS = M*M; //Matrix size
unsigned int sol_count;
vector<pair<int, int> > knights;
int posofattack[8][2] = {
    1, 2,
    1, -2,
    2, 1,
    2, -1,
    -1, 2,
    -1, -2,
    -2, 1,
    -2, -1
};

struct print_knights_positions{
    void operator()(const pair<int, int> &kn) const
    {
        printf("%d %d\n", kn.first, kn.second);
    }
};

bool valid(const int i, const int j) 
{
    return i>=0 && i<M && j>=0 && j<M;
}

void setCellsAttacked(int i, int j, bitset<MS> &m)
{
    int c, x, y;
    for(c=0; c<8; c++){
        x = i + posofattack[c][0];
        y = j + posofattack[c][1];
        if(valid(x, y))
            m.set(x*M+y);
    }
}


void tryPlacing(int k, bitset<MS> m) // Try placing kth knight on matrix/board represented as a bitset
{
    if(k == N){
        //for_each(all(knights), print_knights_positions());
        ++sol_count;
        return;
    }
    int i, j;
    int roffset, coffset;
    if(k - 1 >= 0){
        // If last queen was placed at the end of matrix, then simply return
        int pnr = knights[k-1].first;
        int pnc = knights[k-1].second;
        if(pnr  == M-1 && pnc == M-1)
            return;
        setCellsAttacked(pnr, pnc, m);
        roffset = pnr;
        coffset = pnc + 1;

        // If point is next to the wall, then make offsets
        // point to next row's 0th col.
        if(!valid(roffset, coffset)){
            roffset = pnr + 1;
            coffset = 0;
        }
    }
    else{
        roffset = 0;
        coffset = 0;
    }
    for(i=roffset; i<M; i++){
        for(j=coffset; j<M; j++){
            int index = i*M+j;
            if(m[index]) continue;

            knights[k] = make_pair(i, j);

            m.set(index);
            tryPlacing(k+1, m);
            m.reset(index);
        }
        coffset = 0;
    }
}

void process()
{
    bitset<MS> m;
    tryPlacing(0, m);
}

void display()
{
    printf("Solution count = %d\n", sol_count);
}

void setup()
{
    int i;
    //scanf("%d", &n);
    sol_count = 0;
    for(i=0; i<N; i++)
        knights.push_back(make_pair(0, 0));
}

int main(int argc, char *argv[])
{
    setup();
    process();
    display();

    return 0;
}
```

---

### Post by kcode on 2010-03-08
> **azagaros said:**
> A page fault generally happen when your program access something that it doesn't own.  Generally you tried access a pointer that wasn't null, or wasn't defined by your standards.  Recursive structures need tight variable control.
Isn't that what segmentation fault is?

---

### Post by howlingmadhowie on 2010-03-08
to the best of my knowledge that is the normal output from /usr/bin/time.

---

### Post by MadCow108 on 2010-03-08
yup its normal output:
man time
> 
The default format is:
         %Uuser %Ssystem %Eelapsed %PCPU (%Xtext+%Ddata %Mmax)k
         %Iinputs+%Ooutputs (%Fmajor+%Rminor)pagefaults %Wswaps


a page fault is when your program tries to access memory which has not been mapped from physical to virtual (or vice versa, I don't remember).
This is normal and no problem. The kernel will map it.

what azagaros described is a segmentation fault and that is serious. Inn that case the kernel aborts the process.

---

### Post by kcode on 2010-03-08
> **howlingmadhowie said:**
> to the best of my knowledge that is the normal output from /usr/bin/time.

Yeah, probably you are right. Before this I used either time command or /usr/bin/time --format "%E real time", which never gave such output.

thanks

---

