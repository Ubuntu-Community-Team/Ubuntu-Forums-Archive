---
title: "xml-xalan-c install issue Ubuntu"
date: 2012-02-08
forum: Packaging and Compiling Programs
---

### Post by shayno90 on 2012-02-08
After running the commands below I think xml-xalan-c has not been built correctly:

Download source:
[http://archive.apache.org/dist/xml/xalan-c/](http://archive.apache.org/dist/xml/xalan-c/)

user@user:~$ export XALANCROOT=/home/user/xml-xalan/c
user@user:~$ cd xml-xalan/c
user@user:~/xml-xalan/c$ 
user@user:~/xml-xalan/c$ ./runConfigure -plinux -cgcc -xg++
user@user:~/xml-xalan/c$ make all
user@user:~/xml-xalan/c$ make install

Following this procedure:
"Important: check whether Xalanc Library is really installed after the installation is completed. We can go to the directory /usr/local/lib and /usr/local/include to see whether there are files related to xalanc. If yes, then OK."

Yields no results hence it has not been installed correctly I assume:
user@user:~$ locate xalanc
user@user:~$ 

I ran this test following to detect errors but not sure how to resolve them:

user@user:~/xml-xalan/c$ make -C Tests tests
make: out of directory `/home/user/xml-xalan/c/Tests'
mkdir -p ../lib
mkdir -p ../bin
g++ -O2 -DNDEBUG     -fno-elide-constructors -Wall -fPIC -DLINUX -D_REENTRANT -DXALAN_INMEM_MSG_LOADER -c -I/home/user/xml-xalan/c/src -I/home/user/xml-xalan/c/include -I../nls/include -I/home/user/src/xerces-c-src-3.1.1/src/ -I/home/user/src/xerces-c-src-3.1.1/include/xercesc -I/home/user/src/xerces-c-src-3.1.1/include/  -o ../obj/ThreadTest.o /home/user/xml-xalan/c/Tests/Threads/ThreadTest.cpp
In file included from /home/user/xml-xalan/c/src/xalanc/PlatformSupport/XSLException.hpp:27,
                 from /home/user/xml-xalan/c/src/xalanc/XPath/XalanQName.hpp:38,
                 from /home/user/xml-xalan/c/src/xalanc/XPath/XalanQNameByValue.hpp:27,
                 from /home/user/xml-xalan/c/src/xalanc/XalanTransformer/XalanTransformer.hpp:40,
                 from /home/user/xml-xalan/c/Tests/Threads/ThreadTest.cpp:44:
/home/user/xml-xalan/c/src/xalanc/PlatformSupport/XalanLocator.hpp:62: error: conflicting return type specified for &#8216;virtual XMLSSize_t xalanc_1_10::XalanLocator::getLineNumber() const&#8217;
/usr/local/include/xercesc/sax/Locator.hpp:102: error:   overriding &#8216;virtual XMLFileLoc xercesc_3_1::Locator::getLineNumber() const&#8217;
/home/user/xml-xalan/c/src/xalanc/PlatformSupport/XalanLocator.hpp:65: error: conflicting return type specified for &#8216;virtual XMLSSize_t xalanc_1_10::XalanLocator::getColumnNumber() const&#8217;
/usr/local/include/xercesc/sax/Locator.hpp:112: error:   overriding &#8216;virtual XMLFileLoc xercesc_3_1::Locator::getColumnNumber() const&#8217;
/home/user/xml-xalan/c/Tests/Threads/ThreadTest.cpp: In member function &#8216;void SynchronizedCounter::increment()&#8217;:
/home/user/xml-xalan/c/Tests/Threads/ThreadTest.cpp:144: error: &#8216;LONG_MAX&#8217; was not declared in this scope
/home/user/xml-xalan/c/Tests/Threads/ThreadTest.cpp: In function &#8216;int main(int, char**)&#8217;:
/home/user/xml-xalan/c/Tests/Threads/ThreadTest.cpp:676: error: &#8216;strcmp&#8217; was not declared in this scope
make: *** [../obj/ThreadTest.o] Earráid 1
make: out of directory `/home/user/xml-xalan/c/Tests'

Based on a previous thread:
[http://ubuntuforums.org/showthread.php?t=1302095](http://ubuntuforums.org/showthread.php?t=1302095)

I tried installing the packages below and no luck

user@user:~/xml-xalan/c$ sudo apt-get install libcrypto++-dev libxerces-c2-dev libxml-security-c-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  libxml-security-c-dev: Depends: libxerces-c-dev but it is not going to be installed
E: Broken packages

Any suggestions?

---

### Post by shayno90 on 2012-02-08
Did a clean install and found the following errors upon "make":

:~/xml-xalan/c$ make
make -C src/xalanc all
make[1]: out of directory `/home/user/xml-xalan/c/src/xalanc'
Preparing the directory structure for a build ...
mkdir -p ../../obj
mkdir -p ../../lib
mkdir -p ../../bin
make -C Utils prepare
make[2]: out of directory `/home/user/xml-xalan/c/src/xalanc/Utils'
mkdir -p ../../../nls
mkdir -p ../../../nls/include
make[2]: out of directory `/home/user/xml-xalan/c/src/xalanc/Utils'
make -C Utils locale
make[2]: out of directory `/home/user/xml-xalan/c/src/xalanc/Utils'
make -C MsgCreator 
make[3]: out of directory `/home/user/xml-xalan/c/src/xalanc/Utils/MsgCreator'
g++ -O2 -DNDEBUG     -DXML_BITSTOBUILD_64    -fno-elide-constructors -Wall -fPIC -DLINUX -D_REENTRANT -DXALAN_INMEM_MSG_LOADER -c -I/home/user/xml-xalan/c/src -I/home/user/xml-xalan/c/include -I../../../../nls/include -I/home/user/src/xerces-c-src-3.1.1/src/ -I/home/user/src/xerces-c-src-3.1.1/include/xercesc -I/home/user/src/xerces-c-src-3.1.1/include/  -o ../../../../obj/MsgFileOutputStream.o /home/user/xml-xalan/c/src/xalanc/Utils/MsgCreator/MsgFileOutputStream.cpp
g++ -O2 -DNDEBUG     -DXML_BITSTOBUILD_64    -fno-elide-constructors -Wall -fPIC -DLINUX -D_REENTRANT -DXALAN_INMEM_MSG_LOADER -c -I/home/user/xml-xalan/c/src -I/home/user/xml-xalan/c/include -I../../../../nls/include -I/home/user/src/xerces-c-src-3.1.1/src/ -I/home/user/src/xerces-c-src-3.1.1/include/xercesc -I/home/user/src/xerces-c-src-3.1.1/include/  -o ../../../../obj/ICUResHandler.o /home/user/xml-xalan/c/src/xalanc/Utils/MsgCreator/ICUResHandler.cpp
g++ -O2 -DNDEBUG     -DXML_BITSTOBUILD_64    -fno-elide-constructors -Wall -fPIC -DLINUX -D_REENTRANT -DXALAN_INMEM_MSG_LOADER -c -I/home/user/xml-xalan/c/src -I/home/user/xml-xalan/c/include -I../../../../nls/include -I/home/user/src/xerces-c-src-3.1.1/src/ -I/home/user/src/xerces-c-src-3.1.1/include/xercesc -I/home/user/src/xerces-c-src-3.1.1/include/  -o ../../../../obj/InMemHandler.o /home/user/xml-xalan/c/src/xalanc/Utils/MsgCreator/InMemHandler.cpp
g++ -O2 -DNDEBUG     -DXML_BITSTOBUILD_64    -fno-elide-constructors -Wall -fPIC -DLINUX -D_REENTRANT -DXALAN_INMEM_MSG_LOADER -c -I/home/user/xml-xalan/c/src -I/home/user/xml-xalan/c/include -I../../../../nls/include -I/home/user/src/xerces-c-src-3.1.1/src/ -I/home/user/src/xerces-c-src-3.1.1/include/xercesc -I/home/user/src/xerces-c-src-3.1.1/include/  -o ../../../../obj/MsgCreator.o /home/user/xml-xalan/c/src/xalanc/Utils/MsgCreator/MsgCreator.cpp
g++ -O2 -DNDEBUG     -DXML_BITSTOBUILD_64    -fno-elide-constructors -Wall -fPIC -DLINUX -D_REENTRANT -DXALAN_INMEM_MSG_LOADER -c -I/home/user/xml-xalan/c/src -I/home/user/xml-xalan/c/include -I../../../../nls/include -I/home/user/src/xerces-c-src-3.1.1/src/ -I/home/user/src/xerces-c-src-3.1.1/include/xercesc -I/home/user/src/xerces-c-src-3.1.1/include/  -o ../../../../obj/NLSHandler.o /home/user/xml-xalan/c/src/xalanc/Utils/MsgCreator/NLSHandler.cpp
g++ -O2 -DNDEBUG     -DXML_BITSTOBUILD_64    -fno-elide-constructors -Wall -fPIC -DLINUX -D_REENTRANT -DXALAN_INMEM_MSG_LOADER -c -I/home/user/xml-xalan/c/src -I/home/user/xml-xalan/c/include -I../../../../nls/include -I/home/user/src/xerces-c-src-3.1.1/src/ -I/home/user/src/xerces-c-src-3.1.1/include/xercesc -I/home/user/src/xerces-c-src-3.1.1/include/  -o ../../../../obj/SAX2Handler.o /home/user/xml-xalan/c/src/xalanc/Utils/MsgCreator/SAX2Handler.cpp
g++ -DLINUX -fPIC  -DXALAN_INMEM_MSG_LOADER   \
	  -L/home/user/src/xerces-c-src-3.1.1/lib -lxerces-c ../../../../obj/MsgFileOutputStream.o ../../../../obj/ICUResHandler.o ../../../../obj/InMemHandler.o ../../../../obj/MsgCreator.o ../../../../obj/NLSHandler.o ../../../../obj/SAX2Handler.o -o ../../../../bin/MsgCreator 
make[3]: out of directory `/home/user/xml-xalan/c/src/xalanc/Utils/MsgCreator'
../../../bin/MsgCreator /home/user/xml-xalan/c/src/xalanc/NLS/en_US/XalanMsg_en_US.xlf -TYPE inmem -LOCALE en_US
../../../bin/MsgCreator: error while loading shared libraries: libxerces-c-3.1.so: cannot open shared object file: No such file or directory
make[2]: *** [../../../nls/include/LocalMsgData.hpp] Error 127
make[2]: out of directory `/home/user/xml-xalan/c/src/xalanc/Utils'
make[1]: *** [locale] Error 2
make[1]: out of directory `/home/user/xml-xalan/c/src/xalanc'
make: *** [all] Error 2

It seems it cannot find the correct directory, how is this corrected?

---

### Post by shayno90 on 2012-02-09
Resolved the previous issue by exporting the library path before compiling 

../../../bin/MsgCreator: error while loading shared libraries: libxerces-c-3.1.so: cannot open shared object file: No such file or directory

Do the following before compiling:

user@user:~$ export XALANCROOT=/home/user/xml-xalan/c
user@user:~$ export LD_LIBRARY_PATH=/usr/local/lib:$LD_LIBRARY_PATH
user@user:~$ cd xml-xalan/c
user@user:~/xml-xalan/c$ ./runConfigure -p linux -c gcc -x g++ -b 64
(-b 64 only for 64 bit machines, normally remove for default 32 bit install)
..........

However the next issue occurs for 'make' the install of xalan:

user@user:~/xml-xalan/c$ make all
....................................
/home/user/xml-xalan/c/src/xalanc/Utils/XalanMsgLib/XalanMsgLib.cpp:25: error: expected &#8216;,&#8217; or &#8216;;&#8217; before &#8216;namespace&#8217;
/home/user/xml-xalan/c/src/xalanc/Utils/XalanMsgLib/XalanMsgLib.cpp:74: error: expected &#8216;}&#8217; at end of input
../../../../nls/include/LocalMsgData.hpp:34: warning: &#8216;xalanc_1_10::msgArray&#8217; defined but not used

In the problem file 'XalanMsgLib.cpp':

Line 25: XALAN_CPP_NAMESPACE_BEGIN
Line 74: XALAN_CPP_NAMESPACE_END

Full code:

XALAN_CPP_NAMESPACE_BEGIN


static const XalanDOMChar	s_errString[] =
{
	XalanUnicode::charLetter_M,
	XalanUnicode::charLetter_e,
	XalanUnicode::charLetter_s,
	XalanUnicode::charLetter_s,
	XalanUnicode::charLetter_a,
	XalanUnicode::charLetter_g,
	XalanUnicode::charLetter_e,
	XalanUnicode::charSpace,
	XalanUnicode::charLetter_n,
	XalanUnicode::charLetter_o,
	XalanUnicode::charLetter_t,
	XalanUnicode::charSpace,
	XalanUnicode::charLetter_d,
	XalanUnicode::charLetter_e,
	XalanUnicode::charLetter_f,
	XalanUnicode::charLetter_i,
	XalanUnicode::charLetter_n,
	XalanUnicode::charLetter_e,
	XalanUnicode::charLetter_d,
	0
};



unsigned int
XalanMsgContainer::getNumbOfMsgs()
{
	return gXalanMsgArraySize;
}



const XalanDOMChar*
XalanMsgContainer::getMessage(unsigned int	msgInd)
{
	if ( msgInd < gXalanMsgArraySize )
		return msgArray[msgInd];
	else
		return s_errString;
}




XALAN_CPP_NAMESPACE_END

Other error:
../../../../nls/include/LocalMsgData.hpp:34: warning: &#8216;xalanc_1_10::msgArray&#8217; defined but not used


Need to know if the code requires additional characters or one of the packages needs to be downgraded xerces or xalan?

---

### Post by SevenMachines on 2012-02-09
Hi [shayno90]("http://ubuntuforums.org/member.php?u=1127036"). Can I ask if theres some special reason you need to compile xalan from source? Unless you *really* need to then stick with the repositories version. The reason being, xalan 1.10 is almost 7 years old now since updates, a lifetime in linux terms, compiling unaltered source may well involve a lot of work. 

Luckily that work has already been done for you by other people. To build against xalan then install
```
$ sudo apt-get install libxalan110-dev
```If you need to make changes to xalans source code for some reason, you're better working with the package source, it contains the same source as you were using above plus patches and so on to make it work with ubuntu

```
$ apt-get source libxalan110
$ sudo apt-get build-dep libxalan110
```An additional thing to remember, the 'locate' command searches a regularly updated database file location entries, it does *not* search for files. So, you would need to update the database before searching, for example
```
$ sudo touch /usr/local/lib/somefile
$ locate somefile
#File not found, we need to update the database
$ sudo updatedb
$ locate somefile
/usr/local/lib/somefile

```Better still, do a 'live' file search with find
```
$ find /usr/local/ -name 'somefile'
/usr/local/lib/somefile

```

---

### Post by shayno90 on 2012-02-09
Ok, I have downgraded to xerces-c-src-2.8.0 package due to this:

[http://sourceforge.net/apps/mediawiki/ovaldi/index.php?title=Build_notes](http://sourceforge.net/apps/mediawiki/ovaldi/index.php?title=Build_notes)

"Tested on Solaris 11 Express, gcc/g++ compiler. This may work for other versions of Solaris 11 (e.g. OpenIndiana), but you may have to install pcre and/or libgcrypt by hand. In my system, pcre came without the include files, so I had to grab "headers-pcre" from the package manager. 

- Download Xalan 1.10.0 sources from [http://www.apache.org/dyn/closer.cgi/xml/xalan-c](http://www.apache.org/dyn/closer.cgi/xml/xalan-c) - Download Xerces 2.8.0 (NOT the 3.x version!) from [http://xerces.apache.org/xerces-c/download.cgi](http://xerces.apache.org/xerces-c/download.cgi) - Download OVALdi 5.8.2 from [http://sourceforge.net/projects/ovaldi/files/ovaldi/5.8%20Build%202/](http://sourceforge.net/projects/ovaldi/files/ovaldi/5.8%20Build%202/)"

I have now run into the same issue as the previous poster you helped:

/home/user/xml-xalan/c/src/xalanc/XalanDOM/XalanDOMString.cpp:251: error: &#8216;memmove&#8217; was not declared in this scope
/home/user/xml-xalan/c/src/xalanc/XalanDOM/XalanDOMString.cpp: In static member function &#8216;static unsigned int xalanc_1_10::XalanDOMString::length(const char*)&#8217;:
/home/user/xml-xalan/c/src/xalanc/XalanDOM/XalanDOMString.cpp:780: error: &#8216;strlen&#8217; was not declared in this scope
make[1]: *** [../../obj/XalanDOMString.o] Error 1
make[1]: out of directory `/home/user/xml-xalan/c/src/xalanc'
make: *** [all] Error 2

What was the most effective method of resolving this?

Thanks!

---

### Post by SevenMachines on 2012-02-09
If you're determined to compile it by hand and the -dev headers are no use to you (I wont check again I promise :) )  Two issues to note (at the very least!) in the 7 years.

(1) gcc 4.3 cleaned up includes, this means files will need to have headers added, In the cases mentioned above its <cstring> But see [http://gcc.gnu.org/gcc-4.3/porting_to.html](http://gcc.gnu.org/gcc-4.3/porting_to.html) for reference, there may be more
(2) Ubuntu compiles with --as-needed by default, if you have a newer ubuntu then you might need to deal with making sure libraries are linked after source, a pain

As my previous reply stated, xalan compiles on ubuntu because it has had these, and other, patches applied. If you had
```
 $ apt-get source libxalan110
```
then looked in the debian/patches directory you would see the answer to your problem. I've attached the patches that are needed for issue (1), which you definitely need for the memmove and such issues you mention, and issue(2) which you might.

---

### Post by shayno90 on 2012-02-10
I wasn't too sure if I would have to manually edit the 'xalandomsting.cpp' file myself. Had to do this a few times in the attempt to setup ovaldi with other packages. Amazed that xalan and xerces packages have had few changes over 7 years!

I get this error when trying to unzip the somefixes zipped file with file roller/archive manager:

gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Exiting with failure status due to previous errors

Can you check if the zipped file is fine on your end?

Thanks!

---

### Post by shayno90 on 2012-02-10
Found an apparent patch here and applied it manually as many times when I ran the patch through the terminal some 'hunks' would not complete due to incorrect line numbers:

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=454820](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=454820)

[http://bugs.debian.org/cgi-bin/bugreport.cgi?msg=10;filename=xalan.patch;att=1;bug=454820](http://bugs.debian.org/cgi-bin/bugreport.cgi?msg=10;filename=xalan.patch;att=1;bug=454820)

Applied the patch to five files:
xalan.old/c/src/xalanc/PlatformSupport/DirectoryEnumerator.hpp xalan-1.10/c/src/xalanc/PlatformSupport/DirectoryEnumerator.hpp

xalan.old/c/src/xalanc/XalanDOM/XalanDOMString.cpp xalan-1.10/c/src/xalanc/XalanDOM/XalanDOMString.cpp

xalan.old/c/src/xalanc/XalanExe/XalanExe.cpp xalan-1.10/c/src/xalanc/XalanExe/XalanExe.cpp

xalan.old/c/src/xalanc/XMLSupport/FormatterToHTML.cpp xalan-1.10/c/src/xalanc/XMLSupport/FormatterToHTML.cpp

xalan.old/c/src/xalanc/XSLT/ElemNumber.cpp xalan-1.10/c/src/xalanc/XSLT/ElemNumber.cpp

Ran and tried to compile xalan again but now have new error messages:

/home/user/xml-xalan/c/src/xalanc/PlatformSupport/ProblemListenerBase.cpp: In static member function ‘static void xalanc_1_10::ProblemListenerBase::defaultFormat(xalanc_1_10::PrintWriter&, xalanc_1_10::ProblemListenerBase::eSource, xalanc_1_10::ProblemListenerBase::eClassification, const xalanc_1_10::XalanDOMString&, const xercesc_2_8::Locator*, const xalanc_1_10::XalanNode*)’:
/home/user/xml-xalan/c/src/xalanc/PlatformSupport/ProblemListenerBase.cpp:72: error: no matching function for call to ‘xalanc_1_10::XalanLocator::getSystemId(const xercesc_2_8::Locator*&)’
/home/user/xml-xalan/c/src/xalanc/PlatformSupport/XalanLocator.hpp:59: note: candidates are: virtual const XMLCh* xalanc_1_10::XalanLocator::getSystemId() const
/home/user/xml-xalan/c/src/xalanc/PlatformSupport/ProblemListenerBase.cpp:73: error: ‘XalanFileLoc’ does not name a type
/home/user/xml-xalan/c/src/xalanc/PlatformSupport/ProblemListenerBase.cpp:74: error: ‘XalanFileLoc’ does not name a type
/home/user/xml-xalan/c/src/xalanc/PlatformSupport/ProblemListenerBase.cpp:81: error: ‘lineNo’ was not declared in this scope
/home/user/xml-xalan/c/src/xalanc/PlatformSupport/ProblemListenerBase.cpp:82: error: ‘charOffset’ was not declared in this scope
/home/user/xml-xalan/c/src/xalanc/PlatformSupport/ProblemListenerBase.cpp: At global scope:
/home/user/xml-xalan/c/src/xalanc/PlatformSupport/ProblemListenerBase.cpp:137: error: ‘XMLMessage’ is not a member of ‘xalanc_1_10::XalanMessages’
/home/user/xml-xalan/c/src/xalanc/PlatformSupport/ProblemListenerBase.cpp:138: error: ‘XMLWarning’ is not a member of ‘xalanc_1_10::XalanMessages’
/home/user/xml-xalan/c/src/xalanc/PlatformSupport/ProblemListenerBase.cpp:139: error: ‘XMLError’ is not a member of ‘xalanc_1_10::XalanMessages’
/home/user/xml-xalan/c/src/xalanc/PlatformSupport/ProblemListenerBase.cpp:142: error: ‘XSLTMessage’ is not a member of ‘xalanc_1_10::XalanMessages’
/home/user/xml-xalan/c/src/xalanc/PlatformSupport/ProblemListenerBase.cpp:143: error: ‘XSLTWarning’ is not a member of ‘xalanc_1_10::XalanMessages’
/home/user/xml-xalan/c/src/xalanc/PlatformSupport/ProblemListenerBase.cpp:144: error: ‘XSLTError’ is not a member of ‘xalanc_1_10::XalanMessages’
/home/user/xml-xalan/c/src/xalanc/PlatformSupport/ProblemListenerBase.cpp:147: error: ‘XPathMessage’ is not a member of ‘xalanc_1_10::XalanMessages’
/home/user/xml-xalan/c/src/xalanc/PlatformSupport/ProblemListenerBase.cpp:148: error: ‘XPathWarning’ is not a member of ‘xalanc_1_10::XalanMessages’
/home/user/xml-xalan/c/src/xalanc/PlatformSupport/ProblemListenerBase.cpp:149: error: ‘XPathError’ is not a member of ‘xalanc_1_10::XalanMessages’
make[1]: *** [../../obj/ProblemListenerBase.o] Error 1
make[1]: out of directory `/home/user/xml-xalan/c/src/xalanc'
make: *** [all] Error 2

The patch applied manually did not work so not too sure what to do now, reverse the patch changes or add you somefixes zipped file?

---

### Post by SevenMachines on 2012-02-10
Are you sure you're building [https://archive.apache.org/dist/xml/xalan-c/Xalan-C_current-src.tar.gz](https://archive.apache.org/dist/xml/xalan-c/Xalan-C_current-src.tar.gz)
It has no ProblemListenerBase as far as i can see. The archive posted is fine here but as i mentioned you can get all the current patches by running
$ apt-get source libxalan110
and looking in the debian/patches directory

---

### Post by shayno90 on 2012-02-13
Thanks for the advice sevenmachines, I downloaded the source file for xalan and was able to compile it without any errors.

However I was trying to locate it in the following directories:

 "Important: check whether Xalanc Library is really installed after the installation is completed. We can go to the directory /usr/local/lib and /usr/local/include to see whether there are files related to xalanc. If yes, then OK."

It is not located in either directory, only folders related to xerces.

I installed as follows:

user@user:~$ export XERCESCROOT=/home/user/xerces-c-src_2_8_0
user@user:~$ export XALANCROOT=/home/user/xalan-1.10/c
user@user:~$ export LD_LIBRARY_PATH=/usr/local/lib:$LD_LIBRARY_PATH
user@user:~$ cd xalan-1.10/c
user@user:~/xalan-1.10/c$ cd ~
user@user:~$ sudo su
root@user:/home/user#
root@user:/home/user# sudo chown -R user:user xalan-1.10  (directory was locked as root)
root@user:/home/user# exit
exit
user@user:~$ cd xalan-1.10/c
user@user:~/xalan-1.10/c$ ./runConfigure -p linux -c gcc -x g++ -b 64
user@user:~/xalan-1.10/c$ make
make -C src/xalanc all
.......................
make[1]: out of directory`/home/user/xalan-1.10/c/src/xalanc'

I am guessing that xalan is not installed correctly otherwise it would be located in those directories plus the 'make install' command doesn't work:

user@user:~/xalan-1.10/c$ sudo make install (same of just make install)
[sudo] password for user: 
make -C src/xalanc install
make[1]: out of directory `/home/user/xalan-1.10/c/src/xalanc'
Makefile:126: /version.incl: No such file or directory
make[1]: *** there is no rule for this object `/version.incl' to do.  Stop.
make[1]: out of directory `/home/user/xalan-1.10/c/src/xalanc'
make: *** [install] errors 2

It is looking for the above 'makefile:126: /version.incl'.

---

### Post by SevenMachines on 2012-02-13
Not sure why you have a user called confusingly 'user', or why root ownerships are getting involved. But anyway, the short answer is that 
```
Makefile:126: /version.incl: No such file or directory

```
happens because XALANCROOT is not set. Remember, you set XALANCROOT for a user, then you're sudo'ing to execute a command as another one, root. You could preserve the environment variables across sudo but much better is just to pass it along with the command
```
$ sudo XALANCROOT=/home/user/xalan-1.10/c make -C src/xalanc install
```

---

### Post by shayno90 on 2012-02-13
For xerces, you install as root hence this message:

user@user:~/xerces-c-src_2_8_0/src/xercesc$ sudo make install 
[sudo] password for user: 
make -C util install
make[1]: out of directory `/home/user/xerces-c-src_2_8_0/src/xercesc/util'
mkdir -p /usr/local/include/xercesc/util
make[3]: out of directory `/home/user/xerces-c-src_2_8_0/src/xercesc/validators/schema/identity'
make[2]: out of directory `/home/user/xerces-c-src_2_8_0/src/xercesc/validators/schema'
make[1]: out of directory `/home/user/xerces-c-src_2_8_0/src/xercesc/validators'
make -C /obj install
make: *** /obj: No such file or directory.  Stop.
make: *** [install] Error 2

user@user:~/xerces-c-src_2_8_0/src/xercesc$ sudo su
root@user:/home/user/xerces-c-src_2_8_0/src/xercesc# make install
make -C util install
make[1]: out of directory `/home/user/xerces-c-src_2_8_0/src/xercesc/util'
mkdir -p /usr/local/include/xercesc/util


[http://www.yolinux.com/TUTORIALS/XML-Xerces-C_2.7.0.html](http://www.yolinux.com/TUTORIALS/XML-Xerces-C_2.7.0.html)

"[Potential Pitfall]: If installing as root (required when installing to directory paths like /opt and /usr), remember that root also requires the environment variable XERCESCROOT. Possible error: "

So if I want to add the xalan libraries to /usr/local/lib and /usr/local/include, I should just run sudo with environment variable instead of changing the user to root like below:

user@user:~$ sudo export XERCESCROOT=/home/user/xerces-c-src_2_8_0
user@user:~$ sudo export XALANCROOT=/home/user/xalan-1.10/c

Got this after trying the sudo export:

user@user:~$ sudo export XERCESCROOT=/home/user/xerces-c2-2.8.0+deb1/
sudo: export: command not found

So, you have to change user to root before you export the environmment variable but then switch back to user before the build.

---

### Post by SevenMachines on 2012-02-13
You might as well open a shell for root and run the export commands and make install there. 
```
$ sudo -s
$ export XERCESCROOT=/home/user/xerces-c-src_2_8_0
$ export XALANCROOT=/home/user/xalan-1.10/c
$ make install
```

---

### Post by shayno90 on 2012-02-14
I finally managed to compile and install Xerces and Xalan together for Ubuntu 10.04 with some help from sevenmachines, do as follows:

1.
sudo apt-get source libxerces-c28
sudo apt-get source libxalan110

2.
add "export LD_LIBRARY_PATH=/usr/local/lib:$LD_LIBRARY_PATH" to /etc/ld.so.conf

3.
you may need to change owner of source packages from root to normal user

4. Build Xerces
export XERCESCROOT=/home/user/xerces-c2-2.8.0+deb1
cd $XERCESCROOT
cd src/xercesc
./runConfigure -plinux -cgcc -xg++ -minmem -nsocket -rpthread -b64 -P /usr/local
make
sudo XERCESCROOT=$XERCESCROOT make install

5. Build Xalan
export XERCESCROOT=/usr/local
cd $XERCESCROOT
/usr/local$ cd ~
export XERCESCROOT=/home/user/xerces-c2-2.8.0+deb1
cd $XERCESCROOT
cd ~
export XALANCROOT=/home/user/xalan-1.10/c
cd $XALANCROOT
./runConfigure -p linux -c gcc -x g++ -b64 -P /usr/local
make
sudo XALANCROOT=$XALANCROOT make install

6. 
Check the directories of /usr/local/lib and /usr/local/include to confirm the both Xerces and Xalan are both installed

---

