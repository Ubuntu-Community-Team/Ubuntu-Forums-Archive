---
title: "Java and c++"
date: 2010-12-29
forum: Programming Talk
---

### Post by simolokid4 on 2010-12-29
Hi ubuntuforums,

To begin; I know OOP Java. Lets say i can dream the basic concepts and would to learn a ****-load more. Learned myself ASP.NET (C#) in 45 minutes yesterday (the basics ofcourse).

Okayz, now move on the the core of my question;

Since one of the finishing-touches of an application is that it has its own icon to launch it (For instance, Skype has that S-symbol) and Java currently only lets me generate a runnable .jar file which looks.. ugly.

I'd like to know how to work around this. I'm also interested in c++ but I haven't been able to find a GUI - Designer for c++ yet. Or am I mis-grasping the concepts of c++ here?

So basicly, after knowing the basiscs and some extras of java, what would you recommend I do next? I'd like a programming language with some kind of memory management (combined languages are fine to, c++ and java for example) which lets me put in my own launch icon (stupid requirement but hey.. im hobby-ing here =P ) and is preferably launch and developable in both ubuntu 10.10 and windows.

Thanks for all the pointers I may get ;)

Kind regards,

Simolokid

---

### Post by Simian Man on 2010-12-29
On Linux, the applications icons are not part of the executable file as they are under Windows.  To add your program to the menus with an icon, you need to create a .desktop file in /usr/share/applications and an icon in /usr/share/pixmaps.  You can look at the .desktop files in /usr/share/applications to see how to write them.  This is a nice way to do it because icons and launchers are handled the same whether they are Java bytecode, C executables or Python scripts.

As for languages, I would stick with Java.  There is a lot more to learning how to program than learning language syntax.  Often when people are beginning, they learn the syntax of a dozen languages without ever learning to program effectively in any of them.  Also there is no point learning about memory management as a beginner; it's a relatively unimportant and uninteresting part of programming.

---

### Post by simolokid4 on 2010-12-29
Probably my bad here,

But that kinda raises more questions then it answers =P

- How would i create a program in java that would have it's own icon under windows aswell?
- When i learn the syntax of a language, how do i learn to use it effectlvly besides making a gazlillion programs in that language? And since Java usually takes a lot of bashing because of it's lack of memory management I'd like to learn it =P
- I wouldn't consider myself as a beginner, more of a 'i know the stuff but im not intermediate yet.. ' But to have some kind of question on the '-' here; c++ gui designers.. misgrasping the concept of the language or am I not looking in the right direction?

Also, java and c++, I'm not hearing a lot about that combination.. why not? ;x

---

### Post by dwhitney67 on 2010-12-29
> **simolokid4 said:**
> 
- When i learn the syntax of a language, how do i learn to use it effectlvly besides making a gazlillion programs in that language? 
Thanks for the laugh!  That's exactly how one becomes effective... by developing applications.  Probably not a gazillion, but in the hundreds for sure.

In the real world, developers run off to the corner of the office to develop code, which then at a later time, is peer reviewed by other developers.  This is where the fun begins, and of course the learning.

---

### Post by Simolokid on 2010-12-29
> Thanks for the laugh!  That's exactly how one becomes effective... by  developing applications.  Probably not a gazillion, but in the hundreds  for sure.

In the real world, developers run off to the corner of the office to  develop code, which then at a later time, is peer reviewed by other  developers.  This is where the fun begins, and of course the learning. 	

Heh, nice to have brightened up your evening ;)

But, After some googleing; as far as this i understand:

I can make a skeleton in java and then write the logic in c++ (aka memorymanagement + java = imba? =P ), I can make guis in both java and c++ ?

And last but not least, own icon as launcher for java/c++ apps.. possible in windows? :)

---

### Post by Simian Man on 2010-12-29
> **simolokid4 said:**
> - How would i create a program in java that would have it's own icon under windows aswell?
Sorry I don't know.

> **simolokid4 said:**
> - When i learn the syntax of a language, how do i learn to use it effectlvly besides making a gazlillion programs in that language?
As dwhitney67 said, you don't.  You learn to employ algorithms and data structures in your language to solve real problems.  The good news is that once you do this for one language, the knowledge transfers almost totally to other languages you learn.  For example someone who has years of experience with Java will be a better C++ programmer after a week than someone who has been programming in C++ for six months.

> **simolokid4 said:**
> And since Java usually takes a lot of bashing because of it's lack of memory management I'd like to learn it =P
How is that?  Java handles memory management for you via the built-in garbage collector.  Doing it yourself usually has no advantage.

> **simolokid4 said:**
> c++ gui designers.. misgrasping the concept of the language or am I not looking in the right direction?
QT Creator is probably the most complete C++ GUI editor for Linux.  There is also Glade for GTK+ but I haven't used it before.

> **simolokid4 said:**
> Also, java and c++, I'm not hearing a lot about that combination.. why not? ;x
You mean using both in the same program?  That's not a great idea because they're pretty much the same type of language.  Usually when people use multiple languages for one project it's because they each bring something different to the table, like C and Python.

---

### Post by dwhitney67 on 2010-12-29
During the last 20 years, aside from one little gig that lasted 6 months, I have never worked on a software development project under Windows.  Do people even do that anymore? I thought it was all Linux nowadays?  Hmm, I guess people still like to waste their money on M$.  Such a shame.

---

### Post by Simolokid on 2010-12-29
Ghehe.. I didn't think of this before.

I Could write a simple installer that will check if jre has been installed, and then just make a shortcut with custom icon in windows to that .jar =P

Quick & dirty, but it will work ^^

Oh and what makes the combination of c and python so great?
Havent gotten a clue what each of those does. Im guessing python gui and c for logic but thats just a wild guess.

So basicly my answer is; continue with java and find out how to make a simply installer for windows and .deb for linux ^^

Then the last question I can think of; Any programming things I should google to get going?

I've heared about JREE and stuff but I haven't really looked into it yet. Also hibernate and stuff.

'What would be the next logical term to google? '

Thanks for the fast responses btw. I greatly appreciate it.

---

### Post by PaulM1985 on 2010-12-29
It seems that you are looking a lot at combining languages...  

I would probably recommend, if you are a beginner, to work on just on language per project rather than group them together because one thing is slightly better for X and another slightly better for Y.  You may end up getting bogged down in getting the languages to "talk to each other" rather than actually making the thing you want to make.

Once you have done this for a while, then maybe consider a different language.

After that, when you identify a problem that needs solving, you will be able to see the entire problem and consider which language would be best suited overall to complete the task.

(But talking about mixing languages, I personally would not mix Java and C++ and instead have C# and C++. C# has greater support for it by the use of interops and managed C++ wrappers for OO design.  Anyway, as I said before, stick with one language, don't mix unless you need to).

Paul

---

### Post by r-senior on 2010-12-29
> **simolokid4 said:**
> - How would i create a program in java that would have it's own icon under windows aswell?
Are you using Netbeans or Eclipse? Both Java programs that are commonly used on Windows/Linux/Mac OS. Have a look at how they solve the problem. (I think you'll find it's separate installers).

---

### Post by Simolokid on 2010-12-29
r-senior;

Yes im using Eclipse.

But I wouldn't have a clue about decompiling that executable into source, then diving in that source where I hope to find something refering to... eclipse.ico or something.

Could you give me a bit more of a pointer? ;x great thinking, but I'm afraid I'm not that awesome yet =P

---

### Post by r-senior on 2010-12-29
I wasn't thinking on those lines. If you look at your Eclipse or Netbeans "executable", you'll find it's actually a shell script:

```

$ file /usr/bin/eclipse
/usr/bin/eclipse: POSIX shell script text executable

$ file /usr/bin/netbeans
/usr/bin/netbeans: POSIX shell script text executable

```

On Linux, Eclipse then fires off a small (19k) executable in /usr/lib/eclipse/eclipse and you are at a dead end.

On the other hand, Netbeans goes through a few hoops before ending up in /usr/share/netbeans/platform12/lib/nbexec which is a shell script that builds up a java command line - searching for the "java" executable, working out a classpath argument and calculating things like JVM heap size. Presumably Eclipse is doing that in the executable I refer to above.

I was thinking that you could adopt a similar approach, i.e. for Linux have a shell-script launcher that can be added to the menu programmatically with an installation script, along with its icon? (This is basically adding a .desktop file in /usr/share/appliciations and there's an example [here]("http://www.stchman.com/menu_entry.html") but I don't know if it works).

Obviously on Windows it's a different ball game altogether, which is what I meant by separate installers.

---

### Post by Simolokid on 2010-12-29
> **r-senior said:**
> I wasn't thinking on those lines. If you look at your Eclipse or Netbeans "executable", you'll find it's actually a shell script:

```

$ file /usr/bin/eclipse
/usr/bin/eclipse: POSIX shell script text executable

$ file /usr/bin/netbeans
/usr/bin/netbeans: POSIX shell script text executable

```On Linux, Eclipse then fires off a small (19k) executable in /usr/lib/eclipse/eclipse and you are at a dead end.

On the other hand, Netbeans goes through a few hoops before ending up in /usr/share/netbeans/platform12/lib/nbexec which is a shell script that builds up a java command line - searching for the "java" executable, working out a classpath argument and calculating things like JVM heap size. Presumably Eclipse is doing that in the executable I refer to above.

I was thinking that you could adopt a similar approach, i.e. for Linux have a shell-script launcher that can be added to the menu programmatically with an installation script, along with its icon? (This is basically adding a .desktop file in /usr/share/appliciations and there's an example [here]("http://www.stchman.com/menu_entry.html") but I don't know if it works).

Obviously on Windows it's a different ball game altogether, which is what I meant by separate installers.

Damn, that would require bash-scripting I'm thinking. A lot more then echo "hello world" i dont have for bash-scripting =P

Also, I dont have the eclipse script thing in /usr/bin ur refering to. I simply downloaded eclipse from the site and extracted the folder on my desktop. Since the last time i tried eclipse from the repo it wouldn't get along with svn. 

So it's a little out of my league I'm afraid.

A google search of '.deb from .jar' did turn up some interesting conversion methods but non that took the hassle of changing the icon. So we're back to scrap. >.<

Thanks a lot for your answers so far. Looks like I'm going to need to learn how to bash script in order to be able to distribute my java projects in a noob-friendly manner =[ (aka, family, friends who can barely check their email =P)

---

### Post by Some Penguin on 2010-12-29
Or you could realize that cross-platform installation of Java software probably isn't a task unique to you, and look for prebuilt stuff rather than re-inventing that particular wheel.

[http://ewert-technologies.ca/blog/blog5.php/articles/install-cross-platform-java-applications]("http://ewert-technologies.ca/blog/blog5.php/articles/install-cross-platform-java-applications")
in particular

[http://izpack.org]("http://izpack.org")

---

### Post by Simolokid on 2010-12-29
Holy... thats look promising.

Going to mark this thread as solved.

This'll do. Thanks a lot.

Well, added a solved tag instead ><

---

### Post by trent.josephsen on 2010-12-30
> **Simolokid said:**
> Damn, that would require bash-scripting I'm thinking. A lot more then echo "hello world" i dont have for bash-scripting =P

Also, I dont have the eclipse script thing in /usr/bin ur refering to. I simply downloaded eclipse from the site and extracted the folder on my desktop. Since the last time i tried eclipse from the repo it wouldn't get along with svn. 

So it's a little out of my league I'm afraid.

A google search of '.deb from .jar' did turn up some interesting conversion methods but non that took the hassle of changing the icon. So we're back to scrap. >.<

Thanks a lot for your answers so far. Looks like I'm going to need to learn how to bash script in order to be able to distribute my java projects in a noob-friendly manner =[ (aka, family, friends who can barely check their email =P)

Did it not occur to you that in order to achieve what you didn't know how to do, LEARNING might have to take place? :rolleyes:

---

