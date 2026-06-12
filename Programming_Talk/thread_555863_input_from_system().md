---
title: "input from system() ??"
date: 2007-09-20
forum: Programming Talk
---

### Post by ant2ne on 2007-09-20
```
system("whoami | who | cut -c11-15 ");
``` is a nifty function.  But I want to put this information, not as screen output, but as a variable to be manipulated in my program.

---

### Post by Fixman on 2007-09-20
Just put on a file and read

```

#include <stdio.h>
#include <stdlib.h>

int main()
{
  system ("echo Hi > file") ;
  FILE *a = fopen("file", "r") ;
  char buf[3000] ;
  
  while (!feof(a)) fgets (a, buf, 3000) ;
  puts (buf) ;
}

```

---

### Post by psusi on 2007-09-20
Or you can open a pipe(), close( 1 ), close ( 2 ), then use dup2() to copy one of the pipe fds to descriptors 1 and 2 ( stdout and stderr ), fork() a child process, have it call system() then exit, and the parent process can read the output from the pipe fd.

---

### Post by DMills on 2007-09-20
Look at the popen function.

Regards, Dan.

---

### Post by gnusci on 2007-09-20
You can try with popen but also check: pipe(), dup(), fork(), and exec().

---

### Post by ant2ne on 2007-09-20
> **Fixman said:**
> Just put on a file and readI'd rather not write to the hard drive. 
> **gnusci said:**
> You can try with popen but also check: pipe(), dup(), fork(), and exec().Can you point me to a simple example code. All I find on the web is far to complex for me to make much sense of it. I don't understand why web tutorials need to include a lot of code that is not relevant to the task it is tutoring.  Or if someone is feeling ambitious they could give me a snip of code to toy with. Assume that I would like to put ```
system("whoami | who | cut -c11-15 ");
```into a variable called "idl".

Thanks

---

### Post by ghostdog74 on 2007-09-20
seriously speaking, are you really coding a C program that calls OS commands like this? This is really not very portable across systems..IMO.
If you want to use whoam,who,cut, use it from the shell...

---

### Post by dwhitney67 on 2007-09-21
I guess nobody uses getenv() anymore?

Actually, I guess that only works for getting environment values, not for performing complex commands.

---

### Post by walkerk on 2007-09-21
python
```
import os

temp os.popen("whoami | who | cut -c11-15 ")
who = temp.read()
```

who is now your string..

---

### Post by gnusci on 2007-09-21
I just wrote a toy example for you, but believe me I did input [COLOR="Red"]popen[/COLOR] in to gg and after a patient lecture :) and search I got a lot of info, anyway here the code....

[PHP]
#include <stdio.h>
#include <stdlib.h>

int main(){

  FILE *a;
  char buf[3000] ;
  
  a = popen ("whoami","r") ;
  
  while (!feof(a)) fgets (buf, 3000, a) ;
  puts (buf) ;
  
  pclose(a);

  return 0;
}
[/PHP]

I also have fund this :)
```

            o      _      _         _
   _o      /\_   _ |\o   (_)\__/o  (_)
 _< \_    _>(_) (_)/<_     \_| \   _|/' \/
(_)>(_)o (_) o   o  (_) o  (_)    (_)'  _\o_
-----------------------------------------------
```

EDITED: Sorry I fortgot to add the links:

[http://www.mkssoftware.com/docs/man3/popen.3.asp](http://www.mkssoftware.com/docs/man3/popen.3.asp)
[http://cvsweb.xfree86.org/cvsweb/cvs/os2/popen.h?rev=1.1.1.2](http://cvsweb.xfree86.org/cvsweb/cvs/os2/popen.h?rev=1.1.1.2)
[http://opengroup.org/onlinepubs/007908799/xsh/popen.html](http://opengroup.org/onlinepubs/007908799/xsh/popen.html)
[http://opengroup.org/onlinepubs/007908799/xsh/pclose.html](http://opengroup.org/onlinepubs/007908799/xsh/pclose.html)
[http://www.phim.unibe.ch/comp_doc/c_manual/C/FUNCTIONS/popen.html](http://www.phim.unibe.ch/comp_doc/c_manual/C/FUNCTIONS/popen.html)
[http://bama.ua.edu/cgi-bin/man-cgi?popen+3C](http://bama.ua.edu/cgi-bin/man-cgi?popen+3C)

more:

[http://www.google.de/search?q=popen&hl=en&start=20&sa=N](http://www.google.de/search?q=popen&hl=en&start=20&sa=N)

---

### Post by ant2ne on 2007-09-21
> **gnusci said:**
> 
[http://www.mkssoftware.com/docs/man3/popen.3.asp](http://www.mkssoftware.com/docs/man3/popen.3.asp)
[http://cvsweb.xfree86.org/cvsweb/cvs/os2/popen.h?rev=1.1.1.2](http://cvsweb.xfree86.org/cvsweb/cvs/os2/popen.h?rev=1.1.1.2)
[http://opengroup.org/onlinepubs/007908799/xsh/popen.html](http://opengroup.org/onlinepubs/007908799/xsh/popen.html)
[http://opengroup.org/onlinepubs/007908799/xsh/pclose.html](http://opengroup.org/onlinepubs/007908799/xsh/pclose.html)
[http://www.phim.unibe.ch/comp_doc/c_manual/C/FUNCTIONS/popen.html](http://www.phim.unibe.ch/comp_doc/c_manual/C/FUNCTIONS/popen.html)
[http://bama.ua.edu/cgi-bin/man-cgi?popen+3C](http://bama.ua.edu/cgi-bin/man-cgi?popen+3C)
more:
[http://www.google.de/search?q=popen&hl=en&start=20&sa=N](http://www.google.de/search?q=popen&hl=en&start=20&sa=N)
Great piece of code thanks!! There is lots in that to "play with". I checked the above links, and none of them had that chunk of code. It is exactly what I was looking for. Simple description of a (to me) complex operation. It is excellent for learning purposes. You should write a tutorial!

```

            o      _      _         _
   _o      /\_   _ |\o   (_)\__/o  (_)
 _< \_    _>(_) (_)/<_     \_| \   _|/' \/
(_)>(_)o (_) o   o  (_) o  (_)    (_)'  _\o_
-----------------------------------------------
```
What the heck is this?

---

### Post by gnusci on 2007-09-21
It is a man biking and then crash with an stone... this mean that you have to keep the eyes wide open when you are searching in internet :)

I did write the code by myself... Your welcome...

---

