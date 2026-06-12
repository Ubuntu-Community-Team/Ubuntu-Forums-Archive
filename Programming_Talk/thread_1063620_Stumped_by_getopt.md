---
title: "Stumped by getopt"
date: 2009-02-08
forum: Programming Talk
---

### Post by Xavieran on 2009-02-08
I'm trying to write a simple range calculating program in C++, 
however, I can't seem to get it to parse the arguments.
I have used the info and example from the GNU Getopt page, but it seems as if it can't find the options I put in.

Thanks


```
/*Range.
Echo a list of numbers up to n */

#include <iostream>
#include <unistd.h>
#include <stdlib.h>
#include <typeinfo>

using namespace std;

  

int main(int argc, char ** argv){
    
    int start = 0;
    int interval = 1;
    int end = 10;
    int c;
    
    cout<<"Just before loop\n";
    //Start getting the arguments
    while ((c = getopt(argc, argv, "e:s::i::") != -1)){
        cout<<"Looping\n";
        cout << c;
        switch(c){
            case 'e':
            cout << "END ARG";
            cout << optarg;
            end = int(optarg);
            break;
            case 's':
            cout << "STARG ARG";
            start = int(optarg);
            break;
            cout << "INT ARG";
            case 'i':
            interval = int(optarg);
            break;
        }
    }
    cout << "e" << end << "\n" << "s" << start << "\n" << "i" << interval << "\n";
    //Print out the range.
    for ( int i = start; i < end ; i += interval ){
        cout << i;
        cout << ' ';
    }
        
    cout << '\n' ;
    
    return 1;
}

```

---

### Post by Darkhack on 2009-02-08
I've never used just the shorthand version.  I use the full version so that I can also include long arguments.  Here is the documentation for how to use it, plus an example.

[http://linux.die.net/man/3/getopt_long](http://linux.die.net/man/3/getopt_long)

```

#include <stdlib.h>
#include <stdio.h>
#include <getopt.h>

int main(int argc, char *argv[])
{
    int next_option;
    const char *short_options = "ab:";
    const struct option long_options[] =
    {
        { "action_a", 0, NULL, 'a' },
        { "action_b", 1, NULL, 'b' },
        { NULL, 0, NULL, 0  }
    };
	
    do
    {
        next_option = getopt_long(argc, argv,
                    short_options, long_options, NULL);
        switch(next_option)
        {
            case 'a': do_action_a(); break;
            case 'b': do_action_b(optarg); break;
            case '?': perror("Invalid argument\n"); break;
            case  -1: break;
            default: abort();
        }
    } while (next_option != -1);
    return 0;
}

```

---

### Post by Xavieran on 2009-02-08
Thanks, I'll check that out then :)

---

### Post by geirha on 2009-02-08
In the while loop, the parenthesis are wrong. Instead of setting c to the return value of getopt and then comparing c with -1, you are setting c to the comparison of the return value of getopt and -1 ...

Also, you can't do "int(optarg)". Use a stringstream to convert the cstring to an int.

---

