---
title: "Problem with shared libraries, please help"
date: 2011-03-26
forum: Programming Talk
---

### Post by _eduardo on 2011-03-26
Hi,
i'm using Eclipse CDT in association with a SOAP framework (WSO2 WSF/C++) for creating a C++ client for a web service. I've already added the path for the libraries i'm using in the Project->Properties->GCC C++ Linker->Libraries window. My program compiles, but when i try to run it, this messages appears:

"error while loading shared libraries: libwso2_wsf.so.0: cannot open shared object file: No such file or directory"


I have three different .so files in the same folder (/usr/local/wso2wsfcpp), but with the same name: 

>libwso2_wsf.so
>libwso2_wsf.so.0
>libwso2_wsf.so.0.0.0

The first two are links to the third one. I thought that maybe i should change the destiny of the first link to the second one, but examining the other files in the same folder i saw that all libraries are organized exactly like this libwso2_wsf. In other words, they all have three files, two pointing to the third one, except that instead of "0.0.0" some other files have "0.6.0", for example.

Does someone have any idea of how can i solve this problem?
Thanks

---

### Post by MadCow108 on 2011-03-26
/usr/local/wso2wsfcpp is not in the search path of your runtime linker (ld.so)
There are various ways to solve this:
- add the path to your /etc/ld.so.conf or /etc/ld.so.conf.d/file and reload the cache with ldconfig
- (place the library in a path already searched (/usr/lib))
- add it to the environment variable LD_LIBRARY_PATH, e.g. in bash: export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/wso2wsfcpp
- hard code it in your executable, e.g. with ld: -Wl,-rpath,/usr/local/wso2wsfcpp

the two links have the purpose to install multiple libraries with different interfaces at the same time.
the .so link is used for development and usually points to the newest version available
the .so.X is the interface version or soversion defining the API/ABI.
the .so.X.Y.Z is the actual library with Y,Z being the revision or age. these are incremented when a library updates but the API/ABI stays the same.
The numbers have nothing or little to do with the official version number of the library
the linker will search the appropriate library with a matching soversion to the one needed

---

### Post by _eduardo on 2011-03-26
I've followed one of your suggestions and the error message disappeared. I've been trying to solve this for almost a week, so thank you!

---

### Post by RobertMajor on 2011-11-10
I have been experiencing a very similar problem.  I am trying to run some programs from OpenGL Super Bible which requires the shared library GLTools.  

I have tried multiple ways of generating this shared library following the instructions from these sites:

[www.gnu.org/software/libtool/manual/libtool.html#Creating-object-files](www.gnu.org/software/libtool/manual/libtool.html#Creating-object-files)
tldp.org/HOWTO/Program-Library-HOWTO/shared-libraries.html
[www.yolinux.com/TUTORIALS/LibraryArchives-StaticAndDynamic.html](www.yolinux.com/TUTORIALS/LibraryArchives-StaticAndDynamic.html)

Every time I have managed to generate the shared library and install it with no problems (I do get a few warning when compiling).  At the end of the process I end up with the following three files in /usr/local/lib

libGLTools.so
libGLTools.so.0
libGLTools.so.0.0.0

running ldconfig -v I get: libGLTools.so.0 -> libGLTools.so.0.0.0

But then when I try to run my code in Qt I get the following message in Application Output:

p, li { white-space: pre-wrap; }    [COLOR=#C80000][FONT=Monospace] error while loading shared libraries: libGLTools.so.0: cannot open shared object file: No such file or directory[/FONT][/COLOR]
  
Furthermore, if I use ldd I get a list of all the libraries used by the program including libGLTools but it says libGLTools.so.0 =>   not found

/usr/local/lib is definitely on my search path since the program uses other libraries in that folder and it has no problems finding those.  I have now spent over week on this and I cannot figure out how to fix it.  Any suggestions would be greatly appreciated?

---

