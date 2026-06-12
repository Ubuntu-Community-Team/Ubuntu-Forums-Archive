---
title: "Which programming language could help me ?"
date: 2009-01-20
forum: Programming Talk
---

### Post by feras.ws on 2009-01-20
Dear Sirs,

I used to use Ms Windows for about more than 13 years , and finally I decided to move into Linux especially Ubuntu,
I am a desktop application programmer and I would like to program for Linux but I don't know which programming language could help me , so could you please help me in these questions ?
1- does Mono help me to program applications for Linux using .NET?
2- which is the most useful programming language which allows me to program applications for Linux ?
3- when I program for Linux , should I program an application for each versions (Open Suse,Mandriva,Ubuntu) or just one application ?

Waiting your kind reply.


Feras Allaou

---

### Post by MikeSz on 2009-01-20
you may be better off in the Programming talk section rather than absolute beginners as there are plenty of discussions of this nature that will be of help to you.  I'm only a notice programmer but I am told that Python is the one to go for where Ubuntu is concerned.

edit - if you go to the main Ubuntu Forum Community, you'll see all the different categories and of of them is Development and Programming

---

### Post by feras.ws on 2009-01-20
> **MikeSz said:**
> you may be better off in the Programming talk section rather than absolute beginners as there are plenty of discussions of this nature that will be of help to you.  I'm only a notice programmer but I am told that Python is the one to go for where Ubuntu is concerned.

edit - if you go to the main Ubuntu Forum Community, you'll see all the different categories and of of them is Development and Programming

Thank you very much for your quick reply.I'm sorry for posting it in the inappropriate section , Waiting moderators to move it into the appropriate section .

Feras

---

### Post by MikeSz on 2009-01-20
No problem - I'm glad you like Ubuntu.  The community here is second to none and I'm sure you'll get plenty of help in the Development and Programming section - in my experience those boys love a good programming debate!

---

### Post by feras.ws on 2009-01-20
> **MikeSz said:**
> No problem - I'm glad you like Ubuntu.  The community here is second to none and I'm sure you'll get plenty of help in the Development and Programming section - in my experience those boys love a good programming debate!

thank you very much ;)

---

### Post by directhex on 2009-01-20
> **feras.ws said:**
> 1- does Mono help me to program applications for Linux using .NET?

Yes. Install mono-devel on Jaunty, or mono-2.0-devel on Intrepid. Install mono-vbnc (Jaunty-only) if you want a VB.NET compiler (vbnc command), otherwise use gmcs for your C# compiler. Install "monodevelop" for a SharpDevelop-based IDE

> 2- which is the most useful programming language which allows me to program applications for Linux ?

Whichever language you want to use. Whichever you feel most comfortable with, which allows you to do the most in the least amount of time & effort. A default Ubuntu install includes apps written in C, Perl, Python, C#, and more.

> 3- when I program for Linux , should I program an application for each versions (Open Suse,Mandriva,Ubuntu) or just one application ?

There should never be a need to do this, unless your app interacts with system-specific things like package management

---

### Post by mtausig on 2009-01-20
> **feras.ws said:**
> 
1- does Mono help me to program applications for Linux using .NET?
2- which is the most useful programming language which allows me to program applications for Linux ?
3- when I program for Linux , should I program an application for each versions (Open Suse,Mandriva,Ubuntu) or just one application ?


1) Yes. Mono allows you to run (a lot of) .NET apps in linux and to create application under linux which (most of the time) also run in windows
2) Depends on what you want to do. 10 people will probably give you 11 different answers to this question. But if you already have some .NET experience, mono is probably a good starting point.
3) No, one application is fine. You, or someone else, might at some point create differen packages out of your software, but that should not influence the source code.

---

### Post by ibutho on 2009-01-20
I'm not much of a programmer but I can help with some of your questions.[LIST=1]
[*]Yes, mono can help you develop .net apps for Linux
[*]The most popular programming languages on Linux platforms are C, C++, Python and Perl so you can use any of those to create Linux applications. Pick a language depending on the app and your own experience.
[*]You can create an app on one particular distro, release the source and other developers or distro maintainers can then package your app for their own distro.
[/LIST]

---

### Post by feras.ws on 2009-01-20
well thank you all for your replies.
I already installed mono and I programmed a simple program but how can I find it's debug file ?
I found one file caled program_name.exe ! but exe don't work on Ubuntu !!

Regards
Feras

---

### Post by directhex on 2009-01-20
> **feras.ws said:**
> well thank you all for your replies.
I already installed mono and I programmed a simple program but how can I find it's debug file ?
I found one file caled program_name.exe ! but exe don't work on Ubuntu !!

Regards
Feras

"mono program_name.exe"

Or install the binfmt-support package

---

### Post by Zugzwang on 2009-01-20
> **feras.ws said:**
> well thank you all for your replies.
I already installed mono and I programmed a simple program but how can I find it's debug file ?
I found one file caled program_name.exe ! but exe don't work on Ubuntu !!


Right. You start it with the command "mono <yourexe.exe>" on the terminal.

---

### Post by feras.ws on 2009-01-20
I tried but an error appears 
"Cannot open assembly f.exe." !
by the way , GTK means GUI ? or what ? sorry I still begginer .

Regards
Feras

---

### Post by mtausig on 2009-01-20
GTK is a GUI toolkit that is originally written in C. There is a .NET binding called gtk-sharp which is the most popular UI Toolkit used in mono.

---

### Post by feras.ws on 2009-01-20
thank you ;)
another question,I have mono 1.0.0 already installed ,how can I update it?
which command should I use?

---

### Post by directhex on 2009-01-20
> **feras.ws said:**
> thank you ;)
another question,I have mono 1.0.0 already installed ,how can I update it?
which command should I use?

No Ubuntu release has ever contained Mono 1.0

You're confusing the version number from somewhere else

---

### Post by feras.ws on 2009-01-20
it's written in the About section 
MonoDevelop ,version : 1.0 :)

---

### Post by directhex on 2009-01-20
> **feras.ws said:**
> it's written in the About section 
MonoDevelop ,version : 1.0 :)

Monodevelop is not Mono.

---

### Post by feras.ws on 2009-01-20
Am I so stupid ?
I'm so sorry :( !
mono's website is 
mono-project.com ?

Regards
Feras

---

### Post by feras.ws on 2009-01-20
MonoDevelop is an IDE :)
so sorry !

---

### Post by feras.ws on 2009-01-20
I found these packages for installing them 
deb [http://ppa.launchpad.net/firerabbit/ubuntu](http://ppa.launchpad.net/firerabbit/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/firerabbit/ubuntu](http://ppa.launchpad.net/firerabbit/ubuntu) intrepid main
how can I do so ?

Regards.
Feras

---

### Post by SeanHodges on 2009-01-20
Take a look at this page: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

[Edit] In particular, scroll down to the "Third-Party Software Tab" section.


That site (help.ubuntu.com) is a good source of information for Ubuntu, worth bookmarking.

---

### Post by Kilon on 2009-01-20
> **SeanHodges said:**
> Take a look at this page: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

[Edit] In particular, scroll down to the "Third-Party Software Tab" section.


That site (help.ubuntu.com) is a good source of information for Ubuntu, worth bookmarking.

Agreed , installing from synaptic is far more easier. See the link and if you experience any problems ask again. If you activate all the repositories and type "mono" in the search should find it immediately and then check install and apply and that is it.

---

### Post by feras.ws on 2009-01-20
Thank you all for your assistance , I really appreciate it .
and I'm trying right now , and i'll back to write the result ;)

Regards
Feras

---

### Post by feras.ws on 2009-01-20
Well installing was done successfully 
now I have some questions ,Mono is not a program right ? I mean it's just a compiler , so I cannot run it directly , I have to use mono command to open .exe programms right ? and this exe programs probably wrtitten via MonoDevelop , right ?
waiting your assistance .

best Regards
Fears

---

### Post by ajackson on 2009-01-20
If you install the package binfmt-support you can run compiled programs doing a simple
```
./progname.exe
```

---

### Post by SeanHodges on 2009-01-20
> **feras.ws said:**
> Well installing was done successfully 
now I have some questions ,Mono is not a program right ? I mean it's just a compiler , so I cannot run it directly , I have to use mono command to open .exe programms right ? and this exe programs probably wrtitten via MonoDevelop , right ?
waiting your assistance .

best Regards
Fears

The **Mono Project** comprises of the entire development platform, from the libraries to the development tools. For example, the "mono" and "mcs" programs are part of the Mono project.

The **"mono" program** is the runtime environment that a Mono program depends on to run. Similar (but not the same) as the "java" (JVM) program in the Java programming language.

The "mcs" program is the **compiler**. Which AFAIK is what MonoDevelop uses to compile your programs.

MonoDevelop is an **IDE**, you don't need to use it to create Mono programs, it exists as a tool to make development easier.

I recommend you read the [Getting Started]("http://mono-project.com/Start") sections on the official Mono site, and also scan the [FAQ]("http://www.mono-project.com/FAQ:_General"), which has some useful information as well.

---

### Post by mtausig on 2009-01-21
> **SeanHodges said:**
> 
The "mcs" program is the **compiler**. Which AFAIK is what MonoDevelop uses to compile your programs.


mcs was the compiler used in mono 1.x. Since mono 2.0, the compiler is called gmcs.

---

### Post by SeanHodges on 2009-01-21
> **mtausig said:**
> mcs was the compiler used in mono 1.x. Since mono 2.0, the compiler is called gmcs.

My mistake, it does explain that in the documentation as well.

---

