---
title: "Ubuntu 11.10 and old boost library"
date: 2012-04-25
forum: Programming Talk
---

### Post by erotavlas on 2012-04-25
Hi,

I'm using Ubuntu 11.10 64 bit which uses boost library 1.46 and GCC 4.6.1. I would like to link my executable with the previous version of boost library 1.42. I use only two dynamic libraries boost_system and boost_filesystem. I have copied the two libraries inside /usr/lib and I have passed them to the linker but I get a strange and very long error during the linking phase. Is there something that I have forgotten to do?

Thank you

---

### Post by Zugzwang on 2012-04-25
Can you paste the error messages here?

---

### Post by erotavlas on 2012-04-26
Hi,

the code is trivial
```

#include <boost/filesystem.hpp> // for make dir
#include <iostream>

int main()
{
	// create a directory for the data
    const std::string& path = "data";

    if (!boost::filesystem::create_directories(path.c_str()))
    {
        std::cout << "Cannot create directory ' " << path << "': File exist" << std::endl;
    }

	return 0;
}


```

I can compile with success with: g++ lib_boost.cpp -o lib_boost -lboost_filesystem -lboost_system
or
g++ lib_boost.cpp -o lib_boost -l:libboost_filesystem.so.1.46.1 -l:libboost_system.so.1.46.1.
Where the library_name.so.1.46.1 are located under /usr/lib and are the standard libraries provided by Ubuntu 11.10.

With this g++ lib_boost.cpp -o lib_boost -l:libboost_filesystem.so.1.42.0 -l:libboost_system.so.1.42.0 I get the following error 

```

/tmp/ccrGaAVd.o: In function `__static_initialization_and_destruction_0(int, int)':
lib_boost_prova.cpp:(.text+0x15d): undefined reference to `boost::system::generic_category()'
lib_boost_prova.cpp:(.text+0x169): undefined reference to `boost::system::generic_category()'
lib_boost_prova.cpp:(.text+0x175): undefined reference to `boost::system::system_category()'
/tmp/ccrGaAVd.o: In function `boost::filesystem3::path::codecvt()':
lib_boost_prova.cpp:(.text._ZN5boost11filesystem34path7codecvtEv[boost::filesystem3::path::codecvt()]+0x5): undefined reference to `boost::filesystem3::path::wchar_t_codecvt_facet()'
/tmp/ccrGaAVd.o: In function `boost::filesystem3::create_directories(boost::filesystem3::path const&)':
lib_boost_prova.cpp:(.text._ZN5boost11filesystem318create_directoriesERKNS0_4pathE[boost::filesystem3::create_directories(boost::filesystem3::path const&)]+0x19): undefined reference to `boost::filesystem3::detail::create_directories(boost::filesystem3::path const&, boost::system::error_code*)'
collect2: ld returned 1 exit status

```

also these libraries are unde /usr/lib.

Thank you

---

### Post by dwhitney67 on 2012-04-26
Let's see... your code compiles/links OK with Boost 1.46, but not with 1.42?

I have confirmed that is builds with Boost 1.46, and I have also verified that your code builds with Boost 1.40 (note: only -lboost_filesystem is needed; not -lboost_system when using 1.40).

So, the question is, did you build the boost 1.42 libraries yourself, or did you get it from a repository?  Have you referenced the release notes for Boost 1.4.3 (or whatever version that comes after 1.4.2) to see if there was a bug with 1.4.2?

---

### Post by erotavlas on 2012-04-26
Hi,

I would like to compile/link with the old boost library 1.42 in Ubuntu 11.10. I just took the libraries from Ubuntu 11.04 and copied them in /usr/lib. Is it correct?

Thank

---

### Post by dwhitney67 on 2012-04-26
> **erotavlas said:**
> Hi,

I would like to compile/link with the old boost library 1.42 in Ubuntu 11.10. I just took the libraries from Ubuntu 11.04 and copied them in /usr/lib. Is it correct?

Thank

Noooo!  You should never do that.  The boost 1.42 libraries were undoubtedly built using different C and C++ libraries, and who knows what else.

If you want to use Boost 1.42, download the source code, and then build the library on your system.

P.S.  When you install Boost 1.42, I would recommend that you place it somewhere other than /usr/lib or /usr/lib64.

---

### Post by erotavlas on 2012-04-27
Hi,

I installed the boost library 1.42.0 under /opt/ directory. After that I run the command ldconfig, and I got the message

```

 /sbin/ldconfig.real: /usr/lib/libboost_filesystem.so.1.42.0 is not a symbolic link

```

It refers probably to the old copy in /usr/lib.
What have I to do?

Thank you

---

### Post by dwhitney67 on 2012-04-27
> **erotavlas said:**
> Hi,

I installed the boost library 1.42.0 under /opt/ directory. After that I run the command ldconfig, and I got the message

```

 /sbin/ldconfig.real: /usr/lib/libboost_filesystem.so.1.42.0 is not a symbolic link

```

It refers probably to the old copy in /usr/lib.
What have I to do?

Thank you
Did you build the library?  Again, merely copying it from one system to another, regardless of where you place it, is no guarantee for success.

Download the source code from [here]("http://www.boost.org/users/history/version_1_42_0.html"), and then (sorry to say), figure out the instructions to build the Boost library such that it is installed in /opt.

Btw, why must you use Boost 1.4.2 in lieu of a later version?

---

### Post by erotavlas on 2012-04-27
> **dwhitney67 said:**
> Did you build the library?  Again, merely copying it from one system to another, regardless of where you place it, is no guarantee for success.

Download the source code from [here]("http://www.boost.org/users/history/version_1_42_0.html"), and then (sorry to say), figure out the instructions to build the Boost library such that it is installed in /opt.

Btw, why must you use Boost 1.4.2 in lieu of a later version?

Yes I installed the library in /opt path. Following the standard guide:
```

./bootstrap.sh --prefix=/opt/boost-1.42.0 --with-libraries=filesystem system
 ./bjam install --prefix=/opt/boost-1.42.0

```

Now with this
```

g++ lib_boost_prova.cpp -o lib_boost_prova  -l:/opt/boost-1.42.0/lib/libboost_filesystem.so.1.42.0 -l:/opt/boost-1.42.0/lib/libboost_system.so.1.42.0 

```

I get this message
```

/tmp/cc62XSV3.o: In function `__static_initialization_and_destruction_0(int, int)':
lib_boost_prova.cpp:(.text+0x13c): undefined reference to `boost::system::generic_category()'
lib_boost_prova.cpp:(.text+0x148): undefined reference to `boost::system::generic_category()'
lib_boost_prova.cpp:(.text+0x154): undefined reference to `boost::system::system_category()'
/tmp/cc62XSV3.o: In function `boost::filesystem3::path::codecvt()':
lib_boost_prova.cpp:(.text._ZN5boost11filesystem34path7codecvtEv[boost::filesystem3::path::codecvt()]+0x5): undefined reference to `boost::filesystem3::path::wchar_t_codecvt_facet()'
/tmp/cc62XSV3.o: In function `boost::filesystem3::create_directories(boost::filesystem3::path const&)':
lib_boost_prova.cpp:(.text._ZN5boost11filesystem318create_directoriesERKNS0_4pathE[boost::filesystem3::create_directories(boost::filesystem3::path const&)]+0x19): undefined reference to `boost::filesystem3::detail::create_directories(boost::filesystem3::path const&, boost::system::error_code*)'
collect2: ld returned 1 exit status

```

It's a linker problem. I think that is related to ldconfig.

---

### Post by dwhitney67 on 2012-04-27
> **erotavlas said:**
> 
Now with this
```

g++ lib_boost_prova.cpp -o lib_boost_prova  -l:/opt/boost-1.42.0/lib/libboost_filesystem.so.1.42.0 -l:/opt/boost-1.42.0/lib/libboost_system.so.1.42.0 

```


I tried your program on my Kubuntu 11.10 system, and it works fine.

Try this command, thus ensuring that you are using the proper header files:
```

g++ -I/opt/boost-1.42.0/include lib_boost_prova.cpp -o lib_boost_prova -L/opt/boost-1.42.0/lib -lboost_filesystem -lboost_system

```

---

### Post by erotavlas on 2012-04-28
> **dwhitney67 said:**
> I tried your program on my Kubuntu 11.10 system, and it works fine.

Try this command, thus ensuring that you are using the proper header files:
```

g++ -I/opt/boost-1.42.0/include lib_boost_prova.cpp -o lib_boost_prova -L/opt/boost-1.42.0/lib -lboost_filesystem -lboost_system

```

Great! This solved the problem. Thank you very much. I learnt a new thing.

Bye

---

### Post by erotavlas on 2012-05-05
Hi,

I have a similar problem with Netbeans project. I can compile with success the trivial examples
```

#include <boost/filesystem.hpp> // for make dir #include <iostream>  int main() {     // create a directory for the data     const std::string& path = "data";      if (!boost::filesystem::create_directories(path.c_str()))     {         std::cout << "Cannot create directory ' " << path << "': File exist" << std::endl;     }      return 0; }

```While if I make a trivial project with Netbeans, I get this error

```

build/Debug/GNU-Linux-x86/main.o: In function `boost::enable_if<boost::filesystem::is_basic_path<boost::filesystem::basic_path<std::string, boost::filesystem::path_traits> >, bool>::type boost::filesystem::is_directory<boost::filesystem::basic_path<std::string, boost::filesystem::path_traits> >(boost::filesystem::basic_path<std::string, boost::filesystem::path_traits> const&)':
/usr/include/boost/filesystem/operations.hpp:303: undefined reference to `boost::filesystem::detail::status_api(std::string const&, boost::system::error_code&)'
build/Debug/GNU-Linux-x86/main.o: In function `boost::enable_if<boost::filesystem::is_basic_path<boost::filesystem::basic_path<std::string, boost::filesystem::path_traits> >, bool>::type boost::filesystem::create_directory<boost::filesystem::basic_path<std::string, boost::filesystem::path_traits> >(boost::filesystem::basic_path<std::string, boost::filesystem::path_traits> const&)':
/usr/include/boost/filesystem/operations.hpp:423: undefined reference to `boost::filesystem::detail::create_directory_api(std::string const&)'

```The same procedure under the latest Ubuntu 12.04 works fine.

---

### Post by dwhitney67 on 2012-05-05
Why is Netbeans looking here for Boost header files?:  /usr/include

It should be looking here:  /opt/boost-1.42.0/include

And similarly for the libraries, tell Netbeans to look here:  /opt/boost-1.42.0/lib

---

### Post by erotavlas on 2012-05-05
> **dwhitney67 said:**
> Why is Netbeans looking here for Boost header files?:  /usr/include

It should be looking here:  /opt/boost-1.42.0/include

And similarly for the libraries, tell Netbeans to look here:  /opt/boost-1.42.0/lib
Hi,

I have just copied the  /opt/boost-1.42.0/include/boost in /usr/include. The strange thing is that with default version of gcc 4.6.1 and with version 4.6.3 compiled from source, the program compiles well. With gcc 4.7.0 I get the previous error.
Where could be the problem?

Thank you

---

### Post by erotavlas on 2012-05-06
> **erotavlas said:**
> Hi,

I have just copied the  /opt/boost-1.42.0/include/boost in /usr/include. The strange thing is that with default version of gcc 4.6.1 and with version 4.6.3 compiled from source, the program compiles well. With gcc 4.7.0 I get the previous error.
Where could be the problem?

Thank you

I'm doing a lot of trials. The results are the following:
Ubuntu 12.10 and libboost 1.42.0 installed from source and copied in /usr/include/boost
GCC 4.6.3 native installed from repository works
GCC 4.7.0 installed from source works
Ubuntu 11.10 and libboost 1.42.0 installed from source and copied in /usr/include/boost
GCC 4.6.1 native installed from repository works
GCC 4.6.3 installed from source works
GCC 4.7.0 installed from source does not work
Ubuntu 11.04 and libboost 1.42.0 installed from repository
GCC 4.5.2 native installed from repository works
GCC 4.6.3 installed from source works
 GCC 4.7.0 installed from source does not work
In all case I compile with the previous command line 
```

g++ lib_boost_prova.cpp -o lib_boost_prova -L/opt/boost-1.42.0/lib -lboost_filesystem -lboost_system

```

---

