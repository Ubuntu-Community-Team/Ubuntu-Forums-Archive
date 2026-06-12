---
title: "MIgration to Linux for a .NET programmer, possible?"
date: 2007-09-12
forum: Programming Talk
---

### Post by lordfkiller on 2007-09-12
I am new to Ubuntu, in fact this is my second day of use. But I really love it and I'd like to migrate from WIndows completely.
What is stopping me is that I am an MCP (Microsoft Certified Professional) for .NET development. I don't write code for Windows, rather I'm a Web developer.
Is there a way to write ASP.NET 2 and Microsoft AJAX applications is Linux? or I have to forget .NET or continue using Windows?

Thanks for any help.

---

### Post by justin whitaker on 2007-09-12
> **lordfkiller said:**
> I am new to Ubuntu, in fact this is my second day of use. But I really love it and I'd like to migrate from WIndows completely.
What is stopping me is that I am an MCP (Microsoft Certified Professional) for .NET development. I don't write code for Windows, rather I'm a Web developer.
Is there a way to write ASP.NET 2 and Microsoft AJAX applications is Linux? or I have to forget .NET or continue using Windows?

Thanks for any help.

Not directly: you can't install ASP.Net on an Ubuntu Box AFAIK. What you can do, is use MONO, which is a cross paltform implementation of .Net that seems to do really well at running .Net applications. 

[http://www.mono-project.com/Main_Page](http://www.mono-project.com/Main_Page)

---

### Post by lordfkiller on 2007-09-12
The MONO website says that it does not support ASP.NET AJAX and WebParts yet. Okay, I am currently working on an application that does not use either of them. Can I use the same files I currently have to continue my work in Linux? or I'll have to manipulate some code etc?
Is there an IDE that offers as many features as VS 2005 does?

Thanks.

---

### Post by justin whitaker on 2007-09-12
> **lordfkiller said:**
> The MONO website says that it does not support ASP.NET AJAX and WebParts yet. Okay, I am currently working on an application that does not use either of them. Can I use the same files I currently have to continue my work in Linux? or I'll have to manipulate some code etc?
Is there an IDE that offers as many features as VS 2005 does?

Thanks.

There is nothing that provides the same features as VS2005. Mono has a subproject called MonoDevelop which gives you most of the typical IDE functionality.

Here is an old article on running .Net stuff on Linux...from what I gather, there shouldn't be much of a problem running the files you currently have. 

[http://www.linux.com/articles/53582](http://www.linux.com/articles/53582)

---

### Post by sonofusion82 on 2007-09-12
Hey, I am also a C# .NET programmer and I have been using fully Linux for my home PC for more than 2 years.

About Mono, well, except for small simple apps, directly porting all the existing codes from Visual Studio to Mono will take alittle effort as Mono's class library is not as complete as M$'s. For GUI, their GTK# is probably better than System.Windows.Forms. 

I have tried Mono about 1 year ago when with openSUSE as it come with default installation but I would like to go more Linux way when I am writing little tools for my home PC. I personally like python, C++ and Qt4 because python is fun and Qt class library are quite complete, well design and easy to understand with pretty good documentation, I feel pretty at home just like msdn. okok, gtk ppl might argue against this ;-) 

Anyway, welcome to Linux, learning more of both sides give me a better view and learn from what's good and bad in Linux and Windows.

---

### Post by 23meg on 2007-09-12
I've moved this to Programming Talk, since it doesn't pertain to Gutsy development.

---

### Post by pmasiar on 2007-09-12
> **lordfkiller said:**
> I am new to Ubuntu, in fact this is my second day of use. But I really love it 

Welcome on board! You are getting the feeling why we love it! :-)

> and I'd like to migrate from WIndows completely.
What is stopping me is that I am an MCP (Microsoft Certified Professional) for .NET development. I don't write code for Windows, rather I'm a Web developer.
Is there a way to write ASP.NET 2 and Microsoft AJAX applications is Linux? or I have to forget .NET or continue using Windows?

Previous posters mentioned Mono. But you should understand that MSFT technologies are not "native" on Linux now, and not in near future. There are hacks, some people are in your situation and try to  make it work... it is open source and anybody can hack/improve anything after all. But most people do not care much about MSFT technology (maybe except Silverlight :-) ) and work full speed to enhance **competing** tools. Browse just titles of post for last week and you will see yourself. It is not that we hate MSFT technologies - but we don't care much, and don't believe that are the best what humanity can offer. :-)

One of possible way to get best of both worlds is maybe to use [http://en.wikipedia.org/wiki/IronPython](http://en.wikipedia.org/wiki/IronPython), which is open-source implementation (by MSFT, no less) of popular free software language, Python, tightly integrated with .NET. And it is widely used for web apps too. It is not super-stable yet, but getting there fast. Popular web frameworks are TurboGears and Django. Another option might be IronRuby.

---

### Post by emperon on 2007-09-12
> **pmasiar said:**
> Welcome on board! You are getting the feeling why we love it! :-)

> and I'd like to migrate from WIndows completely.
What is stopping me is that I am an MCP (Microsoft Certified Professional) for .NET development. I don't write code for Windows, rather I'm a Web developer.
Is there a way to write ASP.NET 2 and Microsoft AJAX applications is Linux? or I have to forget .NET or continue using Windows?

Previous posters mntioned Mono. But you should understand that MSFT technologies are not "native" on Linux now, and not in near future. There are hacks, some people are in your situation and try to  make it work... it is open source and anybody can hack/improve anything after all. But most people do not care much about MSFT technology (maybe except Silverlight :-) ) and work full speed to enhance **competing** tools. Browse just titles of post for last week and you will see yourself. It is not that we hate MSFT technologies - but we don't care much, and don't believe that are the best what humanity can offer. :-)

One of possible way to get best of both worlds is maybe to use [http://en.wikipedia.org/wiki/IronPython](http://en.wikipedia.org/wiki/IronPython), which is open-source implementation (by MSFT, no less) of popular free software language, Python, tightly integrated with .NET. And it is widely used for web apps too. It is not super-stable yet, but getting there fast. Popular web frameworks are TurboGears and Django. Another option might be IronRuby.

Your worries are pointless. You can absolutely use mono the same way you use .net.

Let's mention some facts:
ASP.NET 2.0 is 100% complete except web parts
ASP.NET AJAX AND ASP.NET AJAX Control toolkit are both 100% working with  
mono (latest svn)

Windows forms 1.0 is 100% complete
Windows forms 2.0 is mostly complete
C# 2.0 specification is 100% 
ADO.NET is 99%
C# 3.0 is 100% there except LINQ

You can directly use .net libraries written on windows 
for example : NUnit, NHibernate, Rhino Mocks, Log4net work seamlessly

I hope it helps.

---

### Post by skeeterbug on 2007-09-12
> **lordfkiller said:**
> I am new to Ubuntu, in fact this is my second day of use. But I really love it and I'd like to migrate from WIndows completely.
What is stopping me is that I am an MCP (Microsoft Certified Professional) for .NET development. I don't write code for Windows, rather I'm a Web developer.
Is there a way to write ASP.NET 2 and Microsoft AJAX applications is Linux? or I have to forget .NET or continue using Windows?

Thanks for any help.

Welcome!

I am a full time C# developer for my day job. My side job/hobby is working on my site guildreport.com (World of Warcraft related site). I wrote this using Python and the Django web framework. I think the alternatives that run natively on Linux are a more fun, and desirable way to go, IMHO. Besides, Python, Ruby, PHP, and Perl all run in both Linux and Windows, with no dirty hacks. The choice is ultimately yours, but I take any chance I can get to learn something new. Good luck in whatever you choose!

---

### Post by lordfkiller on 2007-09-12
Thank you all for your help! 
Ubuntu's support is really exceptional. I wonder why some people are still using Windows.

Of course I AM going to learn other programming languages like Python, PHP and so on and I won't be limiting myself to Microsoft. But, at the moment, I am in the middle of a Microsoft certification and have already passed some exams. Also, I have been writing code for .NET for 5 years now. And now that I see .NET is not limited to Windows anymore, why should I leave it in this stage?

But there remain a few questions for me, like: How is MONO created? Using open-source part of the .NET? Despite some .NET classes are not open-source, how do they create all of them? Can I use .NET DLLs created in Windows in Linux(MONO)? Will ASP.NET websites created in Linux run faster than/slower than/equal to Windows?

Thanks.

---

### Post by emperon on 2007-09-12
> **lordfkiller said:**
> Thank you all for your help! 
Ubuntu's support is really exceptional. I wonder why some people are still using Windows.

Of course I AM going to learn other programming languages like Python, PHP and so on and I won't be limiting myself to Microsoft. But, at the moment, I am in the middle of a Microsoft certification and have already passed some exams. Also, I have been writing code for .NET for 5 years now. And now that I see .NET is not limited to Windows anymore, why should I leave it in this stage?

But there remain a few questions for me, like: How is MONO created? Using open-source part of the .NET? Despite some .NET classes are not open-source, how do they create all of them? Can I use .NET DLLs created in Windows in Linux(MONO)? Will ASP.NET websites created in Linux run faster than/slower than/equal to Windows?

Thanks.

Mono project first started as an cross platform C# compiler. As you know C# does not belong to MS althought it is created by MS. C# is an ECMA standard language. So by using it you have no royality against MS.

Technically Mono was created by rewriting entire .net stack in a cross platform way. There is no open source part of .net. (Although you can reverse engineer it)

You can use .NET DLL's created in windows on linux with mono and vice versa without recompiling as long as your dll do not use Platform specific code (like p/invoke).

For the web site s well that depends. You usually run mono apache + mod_mono. On general Mono Runtime is slightly slower than .net (about 10% - 20%). But I am not aware of the difference in mod_mono and IIS.

In addition to that I am doing professional web applications with C#/Mono on linux along with NHibernate, my applications become both platform independent and database independent.

Finally the only patented parts of mono are Windows Forms,  ASP.NET and ADO.NET. As long as you don't use these components technically you are not locked in in MS tech.

---

### Post by lordfkiller on 2007-09-12
Sounds like I am not going to need Windows anymore :D

You said the runtime is slightly slower. I think it IS possible to use a Windows server (and Microsoft CLR) as production server, though MONO is used to create the application, isn't it?

---

### Post by Coyote21 on 2007-09-12
yes, it should work, since mono supports most (or even all the features of .NET), and the code is compiled to run in through the interpreter and the bytecode is freely available as an ECMA specification. So, yes it should work. (Note: MONO also exists as an Windows version, and with some configurations Visual Studio .NET can also use MONO in the backend)

---

### Post by lordfkiller on 2007-09-13
Oh I almost forgot! What about SQL Server? I can use another DBMS for development, but the server supports only Microsoft SQL Server 2005.

---

### Post by emperon on 2007-09-13
Mono Runs fine with SQL Server, MySQL and PostgreSQL

of course your code won't be database independant as usual.

IF you want your application to be database independent then you should consider using NHibernate framework

---

### Post by lordfkiller on 2007-09-13
I'm aware that MONO supports SQL Server(has the providers), but I don't think I can have a local SQL Server DB server on linux. Also, I don't want my application to be database independant, I need only SQL Server.

So, if there is a way to have a local SQL Server installed on Linux, then this is the best solution for me. If not, then if there is a BDMS I can use for development and later use SQL Server for production without any changes, it is okay. And finallty, if neither of them is possible, I'll have to use a remote SQL Server for development.

Thanks.

---

### Post by emperon on 2007-09-13
I don't think you can run MSSQL on linux. Nor I am aware any db using same engine.

You can install windows on virtualbox and then install mssql there. I know it's not neat but that's the only thing I can think of if you need mssql locally

---

### Post by lordfkiller on 2007-09-13
What is virtual box?

---

### Post by emperon on 2007-09-14
> **lordfkiller said:**
> What is virtual box?

It's a virtual machine that enables you to run any operating system on your linux. You can think of it like windows running within linux . For further details you may want to google it

---

### Post by pmasiar on 2007-09-14
[http://en.wikipedia.org/wiki/Virtual_machine](http://en.wikipedia.org/wiki/Virtual_machine)

---

