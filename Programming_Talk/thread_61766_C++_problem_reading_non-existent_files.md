---
title: "C++: problem reading non-existent files"
date: 2005-09-02
forum: Programming Talk
---

### Post by omair.majid on 2005-09-02
I recently wrote this program in C++.

```

#include <iostream>
#include <fstream>
// add namespace std to the file
using namespace std;

int main () {
  // program name
  cout << "Error Catching Program. Starting..." << endl;
  try {
    char buffer[250] = "";		// buffer for input
    ifstream myfile("test.txt");  	// open file
    while (!myfile.eof()) {  		// if not the end of file
      myfile.getline(buffer, 100);  	// read a single line of text into buffer
      cout << buffer << endl;       	// output buffer
    }
    myfile.close();			// close file
  }
  catch (...) {				// catch error
    cout << "\nThere was an error reading the file!" << endl;
    return 1;				// abnormal termination
  }
  return 0;				// exit normally
}

```

There are no errors compiling or running it with the test.txt file in the same directory as the binary file. However if the "test.txt" file is not there, then the program enters an infiinte loop. Can anybody explain why?

Thanx

---

### Post by LordHunter317 on 2005-09-02
Yeah, it enters a infinite loop because myfile.eof() will never evaluate to true.  An ifstream that fails to open it's file will only have it's badbit set.  Any I/O operations will fail immediately, but because they do so, eof will never be set.

You need to enable iostream exceptions by the exceptions method (IIRC) in order for your code to work.

---

### Post by omair.majid on 2005-09-02
Thanx for the help. I had no idea I had to set the exceptions.

I modified it to 

```
    ifstream myfile;
    myfile.exceptions(ifstream::eofbit | ifstream::badbit | ifstream::failbit | ifstream::goodbit); 
    myfile.open("test.txt");  		// open file

```
And now it works like a charm  :) 

Thanks!!!

---

### Post by intel17 on 2005-09-03
May I Ask at the Sound of sound of Being Nosey and Stupid, but what dose that Code do?
I am In the Middle of Lerning C++

---

### Post by LordHunter317 on 2005-09-03
What part?

---

### Post by intel17 on 2005-09-04
The whole script.
Thanks again

---

### Post by LordHunter317 on 2005-09-04
Well, you don't write C++ scripts, but programs.  I'm in a nice mode, so I'll annotate it.

I'm not going to surrond it in quotes, but everyone knows where the attributions go to:```
#include <iostream>
#include <fstream>
```This includes the two header files iostream and fstream.  These two files contain the declerations necessary to do I/O to the console and to do I/O to files, using the standard C++ mechanisms.

```
// add namespace std to the file
using namespace std;
```This allows you to use any declerations in the std namespace without having to add the namespace prefix ('std::').  In C++, everything belongs to a namespace.  Items defined without a namespace automatically go into a global namespace ('::').  Namespaces allow you to have two items with the same name, as long as they are in different namespaces:```
namespace ns1 {
    void foo() {
        // Body
    }
}
namespace ns2 {
    void foo() {
        // Different Body
    }
}
```Without namespaces, you couldn't do this.  I should point out that the above in the original code is bad form, and one generally shouldn't have a using directive at anything above function-scope, and you should generally only import the items you're going to use.  So, that should have gone in main(), not where it was.  And it should have really been:```
using std::cout;
using std::endl;
using std::ifstream;
```

Moving on:
```
int main () {
```This starts the definition of main(), which is where the execution of a C++ program begins.

```
 cout << "Error Catching Program. Starting..." << endl;
```std::cout is the stream that you write to to display information on the console (C STDOUT).   '<<' is the operator to write something to the stream, and "endl" is the stream maniuplator to move to the next stream and flush the output, so it is displayed immediately.

```
try {
```This begins an exception try-block, where if an exception occurs, control will be transferred to the approrpiate catch section below, if necessary.

Anyway, I need to stop now, as I have to leave, more later.

---

### Post by thumper on 2005-09-04
[QUOTE=LordHunter317]I should point out that the above in the original code is bad form, and one generally shouldn't have a using directive at anything above function-scope, and you should generally only import the items you're going to use.  So, that should have gone in main(), not where it was.  And it should have really been:```
using std::cout;
using std::endl;
using std::ifstream;
```
[/QUOTE]
There is a big caveat with that comment, and that depends on who you are writing the code for and the general intention of the code.

If you are writing a test program for yourself, like this one, or something small and stand alone, then I don't see anything wrong with a
```
using namespace std;
```
In general there is nothing *wrong* with a using namespace xxx in a souce file, however **never** put a using declaration in a header file.  That is really considered bad form.

Also, the following test condition
```
    ifstream myfile("test.txt");  	// open file
    while (!myfile.eof()) {  		// if not the end of file
      // snip
    }
```
could be
```
    ifstream myfile("test.txt");  	// open file
    while (myfile) { // do while the stream is good
      // snip
    }
```
As the operator bool (or whichever it is) conversion operator checks eof and bad bits.

Also I tend to use the string getline rather than the built in stream one.
```
std::string line;
std::ifstream fin("somefile.txt");
while (fin) {
   // reads a whole line into the string variable.
   std::getline(fin, line);
}
```
You more often want to deal with text files a line at a time rather than a *block* which is what you get with the stream getline.

---

### Post by LordHunter317 on 2005-09-04
> **thumper]There is a big caveat with that comment, and that depends on who you are writing the code for and the general intention of the code.[/quote]Any code that's going to be published shouldn't do it, as it's bad form.

Just like accessors should be written to JavaBeans conventions in Java.  It's not illegal, but it's not something you should disobey, either.

> If you are writing a test program for yourself, like this one, or something small and stand alone,Which are exceptions rather than rules.

> In general there is nothing *wrong* with a using namespace xxx in a souce file,Yes it is, because it makes it really easy to confuse what's imported.  Consider this:```
using namespace std said:**
> ```
    ifstream myfile("test.txt");  	// open file
    while (myfile) { // do while the stream is good
      // snip
    }
```This is also can be bad form, depending on the contents of the loop.  Generally, you want the I/O operation to be the conditional part of the loop, whenever possible.   This ensures that when the stream reaches an exceptional state, that no operation on the input will be performed.  Constructs in such a form will never do a bad thing, whereas doing the I/O in the loop-body *might* do a bad thing without additional error checking.  As such, it's preferable to write I/O in the former method, not the latter, whenever possible.

[Chapter 15 of the C++ FAQ Lite](http://www.parashift.com/c++-faq-lite/input-output.html) covers this in more details.

> As the operator bool (or whichever it is) conversion operator checks eof and bad bits.operator void*()

> Also I tend to use the string getline rather than the built in stream one.
```
std::string line;
std::ifstream fin("somefile.txt");
while (fin) {
   // reads a whole line into the string variable.
   std::getline(fin, line);
}
```This is inarguably bad form and should be:```
std::string line
std::ifstream file("example.txt")
while(std::getline(fin, line)) {
  // Operations
}
```You are correct however, in that this is generally the preferred method for  line-based I/O, as you don't have to handle resizing the buffer.

[edit]More annotations later, I have to run out again :(

---

### Post by LordHunter317 on 2005-09-04
Anyway, continuing where I left off,
```
char buffer[250] = "";		// buffer for input
```This declares an array of characters for storing the data read in from the file.  Though, one should use a std::string in the method thumper and I suggested instead.

```
ifstream myfile("test.txt");  	// open file
```This creates an ifstream object, which handles input (and only input) on a file.  It also automatically opens the file "test.txt" in the current directory.

```
 myfile.exceptions(ifstream::eofbit | ifstream::badbit | ifstream::failbit | ifstream::goodbit); 
```Normally, when an error occurs on an I/O stream, a flag is set that can be check.  This causes an exception to be thrown in addition to setting the flag.

```
while (!myfile.eof()) {  		// if not the end of file
      myfile.getline(buffer, 100);  	// read a single line of text into buffer
      cout << buffer << endl;       	// output buffer
    }
```This loop runs until the end of the file is reached.  It reads up to the next newline ('\n') or 100 characters, whichever comes first, writes it to standard output, and continues.  This loop should be written in the method I suggested to catch all errors, and to avoid writing an extra empty line at the end.

```
myfile.close();			// close file
```This closes the file that was opened.

```
 catch (...) {				// catch error
    cout << "\nThere was an error reading the file!" << endl;
    return 1;				// abnormal termination
  }
```This exception handler responds to any exception.  It outputs an error message and terminates the program with an abnormal program code.

Reader question, how much input will the program show?

---

