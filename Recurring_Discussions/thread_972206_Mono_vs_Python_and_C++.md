---
title: "Mono vs Python and C++"
date: 2008-11-05
forum: Recurring Discussions
---

### Post by Kilon on 2008-11-05
Hello guys , I am new with UBUNTU . Just installed it in work and I use it exclusively . On the other hand I am not new with programming , even though mainly on the academic side , I love studying computer languages. I have studied ,C , C++, assembly, Delphi, Dbase, Clipper, GWbasic, VB, C#, Java, Python and HTML. From all these Delphi, C++, C# and Python are my favourites. 

I am very excited with the warm community surrounding UBUNTU and I will really like to restart programming. 

Initially  I was think of Combining Python and C++ . I am quite experienced with C++ but I like Python because is very easy to use . Unfortunately I had some problem finding appropriate documentation and sample code for python when I was in Windows. That was the reason for turning to C# which I loved very much cause it is very similar to my favourite programming language DELPHI with the difference that like C++ there is a huge community supporting t. 

I have seen that UBUNTU supports all the programming languages. But I am very interested in MONO and of course C#. My question is which one will be easier to find appropriate documentation for and whether it will be easy to port the code to Windows and MAC OS. I have and iMAc at home and I would love to make cross platform software. 

The software that interests me is , database, 3d -2d graphics and music production. 

So basically I want people who have experience with MONO, C# , C++ and Python to share it with me and advice me what will be the easiest to use .


Oh And something else , before the demise of the Delphi project , because .NET frameworks was in a sense a clone of DELPHI , Borland mange to release DELPHI .NET which supported not only the .NET but also all the legacy libraries of Delphi . Does anyone knows if it is possible to port DELPHI .NET or PASCAL to MONO. I know I probably ask too much  but a question never hurts anyone.

---

### Post by cabalas on 2008-11-05
I'm going to avoid commenting on which language to choose as this can very easily turn into a flamewar, but if you are interested in Delphi it might be worth having a look at [Lazarus]("http://www.lazarus.freepascal.org/") which provides similar functionality to Delphi and is available in the repositories.

---

### Post by Kilon on 2008-11-05
> **cabalas said:**
> I'm going to avoid commenting on which language to choose as this can very easily turn into a flamewar, but if you are interested in Delphi it might be worth having a look at [Lazarus]("http://www.lazarus.freepascal.org/") which provides similar functionality to Delphi and is available in the repositories.

Thanks man for reminding Lazarus , shame on me , I had completely forgot about it. I have used lazarus very shortly , and it is quite good actually. Found a usefull you tube video 

[http://www.youtube.com/watch?v=TP7qFVdtmNQ](http://www.youtube.com/watch?v=TP7qFVdtmNQ)
[http://www.youtube.com/watch?v=K9jAdoOzzNM&feature=related](http://www.youtube.com/watch?v=K9jAdoOzzNM&feature=related)

Not interesting in starting a flame war here, I love so many language even as challenging as Assembly, so no , just want to share experience that is all. 

Lazarus is a good suggestion , I will look to it, but I am still very interested in the MONO project. So if anyone has experience with MONO or Python / C++ in UBUNTU , please share and advice me, I will appreciate any help.  Of course you can make suggestions outside these two choices, I have an open mind.

---

### Post by Mickeysofine1972 on 2008-11-05
Well I have recently been freelancing in ASP.NET and found that it isnt easy to use Mono to develop web apps.

The biggest problem was that if your going to use a database you need to have SQL Server not MySql as most web hosts assume you will need a windows based system for .net sites :( 

So that means when you do a site you have to change all your MySql database connects to a SQL Server type instead.

My advice is if you are doing web dev and want to use Mono, make a VM SQL server.

However, Python wont let you down in this regard and you can pretty much do what you want, although from a web dev perspective I would choose PHP or Ruby on Rails

Well thats my 2p anyway and I dont claim to be a authority, only someone who works in the industry.

Mike

---

### Post by ggaaron on 2008-11-05
Don't use lazarus it uses GTK1 which was replaced by GTK2 a long time ago, I had problems even starting it. Python is good and it is pretty well documented too - look at python.org.

---

### Post by jimi_hendrix on 2008-11-05
id say go java...since i think you can run that on your microwave if you need to and it is VERY similar to c# (i like C# better though...)

---

### Post by Delever on 2008-11-05
For C#, I found that MonoDevelop is decent, however, it still can't speed up development the way Visual Studio does. So I run Visual Studio in virtual machine when I need to develop for .Net. If I need assembly to be cross-platform, I from time to time check how it works on linux under mono.

Using Python on Ubuntu is few steps above using it on Windows - being able to run python scripts anywhere "out of the box". Tried to do web development with python - psp (python server pages) and handlers, that was hard to get started and keep going, so in the end I finished what I needed with php. Tried to use various existing libraries with python, I liked how it was easy to install and use them.

I knew only basics of C when I moved to Ubuntu, and I decided to learn C++. It took me a while to find out that popular tool for distributing programs is automake (or autotools). Long story short, learned to compile same C++ sources on both windows and linux (this particular case was with SDL, opengl, boost). I still use Visual Studio for C++ in vm (shame on me), so not really big migration.

To sum up my experience - job is easy when you know the tools.

---

### Post by Kilon on 2008-11-06
**@ Mickeysofine1972:** Thanks a lot for this advice , what you say is important of course , even though I do not see myself doing lot of web development. Maybe I should look to PHP as well, many people use it. 

**@ ggaaron:**That is exactly my fear , that is why I will probably follow your advice and steer away from lazarus. I have looked in python.org in the past and I have to agree is a very well documented site. 

**@ jimi_hendrix :** Java is an very powerful language , the most cross platform and it sacrifices no speed. However , I really hate its GUI and feel like you that C# is easier to write and read. I will probably keep an eye on JAVA as well. 

**@ Delever:** That was I was thinking by the way, that MONO is decent and Python very good. 

And things get more difficult when I saw the poll result , it seems that alot of people like MONO. So I did a little search on sourceforge and I was blown away. Anywhere I looked C# was there. I did some Linux browsing but once again C# came at the top. 

[http://sourceforge.net/softwaremap/trove_list.php?form_cat=201](http://sourceforge.net/softwaremap/trove_list.php?form_cat=201)
[http://sourceforge.net/softwaremap/trove_list.php?form_cat=66](http://sourceforge.net/softwaremap/trove_list.php?form_cat=66)

Of course my search made it clear that most project used several languages which made sense to me. So I think for the time being I will have to take a careful look at MONO and C# , leaving my doors open for Java, Python and C++. 

I was thinking of cooperating with other people on sourceforge on open source software. Preferably Platform Independent but with emphasis on Ubuntu first and MACOS second . 

But please keep your advice and suggestions coming , I can learn alot of things from your experience and avoid unnecessary trouble. I have studied all these language and learn all the basic like , object orientation , data mangement, strings, math, directx, and basic language synthax, so I am not afraid to use them at the same time if this will make my life easier.

I would like to thank all the people who replied , it means alot to me.

---

### Post by raf_kig on 2008-11-06
If you are focusing on developing for GNU/Linux i'd strongly suggest using c/c++. Most large projects are using it.
Using eg QT for your GUI you can develop for a variety of platforms.

For small/fast developed applications you could use python + pyqt, this way you'd always be using the same GUI Framework.

Regards

raf

---

### Post by Kilon on 2008-11-06
Oh by way , has anyone used ironpytnon ? Ironpython is in a sense "PYTHON .NET" it would be cool if ironpython could play nice with MONO , but as I have seen in MONO webpage only C# is fully supported. Any ideas?

**@ raf_King:** I do not know what I did wrong while searching in sourceforge but it seems I was wrong. You are right in LINUX, C++ is dominant. This make more sense now , It felt weird to see the majority of sourceforge for linux code in C# instead of C++. But now I see that 90% uses C++ with a 3% using C# and 7% Java and Python. As cross platform Java seems the winner here. So it seems that studying C++ is mandatory. Well IT was not something I did not expect.

---

### Post by directhex on 2008-11-06
> **raf_kig said:**
> If you are focusing on developing for GNU/Linux i'd strongly suggest using c/c++. Most large projects are using it.
Using eg QT for your GUI you can develop for a variety of platforms.

I'd suggest the opposite - using a language like C means you'll spend hours fighting the language constructs rather than the actual task at hand. I've made that mistake more than once.

> **Kilon said:**
> Oh by way , has anyone used ironpytnon ? Ironpython is in a sense "PYTHON .NET" it would be cool if ironpython could play nice with MONO , but as I have seen in MONO webpage only C# is fully supported. Any ideas?

[http://packages.ubuntu.com/hardy/ironpython](http://packages.ubuntu.com/hardy/ironpython)

jms@osc-franzibald:~$ ipy -V
IronPython 1.1.1 (1.1.1) on .NET 2.0.50727.42

> **Kilon said:**
> My question is which one will be easier to find appropriate documentation for and whether it will be easy to port the code to Windows and MAC OS. I have and iMAc at home and I would love to make cross platform software. 

Any "pure" .NET app should be cross-platform, with literally zero added work. The problem is the question of non-cross-platform sections - The dreaded P/Invoke. Is the native library you're trying to P/Invoke cross-platform? Yeah? Okay, how about the .NET assemblies you're using, e.g. the GUI framework. Is that cross-platform and free of P/Invokes too? Fr'example, Cocoa# is Mac-only, GTK# works anywhere but requires a GTK#-for-MS.NET installation to use on Windows, WinForms runs anywhere but looks like *** on non-Windows.

PM me for links to an app I wrote for use at work, which ran unmodified (and pretty much untested) on Windows & Mac, having been written on AMD64 Ubuntu

---

### Post by Kilon on 2008-11-06
Thanks for the reply. In C++ i am experienced with Dos programming mainly. But C# .NET i studied most beginners  stuff . I would really like to see your code and see for myself what the differences are. Of course , I already understood that there could be differences from platform to platform. But you had shed some light to what exactly this is and I thank you for this. 

Obviosuly if .NET has minor problems to implement would be my main choice. I LOVE .NET!!!! Some people may hate it, but as far as I studied it it seems very easy and straighforward. but as I said no problem working with other languages as well. 

Thanks a ton for the ironpython link. I will try to make some test programms with all these languages in UBUNTU and see by myself how it is going.

---

### Post by pmasiar on 2008-11-06
> **Kilon said:**
> when I saw the poll result , it seems that alot of people like MONO. So I did a little search on sourceforge and I was blown away. Anywhere I looked C# was there.

1) Every language is everywhere.
2) From number of responses, you have pretty weak selection of advisors, most likely self-selected people responding in any thread mentioning Mono (and there is not that many of those). Myself included: I just wondered who in right mind can be so confused and compare so different languages from so different niches. It is almost like: "what is better? Orange, lightbulb, or a dog?"

Your areas of interest seems to be: database, 3d -2d graphics and music production.

For database app, C#/Mono or C++ are overkill, Python is best, especially with web framework like Django or Turbogears.

2D, 3D graphics is done in C++ or C#, but **using it** for applications is overkill again, Python has wrapper for all important libraries. So unless you work on library itself, you don't need low-level language like C++ or C#.

For music, it is question of libraries again, and Python has plenty.

Then, it is question of what project you like to contribute to, and which language it uses: many projects made wrong decision long ago to use low-level language "for speed" and muddle along.

Of course, high-level language is best choice for user-facing code: low-level library is better done in effective low-level language, but then I would prefer C to C++.

Mono is completely different world, designed to be incompatible with free software libraries (and with Java, which is another world), it's almost impossible to mix code together, so be careful in which world you dive and waste years to master.

---

### Post by roelpeeters on 2008-11-06
> **cabalas said:**
> I'm going to avoid commenting on which language to choose as this can very easily turn into a flamewar, but if you are interested in Delphi it might be worth having a look at [Lazarus]("http://www.lazarus.freepascal.org/") which provides similar functionality to Delphi and is available in the repositories.
I coudn't agree more, I refuse to vote, since it all depends on what you have to do.

---

### Post by directhex on 2008-11-06
> **pmasiar said:**
> you have pretty weak selection of advisors

> **pmasiar said:**
> Mono is completely different world, designed to be incompatible with free software libraries (and with Java, which is another world), it's almost impossible to mix code together, so be careful in which world you dive and waste years to master.

Proving your own point, it seems.

1) "designed to be incompatible with free software libraries" - erm... how so? You're telling me the Mono apps installed by default on Ubuntu don't make use of Free software libraries like dbus, gconf2, libart-2.0-2, libatk1.0-0, libc6, libcairo2, libexif12, libflickrnet2.1.5-cil, libgconf2.0-cil, libgl1-mesa-glx, libglade2.0-cil, libglib2.0-0, libglib2.0-cil, libgmime2.2-cil, libgnome2.0-cil, libgnomeprint2.2-0, libgnomeprintui2.2-0, libgnomeui-0, libgnomevfs2-0, libgnome-vfs2.0-cil, libgphoto2-2, libgphoto2-port0, libgtk2.0-0, libgtk2.0-cil, libgtkhtml3.16-cil, libgtkspell0, libjpeg62, liblcms1, libmono2.0-cil, libmono-addins0.2-cil, libmono-addins-gui0.2-cil, libmono-cairo2.0-cil, libmono-corlib2.0-cil, libmono-sharpzip2.84-cil, libmono-sqlite2.0-cil, libmono-system2.0-cil, libmono-system-data2.0-cil, libmono-system-web2.0-cil, libndesk-dbus1.0-cil, libndesk-dbus-glib1.0-cil, libpanel-applet2-0, libpango1.0-0, libx11-6, libxcomposite1, mono-runtime, sqlite and sqlite3 ?

2) Ubuntu has packages for compiling (and using) Java code in Mono. apt-cache search ikvm

3) "impossible to mix code together" - I really don't know where to begin. Have you ever heard of the MIT/X11 license?

---

### Post by Kilon on 2008-11-06
> **pmasiar said:**
> 1) Every language is everywhere.


Mono is completely different world, designed to be incompatible with free software libraries (and with Java, which is another world), it's almost impossible to mix code together, so be careful in which world you dive and waste years to master.

So basically you are a Python supporter . Well you are not mistaken , python is easier to use but it is very slow , I have read that is 20X times slower than C++. Obviously there are optimization solutions. 

You say that I compare very diffirent languages. I must confess I am not an experienced programmer and I will not try to play it smart here. But I have studied all these languges and I would not call C# "low level", at least the part of the language I studied. I made soem basic programms with C# in windows and I had no problems. Python was another story all together. For example tried to build windows with WX in python and it was pain in the ***, the documentation I found was not the best I have seen and in the end I gave up.

[http://wxpython.org/](http://wxpython.org/)

On the the other hand . NET winforms were a piece of cake. This was a big reason why I abandoned Python. If I cannot tame the GUI I see no reason to continue on a a language. 

But his was in windows , now I am in UBUNTU. 

I really like the fact that Python is a spartan language which takes all unnecessary complexity out but I felt that at some areas the documentation was weak. And that is my main problem , I do not want to bother you guys with noob question , I would love to have help files that explain everything with examples and sample code and help me step by step to develop my skills. 

But of course I was amazed by PyGame , a very easy library and quite straightforward. And I know there some very good python  bindings for GNOME , hopefully much better than wxPython. That is why I am very interested in Ironpython which can call both Python and .NET libraries. 

Also I cannot really say exactly where I will be using the language , I wish I knew . Maybe it will be a game , maybe a small database. But what I can say for certain it will be for very small programs. I try to set easy and achievable goals.  

So I have no problem converting 100% to python if I can find all relevant documentation , detailed enough. I am very new with UBUNTU and I have the well known Python Reference book and I have visited python.org many times .

So let me make some questions about documentation.

Where do I go for python database programming (small scale) ?

Where do I go for gnome ? Can I use gnome with MAC OS or Windows ?

Already started to try both Python and C# in Ubuntu, I would like to see for myself which one I find easier. In windows I found C# easier , maybe in Ubuntu things will change.

---

### Post by nvteighen on 2008-11-06
> **directhex said:**
> Proving your own point, it seems.

1) "designed to be incompatible with free software libraries" - erm... how so? You're telling me the Mono apps installed by default on Ubuntu don't make use of Free software libraries like dbus, gconf2, libart-2.0-2, libatk1.0-0, libc6, libcairo2, libexif12, libflickrnet2.1.5-cil, libgconf2.0-cil, libgl1-mesa-glx, libglade2.0-cil, libglib2.0-0, libglib2.0-cil, libgmime2.2-cil, libgnome2.0-cil, libgnomeprint2.2-0, libgnomeprintui2.2-0, libgnomeui-0, libgnomevfs2-0, libgnome-vfs2.0-cil, libgphoto2-2, libgphoto2-port0, libgtk2.0-0, libgtk2.0-cil, libgtkhtml3.16-cil, libgtkspell0, libjpeg62, liblcms1, libmono2.0-cil, libmono-addins0.2-cil, libmono-addins-gui0.2-cil, libmono-cairo2.0-cil, libmono-corlib2.0-cil, libmono-sharpzip2.84-cil, libmono-sqlite2.0-cil, libmono-system2.0-cil, libmono-system-data2.0-cil, libmono-system-web2.0-cil, libndesk-dbus1.0-cil, libndesk-dbus-glib1.0-cil, libpanel-applet2-0, libpango1.0-0, libx11-6, libxcomposite1, mono-runtime, sqlite and sqlite3 ?

3) "impossible to mix code together" - I really don't know where to begin. Have you ever heard of the MIT/X11 license?

pmasiar is confusing copyright licenses with software patents, but what he says it's true. Mono is in a kind of gray-zone, very vulnerable to any Microsoft's patent claim over their .Net platform. That's the problem with Mono today.

---

### Post by directhex on 2008-11-06
> **nvteighen said:**
> pmasiar is confusing copyright licenses with software patents, but what he says it's true. Mono is in a kind of gray-zone, very vulnerable to any Microsoft's patent claim over their .Net platform. That's the problem with Mono today.

It's a topic that's been done to death, and belongs in Recurring Discussions (or the bin, depending). Short version: read [http://www2.apebox.org/wordpress/linux/51/](http://www2.apebox.org/wordpress/linux/51/)

---

### Post by pmasiar on 2008-11-06
> **directhex said:**
> Proving your own point, it seems.

No, I just wanted to throw a grenade, because I **knew** someone will run to save Mono and dig link to endless discussions - I was too busy to do it myself and that viewpoint was clearly missing :evil:

Thanks for all the fish

> 3) "impossible to mix code together" - sorry I misspoke. It is possible. Some people are paranoid about legal issues, some are not afraid to walk into mine field and choose to ignore them. Choose your poison!

---

### Post by themusicwave on 2008-11-06
I read through the thread an honestly it is hard to say what you will enjoy and find most useful.

I have experience in many languages, but primarily use Java, C# and Python for my day to day work.  Each fits a niche for me.

I have never used Mono, only Microsoft's .Net.  To be honest it is a nice frame work if all you ever want to do is Windows.  If you want to write programs for Windows and only Windows it just might be the best choice(depending on application domain).

However, I too am a bit wary of Mono.  As was mentioned it is a bit of a gray area legally, and it is unclear what Microsoft intends to do with it. 

For the most part Java and C# are very similar.  With an IDE like Netbeans, even the GUI creation is fairly simple.  Granted it is still not quite as awesome as Visual Studio's GUI creator, but it is pretty good.


In the Python world I haven't found too many great cross platform GUI editors.  I do love Python, I use it extensively for server scripts and web scripting.  However, I rarely create GUIs with it.  So I cannot speak to this area much.

My advice would be instead of using C# use Java.  This is for a few reasons:

1) It is Open Source
2) It is truly cross platform without the possible legal implications of Mono.
3) It has good tools in the form of Netbeans.

You are free to do whatever you like, but from reading your posts, Netbeans and Java seem like a good combination for you.

However, Java can be overkill depending on the program.  If it is small Python may still be a better choice.

---

### Post by directhex on 2008-11-06
Mono is only "legally grey" because of tinfoil hat wearing rejects like the Boycott Novell morons running around with a paint pot. It is no more "dangerous" than OOo or Firefox - probably less so

---

### Post by samjh on 2008-11-06
> **directhex said:**
> Mono is only "legally grey" because of tinfoil hat wearing rejects like the Boycott Novell morons running around with a paint pot. It is no more "dangerous" than OOo or Firefox - probably less so

Let's be more precise here.

The [ECMA-standardised portions of Mono](http://mono-project.com/ECMA) are legally safe.  Microsoft cannot claim patent rights over those portions, or at least any efforts to do so will be legally dubious.  These portions are the C# language and the CLI.

It's the non-ECMA'ed portions which are in a legal grey-area.  These areas include ADO.NET, ASP.NET VB.NET (the language), WinForms, and others.

> **Kilon said:**
> The software that interests me is , database, 3d -2d graphics and music production. Use Python and C++, and mostly C++.

C# does not yet have mature libraries for 3D graphics and music production, at least not any that I'm aware of.

C++ has plenty of such libraries, and Python has some.  You'll generally want to use C++ for 3D graphics and music, because even when using Python wrappers of C/C++ libraries, the performance slow-downs can be significant, and those are performance-intensive applications.  For databases and 2D graphics, Python should be more than enough.

---

### Post by Kilon on 2008-11-07
Thank you all for your replies, It is not the language you choose, it is the way you present it that it is important to me. 

As I said before there no "better or worse" languages inside my head, each language has its own advantages and disadvantages. 

Unfortunately I had bad experince in MAC OS with both my choices. 2.6 python is installed but refuse to excute any py script and Also IDLE does not even start . 2.5 works fine though. Mono compiles ok , but cannot find GTK assembly and  eventhough I have managed to execute some GTK code , it crashes some times. It loads GTK through X11 and I cannot say i put alot of confidence in X11. 


On UBUNTU , everything installs and runs fine, even iron python so far. 

Of course there is the JAVA choice, but as I have said , I find Java in some case like the SWING unecessary complex. The good news with JAVA is that it is fully supported by APPLE and not only comes with the OS it is updates through the OS and of course there are tons of JAVA info spefic to MAC OS in Apples Developer website.  

I think it is important for the viability of programer that the user will have to do as less as possible , especially in the MAC platform where thing are very easy by nature. So I start to doupt whether MONO or Python are good choices. 

And then is C++ . I am ok with C++ but it is the most complicate of them all. This could be easily compensated by the appropriate libraries to make life easier, Like SDL or GTK.  So it is not an option that I have ruled out. Also I am not kidding myself I know that in both Java and especially C++ I will find tons of documentation and source code to assist me in my progress. 

But I see python as the choice I would like to make , it is the most compact of all and very easy to use , also the fact that is cross platform is something I cannot ignore. I know that python in some areas can be as 20 to 30 times more slow than C++, but I also know that like most programming languages Python can cooperate perfectly with C++ and thus increase its speed immensely.  The Quests continues for an Answer .

---

### Post by sakabato on 2008-11-07
> **themusicwave said:**
> 

I have never used Mono, only Microsoft's .Net.  To be honest it is a nice frame work if all you ever want to do is Windows.  If you want to write programs for Windows and only Windows it just might be the best choice(depending on application domain).


Are you referring .NET or Mono ? And why do you think .NET Programs are windows only ? There are many many applications built on .net or runs on mono. Unless they "use JNI".
> **themusicwave said:**
> 
However, I too am a bit wary of Mono.  As was mentioned it is a bit of a gray area legally, and it is unclear what Microsoft intends to do with it. 
 Microsoft intends to do with Mono ? Microsoft has no control over mono. Zero, zilch , nada!

> **themusicwave said:**
> 


1) It is Open Source
2) It is truly cross platform without the possible legal implications of Mono.
3) It has good tools in the form of Netbeans.


1-) Actually you are confused here. Java is not opensource (not until java 7) but C# is 

2-) So called "potential" patent infringes dicussed a lot. There is no evidence that Mono has legal implications at all. (If you have it then show it). Mono is almost 6 years old!! I wonder this patent discussions will recur when it is 16 years old.


3-) MonoDevelop, Sharpdevelop and Visualstudio is also fine. 
Actually I am turkish and Netbeans never runs in Turkish locale in windows. It just fails as well as many java programs. Sorry but I won't buy a framework who doesn't have decent internationalization support.

---

### Post by directhex on 2008-11-07
> **pmasiar said:**
> No, I just wanted to throw a grenade, because I **knew** someone will run to save Mono and dig link to endless discussions - I was too busy to do it myself and that viewpoint was clearly missing :evil:

Thanks for all the fish

Short version: You're a troll?

---

### Post by pmasiar on 2008-11-07
> **Kilon said:**
>  I know that python in some areas can be as 20 to 30 times more slow than C++, but I also know that like most programming languages Python can cooperate perfectly with C++ and thus increase its speed immensely.  The Quests continues for an Answer .

That **is** your answer. If 90% of the time is spent outside of your code (web server, database query), you have control on 10% of the total running time, and replacing Python with C++ will cut running time by max 10%. What else  you want to know?

Speed is not a problem until you can **measure** where exactly it is a problem (and it is your code). Premature optimization is root of all evil.

---

### Post by pmasiar on 2008-11-07
> **sakabato said:**
>  Microsoft intends to do with Mono ? Microsoft has no control over mono. Zero, zilch , nada!

LOL. When (not if) MSFT decides to change direction ("upgrade") to confuse  competition again (read about [cover fire](http://www.joelonsoftware.com/articles/fog0000000339.html) from someone who worked for MSFT), would Mono has the option not to follow? Zero, zilch , nada! :twisted:

> So called "potential" patent infringes dicussed a lot. There is no evidence that Mono has legal implications at all. (If you have it then show it). Mono is almost 6 years old!! I wonder this patent discussions will recur when it is 16 years old.

Not a chance. Just FYI, patent protection lasts 25 years ;-)

---

### Post by directhex on 2008-11-07
> **pmasiar said:**
> LOL. When (not if) MSFT decides to change direction ("upgrade") to confuse  competition again (read about [cover fire](http://www.joelonsoftware.com/articles/fog0000000339.html) from someone who worked for MSFT), would Mono has the option not to follow? Zero, zilch , nada! :twisted:

Being ignorant is acceptable - but if you don't understand something, ask, don't make things up.

.NET 1.1 is final. Fixed in place. It cannot be "upgraded" without breaking all 1.1 apps on Windows.

.NET 2.0 is final. Fixed in place. It cannot be "upgraded" without breaking all 2.0 apps on Windows.

This is how .NET works. Apps are built against specific versions ("Strong Named" to a particular version number), and can only execute if that version is present (or a version which identifies itself as 100% backward compatible).

There are two ways Microsoft can introduce "issues" - and none of those, **NONE** of those, can affect existing apps. Either they release new assemblies (which apps would need to be reprogrammed to use), or make changes to the language design of their languages (where apps would need to be reprogrammed to make use of them).

If Microsoft introduce some new libraries, or updates their C# compiler, then that DOESN'T MATTER - app developers who want to run on all platforms will simply target the older versions (some people still write in Visual Basic 6 for god's sake!), and those writing quality Linux desktop apps really don't need to care less - does the lack of Windows Presentation Foundation matter if your entire GUI is written with GTK#?

And speaking of "updating their C# compiler", Mono has features today which are due to be added to Microsoft's compiler in 2012, for C# 5.0. Mono is, in some areas, ahead - Microsoft need to pur in serious work to catch up.

So please, don't regurgitate the tired old "MS can break it!" line, because it has very little attachment to the reality of things. And it's rather tiresome.

> > So called "potential" patent infringes dicussed a lot. There is no evidence that Mono has legal implications at all. (If you have it then show it). Mono is almost 6 years old!! I wonder this patent discussions will recur when it is 16 years old.

Not a chance. Just FYI, patent protection lasts 25 years ;-)

Prove to me that "ping", on your Ubuntu system, doesn't infringe any MS patents. Because **they** claim it does.

---

### Post by pmasiar on 2008-11-07
> **directhex said:**
> .NET 1.1 is final. Fixed in place. It cannot be "upgraded" without breaking all 1.1 apps on Windows.

Maybe you are not long enough using computers that you never  heard of MSFT setting "end of lifetime" on a technology, abandoning users? Like [http://en.wikipedia.org/wiki/FoxPro_2](http://en.wikipedia.org/wiki/FoxPro_2) ? Did you even bothered to read the linked article?

> So please, don't regurgitate the tired old "MS can break it!" 

Prove to me that "ping", on your Ubuntu system, doesn't infringe any MS patents. Because **they** claim it does.

Care to prove me that MSFT cannot "retire" any of system they sell?

With ubuntu, I have patents portfolio of IBM and many more companies on my side. With mono, defense is much weaker.

IMHO further discussion makes no sense: we are not going to change each other opinion, and OP is now better aware what a hornet nest of issues Mono is. Have a nice day, again!

---

### Post by directhex on 2008-11-07
> **pmasiar said:**
> Maybe you are not long enough using computers that you never  heard of MSFT setting "end of lifetime" on a technology, abandoning users? Like [http://en.wikipedia.org/wiki/FoxPro_2](http://en.wikipedia.org/wiki/FoxPro_2) ? Did you even bothered to read the linked article?

Who gives a ****? How does that prevent Mono from continuing to include the 1.0 corlib?

And you really haven't noticed that people still produce VB6 apps to this day?

> Care to prove me that MSFT cannot "retire" any of system they sell?

They don't "sell" Mono, they don't "sell" the ECMA/ISO spec for CLR 1.0. The spec is published and final. If they stop producing apps which can use it, then they just screw with thousands of users of existing apps (which can continue to bundle the 1.0 redistributable for as long as they like, of course)

> With ubuntu, I have patents portfolio of IBM and many more companies on my side. With mono, defense is much weaker.

Mono is in the default Ubuntu desktop. Hadn't you noticed?

> IMHO further discussion makes no sense: we are not going to change each other opinion, and OP is now better aware what a hornet nest of issues Mono is. Have a nice day, again!

Who's supplying the hornets? And throwing stones?

---

### Post by pmasiar on 2008-11-07
[Mono  meets MSFT](http://www.youtube.com/watch?v=tAVYYe87b9w)

---

### Post by directhex on 2008-11-07
> **pmasiar said:**
> [Mono  meets MSFT](http://www.youtube.com/watch?v=tAVYYe87b9w)

Classy. Now apply it to OOo or Firefox or Gnome or KDE or whatever

---

### Post by themusicwave on 2008-11-07
> **sakabato said:**
> Are you referring .NET or Mono ? And why do you think .NET Programs are windows only ? There are many many applications built on .net or runs on mono. Unless they "use JNI".
 Microsoft intends to do with Mono ? Microsoft has no control over mono. Zero, zilch , nada!


I do believe there is technology in Mono that falls under some of their patents.  However, most of Mono is surely safe.  There are some parts in question like ASP.net and VB .Net.  Also, very importantly Winforms are a questionable part.  Mono even notes this on their website.  [Mono Licensing]("http://www.mono-project.com/FAQ:_Licensing")They do have a plan to deal with it, but I still wonder why you would choose Mono where there is even a question over Java where there is no question.

> **sakabato said:**
> 
1-) Actually you are confused here. Java is not opensource (not until java 7) but C# is 


Is C# open source?  I know that it has an ISO standard, but Microsoft has no published any of their own code as far as I am aware.  I do know the Mono C# implementation is open source, but I don't believe C# as a whole is open source.  You are correct Java is not 100% open source, but it soon shall be.  It is about 95% there I believe.  It is also Sun's implementation that is being opened up in time.

> **sakabato said:**
> 
2-) So called "potential" patent infringes dicussed a lot. There is no evidence that Mono has legal implications at all. (If you have it then show it). Mono is almost 6 years old!! I wonder this patent discussions will recur when it is 16 years old.


> 
As mentioned above on Mono's website they state "For people who need full compatibility with the Windows platform, Mono's strategy for dealing with any potential issues that might arise with ASP.NET, ADO.NET or Windows.Forms is: (1) work around the patent by using a different implementation technique that retains the API, but changes the mechanism; if that is not possible, we would (2) remove the pieces of code that were covered by those patents, and also (3) find prior art that would render the patent useless. ".  


So on their own website they state that it is possible that part of the Mono framework has patent issues.  All they can offer is a hope to work around them or over turn them.  I don't want to base my software on hope like this.

> **sakabato said:**
> 
3-) MonoDevelop, Sharpdevelop and Visualstudio is also fine. 
Actually I am turkish and Netbeans never runs in Turkish locale in windows. It just fails as well as many java programs. Sorry but I won't buy a framework who doesn't have decent internationalization support.
[/QUOTE]

I have no experience with running things in Turkish so you are probably correct.  You do realize that their is nothing to buy though right?  I know it is a figure of speech, but the framework is free.

Let me just close by saying I actually like the .Net framework.  In fact I code in it quite often.  I use Windows everyday at work to write software.  Much of it is written in C# using Visual Studio.  All in all I like the platform, but I don't pretend it is really cross platform.  When I want a program for Windows I use .Net because it integrates with Windows very well.  When I want to have a worry free truly cross platform program I use Java or Python.  My employer won't touch Mono, they are afraid of the legal questions involved.

I would also like to note that I agree with the choice of Python for the OPs needs.  It has the libraries and cross platform capabilities he needs.  

Also, as for speed, depending what you are doing you may never even notice a program that is 20 or 30 times slower.  Often you would never even notice 100 times slower.  It depends on the task at hand and whether it is CPU bound, as in calculations or I/O bound as in database and memory access.  If the case is the later a faster language will not make your program noticeably faster.

---

### Post by LaRoza on 2008-11-07
> **themusicwave said:**
> 
Is C# open source?

It is a spec, mono is an implementation and is open source.

---

### Post by directhex on 2008-11-07
> **themusicwave said:**
> I do believe there is technology in Mono that falls under some of their patents.  However, most of Mono is surely safe.  There are some parts in question like ASP.net and VB .Net.  Also, very importantly Winforms are a questionable part.  Mono even notes this on their website.  [Mono Licensing]("http://www.mono-project.com/FAQ:_Licensing")They do have a plan to deal with it, but I still wonder why you would choose Mono where there is even a question over Java where there is no question.

Certain? Just because they might not be Sun's patents, doesn't mean there are definitely no patents involved. That's the real problem with patent trolls - they can torpedo anything from anywhere, and love generalizations

> Is C# open source?  I know that it has an ISO standard, but Microsoft has no published any of their own code as far as I am aware.  I do know the Mono C# implementation is open source, but I don't believe C# as a whole is open source.  You are correct Java is not 100% open source, but it soon shall be.  It is about 95% there I believe.  It is also Sun's implementation that is being opened up in time.

It's important not to confuse three things here - C# and .NET are not the same thing (C# is **A** .NET language, but there can be and are others), and Free Software is not the same as Standard. Java the language and Java the framework are "almost" Free Software, i.e. one vendor is pushing the software the way they feel, and most of the source for it can be downloaded - alternative implementations may be created, on the basis of the other source code as reference material.

C# the language and .NET the framework are Standards - meaning those standards are set in stone, and whilst they are updated by the people who wrote the software in the first place (Microsoft), the specifications are complete and allow for multiple implementations without the NEED for the parent company to release any source (and it forces that parent company to maintain compatibility between releases). There are four .NET frameworks in circulation - Microsoft.NET, Microsoft Rotor (an Open Source, but not very Free Software, .NET 1.0 framework for Mac/BSD), DotGNU Portable.NET (an immature but functional Free .NET 1.0 framework for assorted platforms), and Mono (a Free .NET 1/2 framework, with a C# 3.0 compiler.)

I would feel much more comfortable about Java if Sun were constrained by standards enough that they couldn't randomly break functionality between minor releases (as they can & have done)

> So on their own website they state that it is possible that part of the Mono framework has patent issues.  All they can offer is a hope to work around them or over turn them.  I don't want to base my software on hope like this.

What does your patent info on Firefox say, given it uses a probably-infringing COM+ implementation (XPCOM)?


> I have no experience with running things in Turkish so you are probably correct.  You do realize that their is nothing to buy though right?  I know it is a figure of speech, but the framework is free.

Java or .NET? Both!

> Let me just close by saying I actually like the .Net framework.  In fact I code in it quite often.  I use Windows everyday at work to write software.  Much of it is written in C# using Visual Studio.  All in all I like the platform, but I don't pretend it is really cross platform.  When I want a program for Windows I use .Net because it integrates with Windows very well.  When I want to have a worry free truly cross platform program I use Java or Python.  My employer won't touch Mono, they are afraid of the legal questions involved.

Fabricated legal questions. You think Python or Perl would be free from patents? It's not like the US patent Office care about prior art or other minor details like it... And remember, patent danger comes frmo small companies out to make a buck, not big companies who stand to lose more than they gain from patent-related litigation

> I would also like to note that I agree with the choice of Python for the OPs needs.  It has the libraries and cross platform capabilities he needs.

Non-trivial to be as cross-platform as he wants, though. Sadly, NOTHING would mean out-of-the-box "just double click" support across all platforms, everything needs per-arch tweaking (be it installing a framework or lib or something, or just making per-arch shortcuts)

> Also, as for speed, depending what you are doing you may never even notice a program that is 20 or 30 times slower.  Often you would never even notice 100 times slower.  It depends on the task at hand and whether it is CPU bound, as in calculations or I/O bound as in database and memory access.  If the case is the later a faster language will not make your program noticeably faster.

Absolutely 100% correct. As noted elsewhere, premature optimization is bad - and productivity gained from high-level languages is good

---

### Post by Kilon on 2008-11-08
Well I would like to inform you that I finally chose JAVA. 

I wrote down my priorities and said to myself that I wanted:

a. The language that is the easier to install and setup. 
b. The language which is most cross platform
c. The language with a very big community 
d. The language with most Documentation and APIs

In the end it came down to JAVA. The final blow was when I tried NETBEANS which I fell in love with and I finally decide to start with database programming. I spoke with the Greek Linux Group and they adviced me to use MySQL . I bought a big fat book in MySQL and now I have burried myslef inside 2 big books. 

[IMG]http://ecx.images-amazon.com/images/I/516RH3SJXEL._BO2,204,203,200_PIsitb-sticker-arrow-click,TopRight,35,-76_AA240_SH20_OU02_.jpg[/IMG] 

[http://www.amazon.co.uk/Ivor-Hortons-Beginning-Java-Guides/dp/0764568744/ref=sr_1_23?ie=UTF8&s=books&qid=1226182425&sr=1-23](http://www.amazon.co.uk/Ivor-Hortons-Beginning-Java-Guides/dp/0764568744/ref=sr_1_23?ie=UTF8&s=books&qid=1226182425&sr=1-23)

[IMG]http://ecx.images-amazon.com/images/I/414YP5A16AL._BO2,204,203,200_PIsitb-sticker-arrow-click,TopRight,35,-76_AA240_SH20_OU02_.jpg[/IMG]

[http://www.amazon.co.uk/Beginning-MySQL-Programmer-Robert-Sheldon/dp/0764579509/ref=sr_1_16?ie=UTF8&s=books&qid=1226182495&sr=1-16](http://www.amazon.co.uk/Beginning-MySQL-Programmer-Robert-Sheldon/dp/0764579509/ref=sr_1_16?ie=UTF8&s=books&qid=1226182495&sr=1-16)

almost 2000 page of reading , but I love it. I have made some basic Java test programms and I am happy to report that not only they run like a breeze and with no change in Windows , Ubuntu and MACOS, but also inherit the GUIs of each OS , so they look like native applications. Ultra Cool. 

I want to make a database and a software to control it for my office . Will see how it goes from there on. 

Again I would like to thank all people for their advice . I did not expect that I would be using JAVA cause python was my favourite choice. But Unfortunately JAVA is fully supported by APPLE while python is not. Mono has pretty much the same fate with python . 

About the discussion about patents, because I am a lawyer I can say this. Even the slightest effort of copying is infrigment of Copyright or Patent, so If Microsoft wanted to sue she would have done so ages ago. Microsoft benefits from mono and with zero expense, mono expands microsoft products into platforms that microsoft would not go otherwise. There is no fear for mono as matter of fact with the success of .NET , the future of mono is very bright and optimistic.

---

### Post by directhex on 2008-11-08
> **Kilon said:**
> Well I would like to inform you that I finally chose JAVA. 

I wrote down my priorities and said to myself that I wanted:

a. The language that is the easier to install and setup. 
b. The language which is most cross platform
c. The language with a very big community 
d. The language with most Documentation and APIs

In the end it came down to JAVA. The final blow was when I tried NETBEANS which I fell in love with and I finally decide to start with database programming. I spoke with the Greek Linux Group and they adviced me to use MySQL . I bought a big fat book in MySQL and now I have burried myslef inside 2 big books. 

[IMG]http://ecx.images-amazon.com/images/I/516RH3SJXEL._BO2,204,203,200_PIsitb-sticker-arrow-click,TopRight,35,-76_AA240_SH20_OU02_.jpg[/IMG] 

[http://www.amazon.co.uk/Ivor-Hortons-Beginning-Java-Guides/dp/0764568744/ref=sr_1_23?ie=UTF8&s=books&qid=1226182425&sr=1-23](http://www.amazon.co.uk/Ivor-Hortons-Beginning-Java-Guides/dp/0764568744/ref=sr_1_23?ie=UTF8&s=books&qid=1226182425&sr=1-23)

[IMG]http://ecx.images-amazon.com/images/I/414YP5A16AL._BO2,204,203,200_PIsitb-sticker-arrow-click,TopRight,35,-76_AA240_SH20_OU02_.jpg[/IMG]

[http://www.amazon.co.uk/Beginning-MySQL-Programmer-Robert-Sheldon/dp/0764579509/ref=sr_1_16?ie=UTF8&s=books&qid=1226182495&sr=1-16](http://www.amazon.co.uk/Beginning-MySQL-Programmer-Robert-Sheldon/dp/0764579509/ref=sr_1_16?ie=UTF8&s=books&qid=1226182495&sr=1-16)

almost 2000 page of reading , but I love it. I have made some basic Java test programms and I am happy to report that not only they run like a breeze and with no change in Windows , Ubuntu and MACOS, but also inherit the GUIs of each OS , so they look like native applications. Ultra Cool. 

I want to make a database and a software to control it for my office . Will see how it goes from there on. 

Again I would like to thank all people for their advice . I did not expect that I would be using JAVA cause python was my favourite choice. But Unfortunately JAVA is fully supported by APPLE while python is not. Mono has pretty much the same fate with python . 

About the discussion about patents, because I am a lawyer I can say this. Even the slightest effort of copying is infrigment of Copyright or Patent, so If Microsoft wanted to sue she would have done so ages ago. Microsoft benefits from mono and with zero expense, mono expands microsoft products into platforms that microsoft would not go otherwise. There is no fear for mono as matter of fact with the success of .NET , the future of mono is very bright and optimistic.

Have fun with it. java's certainly made improvements from when I was developing with it (at the time, you couldn't even use "int" and "Integer" interchangably without explicit casts)

---

### Post by Kilon on 2008-11-08
> **directhex said:**
> Have fun with it. java's certainly made improvements from when I was developing with it (at the time, you couldn't even use "int" and "Integer" interchangably without explicit casts)


Oh DirectHex ( very nice name by the way) thanks for the link to your mono programm , and all the info , it opened my eyes to things I did not know. I will surly keep my attention on both MONO and Python , I think they have alot to offer and maybe one day when the support for MAC OS is as good as it is in UBUNTU will make the switch to one of them.

---

### Post by neighborlee on 2008-11-08
> **directhex said:**
> Certain? Just because they might not be Sun's patents, doesn't mean there are definitely no patents involved. That's the real problem with patent trolls - they can torpedo anything from anywhere, and love generalizations

Absolutely 100% correct. As noted elsewhere, premature optimization is bad - and productivity gained from high-level languages is good

We understand that someone that programs in this for a living would defend it, but there is actually no defense of the fact that its rand agreement is nothing more than a 'promise' not to sue and you full well know that, so all this is just a diatribe of based on a given set of needs.

Does anyone here really trust M$'s activities if you look at the entire chain of events, and if I need to tell you what they are then you haven't been paying much attention. This leads to having exactly this kind of conversation. Im glad to see  though that some people get the risk and are avoiding mono  due to the patent mindfield it really is. You need to download it directly from Novel to be 'protected' from its threats, and if you call that FREE, I have some specially prepared swampland for you. The politics of fear and lies are over.

[http://en.wikipedia.org/wiki/Mono_(software](http://en.wikipedia.org/wiki/Mono_(software)) < and if we go here, we see how, just like wine chasing the proverbial tail of  gaming on a windows platform, that mono finds itself in the same quandry.

Richard Stallman (who is not involved with the project) has claimed it is "dangerous" to use Mono because of the possible threat of Microsoft patents[6].

"  On November 2, 2006, Microsoft and Novell announced a joint agreement whereby Microsoft agreed to not sue Novell’s customers for patent infringement.[7] According to Mono project leader Miguel de Icaza,[8] this agreement extends to Mono but only for Novell developers and customers. It was criticized by some members of the free software community because it violates the principles of giving equal rights to all users of a particular program (see Novell and their Patent Agreement with Microsoft). "

So tell me, exactly how does one square any of that with telling unsuspecting users that Mono isn't patent encumbered and therefore not free ?


cheers
nl

---

### Post by slavik on 2008-11-08
yet another language/platform war ...

---

