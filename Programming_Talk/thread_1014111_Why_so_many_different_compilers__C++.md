---
title: "Why so many different compilers? :: C++"
date: 2008-12-17
forum: Programming Talk
---

### Post by animefan82 on 2008-12-17
Just as the title says. Why are there so many different C++ compilers out there, and what kind of difference do they make? I mean, PHP, VB, C# and Java all have one compiler (as far as I know) (and php is browser based, isn't it? kinda pointless to list it then? :p), so why is it that there are so many different compilers for C++? Even worse, the code written in one compiler is unaccepted in another... Answers appreciated as much as discussions amongst yourself.

---

### Post by wmcbrine on 2008-12-17
There are in fact several Java compilers, although Sun dominates. PHP is open source, so there hasn't been any great motivation for alternative implementations; plus I think it's lacking in the formal specifications area. VB and C# are Microsoft-centric, although there are some alternatives there, too. And all these languages are relatively young.

But C is nearly four decades old. C++ is newer, but still older than all the others you've listed. They started life as proprietary, and grew open specifications, which led to new implementations, both proprietary and open.

There are other reasons, too. But the history of the way they were developed is the main one, I think.

---

### Post by slavik on 2008-12-17
> **animefan82 said:**
> Just as the title says. Why are there so many different C++ compilers out there, and what kind of difference do they make? I mean, PHP, VB, C# and Java all have one compiler (as far as I know) (and php is browser based, isn't it? kinda pointless to list it then? :p), so why is it that there are so many different compilers for C++? Even worse, the code written in one compiler is unaccepted in another... Answers appreciated as much as discussions amongst yourself.

When you say many? How many do you mean?

---

### Post by Luggy on 2008-12-17
Why are there multiple C++ compilers? Well why are there multiple text editors, music players and CD burning applications?

FLOSS or commercial, there will always be more than one flavour of software package because developers are either trying to make a buck with a competing project or that the project itself is better.

---

### Post by Cracauer on 2008-12-17
Myself, I don't use languages that only have one implementation. The moment that the owner decides to go berserk with future directions you are screwed. It's better with OpenSource, of course, but modern languages are complex enough that it's not really that great either.

It's one major reason I don't like the usual scripting languages, perl, python, ruby. I'd rather have one language definition that people argue over and multiple implementations.

---

### Post by wmcbrine on 2008-12-18
Well, there *are* multiple implementations of Python...

---

### Post by aszxcv on 2008-12-18
i agree with those saying everyone likes their own favor/implementation

---

### Post by dribeas on 2008-12-18
There are not that many C++ compilers out there. There are more IDEs than compilers anyway. In the linux world you have either g++ or intel compilers. The difference is that g++ is open while intel compiler is proprietary and a little better in optimizations for the intel architecture.

If you move out of linux, g++ is available for most platforms. Most platform vendors provide their own compiler system (solaris/ms visual studio,...) while some just depend on gcc (macosx). In some platforms IDE vendors provide their own compiler (borland) and some depend on external compilers (codeblocks/eclipse/netbeans).

Now on the possible reasons. GCC, it is THE opensource compiler, and the standard de facto compiler for many platforms. Intel compiler is tailored for their own processors and generates faster code by using specific processor instructions and knowledge. Each OS vendor must either depend on GCC (now that it is widely available) or they had to provide their own set of compilers, or else they would not be able to compile for that platform (this explains IBM compilers, Sun compilers, Visual Studio). IDE vendors like Borland, Metrowerks could not depend on other vendors compilers (until gcc was available) as they were not free (not just open, but free as in free beer) so they provided their own compilers.

Now, since there are different implementations, each one tries to comply with the C++ standard in as much as possible or desired by the vendor, and some extensions are provided. They are not fully compatible since none of them (with a honorable exception, read below) completely fulfills the standard, and moreover non standard extensions available in one compiler may not be available in others. That is, they are not compatible in those parts that are not standarized or where the compiler does not follow the standard.

There is one last category, defined by one compiler in itself: comeau. Their compiler is not really a compiler in itself, but more of a code translator with one focus in mind: the standard.

Now, this is not just a C/C++ situation, it is the same with many other languages. LISP has many interpreters, not only that, it has many dialects. Java has different compilers and interpreters (including gcj from GNU and IBM compiler set). C# has Microsoft and Mono compiler and VMs.
Name a language and you will surely find alternative compilers that fit a particular purpose.

---

### Post by directhex on 2008-12-18
> **dribeas said:**
> Name a language and you will surely find alternative compilers that fit a particular purpose.

And more importantly, a single-source compiler is BAD. It's a RISK. What if the company or people behind it get bored & stop? Or change things in a breaking way without consultation?

---

### Post by SeanHodges on 2008-12-18
Most popular languages have at least a few alternative compilers:

Java:
- [GCJ]("http://gcc.gnu.org/java/")
- [Jikes]("http://jikes.sourceforge.net/")

PHP:
- [Roadsend]("http://www.roadsend.com/home/index.php?pageID=compiler")
- [phc]("http://www.phpcompiler.org/")

VB:
- [Envelop]("http://www.freebyte.com/programming/compilers/envelop.html")
- [GAMBAS]("http://gambas.sourceforge.net/") (includes a compiler)

Just like everything else in the computing world, there is always an alternative. The lesser-known compilers may appear pointless on first glance, but you can be sure that the author(s) didn't spend potentially years writing a complete implementation if there wasn't a good reason for it. As far as what that reason is, it varies (better performance, better integration with other software, better compatibility with other platforms...) - You'd have to go to the website and perhaps contact the developers to find out.

PHP can be used locally as well as for Web-based solutions. A common approach is to write a PHP script and run it using the "php" program.

---

### Post by jespdj on 2008-12-18
> **animefan82 said:**
> Why are there so many different C++ compilers out there, and what kind of difference do they make?
Are you confusing "compilers" with development environments (IDEs)?

On Linux, g++ (the GNU C++ compiler) is used almost everywhere. There's also a C++ compiler from Intel (which is very good and produces faster code than g++, but which isn't free).

There are lots of editors and IDEs but almost all of them use the g++ compiler to compile your C++ source code.

---

### Post by directhex on 2008-12-18
> **jespdj said:**
> There's also a C++ compiler from Intel (which is very good and produces faster code than g++, but which isn't free).

A couple of other fast, non-free compilers for your list: PGI compiler suite; Pathscale (QLogic) compiler suite, IBM XL compilers (PowerPC-only)

---

### Post by cb951303 on 2008-12-18
well the languages you listed are not compiled to machine code. they are interpreted languages but I'm not sure if this affects the number of compilers for these languages :P

And I don't think there are too many C++ compilers. Only free mature cross-platform one is G++. So it's kinda unrivaled for me :)

---

### Post by nvteighen on 2008-12-18
Hmm... C++ has different compilers because it is an open specification. And also an ISO standard. That ensures the language is nobody's, but a language on its own. You can be 100% sure that any standard compliant compiler will accept any standard compliant C++ code, being the extensions the only possible backfire.

---

### Post by rchrd on 2008-12-18
Sun Studio compilers and tools are also available on Ubuntu (and OpenSolaris), and includes C, C++, and Fortran 2003 compilers, debugger, performance analyzer, and an optimized math library. And because they don't advertise, most people don't know about it. Its industrial strength compilers are standards conforming. And the IDE is based on NetBeans 6.5. 

The compilers support OpenMP 3.0 for shared-memory multi-core parallelization, as well as automatic parallelization. And there's a thread analyzer for finding race conditions in parallel code.

And it's a free download. (But it's not yet on the Ubuntu repository, so you would need to download the tarball installer).

I use it all the time. It's great.

Download: [http://developers.sun.com/sunstudio/downloads/express/index.jsp](http://developers.sun.com/sunstudio/downloads/express/index.jsp)
Full info: [http://developers.sun.com/sunstudio](http://developers.sun.com/sunstudio)
Comments about using it on Ubuntu and other Linuxes:
[http://wikis.sun.com/display/SunStudio/Using+Sun+Studio+on+Linux](http://wikis.sun.com/display/SunStudio/Using+Sun+Studio+on+Linux)
[http://wikis.sun.com/display/SunStudio/Linux+Topics](http://wikis.sun.com/display/SunStudio/Linux+Topics)

And: [http://blogs.sun.com/rchrd/entry/because_i_can_sun_studio](http://blogs.sun.com/rchrd/entry/because_i_can_sun_studio)

---

### Post by animefan82 on 2008-12-30
> **jespdj said:**
> Are you confusing "compilers" with development environments (IDEs)?

No, I meant compilers as what they are. Interpreting source code into, what is it, machine code? But not IDE's, no. More on this on my next post.

---

### Post by animefan82 on 2008-12-30
> **Luggy said:**
> Why are there multiple C++ compilers? Well why are there multiple text editors, music players and CD burning applications?

FLOSS or commercial, there will always be more than one flavour of software package because developers are either trying to make a buck with a competing project or that the project itself is better.

text editors have the purpose of editing text. Agreed.
Music players have the purpose of playing files. Agreed.
CD burnes have the purpose of burning CD/DVD's. Agreed.

however, this is like comparing IDE's, which wasn't part of my question. Any media player (as far as I know) that you find will be able to play mp3-files, or wave.
My point in question was rather the interpretation of source code (which reminds me I'd forgotten about the other Java compilers, since I've mainly just used Sun's javac to compile). They all compile from the same source code though, which is not the case with C++. That, I found weird, since you'll actually have to change some things, depending on the compiler's way of interpreting. 

Source code compiled with g++ may have to be changed if compiled with MinGW, or with microsofts compiler. That was the basis for my question, which now has been answered to some degree.

---

### Post by SeanHodges on 2008-12-30
> **animefan82 said:**
> My point in question was rather the interpretation of source code (which reminds me I'd forgotten about the other Java compilers, since I've mainly just used Sun's javac to compile). They all compile from the same source code though, which is not the case with C++.

Java source code often needs to be modified for different compilers as well. 

The Sun implementation has a slightly more comprehensive API than the OpenJDK implementation, for example. You have to extract any Sun-specific code in order for the code to compile in OpenJDK. The same goes for GCJ, to an even further extreme because it sacrifices some API to support more platforms than both Sun and OpenJDK (on top of the licencing issues).

This same anomaly can be seen in interpreted languages as well, e.g. supporting the Javascript engines in Mozilla, IE, and Chrome.

Language standards attempt to close the gap as much as possible, but it always has to play catch-up with the demand/supply of the market and the implementations.

---

### Post by jpmelos on 2008-12-30
> **animefan82 said:**
> Just as the title says. Why are there so many different C++ compilers out there, and what kind of difference do they make? I mean, PHP, VB, C# and Java all have one compiler (as far as I know) (**and php is browser based, isn't it? kinda pointless to list it then? :p**), so why is it that there are so many different compilers for C++? Even worse, the code written in one compiler is unaccepted in another... Answers appreciated as much as discussions amongst yourself.

I think you are confuing IDE with Compiler. They are different. Just in case, IDE stands for **I**ntegrated **D**evelopment **E**nvironment. NetBeans/Eclipse/etc are **NOT** compilers. They are IDEs and when you ask them to compile your code, they call the compiler (usually gcc in Ubuntu, unless you change it).

PHP is **NOT** browser based. Never was. Browsers do not receive any PHP code from servers. They only see HTML structures. When a page is called, the server interprets the PHP code (it is not compiled, it is interpreted) and, as asked in the PHP code, creates the dynamic HTML structure, or creates the cookie, or a variable and so on...

At least, as far as I know. Correct me if I'm wrong.

---

