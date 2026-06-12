---
title: "New to Linux"
date: 2007-06-15
forum: Programming Talk
---

### Post by dlp21 on 2007-06-15
Hey all,

So I dabbled in Linux about a decade ago and just never really got into it.  But with all the huss and fuss going on I am giving it another go and have dual booted my Sony Vaio Laptop. 

So this is all very new to me and it is kicking my butt....the problem I haven't been able to get past yet though is compiling and executing c++ files.  

Ok so here is what I have done, I ran sudo apt-get install g++ and build-essential.  I also have the Kdev IDE installed(if there is a better IDE let me know please, I tried emacs but didn't like it).  Anyway I can't figure out how to compile with KDev or rather I don't know how to compile with g++.  

-DLP

---

### Post by TreeFinger on 2007-06-15
Write up a quick program ( I'm assuming you can , if not find a quick tutorial for C++ and copy and paste one ). Save the file somewhere ( I save in ./home/C++ ). Open up the terminal and move to the directory you saved in.

```

:~$ g++ filename.cpp -o filename.out
:~$ ./filename.out

```

The first command will compile the program and show you any errors. If you do not include  -o the output file will be saved as defaultfilename.out .The second command will run the program.

---

### Post by avik on 2007-06-15
The simplest way to compile a C++ program is:

```
g++ *<input filename>* -o *<output filename>*
```

That's it!

Edit: barely missed it!

---

### Post by kevinlyfellow on 2007-06-15
for ide suggestions, check out the gigantic favourite ide thread [http://ubuntuforums.org/showthread.php?t=6762](http://ubuntuforums.org/showthread.php?t=6762)

---

### Post by dlp21 on 2007-06-15
Ok, so I am good on this....now I have a much bigger problem.  I get an error 

david@davidlaptop:~$ g++ helloworld.cpp -o helloworld
helloworld.cpp: In function ‘int main()’:
helloworld.cpp:6: error: ‘cout’ was not declared in this scope

and here is my source a basic helloworld program

#include<iostream>

int main();
int main()
{
  cout << "Hello World!";
  return(0);

}

I have also tried it without the definition of main().

Sorry these are prolly really simple problems for you guys.

---

### Post by xtacocorex on 2007-06-15
You need to define the namespace you are using.  Use std::cout instead of cout.  You also don't need to define main.

---

### Post by TreeFinger on 2007-06-15
```

#include <iostream>
using std::cout

```

You should look for a better tutorial if you are following one. This should have been gone over by now.

I like KDevelop C/C++. I am a beginner myself and I really have no problems with it. I wish I could figure out how to make it default to open a new file with line numbers on the left though. It is annoying having to turn the setting on for each new file.

Anyways I had the same question about compiling/running but I don't think I made a post for it. It took some google searching but I figured it out. You should use google, it is your friend :)

---

### Post by dlp21 on 2007-06-15
Ok

Wow....I can't believe I missed that....I haven't programmed in a long while about 7 years now and forgot that you needed the std:: or the using namespace etc

Anyway thanks for the help with getting the compiler working....now is there a way to intergrate the compiler with Kdev??

---

### Post by gsize on 2007-06-16
in c++:

it need  "using nameplace std"!!

---

### Post by gsize on 2007-06-16
in c++:

it need  "using nameplace std"!!


and "main" don't  defined!!!

---

