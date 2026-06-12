---
title: "Program 2"
date: 2014-06-11
forum: Programming Talk
---

### Post by spacerocket on 2014-06-11
Hello,

When trying to compile

```
#include<iostream>
#include<string>
#include<vector>
#include<algorithm>
#include<cmath>
using namespace std;

int main()
{
     cout<< "Please enter a floating-point value: ";
     double n;
     cin>>n;
     cout<< "n ==" <<n
         << "\nn+1 == "<<n+1
         << "\nthree times n == "<<3*n
         << "\ntwice n == "<<n+n
         << "\nn squared == "<<n*n
         << "\nhalf of n == "<<n/2
         << "\nsquare root of n == "<<sqrt(n)
         << `\n`;  // another name for newline ("end of line") in output

}
```


Then I get this error message:

g++ Documents/floating.cpp -o floating
Documents/floating.cpp:14:6: error: stray ‘\302’ in program
          << "\nn+1 == "<<n+1
      ^
Documents/floating.cpp:14:6: error: stray ‘\240’ in program
Documents/floating.cpp:20:10: error: stray ‘`’ in program
          << `\n`;  // another name for newline ("end of line") in output
          ^
Documents/floating.cpp:20:10: error: stray ‘\’ in program
Documents/floating.cpp:20:10: error: stray ‘`’ in program

---

### Post by steeldriver on 2014-06-11
AFAIK **`** (backtick) is NOT a valid substitute for **"** (double quote) to delimit a string constant - it needs to be

```

         << [COLOR=#0000cd]**"**[/COLOR]\n[COLOR=#0000ff]**"**[/COLOR];  // another name for newline ("end of line") in output

```

As well, it looks like you copied the source code in a way that has included some Unicode non-breaking space characters (C2A0 --> octal \302\240)

---

### Post by spacerocket on 2014-06-12
Ok,

Why would there be incorrect code in the book? Does that make any sense? I should remove all \ ?

---

### Post by Vaphell on 2014-06-12
don't touch any \'s, they are ok. It's the wrong quote and funky spaces that are the problem.

is the book a nicely formatted html? If so, you should expect there might be weir characters like non-breaking spaces to make sure the line doesn't break in wrong place (outside of non-breaking spaces you don't really have control over text breaking in html, html engine does what it does). Also i have seen code snippets on the internet that had fancy unicode double quotes because tools that generated the page prettify 'dull' ASCII "s by default. 

that said, backticks ` ` are not used for anything in c/c++ so if you see them, you should assume you need single quotes ' '.

---

### Post by spacerocket on 2014-06-12
Ahh now I get it I deleted the spaces and it worked : ) I didn`t know that spaces are not allowed in C++. About the book, it is written in nicely formatted html, maybe the author expects that I don`t use spaces. Thx anyway.

---

### Post by spacerocket on 2014-06-12
There is also an exercise:

Get this little program to run. Then, modify it to read an int rather than a double. Note that sqrt() is not defined for an int so assign n to a double and take sqrt() of that.

I changed the code, should be something like this?

```
 #include<iostream>
#include<string>
#include<vector>
#include<algorithm>
#include<cmath>
using namespace std;
inline void keep_window_open() {char ch; cin>>ch;}

int main()
{
     cout<< "Please enter a floating-point value:";
     int n;
     n=double
     cin>>n;
     cout<< "n =="<<n
         << "\nn+1 =="<<n+1
         << "\nthree times n=="<<3*n
         << "\ntwice n=="<<n+n
         << "\nn squared=="<<n*n
         << "\nhalf of n=="<<n/2
         << "\nsquare root of n=="<<sqrt(n)
         << "\n";  // another name for newline ("end of line") in output

} 
```

---

### Post by mörgæs on 2014-06-12
Thread closed. Please read #7 here:

[http://ubuntuforums.org/showthread.php?t=2158945](http://ubuntuforums.org/showthread.php?t=2158945)

---

