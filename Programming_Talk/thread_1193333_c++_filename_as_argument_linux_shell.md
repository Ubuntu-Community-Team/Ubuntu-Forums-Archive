---
title: "c++ filename as argument: linux shell"
date: 2009-06-21
forum: Programming Talk
---

### Post by krisfrajer on 2009-06-21
Hi all
I need some help trying to understand the manipulation of arguments for a c++ program. From my tests, I have figured out that my program is not the problem but it looks like the current shell is discarding arguments...

Let me explain my problem in an example.
What I am trying to do is to pass a filename as argument to my program.
I execute the following line 
./bin/APIanalyzer APIanalyzer.vmemac  11 22
However when I read the argument list in my c++ code I get

total argumnets 3
argv[3] is 22
argv[2] is 11
argv[1] is./bin/APIanalyzer

As you notice, the APIanalyzer.vmemac argument was discarded. Remark:APIanalyzer.vmemac is a file that exists in my current directory!!!

I did the same test by inputting a filename that does NOT exist in my current directory:
./bin/APIanalyzer APIanalyzer.v  11 22
Then when I read the list of arguments I get:

argv[4] is 22
argv[3] is 11
argv[2] is APIanalyzer.v
argv[1] is./bin/APIanalyzer

Any suggestions what could be causing this problem? From my point of view, it looks like the executing shell discards any filename parameters if that filename exists. 
I appreciate your comments...

Cheers,

---

### Post by Bachstelze on 2009-06-21
Moved to Programming Talk.

---

### Post by Zugzwang on 2009-06-21
First of all: The name of your executable should be in argv[0] and not in argv[1]. Please verify this first. You seem to be mixing some arguments. Apart from that, there's something wrong with the spacing between "argv[i] is" and the following text. Could you please post the code in which you generate this stuff and make sure that "argv" and "argc" are both declared to be "const" in your program?

---

### Post by MadCow108 on 2009-06-21
does this produce the same problem?
```

#include <iostream>
int main (int argc, char *argv[])
{
	for (int i=0; i<argc; i++)
		std::cout <<"arg "<<i <<": "<< argv[i] << std::endl;
	return 0;
}

```
if yes there's something wrong with your shell (pretty unlikely)
if not then there is something wrong with your code

---

### Post by krisfrajer on 2009-06-21
Thank you for your reply...
First of all, the name of the executable appears in argv[1] instead of argv[0] is because the way I am dealing with the counter. I am sorry for causing this confusion.
I was trying to isolate the problem to post the code in the forum and I realized that the program work fine. I am using ROOT software, a data analysis package, and it happens that there is an object TApplication that is "dealing with my argc.argv" parameters before I use it in my function and it is this object that is removing my filename from my  list of arguments...

In other words, I have found the reason of my problem. I though the problem was related to my current linux shell. A naive assumption.. since I am not a shell expert.
Thanks for the reply and I will post a solution to this problem as soon as a figure it out...

Cheers,

---

### Post by MadCow108 on 2009-06-21
maybe I can help if you post your code
I have a little bit of experience with ROOT

---

### Post by krisfrajer on 2009-06-21
This was my whole problem:

int main(int argc, char **argv){

  TApplication theApp("APIanalyzer", &argc, argv);
  APIanalyzer mainWindow(gClient->GetRoot(),600,500,argc,argv);
  theApp.Run();
  return 0;
}

When I created the object theApp, the constructor was removing my filename. This is because, as far as I understand,  the object removes the "options" from my argument list and palce them in a new member variable. I find out that I can retrieve the original argument list using
theApp.Argc()
theApp.Argv()

so my problem was solved by doing this change to my code:
int main(int argc, char **argv){

  TApplication theApp("APIanalyzer", &argc, argv);
  APIanalyzer mainWindow(gClient->GetRoot(),600,500,theApp.Argc(),theApp.Argv());
  theApp.Run();
  return 0;
}

Cheers,

---

