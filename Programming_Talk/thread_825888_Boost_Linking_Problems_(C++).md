---
title: "Boost Linking Problems (C++)"
date: 2008-06-11
forum: Programming Talk
---

### Post by Schadenfroh on 2008-06-11
Hi,

I have all of the libboost files installed from the Ubuntu repository along with g++.  The version in the Ubuntu 8.04 repository is 1.34.1 (documentation [here](boost.org/doc/libs/1_34_1/libs/filesystem/doc/index.htm))

I am trying to build sample code that I (for the most part) copy and pasted from the documentation, but I am getting errors when I try to build it.  

Code that I am using (modified only to provide a test main and add a missing "namespace" from the using line from the documentation):
```
#include "boost/filesystem.hpp"   // includes all needed Boost.Filesystem declarations
#include <iostream>               // for std::cout
using namespace boost::filesystem;          // for ease of tutorial presentation;
                                  //  a namespace alias is preferred practice in real code
using namespace std;                                  
       
       
bool find_file( const path & dir_path,         // in this directory,
                const std::string & file_name, // search for this name,
                path & path_found );            // placing path here if found  
                
int main(){
	path outPath;
	find_file("/tmp", "test", outPath);
	return 0;
}
                
                                         
bool find_file( const path & dir_path,         // in this directory,
                const std::string & file_name, // search for this name,
                path & path_found )            // placing path here if found
{
  if ( !exists( dir_path ) ) return false;
  directory_iterator end_itr; // default construction yields past-the-end
  for ( directory_iterator itr( dir_path );
        itr != end_itr;
        ++itr )
  {
    if ( is_directory(itr->status()) )
    {
      if ( find_file( itr->path(), file_name, path_found ) ) return true;
    }
    else if ( itr->path().leaf() == file_name ) // see below
    {
      path_found = itr->path();
      return true;
    }
  }
  return false;
}
```


Here is the error I get when I try to build:
```

/tmp/cciarvdc.o: In function `boost::enable_if<boost::filesystem::is_basic_path<boost::filesystem::basic_path<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, boost::filesystem::path_traits> >, bool>::type boost::filesystem::exists<boost::filesystem::basic_path<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, boost::filesystem::path_traits> >(boost::filesystem::basic_path<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, boost::filesystem::path_traits> const&)':
test.cpp:(.text._ZN5boost10filesystem6existsINS0_10basic_pathISsNS0_11path_traitsEEEEENS_9enable_ifINS0_13is_basic_pathIT_EEbE4typeERKS7_[boost::enable_if<boost::filesystem::is_basic_path<boost::filesystem::basic_path<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, boost::filesystem::path_traits> >, bool>::type boost::filesystem::exists<boost::filesystem::basic_path<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, boost::filesystem::path_traits> >(boost::filesystem::basic_path<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, boost::filesystem::path_traits> const&)]+0x31): undefined reference to `boost::filesystem::detail::status_api(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, int&)'
/tmp/cciarvdc.o: In function `boost::enable_if<boost::filesystem::is_basic_path<boost::filesystem::basic_path<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, boost::filesystem::path_traits> >, boost::filesystem::file_status>::type boost::filesystem::status<boost::filesystem::basic_path<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, boost::filesystem::path_traits> >(boost::filesystem::basic_path<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, boost::filesystem::path_traits> const&)':
test.cpp:(.text._ZN5boost10filesystem6statusINS0_10basic_pathISsNS0_11path_traitsEEEEENS_9enable_ifINS0_13is_basic_pathIT_EENS0_11file_statusEE4typeERKS7_[boost::enable_if<boost::filesystem::is_basic_path<boost::filesystem::basic_path<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, boost::filesystem::path_traits> >, boost::filesystem::file_status>::type boost::filesystem::status<boost::filesystem::basic_path<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, boost::filesystem::path_traits> >(boost::filesystem::basic_path<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, boost::filesystem::path_traits> const&)]+0x31): undefined reference to `boost::filesystem::detail::status_api(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, int&)'
/tmp/cciarvdc.o: In function `boost::filesystem::detail::dir_itr_imp<boost::filesystem::basic_path<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, boost::filesystem::path_traits> >::~dir_itr_imp()':
test.cpp:(.text._ZN5boost10filesystem6detail11dir_itr_impINS0_10basic_pathISsNS0_11path_traitsEEEED1Ev[boost::filesystem::detail::dir_itr_imp<boost::filesystem::basic_path<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, boost::filesystem::path_traits> >::~dir_itr_imp()]+0x1b): undefined reference to `boost::filesystem::detail::dir_itr_close(void*&, void*&)'
/tmp/cciarvdc.o: In function `boost::filesystem::basic_directory_iterator<boost::filesystem::basic_path<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, boost::filesystem::path_traits> >::increment()':
test.cpp:(.text._ZN5boost10filesystem24basic_directory_iteratorINS0_10basic_pathISsNS0_11path_traitsEEEE9incrementEv[boost::filesystem::basic_directory_iterator<boost::filesystem::basic_path<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, boost::filesystem::path_traits> >::increment()]+0xe5): undefined reference to `boost::filesystem::detail::dir_itr_increment(void*&, void*&, std::basic_string<char, std::char_traits<char>, std::allocator<char> >&, boost::filesystem::file_status&, boost::filesystem::file_status&)'
/tmp/cciarvdc.o: In function `boost::filesystem::basic_directory_iterator<boost::filesystem::basic_path<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, boost::filesystem::path_traits> >::m_init(boost::filesystem::basic_path<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, boost::filesystem::path_traits> const&)':
test.cpp:(.text._ZN5boost10filesystem24basic_directory_iteratorINS0_10basic_pathISsNS0_11path_traitsEEEE6m_initERKS4_[boost::filesystem::basic_directory_iterator<boost::filesystem::basic_path<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, boost::filesystem::path_traits> >::m_init(boost::filesystem::basic_path<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, boost::filesystem::path_traits> const&)]+0x22): undefined reference to `boost::filesystem::detail::not_found_error'
test.cpp:(.text._ZN5boost10filesystem24basic_directory_iteratorINS0_10basic_pathISsNS0_11path_traitsEEEE6m_initERKS4_[boost::filesystem::basic_directory_iterator<boost::filesystem::basic_path<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, boost::filesystem::path_traits> >::m_init(boost::filesystem::basic_path<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, boost::filesystem::path_traits> const&)]+0xb4): undefined reference to `boost::filesystem::detail::dir_itr_first(void*&, void*&, std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, std::basic_string<char, std::char_traits<char>, std::allocator<char> >&, boost::filesystem::file_status&, boost::filesystem::file_status&)'
collect2: ld returned 1 exit status
Compilation failed.

```

Any ideas?  I do not recall having problems with the boost filesystem in the version that was in the Fiesty Fawn repository a while back.

Thanks!

---

### Post by WW on 2008-06-11
Show the command(s) that you are using to compile your program. My guess is that you are not giving the correct argument to link the boost library.

---

### Post by KingTermite on 2008-06-11
> **WW said:**
> Show the command(s) that you are using to compile your program. My guess is that you are not giving the correct argument to link the boost library.

+1

If its a lot of libraries, you may have to create a simple make file to make sure the libraries get linked in.

---

### Post by moma on 2008-06-11
How do your compile and link your code?
----

Anyhow, let's see how to bake it.

0) First, list all **boost** related dev-packages that are in the Ubuntu's repo.
$ [COLOR="SeaGreen"]apt-cache search boost[/COLOR]

Or better, list the *-dev packages only. The -dev packages contain (header) include files. They also pull out necessary dependencies (libraries) for development.
$ [COLOR="SeaGreen"]apt-cache search boost | grep "\-dev"[/COLOR]
[SIZE="1"]libboost-dev
libboost-python-dev
libboost-date-time-dev 
libboost-filesystem-dev
libboost-graph-dev 
libboost-iostreams-dev
libboost-program-options-dev
libboost-regex-dev
libboost-serialization-dev
libboost-signals-dev
libboost-test-dev
libboost-thread-dev
libboost-wave-dev
[/SIZE]-----

1) Obviously your code needs the "libboost-filesystem-dev" package so install it.
$ [COLOR="SeaGreen"]sudo apt-get install libboost-filesystem-dev[/COLOR]
-----

2) Now write your code.
**Example 1: Test some file system related functions.**
Try this code first. Save it as test1.cpp.
[PHP]// test1.cpp (boost test).

#include <iostream> 
#include "boost/filesystem.hpp"

using namespace std;
namespace fs = boost::filesystem;

int main()
{
   fs::path outPath("foobar");
   fs::create_directory(outPath);

   return 0;
}[/PHP]
Note: The code defines alias (fs) for the boost::filesystem namespace. I do not know why, but the compilation fails if you write "using namespace boost::filesystem" directly. So stick to the alias fs:: instead. Give good, short alias names for the other boost namespaces you may need.

Do not forget to prefix the calls to boost with namespace. 
Examples:
fs::directory_iterator end_itr; 
if (fs::is_directory(...))...
-----

3) Compile and link you code. 

You must link to the "libboost_filesystem.so" library (dll). 

$ [COLOR="SeaGreen"]g++ test1.cpp -lboost_filesystem -o test1[/COLOR]

Run it 
$ [COLOR="SeaGreen"]./test1[/COLOR]
-----

**Example 2: Test boost's threading library.**

Install first libboost-thread-dev package. The -dev package will install library + header (include) files for development.
$ [COLOR="SeaGreen"]sudo apt-get install libboost-thread-dev[/COLOR]

Write your code:
[PHP]// test2.cpp (test boost threading).
#include <boost/thread/thread.hpp>
#include <iostream>

void hello() 
{
	std::cout << "Hello world, I'm a thread!" << std::endl;
}

int main(int argc, char* argv[]) 
{
	boost::thread thrd(&hello);
	thrd.join();
	return 0;
}
[/PHP]

Again, compile and link it:
$ [COLOR="DarkGreen"]g++ test2.cpp -lboost_thread -o test2[/COLOR]

And run it 
$ [COLOR="SeaGreen"]./test2[/COLOR]
------

**Additional information:**

4) Learn how to create a **Makefile** (which the **make** command reads) 
Start with the step 1.3) of this ([http://users.actcom.co.il/~choo/lupg/tutorials/index.html](http://users.actcom.co.il/~choo/lupg/tutorials/index.html) ) guide.
-----

That's it.

------------

I will here show you couple of commands that may help you further.
What boost packages I've already installed? 
$ [COLOR="SeaGreen"]dpkg -l | grep boost[/COLOR]
or better
$ [COLOR="SeaGreen"]dpkg -l | grep boost | grep "^ii"[/COLOR]

Where are my boost libraries (dynamic dll .so files).
Update the system wide file database first.
$ [COLOR="SeaGreen"]sudo updatedb [/COLOR]

Then locate all boost (lib) files
$ [COLOR="SeaGreen"]locate boost | grep lib[/COLOR]

Everything seems to be in the /usr/lib/ directory. List all dynamic libboost*.so libraries.
$ [COLOR="SeaGreen"]ls -l /usr/lib/libboost*so[/COLOR]
-----

What header (*.hpp) file contains this xxx function?
An example: Where is the "create_directory" function declared in? 
$ [COLOR="SeaGreen"]grep -R "create_directory" /usr/include [/COLOR]
/usr/include/boost/filesystem/operations.hpp
which is of course automatically include by "boost/filesystem.hpp".
------

Good luck with your boost adventure ;-)
------
EDIT: There was a typo in the example code. Fixed it.

---

### Post by Schadenfroh on 2008-06-11
I used an improper argument for g++.  


-lboost_filesystem fixed me right up, thanks moma!

---

### Post by WW on 2008-06-11
@moma: *Super* response!

---

### Post by peter1402 on 2009-03-19
Super reply. just had the same problem forgetting the -l in g++. Thanks.

---

