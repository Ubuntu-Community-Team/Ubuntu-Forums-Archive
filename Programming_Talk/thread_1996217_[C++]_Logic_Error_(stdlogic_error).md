---
title: "[C++] Logic Error (std::logic_error)"
date: 2012-06-04
forum: Programming Talk
---

### Post by dodle on 2012-06-04
My program compiles fine but a [logic error]("http://en.cppreference.com/w/cpp/error/logic_error") is thrown if I invoke it without any arguments. Otherwise it works fine.

Code:
[php]#include <iostream>
#include <fstream>
#include <string>
using namespace std;

#include <cstdlib>

void ShowUsage(char* me)
{
  cout << "\n\tUsage:\t" << (string)me << " <infile> <outfile>\n\n";
}

int main(int argc, char** argv)
{
  char me[] = "blah";
  
  if (argc > 3)
  {
    cerr << "\nToo many arguments\n";
    ShowUsage(me);
    return 1;
  }
  
  if ((string)argv[1] == "--help" or (string)argv[1] == "-h")
  {
    ShowUsage(me);
    return 0;
  }
  
  if (argc < 3)
  {
    cerr << "\nNot enough arguments\n";
    ShowUsage(me);
    return 1;
  }
  
  return 0;
}[/php]

Output:
```
$ ./test
terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid
Aborted
```

I can't seem to see where the problem is.


**----- SOLVED -----**

Oh! Caught it. It's this line:
[php]if ((string)argv[1] == "--help" or (string)argv[1] == "-h")[/php]

There is no [color=blue]argv[1][/color].


**----- EDIT -----**

New code:
[php]#include <iostream>
#include <fstream>
#include <string>
using namespace std;

#include <cstdlib>

void ShowUsage(char* me)
{
  cout << "\n\tUsage:\t" << (string)me << " <infile> <outfile>\n\n";
}

int main(int argc, char** argv)
{
  char me[] = "blah";
  
  if (argc > 3)
  {
    cerr << "\nToo many arguments\n";
    ShowUsage(me);
    return 1;
  }
  
  if (argc < 3)
  {
    if (argc == 2 && ((string)argv[1] == "--help" or (string)argv[1] == "-h"))
    {
      ShowUsage(me);
      return 0;
    }
    else
    {
      cerr << "\nNot enough arguments\n";
      ShowUsage(me);
      return 1;
    }
  }
  
  return 0;
}[/php]

---

### Post by the_unforgiven on 2012-06-04
> **dodle said:**
> My program compiles fine but a [logic error]("http://en.cppreference.com/w/cpp/error/logic_error") is thrown if I invoke it without any arguments. Otherwise it works fine.

Code:
[php]#include <iostream>
#include <fstream>
#include <string>
using namespace std;

#include <cstdlib>

void ShowUsage(char* me)
{
  cout << "\n\tUsage:\t" << (string)me << " <infile> <outfile>\n\n";
}

int main(int argc, char** argv)
{
  char me[] = "blah";
  
  if (argc > 3)
  {
    cerr << "\nToo many arguments\n";
    ShowUsage(me);
    return 1;
  }
  
  if ((string)argv[1] == "--help" or (string)argv[1] == "-h")
  {
    ShowUsage(me);
    return 0;
  }
  
  if (argc < 3)
  {
    cerr << "\nNot enough arguments\n";
    ShowUsage(me);
    return 1;
  }
  
  return 0;
}[/php]

Output:
```
$ ./test
terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid
Aborted
```

I can't seem to see where the problem is.


**----- SOLVED -----**

Oh! Caught it. It's this line:
[php]if ((string)argv[1] == "--help" or (string)argv[1] == "-h")[/php]

There is no [color=blue]argv[1][/color].

More like, argv[1] is NULL at that point and string constructor fails when passed a NULL. :)

---

