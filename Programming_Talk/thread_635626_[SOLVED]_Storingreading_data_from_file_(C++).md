---
title: "[SOLVED] Storing/reading data from file (C++)"
date: 2007-12-08
forum: Programming Talk
---

### Post by roberto22085 on 2007-12-08
I solved this problem!

---

### Post by iharrold on 2007-12-10
You should leave the problem and then post your solution for future reference and searches.

I.e.

```

#include <fstream> //file streams and operations
#include <iostream> //cin, cout, cerr, etc
#include <cstdlib> // exit(), etc.

void error (const char* p, const char * p2 = "")
{
    std::cerr<<p<< ' '<<p2<<'\n";
    std::exit(1);
}

int main (int argc, char * argv[])
{
    if (argc !=3) 
        error ("wrong number of arguments");
   
    std::ifstream from (argv[1]);  // open input file stream
    if (!from)
        error ("cannot open input file", argv[1]);
   
    std::ofstream to (argv[2]);    // open output file stream
    if(!to)
        error ("cannot open output file", argv[2]);

    char ch;
    while (from.get(ch))
        to.put(ch);      //copy characters
 
     if(!from.eof() || !to)
         error ("something strange happened");
     
    return 0;
}



```

---

