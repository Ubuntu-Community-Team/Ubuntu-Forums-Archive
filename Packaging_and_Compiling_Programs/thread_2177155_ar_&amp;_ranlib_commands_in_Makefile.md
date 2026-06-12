---
title: "ar &amp; ranlib commands in Makefile"
date: 2013-09-27
forum: Packaging and Compiling Programs
---

### Post by EricDallal on 2013-09-27
I have inherited a fairly large programming project from people who have graduated. So far, I've been able to keep the same structure and make small modifications (for example, when adding new functions) without understanding everything in the Makefile, but there are a few lines that I don't understand:

umdes.a: ${LIB_OBJS}
	ar cr umdes.a ${LIB_OBJS}
	ranlib umdes.a

acc: acc.o umdes.a
	$(ECC) $(CFLAGS) -o acc acc.o umdes.a

What I do understand is as follows: the umdes.a target requires compilation of all of the elements of the list LIB_OBJS (oddly enough though, this is a list of .o files which don't have any rules for compilation). Also, the acc target requires compilation of acc and depends on the umdes.a target being performed first (it does seem circuitous to me that acc requires acc.o though). I also think that I understand that the file acc will comprise the acc.o and umdes.a files.

What I don't understand is the ar and ranlib commands. This is especially problematic now, since this program is supposed to be compiled for Ubuntu, Mac, and Windows. Compilation in Ubuntu and Mac works fine with the Makefile, but compilation in Windows fails. I've tried downloading cygwin, but it fails on the ar command. There are old .vcproj files in the same directory as the .c source files and this apparently was the way by which compilation in Windows used to be done. However, for some reason this now fails with inexplicable compilation errors in newer versions of Visual Studio (even more oddly, all compilation errors occur only in functions that I have modified, but which compile perfectly in Ubuntu).

Is there any way to run the Makefile in the Windows environment? Is there some way to simulate this (my little understanding of ar and ranlib seems to suggest that this is akin to creating a library of functions and linking them to the other files, suggesting something akin to a Windows DLL) in Windows?

Any help would be greatly appreciated.

---

