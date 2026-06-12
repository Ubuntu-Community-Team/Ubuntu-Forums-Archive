---
title: "cross-platform application to make window apps &amp; contribute to Open Source Projects?"
date: 2008-03-21
forum: Programming Talk
---

### Post by bgryderclock on 2008-03-21
I have been using Linux exclusively at home for the last 3 years.

I have no real programming training but I have managed to become the 2nd strongest programmer in my giant healthcare company's patient accounting branch with 2 community college VB classes and art of crudely copy/pasting together code from online tutorials. 

**I want to write code with an open source application.**

It would be great if it were:
-cross-platform so I am able to run it at work
-able to create windows executable.
-able to create code to contribute back to simple open source projects like [GTick]("http://www.antcom.de/gtick/").

What application should I look into? Any suggestion or links to posts/articles would be great!

---

### Post by stevescripts on 2008-03-21
Lots of tools available for cross-platform programming.

In order of *my* preference, ;)  Tcl, Python, Ruby. They all have various widget
sets available for use, on Linux and windows.
(Python has much of the mind share here, and if I had started with it,
it would probably have mine too)

Concerning easy cross-platform deployment - I use starpacks (this is gonna be
a new term on a lotta folks around here...)

Not a shameless self-plug - but there are links on my website [http://www.stevescripts.com](http://www.stevescripts.com)   
... click on the Starpack link on the left

Steve

---

### Post by bgryderclock on 2008-03-21
> **stevescripts said:**
> Lots of tools available for cross-platform programming.

In order of *my* preference, ;)  Tcl, Python, Ruby. They all have various widget
sets available for use, on Linux and windows.
(Python has much of the mind share here, and if I had started with it,
it would probably have mine too)

Concerning easy cross-platform deployment - I use starpacks (this is gonna be
a new term on a lotta folks around here...)

Not a shameless self-plug - but there are links on my website [http://www.stevescripts.com](http://www.stevescripts.com)   
... click on the Starpack link on the left

Steve

Thank you for the quick reply. i like your site :)

Is there an  application you use to code in Tcl, Python, or Ruby that will allow you to drag a button on to a form and click the new button to write code for it?

---

### Post by LaRoza on 2008-03-21
> **bgryderclock said:**
> Thank you for the quick reply. i like your site :)

Is there an  application you use to code in Tcl, Python, or Ruby that will allow you to drag a button on to a form and click the new button to write code for it?

Pull back a second. Don't jump into using RAD tools immediately. You will have to learn to program first. From what you posted, you don't do much programming.

"2 community college VB classes and art of crudely copy/pasting together code from online tutorials."

No offense, but that reminds me of: [http://hackles.org/cgi-bin/archives.pl?request=37](http://hackles.org/cgi-bin/archives.pl?request=37)

For Tcl, Python, and Ruby (all good languages) are very high level and you don't need to compile them. They will work on Windows, Linux and Macs usually with no changes.

See my wiki, the sticky, pmasiars wiki, and stevescripts's site.

After learning how to program, you can use Glade (or a bunch of others) to quickly make GUI's.

It is my opinion that VisualStudio and its RAD tools are for advanced programmers. Unfortunately, it is used as an introduction, and cripples the users.

---

### Post by stevescripts on 2008-03-21
> **bgryderclock said:**
> Thank you for the quick reply. i like your site :)

Is there an  application you use to code in Tcl, Python, or Ruby that will allow you to drag a button on to a form and click the new button to write code for it?

Thanks for the kind words.

For GUIs, I use Tk (in the case of Python, called Tkinter)...

As LaRoza said, don't jump the gun too fast.  VB is a windows only
sort of thing.  Try to get a fair grasp on the basics before you venture too far into the world of GUIs.

All the links furnished by LaRoza are well worth some time to investigate.

That said, just a quickie taste of a GUI:
```

#! /usr/bin/wish

pack [button .b -text "Hello World!" -command {exit}]

```

Paste it into a text editor (like gedit) and save it, as hw.tcl .
From the command line (in the directory where you saved the
script):
```

steveo@linux:~/Desktop> chmod +x hw.tcl
steveo@linux:~/Desktop> ./hw.tcl

```

And you have a one-liner GUI program. Wish is the Tk widget set for tcl.  

As far as what tool do I use to write my programs, mostly
gedit .  Lots of IDEs available, but again, you will learn more,
faster by avoiding those at the beginning.

Steve

EDIT:  I forgot to mention, that all of these languages (as well as others I did not mention) can be used from and interactive shell,
which is a great tool for learning, and breaks the bonds from the code, save, compile, run cycle.

---

### Post by pmasiar on 2008-03-21
You confused GUI building with programming. Hardly anything in common... :-(

Python is very cross-platform, and if you need executables, you can create one (for Windows; Mac nad Linux has Python). Another way to create flexible cross-platform apps is make web-based apps (much simpler to deploy).

As you know by now, VB is very non-cross-platform :-)

See wiki in my sig for links for Python beginners. See also sticky FAQ - it will answer many of questions you did not asked yet :-)

---

### Post by Fbot1 on 2008-03-21
For cross-platform gui apps I like Lazarus. You can develop independently of a widget toolkit and compile it.

---

### Post by LaRoza on 2008-03-21
> **Fbot1 said:**
> For cross-platform gui apps I like Lazarus. You can develop independently of a widget toolkit and compile it.

That uses Free Pascal right?

---

### Post by Fbot1 on 2008-03-21
> **LaRoza said:**
> That uses Free Pascal right?

yes

---

### Post by LaRoza on 2008-03-21
> **Fbot1 said:**
> yes

Do you have any recommend resources for that language? Might want to add it to my wiki and learn a bit of it.

(It would help the OP also, as you gave a recommendation, but no resources unlike the other posters)

---

### Post by WW on 2008-03-21
> **LaRoza said:**
> Do you have any recommend resources for that language? Might want to add it to my wiki and learn a bit of it.

(It would help the OP also, as you gave a recommendation, but no resources unlike the other posters)


Second hit on google for "lazarus" gets you [http://www.lazarus.freepascal.org](http://www.lazarus.freepascal.org)

---

### Post by Fbot1 on 2008-03-21
> **LaRoza said:**
> Do you have any recommend resources for that language? Might want to add it to my wiki and learn a bit of it.

(It would help the OP also, as you gave a recommendation, but no resources unlike the other posters)

To start out this one is good:
[INDENT][http://www.taoyue.com/tutorials/pascal/index.html](http://www.taoyue.com/tutorials/pascal/index.html)[/INDENT]
They also keep some okay documentation.
[INDENT][http://wiki.freepascal.org/Lazarus_Documentation](http://wiki.freepascal.org/Lazarus_Documentation)[/INDENT]

---

### Post by bgryderclock on 2008-03-21
> **LaRoza said:**
> 

No offense, but that reminds me of: [http://hackles.org/cgi-bin/archives.pl?request=37](http://hackles.org/cgi-bin/archives.pl?request=37)


ha! :)

I'd say Art!

```

Function GetPaid()

	If  <paste hack hack paste >  then 
		<paste hack hack paste >
	else 
		<paste hack hack paste >
	end if

End Function
```The projects i will be working on will probably be dealing with reading in text files or information from a SQL query from and creating  different worklist/reports. The end users of my application (sweet lttle ol' patient accounting ladies) like a pretty form. my last app had a gradient of a doctor holding a baby fading in to the background form(Gimp!). They ate it up! That why i am asking about the app forms.

stevescripts

Your hello world tutorial worked great how do you arrange the layout of the form in gedit? 

Starpack is very interesting, does it only work in the .tcl files?

---

### Post by stevescripts on 2008-03-21
> **bgryderclock said:**
> 
stevescripts

Your hello world tutorial worked great how do you arrange the layout of the form in gedit? 

Starpack is very interesting, does it only work in the .tcl files?

pack is one of the Tk geometry managers. (the others being grid and place)

Starpacks are a tcl/tk delivery system only.  Mainly developed by programmers in Europe and Australia. (I am fortunate in being able to count those folks as my friends)

Install == copy ,  uninstall = delete , cant get much simpler than that.

Possible to easily include (or build your own) tcl extensions.  Extensions can be written in tcl, C, or C++ for example.  
(JAVA is doable via jacl and/or tclblend)

Steve
EDIT:  I forgot to thank Fbot1 and WW for the interesting links to lazarus ... I haven't looked at Pascal in many years

---

### Post by pmasiar on 2008-03-22
> **stevescripts said:**
> I haven't looked at Pascal in many years

and for a good reason - learning Pascal now would be about 20 years too late :-)

---

### Post by Fbot1 on 2008-03-22
> **pmasiar said:**
> and for a good reason - learning Pascal now would be about 20 years too late :-)

It actually has a lot good features which I think have not been matched by more "modern" languages. I can definitely see why it was once so popular.

---

### Post by pmasiar on 2008-03-22
> **Fbot1 said:**
> It actually has a lot good features which I think have not been matched by more "modern" languages. I can definitely see why it was once so popular.

Example of such unmatched feature?

I understand fully why it was popular long ago, but today, there are nicer languages, IMHO.

---

### Post by Fbot1 on 2008-03-22
> **pmasiar said:**
> Example of such unmatched feature?

I understand fully why it was popular long ago, but today, there are nicer languages, IMHO.

It's a very straightforward language and it really exploits the syntax in such a neat way.

---

### Post by LaRoza on 2008-03-22
> **Fbot1 said:**
> It's a very straightforward language and it really exploits the syntax in such a neat way.

Uh-oh :-)

@OP Don't mind the follow conversation...

The Pascal Wikipedia article is good I think for getting an overview of Pascal: [http://en.wikipedia.org/wiki/Pascal_(programming_language](http://en.wikipedia.org/wiki/Pascal_(programming_language))

---

### Post by bgryderclock on 2008-03-22
i want to thank everyone for the posts!

I Think i have confused the development tool with the programming Language. it seems that many tools will work with multiple languages; like Kdevelop does Ruby and C++ and does mono develop does C# and .net; and eclipse does lava and .... well i guess just Java... I can learn the language to that is associated with the development tool that feels the most "familiar".

I am also looking to sell the idea of open source development tools to my boss like "check this out, it works a lot like our expensive visual studio package and it is free! i made this at home and it runs great on our windows systems. ..Thanks, i love you too sir" . 

Eclipse does that "displays a menu when you hit the period key" thing. i like that. I will probably look for a used book for eclipse online.

**pmasiar,** in a post you said "You confused GUI building with programming. Hardly anything in common.."

Do most programmer code the functions first and the draw the user interface later? 

For some reason, my peers frown upon python i believe they think it is a old irrelevant language, even though awesome apps like Gimp and Blender use it. 

If you are writing code with Ruby, C or Java that involves send information to Microsoft apps,  do the APIs work the same way as in VB?
like:

```
Dim xlExcel As New Excel.Application
Dim xlBooks As Excel.Workbooks
Dim xlBook As Excel.Workbook
Dim tblSheet As Excel.Worksheet
Dim xlCells As Excel.Range
Dim sFile As String
xlBooks = xlExcel.Workbooks
xlBook = xlBooks.Add
```

Thank you for your patiences!:KS

---

### Post by LaRoza on 2008-03-22
> **bgryderclock said:**
> 
Do most programmer code the functions first and the draw the user interface later? 

For some reason, my peers frown upon python i believe they think it is a old irrelevant language, even though awesome apps like Gimp and Blender use it. 

If you are writing code with Ruby, C or Java that involves send information to Microsoft apps,  do the APIs work the same way as in VB?
like:

Thank you for your patiences!:KS

In big projects, different people work on the GUI and backend. Usually, I like to write the backend first, and test them before making an interface. 

Python is very modern, perhaps they just use Blub. 

Python has access to Windows specific API's. In fact, IronPython is Python for .NET. 

If this is for work, I suggest you use tools you know how to use already and the work place is used to until you feel like you know enough to use other tools/languages.

If your work places is using Windows, it may be best to stick with VB.

---

### Post by pmasiar on 2008-03-22
> **Fbot1 said:**
> It's a very straightforward language and it really exploits the syntax in such a neat way.

This is not a feature. You again just trying hard to disagree? :-) Keep it up.

And of course Pascal cannot match Python, if this is what you wanted to say. :twisted:

---

### Post by pmasiar on 2008-03-22
> **bgryderclock said:**
> it seems that many tools will work with multiple languages;

exactly. And many developers prefer one universal powerful customizable editor like emacs or vim, which can handle all languages they use during the day, and don't be limited to features added/changed in current version of some IDE. Sticky FAQ has big discussion about IDEs, as you can imagine, every developer has at least one opinion about IDE, and many have more than that :-)

> I am also looking to sell the idea of open source development tools to my boss like "check this out, it works a lot like our expensive visual studio package and it is free! 

Sorry to breaking bad news to you, but easier than change language used in organization, is **to change organization you work for**. The bigger the shop, the more it resists any change. Because even if you changed languages, you **still** have that old code to maintain. You can try but it is very, very hard - you need to be considered expert to get your boss' ear. You need to know new language (learn it by yourself) and wait for a project where using it will be beneficial. Ie learn Python and wait for something you need to create test version quickly - or learn TurboGears and wait till you need web based app. And it still might not work because integrating MSFT with free software is often hard - MSFT designed it so.

> Eclipse does that "displays a menu when you hit the period key" thing. i like that. I will probably look for a used book for eclipse online.

Eclipse is written in Java so it is bloated, but has lots of docs online, and plugins for many tools and languages. I don't see reason using Eclipse unless big part of your workday you use Java. Learn editor which big boys use, like vim or emacs :-)  Did I mentioned that eclipse is bloated? And still does not have some simple features that slimmer editors have :-)

> Do most programmer code the functions first and the draw the user interface later? 

Most programmers don't program for GUI at all! :-) Many program web based apps, or utilities/libraries where commandline interface is fine and preferable.

> For some reason, my peers frown upon python i believe they think it is a old irrelevant language

It is because they don't have a clue - they are Blub programmers: [http://www.paulgraham.com/avg.html](http://www.paulgraham.com/avg.html)

Python is one of the most recent mainstream languages, Google, NASA, ILM, Canonical etc uses it extensively.

---

### Post by Fbot1 on 2008-03-22
> **pmasiar said:**
> This is not a feature.
Why not?

---

### Post by pmasiar on 2008-03-22
> **Fbot1 said:**
> Why not?

If being clear, simple syntax and  easy to read is a feature, Python has more of it than Pascal (because Python was build on all those old languages, including Pascal).

---

### Post by LaRoza on 2008-03-22
> **Fbot1 said:**
> Why not?

Don't put the burden of proof on others. You make a statement, you have the burden of supporting it. Your statement has not been accepted, and it is not logical to make other parties prove their points. This may be an interesting philosphical exercise, but for technical discussions, it is just frusterating for those that are willing to communicate.

Please do not try to temp others into making responses to unspoken arguments.

Resistance is futile.

---

### Post by pmasiar on 2008-03-22
> **Fbot1 said:**
> [Pascal] actually has a lot good features which I think have not been matched by more "modern" languages. 

Example of such a feature? Pascal lacks (and Python has): OOP, dynamic typing, garbage collection, list comprehension, functional programming (lambda, map), generators, iterators, flexible string output formatting, convenient libraries to access OS, etc etc. Can you name single feature in Pascal missing in any modern language?

---

### Post by hums07 on 2008-03-22
> **pmasiar said:**
> Example of such a feature? Pascal lacks (and Python has): OOP, dynamic typing, garbage collection, list comprehension, functional programming (lambda, map), generators, iterators, flexible string output formatting, convenient libraries to access OS, etc etc. 
I did make some programs using Pascal for univ projects and one "real" project. Turbo Pascal 7 has many of those features you mention. Later I used Delphi to do some projects.

Since the development of Delphi, Borland did not continue Pascal. So TP7 is stuck to what it was more than 15 years ago. It does not have commands/libraries to manipulate features of more recent technology, e.g. web, USB. Even Pascal only recognize 16 bit CPU registers. Not sure if Free Pascal has better feature than TP7

However, Delphi does have most, if not all, of those features. I see Lazarus with its free Pascal does too.

> **pmasiar said:**
> Can you name single feature in Pascal missing in any modern language?
Pascal is just another (old) programming language. Too old to compare with python, or C++, IMO.

EDIT: python lacks the keyword "begin ... end; " :)

---

### Post by pmasiar on 2008-03-22
Thanks hums07, but I was curious if Fbot1 knows about any such feature, or all his talk is just empty air, as usual. Now I need to wait next time...

IMHO, Delphi is to Pascal what is C++ to C.

BTW, you can use begin...end in Python, too, look: :-)

[php]
if x > 0: # begin
   print x
# end
[/php]

---

### Post by bgryderclock on 2008-03-22
> **pmasiar said:**
> exactly. And many developers prefer one universal powerful customizable editor like emacs or vim, which can handle all languages they use during the day, and don't be limited to features added/changed in current version of some IDE. Sticky FAQ has big discussion about IDEs, as you can imagine, every developer has at least one opinion about IDE, and many have more than that 

Can emacs or vim "displays a menu when you hit the period key" thing? What other editors have the "displays a menu when you hit the period key" thing? And what is the proper name of the displays a menu when you hit the period key" functionality?

>  Learn editor which big boys use, like vim or emacs :-)  Did I mentioned that eclipse is bloated? And still does not have some simple features that slimmer editors have :-) 

That is a little like the Big Boys changing their own oil in their driveways verses paying a mechanic 13 dollars to do it. In theory it's best to "Man-up" and DIY in raw text but I have to do in-house tech support and code at the same time at work so shortcuts are hard to pass up.  :)

 > Most programmers don't program for GUI at all! Many program web based apps, or utilities/libraries where commandline interface is fine and preferable. 

How do you code apps for non-savvy end users with no forms/GUI? My folks need big simple well labeled buttons and desktop shortcuts, many have their PC   resolutions set for 800x600. They need granny apps! :)

I bought these 2used books online to start my journey:

[IMG]http://ecx.images-amazon.com/images/I/51QV8MKC9ML._BO2,204,203,200_PIsitb-dp-500-arrow,TopRight,45,-64_OU01_AA240_SH20_.jpg[/IMG]

[IMG]http://ecx.images-amazon.com/images/I/41LqVSzCYnL._AA240_.jpg[/IMG]

Do you know of any free books (or giant PDF files) that might help me? :)

EDIT: this screencast was Really Helpful!: [http://nat.org/demos/gtksharp.html]("http://nat.org/demos/gtksharp.html")

---

### Post by Fbot1 on 2008-03-22
> **pmasiar said:**
> Thanks hums07, but I was curious if Fbot1 knows about any such feature, or all his talk is just empty air, as usual. Now I need to wait next time...

IMHO, Delphi is to Pascal what is C++ to C.

BTW, you can use begin...end in Python, too, look: :-)

[php]
if x > 0: # begin
   print x
# end
[/php]

The begin and end thing is not what I meant. It's structuring is a little neat. It really shows the positive sides of strictness but still is a little too strict. It's not a feature that's obvious but it's still a feature.

---

### Post by LaRoza on 2008-03-23
> **bgryderclock said:**
> 
How do you code apps for non-savvy end users with no forms/GUI? My folks need big simple well labeled buttons and desktop shortcuts, many have their PC   resolutions set for 800x600. They need granny apps! :)

I bought these 2used books online to start my journey:

Do you know of any free books (or giant PDF files) that might help me? :)

You can write GUI programs without using a GUI. The point here is that you should learn to program first.

---

### Post by bgryderclock on 2008-03-23
indeed. i look forward to receiving my books and learning more. 

i heard that open source programmers are paid more on average.
_[http://www.crn.com/it-channel/206900235]("http://www.crn.com/it-channel/206900235")_

Thanks to all for the replies.

---

