---
title: "What do you guys think about C# under linux?"
date: 2007-10-19
forum: Programming Talk
---

### Post by John2lhotal on 2007-10-19
Just wanted to get couple different feeback about coding in C#, does it got a future under linux?

Lemme know wat you think about it..

Thanx guys and girlz,

have a good day :)

---

### Post by Steveway on 2007-10-19
Nah, too risky and too many flaws.
All applications that use C# that I used, were really slow and use too much memory.
Tomboy, F-spot, Beagle, all big and slow.
I don't see a reason what is good on C#, portability? Yeah sure.

---

### Post by pmasiar on 2007-10-19
Adopting C# means, that every time MSFT decides it is time to shake users for some money to upgrade, and changes specs, you need to change your app too. And no reimplementation is 100%: to be 100% you need to copy also bugs and design errors. Real pain.

Why would sane person agree to follow convicted monopolist (known to destroy collaborating companies) if you can use free software, and lead?

If you want to use C#, use it on its native platform, where you don't have compatibility problems, and hope your app will not compete with MSFT, and if you do, you get bought out, and not squished.

---

### Post by FredB on 2007-10-19
> **John2lhotal said:**
> Just wanted to get couple different feeback about coding in C#, does it got a future under linux?

Lemme know wat you think about it..

Thanx guys and girlz,

have a good day :)

Let's hope no. Every single app in C# is big, slow, and very memory hungry.

I trashed beagle for tracker without any remorse.

---

### Post by bluedalmatian on 2007-10-20
Microsoft already have the Office file format as a defacto standard, what good does it do open source to help them cement another defacto standard?

Stick to open languages

---

### Post by emperon on 2007-10-21
I use C# with great success on Linux. And it provides me excellent portability with windows. Also current mono implementation is almost complete regarding .net 2.0 stack.

I personally highly recommend it over java and for general purpose programming.

---

### Post by ankursethi on 2007-10-21
As long as we have Novell pushing C# and Mono, we'll just have to live with it.

Sometimes I wonder : what is the difference between Mono and now open sourced Java? I mean, both of them are backed by large corporations who cannot really be trusted. In fact, Mono is probably safer to use than Java since Mono at least has some amount of community participation. We have seen with OpenOffice how much the community matters in Sun's OSS projects.

The arguments about Microsoft changing the specification are invalid. You could always use an older version of Mono which I'm sure will be supported by the community as long as there is demand for it.

So basically C# and Java both are evil, but C# is considerably less evil than Java. Yet, since C# is a Microsoft product, it therefore somehow becomes more evil than Java in the eyes of the community.

Wouldn't we be better off using Python and Ruby (and hoping that someday Parrot comes out)?

---

### Post by hecato on 2007-10-21
Yea, Im aproximating to python (also to haskell), and if you need portability Im sure python will do all the work you need (more than C# mono, because python already is there... ;) and like I know is more portable **NOW** to other plataforms as well not only PC compatibles or related, at less in portability like java is now... from what I can see now).

Dont know much about portability in Haskell, but Im sure that at less is like in C (that mean recompiling).

---

### Post by pmasiar on 2007-10-21
> **ankursethi said:**
> what is the difference between Mono and now open sourced Java? I mean, both of them are backed by large corporations who cannot really be trusted. In fact, Mono is probably safer to use than Java since Mono at least has some amount of community participation. We have seen with OpenOffice how much the community matters in Sun's OSS projects.

The arguments about Microsoft changing the specification are invalid. You could always use an older version of Mono which I'm sure will be supported by the community as long as there is demand for it.

So basically C# and Java both are evil, but C# is considerably less evil than Java. Yet, since C# is a Microsoft product, it therefore somehow becomes more evil than Java in the eyes of the community.


You need to read Sun-Tzu a little. **Of course** you never help one of your stronger opponents - you help the weaker. So from tactical POV, supporting Sun against MSFT makes sense. MSFT is considerably bigger, and considerably more evil towards free software community, how you cannot see that? Sun is battling MSFT where it hurts most: in office suite, and we need to help it where we can.

Also, from technical POV: with Java being GPL, it is in much stronger position than C#. Of course you can fork C# if MSFT introduces bad changes - but then you would lose all the compatibility, wouldn't you?

The only problem is, that C# is little better designed than Java. Oh well, who cares about such trifles?

---

### Post by YetAnotherNoob on 2007-10-21
I think C# is a great language that is far more productive than C++ or C.  And using mono .Net frameworks it can be more productive than Java (less code and less time).

As for who is evil, well thats all relative.  

Regarding performance: **All new languages are slow**.  Java, C and C++ were both critized when first developed.  However: over time optimizing compilers, faster runtimes, improved frameworks and design patterns were improved making them the sucesses they are.

C# is a born success.  It has massive backing (MSFT with cash) and 1000's of commercial software houses (currently using C++/MFC/ATL) to jump on board.  I think linux will support it.  Not because it should; but because the market demands it.

---

### Post by LaRoza on 2007-10-21
> **YetAnotherNoob said:**
> I think C# is a great language that is far more productive than C++ or C.  And using mono .Net frameworks it can be more productive than Java (less code and less time).

As for who is evil, well thats all relative.  


C# is more productive than C? That is relative to what and where you are programming. 

Most things can be more productive than Java, if you want that (less code and less time), Python which is very well supported on Windows and Linux and Macs et al, is a better choice.

True, MS's actions, are not evil from MS's perspective, but then again, all people can rationalize their actions if they perceive a greater gain than loss from an action. (Bentham's Calculus)

---

### Post by slavik on 2007-10-22
Mono != .NET

If you think that Mono is the .NET for linux, then I feel sorry for you. You either code for .NET or for Mono, not both (xor).

OS/2 was a better OS than Windows, but to be more widely accepted it included a Windows emulation stack. Then the developers decided to code for Windows and make OS/2 people worry about compatibility. This was the downfall of OS/2 once microsoft started breaking their own API. Talk to the WINE devs, they can tell you a thing or two. It's actually a good thing that Windows apps are not 100% compatible with WINE, because "These other guys made our app run on a platform we don't want to bother supporting" is not considered support.

When Sun was making Java, they wrote JVMs for the major OSs (Windows, Linux, Solaris). If you want an application hosted out of Java/.NET on a very big and fast system ... well Windows doesn't run on SPARC or on a 5000 CPU cluster.

Needless to say, nobody has to catch up when Java 7 gets released. Whereas Mono only has .NET 2.0 and .NET is not completely portable as you think. I have an application that simply doesn't run on Linux using Mono. It uses .NET 3.0 code.

Application's name is Evemon. Show me that it runs on Linux using Mono and then I will consider the Mono == .NET statement.

@YetAnotherNoob:
instead of comparing C# with C++ and C, why don't you compare it with COBOL typed on punchcards. It is a more of an apples to apples comparison. (could you tell the sarcasm?)

C# has backing ... the only reason that the "1000's of commercial software houses" are backing it is because there is "Microsoft" related to it. I happen to know that JPMorgan uses Java for their trading code and it is fast. (I do not work at or for JPMorgan)

C# is also Microsoft's second try at J++, remember that one?

EDIT:
@LaRoza, you are missing a language (that has great support everywhere), guess which one. ;)

---

### Post by LaRoza on 2007-10-22
> **slavik said:**
> 
EDIT:
@LaRoza, you are missing a language (that has great support everywhere), guess which one. ;)

Sorry, I have respect for Perl :), just forgot to write Python or Perl.

---

### Post by slavik on 2007-10-22
> **LaRoza said:**
> Sorry, I have respect for Perl :), just forgot to write Python or Perl.
damn straight :-P

---

### Post by emperon on 2007-10-22
> **slavik said:**
> Mono != .NET

No they are almost equal
> 
If you think that Mono is the .NET for linux, then I feel sorry for you. You either code for .NET or for Mono, not both (xor). 

Vast majority of programs (%99 of all applications excluding the ones using winforms) will  work on both of them.


> 
Needless to say, nobody has to catch up when Java 7 gets released. Whereas Mono only has .NET 2.0 and .NET is not completely portable as you think. I have an application that simply doesn't run on Linux using Mono. It uses .NET 3.0 code.


Mono is much more portable than you think. As long as you are not stuck to winforms 99% portability guaranteed.  .NET 3.0  is just a marketing trick. It uses  the same runtime .NET 2.0 same CLR code. Basically .NET 3.0 = .NET 2.0 + WCF  +WPF +WWF which are partially implemented on mono olive project.

> 
Application's name is Evemon. Show me that it runs on Linux using Mono and then I will consider the Mono == .NET statement.
The following applications I know runs on both : Rhino Mocks, NHibernate, Castle Project, NUnit (including its winforms), NClass (Winforms), Reflector (Winforms) , log4net, MBUnit, Almost all ASP.NET apps excluding the ones using web parts, Almost all console applications, almost all dlls, Iron python, IronRuby, Boo, F# ....

Those above work on mono and .net both on linux and windows


> 
C# is also Microsoft's second try at J++, remember that one?


True. But a  really successful try.
EDIT:

---

### Post by YetAnotherNoob on 2007-10-22
> **slavik said:**
> 
@YetAnotherNoob:
instead of comparing C# with C++ and C, why don't you compare it with COBOL typed on punchcards. It is a more of an apples to apples comparison. (could you tell the sarcasm?)

C# has backing ... the only reason that the "1000's of commercial software houses" are backing it is because there is "Microsoft" related to it. I happen to know that JPMorgan uses Java for their trading code and it is fast. (I do not work at or for JPMorgan)

C# is also Microsoft's second try at J++, remember that one?


Errm...all sarcasm aside I am not saying C and C# are directly related or comparable.  I am saying C and C++ compilers have improved over time.  The performance of mono and .net will also improve over time.

If you think C# will die like J++ you are wrong. J++ did not have the same kind of backing from MSFT.  J++ also had license/trust issues.  MSFT is betting the farm on C# and .NET.  It's success is **everything** to them.  That is why I think it will be a market success.  The almighty $ has a lot to do with success. :)

Just to clarrify: I understand mono is not important to linux, in the way .net is important to MSFT.

---

### Post by hecato on 2007-10-22
mmm, you accept that 1 thing that contradict a rule break the rule (mathematically is enough)?

> Vast majority of programs (%99 of all applications excluding the ones using winforms) will  work on both of them.> As long as you are not stuck to winforms 99% portability guaranteed.Im not C# programmer, but I learned some of it for a migration of a programm, I remember that by some extrange reasin Exit doesnt work the same way than in windows, in windows it break all the programm, in linux, I must first stop manually some threads and then exit, if not the threads of process continue or sometimes crashed randomly.

That is a difference not related to winforms.


Also there is no much meaning in having a "multiplataform language" if you take into account only 1 system (the defacto in this case MS Windows), like it doesnt matter case, paths (hardcoded and separators, permissions for port [windows let you run programms with ports under 1024, where a normal user in Lin cant] the install programm ask you for user and pass equal win installer and lin, but they are different win more like an admin, lin more like a real user not like and admin), etc.

Thus the portability is not guaranteed having a virtual machine (watever they call it with his own choosed name or "technology") at 100% implemented in all plataforms   (x86, 64, sparc, etc) and the OS in case, if the programmer only take into account characteristics of 1 platform ;).

---

### Post by emperon on 2007-10-22
> **hecato said:**
> mmm, you accept that 1 thing that contradict a rule break the rule (mathematically is enough)?

Im not C# programmer, but I learned some of it for a migration of a programm, I remember that by some extrange reasin Exit doesnt work the same way than in windows, in windows it break all the programm, in linux, I must first stop manually some threads and then exit, if not the threads of process continue or sometimes crashed randomly.

That is a difference not related to winforms.


Also there is no much meaning in having a "multiplataform language" if you take into account only 1 system (the defacto in this case MS Windows), like it doesnt matter case, paths (hardcoded and separators, permissions for port [windows let you run programms with ports under 1024, where a normal user in Lin cant] the install programm ask you for user and pass equal win installer and lin, but they are different win more like an admin, lin more like a real user not like and admin), etc.

Thus the portability is not guaranteed having a virtual machine (watever they call it with his own choosed name or "technology") at 100% implemented in all plataforms   (x86, 64, sparc, etc) and the OS in case, if the programmer only take into account characteristics of 1 platform ;).

Well don't be silly. Of course you will lose portability if you use P/Invoke or hard coded directory separators. Those are same for java and python too. We investigate the possibility of write once run everywhere. Still however programmer has the responsibility to be careful for cross platform issues

---

### Post by pmasiar on 2007-10-22
> **YetAnotherNoob said:**
> As for who is evil, well thats all relative.  


OK, kids, gather around me and I will tell you about old times, when evil MSFT was growing from 80 pounds gorilla to 800 and 8000 which is now.

[http://en.wikipedia.org/wiki/Criticism_of_Microsoft](http://en.wikipedia.org/wiki/Criticism_of_Microsoft)

[list]
[*] **OS/2**: MSFT was paid by IBM to develop OS/2 GUI, which they did (and learned making GUIs), but later dropped support to kill OS/2, Windows competitor.

[*] **DR-DOS**: [Digital Research](http://en.wikipedia.org/wiki/Digital_Research) was major OS provider (CP/M) for 8-bit office computers. CP/M ruled back then. Later, Novel bought (crushed) DR-DOS, and wanted to compete: Windows 3.0 run on top of DR-DOS better than on top of MS-DOS (because DR-DOS was better OS). MSFT added to Win3.0 beta hooks to checking binaries, and randomly crashed when running on DR-DOS. People stopped buying DR-DOS.

[*] **Monopoly**: Courts in USA and Europe found that not only MSFT is monopoly, but it abuses its monopoly position to crash competition.

[*] **Innovation**: Despite common belief, MSFT does not innovate. All major products were bought, including MS-DOS, FrontPage, Visio, HotMail (which run on BSD for a long time - Windows could not handle the traffic :-) ). The only original product was Basic compiler back in days, written in most part by Paul Allen BTW.

[*] **Killing startups**: venture capitalist will not fund any company which may compete with MSFT. Even MSFT announcement what they will develop competing product (waporware) will result in complete drying of secound round financing, forcing bankruptcy, or selling for cheap to MSFT.

[/list]

... and many more, but I don't want to bore you. 

Now go play, but remember: MSFT is evil, and will crash you if you come too close. Be careful!

---

### Post by hecato on 2007-10-22
> **emperon said:**
> Well don't be silly. Of course you will lose portability if you use P/Invoke or hard coded directory separators. Those are same for java and python too. We investigate the possibility of write once run everywhere. Still however programmer has the responsibility to be careful for cross platform issues


That is not being silly, Im argumentating that there is no sense in a "multiplataform language" if the developer doesnt take care to develop to more than 1 plataform.

And in fact the developer that do the programm I migrated do exactly that, develop a .NET 1 program that only take into account the characteristics of the defacto OS for .NET programs aka MS Windows.

And also Im sure that is the problem with major part of .NET, because I have listed arguments from programmers that know .NET but not MONO, thus ignoring (in some way) that they programms can run on Linux and they can develop in Linux for free (as we know now). Not all people that is MS know that there is a MONO implementation, thus they not necessarily think of Linux & Windows... that also will imply get some grasp with Linux for know a little best  the called by you "Still however programmer has the responsibility to be careful for cross platform issues".

Is like this...

When you learn a natural language, you should also think in that new language, if you have read some of my post, you will notice that Im not natal english speaker, that is because I don't think in English, I organize in my natal language and write the words in English. Thus hell yea!, Im speaking english but doing some extrange mix with the organization and flow of words. Is the same having a "multiplataform language" doesnt matter that it let you talk in some extend to "other plataforms", if you cant think in the other plataforms, thus probably you without see it will let them "out of the game".

Sillly is think that all programmers that write a .NET application think in Linux also with Windows in mind, even or at less in MONO, that is not true and I think it will not be true (doesnt matter that there are 100% compatibility in ECMA standar for the virtual machine), **if you dont think in the others, you probably will drop them doesnt matter that is a "multiplataform language"**.

> Those are same for java and python too.Read carefully... 
> **Also** there is **no much meaning** in _having a_ "multiplataform language" if you take into account only 1 system (the **defacto _in this case_ MS Windows**).

Thus the portability is not guaranteed having a virtual machine at 100% implemented in all plataforms and the OS in case, if the programmer only take into account characteristics of 1 platform
I not only include Java and Python, I have included all "multiplataform languages".

> 
Of course you will lose portability if you use P/Invoke or hard coded directory separators.
Of course _you assume_ that _*language portability*_ **mean** _*programm portability*_. And that in the more deep mean that _**all**_ programmers know the other platforms and care of them. In the program I migrate, the other programmer didn't know Linux at all also don't care if it exist or can work there (Windows expert or so like that) also didnt know of MONO and is ECMA implementation... thus you dont need to use P/Invoke or hardcode separators, **you only need to be ignorant** (not more not less) of the other platforms for trash the concept of language and program portability [COLOR=DarkSlateBlue][also by the way, you see MS is not here doing evil, at less directly, is enough if you ignore the others ;)][/COLOR].

Also Im near to sure because I really dont know at extend C#, that you can write a portable application (Linux and Windows) tht use PInvoke, thus showing clearly that PInvoke isnt the source of those "issues". Also Im sure I can write a program with hardcoded paths portable or say runnable for Windows and Linux, the source is not that (can be a tricky cause), **the source is IGNORANCE**.

Want a proof???? really??
[http://msdn.microsoft.com/msdnmag/issues/07/07/ShareCode/default.aspx](http://msdn.microsoft.com/msdnmag/issues/07/07/ShareCode/default.aspx)

O!!!! say me the programms that have you write take into account that they can also be run in for the example of msdn on movile devices... haha your application doesnt run there??, you cant compile your programm for it?, you see **ignorance**, and for be more specific see the first point in the content is "Platform differences"... I guess with all I tried to explain and that for some people **is silly** you dont need to guess why in that article first is listed the "Platform differences". [COLOR=DarkSlateBlue][In fact havent read the article, but I have readed the first words there now... "For the last several years, while developers were building Microsoft® .NET Framework client applications for Windows®, many had no idea that they could also have been creating applications for Windows Mobile® using the same skills and toolsets. But Windows Mobile wasn&#8217;t as widespread in the enterprise then, so the need to write custom applications targeting mobile devices was not as great. Today, there&#8217;s a huge demand and many desktop developers are getting their feet wet with mobile development. Unfortunately, many miss the opportunity to share their .NET code cross-platform even though it is relatively easy to do so."[/COLOR]] and that is a proof by the "experts at MS", not me that say silly things because Im not know or trust like the msdn can be.

Explanation "many had no idea" equals ignorance.
Explanation "Unfortunately, many miss the opportunity to share their .NET code cross-platform even though it is relatively easy to do so." equals ignorance and language portability doesnt mean magic program portability, if and only if the programmer care of the differences, thus yea, you have language portability equals programm portability.
Explanation "Today, there&#8217;s a huge demand and many desktop developers are getting their feet wet with mobile development." if mono doesnt get enought demand... thus it will not attract the persons of the defacto OS for .NET development.

---

### Post by xtacocorex on 2007-10-22
You're all forgetting that C# is itself a standardized language with non-standard implementation by the hand of Microsoft.  There is nothing stoping anyone from writing a proper implementation of C# without the .NET proprietary stuff.

---

### Post by aks44 on 2007-10-22
> **xtacocorex said:**
> C# is itself a standardized language

What's the ISO document reference?


EDIT: nvm, found it... it is ISO/IEC 23270.

---

### Post by pmasiar on 2007-10-22
> **xtacocorex said:**
> You're all forgetting that C# is itself a standardized language with non-standard implementation by the hand of Microsoft.  There is nothing stoping anyone from writing a proper implementation of C# without the .NET proprietary stuff.

How it is relevant if MSFT decides it is time to "improve" standards "to provide better value for our users"? Ie: OOXML is obviously much more convoluted (and likely impossible to implement) than cleaner ODF document standard, but how it is relevant to MSFT? MSFT knew well all the time ODF is being created (MSFT representative was on the standard group), and ignored it, and now want to force on us another, different standard. Standards are good: the more of them we have, the better we are, right? :twisted:

Don't fool yourself that MSFT will be bond by their own standards: they broke them before if it was useful to fight past competition, and they will do it again if they feel like it. 

Obviously you did not paid attention to the scary tale I told before :-)

---

### Post by aks44 on 2007-10-22
> **pmasiar said:**
> Don't fool yourself that MSFT will be bond by their own standards: they broke them before if it was useful to fight past competition, and they will do it again if they feel like it.

+1


FWIW it seems that version 3 of C# is currently being standardized (the first version was in 2003). Note the dubious habit of systematically using the fast track process, which ensures that the proposal is not really scrutinized...

Compare that to something like C++, which is currently undergoing its third revision too... since 1983! (1998, 2003, ??) :-\"

---

### Post by slavik on 2007-10-23
C# is a standard, does MS keep that standard?

C++ and C are ISO standards, too. For a company the size of Microsoft, they have a very non-standard compiler.

Java, as opposed to C# actually has proper libraries on all platforms. :)

---

### Post by NeoOblitus on 2007-10-23
:lolflag: Would everyone code in Assembly and get along :lolflag:

---

### Post by xtacocorex on 2007-10-23
> **pmasiar said:**
> How it is relevant if MSFT decides it is time to "improve" standards "to provide better value for our users"?
I don't think improve is the right term... :)
> Obviously you did not paid attention to the scary tale I told before :-)
I did not.
 
I merely mentioned the standard part of the language to get people to think that C# isn't .NET. I doubt it's working, but whatever. I'll now clamber down back into my FORTRAN hole.

---

### Post by LaRoza on 2007-10-23
> **NeoOblitus said:**
> :lolflag: Would everyone code in Assembly and get along :lolflag:

For a new user, this could be spam, but I am assuming it is a joke.

Assembly would make things worse. You would have to completely rewrite the pogram for each platform and OS. That is why C was invented.

---

### Post by pmasiar on 2007-10-23
> **xtacocorex said:**
> I merely mentioned the standard part of the language to get people to think that C# is .NET. 

IMHO there are three kinds of people related to this question: 
- without the (bitter) experience, who drinks MSFT kool-aid and believe its marketoids;
- with the experience making cross-platform apps work (and with working knowledge of workarounds around MSFT non-compliant implementation of standards);
- people so far totally immersed in MSFT world without cross-platform experience.

Fortunately, monopoly abuse of users is coming to the end, thank you Europe protecting users when USA does not care about enforcing own laws against monopolies. MSFT will still try to play every dirty trick they can pull, but they **are** forced to open API to allow interoperability. Will be (not) funny to see how many thousand pages API docs is - they claimed they don't have any docs, just code, that's why they cannot comply. Now they are forced to produce Windows API docs.

Thinking about it, maybe they **really** don't have API docs. That would explain poor quality of their software, don't you think so?

So, not for me. I do not trust MSFT ability to comply with standards. The only standards they like are 'de facto': the one implemented by their code, so everybody else is forced to re-create their sometimes broken functionality, bugs and warts included. Think about audacity of it, suggesting to standardize bugs in their code: instead of fixing them, requiring others to reimplement them.

Just say no to C# if you can avoid it.

---

### Post by YetAnotherNoob on 2007-10-23
> **pmasiar said:**
> 
Thinking about it, maybe they **really** don't have API docs. That would explain poor quality of their software, don't you think so?
Just say no to C# if you can avoid it.

With respect you don't know much about MS programming.  MS has some of the most complete API docs in the world.  [msdn.microsoft.com](msdn.microsoft.com)
AND Available in most major languages.  Their documentation is vastly superior to linux documentation.  However, they do not have a warm and open community like here @ ubuntuforums :)

MS sucks, we all know it.  We would not be hereotherwise.
:guitar:

---

### Post by xtacocorex on 2007-10-23
@pmasiar, I screwed up my second to last sentence in my last post, the is was supposed to be isn't.  
 
I don't know C# and will never use it.
 
This is the second thread I've tried to impart wisdom about C# and have it not work.  Never again I say; I am to avoid C# threads.

---

### Post by slavik on 2007-10-23
MSDN has great API docs??? Whatever you are smoking, I'd like some, too.

Challenge, complete reference to ADSI providers. :)

---

### Post by kentl on 2007-10-23
I like C# as a language and think that it's really neat. But I dislike that parts of it (the class library really, but I count it into the language in this case) are proprietary and might turn into legal actions from Microsoft against Mono. The negative aspect is enough for me to never use it in any of my hobby projects which I want to run on Linux. The positive aspect is enough for me to accept working with it professionally.

---

### Post by skirkpatrick on 2007-10-23
Well, I can tell you this much about the company I now work for (about 6 months).  They have been a MS house for a very long time.  Almost everything is written in either VB6 or VS.  Now that MS is ending support for those development environments and we are now looking at running our code on multiple OSes, we had to make a decision: completely rewrite everything for the new .NET environment or use a new development environment.  Since you can't just convert the old projects into .NET no matter what MS tells you and there will be some point in the future when MS pulls the rug out from under .NET (our software has a lifetime of at least 10 years), we decided to go with wxWidgets using GCC tools.  This allows us to run on Windows, Linux, and Mac.  We are also looking at writing some of our software in Python.

---

### Post by pmasiar on 2007-10-23
> **YetAnotherNoob said:**
> With respect you don't know much about MS programming.  MS has some of the most complete API docs in the world.  

I used those docs, for a while I even worked for authorized MSFT reseller (luckily not anymore). I do not argue they don't provide decent docs for third-party developers: if they did not, ppl would not be able to buy  developer tools they sell, right?

Apparently not all people are as obsessed to follow groklaw as I am, so you did not noticed facts I glanced. Let me put little more details (no links, I assume you just trust me :-) ).

My argument (if you followed what I wrote) was, that MSFT argued before European commission (investigating their anti-competitive behavior) asking them to open Windows internal APIs to competition (like Samba), that they cannot - MSFT does not have the docs, only the sources, and commission cannot (should not) force to reveal the sources. Were they lying to said commission, trying to fight off multi-hundred million dollars fine? Or they **really** don't have the docs? Your guess is as good as mine. 

Either way it is obvious to me that  I cannot trust MSFT. They have obviously in mind interests of MSFT stockholder first, and customers as distant fourth (after CEOs and employees). As I am not a MSFT stockholder, there is nothing good in it for me.

BTW C# is half-decent language (slightly improved Java), Silverlight is interesting technology, what they do with IronPython and kernel (CLI? IIRC) for dynamically typed languages is really hot, etc. But it does not matter, I do not trust MSFT and will prefer to use technology from other sources, where I may have a chance that they have also **my** interest in mind. MSFT lost any of my confidence.

Edit: fresh links: [http://lwn.net/Articles/255396/](http://lwn.net/Articles/255396/) and [http://www.groklaw.net/article.php?story=20071022114731199](http://www.groklaw.net/article.php?story=20071022114731199)

---

### Post by hecato on 2007-10-23
haha, I read from time to time [http://www.groklaw.net/](http://www.groklaw.net/)

> **aks44 said:**
> +1


FWIW it seems that version 3 of C# is currently being standardized (the first version was in 2003). Note the dubious habit of systematically using the fast track process, which ensures that the proposal is not really scrutinized...

Compare that to something like C++, which is currently undergoing its third revision too... since 1983! (1998, 2003, ??) :-\"

yay, very good point!!!!!!!!!!!! ad infinitum

I personally trust more C++ than C#, even that like I remember MS is also there.


From this point of view, I will like to ask, what others ISO standards have this approach I mean in 2003, 2004, 2005, 2006, to this day 3 versions, 7 years 3 versions. Now the question is, why need a ISO standard need a new version? Like I see you are supposed to have a standard for use it... stabilize is usage not? how many people (that really know the lang) now write applications for only .NET 1?


> 
Assembly would make things worse. You would have to completely rewrite the program for each platform and OS. That is why C was invented.
At less there are projects like [http://flatassembler.net/](http://flatassembler.net/) that can run and compile/assemble itself in Linux/Windows, havent tracked from time to now that project, but I remember that run in some other platform and the author claim that is very portable to other new OSs (like [http://www.menuetos.net/](http://www.menuetos.net/) IIRC).

Only for a side note about that, I remember some like "the bad thing that all research and push in the industry is about POO, that procedural languages have lost that investigation, like no investigation of patters and new technologies" perhaps in this page [http://www.geocities.com/tablizer/oopbad.htm](http://www.geocities.com/tablizer/oopbad.htm)

Anyway...
> **pmasiar said:**
> IMHO there are three kinds of people related to this question: 
- without the (bitter) experience, who drinks MSFT kool-aid and believe its marketoids;
- with the experience making cross-platform apps work (and with working knowledge of workarounds around MSFT non-compliant implementation of standards);
- people so far totally immersed in MSFT world without cross-platform experience.

Fortunately, monopoly abuse of users is coming to the end, thank you Europe protecting users when USA does not care about enforcing own laws against monopolies. MSFT will still try to play every dirty trick they can pull, but they **are** forced to open API to allow interoperability. Will be (not) funny to see how many thousand pages API docs is - they claimed they don't have any docs, just code, that's why they cannot comply. Now they are forced to produce Windows API docs.

Thinking about it, maybe they **really** don't have API docs. That would explain poor quality of their software, don't you think so?

So, not for me. I do not trust MSFT ability to comply with standards. The only standards they like are 'de facto': the one implemented by their code, so everybody else is forced to re-create their sometimes broken functionality, bugs and warts included. Think about audacity of it, suggesting to standardize bugs in their code: instead of fixing them, requiring others to reimplement them.

Just say no to C# if you can avoid it.

Like I have explained in my previous post and with proofs even from the msdn... **language portability doesn't mean programme portability**. Because you always neeed to know the differences or "take care" points in other words take into account the others (and the first part is about that).[LIST]
[*]Also let me remember cross-platform languages I know... java (o yea they have a virtual machine that they develop on their own and runs in a mirad of different systems, Linux, Mac OS, SUN OS, etc)
[*]C/C++ (mmm, Intel have a compiler that run not only in Win, but lin and also a version-1 on mac)... (also there is GCC and the standard lib, they run on a mirad of OS and platforms and output formats... I personally think that is why Debian is the most large between platforms GIANT [http://www.us.debian.org/releases/stable/](http://www.us.debian.org/releases/stable/) that is)... hell yea, C/C++ can be cross platform (not only what is "sold like that")
[*][http://python.org/](http://python.org/) page: "Python runs on Windows, Linux/Unix, Mac OS X, OS/2, Amiga, Palm Handhelds, and Nokia mobile phones. Python has also been ported to the Java and .NET virtual machines.", haha, even to .NET
[*][http://haskell.org/](http://haskell.org/) (this is new for me like is Python) for GHC de defacto standar here we go [http://hackage.haskell.org/trac/ghc/wiki/Platforms](http://hackage.haskell.org/trac/ghc/wiki/Platforms) and also are other implementations out there.[/LIST]thinking...[LIST=1]
[*]They are all crossplatform (perhaps some of them not like MS shold the concept)
[*]They all from SUN, GCC, Debian (because languages are not the only things that can be crossplatform), to haskel and python are working themselves in support the different architectures.
[*]Dont know if they have a standar somewhere??, but at less C and C++ have it, dont know about Java, Python and Haskel
[*]But then if they wellcome anyother having a public standar (like python **[PEPS and source code]** and Haskell **[Haskell 98 report and source code]**), but THEY are also working in the support of different platforms
[*]MS only have a ISO or ECMA (or whatever thing they call that), but **MS is not working!!! in the self proclaimed CROSS-PLATFORM!!!**... thus they wanted from start that some 1 (like Miguel the Icaza) started some open source for they to proclaim "you see there, we have an ISO and like Miguel de Icaza show to us now, it can be crossplatform" and **until this day, MS is not working in the OH SO WONDERFULL CROSSPLATFORM**!, _**PWNAGE!. o yea yea MS you are God (because you have a crossplatform product **_[In fact they only have a spec, NOT A CROSSPLATFORM PRODUCT]_**)**_.
[*]From what I see, anyone can publish a paper (let it be ISO, ECMA or other sh*t) and proclaim that your new wonderfull language is crossplatfom, and star working only for your own platform ***AND THAT IS NOT CROSSPLATFORM***, for me, crossplatform mean that _**YOU**_ yea the _"THING"_ that ***_write it is CROSSPLATFORM_*** ***_(only because the spec and design let you)_*** are working for it, not only saying "yea my product is crossplatform, but I not work in any other platform that is not the **MINE and ONLY MINE**".[/LIST]In other words, until I not see a .NET from MS free to all (not Mono thingies), his product is not really crosplatform, because they are not working for it, they only publicate a paper and continued in IS WORK without really take care of the self proclaimed crossplatform, in fact his own product is not crossplatform you need a thing like "Mono" for run it, but GHC by example can run progamms in Lin/Win being the same provider (I see real crossplatform there).

BTW, good points those about "ops we dont have documments sorry :'(", lol.

---

### Post by slavik on 2007-10-23
> **hecato said:**
> haha, I read from time to time [http://www.groklaw.net/](http://www.groklaw.net/)



yay, very good point!!!!!!!!!!!! ad infinitum

I personally trust more C++ than C#, even that like I remember MS is also there.


From this point of view, I will like to ask, what others ISO standards have this approach I mean in 2003, 2004, 2005, 2006, to this day 3 versions, 7 years 3 versions. Now the question is, why need a ISO standard need a new version? Like I see you are supposed to have a standard for use it... stabilize is usage not? how many people (that really know the lang) now write applications for only .NET 1?


At less there are projects like [http://flatassembler.net/](http://flatassembler.net/) that can run and compile/assemble itself in Linux/Windows, havent tracked from time to now that project, but I remember that run in some other platform and the author claim that is very portable to other new OSs (like [http://www.menuetos.net/](http://www.menuetos.net/) IIRC).

Only for a side note about that, I remember some like "the bad thing that all research and push in the industry is about POO, that procedural languages have lost that investigation, like no investigation of patters and new technologies" perhaps in this page [http://www.geocities.com/tablizer/oopbad.htm](http://www.geocities.com/tablizer/oopbad.htm)

Anyway...


Like I have explained in my previous post and with proofs even from the msdn... **language portability doesn't mean programme portability**. Because you always neeed to know the differences or "take care" points in other words take into account the others (and the first part is about that).[LIST]
[*]Also let me remember cross-platform languages I know... java (o yea they have a virtual machine that they develop on their own and runs in a mirad of different systems, Linux, Mac OS, SUN OS, etc)
[*]C/C++ (mmm, Intel have a compiler that run not only in Win, but lin and also a version-1 on mac)... (also there is GCC and the standard lib, they run on a mirad of OS and platforms and output formats... I personally think that is why Debian is the most large between platforms GIANT [http://www.us.debian.org/releases/stable/](http://www.us.debian.org/releases/stable/) that is)... hell yea, C/C++ can be cross platform (not only what is "sold like that")
[*][http://python.org/](http://python.org/) page: "Python runs on Windows, Linux/Unix, Mac OS X, OS/2, Amiga, Palm Handhelds, and Nokia mobile phones. Python has also been ported to the Java and .NET virtual machines.", haha, even to .NET
[*][http://haskell.org/](http://haskell.org/) (this is new for me like is Python) for GHC de defacto standar here we go [http://hackage.haskell.org/trac/ghc/wiki/Platforms](http://hackage.haskell.org/trac/ghc/wiki/Platforms) and also are other implementations out there.[/LIST]thinking...[LIST=1]
[*]They are all crossplatform (perhaps some of them not like MS shold the concept)
[*]They all from SUN, GCC, Debian (because languages are not the only things that can be crossplatform), to haskel and python are working themselves in support the different architectures.
[*]Dont know if they have a standar somewhere??, but at less C and C++ have it, dont know about Java, Python and Haskel
[*]But then if they wellcome anyother having a public standar (like python **[PEPS and source code]** and Haskell **[Haskell 98 report and source code]**), but THEY are also working in the support of different platforms
[*]MS only have a ISO or ECMA (or whatever thing they call that), but **MS is not working!!! in the self proclaimed CROSS-PLATFORM!!!**... thus they wanted from start that some 1 (like Miguel the Icaza) started some open source for they to proclaim "you see there, we have an ISO and like Miguel de Icaza show to us now, it can be crossplatform" and **until this day, MS is not working in the OH SO WONDERFULL CROSSPLATFORM**!, _**PWNAGE!. o yea yea MS you are God (because you have a crossplatform product **_[In fact they only have a spec, NOT A CROSSPLATFORM PRODUCT]_**)**_.
[*]From what I see, anyone can publish a paper (let it be ISO, ECMA or other sh*t) and proclaim that your new wonderfull language is crossplatfom, and star working only for your own platform ***AND THAT IS NOT CROSSPLATFORM***, for me, crossplatform mean that _**YOU**_ yea the _"THING"_ that ***_write it is CROSSPLATFORM_*** ***_(only because the spec and design let you)_*** are working for it, not only saying "yea my product is crossplatform, but I not work in any other platform that is not the **MINE and ONLY MINE**".[/LIST]In other words, until I not see a .NET from MS free to all (not Mono thingies), his product is not really crosplatform, because they are not working for it, they only publicate a paper and continued in IS WORK without really take care of the self proclaimed crossplatform, in fact his own product is not crossplatform you need a thing like "Mono" for run it, but GHC by example can run progamms in Lin/Win being the same provider (I see real crossplatform there).

BTW, good points those about "ops we dont have documments sorry :'(", lol.

Sorry for pointing out some of the spelling mistakes you, but this post is right on the money, especially with the anger and emphasis. You took this right out of my head. :)

THANK YOU! :popcorn:

---

### Post by YetAnotherNoob on 2007-10-24
> **skirkpatrick said:**
> Well, I can tell you this much about the company I now work for (about 6 months).  They have been a MS house for a very long time.  Almost everything is written in either VB6 or VS.  Now that MS is ending support for those development environments and we are now looking at running our code on multiple OSes, we had to make a decision: completely rewrite everything for the new .NET environment or use a new development environment.  Since you can't just convert the old projects into .NET no matter what MS tells you and there will be some point in the future when MS pulls the rug out from under .NET (our software has a lifetime of at least 10 years), we decided to go with wxWidgets using GCC tools.  This allows us to run on Windows, Linux, and Mac.  We are also looking at writing some of our software in Python.

I want your job.  :)
I am currently stuck in an MS pos.

Slavik:
Is this what you are after  :)
[http://msdn2.microsoft.com/en-us/library/aa772235.aspx](http://msdn2.microsoft.com/en-us/library/aa772235.aspx)
But seriously, I know what you mean.  MSFT documents the interfaces **they** want us to use, not what **we** want to use.  A classic example for me is the massive amount of documentation on MFC, but almost none (and low quality) of their STL implementation (which is not standard *ironic*).
:(

---

### Post by slavik on 2007-10-24
> **YetAnotherNoob said:**
> I want your job.  :)
I am currently stuck in an MS pos.

Slavik:
Is this what you are after  :)
[http://msdn2.microsoft.com/en-us/library/aa772235.aspx](http://msdn2.microsoft.com/en-us/library/aa772235.aspx)
But seriously, I know what you mean.  MSFT documents the interfaces **they** want us to use, not what **we** want to use.  A classic example for me is the massive amount of documentation on MFC, but almost none (and low quality) of their STL implementation (which is not standard *ironic*).
:(
I still don't see the docs how winmgmts://./Administrators gets you the administrators group on the current system.

here's another one, when adding a user to a group which he is part of, the VBscript crashes on the add, so I have to check for him before I add. and on error resume next is not what I want (since I need to know that there was an error). double the work, double the "fun" ...

---

### Post by YetAnotherNoob on 2007-10-24
> **slavik said:**
> ... double the work, double the "fun" ...

:) good luck!

---

### Post by emperon on 2007-10-24
Stop spreading FUD. Learn the facts. C# and Core library of .NET framework is not a property of Microsoft. The only patented technologies are Windows Forms , ASP.NET and ADO.NET. You can definitely develop applications without those. And as long as you don't use these you are 100% safe.
And finally Mono is Open Source , Java is NOT (Java 7 has not been released which will then later be named Open Java or Open JDK and sun will also promote its own Java version )

taken from : [http://www.mono-project.com/FAQ:_Licensing](http://www.mono-project.com/FAQ:_Licensing)
**Could patents be used to completely disable Mono?**

First some background information.

The .NET Framework is divided in two parts: the ECMA/ISO covered technologies and the other technologies developed on top of it like ADO.NET, ASP.NET and Windows.Forms.

Mono implements the ECMA/ISO covered parts, as well as being a project that aims to implement the higher level blocks like ASP.NET, ADO.NET and Windows.Forms.

The Mono project has gone beyond both of those components and has developed and integrated third party class libraries, the most important being: Debugging APIs, integration with the Gnome platform (Accessibility, Pango rendering, Gdk/Gtk, Glade, GnomeUI), Mozilla, OpenGL, extensive database support (Microsoft only supports a couple of providers out of the box, while Mono has support for 11 different providers), our POSIX integration libraries and finally the embedded API (used to add scripting to applications and host the CLI, or for example as an embedded runtime in Apache).

The core of the .NET Framework, and what has been patented by Microsoft falls under the ECMA/ISO submission. Jim Miller at Microsoft has made a statement on the patents covering ISO/ECMA, (he is one of the inventors listed in the patent): here ([http://web.archive.org/web/200304241.../msg00218.html](http://web.archive.org/web/200304241.../msg00218.html))

Basically a grant is given to anyone who want to implement those components for free and for any purpose.

For people who need full compatibility with the Windows platform, Mono's strategy for dealing with any potential issues that might arise with ASP.NET, ADO.NET or Windows.Forms is: (1) work around the patent by using a different implementation technique that retains the API, but changes the mechanism; if that is not possible, we would (2) remove the pieces of code that were covered by those patents, and also (3) find prior art that would render the patent useless.

Not providing a patented capability would weaken the interoperability, but it would still provide the free software / open source software community with good development tools, which is the primary reason for developing Mono.

The patents do not apply in countries where software patents are not allowed.

For Linux server and desktop development, we only need the ECMA components, and things that we have developed (like Gtk#) or Apache integration.
With the new Novell/Microsoft agreement, will the patent policy change?

Mono is a community project, and as such, we will continue to implement the policy of not integrating knowingly infringing code into Mono.

And we will continue to follow the steps outlined in the previous topic if code that potentially infringes is found: finding prior art, finding different implementation techniques, or if none of those are possible, removing the code from Mono.
[B]
---------------------------------------------------------------------------------------[/B]
Programming languages are tools. And they give us some abstraction level. I would classify :

Language....................... Abstraction Level

Machine Lang........................ 0
Assembly.............................. 1
C/C++ ................................... 2
Java/C# .................................3
Python, Ruby .........................4
LISP ...................................infinity

We choose a language according the to task and level of abstraction we require. Writing an operating system with LISP is pointless where as, writing an ERP with assembly is pointless as well.

Most Projects fall into the category between level 4 and 3. The main difference between level 4 and 3 is about statically typing or dynamic typing.

With statically typed languages you have compiler as a cop , that checks your code for preliminary compile time mistakes. This is more useful when the project is very large and iti hard to maintain and/or the developers are novice.

With dynamic languages, the language gives the developer more power (at the cost of Performance) , so it is more suitable for when developers are smarter and/or Project is not very large to maintain.

What .NET brings table, this is highly personal. Mono (and not .NET) is the best of the best of all development environments FOR ME. because of the following reasons:

1-) You have bunch of languages with dynamic and static typing that can interop: C#, VB.NET(it sucks I know), Boo (a statically typed language allowing dynamic typing), IronPyton, IronRuby(alpha available),Ruby.NET (Beta availbale), F# (first class functional language) and a lot of less popular ones like nemerle, lispdotnet, prolog.net...

2-) .NET framework is available in windows and gnome by default. Have you ever tried to deliver a python application to your customer who knows nothing about computers ? You cannot instruct them to install python easily. Even if you can sometimes deployment of 1000 computers are problematic. Most XP and all Vista computers already has .NET framework so it is easier to deploy cross platform applications

3-) java is the most popular language now according to TIOBE index: [http://www.tiobe.com/tpci.htm](http://www.tiobe.com/tpci.htm) But popularity does not make a language good (For eg. VB). Although .NET especially c# is highly inspired of java ( the reason C# was born because sun sued Microsoft for Visual J++), for many years, Sun's over protective behavior of java, damaged java community a lot. If you check the bug list of java you will see there are 3 - 4 years standing bugs. GUI development with java sucks.Although Sun recenlty Open sourced java recently , as everything Sun did so far, it is too little and too late. Java is destined to go where PHP and Cobol lies now

4-) Web Development with mono is breeze. What other choices we have ?
Java based framworks (look at item 3), PHP (is already dead), Ruby on Rails (this is a very nice framework but sorry not suitable for large applications, No unicode, no multithreading), Pythonic Frameworks like Django and Turbo Gears, these are also very nice but they are even worse than RoR. Still very nice for small to medium web development

5-) .NET library is large. Python library is also large, and available C librarires are huge. But with .NET you got all in one

6-) You've got the power of frameworks written for windows, like nhibernate, spring.net, db4o, nunit ...

7-) You've got the power of Java frameworks via IKVM. IKVM is a Java VM which can run on mono

Although it is Alpha, we've got Silverlight/moonlight: [http://www.mono-project.com/Moonlight](http://www.mono-project.com/Moonlight)

Note that I am not claiming Mono is better than Python.
These are my opinions what for Mono brings to the table

---

### Post by Capricori on 2007-11-18
Ok, I'd like to bet that I have the least programming experience, or knowledge, of anyone on this thread. I've been using C# for about 2 months (my University's choice, not mine), and writing Bash scripts for about three months. That's all I've done.

From the perspective of a complete noob (me), C# is a decent first language... it tries to stop you from doing some stupid things, which other languages would happily compile, and learning C# should make it easier to learn C, C++ etc.

However, as a Linux user, I would much rather do things in Bash, and I've yet to find anything I can do in C#, that I can't do in Bash (I'm sure they exist though)

Various posts indicate that Microsoft may or may not control C#, but either way, Microsoft are involved. And where they're involved, I tend to apply Murphy's Law - "Anything that can go wrong, will go wrong".

Either way, whilst C# might flourish, I doubt it'll feature heavily in Linux. Just my opinion :D

---

### Post by j_g on 2007-11-19
> **pmasiar said:**
> OK, kids, gather around me and I will tell you about old times

...none of it having to do with the OP's question, nor even programming in general.

Is there something wrong with advocacy newsgroups such that people must instead have those conversations here?

---

### Post by LaRoza on 2007-11-19
> **j_g said:**
> ...none of it having to do with the OP's question, nor even programming in general.


That was many pages back, and the discussions are very dynamic in this forum, so it isn't really random.

---

### Post by j_g on 2007-11-19
> **LaRoza said:**
> the discussions are very dynamic in this forum

Much too "dynamic"... when a post in this forum isn't even about programming, and is just an MS bashing "advocacy post".

---

### Post by LaRoza on 2007-11-19
> **j_g said:**
> Much too "dynamic"... when a post in this forum isn't even about programming, and is just an MS bashing "advocacy post".

The posters dicussion of MS was entirely factual, and gave the reasons why relying on MS was risky. Although everybody is free to develop on and for MS using their own tools, it has certain elements not found in using other languages, platforms, and tools, with the advantage of having a more widely used OS and a consistant IDE.

---

### Post by pmasiar on 2007-11-19
> **j_g said:**
> ...none of it having to do with the OP's question, nor even programming in general.


OP asked me what I think about developing with C#. I mentioned couple facts from history of MSFT, why I think that developing with C# might involve similar risks.

You obviously cannot refute the facts, so decided to attack messenger instead. Such is life on forums. :-(

---

### Post by j_g on 2007-11-19
> **LaRoza said:**
> The posters dicussion of MS was entirely factual.

That's disputable. But what isn't disputable is that a discussion of MS' business history is not a discussion about programming. And the OP didn't ask about MS at all. Why are moderators locking relevant discussion left and right, while clearly allowing continued, off-topic discussion by habitual offenders of such?

---

### Post by ThinkBuntu on 2007-11-19
[LIST=1]
[*]C# isn't a Microsoft product
[*]Banshee is an example of a good program using Mono
[/LIST]

---

### Post by pmasiar on 2007-11-19
> **j_g said:**
> a discussion of MS' business history is not a discussion about programming.

At least OS/2 and DR-DOS entries are directly relevant to anyone interested in MSFT history of interoperability with competing products. Not encouraging, and no improvements in sight.

> And the OP didn't ask about MS at all. 

OP asked if "C#, does it got a future under linux"?

My method to try predict future is to look into past and extrapolate. What is yours?

> Why are moderators locking relevant discussion left and right, while clearly allowing continued, off-topic discussion by habitual offenders of such?

What makes your opinion of what is "right", "on-topic" and even "habitual offender" more relevant than opinion of other people?

---

### Post by pmasiar on 2007-11-19
> **ThinkBuntu said:**
> 
[*]C# isn't a Microsoft product


True, but if you pretend that future of C# on Linux is independent of MSFT, you are kidding yourself, IMHO.

---

### Post by ThinkBuntu on 2007-11-19
> **pmasiar said:**
> True, but if you pretend that future of C# on Linux is independent of MSFT, you are kidding yourself, IMHO.
I think that Microsoft's development division is smart enough to guide the language reasonably. Visual Studio and SQL Server are two quality products, and it would be against Microsoft's interests (always trying to attract developers, especially to the .NET platform which requires expensive licenses usually) to restrict the language much. Don't forget, today's open source C# developer of F-Spot could be tomorrow's developer of a major web portal on a .NET platform.

---

### Post by pmasiar on 2007-11-19
> **ThinkBuntu said:**
> I think that Microsoft's development division is smart enough to guide the language reasonably.

They will do it, for some values of "reasonable". Read [http://en.wikipedia.org/wiki/Halloween_documents](http://en.wikipedia.org/wiki/Halloween_documents) - top priority for MSFT is not to create interoperable systems, but to protect  Windows as near-monopoly platform. they have no problem to break backward compatibility and force everyone on upgrade treadmill to keep competition away. thankfully, it is not as bad as it was 10 years ago, but it is so not for lack of trying.

---

### Post by Capricori on 2007-11-21
The future of C# on Linux is one thing, but what about the present?
Does anyone use C# to code programs intended for Linux? Does anyone use it, even in cases where a simple bash script would be sufficient?

Just outta interest :)

---

### Post by ankursethi on 2007-11-22
Linux doesn't have to hang on to Microsoft and whatever stupid implementations they come up with on Windows. We have our own, GPLd, fully open source implementation, Mono. Mono is what matters, everything else is just exaggerating the situation. Microsoft may do whatever they like, and break backwards compatibility as many times as they please, but Mono will still support all .NET apps simply because "upgrading" a large app to the latest .NET standards would be too much work.

Eventually, even large corporations might get tired of Microsoft's games and decide to switch to Mono. Then Mono would be the de facto .NET implementation.

Microsoft knows all this. They will *not* break backwards compatibilty if they can help it. Thanks to Mono, we can now expect a stable development environment with which we can write (almost) cross platform code.

PS : .NET 3 is just a new set of APIs on top of .NET 2.0. .NET 3.5 is also (AFAIK) a set of new APIs. So there's no break in compatibilty between Mono and MS .NET. It's just a matter of time before the community builds new APIs to supplant the MS ones.

PPS : with enough use, open source APIs are likely to emerge which will reduce our dependance on Microsoft's APIs. For example, GTK# already kicks Windows.Forms' ****.

---

### Post by ThinkBuntu on 2007-11-22
> **ankursethi said:**
> Linux doesn't have to hang on to Microsoft and whatever stupid implementations they come up with on Windows. We have our own, GPLd, fully open source implementation, Mono. Mono is what matters, everything else is just exaggerating the situation. Microsoft may do whatever they like, and break backwards compatibility as many times as they please, but Mono will still support all .NET apps simply because "upgrading" a large app to the latest .NET standards would be too much work.

Eventually, even large corporations might get tired of Microsoft's games and decide to switch to Mono. Then Mono would be the de facto .NET implementation.

Microsoft knows all this. They will *not* break backwards compatibilty if they can help it. Thanks to Mono, we can now expect a stable development environment with which we can write (almost) cross platform code.

PS : .NET 3 is just a new set of APIs on top of .NET 2.0. .NET 3.5 is also (AFAIK) a set of new APIs. So there's no break in compatibilty between Mono and MS .NET. It's just a matter of time before the community builds new APIs to supplant the MS ones.

PPS : with enough use, open source APIs are likely to emerge which will reduce our dependance on Microsoft's APIs. For example, GTK# already kicks Windows.Forms' ****.
Classic NIH.

---

### Post by LaRoza on 2007-11-22
Is there a Mono for Windows?

---

### Post by tyoc on 2007-11-22
Yes.

I think that it is somewhat forget there... I mean why install mono if there is MS product for their platform?

The majority of persons that I know have some C# knowledge have asked about mono and they say "yea I saw a monky in the zoo" ;).

---

### Post by ankursethi on 2007-11-23
Erm, I *would* like to mention here that I program Python as a hobby, not C#. I've only looked into C#, and found it nice. That's all. I was just sick of *OMFG!! Mono is teh ev1l!* tinfoil-hat comments on Slashdot/OSNews/UbuntuForums.

---

