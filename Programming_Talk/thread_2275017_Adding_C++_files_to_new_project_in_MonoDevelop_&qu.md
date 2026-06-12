---
title: "Adding C++ files to new project in MonoDevelop: &quot;Object reference not set&quot;"
date: 2015-04-23
forum: Programming Talk
---

### Post by IZavorin on 2015-04-23
I just installed Ubuntu 14.04.2 64bit on a desktop and then installed MonoDevelop 4.0.12 to try building some old C++ and C# projects I copied from my Win 7 machine. I tried to load a VS2010 solution that included a C++ project and a C# project. It loaded the latter but gave me some error message about the project file for the former.

So, since the C++ project has just a handful of files, I decided to rebuild it from scratch. So I created a new C++ console project and then added the .cpp, and .h files and one .txt file to it. When I clicked the txt file to view it it opened fine. When I clicked on any .h or .cpp file, I got "Object reference not set to an instance of an object". Same problem when trying to build the project.

The files appear to be just fine when I view them in vi. I checked permissions and they are fine and I also had to dos2unix them since they were all in the DOS format. I did all that before adding the files to the new project.

Is the MonoDevelop install that I have somehow incomplete or corrupt? Or am I doing something wrong here?

Thx

---

