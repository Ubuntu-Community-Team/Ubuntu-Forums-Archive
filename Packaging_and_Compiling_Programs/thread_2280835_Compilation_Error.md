---
title: "Compilation Error"
date: 2015-06-02
forum: Packaging and Compiling Programs
---

### Post by ramsforums on 2015-06-02
Greetings :)

I have a seedbox and trying to compile  [http://downloads.sourceforge.net/mktorrent/mktorrent-1.0.tar.gz](http://downloads.sourceforge.net/mktorrent/mktorrent-1.0.tar.gz)

I have downloaded the .tar.gz file.
The instruction on the website says as follows

```


**Basics**

[COLOR=#000000][FONT=Times New Roman]Get the source code from the links above, extract the files, enter the directory and run make to build the program. However, see the recommend build one-liners below.[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]To install the program to [/FONT][/COLOR]/usr/bin[COLOR=#000000][FONT=Times New Roman] do [/FONT][/COLOR]make PREFIX=/usr install[COLOR=#000000][FONT=Times New Roman] as root.

[/FONT][/COLOR]
```

The  README file, the instruction says

> 

Type 'make' to build the program.
Do 'make install' to install the program to /usr/local/bin.





When I execute I get the following message

> 

root@mysbox:~/mktorrent-1.0# make
cc -O2 -Wall   prefix.c -o prefix
make: cc: Command not found
make: *** [prefix] Error 127




If I type the following

> 
root@mysbox:~/mktorrent-1.0# ./configure
-bash: ./configure: No such file or directory



How do I compile?. Appreciate your help.

Thanks :)

---

### Post by steeldriver on 2015-06-02
If cc is not found, you likely don't have a C compiler installed on your system: the standard C compiler is gcc, which you can install from the Software Center or using apt-get. Most people would probably recommend installing the build-essential metapackage, which includes both gcc and g++ (the corresponding C++ compiler) as well as a couple of other useful development packages

---

### Post by ramsforums on 2015-06-02
> **steeldriver said:**
> If cc is not found, you likely don't have a C compiler installed on your system: the standard C compiler is gcc, which you can install from the Software Center or using apt-get. Most people would probably recommend installing the build-essential metapackage, which includes both gcc and g++ (the corresponding C++ compiler) as well as a couple of other useful development packages


thank you steeldriver.
I do not have gui. I am using putty to login remotely.

so the command is  

> apt-get  install build-essential;


Am I correct? Anything else?

---

### Post by steeldriver on 2015-06-02
Yes that should work - from the root prompt - or prefixed by sudo if you are in a regular user shell. The semicolon is not necessary (but not incorrect either).

---

### Post by ramsforums on 2015-06-03
Thank you it worked.

---

