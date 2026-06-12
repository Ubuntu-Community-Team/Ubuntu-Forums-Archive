---
title: "Monodevelop + Database question"
date: 2007-12-10
forum: Programming Talk
---

### Post by clash on 2007-12-10
Hey all, decided to start writing an application which i see a need for for many people I know. 

Anyways, I don't want to do it on windows even though the majority of their machines are going to be windows. I've decided the best idea would be to do it in C# on Monodevelop to run on Linux and Windows. 

Actually this is more or a learning exercise for me than anything. 

Ok first obstacle. This is going to involve a database so whats the standard way database to use with monodevelop when I want to run it cross-platform on mono and .Net ?

---

### Post by Majorix on 2007-12-10
With mono, even if you compile the source code to a .exe, you will still need the end-users to have .NET framework installed. And since it is a rather love possibility they have it already installed on their comp (it is not like the JRE) you will have to include it with your program, which will make the size go upto like 30(?) MB's. And then they have to first install that framework, finally only then can they run your program. This is one of the main reasons I left C# (I had a well-paid job where I used C# 2.0) and went the Python + C++ way under Linux.

If you still want to develop C#, you could use MySQL queries in your program which can be run on both Linux and Windows. I have no real exp with MySQL though, therefore I can't tell how you can do that, but a quick google search for "MySQL query in C#" would reveal enough sources.

Good luck.

---

### Post by rufius on 2007-12-10
I seem to recall that you'd like to be looking into something called ADO.NET. I believe thats the standard .NET way of interfacing with databases.

As far as the rest goes. Depending on what .NET standard you're shooting for *most* machines should have .NET 2.x by now if its in a work environment. Home environment would be hit or miss.

---

### Post by Majorix on 2007-12-10
> **rufius said:**
> I seem to recall that you'd like to be looking into something called ADO.NET. I believe thats the standard .NET way of interfacing with databases.

ADO.NET is the nickname for the System.Data namespace used by a .NET program to interact with databases. Here is a tutorial I have read which will help you get most of your job done:
[http://www.csharp-station.com/Tutorials/AdoDotNet/Lesson01.aspx](http://www.csharp-station.com/Tutorials/AdoDotNet/Lesson01.aspx)

Be aware though, it focuses mainly on SQL Server 2005.

---

### Post by raylitalo on 2009-08-03
> **clash said:**
> Hey all, decided to start writing an application which i see a need for for many people I know. 

Anyways, I don't want to do it on windows even though the majority of their machines are going to be windows. I've decided the best idea would be to do it in C# on Monodevelop to run on Linux and Windows. 

Actually this is more or a learning exercise for me than anything. 

Ok first obstacle. This is going to involve a database so whats the standard way database to use with monodevelop when I want to run it cross-platform on mono and .Net ?

Clash,

I highly recommend MonoDevelop 2.0 and MySql 5.1 with the MySql/Connector .NET 5.1 (at this time, I haven't had luck using the later versions of MySql/Connector .NET in Linux.  I'm not sure, but I think it might have something to do with dependencies on newer Dot NET Framework Versions.)

I'm having great luck with these tools, and am of the opinion that these tools will continue to be developed and advanced--I think there is a wonderful future in this direction.

Good Luck!

Ross Ylitalo

---

### Post by directhex on 2009-08-03
[img]http://www2.apebox.org/wordpress/wp-content/gallery/00-single/htrb.jpg[/img]

---

### Post by Mirge on 2009-08-03
lol:KS

---

