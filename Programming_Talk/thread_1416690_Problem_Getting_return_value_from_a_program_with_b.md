---
title: "Problem: Getting return value from a program with bash script"
date: 2010-02-26
forum: Programming Talk
---

### Post by Navid.Saleh on 2010-02-26
Hi.
I want to get the return value of a program with bash script. we call that program Test.
I searched and I found $? in bash script but I found another problem.
Test has a while. if it works it goes to while. and if it doesn't work it returns 1. I want to execute Test for n time. so I program bash.sh but always the $? is zero and doesn't echo OOPS. what should i do for this. (sorry if you can't understand what i wrote above because I am a new programmer and I don't know programming term)

Test.cpp
-------------
#include <stdlib.h>
#include <iostream>
#include <time.h>

using namespace std;

int main()
{
    srand( time(NULL));
    int r = rand();
    if(r%2 == 0)
    {
          while(true)
          {
                cout << "Hello World" << endl;
                sleep(1);
          }
    }
    else
         return 1;
    return 0;
    
}
------------------


bash.sh
--------------
#! /bin/bash

for i in `seq 0 10`; do
    ./Test
    if [ $? -eq 1]
        then echo "OOPS"
    fi     
done

---

### Post by tomchuk on 2010-02-26
> **Navid.Saleh said:**
> 
```

#! /bin/bash

for i in `seq 0 10`; do
    ./Test
    if [ $? -eq 1]
        then echo "OOPS"
    fi     
done
```

```

#!/bin/bash

for i in {0..10}
do
    ./Test
    RET=$?
    [ $RET -eq 1 ] && echo 'OOPS'
done
```

---

### Post by MadCow108 on 2010-02-26
time only has second resolution
so you'll always get 10 oops (in less than a second) or your program goes in an infinite loop because of the while(true) and never returns

skip the while(true) and add a sleep(1) to the 0 returning branch and its fine

---

### Post by Navid.Saleh on 2010-02-26
@[tomchuk]("http://ubuntuforums.org/member.php?u=1883"): thanks for better bash code.
@[MadCow108]("http://ubuntuforums.org/member.php?u=804725"): thanks for your notification.
but I forgot to write the correct bash code. I want to run 10 Test so I tried to use & after ./Test but always the $? was 0.
this is the correct bash.sh

#!/bin/bash

for i in {0..10}
do
    ./Test &
    RET=$?
    [ $RET -eq 1 ] && echo 'OOPS'
done

if you run this you can't see the OOPS.
thanks

---

### Post by MadCow108 on 2010-02-26
thats because you don't get the return value of the process when you start it with &
just the return value of the subshell creation/forking (or whatever bash does then) which will (almost) always be 0

I don't know an easy solution. Maybe have start a wrapper script with & which writes the return value to a file and read that file continuously in your main script until all processes have ended

---

### Post by falconindy on 2010-02-26
Background the entire innards of the loop:

```
for i in {0..10}; do
  {
    ./Test;
    RET=$?;
    [ $RET -eq 1 ] && echo 'OOPS';
  } &
done
```

You get lots of job control spam, though. Don't know of a way to hide that, offhand.

---

### Post by Navid.Saleh on 2010-02-27
Thanks for your help.

---

