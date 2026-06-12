---
title: "[SOLVED] Installing and using the Boost library for c++"
date: 2008-10-16
forum: Programming Talk
---

### Post by ChrisBookwood on 2008-10-16
Hi,

I'm have just tried to `install` the boost library on my laptop, but already at ./configure state, I got some errors about the regex library not being operated right, though, saying that it wasn't a fatal error. I have no idea how I can get it all installed right, but here how I imagined I would do.

I download the tar.bz2 from the official website
[I]cd /usr/share/
sudo tar -xvjf /Documents/Downloads/boost.tar.bz2
cd /usr/share/boost_1_36_0/
./configure && make
sudo make install[/I]

then throw following in my .bashrc:
[I]PATH=$PATH:/usr/share/boost_1_36_0/bin.v2
export PATH[/I]

And that would be it.
Is that a wrong way of doing it? And as said, I already got an error doing the ./configure command.

---

### Post by matja on 2008-10-16
Hi ChrisBookwood,

If I remember correctly, Boost will make such warnings when a library have optional features that must be enabled explicitly. In the case of the regex library, it can add support for ICU (some kind of unicode support?). Is that mentioned in the error message? If so, and if you need it, you can follow the instructions [here]("http://www.boost.org/doc/libs/1_36_0/libs/regex/doc/html/boost_regex/install.html"). If you don't think you'll need it, you should be able to just ignore it.

> **ChrisBookwood said:**
> 
then throw following in my .bashrc:
[I]PATH=$PATH:/usr/share/boost_1_36_0/bin.v2
export PATH[/I]


I guess you want to make the Boost headers and library files available to the compiler without explicitly giving the paths to them upon compilation? That would be CPLUS_INCLUDE_PATH for C++ headers and LIBRARY_PATH for libraries (at least for gcc). PATH is the paths for executable binaries.

I haven't installed the latest version of Boost myself, so feel free to ignore this if it doesn't make sense. Anyway, good luck!

/Mattias

---

### Post by ChrisBookwood on 2008-10-16
I'm new, so I can't really say i understand the things you mention, i'm sorry.

---

### Post by matja on 2008-10-16
I might have gotten way ahead of myself! First of, what's the reason you're installing Boost? Is it to use it in development of your own C++ projects or is it a prerequisite for some other software you're trying to install? In the latter case, which software?

---

### Post by ChrisBookwood on 2008-10-16
In a project I'm currently working on, I'm getting some data from some files, and without regex, it will be much huger than neccesary with all the explodes and stuff there's needed, to get the needed data and work with it. So it's purely to work on own C++ projects.

---

### Post by dwhitney67 on 2008-10-16
Ubuntu's synaptic provides the means to download the appropriate binaries and header files for your system.

I suggest you "backspace" and use it to get Boost.

**System -> Administration -> Synaptic Package Manager**

---

### Post by ChrisBookwood on 2008-10-16
I have looked for it in Synaptic, but I couldn't find the right files - It looked to me, as if there was only some of the libraries. 
Can you point me in the right direction?

---

### Post by dwhitney67 on 2008-10-16
> **ChrisBookwood said:**
> I have looked for it in Synaptic, but I couldn't find the right files - It looked to me, as if there was only some of the libraries. 
Can you point me in the right direction?
There are some Boost libraries that are not available for Ubuntu (at this time).  You mentioned in your OP that you are interest in the regex library.... now I know for sure that this library is available.

P.S.  I only mentioned the use of synaptic because that is the normal avenue for newbies.  I think that the package you require is boost-build (w/ the universe repo being enabled).

All Ubuntu packages are located here (for 8.04):
[http://packages.ubuntu.com/hardy/allpackages](http://packages.ubuntu.com/hardy/allpackages)

---

### Post by ChrisBookwood on 2008-10-16
Thanks for you reply!
I've just succesfully installed the boost-build package... Now, how do I include the files in my projects? I have tried with <boost/regex> og just simply <regex> (both with an without .hpp) but it doesn't quite work.
Do I need to manually set a path?

---

### Post by matja on 2008-10-16
The boost-build package is actually a build system, i.e. a replacement for make and similar tools. Try the *boost-regex-dev* package instead. It is version 1.34 but I don't think they've made any changes to it since then. After that is installed, you should be able to include it with
```
#include <boost/regex.hpp>
```
and compile the code with
```
g++ -o myapp -lboost_regex myapp.cpp
```
I hope that will work!

---

### Post by ChrisBookwood on 2008-10-16
It works - thank you!

-- just as a pick pointer -> you don't have to write -lboost_regex... It seems to work perfectly fine without the argument.

---

### Post by matja on 2008-10-16
No problem!

As for the -lboost_regex flag, I assume it's needed for some parts of the library, so if you stumble upon an undefined reference error related to a regex function when linking, just put it back there. I haven't used the regex library myself, so I don't know which parts of the interface that requires it.

---

### Post by ChrisBookwood on 2008-10-16
Taken to notice... Thansk.

---

### Post by dwhitney67 on 2008-10-16
> **matja said:**
> The boost-build package is actually a build system, i.e. a replacement for make and similar tools. Try the *boost-regex-dev* package instead. It is version 1.34 but I don't think they've made any changes to it since then.

If all is well, not only does the OP have the Boost regex files, but all of Boost.

If I am wrong, then -1 to Canonical.

> **matja said:**
> 
After that is installed, you should be able to include it with
```
#include <boost/regex.hpp>
```
and compile the code with
```
g++ -o myapp -lboost_regex myapp.cpp
```
I hope that will work!
+1

---

### Post by ChrisBookwood on 2008-10-16
Bugger!
Just as I thought it worked...
When the code actually contain a valid regex, I get a lot of weird errors (like when something `make install` -> kinda unreadable), but when the regex aint valid, I just get a regex error saying it's not valid.

That's what I just noticied ... It might be wrong. I've tried with different regex I know is valid (/.a/).

---

### Post by dwhitney67 on 2008-10-16
> **ChrisBookwood said:**
> Bugger!
Just as I thought it worked...
When the code actually contain a valid regex, I get a lot of weird errors (like when something `make install` -> kinda unreadable), but when the regex aint valid, I just get a regex error saying it's not valid.

That's what I just noticied ... It might be wrong. I've tried with different regex I know is valid (/.a/).
Could you please be more specific?

If your system is configured correctly, you should be able to compile/link the application I have attached.

After you download (to your favorite directory):
```

tar xvf boost_regex.tar
cd regex
g++ regex.cpp -lboost_regex

```

If you want to run the program (which is not important):
```

./a.out http_data.txt

```

---

### Post by ChrisBookwood on 2008-10-16
Aah, it was because I didn't use the arguments -lboost_regex...
Thanks for your example that lead to success:D

---

### Post by ChrisBookwood on 2008-10-16
And yet again - a new problem has occured...

In my main file (c++) I'm including some different files, e.g. *parse.cpp*, where the regex is happening.
When you launch my program, it checks if an argument has been passed, and if it is, it creates an object of the the class 'parse' (from the parse.cpp file). It's also in the parse.cpp the *#include <boost/regex.hpp>* is.

The thing is, if I launch my program, *./a.out*, it works as expected, but if I launch it with an argument, *./a.out test*, it just hangs... It prints nothing to the screen, it just hangs and I can type anything I want, without anything happening. The funny thing is, under both circumstances, the *parse.cpp* is included (read: the *boost/regex.cpp* is included), but it's only if an object of the parse-class is being created, the error occures.

---

### Post by dwhitney67 on 2008-10-16
> **ChrisBookwood said:**
> And yet again - a new problem has occured...

In my main file (c++) I'm including some different files, e.g. *parse.cpp*, where the regex is happening.
When you launch my program, it checks if an argument has been passed, and if it is, it creates an object of the the class 'parse' (from the parse.cpp file). It's also in the parse.cpp the *#include <boost/regex.hpp>* is.

The thing is, if I launch my program, *./a.out*, it works as expected, but if I launch it with an argument, *./a.out test*, it just hangs... It prints nothing to the screen, it just hangs and I can type anything I want, without anything happening. The funny thing is, under both circumstances, the *parse.cpp* is included (read: the *boost/regex.cpp* is included), but it's only if an object of the parse-class is being created, the error occures.

Whoa... too much info.

I need to see the module that defines/implements the main() function.

Typically, one does not "include" a .cpp file.  Can you elaborate more on how you are compiling/linking your application?

---

### Post by ChrisBookwood on 2008-10-16
> I need to see the module that defines/implements the main() function.
I'm not sure of what you mean with that?

I compile the whole with *g++ su*b.cpp -lboost_regex

^^ why doesn't one `indclude` a .cpp file? I have always seen .h files as headers (class/function declarations, for example) and .cpp files for the actual work files (definition of the declared classes and/or function, for example)

---

### Post by dwhitney67 on 2008-10-16
> **ChrisBookwood said:**
> I'm not sure of what you mean with that?

I compile the whole with *g++ su*b.cpp -lboost_regex

^^ why doesn't one `indclude` a .cpp file? I have always seen .h files as headers (class/function declarations, for example) and .cpp files for the actual work files (definition of the declared classes and/or function, for example)

My time "on board" is limited... I need to sleep soon.

What I am asking is what makes a difference between running "a.out" and "a.out somefile".  Is there something in your main() function that interrogates the fact that a command-line argument has been passed?

With respect to the compiling, header files, and by that I mean .h files, are (generally) used to define functions, and in the case of C++, classes.  The implementation is generally included within a .cpp file.

It is NOT common to see in a file, say Foo.cpp, the following:
[PHP]#include "Other.cpp"
...[/PHP]
It would, however be normal to see:
[PHP]#include "Other.h"
...[/PHP]
In the latter example, perhaps see:
```
g++ Main.cpp Other.cpp -o myProg
```
where Other.cpp contains the implementation of the functions (or class) defined in Other.h.

---

### Post by ChrisBookwood on 2008-10-16
Yeah, I have the following in my main file:

```
int main( int argc, char *argv[] ) {
   if( argv[1] ) {
      operate * file = new parse( argc, argv );
      ...
      ...
   } else {
      cout << "Theres no work-file specified, and the application exits." << endl;
   }
```

My idea is, it's easier to compile if you also just include the .cpp files, instead of doing like in your example:P Lazyness -.-

---

### Post by dwhitney67 on 2008-10-16
> **ChrisBookwood said:**
> Yeah, I have the following in my main file:

```
int main( int argc, char *argv[] ) {
   if( argv[1] ) {
      operate * file = new parse( argc, argv );
      ...
      ...
   } else {
      cout << "Theres no work-file specified, and the application exits." << endl;
   }
```

Everything looks fine here; however if your program is hanging, then I will need to see the class definition/implementation for operate and parse  (let me guess... parse is a subclass of operate).

> **ChrisBookwood said:**
> 
My idea is, it's easier to compile if you also just include the .cpp files, instead of doing like in your example:P Lazyness -.-
Break the habit!  It contravenes normal accepted practice.  If you do not like typing long g++ statements, then consider creating a Makefile.

P.S.  In lieu of examining argv[1], I would have examined the value of argc (to see if it is greater than 1).  Perhaps this is merely a personal choice.

---

### Post by ChrisBookwood on 2008-10-16
Here operate:
```

class operate {
    protected:
        char * filename; // the subtitle file
        vector<char *> argm; // vector `array´ of passed arguments
    
        // stream
        fstream file;
        vector<string> lines;

    public:
        void open();
        void save();
        void close();
        void format();
};
```

and here's parse:
```

class parse: public operate {
    public:
        parse( int argc, char * argv[] );
};

```

---

### Post by dribeas on 2008-10-16
> **dwhitney67 said:**
> 
Break the habit!  It contravenes normal accepted practice.  If you do not like typing long g++ statements, then consider creating a Makefile.

+1, plus if you include everything and compile at once you will get longer compile times, higher memory usage during compilation and you will be forced to recompile everything with any and all small changes to your code base. At the end it will backfire on you once your project grows.

---

### Post by dwhitney67 on 2008-10-16
> **ChrisBookwood said:**
> Here operate:
```

class operate {
    protected:
        char * filename; // the subtitle file
        vector<char *> argm; // vector `array´ of passed arguments
    
        // stream
        fstream file;
        vector<string> lines;

    public:
        void open();
        void save();
        void close();
        void format();
};
```

and here's parse:
```

class parse: public operate {
    public:
        parse( int argc, char * argv[] );
};

```

Neither of these classes (especially 'parse') indicate why you are passing argc and argv.

The class 'operate' is missing a constructor (and yes, to be anal, a destructor).

Anyhow, ask yourself what is the purpose of the 'parse' class?  All you have presented is a constructor.  Presumably it initializes the base-class 'operator', but I do not see a constructor in 'operator'.  I also do not see where you are maintaining a ostream object that open(), save(), etc can use for the file (I am being presumptuous here) that you are interested in.

Classes are used to encapsulate data that no other class or function should have direct access to.  These classes, though, should have methods (operators) that can manipulate the data, and these methods should be publicly accessible.

I see a brief attempt in your code, but I believe that it is far from complete.  Since I do not have the requirements for the project you are attempting to complete, I (or others) will await your response.

As for now though, I must retire to count sheep... it is nearing 2am.

---

### Post by ChrisBookwood on 2008-10-16
Well, those are only the header... I have done some reconfiguration of my files and classes, based on your `comments` and here both (now there's only two, yes) files are:

sub.cpp:
```

#include <iostream>

using namespace std;

// include work files
#include "operate.h"

int main( int argc, char * argv[] ) {
    // check if at least one argument, being the filename, was passed
    // and if not, exits the sequence
    if ( argv[1] ) {
        operate file ( argc, argv );
        
        if( file.fvalidation ) { // if the filename was genuine, continue
            file.open();
            file.format();
            file.save();
        }
    } else {
        cout << "There's no work file specified and the application exits..." << endl;
    }
    
    return 0;
}

```And here's operate.h:
```

#include <vector>
#include <string>
#include <fstream>
#include <boost/regex.hpp>

class operate {
    private:
        char *filename; // the subtitle file
        vector<char *> argm; // vector of passed arguments
    
        // stream
        fstream file;
        vector<string> lines;

    public:
        bool fvalidation; // is the filename genuine?
    
        operate( int argc, char *argv[] );
        void open();
        void save();
        void format();
};
    
    operate::operate( int argc, char * argv[] ) {
        // here we are gonna check if it's actually a filename the user entered
        // as the first argument, and throwing the rest in 'argm'
        filename = argv [1]; // declaring the filename
    
        boost::regex fpattern("/./.(srt|sub)/"); // pattern to validate the filename
        
        if( boost::regex_match(filename, fpattern) ) {
            fvalidation = true; // this makes the sequence continue
            
            for( int i = 2; i < argc; i++ ) // i starts at 2 to bypass the two first argv arguments, being the application and subtitle file
                argm.push_back( argv[i] ); // throw all, if any, arguments in argm
        }
    }

    void operate::open() {
        file.open( filename );
        
        string tmp_line; // tmp for the current line before it gets pushed forward to 'lines'
        
        while( !file.eof() ) { // read the whole file, one line by one
            getline (file, tmp_line);
            
            lines.push_back (tmp_line);
        }
    }

    void operate::save() {
        // throw every single line back in the file, one at a time
        for( int i = 0; i < lines.size(); i++ )
            file << lines[i];
        
        // close `file`
        file.close();
    }
    
    void operate::format() {
    
    }

```
The application is still brand new and lots of things are missing, so it's more the `correctness` of things i'm looking for, and not what's missing... Of course, if something is missing to make someother thing right, bring it on.

---

### Post by dwhitney67 on 2008-10-16
I took the liberty to clean up your code, and to also verify that I could get it to compile/link.  To compile the code below, follow this instruction:
```
g++ Main.cpp Operate.cpp -lboost_regex
```

Main.cpp:
[php]
#include "Operate.h"
#include <iostream>


int main(int argc, char** argv)
{
  // check if at least one argument, being the filename, was passed
  // and if not, exits the sequence
  if (argv[1])
  {
    Operate file(argc, argv);
        
    if (file.isFileValid())
    {
      // if the filename was genuine, continue
      file.open();
      file.format();
      file.save();
    }
  }
  else
  {
    std::cout << "There's no work file specified and the application exits..." << std::endl;
  }
    
  return 0;
}
[/php]

Operate.h:
[php]
#ifndef OPERATE_H
#define OPERATE_H

#include <vector>
#include <string>


class Operate
{
  public:
    Operate(int argc, char** argv);

    void open();
    void save();
    void format();
    bool isFileValid() const;

  private:
    std::string              filename;      // the subtitle file
    bool                     fvalidation;   // is the filename genuine?
    std::vector<std::string> argm;          // vector of passed arguments
    std::vector<std::string> lines;         // data read from the file
};

#endif
[/php]

Operate.cpp:
[php]
#include "Operate.h"
#include <boost/regex.hpp>
#include <fstream>


Operate::Operate(int argc, char** argv)
  : filename(argv[1]),
    fvalidation(false)
{
  // here we are gonna check if it's actually a filename the user entered
  // as the first argument, and throwing the rest in 'argm'

  boost::regex fpattern("/./.(srt|sub)/"); // pattern to validate the filename
        
  if (boost::regex_match(filename, fpattern))
  {
    fvalidation = true; // this makes the sequence continue

    // i starts at 2 to bypass the two first argv arguments, being the application
    // and subtitle file
    for (int i = 2; i < argc; ++i)
    {
      argm.push_back(argv[i]);
    }
  }
}

void Operate::open()
{
  std::fstream file(filename.c_str(), std::ios::in);

  if (file)
  {
    std::string tmp;

    while (getline(file, tmp))
    {
      lines.push_back(tmp);
    }

    file.close();
  }
}

void Operate::save()
{
  std::fstream file(filename.c_str(), std::ios::out);

  if (file)
  {
    for (size_t i = 0; i < lines.size(); ++i)
    {
      file << lines[i];
    }
        
    file.close();
  }
}
    
void Operate::format()
{
  // TODO
}

bool Operate::isFileValid() const
{
  return fvalidation;
}
[/php]

A bit of advice...

1.  Avoid (and hence never) declare a "using namespace" in a header file.

2.  Always include local header files, followed by system header files.  Never the other way around.  This assists in ironing out any missing dependencies your local header files may suffer.

3.  Avoid exposing data that is part of a class; provide an accessor to access it.

4.  Do not declare unnecessary variables as class member-data.  If the variable is only going to be used locally within a method, then declare it there.

5.  Whenever possible, consider storing strings as an STL string data type, and not as char pointers.

Finally, I could not test your application thoroughly because I do not have the required input work-file.  If you still have trouble testing on your end, please let me know.

---

### Post by ChrisBookwood on 2008-10-17
I have tried out your example and taken everything you've said to notice. It's great you are willing to help me so much!
There's a few methods you are using, that I'm not familiar with, and some thing you do, that I just can't see the purpose of. Here they are listed:

First, in operate.h, you check if an constant OPERATE_H is defined, and if not, then it gets defined. But why? Whats the purpose of it?

In operate.cpp, you declare the class by doing *Operate::Operate( int argc, char** argv ) : filename( argv[1] ), fvalidation( false )* -Is the latter of it ´just` a definer of filename and fvalidation, and why doesn't you declare the definition in the class declaration instead?


-- Oh, and by the way :: it works great!

---

### Post by dwhitney67 on 2008-10-17
> **ChrisBookwood said:**
> 
First, in operate.h, you check if an constant OPERATE_H is defined, and if not, then it gets defined. But why? Whats the purpose of it?

The OPERATE_H is defined as a measure to prevent the header file from being included twice within a source (or header) file.  It is common practice.  Read more info on this here:  [http://en.wikipedia.org/wiki/Include_guard](http://en.wikipedia.org/wiki/Include_guard)

> **ChrisBookwood said:**
> 
In operate.cpp, you declare the class by doing *Operate::Operate( int argc, char** argv ) : filename( argv[1] ), fvalidation( false )* -Is the latter of it ´just` a definer of filename and fvalidation, and why doesn't you declare the definition in the class declaration instead?

This is the short-hand way of initializing a class' member data.  You should practice it because there are occasions in which it is absolutely required (e.g. a constructor accepts and stores a reference to an object).
[php]
class Foo
{
  public:
    Foo(SomeObject& obj)
    {
      m_obj = obj;   // this will not compile
    }

  private:
    SomeObject& m_obj;
};
[/php]
Instead one must implement:
[php]
class Foo
{
  public:
    Foo(SomeObject& obj)
      : m_obj(obj)
    {
    }

    ...
};
[/php]

Btw, I'm glad the program I provided works for you.

---

### Post by ChrisBookwood on 2008-10-17
```
[COLOR=#007700]class [/COLOR][COLOR=#0000bb]Foo 
[/COLOR][COLOR=#007700]{ 
  public: 
    [/COLOR][COLOR=#0000bb]Foo[/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000bb]SomeObject[/COLOR][COLOR=#007700]& [/COLOR][COLOR=#0000bb]obj[/COLOR][COLOR=#007700]) 
    { 
      [/COLOR][COLOR=#0000bb]m_obj [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#0000bb]obj[/COLOR][COLOR=#007700];   [/COLOR][COLOR=#ff8000]// this will not compile 
    [/COLOR][COLOR=#007700]} 

  private: 
    [/COLOR][COLOR=#0000bb]SomeObject[/COLOR][COLOR=#007700]& [/COLOR][COLOR=#0000bb]m_obj[/COLOR][COLOR=#007700]; 
};  [/COLOR]
```Ahh, that might by why i had so many problems with declaring and defining *fvalidation*, and ended up just declaring it as public, where it was private at first.


EDIT:
Oh, I almost forgot to say thank you for all your help!:)

---

