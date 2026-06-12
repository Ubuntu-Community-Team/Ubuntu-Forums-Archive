---
title: "Gnu"
date: 2007-10-30
forum: Programming Talk
---

### Post by Posterus on 2007-10-30
Hi, I'm currently running Ubuntu Gutsy Gibbon 7.10 on my alienware laptop and im also taking a course in C++,  unfortunately we are using the microsoft .net compiler.  Can anyone point me in the right direction to installing the GNU GCC compiler? I realize that this may be time consuming, im just asking if anyone knows a howto thread or website...I have done some searching but can not find clear instructions.

--Posterus

---

### Post by LaRoza on 2007-10-31
> **Posterus said:**
> Hi, I'm currently running Ubuntu Gutsy Gibbon 7.10 on my alienware laptop and im also taking a course in C++,  unfortunately we are using the microsoft .net compiler.  Can anyone point me in the right direction to installing the GNU GCC compiler? I realize that this may be time consuming, im just asking if anyone knows a howto thread or website...I have done some searching but can not find clear instructions.

--Posterus

```

sudo aptitude install build-essential

```

Not at all hard. Now use: ```
man g++
```

Also, look in the stickies. Look at: [http://ubuntuforums.org/showthread.php?t=554070](http://ubuntuforums.org/showthread.php?t=554070)

[note]gcc is installed, but you need to run the command anyway, to get everything else you need. For C++, use g++. It works like gcc, but is used for C++ programs. It is easy to use. Here is a little list of the commands:

First, open a terminal in the directory with you code. I am using "hw.cpp" as the source's name for these examples.

to compile and link:
```
g++ hw.cpp
```
^This will compile the source and make an executable file named "a.out", run it with "./a.out".

```
g++ hw.cpp -o hw
```
^This will do the same, but name the executable file "hw", run with "./hw".

to compile, but not link:
```
g++ -c hw.cpp
```
^This will compile the source into an object file named "hw.o". Do this for libraries.

to compile and link multiple files:
```
g++ hw.cpp hw.o
```
^This is assuming you compiled, and not linked a file named "hw.o", and have the source in a file named "hw.cpp". You can specify more files also.

There are other switches, use "man gcc" to read them all.

---

### Post by j_g on 2007-10-31
Um, you're not coding in C# or Visual Basic, are you? If so, you do realize that the GNU compiler doesn't compile these languages?

---

### Post by jespdj on 2007-10-31
> **j_g said:**
> Um, you're not coding in C# or Visual Basic, are you? If so, you do realize that the GNU compiler doesn't compile these languages?
> **Posterus said:**
> Hi, I'm currently running Ubuntu Gutsy Gibbon 7.10 on my alienware laptop and im also **taking a course in C++**,  unfortunately we are using the microsoft .net compiler.
.

---

### Post by Posterus on 2007-12-03
> **jespdj said:**
> .

thank you for saving me some time haha

---

### Post by Wybiral on 2007-12-03
Be careful... Not all C++ code that compiles in G++ will compile in MS. You'll definitely want to check before you turn in any work.

---

### Post by Posterus on 2007-12-04
> **Wybiral said:**
> Be careful... Not all C++ code that compiles in G++ will compile in MS. You'll definitely want to check before you turn in any work.

yeah i noticed that, thanks tho:)

---

### Post by Posterus on 2007-12-04
> **LaRoza said:**
> ```

sudo aptitude install build-essential

```

Not at all hard. Now use: ```
man g++
```

Also, look in the stickies. Look at: [http://ubuntuforums.org/showthread.php?t=554070](http://ubuntuforums.org/showthread.php?t=554070)

[note]gcc is installed, but you need to run the command anyway, to get everything else you need. For C++, use g++. It works like gcc, but is used for C++ programs. It is easy to use. Here is a little list of the commands:

First, open a terminal in the directory with you code. I am using "hw.cpp" as the source's name for these examples.

to compile and link:
```
g++ hw.cpp
```
^This will compile the source and make an executable file named "a.out", run it with "./a.out".

```
g++ hw.cpp -o hw
```
^This will do the same, but name the executable file "hw", run with "./hw".

to compile, but not link:
```
g++ -c hw.cpp
```
^This will compile the source into an object file named "hw.o". Do this for libraries.

to compile and link multiple files:
```
g++ hw.cpp hw.o
```
^This is assuming you compiled, and not linked a file named "hw.o", and have the source in a file named "hw.cpp". You can specify more files also.

There are other switches, use "man gcc" to read them all.


Thank you so much LaRoza, I finally got around to doing this, very helpful little tut :)

--Posterus

---

### Post by SOULRiDER on 2007-12-04
I ahve the smae problem that you do. what I did was install VirtualBox and then use Visual Studio.

---

