---
title: "Code written in Ubuntu won't work in Windows"
date: 2009-10-26
forum: Programming Talk
---

### Post by Arthur_D on 2009-10-26
Hello there, I've recently started to learn programming in C++. I've been using the CodeLite IDE to write and compile my code, and everything was well until yesterday.

I had been writing a simple calculator program which ran in the terminal with no OS-spesific code at all. I copied my file to my NTFS partition before I rebooted into Windows XP. I opened the file with the Dev-C++ IDE and tried to compile and run. Then I was really :o to see a terminal window just a tenth of a second before it shut down. I opened the .exe file again from the Windows terminal to see what was happening, and guess what? Nothing happened at all!

I've now tried to troubleshoot the issue for two days. I've tried the Windows version of CodeLite; I've tried different compilers; I've tried basically everything. The weird part is that if I write a small program in Dev-C++, it runs like it should, but when I replace it with my calculator code, it doesn't. And; the programs I can get to run fine have no different includes, compilation parameters or anything different at all. I've tried to check the encoding on the files, and it's identical. And I've tried to copy the code to pastebin.com, save it, and copy it back. The .exe file even runs fine in Wine. By the laws of logic, it **should run fine in Windows**, but it doesn't.

Oh, and I've checked for compilator warnings and debug information, and with Dev-C++ I get none. CodeLite in Windows gives MinGW errors, but I prefer Dev-C++ in Windows anyway since it outputs an .exe file which stays on the hard disk. CodeLite seems to just run it in memory or something.

I'm sorry if I'm not supposed to ask about this on the Ubuntu forum, but now I'm really desperate. :(

Here's my code: [http://pastebin.com/m497998f9](http://pastebin.com/m497998f9)

---

### Post by SledgeHammer_999 on 2009-10-26
I just copy&pasted your code from pastebin into Notepad. Then saved the file as main.cpp. Then did g++ main.cpp and I had a new .exe that worked perfectly in my computer(WinXP).

I suggest you do the same and not involve IDEs in order to isolate the problem.

---

### Post by OpenGuard on 2009-10-26
> **Arthur_D said:**
> By the laws of logic, it **should run fine in Windows** ...


And it does ( Windows XP SP3, latest MinGW ).

---

### Post by Arthur_D on 2009-10-26
> **SledgeHammer_999 said:**
> I just copy&pasted your code from pastebin into Notepad. Then saved the file as main.cpp. Then did g++ main.cpp and I had a new .exe that worked perfectly in my computer(WinXP).

I suggest you do the same and not involve IDEs in order to isolate the problem.
Thanks for the replies. :)
I tried this, but by some reason it won't start the program at all. It says I'm missing libintl3.dll. Any knowledge on this?

Edit: Now it says I'm missing libiconv2.dll.

---

### Post by Potters Son on 2009-10-26
Do a Google search for that file, download it, and put it in the same folder as your program.

If you don't know what a DLL is (and I don't know how much you know, so if it feels like I'm babying or overwhelming you, sorry in advance), it's a "dynamically linked library", basically an external piece of executable code that I think your program depends on, whether you meant it to or not. Putting it in the same folder as your program allows your program to find and use it.

I hope this helped.

---

### Post by Arthur_D on 2009-10-26
Okay, now I don't get any errors, but behaviour is the same. Not a thing happens. :(
And the .exe file seems way too small; it's only 64kB.

---

### Post by OpenGuard on 2009-10-26
> **Arthur_D said:**
> Okay, now I don't get any errors, but behaviour is the same. Not a thing happens. :(
And the .exe file seems way too small; it's only 64kB.

Weird .. I got 486kB and it works like a charm. Have you tried to compile it from the command line ( manually ) ?

[[IMG]http://i35.tinypic.com/2gwuu4m_th.png[/IMG]]("http://i35.tinypic.com/2gwuu4m.png")

---

### Post by Arthur_D on 2009-10-26
> **OpenGuard said:**
> Weird .. I got 486kB and it works like a charm. Have you tried to compile it from the command line ( manually ) ?
Yes that was what I did. I ran cmd and used cd to the MinGW's bin folder and then: g++.exe \path\to\test.cpp

Edit: I was able to produce a 460kB .exe file now, but same problem as always.

---

### Post by OpenGuard on 2009-10-26
> **Arthur_D said:**
> Yes that was what I did. I ran cmd and used cd to the MinGW's bin folder and then: g++.exe \path\to\test.cpp

Add it's bin directory to the system PATH ( environment variables ) and try again.

---

### Post by Arthur_D on 2009-10-26
Same result.

My computer really must hate me.... :(

---

### Post by froggyswamp on 2009-10-26
Your windows setup could be messed up (maybe by an app or virus, or both).

---

### Post by slavik on 2009-10-26
show us your windows terminal session

---

### Post by Arthur_D on 2009-10-27
Here's the terminal session, the environment variables, and the location of the g++ program.

---

### Post by Arndt on 2009-10-27
> **Arthur_D said:**
> Here's the terminal session, the environment variables, and the location of the g++ program.

You said that this program doesn't work, while some small program written from scratch on Windows works.

If nothing else helps, try making those two programs converge. First, remove stuff from the calculator program until it starts working (in some sense). Then, add things to the small program that works, to make it more similar to the calculator, until it stops working. With luck, you should be able to find something specific that causes the problem.

---

### Post by Arthur_D on 2009-10-27
Well, as you can see, the code is NOT the problem. Other's have made a working .exe out of it. The system may be borked in some sense, even though I can't see how or why. I'm going to try compiling on another computer with Windows XP, and see if that solves the problem.

But it's really a mystery.

---

### Post by OpenGuard on 2009-10-27
```
g++ sample.cpp -o sample
sample

```

Copy & paste them into CLI and let us know if you see any changes. The line in your screenshot was confusing ..

---

### Post by Arthur_D on 2009-10-27
Sorry, no changes at all. It's almost spooky. :p

---

### Post by Arthur_D on 2009-10-27
I've downloaded the newest MinGW on my other computer, which got no IDE's or anything like that on it before. And whadd'ya know, it worked! :o :D

So I might use that as my Windows build machine from now on. I think I got too much crap on the other machine, with previous installations of Cygwin, MinGW, and present different IDE's, so something probably messed up stuff.

Thank you all very much for helping me resolve this issue (well, not totally resolved, but I can live with it). Thanks for your time! :D

---

### Post by Arndt on 2009-10-27
> **Arthur_D said:**
> Well, as you can see, the code is NOT the problem. Other's have made a working .exe out of it. The system may be borked in some sense, even though I can't see how or why. I'm going to try compiling on another computer with Windows XP, and see if that solves the problem.

But it's really a mystery.

Yes, the code is sound, and that's also good to know, but I suggested this technique as a way to pinpoint why it fails on *your* computer. For mysterious errors, that's sometimes the only way forward.

---

### Post by chuse on 2009-10-27
Question: have you checked out the encoding?

---

### Post by Arthur_D on 2009-10-27
Yeah, but it seems like I've probably messed to much with my system, and that's why it fails. I guess I won't use much more time on this - I'll probably continue write my code in Ubuntu on my main computer, and then use Windows XP on my secondary computer to compile for Windows.

Thanks for trying to help though, but I got too fed up with this, so as I said I'll lay it to rest and use the other computer.

Ubuntu FTW! ;)

---

### Post by Arthur_D on 2009-10-27
> **chuse said:**
> Question: have you checked out the encoding?
Yes, I have. It was all the same as the ones that worked in Windows.

---

### Post by Npl on 2009-10-27
just use [MSVC 2008 Express]("http://www.microsoft.com/exPress/") on Windows, mingw is a nightmare. And you can use a C++ Runtime that deserves to be called free way more than GPL Software.

---

### Post by ssam on 2009-10-27
its a very sneaky bug :-)

```
int main ()
{
  **short int choice;**
  double num1, num2, add_result, sub_result, mult_result, div_result;
  int mod_result, mod_num1, mod_num2;
  **while (choice != 0)**
...

```

choice is not initialized. it could contain any value. the program is in a while loop with "while (choice !=0)". so if by chance when choice is created it contains zero, then the program will not run.

some compilers will sometimes set uninitialized values to zero.

if you change to
```
  short int choice=1;
```
then it should work anywhere

the lesson is to always check for compiler warnings. use
```
g++ foo.cpp -Wall
```

---

### Post by Arthur_D on 2009-10-27
> **ssam said:**
> its a very sneaky bug :-)
...
Thanks, but how come it works on my other machine then? The command I used, and code I used was exactly the same. :confused:

---

### Post by ssam on 2009-10-27
> **Arthur_D said:**
> Thanks, but how come it works on my other machine then? The command I used, and code I used was exactly the same. :confused:

because the behavior is undefined.

[http://en.wikipedia.org/wiki/Uninitialized_variable](http://en.wikipedia.org/wiki/Uninitialized_variable)

in practice if you run the same code, with the same compiler and compile options, on the same machine multiple times you will often get the same value in the variable. you might find that if you opened a large application before running the code you would get a different result.

try compiling and running this multiple times
```

#include <stdio.h>
int main()
{
    int a,b,c,d,e,f,g;
    printf("%d %d %d %d %d %d %d\n", a,b,c,d,e,f,g);
}

```
```

$ gcc foo.c
$ ./a.out
0 4195392 0 0 0 4195712 32644
$ ./a.out
0 4195392 0 0 0 4195712 32673

```

and if i compile with optimization i get
```

$ gcc foo.c -O2
$ ./a.out
0 0 0 0 0 0 0
$ ./a.out
0 0 0 0 0 0 0

```

---

### Post by ssam on 2009-10-27
another example, where the memory is spiked with 7s, after that when you dont initialize the memory you may find it still has a seven in it.

```
#include <stdio.h>
void unin()
{
    int a,b,c,d,e,f,g;
    printf("%d %d %d %d %d %d %d\n", a,b,c,d,e,f,g);

}
void sevens(){
	int array[100], i;
	for (i =0; i<100; i++) array[i]=7;
}
int main(){
	unin();
	unin();
	sevens();
	unin();
}
```

---

### Post by Arthur_D on 2009-10-27
Thank you very much! I, as a novice programmer (read that expression on Wikipedia, lol, and got to admit it's true), did not know about this at all.

Right now I'm using Ubuntu, so if it solves the compile issue in Windows on this machine I'll know next time I care to reboot, which might take a while. ;)

Thanks again for letting me know this... okay, never use a variable before it's initialized with a certain value... think I got it. :D

---

### Post by Jekshadow on 2009-10-28
I also recommend initializing all variables before use. It will save you many headaches (like the one you just had).

---

### Post by Zugzwang on 2009-10-29
> **Jekshadow said:**
> I also recommend initializing all variables before use. It will save you many headaches (like the one you just had).

...and also: In Linux, learn to use valgrind! It will also find other situations in which you use non-initialised values to split between cases which the compiler cannot find at compile time. Also, it tracks for memory leaks. Don't even think of considering a program portable if valgrind complains about something that's in your code (it might report problems with libraries you are using, though).

---

### Post by karimruan on 2009-10-29
> **SledgeHammer_999 said:**
> I just copy&pasted your code from pastebin into Notepad. Then saved the file as main.cpp. Then did g++ main.cpp and I had a new .exe that worked perfectly in my computer(WinXP).

I suggest you do the same and not involve IDEs in order to isolate the problem.

I agree with you! It is always best to islolate the problem first.

---

