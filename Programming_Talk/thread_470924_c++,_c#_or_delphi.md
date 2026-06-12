---
title: "c++, c# or delphi"
date: 2007-06-11
forum: Programming Talk
---

### Post by ASPCartman on 2007-06-11
When i have only windows on my pc, i used to use Borland c++, c# and Delphi 7/8
But now i'm linux user and i want to continue my learning of this languages. BUT i was not able to find program that has interface like borland. For example: KDevelop. KDevelop c++ app was not like borland. Were are left panel with options? Where right panel with things that i can paste on window and WHERE IS WINDOW ITSELF?! WTF?
Anjuta - same story. HEEEELP I always use interface option first and only than work with the code (only with action part. Anything exept this must be (how i think) created by app automatically) 


HEELP

---

### Post by ASPCartman on 2007-06-11
Example:

[http://geany.uvena.de/images/geany_main.png](http://geany.uvena.de/images/geany_main.png)

WTF all of this? Were is window? Where is library? Were is actions dialog? WTF?
I want borland interface. I don't want to write whole f**ng code from 0!

---

### Post by ASPCartman on 2007-06-11
Have someone of you EVER worked with emmm Visual Basic at school ?(first what our teacher theached us) I want this interface. Not only code. I can edit code with gedit

---

### Post by Lord Illidan on 2007-06-11
What you want is an IDE which enables you to design forms, etc?

For Basic - Gambas
For C++ - Glade in conjuction with Gedit, or QTdesigner in conjuction with Kdevelop. Of course you can use any other text editor instead of Gedit or Kdevelop.
For C# - Mono with stetic or Glade..

Just research a bit. I cannot provide you with tutorials for those, as I don't use them myself, but google helps.

---

### Post by LaRoza on 2007-06-11
What is the problem with the IDE's you tried? Of course they will be different from others. 

You can do what I do, edit with my favourite text editor and compile through the command line.

You can try running the Borland compiler in Wine, but the resulting program will be a Windows program, which you would be able to run under Wine.

---

### Post by Hendrixski on 2007-06-11
What is your problem?

Here, go to Add/Remove programs and install Eclipse.  It is by far the best Development Environment ever made.  IBM makes it with the help of a several thousand developer community.  Borland is crap by comparison.  If you want to program in C_++ on eclipse then install the CDT plugin as well.

I used to program on Delphi back when I was a windows software engineer... and it was good... that was 5 years ago.

Visual Basic is complete crap.  Forget you ever learned it.  I had to write something in VB once and I almost stabbed my eyes out with a fork

---

### Post by Hendrixski on 2007-06-11
for C# there is something called Mono, but I haven't tried it... I've been programming with Qt lately.

If you want an application that does all of the window creation by point and click the way you did in kindergarten with Visual Basic then you can get install qtdesigner (it should be in Add/Remove).  You can even have qtdesigner work in conjunction with Eclipse.

If you want to keep learning programming learn on Linux.  most cell phones, home appliances, and all those sorts of things are run on Linux (or on VXWorks, which is the only OS that has been ported to more platforms than Linux).  Also, servers.  Most of them run on either Linux or Unix (today there is no difference between the two).  so stick with Linux for programming.

---

### Post by ASPCartman on 2007-06-11
I cannot to write the code from 0 just using gedit. 
Yes. I need form editor with code editor. (For example. I have add button on form. I clicked on it two times and code window opend with alreade added string f button action. ANd i just need to write the action(all other parts of code are hidden, but can unhidden if i want))

---

### Post by ASPCartman on 2007-06-11
I used qtdesigner but i have question:
1. What is QT?
2. It's based on KDE. I use GNOME (XGL, Beryl and other stuff)

---

### Post by ASPCartman on 2007-06-11
New question - why all of you writes of using add/remove? Emmm maybe Synaptic? ;)

---

### Post by LaRoza on 2007-06-11
You have more than one option, you have several with Ubuntu, one with add/remove in the menu, one with graphical Synaptic and through the cli with apt-get or aptitude. You can use any one you want, but it is not reasonable for anyone to expect a poster to list every method of any action.

---

### Post by Hendrixski on 2007-06-11
Add/Remove uses synaptic... it's just easier
you could type "sudo apt-get install" into the CLI

Qt is a framework for C++ ... it lets you make safe threads, GUI application (windows with buttons and stuff), and a lot of great database interaction stuff... it's what KDE is built from, but it works everywhere.  It works on Windows, the unixes (like Solaris, linux, or Mac) even vxworks and netware.  So yes, it will work on GNOME.

QtDesigner helps you with programming the GUI... the rest of it you should code by hand.

hope that helps

---

### Post by ASPCartman on 2007-06-11
I my undersdanding - programing thread is Form editior with code editor that can repair yor mistakes. But here is all the wrong way and form part is optional and this all not 1 app but more than 3. It's creazy!

---

### Post by 23meg on 2007-06-11
It's not crazy, it's just not what you're used to.

If you're looking for something strictly similar to Delphi, check out Lazarus.

[http://www.lazarus.freepascal.org/](http://www.lazarus.freepascal.org/)

You can even use your existing Delphi layouts with it.

---

### Post by ASPCartman on 2007-06-11
I (for test) crated simple form with button in qt designer. How to run it?

---

### Post by Hendrixski on 2007-06-11
> **ASPCartman said:**
> I my undersdanding - programing thread is Form editior with code editor that can repair yor mistakes. But here is all the wrong way and form part is optional and this all not 1 app but more than 3. It's creazy!
an application should do one thing and do it well..

Listen, your english is a little hard to understand... there should be communities in your native language.  For example, my native language is Polish, so I can go to IRC and ask people in my questions in Polish.  I just go to #ubuntu-pl

I live in NY so on IRC I just go to #ubuntu-ny and someone who lives close to me can answer my question.

To install an IRC client just go to Add/Remove and install XChat,  or use aptitide to install xchat :-)  then find the chanell in your native language.

---

### Post by ASPCartman on 2007-06-11
> **23meg said:**
> It's not crazy, it's just not what you're used to.

If you're looking for something strictly similar to Delphi, check out Lazarus.

[http://www.lazarus.freepascal.org/](http://www.lazarus.freepascal.org/)

You can even use your existing Delphi layouts with it.

All answers were great but it's the best! Thanks! 
Here i see form editor, code editor, compiler. But What language i can use there?

---

### Post by Hendrixski on 2007-06-11
> **ASPCartman said:**
> I (for test) crated simple form with button in qt designer. How to run it?

[http://doc.trolltech.com/3.3/designer-manual.html](http://doc.trolltech.com/3.3/designer-manual.html)
google is your friend

---

### Post by ASPCartman on 2007-06-11
Google is my frend but some time it makes my head explode :D

---

### Post by fifth on 2007-06-11
Why not check out NetBeans? Its a Java rad ide and platform independent.

[http://netbeans.org](http://netbeans.org)

---

### Post by 23meg on 2007-06-11
> **ASPCartman said:**
> All answers were great but it's the best! Thanks! 
Here i see form editor, code editor, compiler. But What language i can use there?

ObjectPascal, as in Delphi. It compiles with Free Pascal, which apparently can read Delphi ObjectPascal syntax.

---

### Post by ASPCartman on 2007-06-11
Is it good? when i create more than 10 objects on form, x server restart? WTF?

---

### Post by ASPCartman on 2007-06-11
I like Lazaruz. But in that moment when i add 10's object on form, X crashes. Why?

---

### Post by DrMega on 2007-06-11
> **ASPCartman said:**
> I my undersdanding - programing thread is Form editior with code editor that can repair yor mistakes. But here is all the wrong way and form part is optional and this all not 1 app but more than 3. It's creazy!

You can't develop anything serious all in one app even on Windows. In my day job I use Visual Studio.Net. That allows me to develop the client side, and I routinely have open SQL Server Query Analyser for developing the SQL for the server side, and SQL Profiler to debug the interactions between client and server.

I too am interested in making the switch to Linux development but have not found it easy, largely because things are done differently (not necessarily any better or any worse than on Windows). I personally found KDevelop to be the best IDE so far. I also looked at MonoDevelop for the C# aspect of stuff, but as it bears so little resemblance to the Windows version of C# (more due to the underlying OS differences than anything else) I didn't credit it with much merit to be honest.

---

### Post by ASPCartman on 2007-06-11
Anything that i saw so far was not for me. But lazarus is good. Pretty god. BUT - whats going on with xserver!?

PS
I'm not develloper (so far =))) ). I'm simple user that like to change everything and every thing that he see :popcorn: I'm going to be developer. And how u see, i'm 13 years old ;) And my knowledge was enough to kick my dad from my pc :D (1 year ago and bfore - his pc :( )  Now he asks pemition to use it :) 
PSS
My dad - radiofan :D

---

### Post by 23meg on 2007-06-11
> Anything that i saw so far was not for me. But lazarus is good. Pretty god. BUT - whats going on with xserver!?

A bug, probably, which you should submit to the Lazarus developers. Are you using Gutsy? If so, it's quite expectable.

---

### Post by ASPCartman on 2007-06-11
Gutsy? WHERRRREEEE!?!?!
I use Feisty.
Where should i submint bug?

---

### Post by DrMega on 2007-06-11
> **ASPCartman said:**
> Anything that i saw so far was not for me. But lazarus is good. Pretty god. BUT - whats going on with xserver!?

I hadn't heard of Lazarus (in this context at least) before reading this thread. I might give it a look.

> 
PS
I'm not develloper (so far =))) ). I'm simple user that like to change everything and every thing that he see :popcorn: I'm going to be developer. And how u see, i'm 13 years old ;) And my knowledge was enough to kick my dad from my pc :D (1 year ago and bfore - his pc :( )  Now he asks pemition to use it :) 
PSS
My dad - radiofan :D
good luck with that. If I could give you one tip (developer related) it would be this: Avoid any form of Basic if you want to get paid well when you become a developer. If you focus on a language that is has its heritage in C (eg C++, C#, Java or even PHP to some extent) you'll find it easier to transfer your skills to ther languages. Basic is quite different to most of the commercially popular languages.

One other piece of advice: The IT industry can be quite hard to get into. You have to be determined, and don't lose sight of what you want to do.

---

### Post by ASPCartman on 2007-06-11
Thanks :) Basic - is just language that our teacher loves. (Stupid bitch)
I think 120iq for IT will be enought? :D


PS
Still. Were i shold to submint bug?

---

### Post by Lord Illidan on 2007-06-11
> **ASPCartman said:**
> Thanks :) Basic - is just language that our teacher loves. (Stupid bitch)
I think 120iq for IT will be enought? :D


PS
Still. Were i shold to submint bug?

120 iq...can you spell properly please? I am having a hard time understanding half of your posts. Firefox has an inbuilt spell checker. Use it. If you are not a native speaker, well, make the effort. I am not a native speaker either.

---

### Post by ASPCartman on 2007-06-11
sorry.  120 iq - intelligence quotient. =) Tested on some site +) Bullshit but it says that 120 is much more than usual.
PS
Are you Russian? Cos' i'm so.

---

### Post by DrMega on 2007-06-11
> **ASPCartman said:**
> Thanks :) Basic - is just language that our teacher loves. (Stupid bitch)
I think 120iq for IT will be enought? :D


PS
Still. Were i shold to submint bug?
There's no need to slate your teacher, she's just doing her job. She probably uses Basic just because it is especially designed as a teaching language. It will give you a good foundation in the concepts of programming, its just the syntax that is not much like anything else.

Basic actually stands for Beginners All-purpose Symbolic Instruction Code.

---

### Post by ASPCartman on 2007-06-11
I slate her not cos' she teaches my basic :D I slate her cos' she is like crazy Hollywood blond.  ](*,)

---

### Post by newen on 2007-06-11
You can also try out anjuta 2 which comes with glade integration. It is in alpha stage, though

You can start learning Gtkmm, the C++ bindings for GTK+, the toolkit gnome is built upon. There're tutorials out there. You create your interface with Glade which generates a xml. It must be loaded by your code using ligblademm.

Gtk also supports threading, and with Gtkmm you get easy memory management. [http://www.gtkmm.org/](http://www.gtkmm.org/)
There's currently much more support for Gtk+ from mobile device vendors than for QTopia. One plus more in favour of Gtk+. It only lacks a good IDE as KDevelop for the platform.

---

### Post by ASPCartman on 2007-06-12
Sorry. But what is gtk?

---

### Post by Sammi on 2007-06-12
[http://en.wikipedia.org/wiki/Gtk](http://en.wikipedia.org/wiki/Gtk)
Wikipedia is your friend too ;)

---

### Post by Lord Illidan on 2007-06-12
> **ASPCartman said:**
> sorry.  120 iq - intelligence quotient. =) Tested on some site +) Bullshit but it says that 120 is much more than usual.
PS
Are you Russian? Cos' i'm so.

No, I am Maltese...and I knew what IQ was :)

---

### Post by jak on 2007-06-12
ASPCartman: Learn to find things yourself, half of your questions could have easily been answered with a quick search on a search engine.
If you're Russian, try [forum.ubuntu.ru]("http://forum.ubuntu.ru") - hopefully you're more understandable in your native language.

Also, this part of the forum is intended for Development discussion involving Gutsy Gibbon (Ubuntu 7.10) and is the wrong place to post your message as you have already stated you're not using it.

ASPCartman: &#1059;&#1095;&#1080;&#1090;&#1077;&#1089;&#1100; &#1085;&#1072;&#1093;&#1086;&#1076;&#1080;&#1090;&#1100; &#1074;&#1077;&#1097;&#1080; &#1089;&#1072;&#1084;&#1086;&#1089;&#1090;&#1086;&#1103;&#1090;&#1077;&#1083;&#1100;&#1085;&#1086;, &#1085;&#1072; &#1087;&#1086;&#1083;&#1086;&#1074;&#1080;&#1085;&#1091; &#1074;&#1072;&#1096;&#1080;&#1093; &#1074;&#1086;&#1087;&#1088;&#1086;&#1089;&#1086;&#1074;, &#1074;&#1086;&#1079;&#1084;&#1086;&#1078;&#1085;&#1086;, &#1083;&#1077;&#1075;&#1082;&#1086; &#1086;&#1090;&#1074;&#1077;&#1090;&#1080;&#1083; &#1089; &#1073;&#1099;&#1089;&#1090;&#1088;&#1099;&#1084; &#1087;&#1086;&#1080;&#1089;&#1082;&#1086;&#1084; &#1085;&#1072; &#1087;&#1086;&#1080;&#1089;&#1082;&#1086;&#1074;&#1086;&#1081; &#1089;&#1080;&#1089;&#1090;&#1077;&#1084;&#1077;.
&#1045;&#1089;&#1083;&#1080; &#1042;&#1099; - &#1088;&#1091;&#1089;&#1089;&#1082;&#1080;&#1081;, &#1087;&#1088;&#1086;&#1073;&#1091;&#1081;&#1090;&#1077; forum.ubuntu.ru-, &#1084;&#1099; &#1085;&#1072;&#1076;&#1077;&#1077;&#1084;&#1089;&#1103;, &#1042;&#1099; &#1073;&#1086;&#1083;&#1077;&#1077; &#1087;&#1086;&#1085;&#1103;&#1090;&#1085;&#1099; &#1085;&#1072; &#1074;&#1072;&#1096;&#1077;&#1084; &#1088;&#1086;&#1076;&#1085;&#1086;&#1084; &#1103;&#1079;&#1099;&#1082;&#1077;.

&#1050;&#1088;&#1086;&#1084;&#1077; &#1090;&#1086;&#1075;&#1086;, &#1101;&#1090;&#1072; &#1095;&#1072;&#1089;&#1090;&#1100; &#1092;&#1086;&#1088;&#1091;&#1084;&#1072; &#1087;&#1088;&#1077;&#1076;&#1085;&#1072;&#1079;&#1085;&#1072;&#1095;&#1077;&#1085;&#1072; &#1076;&#1083;&#1103; &#1086;&#1073;&#1089;&#1091;&#1078;&#1076;&#1077;&#1085;&#1080;&#1103; &#1056;&#1072;&#1079;&#1074;&#1080;&#1090;&#1080;&#1103;, &#1074;&#1086;&#1074;&#1083;&#1077;&#1082;&#1072;&#1102;&#1097;&#1077;&#1075;&#1086; &#1041;&#1077;&#1089;&#1089;&#1090;&#1088;&#1072;&#1096;&#1085;&#1086;&#1075;&#1086; &#1043;&#1080;&#1073;&#1073;&#1086;&#1085;&#1072; (Ubuntu 7.10) &#1080; - &#1085;&#1077;&#1087;&#1088;&#1072;&#1074;&#1080;&#1083;&#1100;&#1085;&#1086;&#1077; &#1084;&#1077;&#1089;&#1090;&#1086;, &#1095;&#1090;&#1086;&#1073;&#1099; &#1086;&#1073;&#1098;&#1103;&#1074;&#1080;&#1090;&#1100; &#1074;&#1072;&#1096;&#1077; &#1089;&#1086;&#1086;&#1073;&#1097;&#1077;&#1085;&#1080;&#1077;, &#1087;&#1086;&#1089;&#1082;&#1086;&#1083;&#1100;&#1082;&#1091; &#1042;&#1099; &#1091;&#1078;&#1077; &#1079;&#1072;&#1103;&#1074;&#1080;&#1083;&#1080;, &#1095;&#1090;&#1086; &#1042;&#1099; &#1085;&#1077; &#1080;&#1089;&#1087;&#1086;&#1083;&#1100;&#1079;&#1091;&#1077;&#1090;&#1077; &#1101;&#1090;&#1086;.

Do you see how annoying a badly written language is? And a 120 I.Q. is not particularly special.

---

