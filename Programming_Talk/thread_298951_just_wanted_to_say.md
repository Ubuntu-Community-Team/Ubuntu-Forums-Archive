---
title: "just wanted to say"
date: 2006-11-13
forum: Programming Talk
---

### Post by taelatus on 2006-11-13
Just wanted to make some comments for once instead of asking a question.  I'm using Ubuntu to do most of my programming assignments right now.  That fact alone solidifies Ubuntu as an OS I plan on using for quite a bit longer.  It's wonderful that I'm finally able to be productive with Linux instead of just toying with it and saying "Yea I could use this if I had to."  I'm currently using gedit + bash terminal to do my code.  I really want to use Anjuta but I haven't figured out how to use the damned debugger yet.  That said, I wish there was an IDE available in Linux that was as nice as VS.NET.  I guess the only thing holding me back (from using Linux 100% of my time) at this point is that I still have an upcoming project that requires me to use VS.NET 2k5.  I love VS but I can't use it in Linux. :(

---

### Post by mark_g on 2006-11-13
Ever checked out Eclipse and IntelliJ? Both have their pros and cons, but they're overall really great IDEs.
I'm glad we don't have to us VS at school anymore. It looks nice and has some good features, but overall all the mouse clicking in that IDE really makes my arm tired. They really ought to make a vi-emulator for VS2005. :-k

---

### Post by taelatus on 2006-11-13
To my knowledge, Eclipse is a Java IDE.  I just looked up IntelliJ and it's also a Java IDE.  My main concentration right now is C++ as that is what all my assignments are based in.

---

### Post by std on 2006-11-13
Eclipse is an extensible IDE, meaning that you can use it with C++ (there is a set of plugins for working with C++).

I tried it a while ago and I did like it (at least in general terms). I'm still stuck with emacs (I learned to program on a text terminal so I still have these reminiscences...), but found Eclipse to be quite straightforward.

As for Anjuta, I did try to give it a few chances but I always failed around the same things I failed with KDevelop (i.e. horrible UI design, I never managed to find what I wanted).

Anyway. Bottom line, Eclipse can be used with C++, and it's good at it.

---

### Post by Angry on 2006-11-13
I had found that the Anjuta IDE was strange/difficult to work with.  That is to say, I probably wasn't using it in the manner *they* (the Anjuta developers) had in mind.  For example (this is not a verbatum of the actual process, but it feels like it):

Trying to add a file to the project was a pain: "New file" would create a new document, but not create an actual file on disk(or something like that);
Would then have to "Save as", but then proceed to "Add file to project", but header file extensions would forcibly be .hpp;
In addition, it would place header files in a "Header" folder and source files in a "Source" folder, thus requiring a relative "..\myheader.hpp" path.

All in all, I quickly learnt how to use the command line with makefiles, and gedit as the editor.  Which is a shame really, all I want from an IDE is file and compiler/linker management, anything else is just icing.  However, when an IDE tries to do the "icing" first, it just gets in the way.

Now, having said all that - if you are 'required' to use VS2005, then you are probably stuck with VS2005.  Since an IDE is just file/compiler management, I can only assume this requirement is for the professor to double-click your solution file and check out your work in an organized manner (versus a directory of all your source code).  And with that, any other IDE you choose to use would probably be moot, as VS2005 will only recognize other VS projects/solutions.

---

### Post by hod139 on 2006-11-13
[Codeblocks]("http://www.codeblocks.org/") is a new crossplatform C/C++ IDE that i have been using lately.  It is still in active development, but the nightly builds are quite stable.  They also provide ubuntu debs on the nightly builds.

---

### Post by taelatus on 2006-11-13
I'm almost glad that everyone else is having troubles or dislikes while using Anjuta.  It makes me feel less incompetent for not being able to figure it out.  Also, I said I was required to use VS.NET 2k5 but this may not actually be the case.  It was originally an assumption by me but I looked over all my class definitions again and there is no platform specific code.  To my knowledge, it's all code that is included in the standard library so I'm checking to make sure the prof won't mind me turning in a folder full of source code at the end of December.

I will be checking out Eclipse and Codeblocks in that order.  Hopefully they will be easier to use than Anjuta.

---

### Post by sweemeng on 2006-11-13
just wanted to say that, ide is never an integral part of software development in unixes in general. so what you see here not strange. where as in windows, the ide helps code completion. but not so in linux. 

in fact. it is not strange for people here uses emacs or vi to code. on the positive side. the harder it goes, the better coder you are.

eclipse is a ide development tools, uses java, but have develop into those for php,perl,python. and in c++ you need cdt(or is it in other name?).

---

