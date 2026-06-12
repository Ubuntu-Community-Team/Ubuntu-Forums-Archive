---
title: "Complier"
date: 2008-06-11
forum: Programming Talk
---

### Post by CPlusPunk on 2008-06-11
Just starting to programm with ubuntu. Any suggestions on a compiler? I write C# / C++. Thanks in advance for any suggestions.

---

### Post by KingTermite on 2008-06-11
For C++, the built in (once you install it) C/C++/Java/Fortran and a bunch of other languages compiler, gcc works just fine.

Install it with :
sudo apt-get install build-essential

THen you can compile from the command line with:
"gcc myfile.c" or "g++ myfile.cpp"

and it will create an executable file "a.out" which you can run using the current directory prefix "./a.out".

As for C#, I'm not sure. It's my fave language and I hear a lot of people talk about it, so I know there is a C# compiler out there.

---

### Post by CPlusPunk on 2008-06-11
Thank you very much I appreciate the help.

---

### Post by xlinuks on 2008-06-11
gcc is the C compiler
g++ the C++ one.
From my experience, learning C++ coming from Java I noticed:
Eclipse is the IDE of choice of many people, powerful, but is not (very) intuitive, sometimes requires you to do stuff which the IDE should take care of itself. It's in the Ubuntu repositories.
CodeBlocks is pretty nice. It's not in the Ubuntu repositories.
NetBeans is intuitive and easy to use but is (a bit) slow. I chose it cause I have a Java background and cause it comes with C++ support preinstalled. The version from the Ubuntu repositories is old thus it's best to get the latest one from the web.

---

### Post by KingTermite on 2008-06-11
Still no answer about a C# compiler.

Can anybody tell him (and me) what C# compiler options are out there?

I did a quick google and found one called "mono" and possibly something else called DotGNU.

What are the options for a C# compiler?
Are they in repositories?
Are there any GUI toolkits for C#?
Any thoughts on differences between them if there are more than one?

---

### Post by xlinuks on 2008-06-11
A quick google yields
> 
You have to pick one of:

    * mcs: compiler to target 1.1 runtime.
    * gmcs: compiler to target the 2.0 runtime.
    * smcs: compiler to target the 2.1 runtime, to build Moonlight applications. 
[http://www.mono-project.com/CSharp_Compiler](http://www.mono-project.com/CSharp_Compiler)
Have fun with dirt.

---

### Post by Phenax on 2008-06-11
I use MonoDevelop and  gmcs.

For C/C++ you can try the Intel C Compiler as well.

---

