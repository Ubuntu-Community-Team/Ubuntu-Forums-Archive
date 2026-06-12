---
title: "What (and how) to install for programming ourposes?"
date: 2008-08-10
forum: New to Ubuntu
---

### Post by Beezgetz on 2008-08-10
Hello all,

Quite new to linux via ubuntu. I've been working on app using C# in Visual Studio, on XP. There is a need to 'translate' my app for Mac users, so here I am.

If I wish to 'rewrite' my program to work on Mac/linux, what programs should I use if I am used to C#?

As I am learning over last past days that Mono is the thing to go for. Also Mono Develop and gtk#.

What, where and how to get/install those files, so I can see them in Applications/Programming/apps

Kind regards, Beezgetz

---

### Post by WRDN on 2008-08-10
For C# programming, I use [MonoDevelop]("http://www.monodevelop.com/Main_Page") which I find very reliable. I never had to manually install any other packages, and my C# programs compiled and worked immediately.

---

### Post by HotCupOfJava on 2008-08-10
Try searching the repositories for some C# development tools. Go to "System"->"Administration"->"Synaptic Package Manager". You will be prompted to enter your password. The do a search for "C#", "C# development", or something like that. It will show a list of packages you can install. Pick something that looks like what you need, and right-click the box next to it. Choose "Mark for installation". Then you can click the "Apply Changes" button and it will download and install the package for you. I did a search for "C# development" and came across something called monodevelop that may do what you want. I will say that C# is kinda Microsoft's baby, so I don't know if the stuff  available for Linux will be as good as what you can find for say, Java, Python, C++, etc.

Hope that helps.

---

### Post by cmay on 2008-08-10
hi.
there is also a programming talk section in the ubuntu forums.

---

### Post by HotCupOfJava on 2008-08-10
> **cmay said:**
> hi.
there is also a programming talk section in the ubuntu forums.

Yeah, this thread will probably get moved there if it gets long enough.....

---

### Post by Beezgetz on 2008-08-10
Wow, lightning fast answers! Thanks

Sorry admin, I am a beginner, so I thought here was a good thread section  to start. 10x

Right, so by now I have under Applications/Programming/this: ilContrast, MonoDevelop, Monodoc and Monodoc(http). 
I can see the MonoDevelop is very simmilar to VS c#, so I tried out something simple, like adding the button on the form, but I have problem with adding stuff into the form. If I put button on form, it gives me some report and than the button takes all the space on the form. I could not resize the button to smaller size...

"I don't know if the stuff available for Linux will be as good as what you can find for say, Java, Python, C++, etc."
So, approaching Mac users is better with those programming languages? Are they similar with c#? ...and thanks for excellent walk trough

Thanks again guys for sharing wisdom with us and me, and check programming section, since i'll be posting there a couple of questions

Kind regards, Beezgetz

edit:
eh..khm, where is this programming forum, I can't find it?...

---

### Post by HotCupOfJava on 2008-08-10
C# is VERY similar to Java - and Java is about as platform-independent as you can get. The NetBeans IDE is great for doing GUI applications(you shouldn't have any trouble resizing a button!). It is in the repositories as well (find it with Synaptic also).

---

### Post by Beezgetz on 2008-08-11
Hey Hot Cup Of Java, hello

ok, I'm installing NetBeans right now. Done.
Now the problems. I started NetBeans, and on the main window there are several links to useful stuff. The problem is, that any link clicked, I get this message: annot execute /usr/bin/firefox. Check external browser configuration. I looked for firefox in /usr/bin/firefox, and I have a shortcut, I guess, of firefox in there. It is a Type: Link to shell script, and Link target is firefox 3.

but more importaint question. Writing in Java using NetBeans, produces applications that can run on Mac and Linux users?

Thank you

Kind Regards, Beezgetz

Edit:
 Can I also write iPhone applications? if not, what programs support that?

---

### Post by tarps87 on 2008-08-11
> **Beezgetz said:**
> 
but more importaint question. Writing in Java using NetBeans, produces applications that can run on Mac and Linux users?

so write iPhone applications? if not, what programs support that?

Java uses a thing called java runtime environment which can be installed on most if not all platforms, your programs will run inside this environment and act like any other aplication.
Netbeans is a development environment, Java is the language so as long as you compile it to a .jar file it should run.

I believe there is a java runtime for mobile phones, a good place to look is the sun mirosystems website [http://java.sun.com/](http://java.sun.com/)

---

