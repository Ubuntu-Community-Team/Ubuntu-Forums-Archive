---
title: "how to compile a c++ sorce code in Ubuntu"
date: 2010-09-02
forum: Programming Talk
---

### Post by bulbmaker on 2010-09-02
Hi,
I want to compile a free download manager source code(c++) in ubuntu.
plz some one help me in compiling this source code.
fdm sorce code is available at
[http://www.sourceforge.net/projects/freedownload](http://www.sourceforge.net/projects/freedownload)

i just know how to compile n run a simple c program in ubuntu.

thank u in advance.

---

### Post by lisati on 2010-09-02
Moved to "Programming Talk".

Have a look in the file you've downloaded. There is likely to be a "readme" file with specific instructions. A common method is to extract the archive to its own directory, navigate to the directory where you extracted the files, and type in something like the following:
```

./configure
make
make install

```
(Note: only go to the next step if the one you've just done worked without errors)

To compile a "C" program, Ubunutu has the gcc compiler. For C++, there's the g++ compiler. You might have to make sure that the "build-essential" and the g++ packages are installed first.

Although C++ has its origins in the C programming langauge, these days there are enough differences to count them as different langauges - it's usually best to use an appropriate compiler.

---

### Post by GeneralZod on 2010-09-02
> 
Also we **plan to** port it to Linux and Mac OS. 


That doesn't sound too promising :/

Edit:

Woo - several tens of thousands of lines of uncommented MFC code with plenty of magic numbers and Hungarian notation! Joy!

---

### Post by coolman98 on 2010-09-02
nope

---

### Post by v1ad on 2010-09-02
[http://www.ubuntugeek.com/how-to-install-c-and-c-compilers-in-ubuntu-and-testing-your-first-c-and-c-program.html](http://www.ubuntugeek.com/how-to-install-c-and-c-compilers-in-ubuntu-and-testing-your-first-c-and-c-program.html)

here you go.

---

### Post by hakermania on 2010-09-02
You will find info in the README file on how to compile and then install.

---

### Post by bulbmaker on 2010-09-03
neither ./configure nor make worked. actually there is no configure file here nor any README.
I think source code is platform independent and it can be compiled on linux though its written on windows.
These r the contents of fdm(Free Download Manager) source code zip. Plz someone help me. can i compile this on ubuntu? if yes how? should i hav to make some changes to any of these files? plz.... help me

AERDlg.cpp
AERDlg.h
AppStatusBar.cpp
AppStatusBar.h
array.h
Bittorrent
BtDld_Files.cpp
BtDld_Files.h
...
...

remaining files are present in the txt file attached here.

I think i should start with compiling one of these files. I donno what is that file.

---

### Post by James78 on 2010-09-03
```
g++ *.cpp -o executable
```

---

### Post by dwhitney67 on 2010-09-03
> **hakermania said:**
> You will find info in the README file on how to compile and then install.

And a pot o' gold at the end of the rainbow.

---

### Post by spjackson on 2010-09-03
> **bulbmaker said:**
> 
I think source code is platform independent and it can be compiled on linux though its written on windows.

The source is certainly NOT platform independent. Why do you think it is?

> **bulbmaker said:**
> 
 AERDlg.cpp
AERDlg.h

Looking at these in SVN at e.g. [http://freedownload.svn.sourceforge.net/viewvc/freedownload/FDM/AERDlg.cpp?revision=8&view=markup](http://freedownload.svn.sourceforge.net/viewvc/freedownload/FDM/AERDlg.cpp?revision=8&view=markup) I can see that it's an MFC application. You need Microsoft Visual C++ to compile it.

On the very page that you mentioned in your original post, it says, "Operating System: Vista, Win2K, Win98, Microsoft Windows Server 2003, WinXP".

You are not going to be able to compile this natively on Linux. It might be possible to use Microsoft's compiler under Wine, I don't know. Google can probably help you on that.

---

### Post by Zugzwang on 2010-09-03
> **bulbmaker said:**
> I think source code is platform independent and it can be compiled on linux though its written on windows.


Here is the problem - your premise doesn't hold. In fact it is as follows: when you are writing some program and you only use libraries X,Y and Z, *and* do not do some quirky stuff *and* do not call some OS-dependent functions in your program but rather go through the libraries, *then* you can compile the source code to whatever platform the libraries X,Y and Z and the needed compiler is available.

However, the concrete source code you are having here is using some Microsoft library (MFC) that is only available for Windows. Thus you would need to reprogram the code in order *not* to use MFC in order to compile the program for Linux. But it's questionable whether that is worth the hassle.

---

### Post by bulbmaker on 2010-09-04
I think i understood y cant we compile. But, if we hav linux version of all the liabraries used in the source code, can we compile it?

---

### Post by spjackson on 2010-09-04
> **bulbmaker said:**
> I think i understood y cant we compile. But, if we hav linux version of all the liabraries used in the source code, can we compile it?
I am not aware of a linux version of Microsoft's MFC library. Good luck in your search for that.

---

