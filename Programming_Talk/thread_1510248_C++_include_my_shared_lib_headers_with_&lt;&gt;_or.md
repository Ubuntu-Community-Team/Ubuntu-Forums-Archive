---
title: "C++: include my shared lib headers with &lt;&gt; or &quot;&quot;?"
date: 2010-06-15
forum: Programming Talk
---

### Post by FalFire on 2010-06-15
Hi,

In the various files of my C++ shared library project I always included other files of the same project by using #include "subdir/file.h". I just changed all these include directives to #include <mylib/subdir/file.h> because I thought that was the way to do it. However, now everytime I try to compile my library it cannot find any of those files, which doesn't surprise me because they're not installed yet as I just changed the directory structure of my project.

What is the correct way to do this? Do you include files inside the same project using "" and headers files of other, installed libraries using <>?
I looked into the source code of some open source projects and they seem to include all files with <> as well, so I think this should be possible too?

---

### Post by dwhitney67 on 2010-06-15
Use the <> brackets.

Then inform GCC where to find the header file(s) and the library using the -I (uppercase eye) and -L (uppercase ell) options, respectively.

P.S. Consider installing your header file(s) and library relative to /usr/local.  For example, /usr/local/include for your headers, /usr/local/lib for your library.

---

### Post by FalFire on 2010-06-15
I'm afraid I'm not sure what you mean.
I created my project using Anjuta, and the Makefile should be correct, assuming Anjuta created it correctly. I am installing my library in /usr/local/lib and the headers in /usr/local/include.

In Anjuta I can specify multiple options: C compiler flags, C preprocessor flags, C++ compiler flags, Linker flags, Libraries, and Dependencies. Where should I put the options you mention, and exactly what values do I pass them, assuming my project working directory is /home/user/project with the sources in /home/user/project/src ?

EDIT: I tried the -I option and it didn't work, and I think I know why: my project dir containing the sources is /home/user/project/src, but I am including all my header files with <mylib/subdir/file.h>. The "mylib" prefix, which is the folder in /usr/local/include in which my headers are installed, doesn't match the "src" dir in my project root. How do I solve this? This must be a common situation, or am I doing something wrong?

---

### Post by dwhitney67 on 2010-06-15
The short answer is to stop using Anjuta until you have learned to build your projects from the command line, perhaps even going as far as creating your Makefiles.

I'm sure Anjuta, being that it is a GUI, has a Help button on the upper-right corner of the window.

You need to figure out how to specify the base directory where your header files reside.  Thus if you have headers in /usr/local/include/mylib AND you are including them has <mylib/subdir/file.h>, then your base directory is /usr/local/include.

As for linking, your library probably exists in /usr/local/lib as libmylib.so (or libmylib.a).  You'll need to tell Anjuta to refer to that directory to find your library.  Or update ldconfig as appropriate to include it in the library cache.

If any of what I have stated above is too "advanced" for you, then IMO, you should not be using Anjuta or any other IDE.  Learn the basics; then later, if you wish, let the IDE replicate your knowledge.

---

### Post by FalFire on 2010-06-15
You're absolutely right and normally I would have read all the manuals/tutorials etc. until I understand it all 100%, as I hate working with things I don't understand, but this is my first C++ project and right now I just don't have the time to learn all those things when an IDE can (more or less) do it for me. I just need to finish this project in time, and then I'll be able to read up on those things.

Having said that, I think you misunderstood me (or I am misunderstanding you). I am _creating_ a shared library, not using one, and I am trying to build it (not yet install it). The problem is that I am working on my shared library in the directory /home/user/project, and I will later want to install it to /usr/local/lib. Therefore, for example in file A of my shared lib, I include file B of my shared lib like this: #include <mylib/file_b.h>. This because it will be installed in /usr/include/mylib/file_b.h. However, I am trying to build it in my working directory which I mentioned above, and file B is currently in /home/user/project/src/file_b.h and not yet in the location I specified in the include directive in file A. This is something I don't yet fully understand, how do I build it without having the compiler complain about not being able to find those files?

I hope this makes sense, I am rather tired at the moment.

---

### Post by dwhitney67 on 2010-06-15
You compile your library relative to where the source code exists now, not where it will exist later.

Thus don't worry about the /usr/local/include (or /usr/local/lib) at this stage.  These locations should be relevant to the person (or even you) who use the library for a separate project.

Thus in a library I have worked on before, I used the double-quotes to include header files that pertained to the library, not the <> brackets.

All of my header files where located in one directory, but you can define them in multiple directories if you wish.

Say for instance you have to include two header files, one located in subdir1, the other in subdir2:
```

#include "subdir1/Header1.h"
#include "subdir2/Header2.h"

#include <iostream>
#include <string>

// etc

```
In this case, when you compile your C++ module (the .cpp), you need to tell the compiler where to locate subdir1 and subdir2.  If your module is in subdir3, then the path you care about is merely "..".

If you do not wish to specify the specific sub-directory in your include statements, then you would need to inform GCC of each sub-directory where your headers are located at.  For example, if the code looks like:
```

#include "Header1.h"
#include "Header2.h"

#include <iostream>
#include <string>

// etc

```
Then GCC would need to know about "../subdir1" and "../subdir2".

For now, get Anjuta setup so that you can compile your source code and create the shared-object library.

Then worry about installing it (preferably using /usr/bin/install) into /usr/local, with headers in one directory (ie. include) and the library in another (ie. lib).

---

### Post by FalFire on 2010-06-15
Thank you for your replies, I really appreciate it.
So, to summarize, if I understand correctly, I should NOT use <> to include files from the same project, but "".

Thanks again!

---

### Post by dwhitney67 on 2010-06-15
> **FalFire said:**
> 
So, to summarize, if I understand correctly, I should NOT use <> to include files from the same project, but "".


Yes, at least according to "my" standards.  Others may opt to use the <> brackets.  It is really up to the developer.  Some believe that the double-quotes should only be used when the header file is in the same directory as the source-code module.  I don't buy that; I use the "" for project related header file(s), and <> for external library header file(s).

I also make it a habit to always list my project header files before external header files.

---

