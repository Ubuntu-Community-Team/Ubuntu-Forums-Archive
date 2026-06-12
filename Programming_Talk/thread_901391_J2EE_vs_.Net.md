---
title: "J2EE vs .Net"
date: 2008-08-26
forum: Programming Talk
---

### Post by MaindotC on 2008-08-26
I'm learning about these two development environments and I was wondering what your thoughts are on the differences between the two, specifically from a standpoint of integration to existing environments and interoperability? For example, I thought .Net was proprietary to M$oft and can only run in their environments, whereas J2EE is proprietary but can be run on multiple platforms. What are some other comparisons/contrasts between the two? What do you favour?

Apologies in advance if you don't consider this the proper section of the forums.

---

### Post by themusicwave on 2008-08-26
Actually Java is becoming open source.  It is basically 99% Open Source, so it really isn't proprietary at all.

---

### Post by MaindotC on 2008-08-26
Thanks for the input.  Do you have any documentation to back up your claims?  Do you use either J2EE or .Net?

---

### Post by mrsteveman1 on 2008-08-26
The JVM and the class libraries are open source but i don't think all the enterprise stuff is.

---

### Post by themusicwave on 2008-08-26
I don't use J2EE much at all, the enterprise parts could still be closed.  I just know there is much talk of Sun open sourcing "Java".  What that includes I really don't know.  Sorry if I confused something.

---

### Post by pmasiar on 2008-08-26
You compare two platforms, ignoring the "free platform", so I am not sure what are your goals, what kind of project? Is it enterprisey programming? :-)

Also, I would question any enterprise taking risks with any platform without having access to source code and being able to fix it if needed, whatever the "it" is. Most likely you will not needed that ability, but if you need, it, you need it badly, and on your terms.

---

### Post by dracvs on 2008-08-26
I have been working on .Net for some time, and recently started Java development work as well.

I, in my humble opinion, Favour .net because of the simplicity and because it's easy for those who do not know it, be coding and programming in no time. may it be Visual basic or Pascal (the easiest route) or C# (not so easy). Also the .net framework basically integrates all you could ever wish for in one place. 

Now... java...

Java for me is like Clockwork. it has many little pieces that work towards a single goal.

making a single Webpage in Java has taken me roughly 10 times the time and effort of writing a simple Website in .net. It is complicated and is comprised of many many details in which, if one of those fails the whole application fail unexplicably.

in the end, both technologies are very powerful, and with the pass of time, the time used or invested developing a .net application has been rgeatly reduced thanks to the Visual Studio, and the express editions.  meanwhile in the Java side there is still a smallish gap in which there is no comprehensible IDE that offers the flexibility of visual Studio. Maybe Jbuilder 2008 Does it but I have yet to test it furthermore.

Eclipse is fine. but still is not as polished.

---

### Post by MaindotC on 2008-08-27
I'm not really working on any project - I have done a little bit of Java and some VB but just to get the fundamentals of how programming works.  I have to do a paper for this class on Interoperability and I was just curious on what others' perspectives were.  I've been getting some good feedback and things I would never have even thought of :)  Thanks for keeping them coming!

---

### Post by jespdj on 2008-08-27
> **strAlan said:**
> Thanks for the input.  Do you have any documentation to back up your claims?  Do you use either J2EE or .Net?
[Sun: Free and Open Source Java](http://www.sun.com/software/opensource/java/index.jsp)
[OpenJDK](http://openjdk.java.net/)

> **mrsteveman1 said:**
> The JVM and the class libraries are open source but i don't think all the enterprise stuff is.
Yes it is. Sun's implementation of Java EE is called [Glassfish](https://glassfish.dev.java.net/) and is open source. Ofcourse there are also other vendors that implement Java EE. Some of those implementations are open source (JBoss, for example), and some are not (Oracle Weblogic, IBM Websphere).

---

### Post by pmasiar on 2008-08-27
> **strAlan said:**
> I'm not really working on any project - I have done a little bit of Java and some VB but just to get the fundamentals of how programming works.  I have to do a paper for this class on Interoperability and I was just curious on what others' perspectives were. 

So IMHO you just **have to** consider Free software platform: LAMP, POSIX, gcc, whatever you call the GNU/Linux world, because it is completely independent and orthogonal to both Java and .NET, and becoming more and more important.

---

### Post by Tomosaur on 2008-08-27
> **dracvs said:**
> meanwhile in the Java side there is still a smallish gap in which there is no comprehensible IDE that offers the flexibility of visual Studio. Maybe Jbuilder 2008 Does it but I have yet to test it furthermore.

Eclipse is fine. but still is not as polished.

Netbeans? Netbeans provides pretty much the same experience for Java development as VS does for .Net development in my (somewhat limited, in terms of .Net) experience. Particularly the latest version of Netbeans is a much improved version than previous incarnations imo.

---

### Post by themusicwave on 2008-08-27
One thing to consider is what platforms the application can be hosted on.

A J2EE application can be hosted on Linux, BSD, Solaris, Unix, Windows....

A .Net application can really only be hosted on Windows.  You can use Mono to do it on Linux, but it is a bit of a hack and not totally supported.

I would say that right there makes Java win the interoperability war hands down.

I also know that to really host .Net properly you need to be running Windows Server 2008, which is another restriction and also gets expensive. The Web Server is called IIS [http://www.microsoft.com/WindowsServer2003/IIS/Default.mspx](http://www.microsoft.com/WindowsServer2003/IIS/Default.mspx)

---

### Post by skirby on 2008-08-27
>I also know that to really host .Net properly you need to be running Windows Server >2008, which is another restriction and also gets expensive.

This statement is subject to debate.  What do you mean by 'properly'?

---

### Post by themusicwave on 2008-08-27
> **skirby said:**
> >I also know that to really host .Net properly you need to be running Windows Server >2008, which is another restriction and also gets expensive.

This statement is subject to debate.  What do you mean by 'properly'?

By properly I mean, the only way it is intended to work.  It is not intended to work on non-Windows systems.

Also, if you run it on anything other than Windows Server, you are limited to only a few client connections.

So essentially if you don't run it on Windows Server 2008 you get a crippled .Net application.

Also, Mono is not officially supported.

---

### Post by dracvs on 2008-08-27
One thing you must keep in mind:

.net only works on microsoft operating systems for the time being. There is an implementation in linux, called Mono (that gnome uses) but its not as near great as The Framework itself

One annoyance i have found on java is, that one line they have "Write once, run everywhere" is actually not so true. Sometimes the same programs needs heavy modification from one platform to another.

to date, nobody has ever been to tell me why there are 4 versions of eclipse, instead of just one JVM program. 

You mentioned VB, That's one language I personally dislike. 

maybe its too cluttered i dont know.

---

### Post by jespdj on 2008-08-27
> **dracvs said:**
> One annoyance i have found on java is, that one line they have "Write once, run everywhere" is actually not so true. Sometimes the same programs needs heavy modification from one platform to another.
That only happens if you write your application in such a way that it's platform-specific. Java can't magically prevent you from doing that, ofcourse... In other words, if your program needs heavy modification to run on another platform, then that's your own fault.

---

### Post by skirby on 2008-08-27
Granted, IIS only runs on Windows.  But to say that it only runs on Windows 2008 is simply midleading.  IIS and DotNet runs on any Windows system greater than Windows 2000 SP1.  Which includes Windows 2000 SP1, XP, Vista, Windows 2003 Server.  Your link was for IIS6, the current version is IIS7, which is shipped with Vista and Windows 2008 Server.  Also, there is another product to run Windows apps on Linux, called DotGNU.  I do not know anything about this product, but is _supposed_ to be better than MONO, needs to be checked out.  Now if I could only get NetBeans to install and run on Kubuntu...

---

### Post by skeeterbug on 2008-08-27
> **skirby said:**
> Granted, IIS only runs on Windows.  But to say that it only runs on Windows 2008 is simply midleading.  IIS and DotNet runs on any Windows system greater than Windows 2000 SP1.  Which includes Windows 2000 SP1, XP, Vista, Windows 2003 Server.  Your link was for IIS6, the current version is IIS7, which is shipped with Vista and Windows 2008 Server.  Also, there is another product to run Windows apps on Linux, called DotGNU.  I do not know anything about this product, but is _supposed_ to be better than MONO, needs to be checked out.  Now if I could only get NetBeans to install and run on Kubuntu...

This ^

Also, at my last job the java guy had a really horrible time deploying an application on FreeBSD and had to switch it over to Linux instead (problem with Tomcat on FreeBSD if I recall). Maybe the problem is resolved now, I don't know.

---

### Post by themusicwave on 2008-08-27
What I said about IIS is trues for both 6 and 7.

On Vista, IIS has a limited number of concurrent connections.  It is only unlimited on Windows Server.  I didn't say it won't run on Vista or XP, I simply said it is crippled.

When we are comparing .Net to J2EE I am assuming we are talking about web applications, I don't think you would ever use J2EE for purely desktop applications.

The Limitations are:
>  Windows Vista Home Basic and Starter editions: 3
 Windows Vista Home Premium edition: 3
 Windows Vista Ultimate, Business, and Enterprise editions: 10 

Here is a source straight from MSDN that says this:
[http://msdn.microsoft.com/en-us/magazine/cc163453.aspx]("http://msdn.microsoft.com/en-us/magazine/cc163453.aspx")  Look at the part that talks about improved performance it says:

> While Windows Vista is a client operating system release and not intended for high-throughput production deployment (IIS on Windows Vista is limited to 10 concurrent requests at a time), it already showcases some of the major architectural improvements aimed at significantly increasing Web application performance. Coupled with the extensive performance work we are doing in the Windows Server "Longhorn" timeframe, these improvements will help IIS 7.0 elevate the performance of your server.

So there is the proof to backup my statements.  As I said, IIS is crippled on anything other than Windows Server.  Any production web application will have more than 10 concurrent users.

---

### Post by Ruhe on 2008-08-27
> **dracvs said:**
> 
One annoyance i have found on java is, that one line they have "Write once, run everywhere" is actually not so true. Sometimes the same programs needs heavy modification from one platform to another.


Tell us please about *heavy modifications*. What do you mean?

---

### Post by dracvs on 2008-08-27
> **Ruhe said:**
> Tell us please about *heavy modifications*. What do you mean?

There is one app here, called BankTrust. its used to connect the point of sale to a server. it uses a simple socket that receives an Hexadecimal number containing information of accounts and such and such.

it was written for the JVM 5. It worked on Windows. it was platform agnostic. it did not call any fundamental apis. Just normal java functions.

We tried to migrate it to Linux and BSD only to find it wouldnt even compile. We had to modify it almost to the point of basically re writing the core. Why? I still do not know.

Meanwhile There is another app called the TransactionalBank (this one, is a lot more complicated) and it was compiled the first time for a JVM 6 Runtime. For some reason this one app only need two or three tweaks to run in another platform.

Java is a weird specimen. Specially when it comes to J2EE.

Each platform has its Strenghts and Weaknesses. You could use one for one thing that the other wont just cut it. Sometimes, I like to think we developers a picky troublesome persons who get into heated over :

is
```
if condition then begin end
```

better than

```
if condition {}
```

are you more wussy for using the first? smarter for the second?  haha.. i wonder what would happen if someone actually went ahead and made a real one language all platforms

---

### Post by Tomosaur on 2008-08-27
> **dracvs said:**
> There is one app here, called BankTrust. its used to connect the point of sale to a server. it uses a simple socket that receives an Hexadecimal number containing information of accounts and such and such.

it was written for the JVM 5. It worked on Windows. it was platform agnostic. it did not call any fundamental apis. Just normal java functions.

We tried to migrate it to Linux and BSD only to find it wouldnt even compile. We had to modify it almost to the point of basically re writing the core. Why? I still do not know.

Meanwhile There is another app called the TransactionalBank (this one, is a lot more complicated) and it was compiled the first time for a JVM 6 Runtime. For some reason this one app only need two or three tweaks to run in another platform.

Java is a weird specimen. Specially when it comes to J2EE.

Each platform has its Strenghts and Weaknesses. You could use one for one thing that the other wont just cut it. Sometimes, I like to think we developers a picky troublesome persons who get into heated over :

is
```
if condition then begin end
```better than

```
if condition {}
```are you more wussy for using the first? smarter for the second?  haha.. i wonder what would happen if someone actually went ahead and made a real one language all platforms

If the JVM runs on a machine, then so long as the application does not contain any system-specific code, it should run fine. This leads me to believe that the applications which required re-writing must have contained some system-specific code. This is entirely possible - and indeed quite probable if the project is complex enough and was only ever really intended to run on one platform.

To implement a truly platform-independent program, you need to be aware that the program is intended to be platform independent, otherwise you are pretty likely to do something which stops you deploying on platform Y or Z. Indeed, the ability to develop platform independent programs is considered by many employers to be a skill / 'qualification' in itself, not just 'good design' which everybody should know how to do.

---

### Post by skirby on 2008-08-27
Yes, but you said *Windows 2008 Server*.  It runs on other Operating Systems other than Windows 2008 Server.

---

### Post by skirby on 2008-08-27
At my work, I am an Admin and Software Engineer for both Windows and Linux (Debian).  The problem with Linux development is the very thing everyone likes, the fact that the OS is Open Source.  Open Source is not a bad thing (in fact I think it is great!), but how do you support applications if the OS has been changed?

---

### Post by themusicwave on 2008-08-27
> **skirby said:**
> Yes, but you said *Windows 2008 Server*.  It runs on other Operating Systems other than Windows 2008 Server.

Ok you are right it RUNS on them, just not well.  Having 10 users isn't good for production.

I guess you can run it uncrippled on:

Windows Server 2008
Windows Server 2003
Probably other Windows Server versions

That still is not what I would call cross platform support.  Saying "It's cross platform because it runs crippled on Windows and uncrippled on Windows Server" doesn't cut it for me.

---

### Post by pmasiar on 2008-08-27
> **skirby said:**
> The problem with Linux development is the very thing everyone likes, the fact that the OS is Open Source.  Open Source is not a bad thing (in fact I think it is great!), but how do you support applications if the OS has been changed?

You use free community editions for production systems? You get what you paid for.

You can buy support (security updates) for RHEL for 7 years. My bet is, you will reinstall server, and possibly change your programs, after less than 7 years. I doubt that Windows provide you longer support, and more secure platform.

And Windows Service Pack can do nasty things to system (up to breaking), our ITS tests them almost as hard as new system, and warns against installing them off-the-bat on production systems. So I do not see how Windows is superior - in my experience, it is very much not. Or you just serving little FUD?

Ubuntu LTS has sec updates for IIRC 5 years - **for free**. If that is not enough, talk to Canonical.

There is no free lunch - you **always** get what you paid for, except with ubuntu, where you get **plenty** for free ;-)

---

### Post by skirby on 2008-08-27
I did not say that it is 'cross platform'.  Maybe someone else did.  But I think you got my point.  It really makes no sense to run a web server on a desktop platform, except for perhaps development work.  It's all a matter of perspective.  What you are calling 'crippled', others might call an opportunity to develop apps.  A lot of shops do not allow developers to develop on the production servers (I know we don't).  All of our web servers, both IIS and Apache2, run on servers.

---

### Post by skirby on 2008-08-27
> **pmasiar said:**
> You use free community editions for production systems? You get what you paid for.

You can buy support (security updates) for RHEL for 7 years. My bet is, you will reinstall server, and possibly change your programs, after less than 7 years. I doubt that Windows provide you longer support, and more secure platform.

And Windows Service Pack can do nasty things to system (up to breaking), our ITS tests them almost as hard as new system, and warns against installing them off-the-bat on production systems. So I do not see how Windows is superior - in my experience, it is very much not. Or you just serving little FUD?

Ubuntu LTS has sec updates for IIRC 5 years - **for free**. If that is not enough, talk to Canonical.

There is no free lunch - you **always** get what you paid for, except with ubuntu, where you get **plenty** for free ;-)
As a matter of fact, I am posting from a Kubuntu box.  I don't think anyone in their right mind would develop production apps with community editions.  What I am saying is: if I pay good money for a development IDE and develop a product.  This product gets distributed to some of my clients.  One day, a certain client decides to tweak his OS and it breaks my product.  He calls my help desk complaining that his product no longer works.  He may or may not know what broke his product.  Now, I am in the position of trying to help him get the product running on his 'tweaked' system.  I just think this would be a maintenance nightmare.  If the Open Source Community has figured this one out, I would certainly like to know.

---

### Post by howlingmadhowie on 2008-08-27
> **skirby said:**
> I did not say that it is 'cross platform'.  Maybe someone else did.  But I think you got my point.  It really makes no sense to run a web server on a desktop platform, except for perhaps development work.  It's all a matter of perspective.  What you are calling 'crippled', others might call an opportunity to develop apps.  A lot of shops do not allow developers to develop on the production servers (I know we don't).  All of our web servers, both IIS and Apache2, run on servers.

what is a server apart from a desktop computer without a monitor? the differences between apache on a gnu/linux distribution for desktop computers and a gnu/linux distribution for servers is minimal if at all existent. anybody who tells you stuff like 'server operating systems are fundamentally different from desktop operating systems' is lying to you. 

as it is, both .net and java are horribly buggy and slow. this is actually quite an achievement, seeing as the sun jvm (100% free software btw) is actually impressively fast. if you want to develop high load web applications which just work and are platform independent, you're really better off going the php/python/ajax or seaside route. i know what i'm talking about. i develop enterprise level web applications for a living and the php-projects just work and are completed on schedule. the java projects are always buggy nightmares.

---

### Post by howlingmadhowie on 2008-08-27
> **skirby said:**
> As a matter of fact, I am posting from a Kubuntu box.  I don't think anyone in their right mind would develop production apps with community editions.  What I am saying is: if I pay good money for a development IDE and develop a product.  This product gets distributed to some of my clients.  One day, a certain client decides to tweak his OS and it breaks my product.  He calls my help desk complaining that his product no longer works.  He may or may not know what broke his product.  Now, I am in the position of trying to help him get the product running on his 'tweaked' system.  I just think this would be a maintenance nightmare.  If the Open Source Community has figured this one out, I would certainly like to know.

yes, the 'open source community' as you call it has figured this one out. it's called writing software according to a language standard. you write your code to adhere to python2.5 connecting to mysql5.0, for example. if the client then decides in three years time to install python3 that's their problem. i fail to see how running a closed-source operating system on your development computer would help you here.

---

### Post by skirby on 2008-08-27
> **howlingmadhowie said:**
> yes, the 'open source community' as you call it has figured this one out. it's called writing software according to a language standard. you write your code to adhere to python2.5 connecting to mysql5.0, for example. if the client then decides in three years time to install python3 that's their problem. i fail to see how running a closed-source operating system on your development computer would help you here.
I'm not talking about changing the python install.  I'm talking about changing the the kernel, or some other piece that my product depends on.

---

### Post by skirby on 2008-08-27
> **howlingmadhowie said:**
> what is a server apart from a desktop computer without a monitor? the differences between apache on a gnu/linux distribution for desktop computers and a gnu/linux distribution for servers is minimal if at all existent. anybody who tells you stuff like 'server operating systems are fundamentally different from desktop operating systems' is lying to you. 

as it is, both .net and java are horribly buggy and slow. this is actually quite an achievement, seeing as the sun jvm (100% free software btw) is actually impressively fast. if you want to develop high load web applications which just work and are platform independent, you're really better off going the php/python/ajax or seaside route. i know what i'm talking about. i develop enterprise level web applications for a living and the php-projects just work and are completed on schedule. the java projects are always buggy nightmares.
you said:
what is a server apart from a desktop computer without a monitor? the differences between apache on a gnu/linux distribution for desktop computers and a gnu/linux distribution for servers is minimal if at all existent. anybody who tells you stuff like 'server operating systems are fundamentally different from desktop operating systems' is lying to you.

I give up, coming from the Windows world, servers and desktops are significantly different.  If Linux desktops and Linux servers are the same, someone should correct that.

---

### Post by pmasiar on 2008-08-27
> **skirby said:**
> if I pay good money for a development IDE and develop a product.  This product gets distributed to some of my clients.  One day, a certain client decides to tweak his OS and it breaks my product.  He calls my help desk complaining that his product no longer works.  He may or may not know what broke his product.  Now, I am in the position of trying to help him get the product running on his 'tweaked' system.

You realize that this is 100% off-topic discussion about managing expectations of customers' admins?

I still fail how Linux is different. Would you be happy if user installed some custom DLL on Windows, break something, and asked you to help? And how it is different?

So basically MSFT does not allow user to change anything and it is good, and Linux allows, it is bad (even if it might not break).

You obviously cannot accept any responsibility if user installs non-standard or third-party patches, and it is **exactly** the same in Windows or Linux. On Linux it is little easier to understand what you do, and having less chance to break something. On Windows is it is so complicated that hardly anyone tries, so it seems safer to someone with little clue what is really going on, like average journalist.

But if we want to continue this discussion, I think separate thread would be better. Wanna open it?

---

### Post by themusicwave on 2008-08-27
> **skirby said:**
> I did not say that it is 'cross platform'.  Maybe someone else did.  But I think you got my point.  It really makes no sense to run a web server on a desktop platform, except for perhaps development work.  It's all a matter of perspective.  What you are calling 'crippled', others might call an opportunity to develop apps.  A lot of shops do not allow developers to develop on the production servers (I know we don't).  All of our web servers, both IIS and Apache2, run on servers.

The reason I brought up the point is that the OP is interested in interoperability.  To me cross platform support is a big part of that, you can't interoperate with a platform that your code does not run on.

This is one area where Java, and Linux/Apache/Database/Scripting Language have .Net beat.  That's the point I was trying to make.  The Java Platform gives you more OS choices than the .Net Platform.

---

### Post by howlingmadhowie on 2008-08-28
> **skirby said:**
> I'm not talking about changing the python install.  I'm talking about changing the the kernel, or some other piece that my product depends on.

i'm sorry, are you really using the internal kernel abi in your userspace program? if you are, you should really rethink what you're doing. there are external abis for that, and they're static over time.

in other words, if your userspace program depends upon the version of the kernel installed, your programmers have really, really screwed up.

---

### Post by howlingmadhowie on 2008-08-28
> **skirby said:**
> 
I give up, coming from the Windows world, servers and desktops are significantly different.  If Linux desktops and Linux servers are the same, someone should correct that.

i agree. there's no reason apart from marketing why vista home basic should have a less capable kernel than windows server 2008. the linux kernel code can be compiled to run on [this]("http://www.picotux.com/") or [this]("http://domino.research.ibm.com/comm/research_projects.nsf/pages/bluegene.index.html"). just because microsoft chooses to add artificial limitations to the vista kernel when part of vista home basic compared with windows server 2008, doesn't mean that the kernel developers should also build artificial limitations into the linux kernel.

it would also be difficult for the kernel developers to do. adding a constant "__MAX_SIMULTANEOUS_NETWORK_CONNECTIONS" to the kernel sources would just allow everybody to set it themselves. in other words, the only thing stopping vista home basic having the same networking capabilities as windows server 2008 is the value of certain constants in the kernel sources before compilation.

---

### Post by slavik on 2008-08-28
> **skirby said:**
> As a matter of fact, I am posting from a Kubuntu box.  I don't think anyone in their right mind would develop production apps with community editions.  What I am saying is: if I pay good money for a development IDE and develop a product.  This product gets distributed to some of my clients.  One day, a certain client decides to tweak his OS and it breaks my product.  He calls my help desk complaining that his product no longer works.  He may or may not know what broke his product.  Now, I am in the position of trying to help him get the product running on his 'tweaked' system.  I just think this would be a maintenance nightmare.  If the Open Source Community has figured this one out, I would certainly like to know.

Umm, how does this not happen on non-OSS systems?

Case an point: Where I work, we support about 500 Win XP/Vista public access terminals with 20-30 academic apps (all of Adobe, MS Office, Wordperfect Office, SPSS, etc.). We use Symantec Ghost when we need to refresh all the systems (new software, new versions, updates, etc.). We also have to use Microsoft's sysprep when setting systems up so that the machines get picked up properly on WSUS and on the Sophos update server. The funny thing is that sysprep breaks Adobe Premier.

So, you have an OS which the user cannot change (as far as changing code) with the same OS vendor's tool and the application on this supported platform breaks ...

of course, this would be easy if all the user based config was stored in the user's $HOME (aka home directory, aka profile folder).

---

### Post by tinny on 2008-08-28
> **themusicwave said:**
> The reason I brought up the point is that the OP is interested in interoperability.  To me cross platform support is a big part of that, you can't interoperate with a platform that your code does not run on.


Interoperability in the enterprise world is solid (this threads about enterprise Java and .Net in enterprise, right?). It has nothing to do with running your code on whatever OS. Or has this thread lost the plot?

Homework:
[http://java.sun.com/developer/technicalArticles/glassfish/ProjectTango/](http://java.sun.com/developer/technicalArticles/glassfish/ProjectTango/)

<NoTopic>

I believe that EJB technology gives J2EE the advantage over .Net. How do you develop a distributed enterprise application in .Net? Its a real pain!!! You can use a combination of web services and .Net remoting, but this is just sooo much more work than just using EJBs. I understand the smart people at springsource have developed a version of Spring for .Net. So that is promising.

Also J2EE application servers are far superior to IIS. 

[http://java.sun.com/j2ee/1.3/docs/tutorial/doc/Overview4.html](http://java.sun.com/j2ee/1.3/docs/tutorial/doc/Overview4.html)

---

### Post by pmasiar on 2008-08-28
> **tinny said:**
> Interoperability in the enterprise world is solid (this threads about enterprise Java and .Net in enterprise, right?). It has nothing to do with running your code on whatever OS. 

Exactly. Ie Linux's samba can interoperate with Windows' SMB, it is not about running code on Windows. Running code on different platform is cross-platform support, which is quite different beast than interoperability. Only someone not involved in neither can mistake one for another :-)

> I believe that EJB technology gives J2EE the advantage over .Net.

IMHO experience and market niche shows in this distinction. Sun knew well how big systems work, and IBM (another huge supporter of Java) has decades of experience with enterprise systems. Compared to that, MSFT started as single-user desktop OS company, then added GUI, office apps - most of "bigger system" experience was not grown/learned inside but bought, like White Plains.

So I am not surprised when Enterprise capabilities of MSFT's software sucks, or if it is friendlier to noob user. MSFT always focused on different audience: 80% of beginners, 20% of experts be damned.

---

### Post by pmasiar on 2008-08-28
> **howlingmadhowie said:**
> i agree. there's no reason apart from marketing why vista home basic should have a less capable kernel than windows server 2008. [...] just because microsoft chooses to add artificial limitations to the vista kernel 

Those not just "artificial limitations" - they not only cripple the software, but make it more complex and bug prone, and inconvenience the users, just for one goal: make people to pay hundreds of dollars for something what other users (like in Thailand IIRC) can get for $4. It's not marketing, it's user abuse and greed.

---

### Post by dracvs on 2008-08-28
> **tinny said:**
> 

I believe that EJB technology gives J2EE the advantage over .Net. How do you develop a distributed enterprise application in .Net? Its a real pain!!! You can use a combination of web services and .Net remoting, but this is just sooo much more work than just using EJBs. I understand the smart people at springsource have developed a version of Spring for .Net. So that is promising.

Also J2EE application servers are far superior to IIS. 

I do believe that Either application has the same level of performance. No matter the OS, The Objective, processor, it doesnt matter. its too fast to notice any real difference.

Last night I was intrigued by this  about that write once deploy everywhere. And I did A Small Test.

I wrote a class (In C# 3.0 in VS2008, Mono And In Java JDK 6 using eclipse 3.4, ran in Windows Vista 64, and Ubuntu Linux 8.4.1, Core 2 Duo 2.66 and 3 gigs of ram.) that emulated the generation of a bingo carton (well...... 1000 cartons...)

What it did: it generates 24 Random number from 1 to 75, then it puts them in an array, Every number its then checked against each other on the carton, to avoid repeating a digit in each carton. then each carton is Checked against the others to assure there are no repeated cartons.

in java and in C# it doesnt take more than 1.5 seconds to generate 1000, 2 seconds to generate 2000, and five to generate 10 000

I had to play stopping and sleeping the threads in both programs, given they would basically spit 10 000 cartons in 0.56 Seconds or less.... Problem being it was only the last carton generated 10 000 Times. It finished the check extremely fast for it even to register. The performance was quite the same.

We are talking here about fractions of a second to a heavy process, Are we humans that picky that, we care about what we don't even get to notice?

Sure, a real world application that has an actual meaning this is useful to know, but in the end it all depends On perspective.

**Again, I think is a matter of coding preference AND IN MY HUMBLE OPINION:**

Java has Eclipse, JBuilder, Netbeans (Integrated IDes That are okay)

.net has Mono and visual studio (and to some degree Borland Developer tools, And Code gear Developer tools) Yet these IDES (VS and Rad 2007 And BDS 206) Have everything you could ever wish for, Debugging, virtual Servers and are easy to use. They are actual Rapid Development tools.

Sometimes Eclipse has some epic fails and instead of helping you out it slows you down.

Again Is a matter of opinion, I would take .net anyday over java given I would have the program ready in 1/4 of the time without so many bugs and a pretty interface.

---

### Post by themusicwave on 2008-08-28
> **pmasiar said:**
> Exactly. Ie Linux's samba can interoperate with Windows' SMB, it is not about running code on Windows. Running code on different platform is cross-platform support, which is quite different beast than interoperability. Only someone not involved in neither can mistake one for another :-)


I guess the problem there was my definition.  Honestly, I don't use J2EE much at all I mainly use J2SE.  I also use C# .Net a good bit.  Thanks for correcting my definition, while it is never fun to be wrong, it is always good to learn something.  I'm still pretty new at the whole corporate programming thing, so anything I can learn is good.

---

### Post by Reiger on 2008-08-28
> **howlingmadhowie said:**
> i agree. there's no reason apart from marketing why vista home basic should have a less capable kernel than windows server 2008. the linux kernel code can be compiled to run on [this]("http://www.picotux.com/") or [this]("http://domino.research.ibm.com/comm/research_projects.nsf/pages/bluegene.index.html"). just because microsoft chooses to add artificial limitations to the vista kernel when part of vista home basic compared with windows server 2008, doesn't mean that the kernel developers should also build artificial limitations into the linux kernel.

it would also be difficult for the kernel developers to do. adding a constant "__MAX_SIMULTANEOUS_NETWORK_CONNECTIONS" to the kernel sources would just allow everybody to set it themselves. in other words, the only thing stopping vista home basic having the same networking capabilities as windows server 2008 is the value of certain constants in the kernel sources before compilation.

There is a good use for artificial constraints with certain types of processes. For one thing a real server is supposed to have significantly more raw 'computing power' to its disposal than does the 'average' desktop or latop. It makes a good deal of sense to limit resource intensive operations such as I/O (incidentally the example you picked) to keep the workload down.

Of course, the fact that Windows is typically paid for makes it somewhat of a let-down to people with higher end systems; but that is not the market Microsoft actively caters for. Despite the prices they charge; these companies still aim at the average ignorant PC user (who likely doesn't have top of the line systems). A bit like the hard discount: more junkfood for less PC(-knowledge).

---

### Post by howlingmadhowie on 2008-08-28
> **Reiger said:**
> There is a good use for artificial constraints with certain types of processes. For one thing a real server is supposed to have significantly more raw 'computing power' to its disposal than does the 'average' desktop or latop. It makes a good deal of sense to limit resource intensive operations such as I/O (incidentally the example you picked) to keep the workload down.


so your saying changing some constants prior to compilation is worth 500$? basically microsoft is trying to propagate the myth that servers are fundamentally different from pcs or workstations or laptops or mobile phones or routers or whatever. they aren't. the same operating system kernel will run just great on all of them. look at the linux kernel--the kernel of choice for almost any computer if there isn't an extraneous reason for choosing a different one.

---

### Post by skeeterbug on 2008-08-28
> **tinny said:**
> 
I believe that EJB technology gives J2EE the advantage over .Net. How do you develop a distributed enterprise application in .Net? Its a real pain!!! You can use a combination of web services and .Net remoting, but this is just sooo much more work than just using EJBs. I understand the smart people at springsource have developed a version of Spring for .Net. So that is promising.

Also J2EE application servers are far superior to IIS. 

[http://java.sun.com/j2ee/1.3/docs/tutorial/doc/Overview4.html](http://java.sun.com/j2ee/1.3/docs/tutorial/doc/Overview4.html)

How exactly is remoting a pain?

```

public class UserManager : MarshalByRefObject

// UserManager code

```

Serve it up in IIS with only a web.config addition:
```

	<system.runtime.remoting>
		<application>
			<service>
				<wellknown mode="SingleCall" type="TestBLL.UserManager, TestBLL" objectUri="service.soap"/>
			</service>
      <channels>
        <channel ref="http"/>
        <serverProviders>
          <formatter ref="binary" />
        </serverProviders>
      </channels>
		</application>
	</system.runtime.remoting>

```


Calling it from a client:
```

//Register HTTP Channel
            HttpChannel chan = new HttpChannel();
            ChannelServices.RegisterChannel(chan, true);

            UserManager um = Activator.GetObject(typeof(UserManager), @"http://localhost:8080/WebSite/service.soap") as UserManager;
            string[] users = um.GetUsers();

```

You can also setup network load balancing if you want to scale it. Your entire business logic layer could be easily served up this way. It is also a speed improvement over web services if you are communicating from .NET <-> .NET applications.

---

### Post by Reiger on 2008-08-28
> **howlingmadhowie said:**
> so your saying changing some constants prior to compilation is worth 500$? basically microsoft is trying to propagate the myth that servers are fundamentally different from pcs or workstations or laptops or mobile phones or routers or whatever. they aren't. the same operating system kernel will run just great on all of them. look at the linux kernel--the kernel of choice for almost any computer if there isn't an extraneous reason for choosing a different one.

There is no myth there. In fact: there are only a few paradigms networking students are taught; and the first is that of 'Client-Server'. The close second is that of 'P2P'.

And you'll find that even Debian or Ubuntu do the same (note how you don't get Apache or similar webserver packages installed by default?); though they do not charge their consumers with a fee. I'm not saying it's worth $500 just for those constants (incidentally: do we *know* we're talking about constants and nothing else?); and I'd agree it be a better job if it was manually configurable and read from an ini file at startup or sth.

But I maintain Vista *Basic* has never actively been put on the market as your home-server solution; if anything all I remember is how they proclaimed everything would now be so easy, any computer illiterate person could easily work with it etc. etc. etc. Windows2008 Server on the other hand was agressively marketed as the 'ideal' server solution. Something says to me that they want to target a different audience with Vista than they want to with Server. Guess on what kind of systems them illiterate users run their OS?

From the P.O.V. of higher end system users their 'simplistic' approach to limiting the number of files is just a let down; but if they wished to keep the 'simplistic' way I'm in agreement better hardcode limitations in for a low end user and fail the higher end one. At any rate the higher end one can still go with an BSD or Debian style system and manually remove such limitations from the kernel. Have fun. ;)

---

### Post by tinny on 2008-08-28
> **skeeterbug said:**
> How exactly is remoting a pain?

```

public class UserManager : MarshalByRefObject

// UserManager code

```

Serve it up in IIS with only a web.config addition:
```

	<system.runtime.remoting>
		<application>
			<service>
				<wellknown mode="SingleCall" type="TestBLL.UserManager, TestBLL" objectUri="service.soap"/>
			</service>
      <channels>
        <channel ref="http"/>
        <serverProviders>
          <formatter ref="binary" />
        </serverProviders>
      </channels>
		</application>
	</system.runtime.remoting>

```


Calling it from a client:
```

//Register HTTP Channel
            HttpChannel chan = new HttpChannel();
            ChannelServices.RegisterChannel(chan, true);

            UserManager um = Activator.GetObject(typeof(UserManager), @"http://localhost:8080/WebSite/service.soap") as UserManager;
            string[] users = um.GetUsers();

```



Java (EJB3)

Define and implement your remote bean.
```

@Remote
public interface NewSessionRemote {
    //CODE define the interface
}

@Stateless(name="NewSessionBean")
public class NewSessionBean implements NewSessionRemote {
    //CODE implement the remote interface
}

```

Use your remote bean. J2EE container injects the remote bean.

```

public class ClientClass {
    @EJB(name="NewSessionBean")
    private NewSessionRemote remoteBean;

    //CODE
}

```

DONE!!!

> **skeeterbug said:**
> 
You can also setup network load balancing if you want to scale it. Your entire business logic layer could be easily served up this way. It is also a speed improvement over web services if you are communicating from .NET <-> .NET applications.

We have been doing this forever in J2EE :) Thats what application servers are for.

[http://developers.sun.com/appserver/reference/techart/glassfishcluster/](http://developers.sun.com/appserver/reference/techart/glassfishcluster/)

---

### Post by LaRoza on 2008-08-28
> **themusicwave said:**
> 
As I said, IIS is crippled on anything other than Windows Server.  Any production web application will have more than 10 concurrent users.

And Windows Server is crippled itself, so if you take away the crippled server software, and put it on a crippled OS, it is still crippled.

(Before arguing here, look at the system requirements for Windows Server and any modern Linux/BSD based OS with Apache.)


> **slavik said:**
> of course, this would be easy if all the user based config was stored in the user's $HOME (aka home directory, aka profile folder).

You are not thinking like them. They (MS) used to do exactly that, but they introduced the registery to make it harder to "pirate" software.

---

### Post by howlingmadhowie on 2008-08-28
> **LaRoza said:**
> 
You are not thinking like them. They (MS) used to do exactly that, but they introduced the registery to make it harder to "pirate" software.

i thought the registry was introduced out of pure stupidity, but i may be wrong there.

---

### Post by LaRoza on 2008-08-28
> **howlingmadhowie said:**
> i thought the registry was introduced out of pure stupidity, but i may be wrong there.

No, it is a brilliant tactic. They had a "justification" for it (clean up all those files) and are able to fool the users (even though the registry is the heart of all borked Windows installs and the target of most malware)

---

### Post by howlingmadhowie on 2008-08-28
> **Reiger said:**
> There is no myth there. In fact: there are only a few paradigms networking students are taught; and the first is that of 'Client-Server'. The close second is that of 'P2P'.
exactly. it's a paradigm. no more, no less. it describes the interactions between one computer which is at that moment offering something and another which is receiving it. any computer can be a server (it may be slower than an E25000 but it will work, just as any computer can be a client.

> 
And you'll find that even Debian or Ubuntu do the same (note how you don't get Apache or similar webserver packages installed by default?);

ubuntu produces two different basic package selections. that's it. they don't artificially cripple one product so as to make you believe that the other does something fundamentally different. 
> 
though they do not charge their consumers with a fee. I'm not saying it's worth $500 just for those constants (incidentally: do we *know* we're talking about constants and nothing else?); and I'd agree it be a better job if it was manually configurable and read from an ini file at startup or sth.
as far as i know all the extraneous settings built in to cripple the vista kernel in anything other than mega server 2008 professional edition are in the registry. i don't really care. 

look, you're obviously not getting what i'm saying here, so i'll try to explain it again. any pc you find lying around in an office nowadays is faster than the fastest server you could buy 15 years ago. a standard dual-core pentium machine with 2GB of RAM could run a number of high volume internet sites without any difficulty nowadays. just throw an ubuntu desktop edition on it and install the apache packages (and tomcat and whatever else you want to use). that computer is now a server, because it fulfills the role of a server, and it does it very well. 

so the basic difference between a server and a client is found in the applications installed. any other differences have to be carefully manufactured. microsoft and others (ibm, sun, dell, hp...) have spent a lot of time and money trying to convince the world that servers and pcs/workstations/laptops/whatever are fundamentally different. they aren't.

---

### Post by pmasiar on 2008-08-28
> **howlingmadhowie said:**
> as far as i know all the extraneous settings built in to cripple the vista kernel in anything other than mega server 2008 professional edition are in the registry. i don't really care. 

That would be too easy. In corporate environment you have to run License management server, which dynamically lets users to use only bought number of clients: even if installed, you cannot use it because dork in HR went to lunch and did not logged out, and number of paid licenses is maxed out. This is kind of services MSFT customers love and appreciate (and pay for). Crippling software with compiled-in constants is not fun enough - any idiot can to **that**. But try to make people to pay for software which is crippled dynamically!

---

### Post by LaRoza on 2008-08-28
> **pmasiar said:**
> That would be too easy. In corporate environment you have to run License management server, which dynamically lets users to use only bought number of clients: even if installed, you cannot use it because dork in HR went to lunch and did not logged out, and number of paid licenses is maxed out. This is kind of services MSFT customers love and appreciate (and pay for). Crippling software with compiled-in constants is not fun enough - any idiot can to **that**. But try to make people to pay for software which is crippled dynamically!
Thats messed up.

---

### Post by themusicwave on 2008-08-28
> **pmasiar said:**
> That would be too easy. In corporate environment you have to run License management server, which dynamically lets users to use only bought number of clients: even if installed, you cannot use it because dork in HR went to lunch and did not logged out, and number of paid licenses is maxed out. This is kind of services MSFT customers love and appreciate (and pay for). Crippling software with compiled-in constants is not fun enough - any idiot can to **that**. But try to make people to pay for software which is crippled dynamically!

I can attest to seeing many systems at work like this, some our certainly based on Windows Server, others I don't know.

Nothing like getting that little There are too many sessions in use, please wait for an available session and try again messages....

---

### Post by howlingmadhowie on 2008-08-29
> **themusicwave said:**
> I can attest to seeing many systems at work like this, some our certainly based on Windows Server, others I don't know.

Nothing like getting that little There are too many sessions in use, please wait for an available session and try again messages....

on a similar note i once translated the site administrator's manual for a large e-commerce shop software (the site administrator sells shops to the shop administrators, by the way). in the manual there was a sentence something like "if you need more shop licenses to sell, just contact us and we'll increase your license count remotely so you can offer shops to more shop administrators". It was one of the moments in my life which pushed me towards free software.

---

### Post by dracvs on 2008-08-29
Are you still helping out the guy with question about languages or are we still debating which webserver is better or are we debating what kernel compilation works better or what Operative systems has more Cool.... or what?


I would like, if the creator of this thread re appeared. He is probably running away from us XD

---

### Post by skeeterbug on 2008-08-29
> **tinny said:**
> Java (EJB3)

Define and implement your remote bean.
```

@Remote
public interface NewSessionRemote {
    //CODE define the interface
}

@Stateless(name="NewSessionBean")
public class NewSessionBean implements NewSessionRemote {
    //CODE implement the remote interface
}

```

Use your remote bean. J2EE container injects the remote bean.

```

public class ClientClass {
    @EJB(name="NewSessionBean")
    private NewSessionRemote remoteBean;

    //CODE
}

```

DONE!!!



We have been doing this forever in J2EE :) Thats what application servers are for.

[http://developers.sun.com/appserver/reference/techart/glassfishcluster/](http://developers.sun.com/appserver/reference/techart/glassfishcluster/)

I believe you ;)

You don't think EJB's are hard, and I don't think remoting is hard! EJB has come a long way since I last looked at it, that is for sure.

---

### Post by CptPicard on 2008-08-29
> **skeeterbug said:**
> EJB has come a long way since I last looked at it, that is for sure.

+100

This is my impression too. My previous experience with EJB is with EJB2.0 and the time when you had to hand-tune magically breaking ant scripts to manage your build and deployment to your (flaky) development server... modern Netbeans + EJB combo is much more comfortable.

If there is anything I would complain about is that it still relies a lot on tools "just working", but the spec itself has got more simple and the underlying tools more robust that you are not completely at the mercy of your IDE doing things right.

---

### Post by pmasiar on 2008-08-29
> **skeeterbug said:**
> You don't think EJB's are hard, and I don't think remoting is hard! EJB has come a long way since I last looked at it, that is for sure.

There is something magical in version 3 release (Windows 3.1 was first usable version too) and 10 years of development. Brooks laws also apply ("Plan a version to throw out, you will do it anyway").

Regardless of all marketing, it takes 10 years to develop complex unobvious technology what is also usable.

---

### Post by dracvs on 2008-09-15
.... I cant believe I have to add 4 or 5 new modules to get BASIC functionality out of J2EE

Worst example and thing that has me losing interest rapidly into it:

I need a special compilation so it will work with XHTML.... Else it fails. Big.

I mean... Come on.

---

### Post by tinny on 2008-09-15
> **dracvs said:**
> .... I cant believe I have to add 4 or 5 new modules to get BASIC functionality out of J2EE

Worst example and thing that has me losing interest rapidly into it:

I need a special compilation so it will work with XHTML.... Else it fails. Big.

I mean... Come on.

:confused:

What are these 4 or 5 modules? Doesn't sound right to me.

Have a look at the Netbeans J2EE learning trail, its easy.

[http://www.netbeans.org/kb/trails/java-ee.html](http://www.netbeans.org/kb/trails/java-ee.html)

---

### Post by dracvs on 2008-09-16
> **tinny said:**
> :confused:

What are these 4 or 5 modules? Doesn't sound right to me.

Have a look at the Netbeans J2EE learning trail, its easy.

[http://www.netbeans.org/kb/trails/java-ee.html](http://www.netbeans.org/kb/trails/java-ee.html)

Im using Real weapons of Mass destruction here, talk about Jbuilder 2008 and Eclipse 3.4.

In the default configuration, for some reason, neither of the two add the facelets functionality. Neither does Glassfish 2V2.

But then again, these are the kind of things that stumps the people learning with tools other than netbeans (That I dont think has, 1/100 of the power of Jbuilder and or Eclipse) or happen to find the problem. 

Maybe i missed something. one hidden checkbox. But neither me or my boss could make it work on the default config (and hes a seasoned Java Developer )

---

### Post by tinny on 2008-09-16
> **dracvs said:**
> 
(That I dont think has, 1/100 of the power of Jbuilder and or Eclipse).


Netbeans is good. Like any tool you just need to learn how to use it.

> **dracvs said:**
> 
In the default configuration, for some reason, neither of the two add the facelets functionality. Neither does Glassfish 2V2.


FYI: Netbeans 6.x, Facelets
[https://nbfaceletssupport.dev.java.net/features.html](https://nbfaceletssupport.dev.java.net/features.html)

---

### Post by dracvs on 2008-09-17
> **tinny said:**
> Netbeans is good. Like any tool you just need to learn how to use it.



FYI: Netbeans 6.x, Facelets
[https://nbfaceletssupport.dev.java.net/features.html](https://nbfaceletssupport.dev.java.net/features.html)

Good to know! haha

I still like more the flexibility of the Jbuilder 2008.

OH! and im done doing Webtests C# Against J2ee performance wise

Result:

IT DOESNT MATTER! As long as you know what you are doing the end user wont notice and seriously, wont care. The execution times are nearly indescriptible or indiscernible...

---

### Post by CptPicard on 2008-09-17
> **dracvs said:**
> 
IT DOESNT MATTER! As long as you know what you are doing the end user wont notice and seriously, wont care. The execution times are nearly indescriptible or indiscernible...

No kidding. Consider the IO latency especially over network compared to execution times "inside the process"...

---

### Post by tinny on 2008-09-17
> **dracvs said:**
> 
I still like more the flexibility of the Jbuilder 2008.


:confused: flexibility?

Modern software developers are blessed with great IDE's. Which one is best? I dont know... This just comes down to personal preference.

---

### Post by LaRoza on 2008-09-17
> **tinny said:**
> 
Modern software developers are blessed with great IDE's. Which one is best? I dont know... This just comes down to personal preference.

Modern software developers using corporation created languages are cursed with languages that need great IDE's.

</semi-serious>

Best? The one that one uses and is productive.

---

### Post by dracvs on 2008-09-18
> **LaRoza said:**
> Modern software developers using corporation created languages are cursed with languages that need great IDE's.

</semi-serious>

Best? The one that one uses and is productive.

Notepad?

Does anyone remember when a program was a ONE File thing you went and compiled, linked and worked right off the bat?

Nowadays they have so many parts, configurations and stuff and then we rely on the IDE to make sure we dont miss this references...

Now I like Jbuilder 2008 (and basically eclipse Ganymede since they are almost the same, given Jbuilder has more collaboration stuff)and i Dont like netbeans.

Other people I know adore netbeans and hate the ton of options in eclipse.

What do you guys use?

Oh and I use Visual Studio And Express 2008.

---

### Post by pmasiar on 2008-09-18
> **dracvs said:**
> Notepad?

Does anyone remember when a program was a ONE File thing you went and compiled, linked and worked right off the bat?

I do - and even back then, before notepad ever existed, there were better editors than notepad. Nopepad was crappy editor for crappy system, and nothing more. Although notepad is not the worst editor ever, that award goes to TEX editor for RS/11. That was really evil one :-)

---

### Post by LaRoza on 2008-09-18
> **pmasiar said:**
> I do - and even back then, before notepad ever existed, there were better editors than notepad. Nopepad was crappy editor for crappy system, and nothing more. Although notepad is not the worst editor ever, that award goes to TEX editor for RS/11. That was really evil one :-)

+1 (I wasn't back then, but I find edit.com better than notebad.)

---

### Post by pmasiar on 2008-09-18
My bad, it was TECO, and deserves own wikipage: [http://en.wikipedia.org/wiki/Text_Editor_and_Corrector](http://en.wikipedia.org/wiki/Text_Editor_and_Corrector)

Edit command sequence was basically a program to transform input file in tricky way. Common game was to open a file and type some random sentence, and take bets what would happen. :-) Closing without saving changes was the least of the problems...

---

### Post by LaRoza on 2008-09-18
> **pmasiar said:**
> My bad, it was TECO, and deserves own wikipage: [http://en.wikipedia.org/wiki/Text_Editor_and_Corrector](http://en.wikipedia.org/wiki/Text_Editor_and_Corrector)

Edit command sequence was basically a program to transform input file in tricky way. Common game was to open a file and type some random sentence, and take bets what would happen. :-) Closing without saving changes was the least of the problems...

Now we know why E**** is so evil. Spawn of something more evil.

---

### Post by tinny on 2008-09-18
> **dracvs said:**
> 
Other people I know adore netbeans and hate the ton of options in eclipse.

What do you guys use?


I use Eclipse and Netbeans. I use Eclipse at work and I think it is slightly better than Netbeans (although Netbeans is a good beginners Java IDE). I use Netbeans at home because I want to keep up to speed with it for my ROD (Resume orientated development).

I can understand that JBuilder would give you a very nice out of the box experience. Eclipse can be customised with various plugins, it just takes time and research.

> **dracvs said:**
> 
given Jbuilder has more collaboration stuff


What collaboration stuff are you after? Maybe I could show you the Eclipse equivalent.

Also...

I find it really hard to believe that large software projects are delivered in Python with just text editors. Id love to know how those Google guys do it.

---

### Post by descendency on 2008-09-18
In my opinion, .NET is better simply because the IDE is so much better than 99% of IDEs (let alone Java IDEs)

---

### Post by tinny on 2008-09-18
> **descendency said:**
> In my opinion, .NET is better simply because the IDE is so much better than 99% of IDEs (let alone Java IDEs)

What can Visual Studio do that Eclipse + plugins cant?

Back up your comments please :-)


To turn it around on you... Java is better simply because the operating systems it can run on are so much better than Windows. ;) (MonoDevelop for C# linux development is not as good as Eclipse)

---

### Post by LaRoza on 2008-09-18
> **tinny said:**
> 
Back up your comments please :-)

It is obvious, the IDE is the most important part of a platform, not its capabilities. Indication of a not-so-great coder ;)

> 
To turn it around on you... Java is better simply because the operating systems it can run on are so much better than Windows. ;) (MonoDevelop for C# linux development is not as good as Eclipse)
+1 Also, Java itself is a good platform.

---

### Post by tinny on 2008-09-18
> **LaRoza said:**
> It is obvious, the IDE is the most important part of a platform, not its capabilities.)


Yeah that really is true. You simply cant do **professional** .Net development without Visual Studio.

IMO, you cant do **professional** Java development without an IDE (I think you can learn Java without an IDE), but at least with Java you have a choice. (Eclipse, Netbeans, Intellij, JBuilder)

---

### Post by LaRoza on 2008-09-18
> **tinny said:**
> Yeah that really is true. You simply cant do **professional** .Net development without Visual Studio.

IMO, you cant do **professional** Java development without an IDE (I think you can learn Java without an IDE), but at least with Java you have a choice. (Eclipse, Netbeans, Intellij, JBuilder)

What is the difference between professional and non-professional?

---

### Post by skeeterbug on 2008-09-18
cake > pie

If you like pie more, you are WRONG.

---

### Post by skeeterbug on 2008-09-18
> **descendency said:**
> In my opinion, .NET is better simply because the IDE is so much better than 99% of IDEs (let alone Java IDEs)

This is 100 percent false. I have used Eclipse(For C, Python, Perl, and Ruby) and VS (version 6, 2003, 2005, and 2008). You obviously haven't used an IDE outside of VS, so don't make ignorant remarks about which is better.

---

### Post by mike_g on 2008-09-18
> What is the difference between professional and non-professional?
In short professionals get paid; they have greater commitments and if they screw up other people get pissed of.

---

### Post by LaRoza on 2008-09-18
> **mike_g said:**
> In short professionals get paid; they have greater commitments and if they screw up other people get pissed of.

Then that is a flawed concept. 

Professionals are often the least...professional. Read the [http://thedailywtf.com/](http://thedailywtf.com/)

I would say open source is the pinacle of software development.

---

### Post by mike_g on 2008-09-18
Yes, its surprising how some people manage to land jobs in programming. The stuff on wtf is rare examples. To get a job you usually have to prove your capabilities and when working theres deadlines and can be a lot of pressure; i expect that its completely different to programming as a hobby. Also, most of the experienced OS developers are, or have been, professionals.

---

### Post by tinny on 2008-09-18
> **LaRoza said:**
> What is the difference between professional and non-professional?

A professional developer to me is a developer that works on software of substance that provides a solution to a problem. If their coding doesn't work they are held accountable for it. Their software actually has users. I dont think you need to be paid to be a professional developer, OSS developers are professional developers.

Of course as in any profession there are varying levels of ability.

---

### Post by LaRoza on 2008-09-18
> **tinny said:**
> A professional developer to me is a developer that works on software of substance that provides a solution to a problem. If their coding doesn't work they are held accountable for it. Their software actually has users. I dont think you need to be paid to be a professional developer, OSS developers are professional developers.

Very good definitions. +1

I haven't used Java professionally, and I wouldn't try. Perhaps I think that because I never tried an IDE with it. Perhaps it is just as managable with an IDE as what I am used to with C and Python.

---

### Post by tinny on 2008-09-18
> **LaRoza said:**
> Very good definitions. +1

I haven't used Java professionally, and I wouldn't try. Perhaps I think that because I never tried an IDE with it. Perhaps it is just as managable with an IDE as what I am used to with C and Python.

If I had to use an Editor for my Java development I would quit!

I think a beginner could manage 5-10 Java files in an editor and gain the learning benefit that comes from using an editor (training your eye), but beyond that...

I would still love to know if it is **practical** to develop a complicated / big application with Python / PHP / Ruby etc without using a IDE. (I will find out one day :-) )

---

### Post by cprofitt on 2008-09-18
> **themusicwave said:**
> 

I also know that to really host .Net properly you need to be running Windows Server 2008, which is another restriction and also gets expensive. The Web Server is called IIS [http://www.microsoft.com/WindowsServer2003/IIS/Default.mspx](http://www.microsoft.com/WindowsServer2003/IIS/Default.mspx)

First... for .Net web applications you can run them on:

Windows Server 2003 or 2008
Windows XP or Vista (recommended: testing or development only)

.Net as a whole can run on Windows XP, 2003, Vista or 2008 if you are making a Windows Forms or Console application.

---

### Post by tinny on 2008-09-18
> **PrivateVoid said:**
> First... for .Net web applications you can run them on:

Windows Server 2003 or 2008
Windows XP or Vista (recommended: testing or development only)

.Net as a whole can run on Windows XP, 2003, Vista or 2008 if you are making a Windows Forms or Console application.

Yep .Net has a lot of flexibility when it comes to the operating system you can run it on. :lolflag:

---

### Post by LaRoza on 2008-09-19
> **tinny said:**
> I would still love to know if it is **practical** to develop a complicated / big application with Python / PHP / Ruby etc without using a IDE. (I will find out one day :-) )

It would depend on how you define IDE. By definition, anything used is an IDE. I use a customised Vim setup, a terminal and other tools. That is an IDE. It isn't one program, nor does it have to be.

The language Python is suitable for large projects, so is PHP. Python code itself would be more expressive than Java, so you'd have less junk to deal with (meaning, line 100 in a Python program is likely comparable to line 1000 in a Java program) PHP would be a little shorter, but not as short as the Python code.

Python is a language you can write without need much to deal with the code. In the system restore program, the core module is less than 261 lines of code. I'd like to see what that code would be in Java! [http://bazaar.launchpad.net/~laroza/sysres/sysres/annotate/62?file_id=system_restore.py-20080911143258-1550tlu03fjqoveq-19](http://bazaar.launchpad.net/~laroza/sysres/sysres/annotate/62?file_id=system_restore.py-20080911143258-1550tlu03fjqoveq-19)

None of us are using large IDE's. I think one of the devs uses Geany, but I use Vim and Gedit.

---

### Post by tinny on 2008-09-19
> **LaRoza said:**
> It would depend on how you define IDE. By definition, anything used is an IDE. I use a customised Vim setup, a terminal and other tools. That is an IDE. It isn't one program, nor does it have to be.


For me an IDE is a bunch of tools integrated into one application. E.g. Intelligent editor, Subversion client, Refactoring tools...

> **LaRoza said:**
> 
The language Python is suitable for large projects, so is PHP. Python code itself would be more expressive than Java, so you'd have less junk to deal with (meaning, line 100 in a Python program is likely comparable to line 1000 in a Java program) PHP would be a little shorter, but not as short as the Python code.


I don't doubt this. But not everything can be done in 100 lines, right? A banking system written in Java might be 1,000,000,000 lines of code. Say you could do this in Python in 100,000,000 lines of code, would you still use an Editor?

> **LaRoza said:**
> 
Python is a language you can write without need much to deal with the code. In the system restore program, the core module is less than 261 lines of code. I'd like to see what that code would be in Java! [http://bazaar.launchpad.net/~laroza/sysres/sysres/annotate/62?file_id=system_restore.py-20080911143258-1550tlu03fjqoveq-19](http://bazaar.launchpad.net/~laroza/sysres/sysres/annotate/62?file_id=system_restore.py-20080911143258-1550tlu03fjqoveq-19)


Thats great.

---

### Post by LaRoza on 2008-09-19
> **tinny said:**
> For me an IDE is a bunch of tools integrated into one application. E.g. Intelligent editor, Subversion client, Refactoring tools...

Does integrated mean "stuck together" or "work together"? From a total perspective, all the software used is part of the "IDE", right down to the kernel.



> 
I don't doubt this. But not everything can be done in 100 lines, right? A banking system written in Java might be 1,000,000,000 lines of code. Say you could do this in Python in 100,000,000 lines of code, would you still use an Editor?

No, of course not. I didn't say that ;) 

Good design means functions should be short. Even in the Linux kernel, 22000 files, Linus says functions shouldn't take up more than two screens at the very most (this is on an 25x80 terminal)

The total size shouldn't matter. The individual files shouldn't be very large. The functions should be small. The code should be logical. 

I can see no feature in a large IDE that I'd want that my editors don't already have.

[[IMG]http://img47.imageshack.us/img47/4379/200809190100081680x1050pq2.th.png[/IMG]](http://img47.imageshack.us/my.php?image=200809190100081680x1050pq2.png)

---

### Post by skeeterbug on 2008-09-19
> **LaRoza said:**
> Does integrated mean "stuck together" or "work together"? From a total perspective, all the software used is part of the "IDE", right down to the kernel.




No, of course not. I didn't say that ;) 

Good design means functions should be short. Even in the Linux kernel, 22000 files, Linus says functions shouldn't take up more than two screens at the very most (this is on an 25x80 terminal)

The total size shouldn't matter. The individual files shouldn't be very large. The functions should be small. The code should be logical. 

I can see no feature in a large IDE that I'd want that my editors don't already have.

[[IMG]http://img47.imageshack.us/img47/4379/200809190100081680x1050pq2.th.png[/IMG]](http://img47.imageshack.us/my.php?image=200809190100081680x1050pq2.png)

For example, with a feature rich IDE you can right click a function call, and jump to the definition or find all usages of it. This alone is a huge time saver in large projects. Also the IDE is integrated, you can do your development, SVN, database manipulation, project configuration, etc from one program without alt tabbing around. It offers time savers tailored to your language and framework (launching servers, attaching to processes to debug, etc).

---

### Post by tinny on 2008-09-19
> **LaRoza said:**
> 
Does integrated mean "stuck together" or "work together"?


Both, a one stop shop.

> **LaRoza said:**
>  From a total perspective, all the software used is part of the "IDE", right down to the kernel.


I think you are stretching it a bit now ;) My mum has a computer and she doesnt have an IDE.

> **LaRoza said:**
> 
I can see no feature in a large IDE that I'd want that my editors don't already have.


What is the largest code base you have worked on?

> **skeeterbug said:**
> For example, with a feature rich IDE you can right click a function call, and jump to the definition or find all usages of it. This alone is a huge time saver in large projects. Also the IDE is integrated, you can do your development, SVN, database manipulation, project configuration, etc from one program without alt tabbing around. It offers time savers tailored to your language and framework (launching servers, attaching to processes to debug, etc).

1+ Good examples

Also if you right click on a function call you can rename usages and definitions by using the inbuilt refracting tool.

---

### Post by fballem on 2008-09-19
> **dracvs said:**
>  ...
to date, nobody has ever been to tell me why there are 4 versions of eclipse, instead of just one JVM program. 


I assume that you are referring to the different platforms (Windows, Linix, ...) and not the different packaging (Java EE, Eclipse Modeler, Eclipse RCP ...).

I believe that one of the primary reasons is because of the Standard Widget Toolkit ([http://www.eclipse.org/swt/](http://www.eclipse.org/swt/)), which is included in eclipse.

SWT is not part of 'standard' Java, so is not included in the platform specific version of Java that you installed on your system.

Regards,

---

### Post by scottuss on 2008-09-19
To be honest I find .NET easier to use (not the better platform though) simply because J2EE is so darn complicated. There is so much to learn to make a simple app where in .NET I can drag a few components, write a little glue code and I have an app that would take hours on J2EE.

Clearly this is my fault for lack of knowledge but just thought I'd offer my thoughts anyway

---

### Post by tinny on 2008-09-19
> **scottuss said:**
> To be honest I find .NET easier to use (not the better platform though) simply because J2EE is so darn complicated. There is so much to learn to make a simple app where in .NET I can drag a few components, write a little glue code and I have an app that would take hours on J2EE.

Clearly this is my fault for lack of knowledge but just thought I'd offer my thoughts anyway

You are finding .Net easier because the type of development you describe above is not enterprise development. Enterprise development by its very nature is very large and complicated (banking, insurance, billing systems etc...). Web 2.0 type development should not be done with J2EE. Instead you should use something like Groovy + Grails or JRuby + Rails for the Java platform.

If you where to try and develop a .Net enterprise application with say distributed services and distributed transactions etc... you would find it incredibly complicated.

---

### Post by cprofitt on 2008-09-19
> **tinny said:**
> Yep .Net has a lot of flexibility when it comes to the operating system you can run it on. :lolflag:

In comparison to Java, no... but the post I was correcting was inaccurate as it made the claim that you needed server 2008. While I may not like a platform I see no reason to be inaccurate about it.

---

### Post by dracvs on 2008-09-19
So many Answers spawning of a single question! 

Okay, let me recap:

IDE: help for the developer so he doesnt become completely insane trying to remember every single thing in their multiple files in a big project.

Also a more standard definition is the name itself, Integrated Development Environment. Why do we even bother to redefine the thing?

J2EE it's enterprise yes, but Where I work .NET has been used in big enterprise banking Apps more and more given its short development time and fast response and stability inside windows (For some reason it is less prone to crazy server behaviors as I have seen with EJB's )

Then again, The IDE doesn't matter, If you have the best IDE in the world, and you don't have idea how to use it's capabilities it's like working with Notepad++. A nice expensive (in some cases) text editor.

There has been lately this.. RAD kind of solution, Rapid Application Development, where the idea is to make an App, Enterprise or  not in the shortest time possible and with the most stability without suffering too much.

CodeGears Jbuilder 2008 goes by this standard, and Eclipse and Visual Studio does Too lately. Mono Tries... But sometimes I would like someone would insert some money so it would work better and a bit faster. (if I had Any kind of money I would!)

Then we have People like Laroza who loves to just have an editor and some terminals.

But keeping track of a multi tiered project its a real pain. Specially working on J2EE with Multiple EJB's and persistence and then ARGGH!! 

It's All in the eye of the beholder.


PS: PHP is only good for static webpages that dont need to be reliable or usable. I don't think we should be doing Scripting Salad with XHTML in this age of .NET and J2EE.

Seriously.

---

### Post by pmasiar on 2008-09-19
> **tinny said:**
> I find it really hard to believe that large software projects are delivered in Python with just text editors. Id love to know how those Google guys do it.

Calling vim or emacs "just a text editor" is quite understatement. Compared to IDEs, which are optimized to help you writing more lines of code faster (intellisense and all those suggestions), great editors are optimized to **refactor** existing code faster. Old hands have own macros, which are like IDE plugins, only simpler to enhance and maintain (because they don't bother with GUI). As you know, having to deal with GUI (trying to be newbie-friendly) is sink of productivity, because noobs are so innovative in finding new ways to break logic.

---

### Post by pmasiar on 2008-09-19
> **descendency said:**
> In my opinion, .NET is better simply because the IDE is so much better than 99% of IDEs (let alone Java IDEs)

You so obviously lack the experience of hitting the wall when your IDE does not allow you to do something you know is possible but IDE authors prevented you to do because it is dangerous for noobs to do or authors just did not thought about it. Is it because lack of experience in general? 8-)

---

### Post by tinny on 2008-09-19
dracvs, I dont believe you have used J2EE in professional development.

> **dracvs said:**
> 
J2EE it's enterprise yes, but Where I work .NET has been used in big enterprise banking Apps more and more given its short development time and fast response and stability inside windows (For some reason it is less prone to crazy server behaviors as I have seen with EJB's )


Sorry I completely disagree. "crazy server behaviors as I have seen with EJB's", what are you talking about? This technology is used by thousands of enterprise systems. Ive used it for nearly 10 years and to be honest I have seen crazy behaviors, but it has ALWAYS been due to the human factor (poor coding). I have also seen poor coding produce crazy behaviors in .Net (I was a .Net developer for 1 year), does this make .Net sub par?

> **dracvs said:**
> 
There has been lately this.. RAD kind of solution, Rapid Application Development, where the idea is to make an App, Enterprise or  not in the shortest time possible and with the most stability without suffering too much.


The concept of RAD has existed for a long time.

> **dracvs said:**
> 
CodeGears Jbuilder 2008 goes by this standard, and Eclipse and Visual Studio does Too lately. Mono Tries... But sometimes I would like someone would insert some money so it would work better and a bit faster. (if I had Any kind of money I would!)


Ummm, have you heard of a company called Novel? A.K.A the driving force behind Mono.

> **dracvs said:**
> 
But keeping track of a multi tiered project its a real pain. Specially working on J2EE with Multiple EJB's and persistence and then ARGGH!! 


Specially if you dont know what you are talking about. EJB's exist to facilitate these multi tiers. Learn this stuff before you put it down.

> **dracvs said:**
> 
PS: PHP is only good for static webpages that dont need to be reliable or usable. I don't think we should be doing Scripting Salad with XHTML in this age of .NET and J2EE.


Thats is a very ignorant comment. Have you used PHP? Have you used any scripting language? (beyond hello world)

---

### Post by tinny on 2008-09-19
> **pmasiar said:**
> Calling vim or emacs "just a text editor" is quite understatement. Compared to IDEs, which are optimized to help you writing more lines of code faster (intellisense and all those suggestions), great editors are optimized to **refactor** existing code faster. Old hands have own macros, which are like IDE plugins, only simpler to enhance and maintain (because they don't bother with GUI). As you know, having to deal with GUI (trying to be newbie-friendly) is sink of productivity, because noobs are so innovative in finding new ways to break logic.

Yep, that all makes sense.

To be honest ive never taken the time to get up to speed with a smart editor. I only used an Editor to code when I was learning Java.

---

### Post by pmasiar on 2008-09-19
Difference between .NET and J2EE is in my view in origins of the system: MSFT had lock on desktop apps and was scaling "up" to workgroup apps. Sun and IBM had lock on big systems (which cost dozens of millions USD) and looked for tool to simplify development to medium size system (costing mere dozens of thousands USD). So J2EE is complicated because it is designed to handle complicated problems which .NET was not able to handle until recently, if at all.

It's always the little upstart who tries to overcome established dinosaur in the niche. As upstart is gaining features, dinosaur needs to learn to be more nimble to crush the newcomer, or the newcomer will eat his lunch.

I think that MSFT had the obvious realization (which look brilliant when compared to complacency of the giants) that you don't aim for silver bullet - single language to rule them all, like Java was marketed, but group of languages which work well together: nimble languages like IronRuby and IronPython for developing apps, and C# for developing libraries. 

Sun could support Jython in this role for Java 10 years ago but choose not to (because they trusted their own marketoids - always a mistake to believe your propaganda), and let Jython's lead developer be hired by MSFT and design the dynamic language runtime for .NET.

But even now, many people in .NET do not understand how the game changed, and think the battle will be between Java and C#. Ridiculous: battle will be between languages used to create  solutions to user's problems, which need to be nimble. Runtime effectiveness is required for libraries.

---

### Post by tinny on 2008-09-19
> **pmasiar said:**
> Difference between .NET and J2EE is in my view in origins of the system: MSFT had lock on desktop apps and was scaling "up" to workgroup apps. Sun and IBM had lock on big systems (which cost dozens of millions USD) and looked for tool to simplify development to medium size system (costing mere dozens of thousands USD). So J2EE is complicated because it is designed to handle complicated problems which .NET was not able to handle until recently, if at all.

It's always the little upstart who tries to overcome established dinosaur in the niche. As upstart is gaining features, dinosaur needs to learn to be more nimble to crush the newcomer, or the newcomer will eat his lunch.

I think that MSFT had the obvious realization (which look brilliant when compared to complacency of the giants) that you don't aim for silver bullet - single language to rule them all, like Java was marketed, but group of languages which work well together: nimble languages like IronRuby and IronPython for developing apps, and C# for developing libraries. 

Sun could support Jython in this role for Java 10 years ago but choose not to (because they trusted their own marketoids - always a mistake to believe your propaganda), and let Jython's lead developer be hired by MSFT and design the dynamic language runtime for .NET.

But even now, many people in .NET do not understand how the game changed, and think the battle will be between Java and C#. Ridiculous: battle will be between languages used to create  solutions to user's problems, which need to be nimble. Runtime effectiveness is required for libraries.

Yeah, .Net is keeping Java honest and forcing the Java community to look for better ways of doing things (this is a really good thing). I do think that J2EE development is getting a bit over the top, but I think this is mostly due to the mentality of a lot of J2EE developers. Just because we have design patterns and service layers for abstraction doesn't mean we have to use them. Today I added one text input field to a web page in an existing J2EE application im currently working on. I needed to persist this fields value to a database, to do this I had to go through 2 session beans, 1 adapter, 1 service layer, a DAO and a persistence context. Now the original developer didnt need to do this, but its enterprisey right?

J2EE gives us a huge tool box to use, this doesnt mean we need to use a hammer, drill, screw driver and saw all at the same time. You can do things simply in J2EE (relative to .Net).

---

### Post by pmasiar on 2008-09-19
... or in single sentence, .NET is working hard to scale up, while J2EE realized it should to scale down too :-)

---

### Post by sakabato on 2008-09-19
I am professionally involved in J2EE , .net and rails projects in the past. Note that we do not have J2EE any more. Last time I checked the name was JEE.

Back in 2004 my first professional job was in J2ee platform. We were using Struts, hibernate and EJB 2 without entity beans.

It was okay platform for those days. But java people including me realized J2EE approach is a bit more academic. 

.NET framework had better practices in someways and in someways it was worse. I would technically find .NET superior every which way compared to JEE. However following MS practices led many developers crappy unmaintainable code. JEE had an ORM framework since 2003 and Microsoft  has just released an ORM framework in 2008.  Many .net developers tend to be Visual Studio monkeys without knowing what they are actually doing.

Now the other side of the equation, there is an ALT.NET movment recently growing. Those people follow community practices rather than MS practices which results in much much better way than Java ways.

Excluding the runtime libraries and comparing the 2 main stream languages for each platform  Java and C#, C# is a clear winner. Besides it's main stream IDE Visual Studio is pretty much integrated with the platfrom. Java also has Eclipse , JDeveloper and  IntelliJ Idea and netbeans. But still Visual Studio is overwhelms them imho.

As many people stated in this forum once you start using .NET (and not C#) you will find your self vendor locked in. More over you will feel yourself stuck in Windows platform. Besides Visual Studio 2008 might be very costly.

However imho, this proves to be wrong. There is an open source implementation of .NET framework called Mono which causes many debates in linux community these days about patent issues. Disregarding those patent issiues I truly think Mono really cleanses this last downside of .net framework in a very good way. So your .NET applications are not restricted to Windows anymore. (this has exceptions, like Windows Presentation Foundation , and some minor parts of .NET framework , but you really wouldn't want to port them anyway). Further more you are able to develop .NET applications on your linux box with Free a IDE monodevelop. 

These are my personal opinions on technical merits of the 2 frameworks. The industry also day by day pushes .NET framework rather than java. Actually as a requirement to my professional job, while following daily developments in the .net framework I am astonished how fast Microsoft pushes new frameworks and toys. It is impossible to follow up. But I have no complains. Options are good. On Sun side you will see there are some java bugs waiting to be fixed since 1998! Java had a great potential. And it occuppied many enterprise software written in early 2000's. But Sun's overprotecting and breucratic behaviors for java made it unpopular recently and this trend still goes on. We have many C# appications for linux and a few Java ones for client. (this does not prove anything but I find it interesting)

So my 2 cents,

---

### Post by pmasiar on 2008-09-19
> **sakabato said:**
> I am astonished how fast Microsoft pushes new frameworks and toys. It is impossible to follow up. But I have no complains. Options are good.

Too many options does not give you any good (it's even harmful)  [as proven by psychology research](http://en.wikipedia.org/wiki/The_Paradox_of_Choice), and besides MSFT might be just cranking tools as [cover fire](http://www.joelonsoftware.com/articles/fog0000000339.html) while retooling themselves, to keep competitive advantage: they have more money than God, so cranking new toys is cheap way to keep competitors confused.

I agree with you in general, I just want to FYI why more choice is not automagically a win-win (if the change offered is just cover fire).

---

### Post by LaRoza on 2008-09-19
> **pmasiar said:**
>  and besides MSFT might be just cranking tools as [cover fire](http://www.joelonsoftware.com/articles/fog0000000339.html) while retooling themselves, to keep competitive advantage: they have more money than God, so cranking new toys is cheap way to keep competitors confused.

Or to keep customers confused, as they should be. If they knew all the choices they had equally, they probably wouldn't be using Microsoft.

---

### Post by skeeterbug on 2008-09-19
> **LaRoza said:**
> Or to keep customers confused, as they should be. If they knew all the choices they had equally, they probably wouldn't be using Microsoft.

What?

---

### Post by LaRoza on 2008-09-19
> **skeeterbug said:**
> What?

Microsoft's idea of "choice" is "choices chosen by us", not real choices. Like a mother giving her child choices on what to wear or eat. No matter how many choices Microsoft gives you, you still have essential no choices.

---

### Post by skeeterbug on 2008-09-19
> **LaRoza said:**
> Microsoft's idea of "choice" is "choices chosen by us", not real choices. Like a mother giving her child choices on what to wear or eat. No matter how many choices Microsoft gives you, you still have essential no choices.

Clearly it's because their customers have been forced to using their products and there are no other competing frameworks out there for anyone to consider.

---

### Post by pmasiar on 2008-09-19
> **skeeterbug said:**
> Clearly it's because their customers have been forced to using their products and there are no other competing frameworks out there for anyone to consider.

Users were conditioned not to look for competing products - as someone posted above, they have hard time to keep up with changes churned out by MSFT (big part of which is just cover fire), so for sure they don't have time even to think about competing offers - that's the whole point of cover fire 8-)

---

### Post by tinny on 2008-09-19
> **pmasiar said:**
> Too many options does not give you any good (it's even harmful)  [as proven by psychology research](http://en.wikipedia.org/wiki/The_Paradox_of_Choice), and besides MSFT might be just cranking tools as [cover fire](http://www.joelonsoftware.com/articles/fog0000000339.html) while retooling themselves, to keep competitive advantage: they have more money than God, so cranking new toys is cheap way to keep competitors confused.

I agree with you in general, I just want to FYI why more choice is not automagically a win-win (if the change offered is just cover fire).

Yep too many choices... I actually think that J2EE suffers far more in this area than .Net. Struts, Spring, JBoss Seam, Wicket, Stripes etc etc it just goes on and on.

If we just got behind say 2 frameworks, imagine how good they would be.

---

### Post by dracvs on 2008-09-20
> **tinny said:**
> Yep too many choices... I actually think that J2EE suffers far more in this area than .Net. Struts, Spring, JBoss Seam, Wicket, Stripes etc etc it just goes on and on.

If we just got behind say 2 frameworks, imagine how good they would be.

And that's what I have been trying to say all along!

.NET is a single framework in which you get out all of the functionality.

In contrast With Java, you need to go adding layers to get functionality, this is awesome because then you don't overload your project with unused layers and make it a lot more simple. but the initial Impact of the configuration for someone whos learning could be rather scary. Specially if you go adding layers upon layers

And yes, I do know Java, sadly i have been forced to work with it in some projects (rather large scale projects that I wish were done in .net for the sake of maintenance). I still don't like it but I think its a very nice language.


Oh and I wish I took pictures of the weird behaviour! I seriously can't point you to reproduce one of those because they were a thing of the moment and never repeated, but all things related to computers do that kind of thing. Wether is human error or not.

---

### Post by tinny on 2008-09-20
> **dracvs said:**
> 
And that's what I have been trying to say all along!

.NET is a single framework in which you get out all of the functionality.


This is where .Net wins and loses. It wins because you can just get straight into it and start coding without needing to do the research on what framework to use. It loses because you don't have a choice.

> **dracvs said:**
> 
In contrast With Java, you need to go adding layers to get functionality, this is awesome because then you don't overload your project with unused layers and make it a lot more simple. but the initial Impact of the configuration for someone whos learning could be rather scary. Specially if you go adding layers upon layers


These layers you talk of are not necessary, just because you have these tools (Session beans entity beans dependency injection) doesn't mean you have to use them. There is a time and place for them, but its not all the time.

> **dracvs said:**
> 
Oh and I wish I took pictures of the weird behaviour! I seriously can't point you to reproduce one of those because they were a thing of the moment and never repeated, but all things related to computers do that kind of thing. Wether is human error or not.

.Net and J2EE are both solid. We are not...

---

### Post by sakabato on 2008-09-20
The difference between Java and .net choices. Microft pushes new options vertically. So you generally know, new stuff tends to be better. If you have courage/time to learn them, you can learn, if not do as usual.

In java world since it is more community driven the choices grow horizontally. So it really becomes hard to choose best tool from the begining. This can cause confusion for idealist developers.

In any case there is nothing bad in sticking what  you know already as long as it does the job and fits the requirements.

---

### Post by tinny on 2008-09-20
> **sakabato said:**
> 
In any case there is nothing bad in sticking what  you know already as long as it does the job and fits the requirements.

This is a trap. You have got to keep your skills sharp and keep learning otherwise you turn into a [blub]("http://en.wikipedia.org/wiki/Blub#Blub"). All your life you learn and then you die, programming should be no different.

In programming if you don't continue to learn you become obsolete ;)

---

### Post by sakabato on 2008-09-20
> **tinny said:**
> This is a trap. You have got to keep your skills sharp and keep learning otherwise you turn into a [blub]("http://en.wikipedia.org/wiki/Blub#Blub"). All your life you learn and then you die, programming should be no different.

In programming if you don't continue to learn you become obsolete ;)

I personally agree with you. There is no point in using cobol. On the other hand you don't have time/energy to learn everything. I personally my self am trying to develop a "developer's eye" which is suppose to be selective for what to learn and what not. We have a saying here. "Try to learn one thing about everything and everything about one thing." That way you keep your vision widened but not dispersed. And a new question arises then "what is that one thing ?"

---

### Post by cprofitt on 2008-09-20
> **sakabato said:**
> i personally agree with you. There is no point in using cobol. On the other hand you don't have time/energy to learn everything. I personally my self am trying to develop a "developer's eye" which is suppose to be selective for what to learn and what not. We have a saying here. "try to learn one thing about everything and everything about one thing." that way you keep your vision widened but not dispersed. And a new question arises then "what is that one thing ?"

[size=5][b]
42[/b][/size]

---

### Post by LaRoza on 2008-09-20
> **tinny said:**
> This is a trap.

[img]http://seoblackhat.com/images/its-a-trap-admiral-akbar.jpg[/img]

> **sakabato said:**
> I personally agree with you. There is no point in using cobol. On the other hand you don't have time/energy to learn everything. I personally my self am trying to develop a "developer's eye" which is suppose to be selective for what to learn and what not. We have a saying here. "Try to learn one thing about everything and everything about one thing." That way you keep your vision widened but not dispersed. And a new question arises then "what is that one thing ?"

sakabato: This is a primarily open source oriented forum. The main focus isn't so much on staying hired, but by programming. Mediocre programmers churned out by code monkey factories are hired every day. A job is good. However, programming is beyond what the boss wants to most of us ;) Although some people here use Java at work (I am thinking of specific people, so don't feel I am picking on Java, for once), they learn and use other languages for their own benefit.

---

### Post by cprofitt on 2008-09-20
LaRoza:

I use C# at work... and am learning Python/C for my own benefit. I am in full rebellion.

---

### Post by tinny on 2008-09-21
> **PrivateVoid said:**
> LaRoza:

I use C# at work... and am learning Python/C for my own benefit. I am in full rebellion.

And I bet you find the approaches you learn with Python help you in your C# day job. 

Ive been hacking around with Groovy and Python at home lately, this is breathing new life into not only my passion for programming but helping me solve my 9 to 5 Java problems.

---

### Post by pmasiar on 2008-09-21
> **dracvs said:**
> And that's what I have been trying to say all along!

.NET is a single framework in which you get out all of the functionality.

.NET is "one size fits all" kind of framework. Sorry but I am strong believer in evolution and democracy, in competing ideas, and let the best idea win. I know better what solution fits better my needs and situation that guys in Redmond, however smart they pretend to be. Thanks but no thanks, I'll keep my messy freedom over your "Bill knows better" world.

---

### Post by tinny on 2008-09-21
> **pmasiar said:**
> .NET is "one size fits all" kind of framework. Sorry but I am strong believer in evolution and democracy, in competing ideas, and let the best idea win. I know better what solution fits better my needs and situation that guys in Redmond, however smart they pretend to be. Thanks but no thanks, I'll keep my messy freedom over your "Bill knows better" world.

YES!!!

Sometimes I need a hammer sometimes I need a screwdriver, I dont just want this everything tool I brought from the 24hr shopping network.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=86033&d=1222048524[/IMG]

---

### Post by pmasiar on 2008-09-21
+1

The best picture of .NET approach I ever seen :-)

---

### Post by dracvs on 2008-09-22
At least .net doesnt hate my flash files like Java does
Today I added a Flash file to a Normal Dynamic Website as they call it..

It worked fine. For 5 hours. (from 8:00 AM to 12:00 PM) No changes were made since 8:00 AM)

My boss opened it... and SUDDENLY the flash was gone. I spent the whole evening wondering what was wrong. Recompiled the EJB's, redid the flash implementation......

... and suddenly..it reappeared! at 7:00 PM without explanation. I just left it alone and it spitted it in the end.

And you dared to tell me it didn't have erratically crazy Server behavior? I just can't wait to see what I find...

---

### Post by CptPicard on 2008-09-22
> **dracvs said:**
> 
And you dared to tell me it didn't have erratically crazy Server behavior?

If you're suggesting this has something to do with J2EE application servers or J2EE in general, by all means, file a bug. Sounds so remarkably atrocious that Sun or whoever will be very grateful for you to report it :)

(In other words, problem is probably between keyboard and chair)

---

### Post by tinny on 2008-09-22
> **dracvs said:**
> At least .net doesnt hate my flash files like Java does
Today I added a Flash file to a Normal Dynamic Website as they call it..

It worked fine. For 5 hours. (from 8:00 AM to 12:00 PM) No changes were made since 8:00 AM)

My boss opened it... and SUDDENLY the flash was gone. I spent the whole evening wondering what was wrong. Recompiled the EJB's, redid the flash implementation......

... and suddenly..it reappeared! at 7:00 PM without explanation. I just left it alone and it spitted it in the end.

And you dared to tell me it didn't have erratically crazy Server behavior? I just can't wait to see what I find...

Look in the mirror and you will see your bug.

I think you really need to read this. (At some point I always seem to have to flick this link to the junior developers that I work with)

[http://www.codinghorror.com/blog/archives/000051.html](http://www.codinghorror.com/blog/archives/000051.html)

I sincerely hope that you learn to adapt your mind to its own inferiority. I too struggle with this every day, but at least at the end of the day I know im dumb.

---

### Post by dracvs on 2008-09-23
"Works for me" tm.

---

### Post by skeeterbug on 2008-09-23
A lot of you are forgetting there are *other* frameworks out there for .NET. However, we aren't forced to make the choice from the beginning if we don't want to.

---

### Post by themusicwave on 2008-09-23
> **tinny said:**
> I think you really need to read this. (At some point I always seem to have to flick this link to the junior developers that I work with)

[http://www.codinghorror.com/blog/archives/000051.html](http://www.codinghorror.com/blog/archives/000051.html)

I sincerely hope that you learn to adapt your mind to its own inferiority. I too struggle with this every day, but at least at the end of the day I know im dumb.

That was a great article and was worth a read.  I'm still new in this game so it is great advice.

I also don't feel as dumb now that I see that I am not the only one who has to say "No I can't" or "I don't know how, but I may be able to figure it out".

---

### Post by tinny on 2008-09-23
> **skeeterbug said:**
> A lot of you are forgetting there are *other* frameworks out there for .NET. However, we aren't forced to make the choice from the beginning if we don't want to.

Maybe you could point out a couple for us? I know of [Spring .Net]("http://www.springframework.net/"). I wonder if anyone here has used Spring .Net?

> **themusicwave said:**
> That was a great article and was worth a read.  I'm still new in this game so it is great advice.

I also don't feel as dumb now that I see that I am not the only one who has to say "No I can't" or "I don't know how, but I may be able to figure it out".

Its good that you're open to this. The true professionals know how to say "I dont know" because they are confident with their own ability.

---

### Post by LaRoza on 2008-09-23
> **tinny said:**
> 
Its good that you're open to this. The true professionals know how to say "I dont know" because they are confident with their own ability.

I agree. I also try to make that point when needed: [http://ubuntuforums.org/showpost.php?p=5814875&postcount=7](http://ubuntuforums.org/showpost.php?p=5814875&postcount=7)

---

### Post by skeeterbug on 2008-09-23
> **tinny said:**
> Maybe you could point out a couple for us? I know of [Spring .Net]("http://www.springframework.net/"). I wonder if anyone here has used Spring .Net?


Web Frameworks
[http://csharp-source.net/open-source/web-frameworks](http://csharp-source.net/open-source/web-frameworks)

ORM libraries
[http://csharp-source.net/open-source/persistence](http://csharp-source.net/open-source/persistence)

Microsoft released their own MVC pattern framework on top of asp.net as well.

---

### Post by dracvs on 2008-09-23
> **tinny said:**
>  Its good that you're open to this. The true professionals know how to say "I dont know" because they are confident with their own ability.

You know, that one was the first thing I was told in my first job as professional developer about 5 years ago. And it has worked great in my training!

My actual boss told me that "Dont believe you know. Say you don't know. It's easier to teach you what I know"

We should write a book

"when to say I dont know" by The Ubuntu Community

---

### Post by frankhevans on 2008-09-24
Would have to agree (then duck-n-cover) on mono. I'm very impressed. One thing many people overlook is the java/ikvm support. I'm moving into a development pattern of maintaining helper-classes in java, then exposing them in mono/.net via ikvm. That way, the classes are accessible in both the JRE and CLR.

---

### Post by tinny on 2008-10-01
> **skeeterbug said:**
> 
Microsoft released their own MVC pattern framework on top of asp.net as well.

Yeah, ive heard a little about this. Based on Rails, right?

---

### Post by skeeterbug on 2008-10-02
> **tinny said:**
> Yeah, ive heard a little about this. Based on Rails, right?

Yes, but rails didn't invent MVC. :P

---

