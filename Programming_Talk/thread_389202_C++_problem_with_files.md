---
title: "C++ problem with files"
date: 2007-03-20
forum: Programming Talk
---

### Post by tkjacobsen on 2007-03-20
I'm making a small c++ linux program. 
How do I check if a file exists (a configuration file)
How do I detect the home folder of the user running the program
How do I create a folder in $HOME

I need the program to check if the configuretion file exists, and if not, create a folder in $HOME and in that folder create the  configuration file..

---

### Post by khedron on 2007-03-20
Ok, to see if a file exists, try opening it for reading. The opening will fail if there is no file.

To get $HOME, include <cstdlib> and use the getenv function. More details here:
[http://www.acm.uiuc.edu/webmonkeys/book/c_guide/2.13.html#getenv](http://www.acm.uiuc.edu/webmonkeys/book/c_guide/2.13.html#getenv)

Getenv takes a char* (a c-string) as an argument and returns one as well. I haven't used it (yet), you'll have to experiment.

To make a folder, look at this question: [http://c-faq.com/osdep/mkdir.html](http://c-faq.com/osdep/mkdir.html)
It's about C, unfortunately, not C++, but my experience so far has been with C. I'm only now learning C++.

---

### Post by hod139 on 2007-03-20
Check out the [Boost Filesystem Library as well.]("http://www.boost.org/libs/filesystem/doc/index.htm") The Boost solution will be more complicated, but portable.

---

### Post by tkjacobsen on 2007-03-20
Thanks guys. I will try all options out as soon as possible and write back how it went afterwards.

---

### Post by xtacocorex on 2007-03-20
Here is some simple stuff I've done to find a config file with an environment variable:
```

#include<iostream>
#include<string>
#include<fstream>
#include<stdlib.h>

// config
// ===============================================
// Reads in the configuration parameters for PMARC
void config()
{
    // Variable declarations
    std::string t1, t2, cfignlist, fpath;
    char *path;
    std::ifstream fin;

    // Get the path to the PMARC config file
    path = getenv("PMARCCONFIG");
    // If path doesn't exits, throw out error and exit program
    if (path == NULL)
    {
        std::cout << "ERROR-UNABLE TO FIND ENVIRONMENT VARIABLE: PMARCCONFIG" << std::endl;
        std::exit(1);
    }

    // Set string that holds the path and filename of the config file
    // This resize needs stay
    fpath.resize(strlen(path)+11);
    for (int i=0;i<=strlen(path);i++)
    {
        fpath[i]=path[i];
    }
    fpath += "/pmarc.conf";
    
    // *** FOR TESTING ***
    fpath="pmarc.conf";
    
    // Open the file
    fin.open(fpath.c_str());
    // If it fails, show error and exit
    if (fin.fail() == true)
    {
        std::cout << "ERROR-PMARC CONFIGURATION FILE CANNOT BE OPENED" << std::endl;
        std::exit(1);
    }
    // Otherwise do the work to parse the namelist
    else
    {
        // Get the lines from the input file
        std::getline(fin,t1);
        std::getline(fin,t2);

        // Close the file
        fin.close();
    }
    // Return to calling routine
} // End config


```
Hope this helps some.

---

### Post by g8m on 2007-03-21
If you're configuration file is in ini-like format.
Like:
[header1]
variable1 = value1
variable2 = value2

[header2]
variable3 = value3

You might want to have a look at key-value file parser functions from glib top parse ini-files
[http://developer.gnome.org/doc/API/2.0/glib/glib-Key-value-file-parser.html](http://developer.gnome.org/doc/API/2.0/glib/glib-Key-value-file-parser.html)

---

### Post by RealTonko on 2007-03-24
You may want to delegate those issues to config and make install.
Check [http://sourceware.org/autobook/](http://sourceware.org/autobook/)

---

