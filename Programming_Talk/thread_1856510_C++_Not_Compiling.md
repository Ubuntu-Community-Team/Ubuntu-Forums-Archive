---
title: "C++ Not Compiling"
date: 2011-10-08
forum: Programming Talk
---

### Post by DaimyoKirby on 2011-10-08
Hi there.
I was working on a program in C++, and I compiled it, ran it, and then went back to edit it again.
Oddly enough, the buttons to compile are grayed out, and I can't press them, so I can't recompile my program.

Anyone know why this is happening?

---

### Post by cgroza on 2011-10-08
What IDE do you use? Did you save the file?

---

### Post by nickleboyblue on 2011-10-08
Yeah, can't help until you tell us what happened.  we need to know the IDE, the compiler it tries to use, etc.  Also, if the button doesn't work, does g++ from the command line do anything?

---

### Post by MG&amp;TL on 2011-10-08
```

sudo apt-get install g++
cd <source code directory>
g++ -o <nameofprogram> *.cxx
./<nameofprogram>
```For instance.

---

### Post by DaimyoKirby on 2011-10-08
I'm guessing the IDE is the program I'm using (based on my wiki searches), so I suppose that would be Bloodshed Dev C++.
Yes, I saved the file. I had to save it to compile it in the first place.
How would I find the compiler it's trying to use?
Well, nickleboyblue, I'm a real noob at coding and all that, so I don't really get what you mean when you say "g++ from the command line", since I don't know what g++ is.
But, I'm assuming that's what MG&TL is talking about, so I ran those lines of code, and this is what I got. It gets kinda messy, as I try multiple different things:
```

alden@Laptop:/media/D-ERED/School/Tech$ sudo apt-get install g++
[sudo] password for alden: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
g++ is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
alden@Laptop:/media/D-ERED/School/Tech$ g++ -o Ints.cxx
g++: no input files
alden@Laptop:/media/D-ERED/School/Tech$ g++ -o Ints*.cxx
g++: no input files
alden@Laptop:/media/D-ERED/School/Tech$ g++ -o Ints.cpp.cxx
g++: no input files
alden@Laptop:/media/D-ERED/School/Tech$ g++ -o Ints.exe.cxx
g++: no input files
alden@Laptop:/media/D-ERED/School/Tech$ ./Ints.cpp
bash: ./Ints.cpp: Permission denied
alden@Laptop:/media/D-ERED/School/Tech$ sudo ./Ints.cpp
[sudo] password for alden: 
sudo: ./Ints.cpp: command not found
alden@Laptop:/media/D-ERED/School/Tech$ sudo su -
root@Laptop:~# g++ -o Ints.cpp*.cxx
g++: no input files
root@Laptop:~# g++ -o Ints.cpp.cxx
g++: no input files
root@Laptop:~# ./Ints.cpp
-su: ./Ints.cpp: No such file or directory
root@Laptop:~# ./Ints.exe
-su: ./Ints.exe: No such file or directory
root@Laptop:~# exit
logout

```

Also, I don't know if it makes a difference or not, but the program I'm editing, saving, and trying to compile is located on a flash drive.

---

### Post by MG&amp;TL on 2011-10-08
you need to specify a program name.

-o means do not call the ouput the default name, call it <program name> instead.

So in your case:

```
g++ -o Ints Ints.cxx
./Ints
```

For more info, use:

```
man g++
```

---

### Post by DaimyoKirby on 2011-10-08
For some reason it's now working, but I tried running that code anyway:
```

alden@Laptop:/media/D-ERED/School/Tech$ sudo su -
[sudo] password for alden: 
root@Laptop:~# g++ -o Ints Ints.cxx
g++: Ints.cxx: No such file or directory
g++: no input files
root@Laptop:~# ./Ints
-su: ./Ints: No such file or directory
root@Laptop:~# g++ -o Ints Ints.cxx ./Ints
g++: Ints.cxx: No such file or directory
g++: ./Ints: No such file or directory
g++: no input files
root@Laptop:~# exit
logout

```

I also have another question (ignore this if you want, as it probably should go in another post, but I thought to try here first) - In a program I'm trying to write, I want it to output a long double/float, but whenever I run the program, it cuts the decimal. Here's what I have:
```

//Ints.cpp
//Alden Davidson

#include <iostream.h>

int main()
{
    int integer, counter, sum, largest, smallest;
    long double average;
    counter = 0;
    sum = 0;
    largest = 1;
    smallest = 1000000000;
    
    do
    {
        cout << "Please enter an integer(except 0): ";
        cin >> integer;
        if(integer != 0)
                   {
                   counter++; sum = integer + sum;
                   if(integer > largest)
                              {largest = integer;}
                   if(integer < smallest)
                              {smallest = integer;}
                   }
    }
    while(integer != 0);
    
    cout << "You entered " << counter << " integers, not including 0.\n";
    average = sum / counter;
    cout << "\nThe average of the integers was " << average << ".\n";
    cout << "\nThe largest integer entered was " << largest << ".\n";
    cout << "\nThe smallest integer entered was " << smallest << ".\n";
    cout << "\nThe difference between the largest and smallest integer is " << largest - smallest << ".\n";
    
    system("pause");
    return 0;
}

```

As you can see, it's made to input any number of integers, then output various results. "counter" is made to count the number of times user inputs an integer, excepting 0.

---

### Post by cgroza on 2011-10-08
The decimal is lost when dividing the 2 integers. You need to declare them double too to preserve the decimal point.

---

### Post by MG&amp;TL on 2011-10-08
You need to be in the current directory of the source code. cd to it first.

And you don't need to be root, I don't think.

---

### Post by MG&amp;TL on 2011-10-08
In your case, you do.

specific instructions:

```
cd /media/D-ERED/School/Tech
sudo g++ -o Ints Ints.cpp
sudo ./Ints
```

Compiling from command line is an art that is well worth learning, even if you end up with an IDE. Especially if you can learn an editor like Vim or Emacs. Or even Nano would do.

---

### Post by DaimyoKirby on 2011-10-08
Ok, so cgroza's solution worked - I changed:
```

average = sum / counter

```
to:
```

average = **float**(sum) / **float**(counter)

```
and now it works!
I tried your solution anyway, MG&TL, but I got:
```

alden@Laptop:~$ cd /media/D-ERED/School/Tech
alden@Laptop:/media/D-ERED/School/Tech$ sudo g++ -o Ints Ints.cpp
[sudo] password for alden: 
Ints.cpp:4:22: fatal error: iostream.h: No such file or directory
compilation terminated.

```
I think the problem with that is that I'm using some antiquated/deprecated headers (iostream.h), and so that messes it up.

---

### Post by Vaphell on 2011-10-08
is there any reason why you are doing that?

---

### Post by Michael-Siu on 2011-10-08
Hi dude,

Try this and let me know if you had success. This is your code i just added a #include <cstdlib> and using namespace std; 

```
#include <iostream>
#include <cstdlib>
using namespace std;

int main()
{
    int integer, counter, sum, largest, smallest;
    long double average;
    counter = 0;
    sum = 0;
    largest = 1;
    smallest = 1000000000;
    
    do
    {
        cout << "Please enter an integer(except 0): ";
        cin >> integer;
        if(integer != 0)
                   {
                   counter++; sum = integer + sum;
                   if(integer > largest)
                              {largest = integer;}
                   if(integer < smallest)
                              {smallest = integer;}
                   }
    }
    while(integer != 0);
    
    cout << "You entered " << counter << " integers, not including 0.\n";
    average = sum / counter;
    cout << "\nThe average of the integers was " << average << ".\n";
    cout << "\nThe largest integer entered was " << largest << ".\n";
    cout << "\nThe smallest integer entered was " << smallest << ".\n";
    cout << "\nThe difference between the largest and smallest integer is " << largest - smallest << ".\n";
    
    system("pause");
    return 0;
}
```save it as .cpp in your desktop then with your terminal make a cd to your desktop and let's say you saved it as program.cpp , after you've cd to your desktop type ```
g++ program.cpp -o program
```then make ```
./program
```

---

### Post by cgroza on 2011-10-09
> **DaimyoKirby said:**
> 
I tried your solution anyway, MG&TL, but I got:
```

alden@Laptop:~$ cd /media/D-ERED/School/Tech
alden@Laptop:/media/D-ERED/School/Tech$ sudo g++ -o Ints Ints.cpp
[sudo] password for alden: 
Ints.cpp:4:22: fatal error: iostream.h: No such file or directory
compilation terminated.

```I think the problem with that is that I'm using some antiquated/deprecated headers (iostream.h), and so that messes it up.
iostream is not antique nor deprecated. You need to #include <iostream>, without the ".h" at the end because C++ standard headers do not have it. 
If you want to include a standard C header, you append a "c" and to the beginning and remove the ".h".
So:
```

#include <stdlib.h> //wrong way in C++
#include <cstdlib> //right way in C++

```The above applies only to standard headers, and not custom made ones.

And are you sure you installed the build-essential package?

---

### Post by DaimyoKirby on 2011-10-09
I just installed it from [bloodshed.net]("http://www.bloodshed.net/dev/devcpp.html") - what is a *build-essential package*?
Just so you who wonder know, I'm doing this for my computer programming class; I learned to use .h(such as *#include <iostream.h>*) there, and it works fine. My teacher says that there *are* other ways to go about things, we're just learning them with .h.
Yes, I *am* in highschool, and so am quite a novice at coding, and all this stuff you guys are talking about kinda confuses me...
Yes, Michael-Siu, that worked, and it ran successfully.

In summary:
I don't know what happened, but after Dev C++ stopped compiling, I opened it later, and it was working normally and allowed me to compile. So who knows what went wrong - definitely not me. But thank you all for your help, and I'll know what to do and where to go if it stops again.
Of course, if you all would like me to continue in pursuit of troubleshooting the problem, so as to give this thread actual resolution and/or to help others with the same problem, just let me know.

Also, as to my second question:
Cgroza, your solution worked beautifully. Thank you so much.

---

### Post by DaimyoKirby on 2011-10-09
**EDIT:** Sorry, accidental double-post.

---

### Post by nvteighen on 2011-10-09
> **DaimyoKirby said:**
> I just installed it from [bloodshed.net]("http://www.bloodshed.net/dev/devcpp.html") - what is a *build-essential package*?
Just so you who wonder know, I'm doing this for my computer programming class; I learned to use .h(such as *#include <iostream.h>*) there, and it works fine. My teacher says that there *are* other ways to go about things, we're just learning them with .h.
Yes, I *am* in highschool, and so am quite a novice at coding, and all this stuff you guys are talking about kinda confuses me...
Yes, Michael-Siu, that worked, and it ran successfully.

In summary:
I don't know what happened, but after Dev C++ stopped compiling, I opened it later, and it was working normally and allowed me to compile. So who knows what went wrong - definitely not me. But thank you all for your help, and I'll know what to do and where to go if it stops again.
Of course, if you all would like me to continue in pursuit of troubleshooting the problem, so as to give this thread actual resolution and/or to help others with the same problem, just let me know.

Also, as to my second question:
Cgroza, your solution worked beautifully. Thank you so much.

No. OK, do what your teacher tells yo to do, but this is not about "different ways" of doing things.

C++ may be a horrible language, but it's standarized. This means that there is a set of rules established for writing a C++ compiler and Dev-C++ is very well-known to allow things that it shouldn't, e.g. #include <iostream.h>. The risk of using non-standard extensions is that they lock your code down to a specific implementation; sometimes you have no choice (as it seems to be your case), but whenever you have it, the best is to go to that common ground that the C++ standard is meant to be.

About *build-essentials*: It's a package in the Ubuntu repositories. Not sure if it appears on the Software Center, but it surely does on Synaptic, apt-get or aptitude. I hope you know what I'm talking about, because knowing what package repositories are is a key part of keeping a GNU/Linux distribution secure and stable. (If not, please look for it on Google).

Install build-essentials in order to have the C++ headers installed on your computer.

---

### Post by DaimyoKirby on 2011-10-09
Ok, so I searched *build-essential* in Synaptic, and it showed I had it installed (description: informational list of build-essential packages). And it was checked.
So yes, I do have it installed.

Also, that explanation kinda clears things up.

---

### Post by MG&amp;TL on 2011-10-10
> **nvteighen said:**
> ...Dev-C++ is very well-known to allow things that it shouldn't, e.g. #include <iostream.h>. The risk of using non-standard extensions is that they lock your code down to a specific implementation; sometimes you have no choice (as it seems to be your case), but whenever you have it, the best is to go to that common ground that the C++ standard is meant to be.



Dev-C++ is OK for when you're starting out, but when you're ready to move on, try Code::Blocks for an IDE, or (my personal preference) compiling from command-line with an editor and g++.

---

### Post by DaimyoKirby on 2011-10-10
Yeah, ok.
I've really gotten into coding, as I've started to learn it, and so I think I might take another independent study next year on programming.

---

