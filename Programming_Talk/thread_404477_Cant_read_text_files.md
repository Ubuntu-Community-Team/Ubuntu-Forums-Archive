---
title: "Cant read text files?"
date: 2007-04-08
forum: Programming Talk
---

### Post by FlyingIsFun1217 on 2007-04-08
Hey!

I have a very simple program, nothing much:

```
#include <iostream>
#include <stdio.h>
#include <fstream>
#include <sstream>

using namespace std;

string InfoCollectDataHolder;

class ParseText
{
    public:
        ParseText();
        ~ParseText();
        void Parse();
    protected:
};

ParseText::ParseText()
{

}

ParseText::~ParseText()
{

}

void ParseText::Parse()
{
    ifstream FileToParse("InfoCollect.txt");

    if (FileToParse)
    {
        ostringstream oss;

        oss << FileToParse.rdbuf();

        InfoCollectDataHolder = oss.str();
    }

    else
    {
        InfoCollectDataHolder = "Sorry, couldn't open file...";
    }

    cout<<InfoCollectDataHolder;
}

int main()
{
    ParseText ParseExample;
    ParseExample.Parse();
    cin.get();
}

```

And of course right next to it, I have the text file it wants. But it just gives me the error, showing it can't open the file...

Any clue on this one?

Thanks!
FlyingIsFun1217

---

### Post by FlyingIsFun1217 on 2007-04-08
Anybody?

Thanks again!
FlyingIsFun1217

---

### Post by yabbadabbadont on 2007-04-08
Remove: ```
#include <stdio.h>
```
and it works fine.

---

### Post by FlyingIsFun1217 on 2007-04-08
is stdio.h a windows only type header?

Thanks, will do!
FlyingIsFun1217
----------EDIT----------

Hmm... still doesn't work... :/

FlyingIsFun1217

---

### Post by duff on 2007-04-08
> **FlyingIsFun1217 said:**
> is stdio.h a windows only type header?

Thanks, will do!
FlyingIsFun1217
----------EDIT----------

Hmm... still doesn't work... :/

FlyingIsFun1217

stdio.h is for C I/O, so you don't need it.  And check your file names and path again, this program works just fine for me.

---

### Post by russell.h on 2007-04-08
I know this sounds stupid, but you're sure the names are exactly the same? I spent like 5 hours discovering that one once.

---

### Post by FlyingIsFun1217 on 2007-04-09
Me too. That taught me! Now I just copy the filename straight to the file :)
I would think that the paths are correct. Its right next to it...
I'll try just restarting C::B and see if it just didn't need restarted. That seems to happen from time to time... :/

FlyingIsFun1217

---

### Post by FlyingIsFun1217 on 2007-04-09
Ok, I don't know what's going on. It still doesn't work!
Is the fault most likely in the IDE? C::B has screwed around before with my stuff.

FlyingIsFun1217

---

### Post by yabbadabbadont on 2007-04-09
I just copy and pasted it into a text file and used g++ to compile it.  I copied the source code into the data file too, then ran the a.out that g++ produced.  The code was echoed to the screen as it should have been.  Try doing it that way and see if it works.  If so, then it must be your IDE that is messsing things up.  If not, you have bigger problems...

---

### Post by WW on 2007-04-10
I can confirm what yabbadabbadont said.  With or without stdio.h, the program compiles and runs fine for me.  I also opened it up in Code::Blocks (version svn 3816--the April 6 build), and it also compiles and runs fine when I hit F9 ("Build and Run").

I am new to Code::Blocks, so I don't know all its options. Perhaps you are running it in a way that makes it execute the program in a different directory?  Take a look in the "Messages" area.  What is the command that it is using to run the program?

---

### Post by FlyingIsFun1217 on 2007-04-10
> Executing: xterm -T 'Text Parser' -e'LD_LIBRARY_PATH=.:$LD_LIBRARY_PATH /usr/bin/cb_console_runner "/home/myusername/Code::Blocks/Text Parser/bin/Release/Text Parser" ' (in /home/myusername/Code::Blocks/Text Parser/.)

:(
I think I might just switch to Anjuta. See if that doesn't help...

FlyingIsFun1217

---

### Post by WW on 2007-04-10
If I am interpreting the command correctly, it is running your program in either the directory /home/myusername/Code::Blocks/Text Parser/ or /home/myusername/Code::Blocks/Text Parser/bin/Release/.  One way to rule out the possibility of not running the program in the same directory as the data file is to give the full path to the data file.  That is, change the declaration of FileToParse to
```

        ifstream FileToParse("/home/myusername/.../InfoCollect.txt");

```
(Change the file name to the correct full path.)

By the way, if you decide to stick with Code::Blocks, you can also try to get help in the IRC channel #codeblocks (but it can be pretty quiet there).

---

### Post by FlyingIsFun1217 on 2007-04-11
> **WW said:**
> If I am interpreting the command correctly, it is running your program in either the directory /home/myusername/Code::Blocks/Text Parser/ or /home/myusername/Code::Blocks/Text Parser/bin/Release/.  One way to rule out the possibility of not running the program in the same directory as the data file is to give the full path to the data file.  That is, change the declaration of FileToParse to
```

        ifstream FileToParse("/home/myusername/.../InfoCollect.txt");

```
(Change the file name to the correct full path.)

By the way, if you decide to stick with Code::Blocks, you can also try to get help in the IRC channel #codeblocks (but it can be pretty quiet there).

Yep, the setup is such that both the program and the text file are in the project/bin/release setup.
The only reason I don't want to staticly link to that location though is because I need it to eventually be able to read the file next to it (it will be part of a VERY small game engine), so it needs to be dynamic.

Thanks again for the help! Ill try the absolute path to see if it doesn't work that way :)
FlyingIsFun1217

---

