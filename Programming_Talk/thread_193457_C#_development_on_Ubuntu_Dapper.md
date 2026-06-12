---
title: "C# development on Ubuntu Dapper"
date: 2006-06-10
forum: Programming Talk
---

### Post by Z13 on 2006-06-10
I am new in Linux technology and want to know what are the alternatives for Dapper C# programming. I've been using Visual.Net by now but recently I've quit using Windows (for hundreds of reasons).
I've tried myself to find out what are the options for me and read some info about the Mono and Monodevelop applications. It seems to me (I may be wrong though) that Mono is build only for RedHat, Fedora and Suse platforms, not also for Debian Ubuntu. 
And Monodevelop is for Ubuntu users, right? Anyway, I read some posts and people were saying Monodevelop (even under the last version, 0.11) builds applications that run extremely slow. Is that true?

Thank you for your time.

---

### Post by jbtechie on 2006-06-10
Hello,
For linux, and other platforms, Mono is really your only practical .Net implementation.  I've only used Mono, and its related tools, on Ubuntu.  So far, even with the relatively young age of all the Mono and related software, it's a fairly complete and adequate development environment for most situations.  The version(1.1.13.6) in the repositories is considered the latest stable release of Mono, but I would recommend compiling it from source(version 1.1.15).  I know at least in the i386 version in the repository, GZipStream wasn't working correctly for me, but building everything from scratched fixed that, and I haven't found anything else that doesn't work where expected except where stated explicitly.  You can find the packages [here]("http://go-mono.com/sources-latest/").  

I don't know how familiar you are with compiling linux packages from source, but the Mono compilation is fairly straightforward.  Just ./configure the sources in a logical order based on dependencies and apt-get install packages that are missing for each project.  You'll have to install many packages to satisfy the configuration requirements.  Then, make, sudo make install each one. 

As for the performance, MonoDevelop is only an IDE and the applications built with it should be just as fast as anything built with the Mono C# compiler(assuming you are programming in C#).  Now, as for performance relative to MS's implementation of the .Net platform, I have done no tests, but the performance for things I've compiled and run on both is perceivably the same.

---

### Post by Z13 on 2006-06-10
Thank you jbtechie for the information. As I said before, I'm new in Linux technologies (to be more specific, it's my 4th day of using it) and I've asimilated lots of information about Ubuntu and its structure, by now. Don't think I'm ready to compile Mono's source code without getting a terrible headache. It's still odd to me the fact that I have to install lots of programs for getting what I need and also that I have to use the console commands.

For now I think I'll go for the already tested, compiled and packed versions. Still, don't know which one to chose. What package is designed for Ubuntu? (I don't mind the .rpm extension of some archives; I learned how to convert them to .deb). Will you please indicate me which link should I chose from [this]("http://www.mono-project.com/Downloads") page?

Thank you in advance. :)

---

### Post by muzaki on 2006-06-10
i think you can install it from Synaptic  (System>>Administration>>Synaptic)
search for mono, then install package you want

---

### Post by Z13 on 2006-06-10
Muzaki, I have tried before what you adviced me to, but the Synaptic search command doesn't seem to show any results for Mono key-word.

---

### Post by muzaki on 2006-06-10
may be you should update your repository
I use this one
[http://www.ubuntuforums.org/showthread.php?t=185758](http://www.ubuntuforums.org/showthread.php?t=185758)


[[IMG]http://img82.imageshack.us/img82/6149/screenshot7fd.png[/IMG]](http://imageshack.us)

---

### Post by Kimm on 2006-06-10
Perhaps you need to enable extra repositories? Search the forum for Universe and Multiverse repositores.

I think mono has its own repo too. Back when I was using breezy I used this to get the latest version of Mono.

Mono is a great framework. If you know C# and still want to use it, then do so, its truly marvelous. (try the Banshee media player, its written in Mono)

---

### Post by asimon on 2006-06-10
[QUOTE=Kimm]Perhaps you need to enable extra repositories? Search the forum for Universe and Multiverse repositores.[/quote]
Actually mono is part of main, but some other stuff like monodevelop is in universe.

---

### Post by Z13 on 2006-06-10
Muzaki, I updated my repository and eventually installed the Mono compiler and the IDE called MonoDevelop.

I want to thank you all who replied for trying to help me.

As a Linux beginner  I may say that there are some differences between C# programming in Windows and the one in Linux + the MonoDevelop form designer is not actually what I was looking for - too many clicks needed (doesn't even accept ENTER for applying changes to a property). :???:

How did you folks manage to change your working style when moving from Visual Studio.Net to MonoDevelop? I didn't either get the idea why when inserting a button to my form it is maximized (it covers the whole form area) and apparently, bounded to the form's edges.

---

### Post by jbtechie on 2006-06-10
Z13,
Well, the reason the GUI designer seems different is because it's not using the Windows Forms library.  It's using GTK-Sharp, which is basically an object oriented managed wrapper around GTK+, a well known and used cross platform GUI library.  Other language bindings to GTK+ usually use a library named Glade with a Glade library frontend to create XML describing a GTK+ user interface.  The library can export C and C++ code, but I think because of the power of reflection, and other benefits of the platform, Mono developers decided to create a GUI designer from scratch.  But, you still have the option to use Glade and Glade-Sharp, or you can write code interfacing with GTK-Sharp directly.  Also, you can even use Window Forms directly without a GUI designer, but it's not recommended.  The System.Windows.Forms is not part of the ECMA, so MS doesn't have to release information on how it works, so you'll be working with a buggy library that looks ugly on any platform other than windows.  And understandably, it's because it was not intended to be used on any platform other than Windows.

> It's still odd to me the fact that I have to install lots of programs for getting what I need and also that I have to use the console commands.

Well, the reason you would have to install so many packages is because Mono contains many wrappers around very stable and popular libraries, so it needs all of the development packages for each of those libraries.

---

### Post by guitarded on 2006-06-10
i have been developing in c# since the beta stages.  i currently develop c# applications for a healt care company.  at home, i have 5 machines, all but one are exclusively linux.  my one and only winxp machine is used for windows development.  like you, i have made the switch to linux.  in fact, when i develop on my windows machine, i remote in via my one of my linux machines. 

anyway, i tried mono and if you are coming from heavy visual studio background, you will not find it very similar.  so to used it, you have make a mental switch.  

so, for me, personally, i have decided to code in java when using linux using netbeans as my ide.  infact, the newest version of the ide has some features that vs.net did not have.  prior version forced you to use layout manager, however, now that is managed by netbeans (of course, you can still manage it yourself).  so now, i develop c# in my day job and java for all other programming.

if you decide to try netbeans, run the demos, then you will see some of the nifty gui layout features of the ide.

then, of course, there are all the other linux ide's, C, C++, python, ruby...

---

### Post by Z13 on 2006-06-10
[QUOTE=guitarded]
anyway, i tried mono and if you are coming from heavy visual studio background, you will not find it very similar.  so to used it, you have make a mental switch.  
[/QUOTE]

Actually I've been using Visual C#.Net since the beginning of 2003 and felt pretty confortable using the .Net framework with a simple and powerful C, after experiencing alorithms in ol' C++ at school. 

Anyway, this year I'm going to college and have to learn Java too (but I heard C# is a mixture between Java and C++, so I don't worry) and probably I'll try netbeans IDE, like you said. Still, have to get used with MonoDevelop IDE 'cause want to keep working in C# (I must say it's harder than smth I tried some time ago: to work with Borland C# :p ).

---

