---
title: "gcc compiling error for c"
date: 2009-10-03
forum: Programming Talk
---

### Post by jessiebrownjr on 2009-10-03
Moderator please fix this to all variants please, incorrectly put "solved"


hey guys! I'm on my trek to learn c now that I've got a decent handle on Linux.

I'm having a heck of a time trying to make the normal hello world program compile and run... These are basically the errors I keep getting, no matter what program I save it under.

This is with the standard code just copy and pasted into gedit, or any other IDE. 

fml.c: In function &#8216;main&#8217;:
fml.c:4: error: stray &#8216;\342&#8217; in program
fml.c:4: error: stray &#8216;\200&#8217; in program
fml.c:4: error: stray &#8216;\234&#8217; in program
fml.c:4: error: &#8216;Goodbye&#8217; undeclared (first use in this function)
fml.c:4: error: (Each undeclared identifier is reported only once
fml.c:4: error: for each function it appears in.)
fml.c:4: error: &#8216;cruel&#8217; undeclared (first use in this function)
fml.c:4: error: expected &#8216;)&#8217; before &#8216;world&#8217;
fml.c:4: error: stray &#8216;\&#8217; in program
fml.c:4: error: stray &#8216;\342&#8217; in program
fml.c:4: error: stray &#8216;\200&#8217; in program
fml.c:4: error: stray &#8216;\235&#8217; in program
jessie@ubntu:~/prog/c/learn$ 

when I type this $ gcc -v, this is what I see.

jessie@ubntu:~/prog/c/learn$ gcc -v
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu 4.3.3-5ubuntu4' --with-bugurl=file:///usr/share/doc/gcc-4.3/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --with-gxx-include-dir=/usr/include/c++/4.3 --program-suffix=-4.3 --enable-clocale=gnu --enable-libstdcxx-debug --enable-objc-gc --enable-mpfr --enable-targets=all --with-tune=generic --enable-checking=release --build=i486-linux-gnu --host=i486-linux-gnu --target=i486-linux-gnu
Thread model: posix
gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) 

Not sure what to do.. when I try to use an IDE as well thats made for programming, it compiles weird.. am  I missing something..?

this is the code.

#include <stdio.h>
int main()
{
printf(&#8220;Goodbye, cruel world! \n&#8221;);
return(0);
}

---

### Post by Bachstelze on 2009-10-03
> **jessiebrownjr said:**
> 
#include <stdio.h>
int main()
{
printf(“Goodbye, cruel world! \n”);
return(0);
}

You must put ASCII double-quotes ("), not “”.

---

### Post by dinxter on 2009-10-03
watch out for the double quotes when you cut and paste from documents/web pages, you can easily find you've got a &#8221; instead of a " :)

---

### Post by jessiebrownjr on 2009-10-03
So simple and so hidden to the naked eye, thanks guys!

Ok now I have tried using ' x1, and x2 in diff spots, and keep getting wonkey errors... Sigh :-)

They atleast are smaller though lol

---

