---
title: "source vs. binary - windows vs. linux - etc."
date: 2008-02-26
forum: Programming Talk
---

### Post by rendon on 2008-02-26
source vs. binary - windows vs. linux - etc.

Hi!

Although this is a newbie-ish question, I'm not quite a newbie, and I'm hoping I can get answers to this from a "programmers perspective" as I am an application developer myself.

I've been using linux for many years now, and I've studied programming from desktop applications with python to PHP development and shell scripting... but...

I still don't understand something about the differences between installing a program and making a script that can be run "on the fly".

So, in other words,  if 

1) I use python to make a big complex fancy game with pictures and sound, and (if you have python installed) you only have to download the package and double click the "run.py" icon to play... 

why is this much different from 

2) making a "program" which "installs" into the system and puts all of these files and folders in certain locations around your OS?

is there a benifit from using one over the other?

Also:

In the case of "binaries" or "exe"s for windows, and whatever other type there might be...  How do these associate with the installation process?  

If I'm not compiling from source, then I guess that means I'm installing something which is pre-compiled, so if it's precompiled then it should be ready to go... ergo, why do I need this "installation" process? 

feedback much appreciated!

---

### Post by darsu on 2008-02-26
In scenario 1 the same game package will work on any system that can host a Python interpreter and libraries, but in scenario 2 you need to prepare and supply different binaries for different systems.

Installation can mean different things for different programs and different systems. Installation concerns setting up program components in the way required by the program to operate and expected in terms of user convenience. Putting files in standard locations so (X) can find them, creating icons/shortcuts, fiddling with register database in Windows...

---

### Post by rendon on 2008-02-26
Thanks for your response, darsu.  I have many specific questions about this topic, that's why I wanted to start a thread about it.

You just reminded me of another question.  About the windows "registry".  What is that, and why do programmer want to access this?  (another reason why I put this topic in programmers forum) 

what is the registry and how does it benifit the programmer over an application with it's own files...

> 
In scenario 1 the same game package will work on any system that can host a Python interpreter and libraries, but in scenario 2 you need to prepare and supply different binaries for different systems.


but remember, I don't understand binaries ;)  Why do I need to supply binaries for different systems?  what would the binaries be?  such as a python interpreter in this case?

---

### Post by darsu on 2008-02-26
A binary executable is the program code translated into the native code of a particular operating system and processor architecture; but with Python, the program code is compiled into a standard intermediate representation, and the Python interpreter takes responsibility for invisibly translating this representation into the native code of the system being used. 


And the Windows registry - I don't really know or care to find out myself, but I bet [http://en.wikipedia.org/wiki/Windows_Registry](http://en.wikipedia.org/wiki/Windows_Registry) would be a start.

---

### Post by Acapulco on 2008-02-26
As far as I know, the Registry is a place where you associate things like file types with the program to open it, location of DLLs, some OS settings (like the title on the IExplorer window), etc. 

It's kinda like a repository for settings, in a way. It's also where you tell the OS to run programs at start, define driver files, etc.

You install a program when say, you need to supply special drivers for the video card (although that's rarely done this days), to copy all the resources to their correct folders (images, sounds, video, etc) to see if certain DLL is already in the system, and if not, installing it (ie. directx version YYY)

So, the advantages depend on your particular program.

For exaple, Blizzard's World of Warcraft uses Python I believe for all the UI scripting things, so you are able to program your own UI addons, etc, without the need for Blizzard to supply it's own language.

Still, the game needs to install images, icons, character sounds, the world map, etc.

---

### Post by rendon on 2008-02-26
Thanks for your responses!

I think I can assess my questions in the following manner, perhaps with more questions:

1) binaries = executables?

2) executables are OS and processor architecture specific, that would explain why you have to choose the correct software for your operating system... however, I don't understand, when I choose the software for my operating system, it doesn't ask me which processor architecture I'm using.  Is that because just about everyone is using x86?  does the same binary for Anthlon work for x86?

3) Windows Registry:  This allows programs to use windows integrated tools and settings.  Ok, so I guess an example of this is like when I installed skype on windows before, and adware warned me that skype wanted to make a registry entry.  After installing skype I saw that skype highlighted all phone numbers it found in IE when I was web surfing.

I'm started to get a clearer picture... I welcome any more comments or more detailed info on this topic.

---

### Post by darsu on 2008-02-26
> **rendon said:**
> 

1) binaries = executables?


In this narrow context yes -"binary" being used as a general contrast to "source code".

> **rendon said:**
> 
2) executables are OS and processor architecture specific, that would explain why you have to choose the correct software for your operating system... however, I don't understand, when I choose the software for my operating system, it doesn't ask me which processor architecture I'm using.  Is that because just about everyone is using x86?  does the same binary for Anthlon work for x86?


Different processor architectures have differing instruction sets. This is why eg. Ubuntu is available separately for the i386 and AMD64 (and PowerPC? Others? I can't remember) architectures. The low-level machine isn't entirely mutually comprehensible.

---

### Post by rendon on 2008-02-26
> **darsu said:**
> 
Different processor architectures have differing instruction sets. This is why eg. Ubuntu is available separately for the i386 and AMD64 (and PowerPC? Others? I can't remember) architectures. The low-level machine isn't entirely mutually comprehensible.

So based on what we've said here...

Software, as I download it from different locations, doesn't specify on my processor architecture, providers only require me to download based on my OS.  So, I suppose the OS is doing the job of allowing the said binaries to work on the machine's processor architecture.  Thus, the binaries are designed for the OS and not for the processor architecture?  Otherwise every time I went to download a software it would not only ask me which OS I'm using but which processor I'm using.  


Any more input on this topic is welcome...

---

### Post by pmasiar on 2008-02-26
> **rendon said:**
> 1) binaries = executables?


Yes, on Windows: because MSFT does not want you to see source code of the program you execute.

No, on Linux. Linux has permission for each file to make it executable. So you can make Python, Perl, PHP, bash etc source file executable if you need it.

---

### Post by ZuLuuuuuu on 2008-02-26
Very good topic. I also wonder why there aren't binaries for Linux distributions in general. I mean why the binary files for Ubuntu does not work on Fedora or on other Linux distributions? If they do work then why people does not provide the binaries so that amateur users can easily install programs like in Windows?

---

### Post by pmasiar on 2008-02-26
> **rendon said:**
> 2) executables are OS and processor architecture specific, that would explain why you have to choose the correct software for your operating system... however, I don't understand, when I choose the software for my operating system, it doesn't ask me which processor architecture I'm using.  Is that because just about everyone is using x86?  does the same binary for Anthlon work for x86?


Operating system "remembers" what you installed: Windows on Intel pentium? Linux on Athlon 64? Etc. So ie  ubuntu has different repositiories for different architectures, and Windows runs on Intel architecture only (and generic [not optimized] programs do not use specific instructions from  specific architecture) (and I know about Windows for Alpha, thank you). gentoo distributes sources, and users compile sources to optimize code for given architecture.

Also, some programs written in crosplatform languages can be distributed on multiple platforms: 
- java binaries  created on Linux run on Windows and vice versa
- Python programs using only cross-platform libraries can run same code on either platform.

When you learn programming all this will be obvious, because it all are pragmatic decisions following from language decision.

---

### Post by darsu on 2008-02-26
> **ZuLuuuuuu said:**
> Very good topic. I also wonder why there aren't binaries for Linux distributions in general. I mean why the binary files for Ubuntu does not work on Fedora or on other Linux distributions? If they do work then why people does not provide the binaries so that amateur users can easily install programs like in Windows?

This may have to do with the nature of dynamic linking. When you compile a program that uses external libraries, you can compile it with either dynamic or static linkage. The latter means that the external libraries will be incorporated physically into your program executable, making it possibly very bulky but ensuring that everything needed by the program is included; the former means that whoever installs the program must also make sure he's got the same libraries installed in his system in order for the program to run. In some cases, he will need to have the same *versions* of the libraries as you did, and I seem to recall having gotten program errors because I had compiled a library with one compiler version and later used another version of the compiler to compile a program that uses the library. 

So, there are potential little pitfalls/inconveniences when you distribute Linux binaries. This is why Linux distributions have package management systems: they are automatised devices for distributing binaries, first and foremost. The package manager will take care that you always have correct, matching libaries and programs.

---

### Post by slavik on 2008-02-26
the registry is a setting database ... it is supposed to be the one place to store any configuration options a program needs. gconf is similar to this (except that the gconf backend is loads of xml files, whereas windows I don't know).

if you are running Windows, then 100% of the time, you have an x86 CPU (I consider amd64 to be part of x86 :)). If you are running Linux, then you might be using sparc (if this is a desktop system). If the application is intended to run on a server then there are many more 'requirements' which you would know about anyway. :)

As for different linux distros, they might keep libraries and system stuff in different places. For example, look at how Apache gets installed on Ubuntu and Fedora. In Ubuntu, you have a directory with all the modules it came with and create a symlink for any module you want to use in another directory. In Fedora, you have to actually change the config file. Same for how they manage config files. If your program depends on getting some info about apache configuration, the distro plays a huge role. Especially when you get Gentoo control freaks ;).

Another example: Did you install a library from a package by the distro maintainers and it's in /usr/lib or you compiled it from source with your custom patches and it is somewhere else.

---

### Post by rendon on 2008-02-27
> **pmasiar said:**
> Yes, on Windows: because MSFT does not want you to see source code of the program you execute.

No, on Linux. Linux has permission for each file to make it executable. So you can make Python, Perl, PHP, bash etc source file executable if you need it.

I understand that aspect of things...

But, for example, when I went to wesnoth.org to get the latest version of wesnoth (the game), they provide downloads for "source" and "binaries" for linux.  They provide binaries for different distros, and also have a special binary package which is supposed to work on all distros.

So anyway, I mean to say, I think that in linux you can also acquire some binaries without the source code, which means the binaries would be just like exe's... no?

Also, I believe that any source code, even from interpreted languages such as Python also need to make binaries.  I used to program in Python a lot, I remember that after executing my program.py, it would automatically make a (...urm?...forget) program.pyc (is that correct?) in the same directory, which was like the actual executable... I'm guessing this was the binary and/or executable, and this pyc if you were to open it in a text editor would look like all garbled gunk, ergo, was not source.  So technically couldn't I release that pyc to people and keep my code a secret if I so wished?  

I guess I'm trying to figure out why the wesnoth game offered these 2 choices?  I downloaded the source and made it myself, what would the difference be if I downloaded the "binaries"?

> 
When you learn programming all this will be obvious, because it all are pragmatic decisions following from language decision.


Well...  Like I said, I've been programming with different languages for years and I'm not exactly a newbie to linux, but I still didn't get this stuff :)  I know that I can take a python script and run it on any machine with the corresponding version of the Python interpreter installed, and I know that Java is cross platform... I've made dozens of programs with these languages and experimented before.   The thing that eludes me is more about the "installation" process and the differences (and benifits) with "installing" into the system or just running from within a directory.  

I think I'm getting the gist of it now.  It seems  you will do a big fancy "installation" process when you want to use system resources, and perhaps integrate the program into the systems menus.

But I still don't know why you have a choice of downloading "binaries" for a program.  Wouldn't downloading the raw source be faster and compiling the program yourself be more efficient for your particular system?

---

### Post by pmasiar on 2008-02-27
> **rendon said:**
> which means the binaries would be just like exe's... no?

binaries == executables
executable != .exe

.EXE is one of executable file formats for windows, and windows only. 
On Linux, you need some tricks (Wine etc) to execute window's .EXE file (and some luck). As I said before, source files (bash, Perl, Python) can be made executable on Linux, not only binaries.

I hope this is clear enough now. :-)

> Also, I believe that any source code, even from interpreted languages such as Python also need to make binaries. ....

 So technically couldn't I release that pyc to people and keep my code a secret if I so wished?    

Yes, you can make .pyc binaries, but usually you don't distribute them. It is easy to restore sources from it, so it is not very good way to obfuscate the code or make it secret.


>   The thing that eludes me is more about the "installation" process and the differences (and benifits) with "installing" into the system or just running from within a directory.  

Properly installing (and possibly building binaries) means your code will use proper libraries from your system, and not some incompatible random ones as found in your own custom directories.

> But I still don't know why you have a choice of downloading "binaries" for a program.  Wouldn't downloading the raw source be faster and compiling the program yourself be more efficient for your particular system?

For compiling you need to have all tools installed and environment set properly, including dependencies, which might not be case for   simple user desktop used for browsing internet and checking email. And if something will go wrong, some users will freak out.

Of course there are users who prefer compiling it all, and run Gentoo Linux distribution.

---

### Post by rendon on 2008-02-27
Got it!!!

Thanks, pmasiar!  Much clearer now, and it makes sense!  ;)

---

