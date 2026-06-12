---
title: "Managing an Open Source project using Git"
date: 2011-04-01
forum: Programming Talk
---

### Post by Spitted on 2011-04-01
Hello.

I'm fairly new to Ubuntu (and Linux in general) and I'm willing to start a small C++ project at home for educational purposes.

At work I use C++ extensively, though on Windows. The tools I use are CMake for configuring, Visual Studio as an IDE, and Subversion as source control.
For the this project, I want to try, for the first time, programming on Linux with Git.

So I learned Git and created a new project in GitHub, but then I realised I have a problem:
My project have some dependencies on other projects (specifically, libwiiuse and libwiiuse-dev which are found on Ubuntu repositories, WiiUseCpp which can be downloaded from the author's site, and a graphics library which I haven't yet decided on).
At work, I just put the dependencies at my project's repository (sometimes as svn externals), and make CMake configure everything to a single VS Solution.
If I would apply this method here, the repository's folder tree will look like this:
/wiiuse/
/wiiusecpp/
/graphics-library/
/myproject/
CMakeList.txt
README
etc...

And everything will be stored at GitHub which seems like a waste.
Other solution will be to somehow "declare" my dependencies so people would know they have to get them from Synaptics or whatnot before compiling my project. I think this is not that portable because installing the dependencies manually might not be that easy on all systems.

I realise this is a VERY common issue. I would like to know how this is solved most of the time and what is considered best practice. Also if you have any other tips regarding programming in Linux I will be grateful reading them.

Thanks
Eyal

---

### Post by Barrucadu on 2011-04-01
You will generally list your dependencies in a README file or something - it's up to whoever compiles your project / builds a package to resolve those dependency issues.

---

### Post by SledgeHammer_999 on 2011-04-01
> **Barrucadu said:**
> You will generally list your dependencies in a README file or something - it's up to whoever compiles your project / builds a package to resolve those dependency issues.

Exactly!

But if you want to pull the source of those dependencies in your source tree then you should look into "git submodule". I've seen people using it for keeping a local copy of a lib on which their project depends on. I, however, never used it, so I may be wrong.

---

### Post by Spitted on 2011-04-02
I see. 

Git submodule is not an option, unfortunately, because my dependencies don't have a git repository AFAIK.

Are there any cases when you would actually include the files to your project?
I just remembered OpenCV had a "3rdparty" directory, where they put stuff such as zlib and libpng. Does someone know about another example for this and maybe can tell when doing so is more appropriate?
I just thought, well, libwiiuse and libwiiuse-dev are currently easy to install since they are in the Ubuntu repositories, but it might not be that easy in other distributions or even in other OS. Moreover, WiiUseCpp is only found in the author's site as source, and one day this site can get down and never return (or the author could just stop supplying to code for some reason). 
Listing my dependencies and acting as if everyone can get them any time sounds pretty unsafe. Is this really the only method considered best practice or are there some people who do it differently? I would like to hear some opinions on this.

Thanks

---

### Post by SledgeHammer_999 on 2011-04-02
Your other option is to include the source manually in your source tree and then allow the person who builds your project to use the system-provided library and not your internal library.

Also, read the LICENSE of each dependecy it may not allow distributing.

---

### Post by eeperson on 2011-04-02
This is not something you should be handling with your version control tool.  Otherwise you can only use libraries that use the same version control (for the most part).

Instead, your build tool should be doing this.  Check out cmake's [external projects]("http://www.kitware.com/products/html/BuildingExternalProjectsWithCMake2.8.html").

---

