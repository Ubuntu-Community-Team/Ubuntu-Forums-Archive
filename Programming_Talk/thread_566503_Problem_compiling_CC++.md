---
title: "Problem compiling C/C++"
date: 2007-10-03
forum: Programming Talk
---

### Post by lavajumper on 2007-10-03
Does anyone know how to fix this???

file: test.cc
```

using namespace std;  

int main()
{
  return(0);
}


```

and running:
```

gcc test.cc -o test

```

returns:

```

/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/crt1.o: In function `_start':
(.text+0x1d): undefined reference to `__libc_start_main'
collect2: ld returned 1 exit status

```

I've reinstalled build-essentials, libc6-dev and libc6-dbg,  gcc, cc and g++. I also tried with and without the 'using namespace std;' statement.  I'm just not sure where to go from here?

---

### Post by Wybiral on 2007-10-03
Have you tried "int main(int argc, char *argv[])"?

I've come across a couple of compilers that refuse to accept main without those parameters (it's standard practice anyway).

---

### Post by dwhitney67 on 2007-10-03
First, you included a "using namespace std".  Why?  You don't need it.

Second, if you do indeed want to program in C++, then please use the g++ compiler; not the gcc.

---

### Post by lavajumper on 2007-10-03
this->:confused:

Here's what C++ does:

file test.cpp
```

#include <iostream>

using namespace std;

int main(int argc, char *argv[]){
    cout << "Dropped another one." << endl;
    return(0);
}

```

running:
```

g++ test.cpp -o test

```

the output:
```

/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/crt1.o: In function `_start':
(.text+0x1d): undefined reference to `__libc_start_main'
/tmp/ccJSVoTP.o: In function `__static_initialization_and_destruction_0(int, int)':
test.cpp:(.text+0x3f): undefined reference to `__cxa_atexit'
/usr/lib/gcc/i486-linux-gnu/4.1.2/libstdc++.so: undefined reference to `stdout@GLIBC_2.0'
/usr/lib/gcc/i486-linux-gnu/4.1.2/libstdc++.so: undefined reference to `mbrtowc@GLIBC_2.0'
/usr/lib/gcc/i486-linux-gnu/4.1.2/libstdc++.so: undefined reference to `__stack_chk_fail@GLIBC_2.4'
/usr/lib/gcc/i486-linux-gnu/4.1.2/libstdc++.so: undefined reference to `__strtod_l@GLIBC_2.1'
/usr/lib/gcc/i486-linux-gnu/4.1.2/libstdc++.so: undefined reference to `wcslen@GLIBC_2.0'
/usr/lib/gcc/i486-linux-gnu/4.1.2/libstdc++.so: undefined reference to `memset@GLIBC_2.0'
/usr/lib/gcc/i486-linux-gnu/4.1.2/libstdc++.so: undefined reference to `lseek64@GLIBC_2.1'
/usr/lib/gcc/i486-linux-gnu/4.1.2/libstdc++.so: undefined reference to `wcrtomb@GLIBC_2.0'
/usr/lib/gcc/i486-linux-gnu/4.1.2/libstdc++.so: undefined reference to `mbsrtowcs@GLIBC_2.0'
/usr/lib/gcc/i486-linux-gnu/4.1.2/libstdc++.so: undefined reference to `putc@GLIBC_2.0'
/usr/lib/gcc/i486-linux-gnu/4.1.2/libstdc++.so: undefined reference to `wctob@GLIBC_2.0'
/usr/lib/gcc/i486-linux-gnu/4.1.2/libstdc++.so: undefined reference to `setvbuf@GLIBC_2.0'
/usr/lib/gcc/i486-linux-gnu/4.1.2/libstdc++.so: undefined reference to `__fxstat64@GLIBC_2.2'
/usr/lib/gcc/i486-linux-gnu/4.1.2/libstdc++.so: undefined reference to `__wcsxfrm_l@GLIBC_2.1'
/usr/lib/gcc/i486-linux-gnu/4.1.2/libstdc++.so: undefined reference to `bindtextdomain@GLIBC_2.0'
/usr/lib/gcc/i486-linux-gnu/4.1.2/libstdc++.so: undefined reference to `writev@GLIBC_2.0'
/usr/lib/gcc/i486-linux-gnu/4.1.2/libstdc++.so: undefined reference to `memchr@GLIBC_2.0'
/usr/lib/gcc/i486-linux-gnu/4.1.2/libstdc++.so: undefined reference to `getc@GLIBC_2.0'
/usr/lib/gcc/i486-linux-gnu/4.1.2/libstdc++.so: undefined reference to `__strtof_l@GLIBC_2.1'
/usr/lib/gcc/i486-linux-gnu/4.1.2/libstdc++.so: undefined reference to `gettext@GLIBC_2.0'
/usr/lib/gcc/i486-linux-gnu/4.1.2/libstdc++.so: undefined reference to `__uselocale@GLIBC_2.3'
/usr/lib/gcc/i486-linux-gnu/4.1.2/libstdc++.so: undefined reference to `wmemcpy@GLIBC_2.0'
/usr/lib/gcc/i486-linux-gnu/4.1.2/libstdc++.so: undefined reference to `strcmp@GLIBC_2.0'
/usr/lib/gcc/i486-linux-gnu/4.1.2/libstdc++.so: undefined reference to `wmemcmp@GLIBC_2.0'
/usr/lib/gcc/i486-linux-gnu/4.1.2/libstdc++.so: undefined reference to `write@GLIBC_2.0'
/usr/lib/gcc/i486-linux-gnu/4.1.2/libstdc++.so: undefined reference to `__freelocale@GLIBC_2.1'
/usr/lib/gcc/i486-linux-gnu/4.1.2/libstdc++.so: undefined reference to `mbsnrtowcs@GLIBC_2.0'
/usr/lib/gcc/i486-linux-gnu/4.1.2/libstdc++.so: undefined reference to `btowc@GLIBC_2.0'
/usr/lib/gcc/i486-linux-gnu/4.1.2/libstdc++.so: undefined reference to `isalnum@GLIBC_2.0'
/usr/lib/gcc/i486-linux-gnu/4.1.2/libstdc++.so: undefined reference to `strchr@GLIBC_2.0'
/usr/lib/gcc/i486-linux-gnu/4.1.2/libstdc++.so: undefined reference to `__duplocale@GLIBC_2.1'
/usr/lib/gcc/i486-linux-gnu/4.1.2/libstdc++.so: undefined reference to `fdopen@GLIBC_2.1'
/usr/lib/gcc/i486-linux-gnu/4.1.2/libstdc++.so: undefined reference to `strtold_l@GLIBC_2.3'
/usr/lib/gcc/i486-linux-gnu/4.1.2/libstdc++.so: undefined reference to `wmemset@GLIBC_2.0'
/usr/lib/gcc/i486-linux-gnu/4.1.2/libstdc++.so: undefined reference to `fopen64@GLIBC_2.1'
/usr/lib/gcc/i486-linux-gnu/4.1.2/libstdc++.so: undefined reference to `ungetc@GLIBC_2.0'
/usr/lib/gcc/i486-linux-gnu/4.1.2/libstdc++.so: undefined reference to `fwrite@GLIBC_2.0'
/usr/lib/gcc/i486-linux-gnu/4.1.2/libstdc++.so: undefined reference to `getenv@GLIBC_2.0'
/usr/lib/gcc/i486-linux-gnu/4.1.2/libstdc++.so: undefined reference to `fputc@GLIBC_2.0'
/usr/lib/gcc/i486-linux-gnu/4.1.2/libstdc++.so: undefined reference to `poll@GLIBC_2.0'
/usr/lib/gcc/i486-linux-gnu/4.1.2/libstdc++.so: undefined reference to `__ctype_get_mb_cur_max@GLIBC_2.0'
/usr/lib/gcc/i486-linux-gnu/4.1.2/libstdc++.so: undefined reference to `wcsnrtombs@GLIBC_2.0'
/usr/lib/gcc/i486-linux-gnu/4.1.2/libgcc_s.so: undefined reference to `dl_iterate_phdr@GLIBC_2.2.4'
/usr/lib/gcc/i486-linux-gnu/4.1.2/libstdc++.so: undefined reference to `isspace@GLIBC_2.0'
/usr/lib/gcc/i486-linux-gnu/4.1.2/libstdc++.so: undefined reference to `read@GLIBC_2.0'
/usr/lib/gcc/i486-linux-gnu/4.1.2/libstdc++.so: undefined reference to `fflush@GLIBC_2.0'
/usr/lib/gcc/i486-linux-gnu/4.1.2/libstdc++.so: undefined reference to `fread@GLIBC_2.0'
/usr/lib/gcc/i486-linux-gnu/4.1.2/libstdc++.so: undefined reference to `textdomain@GLIBC_2.0'
/usr/lib/gcc/i486-linux-gnu/4.1.2/libstdc++.so: undefined reference to `stderr@GLIBC_2.0'
/usr/lib/gcc/i486-linux-gnu/4.1.2/libstdc++.so: undefined reference to `memcpy@GLIBC_2.0'
/usr/lib/gcc/i486-linux-gnu/4.1.2/libstdc++.so: undefined reference to `getwc@GLIBC_2.2'
/usr/lib/gcc/i486-linux-gnu/4.1.2/libstdc++.so: undefined reference to `wmemmove@GLIBC_2.0'
/usr/lib/gcc/i486-linux-gnu/4.1.2/libstdc++.so: undefined reference to `strlen@GLIBC_2.0'
/usr/lib/gcc/i486-linux-gnu/4.1.2/libstdc++.so: undefined reference to `fileno@GLIBC_2.0'
/usr/lib/gcc/i486-linux-gnu/4.1.2/libstdc++.so: undefined reference to `putwc@GLIBC_2.2'
/usr/lib/gcc/i486-linux-gnu/4.1.2/libstdc++.so: undefined reference to `__strftime_l@GLIBC_2.3'
/usr/lib/gcc/i486-linux-gnu/4.1.2/libstdc++.so: undefined reference to `__errno_location@GLIBC_2.0'
/usr/lib/gcc/i486-linux-gnu/4.1.2/libstdc++.so: undefined reference to `strcat@GLIBC_2.0'
/usr/lib/gcc/i486-linux-gnu/4.1.2/libstdc++.so: undefined reference to `__wcsftime_l@GLIBC_2.3'
/usr/lib/gcc/i486-linux-gnu/4.1.2/libstdc++.so: undefined reference to `__wcscoll_l@GLIBC_2.1'
/usr/lib/gcc/i486-linux-gnu/4.1.2/libstdc++.so: undefined reference to `__newlocale@GLIBC_2.1'
/usr/lib/gcc/i486-linux-gnu/4.1.2/libstdc++.so: undefined reference to `__wctype_l@GLIBC_2.1'
/usr/lib/gcc/i486-linux-gnu/4.1.2/libstdc++.so: undefined reference to `fseeko64@GLIBC_2.1'
/usr/lib/gcc/i486-linux-gnu/4.1.2/libstdc++.so: undefined reference to `strcpy@GLIBC_2.0'
/usr/lib/gcc/i486-linux-gnu/4.1.2/libstdc++.so: undefined reference to `wcscmp@GLIBC_2.0'
/usr/lib/gcc/i486-linux-gnu/4.1.2/libstdc++.so: undefined reference to `memmove@GLIBC_2.0'
/usr/lib/gcc/i486-linux-gnu/4.1.2/libstdc++.so: undefined reference to `__assert_fail@GLIBC_2.0'
/usr/lib/gcc/i486-linux-gnu/4.1.2/libstdc++.so: undefined reference to `__nl_langinfo_l@GLIBC_2.2'
/usr/lib/gcc/i486-linux-gnu/4.1.2/libstdc++.so: undefined reference to `ftello64@GLIBC_2.1'
/usr/lib/gcc/i486-linux-gnu/4.1.2/libstdc++.so: undefined reference to `abort@GLIBC_2.0'
/usr/lib/gcc/i486-linux-gnu/4.1.2/libstdc++.so: undefined reference to `__iswctype_l@GLIBC_2.1'
/usr/lib/gcc/i486-linux-gnu/4.1.2/libstdc++.so: undefined reference to `__cxa_atexit@GLIBC_2.1.3'
/usr/lib/gcc/i486-linux-gnu/4.1.2/libstdc++.so: undefined reference to `snprintf@GLIBC_2.0'
/usr/lib/gcc/i486-linux-gnu/4.1.2/libstdc++.so: undefined reference to `ungetwc@GLIBC_2.2'
/usr/lib/gcc/i486-linux-gnu/4.1.2/libstdc++.so: undefined reference to `__strcoll_l@GLIBC_2.1'
/usr/lib/gcc/i486-linux-gnu/4.1.2/libstdc++.so: undefined reference to `__towlower_l@GLIBC_2.1'
/usr/lib/gcc/i486-linux-gnu/4.1.2/libstdc++.so: undefined reference to `wmemchr@GLIBC_2.0'
/usr/lib/gcc/i486-linux-gnu/4.1.2/libstdc++.so: undefined reference to `fputs@GLIBC_2.0'
/usr/lib/gcc/i486-linux-gnu/4.1.2/libstdc++.so: undefined reference to `__strxfrm_l@GLIBC_2.1'
/usr/lib/gcc/i486-linux-gnu/4.1.2/libstdc++.so: undefined reference to `setlocale@GLIBC_2.0'
/usr/lib/gcc/i486-linux-gnu/4.1.2/libstdc++.so: undefined reference to `fclose@GLIBC_2.1'
/usr/lib/gcc/i486-linux-gnu/4.1.2/libstdc++.so: undefined reference to `__towupper_l@GLIBC_2.1'
/usr/lib/gcc/i486-linux-gnu/4.1.2/libstdc++.so: undefined reference to `stdin@GLIBC_2.0'
/usr/lib/gcc/i486-linux-gnu/4.1.2/libstdc++.so: undefined reference to `ioctl@GLIBC_2.0'
collect2: ld returned 1 exit status

```

This code works on my other Ubuntu boxes (fiesty and dapper).

---

### Post by Wybiral on 2007-10-03
I may be wrong, because I've never seen that error before, but it looks like you don't have all of the development files. But you say you installed build-essential?

---

### Post by stchman on 2007-10-03
> **lavajumper said:**
> Does anyone know how to fix this???

file: test.cc
```

using namespace std;  

int main()
{
  return(0);
}


```

and running:
```

gcc test.cc -o test

```

returns:

```

/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/crt1.o: In function `_start':
(.text+0x1d): undefined reference to `__libc_start_main'
collect2: ld returned 1 exit status

```

I've reinstalled build-essentials, libc6-dev and libc6-dbg,  gcc, cc and g++. I also tried with and without the 'using namespace std;' statement.  I'm just not sure where to go from here?

First off did you install build-essential?  

Second use the g++ instead of gcc.  g++ is the c++ compiler.

---

### Post by aks44 on 2007-10-03
Just a wild guess:

1. sudo apt-get remove --purge build-essential
2. sudo apt-get autoremove --purge
3. repeat step 1-2 for any other dev-related package you installed manually
4. sudo apt-get install build-essential

With some luck it *may* reinstall the whole thing properly... (not that you've got much to loose trying it ;))

---

### Post by lavajumper on 2007-10-03
Trust me, I'm pretty baffled.  And build-essentials is installed (and reinstalled) as are all the packages listed in /usr/share/build-essential/list

I'm trying to hunt down which package the crt1.o (c run time?) is in, but at this point I'm just poking at stuff.

I really wish there were some kind of validator for the build environments(but I guess that's what the error message tells us).

And just so that we don't keep beating a red herring, I added the 'using namespace std' because another distribution I used required it for C programs as well as C++. If you read the original post you'll note that I tried both with and without.

I'm going to try the --purge switch, haven't done that yet.

---

### Post by kknd on 2007-10-03
Maybe a ldconfig would help?

---

### Post by PaulFr on 2007-10-04
I hope you've fixed it, but here goes:

1. The typical crt1.o is in libc6-dev and libc6-dev-amd64 packages. Install **apt-file** package if you want to find packages that contain a specific file.

2. If you use **g++ -v test.cpp -o test** instead of the command line you used, you can get the exact command that is being executed at each stage. That might tell you something.

3. It looks like you may not have libstdc++-dev libraries installed - please check with **aptitude search libstdc++** and see which ones are installed (**i** in leftmost column). On my Feisty machine, libstdc++5, libstdc++6, libstdc++6.4.1-dev are installed.

4. When you do get your executable called **test**, please execute with ./test - remember there is a /usr/bin/test :-)

---

### Post by preacher2B on 2007-10-04
I have been having a problem with this as well.  I did some research and found a [bug report here]("http://bugs.launchpad.net/ubuntu/+source/gdebi/+bug/120935").

If you find out how to solve this let us know. 
Thanks.

---

### Post by lavajumper on 2007-10-04
I want to thank everyone for trying to help on this. 

This one was solved by a re-install  :mad:

The --purge switch got me half-way.  So I'm sure there was something crossed up, as I got a new set of error messages. (Thanks for the tips).

Looking at the outputs, I got the idea( as I'm sure many others had in the back of their mind) that at least part of it had to be a versioning problem.  So I tried using apt-get to reinstall libc6. Well, it got half-way through and I got the dreaded "dpkg --configure -a" message. I ran it...the system lost its libc.so.6 link and I couldn't run anything. I rebooted hoping that ldconfig would run at boot, and the computer froze at the splash-screen.  (with the cap and scroll lock keys blinking).  Rebooted from the CD, and manually inserted the libc6 link. Still no dice. So I decided the shortest path at that point (for me) was to backup data and reinstall. Did I mention how much I LOVE the live boot CD?

So, whatever happened....heheh....its fixed now. I'm just glad it didn't happen on one of our production machines.

Also, the rest of the information from this thread is now in my systems book. Thank you all for taking the time to wrestle with it.

If anyone else figures out what was going on I'd love to know about it.

---

### Post by preacher2B on 2007-10-04
```
sudo aptitude update
sudo aptitude install build-essential
```

This did it for me. 
Because of the dependency cycle I was getting nowhere fast. This I found in another post [here]("http://ubuntuforums.org/archive/index.php/t-374821.html").

---

