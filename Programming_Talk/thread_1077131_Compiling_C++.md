---
title: "Compiling C++"
date: 2009-02-22
forum: Programming Talk
---

### Post by wolfman1221 on 2009-02-22
I am taking a class in unix programming and my teacher recommended that I use ubuntu to compile c++ assignments. However, I do not what to use in ubuntu or how I would go about that, so if anyone could help me I would really appreciate it. Also, I am quite the newbie at this.

---

### Post by feelshift on 2009-02-22
To compile C++ programs, you need the build-essential package. You can install it trough Synaptic. If you want an IDE, give Geany a try.

---

### Post by era86 on 2009-02-22
Did your teacher provide any information as far as Makefiles and gcc compiling goes?  I'm sure you don't have to figure all of this out on your own, correct?

Just install build-essential and you should have all the tools you need to compile C++ code.

sudo apt-get install build-essential

---

### Post by abhilashm86 on 2009-02-22
so there is not much difficultly in compiling c++ in ubuntu,
create a file of extension programname.cpp,open in any of editors(vim,nano,emacs,gedit), write the code and save it
from terminal,
to compile use,
g++ programename.cpp 

to execute,
./a.out

done so easy right:)try and ask forums,they'll help u out

---

### Post by abhilashm86 on 2009-02-22
to run this c++ program,
go to terminal

gedit pgm.cpp

then type,
#include<iostream>
using namespace std;
int main()
{
 char name[20];
 cout<<"whats ur name"<<endl;
 cin>>name;
 cout<<"hey "<<name<<",how are u doing"<<endl;
}

again save,go to terminal

to compile
abhilash@abhi:~$ g++ pgm.cpp -o pgm

to run
abhilash@abhi:~$ ./pgm

---

### Post by christian8807 on 2009-02-22
By default, you don't get the full vim (which is what I use, but emacs is also good from what I hear), so if you use vi, then be sure to install it. As said earlier, be sure to get the build-essential package. Here's how to make a c++ code. 
1) Open the terminal.
2) Type "vi test.cpp" (no quotes)
3) Press "i" to go in to insert mode.
4) Type a standard c++ code.

```

#include <iostream>
using namespace std;

int main()
{
cout << "Hello World!\n";
return 0;
}

```

4) Press esc to exit insert, then type ":wq" which will save and take you back to the terminal.
5) To compile, type "g++ test.cpp"
6) Finally, run the executable by typing "./a.out"

This is just the very very basic. When you get into it, look into making makefiles, renaming executables, permissions, etc.

Good luck.

---

