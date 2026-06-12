---
title: "using * as part of an argv in C++"
date: 2009-07-12
forum: Programming Talk
---

### Post by swappo1 on 2009-07-12
Hello,

I have a program where I search a directory tree for all files of a certain type. For example, the program takes three arguments:
```
$./myprog /my/path *.cpp
```
When I print out the third argument, argv[2], I am getting find1.cpp rather than *.cpp.  The third argument is to be used as a comparison to find all files with .cpp.  I am assuming the *.cpp is finding the first file with .cpp and using that as the argument?  Is there anyway around this other than using a different character?

---

### Post by Finalfantasykid on 2009-07-12
This isn't really a very pretty way of doing this, but if you used  "*.cpp" as your argument, would it not pass it correctly?  Or at the very least it would pass it with the quotes, but the asterisk would still be there, and if that is the case you would just need to get rid of the quotes in your program.

This would at least be a quick work around so that you can work on the rest of the program until someone else comes up with a better solution.  Sorry I'm not a very proficient c/c++ programmer :P

---

### Post by swappo1 on 2009-07-12
> This would at least be a quick work around so that you can work on the rest of the program until someone else comes up with a better solution.
I'm using ^.cpp as my work around for the time being.  Hopefully somebody knows of a line of code to use * as a character in an argument.

---

### Post by Habbit on 2009-07-12
The problem is not C++, but the shell. "*" is a glob character for sh, and when it sees * in an expression it is parsed and expanded to its value. Thus, *.cpp would expand to the names of all files that end in .cpp in the current directory. In order to pass a literal asterisk to a program you need to quote it as Finalfantasykid suggested. Either single or double quotes will do.

Just to remark it, this is not a problem with your program. The same would happen if you wanted your application to receive some string like $name in argv - you would need to write "myapp '$name'" or "myapp \$name" to get the shell to send it in literally instead of substituting it with the value of the "name" shell variable. This also happens in the Windows shell (cmd.exe) with their own variable notation %name%, though not with * or ? because cmd does not care about them.

---

### Post by ibuclaw on 2009-07-12
It isn't your program's fault. It's the **shell** that loads the application/preps the input arguments.

A workaround would be to use an escape character:
```
./myprog /my/path \*.cpp
```
Although why you would want this is beyond me. If you are looking for an **ls** style behaviour, then you should work with this feature, not against it.

Regards
Iain

---

### Post by monraaf on 2009-07-12
You'll have to put it in quotes otherwise it's subject to shell expansion.

---

### Post by MadCow108 on 2009-07-12
you can disable pathname expansion with set -f (reset with set +f)

---

