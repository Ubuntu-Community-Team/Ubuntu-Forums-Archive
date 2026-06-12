---
title: "Setting up Eclipse for C++"
date: 2006-08-26
forum: Programming Talk
---

### Post by [K]eep[A]way on 2006-08-26
Hi,

I'm a new Ubuntu user, and I want to be able to program C++ in Eclipse.  Can someone walk me through the steps?  I'm doing something wrong and I figure it would be best to just start from scratch.  I know I have to have the GNU C++ compiler (g++) and install GNU Make, and install Eclipse.

Thanks in advance.

---

### Post by neilp85 on 2006-08-26
Why not just use something like Anjuta for your C++ IDE. The last time I tried the C++ plugins it brought eclipse to a crawl. That was a while ago so maybe they've gotten better but I wouldn't count on it.

---

### Post by jjtechno on 2006-08-26
I have tried CDT and it runs incredibly slowwww. Use Anjuta for c++ IDE,
or install the CodeBlocks.deb package from Berlios.de(I use this one personally for a c++ class at school.)
The Eclipse project has a long way to go yet with c++.
my 2 cents worth

---

### Post by [K]eep[A]way on 2006-08-27
Thanks guys, but I *have* to use Eclipse.  I have to submit projects for school through a plugin, which submits my project to an automatic grader.  I also have to use CxxTest, which creates test cases for C++ classes (this is also an Eclipse plugin).  Could you please just walk me through the steps?  Or I could continue developing under Windows.

---

### Post by Keffin on 2006-08-27
Installing the "build-essential" package should give you everything you need to compile C/C++ code (which is more than just g++ and make), then it should just be a case of downloading eclipse and the cdt plugin and following the instructions. If you haven't already, I would reccomend installing Suns Java from the repositories ("sun-java5-jdk" I think) and the eclipse/CDT from their official sites.

---

### Post by [K]eep[A]way on 2006-08-27
Thanks! I'll try that.

---

### Post by sturnira on 2006-09-02
Hey guys,

I am having a similar problem: I have to use Eclipse and I downloaded Eclipse cdt. Now, how do you add this to the GUI menu in the "Applications" dialog? I already had Eclipse SDK and can't figure out a way to open the C++ Eclipse..

Thanks, 

S.

---

### Post by kaamos on 2006-09-03
Just open the c/c++ perspective in eclipse.

Window->Open perspective->Other->C/C++

---

### Post by KyleCF on 2011-03-08
Hi guys

I'm also having a problem with eclispe. Everything is set up (or so I thought), but every time I try to compile the IDE give me the error: "Error launching external scanner info generator (g++ -E -P -v -dD /home/user_name/documents/workspace/.metadata/.plugins/org.eclipse.cdt.make.core/specs.cpp)".

Any advice would be appreciated.

---

### Post by stchman on 2011-03-08
> **KyleCF said:**
> Hi guys

I'm also having a problem with eclispe. Everything is set up (or so I thought), but every time I try to compile the IDE give me the error: "Error launching external scanner info generator (g++ -E -P -v -dD /home/user_name/documents/workspace/.metadata/.plugins/org.eclipse.cdt.make.core/specs.cpp)".

Any advice would be appreciated.

Install the build essential package.  Without this, you won't have all the libraries needed.

```

sudo apt-get install build-essential

```

How did you install eclipse for Ubuntu?  The C/C++ Eclipse is not available in the repositories AFAIK.

---

