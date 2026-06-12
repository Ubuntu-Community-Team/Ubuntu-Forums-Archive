---
title: "C++ Boost file system compilation problem"
date: 2007-08-26
forum: Programming Talk
---

### Post by fledder on 2007-08-26
hi,

I am new to C++ programming but not new to Ubuntu. I am using Eclipse on Ubuntu 6.10. I want to make use of the Boost C++ libraries, particularly the file system library. I have successfully installed both the general and the specific file system libraries. I can also successfully include them in my program. So far, so good.

Problems arrive however when I want to compile a Boost sample program, as taken directly from the Boost site. Here's the code:

```
//  simple_ls program  -------------------------------------------------------//

//  Copyright Jeff Garland and Beman Dawes, 2002

//  Use, modification, and distribution is subject to the Boost Software
//  License, Version 1.0. (See accompanying file LICENSE_1_0.txt or copy at
//  http://www.boost.org/LICENSE_1_0.txt)

//  See http://www.boost.org/libs/filesystem for documentation.

#include "boost/filesystem/operations.hpp"
#include "boost/filesystem/path.hpp"
#include "boost/progress.hpp"
#include <iostream>

namespace fs = boost::filesystem;

int main( int argc, char* argv[] )
{
  boost::progress_timer t( std::clog );
  fs::path full_path( fs::initial_path<fs::path>() );

  if ( argc > 1 )
    full_path = fs::system_complete( fs::path( argv[1], fs::native ) );
  else
    std::cout << "\nusage:   simple_ls [path]" << std::endl;

  unsigned long file_count = 0;
  unsigned long dir_count = 0;
  unsigned long other_count = 0;
  unsigned long err_count = 0;

  if ( !fs::exists( full_path ) )
  {
    std::cout << "\nNot found: " << full_path.native_file_string() << std::endl;
    return 1;
  }

  if ( fs::is_directory( full_path ) )
  {
    std::cout << "\nIn directory: "
              << full_path.native_directory_string() << "\n\n";
    fs::directory_iterator end_iter;
    for ( fs::directory_iterator dir_itr( full_path );
          dir_itr != end_iter;
          ++dir_itr )
    {
      try
      {
        if ( fs::is_directory( dir_itr->status() ) )
        {
          ++dir_count;
          std::cout << dir_itr->path().leaf() << " [directory]\n";
        }
        else if ( fs::is_regular( dir_itr->status() ) )
        {
          ++file_count;
          std::cout << dir_itr->path().leaf() << "\n";
        }
        else
        {
          ++other_count;
          std::cout << dir_itr->path().leaf() << " [other]\n";
        }

      }
      catch ( const std::exception & ex )
      {
        ++err_count;
        std::cout << dir_itr->path().leaf() << " " << ex.what() << std::endl;
      }
    }
    std::cout << "\n" << file_count << " files\n"
              << dir_count << " directories\n"
              << other_count << " others\n"
              << err_count << " errors\n";
  }
  else // must be a file
  {
    std::cout << "\nFound: " << full_path.native_file_string() << "\n";    
  }
  return 0;
}
```

Trying to compile this in Eclipse gives me the following compilation errors:

```
**** Build of configuration Debug for project ListFiles_Boost ****

make -k all 
Building file: ../main.cpp
Invoking: GCC C++ Compiler
g++ -O0 -g3 -Wall -c -fmessage-length=0 -MMD -MP -MF"main.d" -MT"main.d" -o"main.o" "../main.cpp"
../main.cpp: In function ‘int main(int, char**)’:
../main.cpp:21: error: expected primary-expression before ‘>’ token
../main.cpp:21: error: expected primary-expression before ‘)’ token
../main.cpp:50: error: ‘class boost::filesystem::path’ has no member named ‘status’
../main.cpp:53: error: invalid use of ‘class boost::filesystem::path’
../main.cpp:55: error: ‘is_regular’ is not a member of ‘fs’
../main.cpp:55: error: ‘class boost::filesystem::path’ has no member named ‘status’
../main.cpp:58: error: invalid use of ‘class boost::filesystem::path’
../main.cpp:63: error: invalid use of ‘class boost::filesystem::path’
../main.cpp:70: error: invalid use of ‘class boost::filesystem::path’
make: *** [main.o] Error 1
make: Target `all' not remade because of errors.
Build complete for project ListFiles_Boost
```

I would expect that a code sample from the people documenting the library would work, so it must be me doing something wrong? I have not set any specific project properties in Eclipse, and am not sure if I should? Any other clues why I am getting these errors?

Not very constructive to say, but it does bother me that doing something as simple as looping through a directory is so much trouble in C++. 

Thanks so much in advance,

Ferdy

---

### Post by Mirrorball on 2007-08-26
Which line is the 21st?

---

### Post by fledder on 2007-08-28
Thanks for your interest, this line is the 21st....

```
 fs::path full_path( fs::initial_path<fs::path>() );
```

Ferdy

---

### Post by Soybean on 2007-08-28
Ah... took me a bit of fumbling around to figure out what was going on here.

The latest release of the Boost.Filesystem library is 1.34.0. The version that you (and I) installed from the Ubuntu repositories is 1.33.1. As you can see in the change history ([http://www.boost.org/libs/filesystem/doc/index.htm#Change-history](http://www.boost.org/libs/filesystem/doc/index.htm#Change-history)), some of the functions used in the example are new to version 1.34.0.

So you'll either need to get the latest version (there are instructions on the Boost site... it's going to be trickier than using aptitude or synaptic, but you should be able to handle it), or you'll need to find examples that work with the older version.

---

### Post by fledder on 2007-08-29
Thanks, that makes sense. 

I first tried to upgrade to 1.34 but failed. I followed the exact instructions from the official boost site but at the end of the build step the CLI mentions that not all library functions were built correctly. I tried to compile the 1.34 sample program in Eclipse anyway, but got even more errors this time. 

Since I do not have the skills, patience or time to investigate the build problem for such a simple thing as listing a dir of files in C++, I tried the easy way out: going back to 1.33 using the package manager. I did so, and now found the simple_ls.cpp example file for this specific version.

Unfortunately, I still cannot get it to work. The compilation errors are gone, but now there is a linkage problem:

```
**** Build of configuration Debug for project ListFiles_Boost ****

make -k all 
Building target: ListFiles_Boost
Invoking: GCC C++ Linker
g++  -o"ListFiles_Boost"  ./main.o   -l/usr/lib/libboost_filesystem-gcc-mt-1_33_1.so
/usr/bin/ld: cannot find -l/usr/lib/libboost_filesystem-gcc-mt-1_33_1.so
collect2: ld returned 1 exit status
make: *** [ListFiles_Boost] Error 1
make: Target `all' not remade because of errors.
Build complete for project ListFiles_Boost
```

I've tried numerous combinations of the -l and -L parameters always get an error indicating the library cannot be found:

```
ld: cannot find -l/usr/lib/libboost_filesystem-gcc-mt-1_33_1.so
```

I am a 100% sure that this file exists, so now I'm clueless again. Given my very simple goal of listing a dir of files, this is turning into a nightmare. :(

---

### Post by fledder on 2007-08-29
ummm, consider me a a dumbass. I should have been linking to lib_filesystem. Now it works. In my defense, the Boost documentation mentioned one should link to the full library file name.

In order to give something back to this community, I've written a small article discussing the full process:

[http://www.ferdychristant.com/blog/articles/DOMM-76JN6N](http://www.ferdychristant.com/blog/articles/DOMM-76JN6N)

No blogspam, just trying to help out.

Thanks for the help!

---

