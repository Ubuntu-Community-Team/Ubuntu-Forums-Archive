---
title: "c++ development  questions!"
date: 2014-07-10
forum: Programming Talk
---

### Post by thexnightmare on 2014-07-10
Dear,
I am new to ubuntu, and just compiled few programs on c and c++ in consoles.
I've installed netbeans and eclipse, but they just supported java, how to get the c++ versions?
and how to support other libraries augmented reality libraries?
Thanks

---

### Post by Warren Hill on 2014-07-10
Did you install eclipse from the software centre?

If you did then
 
> 
sudo apt-get install eclipse-cdt

Should get you going using eclipse with C / C++

If not you can get the download for the version of eclipse you have from the eclipse website.

---

### Post by thexnightmare on 2014-07-10
1. what about netbeans c++?
2- and where can i found a list of all software commands to install like this?

---

### Post by Warren Hill on 2014-07-10
I don't use netbeans but a quick search has just found instructions on configuring netbeans for c++ [here]("https://netbeans.org/community/releases/71/cpp-setup-instructions.html")

If you have run the command I gave in post #2 then you will already have the compiler etc.

But, if not you will need to install these first

> sudo apt-get install build-essential

Will get you the compiler, debugger and most of libraries you are likely to want.

For help in learning the command line see [here]("https://help.ubuntu.com/community/CommandlineHowto") and [here]("https://help.ubuntu.com/community/UsingTheTerminal").

---

### Post by thexnightmare on 2014-07-10
Thanks for the valuable infos.
Does there is exist a list where i can found each software name what is the package name for it to be able too install?
like eclipse software what is it's package name and so on?
2- in the software center i found that netbeans have haversion 7.1, but in the site there is version 8. so, can't i update it from software center or apt-get?
Thamks

---

### Post by Warren Hill on 2014-07-10
You can search in the Software Centre or install Synaptic Package Manager and use that to search.

You should be able to find synaptic in the software centre or if you like the command line 

> sudo apt-get install synaptic

---

### Post by thexnightmare on 2014-07-10
Wow thanks it is clear now.
Just last thing, if software in the site have newer verison but in the synaptic have lower version, does it normal? or i am doing search wrong way? like netbeans have ver 7 but in the site there is version 8/

---

### Post by shadesofoctober on 2014-07-10
Often, the packages in the repositories are older versions than the one directly from the creators.
That is normal, and is usually not an issue unless you really want newer features or fixes. In that case, you can often get the latest version directly from the developers, or get a repository that packages newer versions than the ones in the official repositories.

Generally I just use the version in Synaptic, unless there's some issue fixed by the newer version.
For instance, I use QT Creator personally for C++ dev under Linux. There has been an issue recently where you cannot launch executables from the IDE ('No executable specified'), but supposedly the version directly from Digia fixes that, so I may use that one instead.
(Anyone know if that stupid executable issue has been fixed yet? It's slightly annoying to keep a terminal open so I can run my program everytime I compile..)
I also used to go find newer versions of Xserver and Java 1.7 a while ago, but no longer need to.

Both Netbeans and Eclipse offer downloads from their site that you can extract to a folder and run from there. You can specifically download a C++ set-up version too. They have both run great for me. They also run just fine from Ubuntu repos. Keep in mind you still need Java installed to run those manually downloaded version!

---

