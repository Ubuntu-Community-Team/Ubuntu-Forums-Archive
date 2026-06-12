---
title: "converting beetween char* strings and integers (c++)"
date: 2009-03-09
forum: Programming Talk
---

### Post by Gediminas2 on 2009-03-09
Hello everyone, it's me again.

I am looking a way to easily convert char* to int; The opposite is not required, but I'd appreciate it too. 

I have tried googling and searching this forum for answers. Google tells me to use atoi() and itoa(), but can't get them to work. They must be some kind of non-standard functions.

```

#include "Unit2.h"
#include <iostream>
using namespace std;

int main(int argc, char *args)
{
   if(!argc){cout << "Cannot run without arguments!\n";return 0}
   if(argc < 2){cout << "Too few arguments! (needed : YY MM DD)\n";return 0}
   int DD, MM, YY;
   //convert strings to int

   //YY = stringToInt(argv[0]);
   //MM = stringToInt(argv[1]);
   //DD = stringToInt(argv[2]);

   Skaiciavimai S;
   S.Skaityti();
   S.SkKord(YY,MM,DD);
   system("./planetGL");

   return 1;
}

```

I'm am working on this project with my friend, and I don't really know what his part of the program does. I just know it needs to get the date from the command line as arguments (int YY, int MM, int DD).

So if I could make the strings into integers the project would be almost complete.

Thanks in advance,
Gedas

---

### Post by dwhitney67 on 2009-03-09
```

#include <cstdlib>
...
int YY= atoi(argv[1]);
int MM = atoi(argv[2]);
int DD = atoi(argv[3]);

```

OR

```

#include <sstream>
...
int YY = 0;
int MM = 0;
int DD = 0;

std::stringstream ss;
for (int i = 1; i < argc; ++i)
{
  ss << argv[i] << ' ';
}

ss >> YY;
ss >> MM;
ss >> DD;

```

There is no function in *nix called itoa().  However, you can write your own, or just use the std::stringstream in reverse (use the << operator) wrt what is shown above.

P.S.  You did not specify if you need to verify that the input for each field must be two-chars wide or not.  For instance, for the month of March, is '3' acceptable, or must the user enter '03'?

EDIT-  WRT the P.S. above, it really doesn't matter if the user enters 2-characters or 1-character.  Just be cautious if the data is more than 3 characters long.  Thus, consider saving the argv[] values to an std::string first, do some basic checks, then convert to an integer, where then you can do other checks.

---

### Post by the_unforgiven on 2009-03-09
You could use the [std::istringstream]("http://www.cplusplus.com/reference/iostream/istringstream/") class to convert the char* into a stringstream.
Then, it was just a matter of using the [operator>>()]("http://www.cplusplus.com/reference/iostream/istream/operator%3E%3E.html").
Check the example in the second link.

EDIT:
dwhitney67 beat me to it.. :p

---

### Post by babyhuey on 2009-03-09
> **Gediminas2 said:**
> Hello everyone, it's me again.

I am looking a way to easily convert char* to int; The opposite is not required, but I'd appreciate it too. 

I have tried googling and searching this forum for answers. Google tells me to use atoi() and itoa(), but can't get them to work. They must be some kind of non-standard functions.

```

#include "Unit2.h"
#include <iostream>
using namespace std;

int main(int argc, char *args)
{
   if(!argc){cout << "Cannot run without arguments!\n";return 0}
   if(argc < 2){cout << "Too few arguments! (needed : YY MM DD)\n";return 0}
   int DD, MM, YY;
   //convert strings to int

   //YY = stringToInt(argv[0]);
   //MM = stringToInt(argv[1]);
   //DD = stringToInt(argv[2]);

   Skaiciavimai S;
   S.Skaityti();
   S.SkKord(YY,MM,DD);
   system("./planetGL");

   return 1;
}

```

I'm am working on this project with my friend, and I don't really know what his part of the program does. I just know it needs to get the date from the command line as arguments (int YY, int MM, int DD).

So if I could make the strings into integers the project would be almost complete.

Thanks in advance,
Gedas

Off topic but...by convention you want to return 1 if there is an error and 0 if everything ran okay. I would also recommend using the " exit(1) " function to end the program with an error instead of "return 1" 

No biggie really just my 2 cents.

---

