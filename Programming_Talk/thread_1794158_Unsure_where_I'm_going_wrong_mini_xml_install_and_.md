---
title: "Unsure where I'm going wrong? mini xml install and usage"
date: 2011-06-30
forum: Programming Talk
---

### Post by ubundurp on 2011-06-30
If anyone can help me or let me know where I should repost this question, I would be greatly appreciative.  Thanks.

I am developing an application.... call it myapplication.  I started to input and parse a text cfg file manually in ansi c.  I started getting clever with a txt version of a config file using keywords and trying to read in and parse the data I needed from each table into char arrays.  I started thinking that XML would be a lot easier and since I need to do that eventually anyhow I dropped the effort for reading in the data from a formatted txt file and I have now spent over 2 days trying to get an ansi c compatible version of XML (called mini-xml) running on Ubuntu so that I can use the xml functions from my "myapplication" to read in an xml file.  It is not going well.  I think both my unfamiliarity with Linux and the lack of a good set of instructions for mini-xml installation/build is holding me back.  But I thinkmy lackof knowledge on how Linux features/additions are integrated into each other is the real issue here.

In short, I do not know the steps I need to do to use mini-xml.

I do not know:
    - what to install, build/make, or where the output of such actions will put what files
    - where to take these files and place them in order to be able to include the mxml.h file to my "myapplication" and use.   


My Goal: To use fns in the mini-xml API such as 
	MiniXMLDoc
	createElement
	getElement
	fromFile
	etc...


How the directory structure looks on Ubuntu:
Ubundurp\
	myapplication 
	CCU5
	mini-xml

Here are the instructions that come with mini-xml: (SEE MY COMMENTS IN CAPITAL BELOW WITH MY USERNAME "UBUNDURP" PRECEDING) 

README - 2009-05-17
-------------------


INTRODUCTION

    This README file describes the Mini-XML library version 2.6.

    Mini-XML is a small XML parsing library that you can use to read XML and
    XML-like data files in your application without requiring large non-standard
    libraries.  Mini-XML only requires an ANSI C compatible compiler (GCC works,
    as do most vendors' ANSI C compilers) and a "make" program.

    Mini-XML provides the following functionality:

	- Reading of UTF-8 and UTF-16 and writing of UTF-8 encoded XML files and
	  strings.
	- Data is stored in a linked-list tree structure, preserving the XML
	  data hierarchy.
	- Supports arbitrary element names, attributes, and attribute values
	  with no preset limits, just available memory.
	- Supports integer, real, opaque ("cdata"), and text data types in
	  "leaf" nodes.
	- Functions for creating and managing trees of data.
	- "Find" and "walk" functions for easily locating and navigating trees
	  of data.

    Mini-XML doesn't do validation or other types of processing on the data
    based upon schema files or other sources of definition information.


BUILDING Mini-XML

    Mini-XML comes with an autoconf-based configure script; just type the
    following command to get things going:

        ./configure	(UBUNDURP: THIS WORKED AFTER I REMOVED THE WINDOWS STYLE LINEFEED/CARRIAGE RETURN) 

    The default install prefix is /usr/local, which can be overridden using the
    --prefix option:

        ./configure --prefix=/foo

    Other configure options can be found using the --help option:

        ./configure --help

    Once you have configured the software, type "make" to do the build and run
    the test program to verify that things are working, as follows:

        make	(UBUNDURP: SEEMS TO HAVE WORKED HOWEVER NOT ALL OF THE TESTS THAT WERE RUN PASSED.  SOME FAILED.  I THINK AT THIS POINT I'M EITHER TRYING TO ACCESS A FEATURE OF LINUX THAT IS EITHER NOT INSTALLED OR NOT AVAILABLE/VISIBLE TO ME FROM WITHIN THE MINI-XML FILES STRUCTURE) 

    If you are using Mini-XML under Microsoft Windows with Visual C++ 2008, use
    the included project files in the "vcnet" subdirectory to build the library
    instead.


INSTALLING Mini-XML

    The "install" target will install Mini-XML in the lib and include
    directories:

        make install	(UBUNDURP: THIS ALSO SEEMED TO WORK SINCE I HAVE A BUNCH OF .O TYPE FILES IN MY MINI-XML DIRECTORY) 

    Once you have installed it, use the "-lmxml" option to link your application
    against it.	

(UBUNDURP: I CANNOT SEEM TO GET THIS TO WORK IN THE MAKE FILE WHEN I ADD THIS OPTION TO THE EXISTING LINE in "myapplication"s make file. 

$(TARGET): $(COBJS)
	$(CC) $(CFLAGS) -o $@ $(COBJS) $(LDFLAGS) -lnsl -lrt -lpthread -lmxml $(EXTRA_LIBS)    	(UNUNDURP: <- FAILS AND SAYS "cannot find -lmxml")

I WAS UNDER THE IMPRESSION THE -LMXML WAS AN OPTIONAL DIRECTIVE TO THE COMPILER.  BUT HERE IT SEEMS LIKE WHEREVER THEY HAVE THAT LMXML DIRECTIVE DEFINED IS NOT IN THE SCOPE OF THE APPLICATION I AM DEVELOPING.  I JUST DO NOT KNOW WHAT PART(S) OF THE MINI-XML PACKAGE I NEED TO PULL INTO THE APPLICATION FOLDERS.  THE '.O' FILES?  ALL OF THE CODE FILES?  SOME .LIB FILE? EVERYTHING?  I KNOW THESE AREN'T FAIR QUESTIONS, BUT I FIGURED IF I EXPLAINED MY ISSUE, YOU MIGHT HAVE A LEAD I CAN FOLLOW.  IF SO, MAYBE IT'LL GET ME OUT OF BEING STUCK LIKE I AM NOW.  ) 


DOCUMENTATION

    The documentation is available in the "doc" subdirectory in the files
    "mxml.html" (HTML) and "mxml.pdf" (PDF). You can also look at the
    "testmxml.c" and "mxmldoc.c" source files for examples of using Mini-XML.

    Mini-XML provides a single header file which you include:

        #include <mxml.h>

    Nodes are defined by the "mxml_node_t" structure; the "type" member defines
    the node type (element, integer, opaque, real, or text) which determines
    which value you want to look at in the "value" union.  New nodes can be
    created using the "mxmlNewElement()", "mxmlNewInteger()", "mxmlNewOpaque()",
    "mxmlNewReal()", and "mxmlNewText()" functions.  Only elements can have
    child nodes, and the top node must be an element, usually "?xml".

    You load an XML file using the "mxmlLoadFile()" function:

        FILE *fp;
        mxml_node_t *tree;

	fp = fopen("filename.xml", "r");
	tree = mxmlLoadFile(NULL, fp, MXML_NO_CALLBACK);
	fclose(fp);		

(UNUNDURP: THIS IS THE CODE SNIPPPET I AM TRYING TO GET TO WORK.   IT FAILS DURING THE MAKE SAYING "underfined reference to 'mxmlLoadFile' " WHICH MAKES SENSE BECAUSE EVEN IF I PUT THE MXML.H FILE INTO THE APPLICATION FOLDER, THE DEFENITION OF THE FN IS EXTERN.  BUT EXTERN TO WHERE?

---

### Post by Arndt on 2011-06-30
> **ubundurp said:**
> If anyone can help me or let me know where I should repost this question, I would be greatly appreciative.  Thanks.

[...]
        FILE *fp;
        mxml_node_t *tree;

	fp = fopen("filename.xml", "r");
	tree = mxmlLoadFile(NULL, fp, MXML_NO_CALLBACK);
	fclose(fp);		

(UNUNDURP: THIS IS THE CODE SNIPPPET I AM TRYING TO GET TO WORK.   IT FAILS DURING THE MAKE SAYING "underfined reference to 'mxmlLoadFile' " WHICH MAKES SENSE BECAUSE EVEN IF I PUT THE MXML.H FILE INTO THE APPLICATION FOLDER, THE DEFENITION OF THE FN IS EXTERN.  BUT EXTERN TO WHERE?

I haven't used mini xml before, but I just now installed it, and got this little program to build. I didn't fetch the source code, like you did, but installed it with the synaptic package manager, so I can't answer those questions of yours. If you don't have any particular reason for building it yourself, I suggest you just give that up and fetch it from the repositories instead.

The complete program looks like this:

```
#include <stdio.h>
#include <mxml.h>

int main()
{
  FILE *fp;
  mxml_node_t *tree;

  fp = fopen("filename.xml", "r");
  tree = mxmlLoadFile(NULL, fp, MXML_NO_CALLBACK);
  fclose(fp);
}

```

and I build it with this command:

```
gcc -o mx mx.c -lmxml
```

There is a mxml manual page.

---

### Post by cgroza on 2011-06-30
In the future, code tags will make the thing a lot more readable, keeps the identation too.

---

### Post by cygnusc on 2013-02-21
I know this is an old thread but I am having trouble with using Mini-XML on Visual Studio.

After compiling the source code with VS , I sent mxml1.lib to my lib directory and mxml.h to my include directory, and also include the path to mxml1.dll to my PATH variable.

I assume that's all I need to do but when I tried to run the sample program above, VS gave me the following error message:

Unhandled exception at 0x77a08df9 in testmxml.exe: 0xC0000005 Access violation writing location 0x00000014.

This is probably due to the function call mxmlLoadFile(). Any idea? :)

---

### Post by Zugzwang on 2013-02-21
> **cygnusc said:**
> 
Unhandled exception at 0x77a08df9 in testmxml.exe: 0xC0000005 Access violation writing location 0x00000014.

This is probably due to the function call mxmlLoadFile(). Any idea? :)

Absolutely. Location "0x00000014" is a good indication for the fact that you used a NULL pointer somewhere. Since you have Visual Studio, firing up its debugger should be easy for you. Then see if you passed a NULL pointer to a function of that library. If you used the same test program, my guess is that "fopen" failed.

---

### Post by cygnusc on 2013-02-21
Thanks. I just tried mini-xml 2.6 and the problem disappeared (I was using ver 2.7 back then).

---

