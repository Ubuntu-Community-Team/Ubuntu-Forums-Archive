---
title: "Creating executable library such that it run on other ubuntu without code/compiling."
date: 2016-05-05
forum: Programming Talk
---

### Post by Balbir_Kumar on 2016-05-05
Hi all,

  I want to make executable from a library which in turns depends on 3 other library so that it can run on other ubuntu systems without compiling/code. What I need to do? shall I compile all libraries in shared / static mode or only the final library?

Thanks,
-Balbir Kumar

---

### Post by Rocket2DMn on 2016-05-05
You can compile your libraries as either static or shared.  Whenever you compile code, it will only run on systems with the same architecture though, so you can't run the same binary on both x86 and ARM (furthermore there are different variants of each of those).

I'm not sure what you mean by "make executable from a library".  Libraries don't have main functions, so they are not executables on their own.  If you build static libraries, binaries incorporate the library code directly into the executable.  If you use shared libraries, the binary and the dependent libraries need to be available on the target system, typically on a path defined by the LD_LIBRARY_PATH environment variable.  AFAIK, libraries that depend on other libraries do not include their code, even if they are built as static libs - only binaries will do that.

---

### Post by Balbir_Kumar on 2016-05-06
I do have a main function in the final library. I create output file from that. But that output file is not working in other ubuntu system. Is it possible to run this output file in other Ubuntu system without compiling/code? You had mentioned binary. How can I create binary in this situation?

---

### Post by Rocket2DMn on 2016-05-08
What is the error (if any) you get when trying to run?  We need more information in order to help with the problem, like what hardware architectures you're using, what version(s) of Ubuntu, and how you are compiling and linking your various libraries.

A binary is the compiled executable file - what you're calling the output file, if I've understood correctly.  Are you actually able to run the binary on both machines if you compile natively on them?

---

### Post by Balbir_Kumar on 2016-05-09
I am using ubuntu 14.04 LTS and 16.04. The error I am getting is following "error while loading shared libraries: libfontforge.so.2: cannot open shared object file: No such file or directory". N.B:- My both ubuntu system is installed in VMWare.

---

### Post by Rocket2DMn on 2016-05-09
That error indicates that you are missing a library dependency, in this case libfontforge.  You can install it with

```
sudo apt-get install libfontforge1
```

After installing, you might need to run

```
sudo ldconfig
```

Are you able to execute the program then?

---

### Post by Balbir_Kumar on 2016-05-10
After executing these two commands. I still get the same error. Is it possible that there is some mismatch between required .so and installed .so file?

---

### Post by Rocket2DMn on 2016-05-10
Hmm, it looks like libfontforge1 installs libfontforge.so.1 ln my system (still running Ubuntu 15.10).  Do you know where you got libfontforge on the system you compiled on?  Can you try installing "libfontforge-dev" as well?  If that doesn't work, you may need a newer version of the library, which you can get from the PPA at [https://launchpad.net/~fontforge/+archive/ubuntu/fontforge](https://launchpad.net/~fontforge/+archive/ubuntu/fontforge)
There are some instructions on the site about how to add the PPA.
You can read more about PPAs here or by a simple web search:
[https://help.ubuntu.com/community/PPA](https://help.ubuntu.com/community/PPA)
[https://help.ubuntu.com/16.04/ubuntu-help/addremove-ppa.html](https://help.ubuntu.com/16.04/ubuntu-help/addremove-ppa.html)

You could also try creating a symlink to libfontforge.so.1 called libfontforge.so.2, but no guarantees of compatibility.  These kinds of issues tend to arise when trying to port between Ubuntu releases.

---

### Post by Balbir_Kumar on 2016-05-16
Thanks @Rocket2DMn for your replies. I am considering to make debian package of the final library, since I have make certain changes into it. Is it possible?

---

### Post by Rocket2DMn on 2016-05-16
I expect so, but I don't know anything about creating debian packages.  You will need to start a new thread - in fact we have a [subforum just for packaging]("http://ubuntuforums.org/forumdisplay.php?f=44").

---

