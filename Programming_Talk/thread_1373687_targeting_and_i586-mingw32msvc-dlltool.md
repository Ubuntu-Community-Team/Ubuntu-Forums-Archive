---
title: "targeting and i586-mingw32msvc-dlltool"
date: 2010-01-06
forum: Programming Talk
---

### Post by leblancmeneses on 2010-01-06
queston 1)
makefile below
[php]
mytarget:
    # use platform archiver utility to create library.
    if [ "$PLATFORM" = "WIN32" ] 
    then
        i586-mingw32msvc-dlltool -e exports.o -l library.lib $(OBJ) 
        $(CXX) $(OBJ) exports.o -o library.dll
    else
        ar rvs library.a $(OBJ)
    fi
[/php]
the problem is the shell conditional is spread out on multiple lines and is causing the interpreter to fail with syntax errors..  The solution would be to use semicolons and backslashes but I don't have a good reference on how that should be accomplished with a similar problem.

anyone know how this should look in my makefile?


question 2)
also the goal is to create a dll for windows from my ubuntu box.
$(CXX) is set to i586-mingw32msvc-c++
would library.dll result from this command?

thanks

---

