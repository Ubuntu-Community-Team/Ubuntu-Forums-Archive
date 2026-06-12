---
title: "Question using system() inside c++"
date: 2010-07-15
forum: Programming Talk
---

### Post by sacredfaith on 2010-07-15
Howdy,

Thank  you for all who clicked and are reading...

Quick Stats:
OS: Ubuntu 10.04
 g++ --version:  g++ (Ubuntu 4.4.3-4ubuntu5) 4.4.3

I am currently trying to get system() to work with a char array. The string is:

"dd if=/dev/random of=scanthis.txt conv=notrunc bs=1M count=2"

```

#include<iostream>
#include<fstream>
#include<time.h>
#include<string.h>
#include<stdlib.h>
#include<stdio.h>
#include<unistd.h>
#include<fcntl.h>
#include<sys/stat.h>
#include<sys/types.h>
using namespace std;

int main(){   
    char command[64]="dd if=/dev/random of=scanthis.txt conv=notrunc bs=1M count=2";
    cout << "Starting..." <<  endl;
    system("command"); 
    cout << command << endl;
    cout << "File Creation Complete!" << endl;
    return 0;
}

```Code compiles and runs but does not create scanthis.txt.

Debugging so far I've found that:
when I insert the command in terminal it DOES create scanthis.txt
when I insert a simple shell command 'ls' like this: system("ls"), the ls command works (which means I'm     using the system() syntax correctly (I think)). 

As you might be able to guess from the crazy number of included files, this is the problem-part of a larger program. 

Warm Regards,

sf

---

### Post by PaulM1985 on 2010-07-15
I'm not 100% sure on the usage of the system command, but you have used system("command") with your command variable in quotes.  Did you mean to use system(command)?

Paul

---

### Post by sacredfaith on 2010-07-15
Paul, 

Thank you for your quick reply! Love the forum community.

No. I meant to use system("command") as it's written for the following reason:

> when I insert a simple shell command 'ls' like this: system("ls"), the  ls command works (which means I'm     using the system() syntax  correctly (I think)). 

If you see something wrong with my logic, by all means...

Thanks again for your reply,

-sf

---

### Post by PaulM1985 on 2010-07-15
Erm, not really...

When you use system("ls"), the system is executing the command "ls".  When you use system("command") the system is executing the word "command", not the string that you want to execute.  I would imagine that if you entered:

system("dd if=/dev/random of=scanthis.txt conv=notrunc bs=1M count=2")

it would work as expected because the string to execute is:
"dd if=/dev/random of=scanthis.txt conv=notrunc bs=1M count=2".

So by using system(command) you are really saying system("dd if=/dev/random of=scanthis.txt conv=notrunc bs=1M count=2") and get what you require.  (I reckon)

Paul

---

### Post by dwhitney67 on 2010-07-15
sacredfaith -

You could also trim down the list of included files for your small program, and also rely on the STL string in lieu of a fixed-sized array for your command.

```

#include <cstdlib>
#include <iostream>

int main()
{
    using namespace std;

    string command = "dd if=/dev/random of=scanthis.txt conv=notrunc bs=1M count=2";
    cout << "Starting..." <<  endl;
    system(command.c_str()); 
    cout << command << endl;
    cout << "File Creation Complete!" << endl;
    return 0;
}

```

---

### Post by sacredfaith on 2010-07-15
Paul:

> When you use system("ls"), the system is executing the command "ls".   When you use system("command") the system is executing the word  "command", not the string that you want to execute. Good point. 

dwhitney67: Solved it.

Thank you both very much for your input!! 

-sf

---

