---
title: "Qt: How can I track the time needed by a fuction to execute?"
date: 2007-11-29
forum: Programming Talk
---

### Post by akudewan on 2007-11-29
Hi. I'm a newbie programmer, and I've made a sudoku solving program using Qt 4. Is there any way of tracking the time that my solve() function runs?

For example:
void solve()
{
 // timer starts here

//solving code here

//timer stops & prints time on debug output
}

Will the QTimer class be able to do this? How can I implement it?

Thanks in advance.

---

### Post by smartbei on 2007-11-29
Well, you could always use standard c functions for timing...  Google for a reference for time.h (or ctime). I have never used QTimer but I would assume it is meant for allowing your program to have a timer call a certain callback function every set period of time. See [http://doc.trolltech.com/4.2/qtimer.html](http://doc.trolltech.com/4.2/qtimer.html).

---

### Post by iharrold on 2007-11-29
I am not sure of the code for the QTimer... as I have never used it.

Basically...

// Measure the Processor clock and save as "Start_time"(actually ticks... but not important).

// Do some precessing

// Measure the Processor clock. and save as "End_time"

// Processing_time = End_time - Start_time

// Display Processing_time.

Here it is in regular C
```

#include <iostream>
#include <time.h>
#include <ctime>

//
// 
//
int main(int argc, char** argv) {
    
    // To use TIME
    time_t tStart_time;
    time_t tEnd_time;
    
    tStart_time = time();
    
    // DO some function... defined elsewhere
    foo();
    
    tEnd_time = time();
    
    std::cout<<"Foo() took :"<<difftime(tEnd_time, tStart_time)<<" seconds"<<std::endl;
    
    
    // To use Clock
    clock_t cStart_time;
    clock_t cEnd_time;
    
    cStart_time = clock();
    
    // DO some function... defined elsewhere
    foo();
    
    cEnd_time = clock();
    
    std::cout<<"Foo() took :"<<(cEnd_time - cStart_time)/CLOCKS_PER_SEC<<" seconds"<<std::endl;
    return (EXIT_SUCCESS);
}

```

---

### Post by smartbei on 2007-11-29
You will want to typecast (cEnd_time - cStart_time) to a double, otherwise it wll likely come out 0 every time.

BTW - since you are using iostream that is c++ :D.

---

### Post by iharrold on 2007-11-29
> Re: Qt: How can I track the time needed by a fuction to execute?
You will want to typecast (cEnd_time - cStart_time) to a double, otherwise it wll likely come out 0 every time.

oops... I would have caught that though if I had compiled it.  Just wrote it quickly in the the message box here :0   I'll let the OP figure out how to typecast it.



> BTW - since you are using iostream that is c++ .
bah... details . ;)

---

### Post by smartbei on 2007-11-29
Sorry about the near double-post, just a couple more details :D:
The time function needs as a parameter a pointer to a time_t structure. For some reason, though difftime returns a double it prints it as an int (rounds down), therefore I recommend using the second option, with the casting to double.

---

### Post by akudewan on 2007-11-29
Hi,

Thanks for the quick replies :)

I found a QTime class that should get the job done. If that doesn't work out, I'll just use the standard C++ functions.

```

QTime t;
    t.start();
    some_lengthy_task();
    qDebug("Time elapsed: %d ms", t.elapsed());

```

Thanks again!

---

