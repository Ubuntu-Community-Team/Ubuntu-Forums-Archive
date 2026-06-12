---
title: "Simplest Java editor (for compiling/running Java programs)"
date: 2006-11-09
forum: Programming Talk
---

### Post by Super King on 2006-11-09
As a Computer Science major at college naturally I have to write a few programs in Java. In Windows I use [Textpad]("http://www.textpad.com/"), which while lite can manage multiple files at once and compile/run Java out of the box (assuming the Java SDK is installed) with syntax highlighting. I'm looking for something similarly simplistic in Linux: I've taken a quick peek at Eclipse, which looks overly complex. Any suggestions for a simple Java editor along the lines of Textpad?

---

### Post by raovq on 2006-11-09
i quite like kate. gives you a nice overview of all your classes and allows quick changing between them.

it has a terminal down the bottom so compiling and running is simple enough.

---

### Post by hod139 on 2006-11-10
The native text editor for ubuntu is gedit (kate requires the KDE libs).  Gedit has tabs and syntax highlighting, but you will need to open a separate terminal window to compile.

---

### Post by skymt on 2006-11-10
[jEdit](http://jedit.org/) has great Java support, with tons of Java-related plugins available through the built-in plugin manager. Adding the [JCompiler](http://plugins.jedit.org/plugins/?JCompiler) plugin will complete the package.

---

### Post by igknighted on 2006-11-11
SciTE is really nice for gnome... if you are in KDE then Kate >> all

---

### Post by meng on 2006-11-11
leafpad is lighter than gedit.

---

### Post by Peepsalot on 2006-11-11
I haven't tried programming java with it, but I have use bluefish in the past for some simple web development and found it to be pretty nice.

---

### Post by steve.horsley on 2006-11-11
You should definitely look at BlueJ - [http://www.bluej.org](http://www.bluej.org). It's an editor with class diagram and debugger built in. It was written for teaching java at universities. I heartily recommend it.

---

### Post by Super King on 2006-11-13
Thanks for all the replies. I tried out Eclipse, jEdit, and Kate this weekend, and after playing around I decided I do like Eclipse the most in fact :)

---

### Post by jinx099 on 2006-11-13
Yep, eclipse is awesome!

Anyone know if eclipse can be used with gcc/g++ ?

---

### Post by skymt on 2006-11-13
> **jinx099 said:**
> Yep, eclipse is awesome!

Anyone know if eclipse can be used with gcc/g++ ?

Yes it can, if you install the CDT (C Development Tools) add-on.

---

### Post by nikolaos on 2006-11-13
I go with Jedit (it is just perfect), but i also suggest Jcreator. In fact Jcreator matches the editor you are looking for (from the Title) more accurately i think, it compiles and runs the programs just fine.

---

### Post by Kieranties on 2006-11-14
> **steve.horsley said:**
> You should definitely look at BlueJ - [http://www.bluej.org](http://www.bluej.org). It's an editor with class diagram and debugger built in. It was written for teaching java at universities. I heartily recommend it.

I have to heartily disagree.  If you are a reasonably proficient java programmer bluejay will only hold you back.  Yes it is a good teaching aid, but for anything more then a few basic applications it is very poor.  The framework is great for teaching O-O programming concepts by deatailing the class diagrams, but lacks in just about every other department, the built in debugger is very poor and often displays errors in the wring places in code.

But hey, that is my experience with it.  I am currently looking at [scribes](http://www.ubuntuforums.org/showthread.php?t=278610&highlight=scribes) as my core editor.

---

### Post by Jeff Johnston on 2006-11-14
After using Eclipse you will never want to go back to a simple editor. Netbeans is a really good IDE as well.

I used to say that using an IDE such as Eclipse was not as good for new developers because you had to learn the tool as much as the language. That is no longer the case. Eclipse is now very easy to use and totally non-distracting. Plus because of the auto-completion and other features it can serve as a nice teaching aid. It is hard to believe all the features packed into the editor and each release there are more and more. 

Be sure to read the Help Welcome as that will guide you to a lot of help topics to get started. Also in the editor just remember to keep hitting ctrl + space bar as that is the key to the autocomplete and many other features. You'll get used to it quite fast. Also ctrl + 1 is another great shortcut that offers a lot of refactoring type help.

If you need more web support consider getting MyEclipseIDE. It is a $30 a year subscription that gives you a lot of great plugins for doing web development. Totally worth the money if you need the plugins it provides. If you are just using Tomcat then maybe Netbeans is the way to go as they include Tomcat support automatically.

---

### Post by rko618 on 2006-11-20
> **Jeff Johnston said:**
> After using Eclipse you will never want to go back to a simple editor. Netbeans is a really good IDE as well.

I used to say that using an IDE such as Eclipse was not as good for new developers because you had to learn the tool as much as the language. That is no longer the case. Eclipse is now very easy to use and totally non-distracting. Plus because of the auto-completion and other features it can serve as a nice teaching aid. It is hard to believe all the features packed into the editor and each release there are more and more. 


I disagree.  Eclipse is still a very complex tool that has to be learned.  As such I would not introduce it to someone new to Java programming.  My college (UCI) starts CS majors off programming with Textpad and then lets them migrate to Eclipse on their own.  This is all good but sometimes they become so accustomed to Textpad that they are still using it exclusively in their 4th year when projects are large and are better managed by a full IDE.

---

### Post by Circus-Killer on 2006-11-20
i would get also recommend giving jgrasp a try. just download from [www.jgrasp.org]("http://www.jgrasp.org/"). unzip the file. and run the linux executable.

works well, been using it in windows and linux since i started learning java.

---

### Post by menachemh on 2008-12-13
For a textpad-like program on ubuntu use **Geany** ([http://www.geany.org/](http://www.geany.org/)) It is exactly like textpad which I love too but even better and has a built in terminal. It looks very much like Textpad and even simpler. Very simple and light IDE and even surpasses textpad in many ways. You could actually run textpad on ubuntu with wine but I would yet again recommend installing Geany first as you won't be disappointed. Anyways I hope my reply helps you (I know it's 2 years late) but maybe someone else will come across this thread and find this helpful.

---

### Post by davidsweetboy on 2012-07-24
I need programming code for creating a Simplest Java editor (for compiling/running Java programs)

---

### Post by mickeelm on 2012-07-24
Lot of opinions here so I might as well share mine :)

As has been said, for example gedit has syntax highlighting and jEdit might be even sweeter and more alike your Windows equivalent (I've only used it once or twice, simply because it was part of an assignment).

Today, I am a java professional and wouldn't dream of using anything else than an IDE (nor would my employer). Personally I use Eclipse (or actually SpringSource STS but that is built on Eclipse). Among my colleagues I find usage of IntelliJ, NetBeans and Eclipse, but no one uses a text editor. Simply because we would never deliver any code in time if we did and we would be inventing the wheel everyday, killing all productivity.

The only reason for using a simple text editor (syntax highlighting or not) is for *learning* in my opinion. I started off using text editors and for that I am very greatful today. Everyone should start off with text editors, just to have the initial struggle more or less - because that is how you truly learn the basics!

Once that part is settled, there is no need not to take advantage of the powers that an IDE has to offer. An IDE will give you hints, warn you immediately if your code doesn't compile and so on. As long as you understand WHY you are given warnings like "The local variable foo is never used" - why not get it directly instead of after compiling and save some time?


My recommendation is an IDE (I like Eclipse) since I take it that you have written some java before. Even if you write simple code it will save so much time for you in the end.

At the same time, you asked for the simplest java editor. Well, then gedit might be the answer. If gedit is too basic (and you have coded before so I'd say it is), I see no reason not to go with for example Eclipse, it is not complicated. I can't really answer for jEdit, but as far as I know it is more of an advanced editor than an IDE. Try for yourself :)

Happy coding :)

---

### Post by theDaveTheRave on 2013-07-10
Hi all,

I've decided to add in my thoughts.

I use different IDE for different things.

eclipse: for most 'hard core' java dev stuff.

leafpad / gedit: for quick / easy editing of web pages

geany : if I'm doing more serious web development, I like the idea of 'projects' that you get in geany, so I can work on a specific part of my page only by setting a project with only the required files (ie help pages, menus, php stuff can be in separate projects - they are a bit like workspaces in eclipse)
The only issue I have with geany is that I don't get the pop up details with all of the libraries that I use, and unlike eclipse it doesn't seem so clever at finding variables with the same name across pages (ie function calls on external JS file aren' found automatically).

David

---

### Post by Leuchten on 2013-07-10
For a simple editor, I'd say vi, kedit, or kate. 

For complex, I'm really surprised very few people in this thread have mentioned intellij. There is an opensource version of it, it's leaps and bounds better and more responsive than eclipse, and all in all it's an awesome IDE. Eclipse has been a terrible experience for me every time I've used it.

---

