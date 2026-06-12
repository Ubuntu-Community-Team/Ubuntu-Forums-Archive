---
title: "ASP.NET to PHP Migration"
date: 2010-03-10
forum: Programming Talk
---

### Post by Mosabama on 2010-03-10
hi .. before I moved to GNU/linux I used to be ASP.NET (VB.NET) developer ... and now I took a look at php as an alternative and I found it really difficult compared to ASP. as there are no controls like date picker ... and the programming it self is alot harder .. at least to me ... 

is there any way I can find a PHP tutorial for ASP developers ? 
or do you have any suggestions to make PHP alittle easier by using some special IDEs ? and controls ?

Thanks .

---

### Post by Tibuda on 2010-03-10
Have you tried Mono implementation of ASP.NET?

EDIT: some reference: [http://www.mono-project.com/ASP.NET](http://www.mono-project.com/ASP.NET)

---

### Post by Mosabama on 2010-03-10
well .. to be honest I know about mono .. but at the same time I want better implimentation with mysql database.. and I dont think mono will be as good as ASP.NET and I may have problems with hosting ... so I prefer using linux native and well known for perfomance things like php and mysql. 

thanks for replying

---

### Post by Mosabama on 2010-03-10
also an IDE with auto complete function (intelisence) would be great

---

### Post by Tibuda on 2010-03-10
> **Mosabama said:**
> or do you have any suggestions to make PHP alittle easier by using some special IDEs ?

Well, PHP is more close to classic ASP than to ASP.NET, perhaps that's why you find it so much harder. I'd strongly recommend you to use a PHP framework like Symfony or CakePHP. It makes everything easier.

For IDE, try Aptana Studio, it is the most feature-rich IDE for web development.
[http://www.aptana.org/](http://www.aptana.org/)

---

### Post by Dragonbite on 2010-03-10
Wow.. I got beat on both regards!

I'm an ASP.NET (VB.NET) developer myself and my first thought was Mono's and Aptana Studio for PHP development.

There are a number of IDEs that may work (Eclipse, Zend, NetBeans, etc.) and just like ASP Classic, you can also do it in the text editor and gEdit does have PHP syntax coloring.

One of the things  to keep in mind is PHP (along with Javascript, C#, Qt, Java, etc.) are "C-based" languages, which means they'll be quite different than VB and VB.NET.  

I'm currently fooling around with Aptana Studio (stand-alone) on Linux, and a little C# in Visual Studio to try and become more familiar with the C-base languages.  I took a class in Javascript programming and finding that helping me in the C# side of things (not perfect, but helpful).

---

### Post by Mosabama on 2010-03-10
how about learning ruby on rails ? is it fast in development as asp.net ? does it provide nice controls as asp.net does ?

---

### Post by Tibuda on 2010-03-10
> **Mosabama said:**
> how about learning ruby on rails ? is it fast in development as asp.net ?
Ruby on Rails is my favorite to work with. The Ruby language is very simple IMO, and their ORM implementation (ActiveRecord) is amazing.

> does it provide nice controls as asp.net does ?
It provides some helper methods for some form controls. There are also community plugins out there for almost everything you can think.

---

### Post by samalex on 2010-03-10
ASP.Net is an entire framework while PHP is more the underlying code of the site.  As someone else mentioned PHP is more equal to older ASP (pre DotNet) where you could code the entire site in something as simple as Notepad.  Granted you can still code ASP.Net code by hand, but I wouldn't advise it :)

To get Date and Time Pickers and so forth, you generally have to branch out into the FOSS Community to find code to add this into a PHP website, and for me I find more flexibility doing this in PHP then trying to use what Microsoft has stock with ASP.Net.  

As for IDE's, everyone has their own preference, but I really like [NetBeans for PHP]("http://netbeans.org/features/php/").  It connects to your databases and can setup test and prod environments.  Pretty sweet for PHP coding!  Until I found this I did most of my coding by hand in HTML editors, but I've grown to love Netbeans as a PHP IDE.

But don't let PHP look too complicated... ASP.Net is IMO more crazy behind the scenes, it's just Microsoft has added a pretty good IDE (Visual Studio) to hold your hand along the way.  Again I find this more frustrating as you have less control of what's happening under the hood.  With PHP you are definitely in the drivers seat :)

Take care --  

Sam

---

### Post by Dragonbite on 2010-03-10
> **samalex said:**
>  As someone else mentioned PHP is more equal to older ASP (pre DotNet) where you could code the entire site in something as simple as Notepad.  Granted you can still code ASP.Net code by hand, but I wouldn't advise it :)

The other difference being you compile the ASP.NET, but PHP and ASP Classic are scripting languages and don't require compiling.

> **samalex said:**
> As for IDE's, everyone has their own preference, but I really like [NetBeans for PHP]("http://netbeans.org/features/php/").  It connects to your databases and can setup test and prod environments.  Pretty sweet for PHP coding!  Until I found this I did most of my coding by hand in HTML editors, but I've grown to love Netbeans as a PHP IDE.

Isn't NetBeans the closest thing to Visual Studio, though more focused on Java?

> **samalex said:**
> But don't let PHP look too complicated... ASP.Net is IMO more crazy behind the scenes, it's just Microsoft has added a pretty good IDE (Visual Studio) to hold your hand along the way.  Again I find this more frustrating as you have less control of what's happening under the hood.  With PHP you are definitely in the drivers seat :)

Everything's more flexible when you do it by hand!  I used to use FrontPage for ASP programming, but I didn't use any of FrontPage's extentions or features.  I set it up on the WYSIWYG side, then flip it around to the source code and hand-code everything else.  I used FrontPage extensions on ONE site and I'm still trying to rip out what it put in there!

---

### Post by samalex on 2010-03-10
> **Dragonbite said:**
> The other difference being you compile the ASP.NET, but PHP and ASP Classic are scripting languages and don't require compiling.

You're right, I forgot about that.  ASP.Net is Microsoft's attempt to bring full blown DotNet to a website, and though it ~works, it's VERY clunky.  If you use their IDE and play by their rules you can create a nice site, but try to tinker with any of the IDE-created code or use a non-IE browser and it's quite a frustrating ride.

I'd never recommend someone write a website in ASP.Net, but for internal business applications where you know 100% of your clients are using X operating system and Y Browser you're pretty safe.  But for the World Wild Web I think what it creates is too off base with the W3C standards unless you spend LOTS and LOTS of time testing.

> **Dragonbite said:**
> Isn't NetBeans the closest thing to Visual Studio, though more focused on Java?

NetBeans is a Java IDE, but they have a PHP Development environment available wrapped around NetBeans that's quite simply awesome.  I'll admit, as IDE's go, I've not seen anything better then Visual Studio, but as far as PHP goes NetBeans is the closest thing I've seen.

> **Dragonbite said:**
> Everything's more flexible when you do it by hand!  I used to use FrontPage for ASP programming, but I didn't use any of FrontPage's extentions or features.  I set it up on the WYSIWYG side, then flip it around to the source code and hand-code everything else.  I used FrontPage extensions on ONE site and I'm still trying to rip out what it put in there!

I agree completely.  I've never liked FrontPage or Dreamweaver, and in the earlier days of the web sites written in either almost always had problems.  I'd pretty much refuse to work on sites that were started in either of those applications... but that's just me I guess.  I've always been an old-school coder and preferred coding by hand. 

The way websites are setup I think it's too hard to have an IDE really build the site because there's just too many factors since you have no idea what browser the client will have.

Anyway, somehow I got onto a soapbox I guess, so I'll back away :)

Take care --

Sam

---

### Post by zekopeko on 2010-03-10
> **Dragonbite said:**
> The other difference being you compile the ASP.NET, but PHP and ASP Classic are scripting languages and don't require compiling.

Facebook is planning to open source their PHP-to-C++ compiler in the coming months.

---

### Post by jpeddicord on 2010-03-10
*Moved to Programming Talk*

---

### Post by phrostbyte on 2010-03-10
Mono does ASP.NET

Install [these packages]("apt://xps2,mono-devel,monodevelop").

---

### Post by Mosabama on 2010-03-10
OK .. I downloaded NetBeans IDE .. I have php5 installed already ... I installed symfony framework from inside the IDE, but when I create a php projects .. it displays an error message that says "No PHP interpreter selected .. " what to do ?

I can start a php project normally without symfony ... but it seems symfony with the interpreter helps alot ... I guess thats what I am looking for !! just for now until I find asolution for the controls such as date picker and stuff...

any solutions how to get this interpreter running ?

---

### Post by Tibuda on 2010-03-10
> **Mosabama said:**
> OK .. I downloaded NetBeans IDE .. I have php5 installed already ... I installed symfony framework from inside the IDE, but when I create a php projects .. it displays an error message that says "No PHP interpreter selected .. " what to do ?

I can start a php project normally without symfony ... but it seems symfony with the interpreter helps alot ... I guess thats what I am looking for !! just for now until I find asolution for the controls such as date picker and stuff...

any solutions how to get this interpreter running ?

Do you have [php5-cli](apt:php5-cli) package installed? I think this one is required to run PHP from script apps like Symfony does.

---

### Post by Mosabama on 2010-03-11
I installed php5-cli package .. but now in netbeans when want to make a new php project with symfony option it will say "No symfony script selected ... there is a place in the options to select the symfony script ... butI dont know what is this script !!!

---

### Post by Dragonbite on 2010-03-16
I take it Netbean's does not have a WYSIWYG designer for the PHP plugin, or does it?

---

