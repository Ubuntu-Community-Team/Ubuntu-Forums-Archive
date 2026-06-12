---
title: "C++ Create File ios::in ios::out"
date: 2009-11-15
forum: Programming Talk
---

### Post by Call My Function on 2009-11-15
I'm having an odd problem. According to my textbook, my code should work, but it doesn't seem to be.

I'm working on a larger project, but in order to find the solution to this problem, I've written this little program:
[php]#include <iostream>
#include <fstream>
using namespace std;

int main()
{
   fstream someFile;
   someFile.open("testBin.dat", ios::out | ios::in | ios::binary);

   if (someFile.fail())
   {
      cout << "Failed to create file!\n";
   }
   
   someFile.close();

   return 0;
}[/php]This code works if I only use ios::out, but not if I use both ios::out AND ios::in. If it fails, no file appears in the directory.

Can anyone explain what's going on?

---

### Post by phrostbyte on 2009-11-15
Try removing ios::binary

---

### Post by Call My Function on 2009-11-15
> **phrostbyte said:**
> Try removing ios::binary
Still fails. I need the file to be in binary, anyway.

---

### Post by phrostbyte on 2009-11-15
AFIAK ios::binary doesn't do anything on POSIX systems. I am not sure why this is not working though. You might want to try to replace ios:: with fstream::

If that doesn't work, passing one param (the filename) to the open method will automatically open it read/write.

---

### Post by Call My Function on 2009-11-15
> **phrostbyte said:**
> AFIAK ios::binary doesn't do anything on POSIX systems. I am not sure why this is not working though. You might want to try to replace ios:: with fstream::
I'm still a newbie (to both C++ and Ubuntu/Linux), so I have no idea what POSIX is. I did get the program to write to a file in binary (by opening, writing, closing, opening, reading, closing) and it seems to work fine.

Also, is this what you mean by using fstream::?
[php]someFile.open("testBin.dat", fstream::out | fstream::in);[/php]I tried that, and it compiled but still doesn't work.

---

### Post by phrostbyte on 2009-11-15
POSIX (Portable Operating System Interface) is a OS standard that Linux (mostly/completely) follows. Also other OS like Mac OS X and many other OS follow this standard. So on these OS (AFIAK) ios::binary is meaningless, because there is no distinction between binary and ASCII (they are both 0's and 1's) in these OSes.

It's so strange but it's a bit of a Deja Vu problem because I remember having to deal with a very similar problem, but I don't remember the proper solution. :confused:

Did you try passing only the file name? eg: file.open("foo.bat"); ?

---

### Post by Call My Function on 2009-11-15
Tried it, didn't work either. Could it be something besides the program, like the compiler? I'm using gcc.

---

### Post by phrostbyte on 2009-11-15
Try to compile/run this:

```

#include <iostream>
#include <fstream>
#include <string>
using namespace std;

int main()
{
	string foo;
   fstream someFile;
   someFile.open("testBin.dat");

   if (someFile.fail())
   {
      cout << "Failed to create file!\n";
   }
   
   someFile << "Cheezburgers!" << endl;
   
   someFile.seekg(ios::beg);
   
   someFile >> foo;
   
   cout << "I like " << foo << endl;
   
   someFile.close();

   return 0;
}  

```

---

### Post by Call My Function on 2009-11-15
It worked! (Text and file appeared, and file looks alright.) But I have no idea why. Does it require the string header? LoL

EDIT: Or because I'm not writing anything to it?

---

### Post by Call My Function on 2009-11-15
The plot thickens. I disabled some of your code, and it stopped working:
[php]#include <iostream>
#include <fstream>
#include <string>
using namespace std;

int main()
{
    string foo;
   fstream someFile;
   someFile.open("testBin.dat");

   if (someFile.fail())
   {
      cout << "Failed to create file!\n";
   }
   
   someFile << "Cheezburgers!" << endl;
/*   
   someFile.seekg(ios::beg);
   
   someFile >> foo;
   
   cout << "I like " << foo << endl;
*/   
   someFile.close();

   return 0;
}[/php]Could it be because I'm not *reading* anything from the file?

---

### Post by Call My Function on 2009-11-15
I was trying to narrow down the culprit by "commenting out" the sections of code until it worked again, but when I finally removed them all the program still didn't work. I copied and pasted your entire code again, into a new cpp file, and it didn't work.

---

### Post by Call My Function on 2009-11-16
bump

---

### Post by Zugzwang on 2009-11-16
I guess the problem is that you either need to specify "ios::trunc" or "ios::app" in the opening mode, so the runtime library knows what to do in the case that the file already exists.

For example, the following code works here:
[PHP]
#include <iostream>
#include <fstream>
#include <string>
using namespace std;

#define SHOW_WHERE cout << "Line: " << __LINE__ << "\n";

int main()
{
    try {
        string foo;
        fstream someFile;
  
        SHOW_WHERE
        someFile.exceptions ( ifstream::failbit | ifstream::badbit);
        SHOW_WHERE
        someFile.open("/tmp/testBin.dat", ios::out | ios::in | ios::app);
        SHOW_WHERE
        someFile << "Cheezburgers!" << endl;
        SHOW_WHERE       
        someFile.seekg(ios::beg);
        SHOW_WHERE       
        someFile >> foo;
        SHOW_WHERE       
        cout << "I like " << foo << endl;
        SHOW_WHERE
        someFile.close();
        SHOW_WHERE
    } catch (ifstream::failure e) {
        cout << "Exception opening/reading file: " << e.what() << "\n";
    }


   return 0;
}  
[/PHP]

But without the "ios::app", it doesn't work if the file does not already exist.

---

### Post by dwhitney67 on 2009-11-16
Unless otherwise specified, the default mode for opening an fstream is ios::in | ios::out.

If the file *does not exist*, after calling open() (or the fstream constructor), fail() will evaluate to true.  The reason is that ios::in portion fails because the file does not exist.

If you want to use a file-stream that can be used as read/write, then ensure the file exists.  For example:
```

...

// create file
fstream someFile("./testBin.dat", ios::out);
someFile.close();

// re-open file for read/write
someFile.open("./testBin.dat", ios::in | ios::out);

...

```
Anyhow, I hope my simple explanation helps.

---

### Post by Call My Function on 2009-11-16
@Zugzwang: What you said worked (both your program and when I edited mine). However, I read that ios::trunc is the default setting for ios::out -- that I shouldn't need to specify it. Is that not true, or am I misunderstanding something?

@dwhitney67: So you're saying that if the file doesn't exist, ios::in will ALWAYS fail, even if ios::out is used with it (which should create the file if it doesn't exist)? The file *must* exist already to use ios::in at all?

I'm going to try Zug's method on my main program and see if it works there, too.

---

### Post by Call My Function on 2009-11-16
@dwhitney67: I tried your method and it worked. Here's my code:
[php]#include <iostream>
#include <fstream>
#include <string>
using namespace std;

int main()
{
   fstream someFile;
   someFile.open("testBin.dat", ios::out | ios::in);
   if (someFile.fail())
   {
      // No File Exists
      cout << "Whoopsie!\n";
      someFile.clear();                                  // Clear Flag
      someFile.open("testBin.dat", ios::out);            // Create File
      someFile.close();
      someFile.open("testBin.dat", ios::out | ios::in);  // Reopen for editing
   }

   someFile << "Cheeseburgers are wonderful indeed.";

   someFile.close();

   return 0;
}[/php]

---

### Post by dwhitney67 on 2009-11-16
> **Call My Function said:**
> 
@dwhitney67: So you're saying that if the file doesn't exist, ios::in will ALWAYS fail, even if ios::out is used with it (which should create the file if it doesn't exist)? The file *must* exist already to use ios::in at all?

Yes, that is what I was saying.  I found this out thru experimentation.

P.S.  The example program shown at the site below does *not* work 'as advertised':
[http://www.cplusplus.com/reference/iostream/fstream/open/](http://www.cplusplus.com/reference/iostream/fstream/open/)

I was surprised, because Cplusplus.com is a reputable site for the C++ API.

---

### Post by Call My Function on 2009-11-16
I did some testing, and the only flags that will *create* a file if it doesn't exist are these, it seems: ios::app and ios::trunc. Since I need ios::ate for my program (which doesn't seem to create files), I'm using a combo of your methods in my program. So far it seems to be working well.

Thank you for your help. I appreciate it. :)

> **dwhitney67 said:**
> 
P.S.  The example program shown at the site below does *not* work 'as advertised':
[http://www.cplusplus.com/reference/iostream/fstream/open/](http://www.cplusplus.com/reference/iostream/fstream/open/)I copied and pasted it -- it worked for me, LOL. Doesn't work when I take out fstream::app, though.

---

### Post by dwhitney67 on 2009-11-16
> **Call My Function said:**
> 
I copied and pasted it -- it worked for me, LOL. Doesn't work when I take out fstream::app, though.

You're right!  It works under Linux (Ubuntu), but not under Mac OS, which is what I use at work.  Weird.

---

### Post by Call My Function on 2009-11-16
> **dwhitney67 said:**
> It works under Linux (Ubuntu), but not under Mac OS, which is what I use at work.  Weird.Maybe it's an operating system issue, because I didn't have any problem like the one in this thread when I used Windows.

---

