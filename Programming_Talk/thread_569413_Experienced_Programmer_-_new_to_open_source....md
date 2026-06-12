---
title: "Experienced Programmer - new to open source..."
date: 2007-10-07
forum: Programming Talk
---

### Post by jondecker76 on 2007-10-07
I would like to start developing - I am an experienced programmer, but everything I've seen so far is a little greek to me.

In order to start developing for Ubuntu, I feel that I need to start from the bottom and work my way up to understanding how everything comes together in an open source project. So I figured that I would:

1) Make a simple program
2) Learn about packaging and make a compliant .deb from it
3) Learn about version control techniques
4) try to get an ubuntu dev to sponsor me for some small jobs and work my way in

As of right now, I have a lot to learn. I have a milion questions, so I'm going to ask a few now..

Q) Can anybody give me a good definition of SVN? As I understand it, it allows devs to "check out" a file to work on it, along with keep track of version numbers.

Q) I'm having some trouble understanding what .configure, make and make install do. Yes, I know it compiles source and installs it, but I can't find a more technical definition anywhere. For example, how does the program that you are compiling know which directory to install to??

Q) For Ubuntu development in peticular, is c still preferred over python?

Q) Diffs..  Again another area lacking good definitions and information. As I understand it, a diff allows you to modify a program someone else wrote without actually changing their source code. But how do you make a diff? Do you have to have the original source and also a copy of the original source with your changes?

Programming isn't that hard. Its learning all this other linux specific stuff thats holding me back. Can anyone help me out?

thanks,
Jon

---

### Post by samjh on 2007-10-07
> **jondecker76 said:**
> As of right now, I have a lot to learn. I have a milion questions, so I'm going to ask a few now..I'm no expert at GNU development tools or open source project management, but I will try to answer.

> Q) Can anybody give me a good definition of SVN? As I understand it, it allows devs to "check out" a file to work on it, along with keep track of version numbers.SVN stands for Subversion.  It is a version-control system, like CVS.

Official website: [http://subversion.tigris.org/](http://subversion.tigris.org/)
Wikipedia: [http://en.wikipedia.org/wiki/Subversion_(software](http://en.wikipedia.org/wiki/Subversion_(software))

> Q) I'm having some trouble understanding what .configure, make and make install do. Yes, I know it compiles source and installs it, but I can't find a more technical definition anywhere. For example, how does the program that you are compiling know which directory to install to??Make and Configure are part of the GNU developer tool set.  Configure is used to set build options, while Make scripts the actual build process, solves dependencies, and also performs installation and cleanup (ie. make install, and make clean).

Make, in particular, is just a script.  There are some conventions for writing Makefiles (which Make uses to run), which includes what kind of functionality Make should afford for that project.  Make install and make clean, are functionality that may or may not be included by the developer, although they should be included by convention.

GNU Build System: [http://en.wikipedia.org/wiki/GNU_build_system](http://en.wikipedia.org/wiki/GNU_build_system)

Configure script: [http://en.wikipedia.org/wiki/Configure_%28computing%29](http://en.wikipedia.org/wiki/Configure_%28computing%29)

Make: [http://en.wikipedia.org/wiki/Makefile](http://en.wikipedia.org/wiki/Makefile)

> Q) For Ubuntu development in peticular, is c still preferred over python?Python is the officially-supported language of the Ubuntu project.  Application programming using Python is encouraged.  For system-programming, the obvious requirement is C.

> Q) Diffs..  Again another area lacking good definitions and information. As I understand it, a diff allows you to modify a program someone else wrote without actually changing their source code. But how do you make a diff? Do you have to have the original source and also a copy of the original source with your changes?Strictly speaking, a Diff is actually the DIFFerence between one developer's code and another code.  You could be working on code for a particular part of the project, and the Diff is the deviation between your code and the code officially in the trunk.

Patch is what allows you to modify a program by patching the targeted code with the code in the patch.

---

### Post by Auria on 2007-10-07
> **jondecker76 said:**
> 
Q) Can anybody give me a good definition of SVN? As I understand it, it allows devs to "check out" a file to work on it, along with keep track of version numbers.

It helps you both keep a history of all changes that happened in the code and lets many people work on the same code at the same time. You can also work on a feature without people getting it until it's stable, with branches. I suggest you read about it : [http://svnbook.red-bean.com/en/1.1/ch01.html](http://svnbook.red-bean.com/en/1.1/ch01.html) and google for more websites

> **jondecker76 said:**
> 
Q) I'm having some trouble understanding what .configure, make and make install do. Yes, I know it compiles source and installs it, but I can't find a more technical definition anywhere. For example, how does the program that you are compiling know which directory to install to??

configure looks at what computer you have, checks you have the requirements, generates makefiles appropriate for your computer. makefiles contain the information on how to build the project from the terminal. make install installs builts files into system directories (/usr/ and friends)
In depth info at : [http://en.wikipedia.org/wiki/GNU_build_system](http://en.wikipedia.org/wiki/GNU_build_system) What dir to install to is rather standard on Unix, it's in /usr or /usr/local by default. you can pass --prefix= to configure to change that to anywhere you want.

Note that many projects now find this is too complicated and use other build systems like scons or CMake.

> **jondecker76 said:**
> 
Q) For Ubuntu development in peticular, is c still preferred over python?


Depends what you're writing. If it's just a small utility, python will be much more productive than C. If you'll be coding some high-performance app, C/C++ will do a better job. There's also other languages, i suggest you use what you're comfortable with (unless you want to work on a project that is very specific about what langauge to use)

---

### Post by pmasiar on 2007-10-07
> **jondecker76 said:**
> 
1) Make a simple program
2) Learn about packaging and make a compliant .deb from it
3) Learn about version control techniques
4) try to get an ubuntu dev to sponsor me for some small jobs and work my way in


You can jump directly from 1 to 3 and 4 if you join existing running project. Which I cannot recommend strongly enough: better for you (learn from proven code) and for community (your code is accepted faster and used faster: with new project, chances are it will take you years to build community of users around it)

> Q) Can anybody give me a good definition of SVN?

[http://en.wikipedia.org/wiki/Svn](http://en.wikipedia.org/wiki/Svn)

SVN was created when CVS developers decided than fixing old CVS code does not make sense anymore, and they decided to start anew. It allowed them to add new nifty features, like renaming files, moving directories around, etc, not possible in CVS. But common approach is same (central server),. SVN is CVS done right: disk space is cheaper than bandwidth, and people do rename files.

> As I understand it, it allows devs to "check out" a file to work on it, along with keep track of version numbers.

Use good GUI tool for that. I use SVN workbench, and it is excellent. It also creates diffs and patches for you.

> Q) For Ubuntu development in peticular, is c still preferred over python?

It depends what you want... Yes, ubuntu does all internal projects in Python (sabdfl Mark strongly prefers Python, and it IS excellent language for most use scenarios). But you can pick existing project with any language you prefer, including some in C# or anything.

> Q) Diffs..  Again another area lacking good definitions and information. 

[http://en.wikipedia.org/wiki/Diff](http://en.wikipedia.org/wiki/Diff) Wikipedia knows EVERYTHING :-)

---

### Post by LaRoza on 2007-10-08
> **pmasiar said:**
> 

[http://en.wikipedia.org/wiki/Diff](http://en.wikipedia.org/wiki/Diff) Wikipedia knows EVERYTHING :-)


[http://uncyclopedia.org/wiki/Main_Page](http://uncyclopedia.org/wiki/Main_Page) knows more :D.

---

### Post by pmasiar on 2007-10-08
> **LaRoza said:**
> [http://uncyclopedia.org/wiki/Main_Page](http://uncyclopedia.org/wiki/Main_Page) knows more :D.

I love uncyclopedia! I would not claim that UCP has more articles than WP (obviously not), but many UCP articles are written with deep insight.

Maybe after exhausting all rational arguments, I need to answer more posts with citing UCP? I found interesting unknown "facts"  about [http://uncyclopedia.org/wiki/Ruby](http://uncyclopedia.org/wiki/Ruby) ...

---

### Post by LaRoza on 2007-10-08
> **pmasiar said:**
> 
Maybe after exhausting all rational arguments, I need to answer more posts with citing UCP? I found interesting unknown "facts"  about [http://uncyclopedia.org/wiki/Ruby](http://uncyclopedia.org/wiki/Ruby) ...

Yes, from now on, all citations come from Uncyclopedia, at the very least, we'll all get a laugh. (Read the article on KDE)

---

### Post by jondecker76 on 2007-10-08
Thanks for all of the replies.. I've been doing a lot of reasearch which has brought up a question on revision control...

I read the svn book online and have a very good grasp on in now. However, I am going to do a small project to get more familiar with it - as I have never coded with any kind of revision control software before.

But, now I have to make a choice..  SVN sounds very exciting to me, but doing some reading on the ubuntu developers pages, it appears that they use Bazaar for revision control. Which should I set up for my own personal learning tool? At this point from what I read I think I would prefer svn (bazaar's distributed scheme seems a little chaotic to me). But If I take my time to learn svn, will I have to re-learn a new revisioning system in moving to bazaar?

---

### Post by wolfbone on 2007-10-08
I was going to suggest that it wouldn't  matter much which version control systems you used if you were also using  a powerful tool such as Emacs, for example. Emacs's VC handles several backends, including Subversion, but I see the list does not include Bazaar.  Apparently there are old version control systems and modern ones; Subversion is old, Bazaar is modern, and for Bazaar you'd need DVC:

[http://download.gna.org/dvc/](http://download.gna.org/dvc/)

So although you get a great programmer's tool (and a whole lot more) - especially with the latest Emacs snapshots - it doesn't solve the annoyance of the plethora of version control systems in this particular case.

---

### Post by asoare on 2007-11-24
> **pmasiar said:**
> You can jump directly from 1 to 3 and 4 if you join existing running project. Which I cannot recommend strongly enough: better for you (learn from proven code) and for community (your code is accepted faster and used faster: with new project, chances are it will take you years to build community of users around it)

Hello, I am a beginner in programming ( advanced in algorithmic ), I was taught Pascal (worthless) in school and now am learning C (at university, first year). I have made the switch to Ubuntu and now i use it as my primary OS, I just love it. I was wondering how I could get involved in the open source community, I think this is a great way to learn and at the same time help the open source communities. 
But I have no ideea what I could do ( I know little right now ) and where I could sign up to help on a project.
Can someone enlighten me a little ? :)

Thank you.

---

### Post by ThinkBuntu on 2007-11-24
Subversion is probably the most popular version control software for new software projects, and it was built with lessons learned from CVS which you may have used. It allows you to download a project's files (called "checking out"), commit your own changes, download newer versions that other developers have edited, etc. A new project I'm joining as a contractor this week uses Subversion. You may come across projects using Bazaar (actually developed with desktop users and non-developers in mind, if I understand correctly) and Mercurial.

Good luck!

---

### Post by pmasiar on 2007-11-29
> **asoare said:**
> But I have no ideea what I could do ( I know little right now ) and where I could sign up to help on a project.

Find any project you are interested to hack and learn, and ask developers.

---

### Post by iharrold on 2007-11-29
Here is what I did to get started:

```
sudo apt-get install build-essential
sudo apt-get install gdb
```

--- To install WxWidgets ----
```
curl http://apt.wxwidgets.org/key.asc | sudo apt-key add -
wget http://www.tt-solutions.com/vz/key.asc
sudo apt-key add key.asc
```

Then add the following sources to the /etc/apt/sources.list file
```
gksudo gedit /etc/apt/sources.list

# wxWidgets/wxPython repository at apt.wxwidgets.org
    deb http://apt.wxwidgets.org/ gutsy-wx main
    deb-src http://apt.wxwidgets.org/ gutsy-wx main
    deb http://apt.tt-solutions.com/ubuntu/ gutsy main 
```

Then Update the list on the machine.
```
sudo apt-get update 
sudo apt-get dist-upgrade
```

Now install wxWidgets
```
sudo apt-get install libwxgtk2.8-0 libwxgtk2.8-dev wx2.8-headers wx-common
sudo update-alternatives --config wx-config
 
```

-- To install an IDE... I choose Netbeans... Code blocks is an alternative and can be found [here]("http://wiki.codeblocks.org/index.php?title=Installing_Code::Blocks_nightly_build_on_Ubuntu")
Install Net beans IDE
```
sudo apt-get install netbeans5.5
```

This got me the g++, wxWidgets for C++ and an IDE.  Then go to the Netbeans wesite [here]("http://www.netbeans.info/downloads/index.php") and download the C++ add ons .

Help on installing wxWidgets to Netbeans can be found [here.]("http://www.wxwidgets.org/wiki/index.php/Netbeans")

Then you should be all set.

---

