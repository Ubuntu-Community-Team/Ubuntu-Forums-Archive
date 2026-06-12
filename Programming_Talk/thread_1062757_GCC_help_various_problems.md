---
title: "GCC help: various problems"
date: 2009-02-07
forum: Programming Talk
---

### Post by balagosa on 2009-02-07
it is shocking how most people in this forums are using python. I hope that someone can help me with GCC.

Problems:
1) Let's say I ask for a user Input, which is a string. The Input that I ask will be a location of a file in my hard disk, it would be better if we situate this in windows filesystem format because that is what my teacher uses. After asking for the input, I will print the contents of that file OR I can put the contents of that file in an array/pointer for later use.

2) The over-all output of this program would be a binary file. Let me worry about the content of that file. My question would be: gcc program.c -o prog.bin. a) is "bin" the file extension for binary files b) will this prog.bin be a valid binary file?

I am simultaneously looking at the [GCC user manual v4.2.4]("http://gcc.gnu.org/onlinedocs/gcc-4.2.4/gcc/") for help. But More heads are better than one, hence I am posting here for help.

---

### Post by Zugzwang on 2009-02-07
> **balagosa said:**
> 1) Let's say I ask for a user Input, which is a string. The Input that I ask will be a location of a file in my hard disk, it would be better if we situate this in windows filesystem format because that is what my teacher uses. After asking for the input, I will print the contents of that file OR I can put the contents of that file in an array/pointer for later use.

So where's the question? How to accomplish this? Technically, using the standard techniques, the program will accepts paths in the format used by the underlying operating system, so under windows "C:\hello.txt" is valid while under linux "/tmp/hello.txt" will be a valid path.

Here's a minimal C++ example with incomplete error handling. Ok, this is not C but we're not here to do your homework.
[PHP]
#include <iostream>
#include <fstream>

int main() {
    
    std::string filename;
    std::cout << "Enter file name: ";
    std::cin >> filename;
    
    std::cout << "\nOpening " << filename << "\n";
    
    std::ifstream myfile (filename.c_str());
    if (myfile.is_open()) {
        std::string line;
        std::getline (myfile,line);
        std::cout << "Input: " << line << "\n";
        myfile.close();
     }
    else std::cout << "Error: Unable to open file\n";
}
[/PHP]


> **balagosa said:**
> 
2) The over-all output of this program would be a binary file. Let me worry about the content of that file. My question would be: gcc program.c -o prog.bin. a) is "bin" the file extension for binary files b) will this prog.bin be a valid binary file?

There is no special file extension for binary files in Linux. If they are flagged as executable, you can execute them. Also, "binary" is not the same as "executable". Please look up these terms and use the correct terminology in your next posts in order to avoid confusion here. The output of GCC will be executable unless you got any errors while compiling/linking.

Note that the GCC manual will not help you here - It just tells how to use the compiler quite, not how to solve problems with it. The answer to the second question might actually be in there, but this is not a GCC specific thing.

---

### Post by dwhitney67 on 2009-02-07
The GCC -o option is used to specify the name of the file where the executable image of the application will be created.  It has nothing to do with your assignment.

So for instance, a typical "hello world" program could be compiled/linked as follows:
```

gcc hello.c -o hello.foo

```
The program that you would execute to view the results is 'hello.foo'.  

Typically on *nix systems, developers do not provide a file-extension for executable files, because their need is moot (unlike in windoze). Thus, typically one would compile/link the program above such as:
```

gcc hello.c -o hello

```

For your classroom exercise (and forgive me if it is not), it would appear that you need to create a binary file that contains the equivalent data as that in a text file.  This has absolutely nothing to do with how you name your executable program.  However, you may want to consider adding the .exe extension to your executable file name to appease your windoze-lovin' professor.

---

### Post by balagosa on 2009-02-07
> **Zugzwang said:**
> 
There is no special file extension for binary files in Linux. If they are flagged as executable, you can execute them. Also, "binary" is not the same as "executable". Please look up these terms and use the correct terminology in your next posts in order to avoid confusion here. The output of GCC will be executable unless you got any errors while compiling/linking.


I know of the terminologies. What I was left behind was the "-o" option. I had a mistake in analyzing it's use. Thanks to dwhitney67's reply, I had a quick understanding of what the "-o" option is limited to.

-----------------------------------------------------------------------------

Never in my post did I ask for code. I never stated what I want. But if you take time to analyze my problems then all I wanted were answers/hints to my problems. I never ask for code from people because I have a hard time understanding the system; it will be better if I made my own from scratch. As for your sample code, it is quite useful. I will be translating it into C.

---

