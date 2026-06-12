---
title: "need help on io redirection"
date: 2011-04-17
forum: Programming Talk
---

### Post by Jonas thomas on 2011-04-17
I have this project for a c++ class which is taught in a windows environment.  My preference is to do my development in linux.

Basically the application takes console output and produces console output.
The teacher basically provided a test file for input and redirected visual studio for output.
[Edit. His test file has so much data in it, my terminal window isn't preserving all of it when <input.dat.  When I try to redirect from the console to the file I don't pick up input.dat]

His sample program produced this output.
```

*** Auction Program ***

=======================

1. Start a New Auction

2. Add a New Bid

3. View Current Auction

4. End an Auction

5. Exit

=======================

Please Make Your Choice: -2

Error! Invalid Choice





*** Auction Program ***

=======================

1. Start a New Auction

2. Add a New Bid

3. View Current Auction

4. End an Auction

5. Exit

=======================

Please Make Your Choice: 1

Enter Product ID: CS19

Enter Product Name: Pioneer Car Stereo



Adding: CS19  Pioneer Car Stereo
```

My output looks close but isn't picking up the cins from the file redirect

```
 *** Auction Program *** 
 ======================= 
1. Start a New Auction   
2. Add a New Bid 
3. View Current Auction 
4. End an Auction 
5. Exit 
======================= 
Please make your choice: Input was an integer. Just not one I was expecting.. try again 
 *** Auction Program *** 
 ======================= 
1. Start a New Auction   
2. Add a New Bid 
3. View Current Auction 
4. End an Auction 
5. Exit 
======================= 
Please make your choice: Enter Product ID: Enter Product Description:  *** Auction Program *** 
 ======================= 
1. Start a New Auction   
2. Add a New Bid 
3. View Current Auction 
4. End an Auction 
5. Exit 
```

In my code::blocks ide project->setprogram argument I was playing around with this:
```
echo <input.dat  tee > jtoutput.dat
```
This output isn't really part of the grade.. The teacher will run the app in class.. This was just supposed to help us in development.:cry:.

How do I get  <input.dat to showup in jtoutput.dat??

---

### Post by MadCow108 on 2011-04-17
```
echo <input.dat  tee > jtoutput.dat
```
this looks wrong
you probably want something more like this in the terminal:
```
./executable <input.dat | tee joutput.dat
```
(no idea how that translates to codeblocks)

---

### Post by Jonas thomas on 2011-04-17
This is driving me nuts
I'm trying all sorts of permutations... none seem to work.
```
<input.dat   0>&1 > jtoutput.dat
```
This ignores input.dat and reads the keyboard bypassing the display and putting it in the file... ahh^%$^$.

I thought this would error out and it does.
```
input.dat>0>&1 > jtoutput.dat
```

I think... the trick is in the tee command...  Anyone??

---

### Post by Jonas thomas on 2011-04-17
> **MadCow108 said:**
> ```
echo <input.dat  tee > jtoutput.dat
```
this looks wrong
you probably want something more like this in the terminal:
```
./executable <input.dat | tee joutput.dat
```
(no idea how that translates to codeblocks)

I tried 
```
<input.dat | tee joutput.dat
```
in code::blocks

In my build log I get this message
```
Checking for existence: /media/0AFD-2985/CIS2542/Project02/bin/Debug/Project02
Executing: gnome-terminal  --disable-factory --hide-menubar -t Project02 -x /usr/bin/cb_console_runner LD_LIBRARY_PATH=$LD_LIBRARY_PATH:. /media/0AFD-2985/Project02/bin/Debug/Project02 <input.dat | tee jtoutput.dat (in /media/0AFD-2985/Project02/.)

```

Still not correct... I have the same output in both terminal and file both missing the data from input.dat..

But... I need to try this from the terminal to make sure its not a c:b issue.  Back in a minute.

---

### Post by Jonas thomas on 2011-04-17
From the terminal
> ./Project02 <input.dat  | tee joutput.dat
Still doesn't show input.dat being read in....
maddening.
>  *** Auction Program *** 
 ======================= 
1. Start a New Auction   
2. Add a New Bid 
3. View Current Auction 
4. End an Auction 
5. Exit 
======================= 
Please make your choice: Input was an integer. Just not one I was expecting.. try again 
 *** Auction Program *** 
 ======================= 
1. Start a New Auction   
2. Add a New Bid 
3. View Current Auction 
4. End an Auction 
5. Exit 
======================= 
Please make your choice: Enter Product ID: Enter Product Description:  *** Auction Program *** 
 ======================= 
1. Start a New Auction   
2. Add a New Bid 
3. View Current Auction 
4. End an Auction 
5. Exit 
======================= 

---

### Post by Jonas thomas on 2011-04-17
I've sunk way too much time into this diversion...

Just to get my programmed debugged with the test data I'm doing this.
>     do
    {
        cout <<" *** Auction Program *** "<<endl; //*22*
        cout <<" ======================= "<<endl;
        cout <<"1. Start a New Auction   "<<endl;
        cout <<"2. Add a New Bid "<<endl;
        cout <<"3. View Current Auction "<<endl;
        cout <<"4. End an Auction "<<endl;
        cout <<"5. Exit "<<endl;
        cout <<"======================= "<<endl;
        cout <<"Please make your choice: ";
        getline (cin, strChoice);
        cout <<strChoice<<endl;

Perhaps there is no way to do this... Project isn't do for a week... I'll ask the instructor tomorrow to see what settings he used for windows..

---

### Post by MadCow108 on 2011-04-17
works for me:
```
~/prog$ cat test.cpp
#include <iostream>
#include <string>
using namespace std;
int main()
{
   string line;
   do {
     getline(cin, line);
     cout << "line: " << line << endl;
   } while (line != "stop" || cin.fail());
   return 0;
}
~/prog$ g++ test.cpp
~/prog$ cat test.dat
1
as fasf gask
bfas fas fasf 
cfafgg
stop
~/prog$ ./a.out <test.dat 
line: 1
line: as fasf gask
line: bfas fas fasf 
line: cfafgg
line: stop

```

---

### Post by Jonas thomas on 2011-04-17
> **MadCow108 said:**
> works for me:
```
~/prog$ cat test.cpp
#include <iostream>
#include <string>
using namespace std;
int main()
{
   string line;
   do {
     getline(cin, line);
     cout << "line: " << line << endl;
   } while (line != "stop" || cin.fail());
   return 0;
}
~/prog$ g++ test.cpp
~/prog$ cat test.dat
1
as fasf gask
bfas fas fasf 
cfafgg
stop
~/prog$ ./a.out <test.dat 
line: 1
line: as fasf gask
line: bfas fas fasf 
line: cfafgg
line: stop

```

Not exactly what I was hoping for.  What I wanted to see would be something like this.
```
1
line: 1
as fas fasf
line: as fas fasf
bfas fas fasf
line: bfas fas fasf
cfafgg
line: cfafgg
stop
line: stop

Process returned 0 (0x0)   execution time : 154.877 s
Press ENTER to continue.

```
This would represent a simulation of a user entering data into the keyboard. (which is what I just did to emulate your file.)

---

### Post by Jonas thomas on 2011-04-18
Apparently, I've been way..... overthinking this..
The teacher just said to add some couts to make it look like his output.
I'll probably add a preprocessor statement to enable a cout for testing purposes and then disable for presentation..
Thanks madcow for your help.
JT

---

