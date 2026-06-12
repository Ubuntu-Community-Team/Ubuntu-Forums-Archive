---
title: "Obtain Info From Command Line To A Cpp Var"
date: 2008-03-29
forum: Programming Talk
---

### Post by piotroxp on 2008-03-29
Is there a way to fetch the return information of a terminal call in c++ so you can use the information ?

---

### Post by dwhitney67 on 2008-03-29
That's an interesting question!  I have never had to do something like this.  Below is a "lame" way to do it... perhaps there is another alternative (e.g. redirecting the status of the command to a file, then reading the file).

[PHP]#include <cstdlib>
#include <iostream>

int main( int argc, char **argv )
{
  if ( argc > 1 )
  {
    std::cout << "command line value is: " << atoi( argv[1] ) << std::endl;
  }
  return 0;
}[/PHP]

First compile the program...
```
g++ cmdLineResult.cpp -o cmdLineResult
```

Then test it (note that file foo does not exist)...
```
ls foo || cmdLineResult $?
```

P.S.  I just did a little more testing on the suggestion above.  It will only work if the command returns an error.  Thus this is obviously NOT the ideal solution.  Try redirecting the status of the command to a file, then having your C++ program read the file.

---

### Post by WW on 2008-03-29
> **piotroxp said:**
> Is there a way to fetch the return information of a terminal call in c++ so you can use the information ?

By "a terminal call", do you mean a call to [system()](http://www.cplusplus.com/reference/clibrary/cstdlib/system.html)?  If so, that link explains the return value.

---

### Post by dwhitney67 on 2008-03-29
> **WW said:**
> By "a terminal call", do you mean a call to [system()](http://www.cplusplus.com/reference/clibrary/cstdlib/system.html)?  If so, that link explains the return value.

Right!  I remember this now:

[PHP]#define _XOPEN_SOURCE
#include <cstdlib>
#include <iostream>

int main( int argc, char **argv )
{
  int sysStatus = system( "ls foo >& /dev/null" );

  std::cout << WEXITSTATUS( sysStatus ) << std::endl;

  return 0;
}[/PHP]

---

