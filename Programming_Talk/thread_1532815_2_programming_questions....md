---
title: "2 programming questions..."
date: 2010-07-17
forum: Programming Talk
---

### Post by bocaccio on 2010-07-17
What do you use? In windows i used visual studio and i think eclipse too. I am talking about maybe either C++ or C# 
I took vb.net in school last class and wanna learn something else now. 
I hear something called notepad ++



I wish there was like a programmers game where you could do little challenges to keep learning to write code. I say this because I really don't know what to do if im not in class doing an assignment. What to stay ontop of your game writing code.

---

### Post by linux18 on 2010-07-17
Python is pretty much the standard if you want to start programming in linux, but c++ is there too just grab a web tutorial and fire up geany or gedit ( text hightlighting ftw!!! )

---

### Post by webtechquery on 2010-07-17
Geany is a good tool for programming.. in some cases, you can say its more lil advanced than Notepad ++

Check out the following link for some more details about Geany:
[http://www.webtechquery.com/index.php/2010/06/geany-ubuntu-ide/](http://www.webtechquery.com/index.php/2010/06/geany-ubuntu-ide/)

Thanks

---

### Post by theraje on 2010-07-17
> **bocaccio said:**
> I wish there was like a programmers game where you could do little challenges to keep learning to write code. I say this because I really don't know what to do if im not in class doing an assignment. What to stay ontop of your game writing code.

Ah, reminds me of an OLD game called "Robot Odyssey" (although that was for electrical engineering, rather than programming... still though). Those were the days! :)

As for your questions, in Windows I use Code::Blocks (with MinGW compiler) for C++ and Visual Studio Express for C#. In Linux I use the good old command line GNU Compiler Collection with make files, along with gedit for an editor.

Note that there is a big difference between language compilers and IDE's (editors). The compilers turn code into assembly or bytecode that the computer can run. The IDE's are programs that are used to make coding and editing easier and more convenient. :)

Notepad++ would be an IDE, although it's a glorified text editor.

I never got much into Python, but when I was, I used IDLE as the IDE... I'm sure it's still out there (it's been like eight years since I touched Python).

---

### Post by Tech2077 on 2010-07-17
For linux development, you can pick a language out of a hat, and theirs the tools and tutorials to get you going. On ubuntu, you have bash, gcc, python, perl, and m4 (I think, correct me if i'm wrong) installed by default, so if you don't want to look far, get a nice tutorial on one loaded, and just open up gedit and a command line and you can go far with that. Eventually, ide's like vim, Emacs, and Eclipse make sense, but only after you get into software dev, and even a lot of projects are managed with text editors and notepads :P. For a pointer(pun intended), learn Bash and C.

---

### Post by dv3500ea on 2010-07-17
I use [geany]("apt:geany") + whatever language I feel like. My current favourite is [ruby]("http://www.ruby-lang.org") (which can be really fun if you use it together with [shoes]("http://shoes.heroku.com/")). As for programming games, you could try [kturtle]("apt:kturtle"). For programming challenges you could try the Beginner Programming Challenges in this forum and there are other websites such as this one [http://www.challenge-you.com/challenges]("http://www.challenge-you.com/challenges?sortby=rating") which has lots of challenges to try.

---

### Post by PaulM1985 on 2010-07-17
You can still use Eclipse on Ubuntu to carry on with C++ work.

If you did VB.NET and C#, you can use Mono and Monodevelop.  Monodevelop is an IDE which allows you to write C# programs.  It also has support for VB.NET but I am not sure how good the support is for that. The C# support is pretty good.

It may be better to stick with a language that you already know partly and continue with it rather than try to pick up a new one from the beginning.

For work I develop with C++ and C# using Visual Studio on Windows.  At home I use gedit (normal notepad type program) for my C++ work and compile at command line and use Monodevelop for my C# work.  I do alot of Java at home as well and use Netbeans for that.

Paul

---

### Post by trent.josephsen on 2010-07-17
Python is a good place to start, but there are many more languages available.  Perl is still fairly popular as an early language.  I would recommend avoiding C and family (including C#, C++, Java) until you are a more experienced programmer; to make the best of these languages, you should have prior programming experience.  C in particular requires great caution and close attention to detail.  Java's Achilles heel is verbosity, making certain things that should be easy feel like kludges.  I often recommend Perl as a stepping stone between Python and C or C++, but it's ultimately your choice.

When it comes to environment, you will encounter 2 camps that seldom if ever overlap.
1) Do all the coding in some IDE; punch a button to compile the project and run it.
2) Code in an editor; invoke the compiler directly, or use **make**, to build the project.

An IDE, like Eclipse, NetBeans, or Visual Studio, typically supports only a handful of languages and has limited capability for advanced editing; an editor like Vim, Emacs, jEdit or Gedit usually supports dozens of languages and has features for efficiently editing any kind of file.  The reverse side of the coin is that editors don't usually offer features that require intimate knowledge of a specific language, like visual debugging and viewing relationships between modules.  Many large projects use IDEs to be able to manage complex relationships in large codebases.  For most small projects, an IDE is overkill.

I am a member of camp 2.  I encourage you to use an editor and compile or interpret your code by hand, until it gets challenging to do so (probably never with Python, more than 2-3 files with C or Java) and then move to a build tool like make.  Using an IDE as a newbie teaches you nothing about how code is run; invoking the compiler or interpreter by hand is no more difficult and enforces some important distinctions.  YMMV.

---

### Post by crush304 on 2010-07-17
take a look at [http://projecteuler.net/](http://projecteuler.net/) for small problems to solve

---

### Post by bocaccio on 2010-07-18
I love all the responses;however I may have been misunderstood. I do not want to solely program **for linux. **I just mean that well....basicly everything runs like an orgasm on here compared to windows so why not write code on it instead of 7/xp.
When I would write code on visual studio windows 7 would lag and lock up alot. I would have to wait for windows to catch up with me.

I am really done with programming; hated it actually but i am interested in learning more of it. I like it but am no good at it is what I am trying to say. I am thinking after my Bachelors in Forensics I'll continue and get another degree in or pertaining to programming; so i wanna try and pick up a different language now in my "spare" time.

---

### Post by bocaccio on 2010-07-18
> **webtechquery said:**
> Geany is a good tool for programming.. in some cases, you can say its more lil advanced than Notepad ++

Check out the following link for some more details about Geany:
[http://www.webtechquery.com/index.php/2010/06/geany-ubuntu-ide/](http://www.webtechquery.com/index.php/2010/06/geany-ubuntu-ide/)

Thanks

Can someone tell me why it says supports windows, linux, and ubuntu???? I thought ub was linux or at least a distro off of linux.

**Geany Features**

 Some of the good features of Geany are listed below:
 
[LIST]
[*]Autocomplete for PHP etc.
[*]Auto closing tags for HTML and XML
[*]Syntax Highlighting
[*]Supported filetypes like C, Java, PHP, HTML etc.
[*]Supports Windows, Linux, Ubuntu etc.
[/LIST]

---

### Post by bocaccio on 2010-07-18
> **crush304 said:**
> take a look at [http://projecteuler.net/](http://projecteuler.net/) for small problems to solve
I made an acct!!! I can't wait to get started using netbeans,monodevelop, and geany; gotta figure out which one i wanna use and I think I am gonna go with either python or C#.

Thanks!!!!

---

### Post by KdotJ on 2010-07-18
Java is great for portability and cross-platform development. Netbeans is a great IDE (which has GUI building which you may be used to in Visual Studio). Eclipse is also a great IDE.

Both of these are fully available for both Linux and Windows. 
As for Java, it is my personal language of choice (not trying to be bias or tell you to learn it, just as a suggestion). I am required to learn it for my uni course and in here, it's well paid too. Many people however will tell you that Java is bad, or they hate Java or that you shouldn't touch Java but whatever, your choice.

In my opinion, you can't do VB.net for a class and decide you've done it and want to move onto something else. It is best to learn the fundamentals of programming, algorithms and solving problems rather than focusing on learning one language in depth at first. 
On the other side of the coin... switching languages, chopping and changing early on in learning programming basics is not very helpful and can confuse you

---

### Post by bocaccio on 2010-07-18
> **KdotJ said:**
> Java is great for portability and cross-platform development. Netbeans is a great IDE (which has GUI building which you may be used to in Visual Studio). Eclipse is also a great IDE.

Both of these are fully available for both Linux and Windows. 
As for Java, it is my personal language of choice (not trying to be bias or tell you to learn it, just as a suggestion). I am required to learn it for my uni course and in here, it's well paid too. Many people however will tell you that Java is bad, or they hate Java or that you shouldn't touch Java but whatever, your choice.

In my opinion, you can't do VB.net for a class and decide you've done it and want to move onto something else. It is best to learn the fundamentals of programming, algorithms and solving problems rather than focusing on learning one language in depth at first. 
On the other side of the coin... switching languages, chopping and changing early on in learning programming basics is not very helpful and can confuse you


That makes sense. So your saying I should just continue with vb.net? Or what? I thought C# or java would be more widely used than vb.net is why i want to learn another instead. I didn't choose vb.net it was just in a class.

---

### Post by KdotJ on 2010-07-18
> **bocaccio said:**
> That makes sense. So your saying I should just continue with vb.net? Or what? I thought C# or java would be more widely used than vb.net is why i want to learn another instead. I didn't choose vb.net it was just in a class.

It is indeed difficult to pick a language really. From experience, you will pick one and then get bored and see other people on here talking about other languages and think maybe you should do that etc. That's all well and good, and you get a nice variety of languages. But, for me atleast, I ended up knowing how to the same thing, the same ability in a few languages, where as I could of spend the time on one language and learnt a great deal more. 
As for what language, at the end of the day, generally speaking, for desktop programming you can get the same result in any language. It then comes down to preference. Only when you need specific things that it becomes more of an issue (for example, when speed is crucial for you program, then opting for C over Python would be a good choice) but for the most, you're safe in most languages to do whatever.

Like you, back in college we had to use VB.net and don't get me wrong I loved it, it was my first experience with programming. There's nothing wrong with VB.net and it helped me a lot when I was starting out. But after a while, like you, I wanted to move onto something else. 

My university chose to use Java as the language we had to use for a few reasons,
 
1) It works on any platform and is easily portable. By this I mean that it can be run on a system, regardless of OS without much bother.

2) Java is used widely in the programming world and seen as one of the top contenders of mainstream languages.

3) It has it's own built in GUI toolkit (Swing, and AWT) that is part of Java. This means it can be run on any system that has Java Runtime install, without having to have the other toolkits and libraries installed.

OK, so now I sound like a sales person for Java, which I don't mean to be. I am purely just giving you some info on it. Most people here will suggest Python, which is a great language. It is a fairly simple high-level language that is multi-paradigm (Unlike Java (and VB.net for that matter) which are Object-Oriented). I like Python and use it a bit but I don't know it well enough to argue it for you.

Atop of this, you could learn the syntax and features of any language inside and out, but still not really know how to program but I'm sure this is what your classes is covering now :-)

---

### Post by v1ad on 2010-07-29
i use gedit and just select the language that i am using.

---

### Post by bocaccio on 2010-07-29
> **v1ad said:**
> i use gedit and just select the language that i am using.


Seems to be the best solution. gedit is lightweight and is probably available on all distros.

thanks and i love your signature and hate iPhones.

---

