---
title: "Is Ubuntu For Programmers?? (or students??)"
date: 2009-12-16
forum: Programming Talk
---

### Post by king_009 on 2009-12-16
Hii there....i have just installed Ubuntu 9.04 and found C/C++ compilers in build-essentials... moreover in some other thread, one forum staff memeber said that ubuntu is for the developers...

So guys please tell me... s it good to use ubuntu for programming??
I tried a normal C++ program of "Hello World". n actually found many mistakes in me.. n liked that ubuntu uses totally focussed approach in compiling.. 
i never cared for writing "using namespace std;" in turbo C++ which i used on windows platform (Which was a bad habit though..)

anyways.. i found C, C++ in ubuntu... 
can u please tell me which other programming languages come powerpacked in ubuntu?
1 more doubt..
should i use ubuntu for programming my college projects?

ok this is last qstn most important..
can i install Microsoft's Visual Studio in ubuntu? if yes.. please provide me the link from where i can get VS for ubuntu. i have VS2005 and VS2008 setups but i dont think it would support ubuntu..

---

### Post by theozzlives on 2009-12-16
Ubuntu does have several languages. One that sparked my interest is Lazarus, it uses Pascal, although I haven't messed with it much. No time.

Visual Studio is a Microsoft product, and they aren't gonna make anything for Linux.

---

### Post by sisco311 on 2009-12-16
The stickies in the  [Programming Talk]("http://ubuntuforums.org/forumdisplay.php?s=&daysprune=&f=39") forum should answer your questions.

---

### Post by plusnplus on 2009-12-16
Hi king_009,

it is better learn opensource programming language in opensourse os/ platform.
example: perl and php

---

### Post by rob-ward on 2009-12-16
yes Ubuntu is very suitable for programming, I use it and nothing else for all of my university work(MEng Software Engineering). Ubuntu supports dozens if not hundreds of languages. As you seem to be leaning towards C++ what you probably want is an IDE to do your programming in. There are a large amount out there, I would probably recommend Codeblocks as this is cross platform so you could use it on windows if you needed, however others include Geany, Anjuta, kdevelop, Eclipse an many more.

All of the ones I have mentioned are available in the Ubuntu repositories so are easy enough to install.

Note that for eclipse(which is also cross platform) you need a plugin called Eclipse CDT in order to program C++ if you google it there are lots of instructions.

Hope that helps.

Rob

---

### Post by Dan48p on 2009-12-16
I am at the end of my C programming class in school and all of the computers in the lab are running Ubuntu.  In fact it is required that our programs compile and run properly in linux.

I use the "Kate" text editor (which also requires the installation of "Konsole" to use the built in terminal) to do all of my programming. I haven't had any problems with anything working correctly though the only other programming I have done is VBasic in Visual Studio. The stuff I have been doing recently is primarily numerical analysis, prove the calculus type of stuff, so I have no experience with making graphics type things in linux.

I use ubuntu 9.10 on both of the computers I use on a regular basis and have only had a few problems using these 'puters for school.  Even though these problems may be something that can be fixed, as a full time engineering student/full time diesel mechanic, I really haven't had time to figure out how to make everything work correctly (hence the switch to linux in the first place).

I haven't yet gotten a program that opens .docx files properly formatted, I tend to lose some images and superscripts/subscripts.  Though I have both MSWord 2007 and the recent version of open office installed.  I'm farily certain that there are fixes for this out there and I will look into it on semester break.

The other problem I had was with running a Java Runtime thing called "Molecular Workbench" that I had to use for chemistry classes.  I had a problem getting the text fonts to work correctly making it unable to read the questions I was asked. My teacher told me that she has the same problem with her Mac so I believe the problem may be related to that particular software.

While I use Ubuntu on a daily basis and rarely boot into windows (except to play some games) I'm not quite ready to delete my Windows partition from my desktop.

I'm not really sure what all you wanted in response to your question, but I figured I would share my experiences.

---

### Post by king_009 on 2009-12-16
Okk guys... please tell me does ubuntu supports java???
how to do java programming in ubuntu

---

### Post by Redache on 2009-12-17
> Okk guys... please tell me does ubuntu supports java???
how to do java programming in ubuntu

Ubuntu supports nearly every programming language in existence. The ones it doesn't are typically proprietary languages(like Visual Basic).

Java can be installed by getting the jdk, I think it's in the repos.

I'd also recommend installing either Eclipse or Netbeans as they are both decent Java IDE's, and I think they will grab the jdk for you.

I'd also recommend looking into Python if you're trying to learn languages as Python is a good language for prototyping or writing applications in general. It's also useful as a scripting language.

If you want to Learn Java on the other hand, I'd recommend reading the Sun Java tutorials to get you started.

---

### Post by nishant.singh28 on 2009-12-17
As far as Java programming is concerned, you can simply install jdk, write a program in any text editor you like (vim, kwrite, gedit) and compile it in terminal by typing

$ javac <path of program code>

and run it by typing

$ java <name of main class>

---

### Post by KeLa on 2009-12-17
Try NetBeans it's crossplatform including c/c++, java, perl, php etc...
I have used it in Windoze, Mac and Linux and it's in Ubuntu repos.
After install you can easily add more modules (language supports etc) in to it.

---

### Post by jespdj on 2009-12-17
Ubuntu is great for programmers, because the source code of the whole operating system and almost all programs is freely available and there are lots of tools for developers available for free.

> **king_009 said:**
> Okk guys... please tell me does ubuntu supports java???
how to do java programming in ubuntu
Ofcourse Ubuntu supports Java. Install the package **sun-java6-jdk**:
```
sudo apt-get install sun-java6-jdk
```
Have a look at [Sun's Java tutorials](http://java.sun.com/docs/books/tutorial/) for a good start with Java.

If you want a good IDE for Java and other programming languages, I'd recommend [NetBeans](http://netbeans.org/). Installing it is easy: download it from the website and run the installer.

---

### Post by king_009 on 2009-12-17
> Ubuntu is great for programmers, because the source code of the whole operating system and almost all programs is freely available and there are lots of tools for developers available for free.

hmmm thanks for the info guys..
so i think if i wanna excel in programming.. i must use ubuntu EXCEPT while using .NET languages...

mm many of friends here also advised me to learn python, php, perl...
so, i'll download the tutorials soon from net... thank you friends.... you all rock :guitar:

so guys please tell me in the commercial side of software development, which languages are necessary...

i had done C, C++, Java, C# and ADO.NET also... n soon gonna do ASP.Net....

n many posts i found in this forum about python.. so i m getting intrest in learning python....

Which languages are must today for becoming a good programmer???:confused:

i m just a student right now n soon gonna enter this field within  6 months...

---

### Post by CptPicard on 2009-12-17
> **king_009 said:**
> 
i had done C, C++, Java, C#


These languages all come from the same family more or less, so they share similar ideas in their construction and way of doing things.

> 
n many posts i found in this forum about python.. so i m getting intrest in learning python....

... so, perhaps Python would be an interesting addition to your toolkit. It's very convenient and "fast to use", plus exposes you to concepts you would be hard-pressed to find in the aforementioned group of languages. Besides, having a flexible scripting language at your disposal is always a good thing.

> 
Which languages are must today for becoming a good programmer???

IMO one is a "good programmer" once one has had enough experience in different kinds of programming languages that learning yet another new programming language is no longer a problem. Then there is also the algorithmic/design aspect of programming that transcends language completely... but different languages can take different "views" of things even in this regard when you start implementing things idiomatically in them.

In a lot of ways, you can't go badly wrong with a combination of C, Python, and either Java or C# to begin with. Add C++ if you feel like it or need it.

---

### Post by king_009 on 2009-12-17
thank u for the info.....

loved ubuntu...

are there any certification courses of ubuntu???
havent heard of any in india....
do we have certification centres in india??
if so... please let me know the details....
thanks in advance....

---

### Post by Redache on 2009-12-17
I'd recommend learning Haskell or O'Caml if you really want to become a "Good" programmer as functional Programming Languages have a different programing paradigm.

---

### Post by nvteighen on 2009-12-17
Ubuntu ships even esoteric stuff like Forth, so expect all major programming languages to be supported :p

I suggest you to look at Python. Look at the infernal amount of threads we've got on the topic...

---

