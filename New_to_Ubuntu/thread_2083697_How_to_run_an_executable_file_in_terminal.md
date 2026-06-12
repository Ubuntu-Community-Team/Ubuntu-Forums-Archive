---
title: "How to run an executable file in terminal"
date: 2012-11-13
forum: New to Ubuntu
---

### Post by pkadeel on 2012-11-13
Please refer to the attached image file and guide me what am I supposed to do to run/execute an executable file. Both in Terminal and Thunar the error message is "no such file". I am confused because the file is present and has execute permissions set.

---

### Post by audiomick on 2012-11-13
You are, going by the prompt, already in the directory in which the file you want to execute is in. I see the file peazip there, marked as executable. I assume this is the one you want to run. Given that you are already in the directory, you don't need to put the path in the command. Also, I don't think it is a hidden file, so doesn't have a . before the name. Try just typing

```
peazip
```

I am not too sure about Thunar, but in nautilus you only have to click on an executable file, and get the option "run in terminal".

---

### Post by Lars Noodén on 2012-11-13
For safety reasons the current directory, '.', is never part of the path.  So ./peazip is correct.  It's a mystery what is wrong.  Have you tried using tab completion to spell it.  About the only guess I have is that maybe there is some whitespace in the name.

---

### Post by Impavidus on 2012-11-13
ls -l indeed shows you it is executable. The correct command to execute the file - if you're already in the right directory - is:```
./peazip
```The "./" part is there because the current directory is not in the path where your system looks for executables, so you have to give the path explicitly. There's definitely no need to call sudo. As this obviously doesn't work for you there must be some strange problem. I could imagine a trailing space in the file name, but then it should still work in thunar. Maybe you should try using the entire path: /home/username/blahblah/peazip

---

### Post by Cheesemill on 2012-11-13
I've come across this before but it was years ago and I can't remember how I solved it. As a workaround you could try:
```
sh peazip
```

---

### Post by rnerwein on 2012-11-13
> **pkadeel said:**
> Please refer to the attached image file and guide me what am I supposed to do to run/execute an executable file. Both in Terminal and Thunar the error message is "no such file". I am confused because the file is present and has execute permissions set.
hi
type: file peazip  to get the file-type
and : ls -l peazip  if you get file not found then there is a nonprintable sign in the name ? may be.

---

### Post by jerome1232 on 2012-11-13
I've seen this before when the executable can't find a library and the "no such file or directory" message is actually coming from the running exectuable trying to find the library.

The website you got the executable from should tell you what libraries are required to run the file if that is the case.
You should also be able to run the below to get a list of libraries it wants.
```
ldd peazip
```

---

### Post by CharlesA on 2012-11-13
> **jerome1232 said:**
> I've seen this before when the executable can't find a library and the "no such file or directory" message is actually coming from the running exectuable trying to find the library.

The website you got the executable from should tell you what libraries are required to run the file if that is the case.
You should also be able to run the below to get a list of libraries it wants.
```
ld peazip
```
What he said.

I've seen it for other things too, but if you do have all the libraries installed, I'd run a fsck on the drive and see if that helps.

---

### Post by pkadeel on 2012-11-13
There is no trailing or leading space in the file name. I have rechecked it. I have also tried giving the full path despite I was in the same folder.

Another strange thing is that tab completion is not working for any file inside this folder.

sh filename did something which you can see in the image. That might be the cause but the thing is how can bash know in advance that the file is corrupt and did not offer the auto complete.

I downloaded it from peazip official site and it was mentioned as GTK+ based portable version. this whole folder was in .tar.gz format and I uncompressed it using
```
tar -zxvf filename.tar.gz
```

As rnerwien mentioned two commands the output of those two is as follows
```

adeel@HP-G62:~/Downloads/peazip$ file peazip
peazip: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), stripped

```
```

adeel@HP-G62:~/Downloads/peazip$ ls -l peazip
-rwxrwxr-x 1 adeel adeel 6895680 Oct 22 13:37 peazip

```

---

### Post by pkadeel on 2012-11-13
```

adeel@HP-G62:~/Downloads/peazip$ ld peazip
ld: i386 architecture of input file `peazip' is incompatible with i386:x86-64 output
ld: warning: cannot find entry symbol _start; defaulting to 0000000000415c60

```
This makes some sense. However tab completion accepted when used after ld command :confused:

---

### Post by Lars Noodén on 2012-11-13
> **pkadeel said:**
> ```

adeel@HP-G62:~/Downloads/peazip$ file peazip
peazip: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), stripped

```


This shows that it is not a script.  What about the ld above or ldd?

```

ld peazip
ldd peazip

```

---

### Post by fslezak on 2012-11-13
Simple.

```

sudo chmod 777 peazip
./peazip

```

Make sure you are in the folder where PeaZip is.

Bash does not auto-complete non-runnable files.

---

### Post by jerome1232 on 2012-11-13
> **Lars Noodén said:**
> This shows that it is not a script.  What about the ld above or ldd?

```

ld peazip
ldd peazip

```
 
Try ldd, I accidentally left out a d in my original post

---

### Post by pkadeel on 2012-11-13
[B]Quote from their website:
PeaZip Portable for Linux[/B] does not need to be installed, so it is recommended if you want to test the application, to run it from a removable device, or if you should not modify host system (i.e. library freeze in production machines). It can be used on any Linux family extracting the package and running peazip binary in program's directory.

It is supposed to run without any dependencies if I am not wrong but anyway if I have to install libraries to run a portable software then it doesn't serve the purpose.

---

### Post by pkadeel on 2012-11-13
> **jerome1232 said:**
> Try ldd, I accidentally left out a d in my original post
```
adeel@HP-G62:~/Downloads/peazip$ ldd peazip
    not a dynamic executable

```

---

### Post by Cheesemill on 2012-11-13
[s]Try downloading the file again, I've just tested on my machine and everything works as expected.[/s]

Edit - Scratch that, I just realized I was on my Arch machine where it does work OK.
Just tried the exactly the same file on my Ubuntu VM and I get the same error as you.

---

### Post by pkadeel on 2012-11-13
> **Cheesemill said:**
> [s]Try downloading the file again, I've just tested on my machine and everything works as expected.[/s]

Edit - Scratch that, I just realized I was on my Arch machine where it does work OK.
Just tried the exactly the same file on my Ubuntu VM and I get the same error as you.
Hence topic closed. lol
It is not me, it is the file this time. :)

---

### Post by jerome1232 on 2012-11-13
Out of curiosity cheesemill were these both 64 bit installs or 32 bit installs, does Arch do multiarch?

---

### Post by Cheesemill on 2012-11-13
> **jerome1232 said:**
> Out of curiosity cheesemill were these both 64 bit installs or 32 bit installs, does Arch do multiarch?
Both 64-bit.
I've got the multiarch repository enabled on my Arch system as well.

If you give me a minute I'll check on a 32-bit Ubuntu......

---

### Post by Cheesemill on 2012-11-13
OK so it's using a 64-bit system that's the problem, I've just tried with the same file on a 32-bit Live CD and it works fine. Perhaps installing ia32-libs will sort this out.

---

### Post by Cheesemill on 2012-11-13
Problem solved.

To run this executable on a 64-bit system you need to have ia32-libs installed.

---

### Post by pkadeel on 2012-11-13
> **Cheesemill said:**
> Problem solved.

To run this executable on a 64-bit system you need to have ia32-libs installed.
OK now as you have finally found the problem, I tried that too on my Xubuntu and it didn't help. Not because the solution was faulty but because I couldn't install ia32-libs

Just mentioned this for other xubuntu users who might find this thread relevant to their problem.
```

adeel@HP-G62:~$ sudo apt-get install ia32-libs
[sudo] password for adeel: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 ia32-libs : Depends: ia32-libs-multiarch
 openjdk-7-jre : Depends: libpulse0 (>= 1:0.99.1) but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

```

So now I have abandoned the concept of using this peazip. I think i will be better of  using the command line decompression rather that bringing together a broken operating system.

---

