---
title: "no c compiler!"
date: 2006-01-30
forum: Packaging and Compiling Programs
---

### Post by timmy666 on 2006-01-30
when i try to install programs that i have downloaded (in source code) , ubuntu dosen't find any c compiler. and when i search on my disk for ex: gcc, cc, g++ it dosen't find anything.... 

dosen't ubuntu have a standard c compiler?
and if not, how can i install one the easiest way (im a noob)?

---

### Post by brk3 on 2006-01-30
Just open up synaptic package manager and install the package 'build-essential' which will automatically install all compilers and development librarys needed to compile most software.

---

### Post by timmy666 on 2006-01-30
thanks.. but now it says 

checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

every time i try to install a program

---

### Post by SolidCube on 2006-02-06
I have the same issue re executable.

Astonishing that a modern distro wouldn't include basic GNU dev tools by default.  Are we doing something wrong?

I'm NOT a noob but I don't really have time to waste on this kind of thing.  Looks like it's back to SuSE.

---

### Post by shawway on 2006-12-30
After same errors this worked fine for me:

sudo apt-get install linux-kernel-headers
sudo apt-get install build-essential

---

### Post by nadee on 2007-01-24
> **timmy666 said:**
> when i try to install programs that i have downloaded (in source code) , ubuntu dosen't find any c compiler. and when i search on my disk for ex: gcc, cc, g++ it dosen't find anything.... 

dosen't ubuntu have a standard c compiler?
and if not, how can i install one the easiest way (im a noob)?

i want to compile c program, but i dont know how to install c compiler in ubuntu

---

### Post by CareySchug on 2007-01-24
Thank you !!!

Expanding on another response.  Maybe I'm not sutpized that theese are not INCLUDED in the basic isntall, after all, ubuntu is for unsophisticated users, but i *AM* surprised (and dissapointed) that the instal process is not covered in the desktop install guide (also not in the server install guide)

unfortunately, apparently  need a different compiler.  It's said to be the SUN compiler, as I get errors in the compile, and the make fails.

> **shawway said:**
> After same errors this worked fine for me:

sudo apt-get install linux-kernel-headers
sudo apt-get install build-essential

---

### Post by Manolicious on 2007-10-08
> **brk3 said:**
> Just open up synaptic package manager

how do you do that?  Where is it?  I tried search my drive for it but couldn't find any file titled "synaptic."

---

### Post by maddog39 on 2007-10-08
> **Manolicious said:**
> how do you do that?  Where is it?  I tried search my drive for it but couldn't find any file titled "synaptic."
Its easy. Go to: System > Administration > Synaptic Package Manager, click on Search, search for build-essential, select the package, and then hit Apply. That will then install the package build-essential for you. You can do the same thing for the linux-kernel-headers package.

---

### Post by kosy on 2007-10-09
Done what you suggest but when getting: "configure: error: No C# compiler found" when doing ./configure.

Any idea?

---

### Post by Auria on 2007-10-10
> **kosy said:**
> Done what you suggest but when getting: "configure: error: No C# compiler found" when doing ./configure.

Any idea?

Install mono (don't know the exact package names, should be easy to find with search)

---

### Post by Lord Illidan on 2007-10-10
Do you want a C compiler or a C# compiler??? They're different, you know.

---

### Post by kosy on 2007-10-10
Did like was instructed here: [http://f-spot.org/How_To_Build_from_HEAD](http://f-spot.org/How_To_Build_from_HEAD)

After doing that then I got this error:
checking for mono.pc... configure: error: missing the mono.pc file, usually
found in the mono-devel package

So installed mono-devel package and then this error came up:
checking for System.Runtime.Remoting.dll... configure: error: missing required
mono 2.0 DLL: System.Runtime.Remoting.dll

I can not find this file.:(

Maybe I need to install C# compiler??
How do I install that one?

/kosy

---

### Post by sloggerkhan on 2007-10-10
if it's looking for .dll files, it's probably a program specific to windows.

---

### Post by kosy on 2007-10-15
In addition I needed to installed:
libmono-system-runtime2.0-cil
liblcms-dev
libgphoto2.dev

Then all worked for me:)
Thanks to Maxxer at F-Spot.org

thanks all
/kosy

---

### Post by takerphenom on 2008-01-23
hi, i'm kind of a noob at ubuntu and i keep getting errors for every installation i try to make.  I entered the command "sudo apt-get install build-essential", but that failed. I also tried the synaptic package manager but i got this error:
"E: /var/cache/apt/archives/libc6_2.6.1-1ubuntu10_i386.deb: corrupted filesystem tarfile - corrupted package archive"

The terminal output was:
(Reading database ... 129989 files and directories currently installed.)
Preparing to replace libc6 2.6.1-1ubuntu9 (using .../libc6_2.6.1-1ubuntu10_i386.deb) ...
Unpacking replacement libc6 ...
dpkg: error processing /var/cache/apt/archives/libc6_2.6.1-1ubuntu10_i386.deb (--unpack):
 corrupted filesystem tarfile - corrupted package archive
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.6.1-1ubuntu10_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

please help

---

### Post by ShirishAg75 on 2008-02-28
do the following in your terminal :-

```

sudo apt-get --fix-broken 

```

If it still doesn't respond try 

```

sudo apt-get  --fix--missing

```

I never had a corrupted package archive but saw these commands on the apt-get manual page. Perhaps they might prove to be assistance. 

There is something also called dselect which could be good. But haven't used it so can't say much.

---

### Post by jsoderba on 2008-02-29
> **ShirishAg75 said:**
> do the following in your terminal :-
There is something also called dselect which could be good. But haven't used it so can't say much.dselect is an apt front-end like synaptic or aptitude, so it will not help him fix his corrupted apt files. It is also ancient and infamously hard to use, so you are generally not advised to use it.

---

### Post by michel_f on 2008-04-27
> **shawway said:**
> 
sudo apt-get install build-essential

worked for me too :D

---

### Post by saeid on 2008-05-29
> **kosy said:**
> In addition I needed to installed:
libmono-system-runtime2.0-cil
liblcms-dev
libgphoto2.dev

Then all worked for me:)

me 2 :)

---

### Post by SontagBill on 2008-07-15
Downloaded the build-essential package and found GCC as the compiler.  Clicked on an extracted tarball install file but no GCC option to activate the file was displayed.  Sorry for the inconvenience but all help would be appreciated.
regards, Bill

---

### Post by koolkev on 2008-08-21
I too have gone to system>synapticpackagemanager>search for gcc>selected gcc> installed all that were highlighted. 

I now have several gcc showing as installed as shown on a screen shot:

[ATTACH]82295[/ATTACH] 
 
anyhow if i search in applications I don't see anything. 

Where would I expect to find the program?

I need a compiler for an online class in c programming so I am a beginner.

---

### Post by Vyoma on 2008-08-25
> **koolkev said:**
> ...
 
anyhow if i search in applications I don't see anything. 

Where would I expect to find the program?

I need a compiler for an online class in c programming so I am a beginner.

gcc is a command line compiler. You won't be able to find a Application menu entry for gcc.

Once installed though, you can invoke it at terminal and see if it exists.

```
gcc --version
```

You can even see from where it gets invoked from:

```
which gcc
```

To compile a file, you have to do something along the lines:

```
gcc myfile1.c -o myprog
```

You man need to include other linker options. For more details, check out [gcc documentation]("http://gcc.gnu.org/onlinedocs/").

---

### Post by mrhippieguy on 2009-09-16
i has the same problem this forum was started with, except the solution would work, but my ubuntu has no internet access, and i need this program installed before october, so, any suggestions?

---

### Post by MadCow108 on 2009-09-16
it should be on the ubuntu cd:
[http://ubuntuforums.org/showthread.php?t=381532](http://ubuntuforums.org/showthread.php?t=381532)

---

### Post by shae on 2009-09-19
I believe at least some of the people are looking for an IDE.  Perhaps something like Code::Blocks is what you want?

```
sudo apt-get install codeblocks
```

---

### Post by mrhippieguy on 2009-09-20
okay did that, still gettin' 
[I]
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.[/I]

every time. any ideas?

---

### Post by Joeb454 on 2009-09-20
Is build-essential installed? ```
sudo apt-get install build-essential
```

---

### Post by mrhippieguy on 2009-09-21
iv'e done that a couple times now, still same message.

---

