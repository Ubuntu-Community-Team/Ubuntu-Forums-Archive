---
title: "How to run simple VisualBasic application on Linux?"
date: 2009-01-12
forum: Programming Talk
---

### Post by abcuser on 2009-01-12
Hi,
I am using Ubuntu 8.10, and I know little bit of VisualBasic programming language, I was learning it when I was at school 10 years ago.

Now I have few simple VisualBasic programs I have developed by myself and I use them on Windows XP. I would like them running on Ubuntu.

Is there anyway I could compile the VisualBasic code on Linux? Is there any other way then using Wine. I have tried Wine-way but some programs doesn't work and some are working too slow to use for normal use on older PC.
Regards

---

### Post by Kilon on 2009-01-12
> **abcuser said:**
> Hi,
I am using Ubuntu 8.10, and I know little bit of VisualBasic programming language, I was learning it when I was at school 10 years ago.

Now I have few simple VisualBasic programs I have developed by myself and I use them on Windows XP. I would like them running on Ubuntu.

Is there anyway I could compile the VisualBasic code on Linux? Is there any other way then using Wine. I have tried Wine-way but some programs doesn't work and some are working too slow to use for normal use on older PC.
Regards

Well a VB .NET should run with the MONO. But if you want to move your code from windows I assume it is not .NET then sorry I have not got any solution to your problem. If it is plain old VISUAL BASIC you may find it difficult if not impossible to port in Linux. 

Wine is not a guarantee solution because even if you manage to run it with wine , you would be running it in a WINDOWS environment and produce windows code, which again will require wine to work. Not a preferable solution and very much error prone. 

I have find this article that will interest you 

[http://www.linux.com/articles/34497](http://www.linux.com/articles/34497)

but my advice is to turn to python. Python is a computer language very similar to VB, it has extremely easy syntax and is widely supported on all platforms and especially Linux. You will find many people coding python in linux and python has all the libraries you will need. Also porting your code from VB to python would require to rewrite some code but not too much as the syntax of the two languages is very similar.

---

### Post by nvteighen on 2009-01-12
Actually, I think it's a bit nonsense. VB is a language meant to be written & run from Windows and it's entirely designed to be that way. Yes, there is the Mono project and there's also Wine, but even if they worked in a really reliable way, you'll be still trying to code for Windows in GNU/Linux. Though possible, I just don't get the idea on why someone would like to do this.

I second Kilon's advice on Python. It's a cross-platform language, so you won't restrict yourself to one single OS... and it's possibly the nearest language to VB in easiness you may get in a GNU/Linux environment.

---

### Post by mpsii on 2009-01-12
Since your actual question involved "How do I run this?" and NOT "What is your opinion about running this?"...

Use wine to install the visual basic runtime. Then use wine to install/run your application.

Though the advice on Python is good for the future, wine will help you run windows-based apps on Linux. Your mileage may vary however. As far as I know, though, unless you are using DirectX in your code, you should have no problems. You may face some minor visual bugs; but, seeing as you are the developer of the app, you may be able to code around or modify the code to alleviate the issue.

---

### Post by directhex on 2009-01-12
> **nvteighen said:**
> Actually, I think it's a bit nonsense. VB is a language meant to be written & run from Windows and it's entirely designed to be that way. Yes, there is the Mono project and there's also Wine, but even if they worked in a really reliable way, you'll be still trying to code for Windows in GNU/Linux. Though possible, I just don't get the idea on why someone would like to do this.

VB is a deprecated windows-centric language

VB.NET, however, is no less cross-platform than C# - and if you want to claim C# isn't for Linux apps, then don't look at popular picks like GNOME Do, whatever you do

---

### Post by nvteighen on 2009-01-12
> **directhex said:**
> VB is a deprecated windows-centric language

VB.NET, however, is no less cross-platform than C# - and if you want to claim C# isn't for Linux apps, then don't look at popular picks like GNOME Do, whatever you do
Hmm... You're right; it's just that VB.NET doesn't seem to have any acceptance yet through Mono (as opposed to the increasing presence of C#).

---

### Post by mssever on 2009-01-12
> **Kilon said:**
> I have find this article that will interest you 

[http://www.linux.com/articles/34497](http://www.linux.com/articles/34497)
I don't consider RealBasic to be a viable option. Judging by the small number of RealBasic apps I've used (I don't know the language itself), there's no attempt to match native look and feel on any platform and the L&F used is almost as hideous as Tk on Linux. At least it doesn't play favorites; the L&F is as ugly on Windows as it is on Linux. Furthermore, the Linux version has serious font rendering issues--serious to the point that the app becomes nearly unusable.

---

### Post by directhex on 2009-01-12
> **nvteighen said:**
> Hmm... You're right; it's just that VB.NET doesn't seem to have any acceptance yet through Mono (as opposed to the increasing presence of C#).

Well, sure. That's 'cos it's a poopy language ;)

---

### Post by abcuser on 2009-01-14
> **nvteighen said:**
> Actually, I think it's a bit nonsense... Though possible, I just don't get the idea on why someone would like to do this.Very simple reason. I know how to program in VisualBasic and I don't know other programming languages. Why should I learn new language if I don't need programming too much. I only have a need time to time to program some simple programs.

---

### Post by abcuser on 2009-01-14
Hi,
I have found out very interesting open source project. It's name is Jabaco, read more on web page: [http://www.jabaco.org/](http://www.jabaco.org/)

The idea is simple: write program in VisualBasic like sintax (it is almost 100% the same code as in VisualBasic). Jabaco then generates Java jar file that can be executed on any platform using Sun Java Run-time environment. Java is installed on any platform I have seen so far, so this is good idea - no software installing required.

See this excellent webcast to present how to convert VisualBasic code to Jabaco: [http://www.jabaco.org/index.php?page=webcast](http://www.jabaco.org/index.php?page=webcast)

By the way. I have written one simple calculator in VisualBasic, now opened the project in Jabaco and convert it into jar file. Then I have executed this program using Java on:
1. Windows XP Intel x86,
2. Ubuntu 8.10 on Intel x86 and
3. Suse 10.1 on IBM zServer **mainframe**! I run mainframe program accessing it by ssh on Ubuntu.

On all systems program works excellent without any problem at all. There is just some little fonts size difference, but not too much a problem. See attachments.

Regards

---

### Post by Kilon on 2009-01-14
> **nvteighen said:**
> Hmm... You're right; it's just that VB.NET doesn't seem to have any acceptance yet through Mono (as opposed to the increasing presence of C#).

Well that is because VB .NET is no VISUAL BASIC. It is C# that tries to be Visual Basic and it fails miserably . Visual Basic used to be the most popular language in the world. The perfect candidate for the majority of software out there. Yes you guessed small highly useful apps made by a single man.  

Ex Visual Basic developers saw that because they were not as stupid as some of C++ colleagues thought they were and moved to C# (which is by the way a kick *** language , do not mind the Microsoft haters) as quickly as they could. Fortunately  C# is alot easier than both C++ and Java. 

The new Visual Basic is python and other languages that do not promote mandatory use of Object Orientation. Maybe other languages as well that elude me, you mentioned them here. 


Python may not be as popular as Visual Basic was , not even by a long margin, but it is the VISUAL BASIC as it should have been in the first place and alot more.

---

### Post by Kilon on 2009-01-14
> **abcuser said:**
> Hi,
I have found out very interesting open source project. It's name is Jabaco, read more on web page: [http://www.jabaco.org/](http://www.jabaco.org/)



WOW , that is very interesting tool. Thank you alot, I must check it out and I will check it out now!!!

---

### Post by thomasaaron on 2009-01-14
> **abcuser said:**
> Very simple reason. I know how to program in VisualBasic and I don't know other programming languages. Why should I learn new language if I don't need programming too much. I only have a need time to time to program some simple programs.

Because you need an adventure? ](*,)

---

### Post by mpsii on 2009-01-14
As no one has pointed it out... the reason VB.NET has not infiltrated Mono like C# is because VB.NET is not a public specification as C# components are.

---

### Post by directhex on 2009-01-14
> **mpsii said:**
> As no one has pointed it out... the reason VB.NET has not infiltrated Mono like C# is because VB.NET is not a public specification as C# components are.

Also a pretty important point, yes.

I stand by my "VB.NET is poop" comment though as a valid reason ;)

---

### Post by nvteighen on 2009-01-15
> **abcuser said:**
> Very simple reason. I know how to program in VisualBasic and I don't know other programming languages. Why should I learn new language if I don't need programming too much. I only have a need time to time to program some simple programs.

OK, but the problem is that you will spend a lot of time trying to make a Windows program work in GNU/Linux if it even happens to work. I understand why you don't want to learn another language, but I'd really consider it so you are free of these issues. (Also, it would expand you horizons, who knows?).

---

### Post by Kilon on 2009-01-15
> **abcuser said:**
> Very simple reason. I know how to program in VisualBasic and I don't know other programming languages. Why should I learn new language if I don't need programming too much. I only have a need time to time to program some simple programs.

Well if you want to spend the absolute minimum of time on programming. Then it is absolutely understandable why you do ** NOT ** want to learn a new programming language. 

Learning Python under this circumstance would be** WRONG!!!** Python syntax is very similar to VB syntax , so it should take a few days to learn the basic python syntax, but it will take several weeks or months to learn the needed libraries. 

So I think you prove once more what I am always advising people. The perfect person for finding a solution to your problem, is yourself. 

I think that JABACO is the **BEST** solution so far. JABACO can port VISUAL BASIC code to both MACOSX and LINUX with no change to the code. **_It is almost impossible to beat that_**. Carry on , on this route ! Keep python in the back of your head , when you need to do more advanced stuff and visual basic does not fulfill your needs.

Once again thank you for bring this to my attention, it is highly useful for ex Ex-Windows Visual Basic developers .

Keep sharing your experience with JABACO I am very interested.

---

### Post by eye208 on 2009-01-15
> **Kilon said:**
> The new Visual Basic is python and other languages that do not promote mandatory use of Object Orientation.
There is no language where OOP is mandatory. Even in Java you can put all your procedural code into a single class and forget about OOP.

Implementing OOP with a procedural language is tricky, but avoiding OOP is trivial.

---

### Post by Kilon on 2009-01-15
> **eye208 said:**
> There is no language where OOP is mandatory. Even in Java you can put all your procedural code into a single class and forget about OOP.

Implementing OOP with a procedural language is tricky, but avoiding OOP is trivial.


You must be joking , right ?

An object orientated library requires knowledge of Object Orientation and use of Object Orientation. Especially in languages like Java and C#. Not even mentioning the extra typing that an Object Orientation library requires. Trying to use OO libraries, without knowing OO will create confusion and frustration in many case for a beginner.  

My experience tells me that OO is the most over estimated feature in a programming language. I used to be a huge fan , no I am less and less, not because of python as much as the need I had for OO all these years. I can see the usefullness of OO when the project gets to a considerable size but before that it is more of an obstacle than a helping hand. 

I am using Java and python , your claim about trying to do procedura programming in language highly dependent on OO  makes no sense and is the worst advice you can give to a beginner. 

Comparing languages like VB to Java is simply a joke in matters of ease of use. I love Java but I would not recommend it to a beginner and of course to an ex VB developer.

---

### Post by eye208 on 2009-01-15
> **Kilon said:**
> An object orientated library requires knowledge of Object Orientation and use of Object Orientation. Especially in languages like Java and C#. Not even mentioning the extra typing that an Object Orientation library requires. Trying to use OO libraries, without knowing OO will create confusion and frustration in many case for a beginner.
As soon as your program uses a library, it uses OOP features, even if the language is C. It doesn't make much difference whether you type
```
write(file, data);
```
or
```
file.write(data);
```
By the way, Visual Basic has been using OOP features at least since version 5, probably earlier. The only difference was that COM did not support inheritance.

> I am using Java and python , your claim about trying to do procedura programming in language highly dependent on OO  makes no sense and is the worst advice you can give to a beginner.
This is nonsense. First, I didn't advise anyone to avoid OOP. Second, it is perfectly possible to do procedural programming in Java. All you have to do is declare all your functions and variables **static** so that they can be called/accessed without an object instance.

> Comparing languages like VB to Java is simply a joke in matters of ease of use. I love Java but I would not recommend it to a beginner and of course to an ex VB developer.
Maybe that's because you are a beginner yourself. Nothing wrong with that, but in order to give advice, you should at least know what you are talking about.

---

### Post by Kilon on 2009-01-15
Well If you cannot distinguish a beginner from a experienced programmer after all the posts we have exchanged in the past , then I have nothing more to say.  But really you will find it hard to fool me. Nice try though.

---

### Post by eye208 on 2009-01-15
> **Kilon said:**
> Well If you cannot distinguish a beginner from a experienced programmer after all the posts we have exchanged in the past , then I have nothing more to say.
You spend most of your time in this forum discouraging people:

Don't learn C/C++! It's difficult!
Don't learn Java! It's difficult!
Don't learn VB.NET! It's difficult!
Don't learn *anything* except Python! We all must learn Python!

You are such a zealot. The OP said he has prior experience with VB6. Learning VB.NET will be easy for him. He will probably appreciate the additional features available in .NET/Mono because VB6's lack of inheritance and polymorphism was a major pain in many cases.

---

### Post by Kilon on 2009-01-15
> **eye208 said:**
> You spend most of your time in this forum discouraging people:

Don't learn C/C++! It's difficult!
Don't learn Java! It's difficult!
Don't learn VB.NET! It's difficult!
Don't learn *anything* except Python! We all must learn Python!

You are such a zealot. The OP said he has prior experience with VB6. Learning VB.NET will be easy for him. He will probably appreciate the additional features available in .NET/Mono because VB6's lack of inheritance and polymorphism was a major pain in many cases.

You know there is a post of mine above , recommending to avoid learning python. So your claims is pretty much mute.

I never have told anyone what to do. I certainly have not told anyone not to learn C/C++. 

Also I have not told that C++ is difficult , I have said its libraries in windows (MFC) which I have used for some time are awful.But some of tis features like memory management etc is pretty difficult to use in a regular base.   Do not know what happens with Linux have not tried it and cannot comment on the available libraries.    

I actually said that C++ is not that difficult as people make to be. 

For Java I do not know where you imagine the things you think you hear . But if you missed it I am a jython developer and that makes me highly dependent on both python syntax and java libraries. So I would be an idiot to accuse Java . As matter of fact I have found several java libraries that are amazing. 

Oh you also missed all those praises for .NET that I have spread in the forum , even among Microsoft haters.

Actually you got the VB .NET right , I hate it , it is not VB and should not be called as such. I would never recommend it even if you made me smell your feet. 

Now about python. Well as I see it , this forum attracts alot of new developers , who do not know much about programming and would be most comfortable with a language that is easy to use, requires little code for doing even advanced stuff , highly supported and very capable.    Well in my book this narrows it down to Python and python hybrids (Ironpython and Jython) . C# comes pretty close as a second option. Then is Java . C++ is something that I will discourage to use. 

Maybe now you can copy and paste my message to your hard drive  and read it each time you try to accuse me of anything .

---

