---
title: "Trouble linking boost in Qt application"
date: 2011-01-01
forum: Programming Talk
---

### Post by antman8969 on 2011-01-01
Hi all,

I'm using Qt creator to try and port a media player application that I wrote in python to c++ to help teach myself, but I've run into a problem I cannot solve it seems.

I wrote a Song.h file and a SongCreator.cpp file that contains a few functions that don't belong to any class, such as recursively searching through a directory, which I use boost_filesystem to do. 


 ```
#include <boost/filesystem.hpp>
#include <boost/filesystem/path.hpp>
#include <boost/filesystem/operations.hpp>

/** Function for retrieving a list of all files in a top level directory
 * recursively. Used to get a list of all of the songs in a file system.
 */
string* recursiveFileList(string& directory){
        path p(directory);
        string* files = new string[2400];

        int i = 0;
        recursive_directory_iterator end;
        for(recursive_directory_iterator start(p); start != end; ++start){
                string path = start->path().string();
                files[i] = path;
                i++;
        }

        return files;
}
```

It isn't done yet obviously (currently using 2400 as an arbitrary list size) but I've compiled it and ran test code in Eclipse linking the library with the -lboost_filesystem tag.

In Qt creator (qmake I suppose) I can only compile successfully when I DON'T #include <boost/filesystem.hpp>. I get this error if I include it: 


> error: undefined reference to `boost::system::generic_category()'
error: undefined reference to `boost::system::generic_category()'
error: undefined reference to `boost::system::system_category()'

among other 'undefined reference to' errors... This is obviously a problem because I need the recursive_directory_iterator.

I can compile it when I use a desktop build, but the maemo one gives me trouble, does anyone have any experience with this?

---

### Post by MadCow108 on 2011-01-01
this is probably a linking problem of the boost packages in the ubuntu toolchain.
boost-filesystem requires boost-system symbols in its headers (even if you don't use them directly)
The indirect linkage of libboost-system is removed by the ubuntu toolchain (because of --as-needed default I think)

linking with libboost-system explicitly should fix it

see also here:
[http://lists.debian.org/debian-devel/2010/12/msg00058.html](http://lists.debian.org/debian-devel/2010/12/msg00058.html)

---

### Post by antman8969 on 2011-01-01
> **MadCow108 said:**
> this is probably a linking problem of the boost packages in the ubuntu toolchain.
boost-filesystem requires boost-system symbols in its headers (even if you don't use them directly)
The indirect linkage of libboost-system is removed by the ubuntu toolchain (because of --as-needed default I think)

linking with libboost-system explicitly should fix it

see also here:
[http://lists.debian.org/debian-devel/2010/12/msg00058.html](http://lists.debian.org/debian-devel/2010/12/msg00058.html)

reading now. This is also probably of note. This is how I ended up linking the libraries in the .pro file

```
INCLUDEPATH += /home/user/Desktop/boost_1_45_0
```

I had to download the source from the website and link to it that way because when I did  this:

```
LIBS += -L/usr/lib/ -lboost_filesystem
```

it only worked if I was building for desktop, (as opposed to maemo)

So I'm not sure I'm explicitly linking libboost_filesystem any more so than libboost_system. Another disclaimer...ultra noob here

---

### Post by dwhitney67 on 2011-01-01
The following works fine for me, linking only with boost_filesystem.

```

// To build:
//
//      g++ ListDir.cpp -lboost_filesystem
//
//
#include <boost/filesystem.hpp>
#include <string>
#include <vector>
#include <iostream>
#include <iterator>


void
recursiveFileList(const std::string& dir, std::vector<std::string>& fileList)
{
   fileList.clear();

   boost::filesystem::recursive_directory_iterator end;

   for (boost::filesystem::recursive_directory_iterator start(dir); start != end; ++start)
   {
      fileList.push_back(start->path().filename());
   }
}

int main(int argc, char** argv)
{
   if (argc != 2)
   {
      std::cerr << "Usage: " << argv[0] << " <dirpath>" << std::endl;
      return -1;
   }

   std::vector<std::string> fileList;

   recursiveFileList(argv[1], fileList);

   std::copy(fileList.begin(), fileList.end(), std::ostream_iterator<std::string>(std::cout, "\n"));
}

```

---

### Post by MadCow108 on 2011-01-01
> **dwhitney67 said:**
> The following works fine for me, linking only with boost_filesystem.



not with gcc-4.5 which will be default in natty (and has the --as-needed change if no one decides to reverts it):
> 
g++-4.5 test.cpp -lboost_filesystem
/usr/bin/ld: /tmp/cckhTfdy.o: undefined reference to symbol 'boost::system::get_system_category()'
/usr/bin/ld: note: 'boost::system::get_system_category()' is defined in DSO //usr/lib64/libboost_system.so.1.42.0 so try adding it to the linker command line


g++-4.5 file.cpp -lboost_filesystem -lboost_system
or 
g++-4.4 file.cpp -lboost_filesystem
works

so
```

LIBS += -L/usr/lib/ -lboost_filesystem -lboost_system

```
might solve your problem

---

### Post by antman8969 on 2011-01-03
> **MadCow108 said:**
> not with gcc-4.5 which will be default in natty (and has the --as-needed change if no one decides to reverts it):


g++-4.5 file.cpp -lboost_filesystem -lboost_system
or 
g++-4.4 file.cpp -lboost_filesystem
works

so
```

LIBS += -L/usr/lib/ -lboost_filesystem -lboost_system

```
might solve your problem


I can compile from the command line using g++ just fine, but when I try to add the libs in Qt using the LIBS += method under my maemo build then it cannot even find the library. But it compiles fine with the same .pro file when doing it for desktop...

---

