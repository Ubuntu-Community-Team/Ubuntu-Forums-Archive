---
title: "Pointer Query C++"
date: 2010-01-21
forum: Programming Talk
---

### Post by RevengeOfTidus on 2010-01-21
Hey everyone,

My friend and I are making a command line user interface.  We pretty much finished it, however we're having problems with strings and their pointers.  We're trying to ask the user the name of the picture they want to display.  I could just use a char array like in C, however, I'm trying to learn how to do a more C++ approach of doing it by possibly using strings (string class), etc.

The following is the code we're having trouble with:

```

void get_arguments(int num_of_args, **char*** args){
//get user argument
//store user argument at passed pointer.
}

```The variable *num_of_args* will specify how many arguments we want to get from the user (let's just say 1 for simplicity for now).  The variable *args* is the location of where to store the user input after retrieved.  I tried doing:

```

void get_arguments(int num_of_args, string* args){
}

```but the compiler said it didn't like the string pointer.

Also, an example of user input would be something like "lena.jpg" .

Any advice would be helpful.

Thanks,
-RoT

---

### Post by dwhitney67 on 2010-01-21
Here's a less than adequate approach:
```

#include <string>

bool getArgs(const int argc, const char** argv, std::string& jpgFile)
{
   bool gotArgs = false;

   if (argc == 1)
   {
      jpgFile = *argv;
      gotArgs = true;
   }

   return gotArgs;
}

int main(int argc, char** argv)
{
   --argc; ++argv;  // we skip the app name

   std::string jpgFile;

   if (getArgs(argc, argv, jpgFile))
   {
      // got jpgFile...
   }
   else
   {
      // error: missing arg(s)
      return -1;
   }
}

```
If you expect more than one arg on the command line, you should consider using getopt() or getopt_long().  You can read about these in the man-pages:
```

man 3 getopt

```

---

### Post by MadCow108 on 2010-01-22
this is one of the points where you have to use char even in C++ code, because the char (and void) definition of main is standard.
Anything else (even if possible) would be non-standard/non-portable.
but you can easily convert the chars to strings like dwhitney showed.

there are also C++ frameworks which do what getopt does in a more C++ way.
Boost program_options would be an example

---

### Post by nvteighen on 2010-01-22
Hum... Why not do something like this to get rid of using an "argument as return place":

```

#include <string>

std::string getArgs(int argc, char** argv)
{
    std::string Arg("");
    
    if (argc == 1)
    {
        Arg = *argv;
    }   

    return Arg;
}

int main(int argc, char** argv)
{
    --argc; ++argv;  // we skip the app name

    std::string jpgFile = getArgs(argc, argv);
    if (jpgFile != "")
    {
        // Do something...
    }
    else
    {
        // error: missing arg(s)
        return -1;
    }

    return 0;
}

```

---

