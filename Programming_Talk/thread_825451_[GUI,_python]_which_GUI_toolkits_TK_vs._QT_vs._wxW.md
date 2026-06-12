---
title: "[GUI, python] which GUI toolkits?? TK vs. QT vs. wxWidgets vs. GTK....."
date: 2008-06-11
forum: Programming Talk
---

### Post by kakyoism on 2008-06-11
I'm trying to learn a GUI tookits available for python that would live long enough and will be most probably used by large companies...(sorry for such a funny thought)

I was pretty fine with wxPython because it's easy to get my hands on and have a lot of compound widgets available. Unfortunately I don't see many realworld applications of it (except for a few open-source ones).

I've never tried pyQT, pyGTK, or Tk with python.

Please share your ideas~

---

### Post by mevets on 2008-06-11
You really have to consider what platform the applications are going to developed for. If its a kde install go with pyQT or pyGTK for gnome installs. If its for Windows I dont see why you would want to use gtk or qt when you already know wxWidgets. I would not use wxWidgets if its going to be developed for linux though, they're just such eyesores on Linux.

---

### Post by irrdev on 2008-06-11
First of all, you probably won't see many "real-world" GUI applications using python. Why? Most companies don't want to release the source code. Even programs such as py2exe don't really compile the python source code; the source code is simply added as a resource to the executable, and it is therefore easily extracted and modified.

Commercial programs that use python use it largely for scripting custom AI and program behaviours. Such an example is Civilization 3. The Python code actually makes calls to compiled C/C++ functions which manipulate the GUI. Using this method, the program is easily distributed and the scripting capabilities are restricted. You'll find that this is how most commercial programs using python work.

When it comes down to choosing a direct GUI library for python, my personal choice is definitely wxPython. It is still the most community-supported GUI library. If you are just programming for Linux, then pyGTK can be a good choice. I wouldn't recommend pyQT, simply because of the licensing retrictions. TK is good for small user interfaces, and the lastest version included with TCL has native theming on both Windows and Mac OS X. This updated version of TK should be included with Python 3. In the end, it is also a personal preference in relation to coding style; wxPython is very object oriented, while TK is the complete opposite, allowing for dynamic calls. You should seriously try them all out before making a final choice. ;)

---

### Post by regomodo on 2008-06-11
For a small application i would personally use Tk. It's easy to get the hang of and it's fairly obvious when you read it. However, it looks dog-ugly and i can't for the life of me figure out how to change tk apps themes.

I'm in the process of learning PyQt and it's not as easy (to read and learn) as i was lead to believe.

---

### Post by ByteJuggler on 2008-06-11
[This]("http://www.xminc.com/linux/wxpython.html") article might help.

---

### Post by ankursethi on 2008-06-11
PyGTK is pretty easy to learn. They have a neat tutorial on their website, too. What else could you ask for?

Use Tk for trivial interfaces. Otherwise, PyGTK.

---

### Post by pmasiar on 2008-06-11
> **irrdev said:**
> First of all, you probably won't see many "real-world" GUI applications using python. 

But this might not matter for what most programmer do: custom internal app development (as compared to shelfware) - where productivity is the most important, and Python is  considered more productive than most competitors (C++/C#/Java). And arguably you can create GUI and web app, and share big part of Python modules for it - and do it RAD style.

---

### Post by LaRoza on 2008-06-11
> **irrdev said:**
> First of all, you probably won't see many "real-world" GUI applications using python. Why? Most companies don't want to release the source code. Even programs such as py2exe don't really compile the python source code; the source code is simply added as a resource to the executable, and it is therefore easily extracted and modified.

The Ubuntu installer is one big one...

In the "real world", software is mostly open source, and the few proprietary closed source apps are the odd ones. Also, most programmers don't write shrink wrapped software, as it is mostly for in house use.

As for what toolkits to use, my wiki has information on that.

---

### Post by dje on 2008-06-11
personally i'd use pygtk, i'm finding it pretty easy to learn

---

### Post by ankursethi on 2008-06-11
> First of all, you probably won't see many "real-world" GUI applications using python.
An increasing number of GNOME apps are in Python. Exaile, Scribes, Deluge, the Ubuntu installer etc. use Python. Many configuration tools are written in Python.

I'd still say Tk for small, one-off stuff and PyGTK for "real world" applications.

---

### Post by kakyoism on 2008-06-11
Thanks Guys.

Wonder why wxPython is not the most recommended one?
From a link in this thread,....Looks like wxWidgets got a very
high mark in comparison with the others...

Also, if companies like closed-source, is it a good idea that I learn the C++ version of anything you recommend as well? I have quite a few years of C++ experience but only with MFC.

---

### Post by LaRoza on 2008-06-11
> **kakyoism said:**
> 
Wonder why wxPython is not the most recommended one?
From a link in this thread,....Looks like wxWidgets got a very
high mark in comparison with the others...

Because it is a random dispursement of random people on the internet.

> 
Also, if companies like closed-source, is it a good idea that I learn the C++ version of anything you recommend as well? I have quite a few years of C++ experience but only with MFC.

Companies don't like closed source in general. Companies that sell software might, but most companies that hire developers don't sell the software.

Learn anything you want, your brain won't explode (probably) and you can always learn more and forget things you don't need.

---

### Post by irrdev on 2008-06-12
> Wonder why wxPython is not the most recommended one?
From a link in this thread,....Looks like wxWidgets got a very
high mark in comparison with the others...
wxPython probably is the most-used of all python gui toolkits. It is also more complicated and, depending upon your needs, possibly overkill. If you are specifically serving Linux, and more specifically Gnome users, then pyGtk is a fine choice. Otherwise, I would definitely go with wxPthon.

> Also, if companies like closed-source, is it a good idea that I learn the C++ version of anything you recommend as well? I have quite a few years of C++ experience but only with MFC.
Let me put it this way: once you master C++, almost any other programming language will come easily (the exception is ASM!). Java, C#, D, even Visual Basic .NET, all have C++ idioms, keywords, and other similarities. Python in the end remains a scripting language, albeit a powerful one. A good knowledge of C++ is generally invaluable, and will serve you well with other programming languages even if you rarely use C++ itself. I am not suggesting that you only learn C++; far from it. So many other languages are simply offshoots of C++, however, that knowing it will greatly help you eventually learn all of the others. ;)

Edit: Another good thing about learning C++ is that it makes you very aware of good programming practices. The GNU compilers in particular truly enforce the C++ standard, with the result that sloppy practices are usually uncovered. With time good programming semantics became a habit, and your program is accordingly optimized and hopefully more bug-free.

---

### Post by LaRoza on 2008-06-12
> **irrdev said:**
> Python in the end remains a scripting language, albeit a powerful one. 

That, in the end, doesn't mean anything.

The use of Python can be seemless with C. The use of Python doesn't have clear lines. One can use C for the real work, Python for the the rest, and Tcl for the GUI.

It is a big mistake to say "just a scripting language" as if that means anything. C is just a high level language (when compared to asm). Java is just a byte code language (so is Python and Perl by the way, they are compiled to byte code before being executed)

---

### Post by irrdev on 2008-06-12
**@LaRoza:** When referring to Python as a scripting language (which it is), I am referring to more than just the Python *platform*. Scripting languages as a rule offer some different features than compiled languages, and even a bypte code language such as Java. For example, scripting langues are usually intended or optimized for specific purposes. There are math scripting languages, game scripting languages, network scripting languages, etc. Even Python has noticably strong built-in support for string/data manipualtion. Sure, some of these features are supported through libaries, but these libraries are nevertheless included with the Python runtime. IMO, Python is still better compared to Ruby, TCL/TK, Perl and even Bash than to compiled languages such as C++.

---

### Post by pmasiar on 2008-06-12
Thanks for informed info comparing Py GUI toolkits. But...
> **irrdev said:**
> Let me put it this way: once you master C++, almost any other programming language will come easily (the exception is ASM!). Java, C#, D, even Visual Basic .NET, all have C++ idioms, keywords, and other similarities.

Python, or any procedural/OOP language from ALGOL family can take this pace as well, and will not help mastering languages from other families, like lisp, Prolog, Forth, Haskel, etc. You are just saying that C++ all those languages belong to same family, and learning one greatly helps learnig **syntax** of any other (while completely ignoring libraries!).

And suggesting C++, arguably one of the hardest of them, is a disservice, especially for someone who already started with the easiest to learn - Python.

> Python in the end remains a scripting language, albeit a powerful one.

You suggest that "scripting" languages are somewhat inferior to "real" languages. Well, let me say that C++ is like Python, only it forces programmer to: (1) manage memory manually (which is known to be error-prone - one of the most often security problem) instead of automatic garbage collection, (2) manually control all type information, (3) lacking embedded flexible data structures and generic functions.

How lack of those (IMHO fundamental for most people except selected few writing system applications requiring CPU speed) features makes C++ more "real"?

> A good knowledge of C++ is generally invaluable

To whom? I work with many biologists statisticians, they prefer Perl and Python to any compiled language (if they are able to program at all).



> and will serve you well with other programming languages even if you rarely use C++ itself. I am not suggesting that you only learn C++; far from it. So many other languages are simply offshoots of C++, however, that knowing it will greatly help you eventually learn all of the others. ;)

When OP learns Python, chances are that will not need any other language. And if new language will be needed, Python is as good entrance as C++ (except of annoying type info in statically typed languages, of course).

> your program is accordingly optimized and hopefully more bug-free.

You seems to be another mystic who believes that compiler magically can remove bugs. Only very small class of bugs can be checked that way, and testing (unittest and friends) are generally considered the only reliable way to keep bugs under control.

> Sure, some of these features are supported through libaries, but these libraries are nevertheless included with the Python runtime.

IIRC libraries are loaded by request from disk, they are not included in runtime all the time, as your comment suggests.

As I see Python, it is definitely specialized: for rapid problem-solving :-) where computer handles all those nasty details slowing programmer in other languages: types, typecasting, memory, etc. Python is often called "executable pseudocode" :-)

---

### Post by LaRoza on 2008-06-12
> **irrdev said:**
> **@LaRoza:** When referring to Python as a scripting language (which it is), I am referring to more than just the Python *platform*. Scripting languages as a rule offer some different features than compiled languages, and even a bypte code language such as Java. For example, scripting langues are usually intended or optimized for specific purposes. There are math scripting languages, game scripting languages, network scripting languages, etc. Even Python has noticably strong built-in support for string/data manipualtion. Sure, some of these features are supported through libaries, but these libraries are nevertheless included with the Python runtime. IMO, Python is still better compared to Ruby, TCL/TK, Perl and even Bash than to compiled languages such as C++.

C is also a scripting language, you can use C interpreters (tcc is the one I use).

Python is compiled to byte code, like Java. Python has the ability to have embedded C, C data types, and other lower level features when needed.

---

### Post by KingTermite on 2008-06-12
> **LaRoza said:**
> Companies don't like closed source in general. Companies that sell software might, but most companies that hire developers don't sell the software.
This is not true in my experience. I work for a large (Fortune 100) company, more or less a tech company (albeit many different technologies). I have also had the opportunity to deal somewhat closely with many other big companies.

For the most part, these big companies don't like open-source because they fear no "real" support. I'm not arguing they are right (I think they are dead wrong), but they are happier to spend bigger bucks on proprietary software from companies because they expect a certain level of support.

Thankfully, I am starting to see that mindset change slightly, but only slightly. I know of a few small pockets where some programs are using Linux and subversion, but only a few. I was just given the task of setting up and piloting subversion for the project I work on.

But for the most part, companies (at least the 'big' ones) prefer proprietary software because they perceive a higher level of tech  support.


That is for software used. For software developed, the companies also prefer closed-source because they consider everything (and I mean "everything") Intellectual Property. We would almost never use a scripting language ("almost", but not "never") because the company tries to protect is "IP" by not giving source code to the customer, only binaries.

---

### Post by LaRoza on 2008-06-12
> **KingTermite said:**
> This is not true in my experience. I work for a large (Fortune 100) company, more or less a tech company (albeit many different technologies). I have also had the opportunity to deal somewhat closely with many other big companies.

For the most part, these big companies don't like open-source because they fear no "real" support. I'm not arguing they are right (I think they are dead wrong), but they are happier to spend bigger bucks on proprietary software from companies because they expect a certain level of support.

I didn't mean it that way. I meant that companies don't care if the source of the software their employees write is viewable. It isn't in the interest to do that for internally used software, which is the majority of programming being done.

The use of opensource software is high in companies. Red Hat is very common and open source and paid support is available. (Ubuntu has that also, but is less commonly used in that area) SUSE is also another common distro with paid support and is open source.

---

### Post by KingTermite on 2008-06-12
> **LaRoza said:**
> I didn't mean it that way. I meant that companies don't care if the source of the software their employees write is viewable. It isn't in the interest to do that for internally used software, which is the majority of programming being done.

The use of opensource software is high in companies. Red Hat is very common and open source and paid support is available. (Ubuntu has that also, but is less commonly used in that area) SUSE is also another common distro with paid support and is open source.

see bottom paragraph

---

### Post by KingTermite on 2008-06-12
Let me also clarify that the closed-source due to "IP" model is the trend. I think it "used to be" more open source code previous, the whole "IP" kick is something that has started in the last 5-10 years.

I remember my manager fighting hard with some customers in the early days 7-8 years ago about not giving them the source code. It took a while for it to be the "standard practice", but now when those companies create things that we receive, we don't usually get source code any more either.

---

### Post by LaRoza on 2008-06-12
> **KingTermite said:**
> Let me also clarify that the closed-source due to "IP" model is the trend. I think it "used to be" more open source code previous, the whole "IP" kick is something that has started in the last 5-10 years.

I remember my manager fighting hard with some customers in the early days 7-8 years ago about not giving them the source code. It took a while for it to be the "standard practice", but now when those companies create things that we receive, we don't usually get source code any more either.

Forgive my confusion, but what is "IP"? It isn't the protocol is it?

---

### Post by KingTermite on 2008-06-12
> **LaRoza said:**
> Forgive my confusion, but what is "IP"? It isn't the protocol is it?

No....I defined it in the last paragraph of the previous post.

IP = Intellectual Property

IP is the buzzword passed around constantly with companies as to why they protect their source code. Our company even started nagging us to try to develop some software patents if we had any good ideas, though I haven't heard much push since the initial one 2 years ago.

---

### Post by LaRoza on 2008-06-12
> **KingTermite said:**
> No....I defined it in the last paragraph of the previous post.

IP = Intellectual Property


I see. 

You didn't define it. You use the phrase, then a sentence later the abbreviation, but IP has a real meaning and that would be confusing to someone familiar with that meaning.

Changing the meaning of an abbreviation, especially in this area, should be a bit more explicit.

---

### Post by KingTermite on 2008-06-12
> **LaRoza said:**
> I see. 

You didn't define it. You use the phrase, then a sentence later the abbreviation, but IP has a real meaning and that would be confusing to someone familiar with that meaning.

Changing the meaning of an abbreviation, especially in this area, should be a bit more explicit.

I figured it was mentioned obvious enough to understand, but I see maybe not.

Anyway, I agree that its an ambiguous term to use in the software field, but don't shoot the messenger. I didn't make it up....only got slammed with it at work.

Anyway, it was part of the point I was making about companies going more closed-source than open-source. I'm not agreeing with it, just pointing out that its the trend.

One reason, as it was directly explained to us, is that if we have software patents that others may want and they have some technology we want, its good to use them as trade. They wanted us to create many patents so we had more "bargaining power" to get other software technologies free if we wanted.

It's sad, but in my view the big companies are still turning a pretty blind eye to the open-source model.

---

### Post by ByteJuggler on 2008-06-12
> **KingTermite said:**
> I figured it was mentioned obvious enough to understand, but I see maybe not.

Anyway, I agree that its an ambiguous term to use in the software field, but don't shoot the messenger. I didn't make it up....only got slammed with it at work.

Anyway, it was part of the point I was making about companies going more closed-source than open-source. I'm not agreeing with it, just pointing out that its the trend.

One reason, as it was directly explained to us, is that if we have software patents that others may want and they have some technology we want, its good to use them as trade. They wanted us to create many patents so we had more "bargaining power" to get other software technologies free if we wanted.

It's sad, but in my view the big companies are still turning a pretty blind eye to the open-source model.

Well, some companies yes, others, not so much.  [This,]("http://www.groklaw.net/article.php?story=20080611191302741") for example is very good news, and counter to the propriatary trend.  Personally I'm just glad we don't have software patents where I live.  (Unfortunately, not sure how long that will last, lots of pressure from the US on tha t front... :( :( )   I don't think they should exist, and certainly not when primarily used as anti-competitive weapons like is the case in the US presently.

Anyway, this is getting *waaay* off topic so I'll shut up now.

---

### Post by pmasiar on 2008-06-12
> **LaRoza said:**
> Forgive my confusion, but what is "IP"? It isn't the protocol is it?

IP is buzzword created by corporate lawyers (with no clue in informatic technology at all - you can see it from the selected abbreviation) to confuse consumers. It mixes together in one term patent law, contract law, and copyright law (completely different by approach, methods, usage, protection offered etc). It is like biologist have term covering animals, plants, fungi: Eucaryots. They different enough, but they like to cover them in one term.

RMS has good essay explaining why using term IP (designed to confuse us) helps to promote the confusion.

---

### Post by bapoumba on 2008-06-18
> **pmasiar said:**
> ... It is like biologist have term covering animals, plants, fungi: Eucaryots. They different enough, but they like to cover them in one term...
Late OT: it's not about likings :)
Eucaryotes have a linear DNA that is inside a particular cell structure, the cell nucleus. Procayotes have circular DNA and no nucleus. So the way you can have offsprings is different from the bacteria's, but not that different from the fungi's (at least at the cell level :þ).

Eucaryote means real, true nucleus (translated from French).

---

### Post by LaRoza on 2008-06-18
> **bapoumba said:**
> Late OT: it's not about likings :)
Eucaryotes have a linear DNA that is inside a particular cell structure, the cell nucleus. Procayotes have circular DNA and no nucleus. So the way you can have offsprings is different from the bacteria's, but not that different from the fungi's (at least at the cell level :þ).

Eucaryote means real, true nucleus (translated from French).

Biology teachers...

Prokaryotes: Nations that have agreed to not use nuclear weapons.

---

### Post by bapoumba on 2008-06-18
> **LaRoza said:**
> Biology teachers...

Prokaryotes: Nations that have agreed to not use nuclear weapons.
Eheheh :)

---

