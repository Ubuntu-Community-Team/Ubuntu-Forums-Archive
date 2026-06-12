---
title: "Simple Cmake question."
date: 2011-07-20
forum: Programming Talk
---

### Post by Jonas thomas on 2011-07-20
I'm looking at this project
[https://github.com/Heeks/heekscad/blob/master/CMakeLists.txt]("https://github.com/Heeks/heekscad/blob/master/CMakeLists.txt")

There is a bin directory that gets created when I generate a code blocks project file using cmake.

I need to understand the point this directory is created since I need to create some symlinks for some pngs...
There is nothing obvious on where this bin gets created... Does this just automatically happen?

[Edit.  I was missing something Exceeding obvious...]
I was assumed that cmake magically created the /bin directory (seemed like a good theory at the time and something I should test a bit on before I post for help).
No such thing...
At the bottom of the CMakeLists.txt there is a line.

> #---------- put subdirs down here so that the package version vars above are visible to them -----------
add_subdirectory( interface )
add_subdirectory( tinyxml )
add_subdirectory( sketchsolve/src )
add_subdirectory( translations )
**add_subdirectory( src )  #needs libraries from other subdirs, so it goes last**


This invokes causes the CMakeList.txt in heekscad/src to execute which contains the line
install( TARGETS heekscad DESTINATION bin )

Because I'm generating a codeblock cbp at this point with cmake, I think it just creates the bin file and doesn't populate...
(I think.... need to test but got to go to the day job)

---

