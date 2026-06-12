---
title: "Java and the GPL, Is anyone interested?"
date: 2006-12-18
forum: Programming Talk
---

### Post by gh0st on 2006-12-18
As Java is about to be released under the GNU/GPL v2 I just thought I'd see what people thought about it. Would you be more likely to look at using Java now? Do you think it will make Java more popular on Linux?

I have been using Java for a few years under windows and I thought it would be reasonably popular on Linux before I moved over. It seems I was wrong though. Most people I have talked to in the Linux community don't like Java at all. I wondered if this was just because it wasn't open source and if so, will it become more popular under the GPL?

What do people think? :-k

---

### Post by lnostdal on 2006-12-18
> **gh0st said:**
> As Java is about to be released under the GNU/GPL v2 I just thought I'd see what people thought about it. Would you be more likely to look at using Java now?

Yes, it is a major improvement. If I where to use Java, the non-technical issues (closed source) I've had with it are gone now.

> **gh0st said:**
> Do you think it will make Java more popular on Linux?

Possibly; many find it essential that the software they very much depend upon is Open Source.

> **gh0st said:**
> I have been using Java for a few years under windows and I thought it would be reasonably popular on Linux before I moved over. It seems I was wrong though. Most people I have talked to in the Linux community don't like Java at all. I wondered if this was just because it wasn't open source and if so, will it become more popular under the GPL?


That might be a reason but another reason might be that other languages (Python, Ruby, Lisp, etc.) are more easily available and used in Linux. People might feel that there is no need for Java; as there are better alternatives.

What I do like about Java (technically) are the possibilities with the VM and the JIT-compiler. Using the portable Java-platform to build or support *interactive*(#1) languages like Jython is a great idea.

[http://java.sun.com/developer/technicalArticles/J2SE/Desktop/scripting/index.html](http://java.sun.com/developer/technicalArticles/J2SE/Desktop/scripting/index.html)
[https://scripting.dev.java.net/](https://scripting.dev.java.net/)

#1: Interactive languages and environments lets one manipulate code ("functions") at run-time. Interactive does not necessarily mean *interpreted* - as the code can be compiled when it is changed; even at run-time.

---

### Post by welshboy on 2006-12-18
But don't sun include the source code with the SDK?  

I can distinctly remember reading through loads and loads of source code, to try and learn how Java works.

Then again, I guess the fact they give you the source code with it doesn't make it open source.

I'm still pretty new to this concept of open source.  If any one would be kind enough to explain to me the concept, then I would be much obliged :)

---

### Post by lnostdal on 2006-12-18
> **welshboy said:**
> I'm still pretty new to this concept of open source.  If any one would be kind enough to explain to me the concept, then I would be much obliged :)

You'll probably find most answers here: [http://en.wikipedia.org/wiki/Open-source_software](http://en.wikipedia.org/wiki/Open-source_software)

---

### Post by pmasiar on 2006-12-18
> **gh0st said:**
> Most people I have talked to in the Linux community don't like Java at all. I wondered if this was just because it wasn't open source and if so, will it become more popular under the GPL?

Java was proprietary answer to Microsoft dominance on desktop. It was supposed to be "compile once, run anywhere" on Sun's proprietary JVM in Netscape  browser in thin client PC. That's why java has complicated security model, allowing "securely" to run other people's applets in my browser. Concept of applets was mostly flop, java is used mostly on servers, where all this security layers is unnecessary compilations. 

Another problem java was supposed to solve was memory leaks of C++. But solution (garbage collection methods) causes java to become unresponsive at random intervals. Python has reference couting, which has more predictable response time.

Java is good enough improvement from C++, but does not go far enough - dynamic languages like python, ruby and perl, which were not designed under pressure of marketing department, are far better solutions - because all features they have are solutions to someone's problems. :-)

Problem with java is, that **for marketing reasons** java reinvents the wheel, rushes into production concepts which are not thought through (like GC), and builds separate ecosystem incompatible with LAMP stack. CGI written in java does not run on Apache. Oracle supports java as a way to place sticks to MySQL wheels. etc etc.

Java was put under GPL not because Sun is nice and altruistic: it was bacause without that, java would be irrelevant in couple years. Proprietary java could not accomplish what Sun intended: to create alternative platform to MS Windows - Linux with C, C++ and dynamic languages did that.

That said, I am forced to learn Java now :-( because our department head, and ever less competent boses above him, decided to switch from LAMP to java. Java has more resources to marketing... and all we know that marketiods are the finest, smartest specimens of human race. ;-)

---

### Post by welshboy on 2006-12-18
> **lnostdal said:**
> You'll probably find most answers here: [http://en.wikipedia.org/wiki/Open-source_software](http://en.wikipedia.org/wiki/Open-source_software)

Reading it now :D 

Many thanks

---

### Post by gh0st on 2006-12-18
> **pmasiar said:**
> 

Java was put under GPL not because Sun is nice and altruistic: it was bacause without that, java would be irrelevant in couple years. Proprietary java could not accomplish what Sun intended: to create alternative platform to MS Windows - Linux with C, C++ and dynamic languages did that.



A good point and I'm not saying Java is fantastic and everyone should move to it under GPL, I think Python is great. After all it is cross-platform as well and even has suport in .NET with IronPython which Java doesn't really other than J#. I certainly don't think Sun open sourced Java because they are such fantastic people either, it's about marketing as you say.

Never the less I am curious to see what inovations will be made with Java under the GPL, I wonder if the community will embrace it or have Sun missed the boat? It could be a nice tool to have in the armory along with all the others.

As for learning Java, I reckon you'll find it easy if you already know C++, the syntax is very similar, good luck :-)

---

### Post by pmasiar on 2006-12-18
> **lnostdal said:**
> You'll probably find most answers here: [http://en.wikipedia.org/wiki/Open-source_software](http://en.wikipedia.org/wiki/Open-source_software)

Open source is neat marketing trick to make [http://en.wikipedia.org/wiki/Free_software](http://en.wikipedia.org/wiki/Free_software) acceptable for business. Access to source is just prerequisite to guarante certain freedoms. Free as free speech, not as free beer.

You need to understand the difference between Open Source and Free Software.. and then side with freedom. :-)

---

### Post by gh0st on 2006-12-18
> **pmasiar said:**
> Open source is neat marketing trick to make [http://en.wikipedia.org/wiki/Free_software](http://en.wikipedia.org/wiki/Free_software) acceptable for business. Access to source is just prerequisite to guarante certain freedoms. Free as free speech, not as free beer.

You need to understand the difference between Open Source and Free Software.. and then side with freedom. :-)

The article on Wikipedia is very interesting thanks. The bit that cought my eye was this:

[From Wikipedia]
*Free software gives users the ability to cooperate with each other in enhancing and refining the programs they use. Free software is a pure public good rather than a private good. Companies that contribute to free software can increase commercial innovation amidst the void of patent cross licensing lawsuits.*
[End of quote]

I think a lot of people assume open source software and free software are the same thing. It's an easy mistake to make and companies often encourage this misleading view in their own adverts.

---

### Post by samjh on 2006-12-18
Back on topic.

Yes, I think more developers in the Linux environment will use Java.  Java has been treated 2nd class in Linux distros because of its license.  Hopefully, Sun's reference implementation will become as widely accepted as pure Open Source development platforms like Python.

It should be remembered that Java is ever-improving.  Just because it is/was proprietary or "designed under the pressure of marketing department" does not make it bad or worse than FOSS.  Marketing departments put pressure because of the way the market - ie. customers - change.  Ultimately, influences from marketing is a positive thing, because it keeps the technical teams in line with real-world expectations of what business clients want.  It doesn't always work well, but it works well if the marketing process is well implemented.

For Java, the use of the Java Community Process has been quite successful.  Microsoft's .NET was predicted by some analysts to kill off Java.  Well, .NET has been in the industry for 5-odd years now, and it hasn't made too much of a dent in Java's market share, despite Microsoft using every trick it its books to throw off Java.  If Java was not a continually evolving platform, and not only just evolving, but also evolving in the best direction, than it would have indeed been crushed by .NET.

I think Java is considered poorly by a lot of programmers, because it is restrictive, big, proprietary, and suffers from image problems back in its earlier years.  Most of those concerns are purely subjective (eg. syntax), others are actually good (eg. strong typing, garbage collection, extensive standard API).  The proprietary-ness of Java is soon to disappear.  The carry-over bad image from its earlier flaws can be ironed out by better promotion and increased usage.  Java is now comparatively quick, even giving pure C a run for its money under some conditions, competitively fast against JIT-compiled languages of the .NET platform, with good native Swing LAF, improved desktop integration, while also continuing to build on its enterprise computing muscle.

---

### Post by FyreBrand on 2006-12-18
> **pmasiar said:**
> Java was proprietary answer to Microsoft dominance on desktop. It was supposed to be "compile once, run anywhere" on Sun's proprietary JVM in Netscape  browser in thin client PC. That's why java has complicated security model, allowing "securely" to run other people's applets in my browser. Concept of applets was mostly flop, java is used mostly on servers, where all this security layers is unnecessary compilations. 

Another problem java was supposed to solve was memory leaks of C++. But solution (garbage collection methods) causes java to become unresponsive at random intervals. Python has reference couting, which has more predictable response time.

Java is good enough improvement from C++, but does not go far enough - dynamic languages like python, ruby and perl, which were not designed under pressure of marketing department, are far better solutions - because all features they have are solutions to someone's problems. :-)

Problem with java is, that **for marketing reasons** java reinvents the wheel, rushes into production concepts which are not thought through (like GC), and builds separate ecosystem incompatible with LAMP stack. CGI written in java does not run on Apache. Oracle supports java as a way to place sticks to MySQL wheels. etc etc.

Java was put under GPL not because Sun is nice and altruistic: it was bacause without that, java would be irrelevant in couple years. Proprietary java could not accomplish what Sun intended: to create alternative platform to MS Windows - Linux with C, C++ and dynamic languages did that.

That said, I am forced to learn Java now :-( because our department head, and ever less competent boses above him, decided to switch from LAMP to java. Java has more resources to marketing... and all we know that marketiods are the finest, smartest specimens of human race. ;-)Java wasn't developed as an answer to MS desktop dominance any more than almost anything is developed as an answer to MS dominance.  It was developed (beginning as the Green project) as a language for small electronic appliances (from microwaves to cell phones).  It flopped in that direction at the time.  It fit in well with the birth of the internet and multi-platform development.

There are lots of problems with Java, but then again there are lots of problems with many languages including C, C++, C#, Python, Ruby, lisp, etc ad naseum.  The strength of Java is that it's a mature language.  Python and Ruby are great languages but still have a little growing to do.

I'm sure marketing has had a lot to do with Java opening.  It's a great time for Java to open and a great time for Linux to have it opened.  Since Linux is a popular server platform having Java opened will strengthen both platforms.  Did Sun do this altruistically?  I seriously doubt it.  But to think any company has purely altruistic motives in the commercial market is naive.  It's still a good move by Sun for them, for Linux, and for FOSS in general.

As far as your opinion on LAMP, I would ask that you keep an open mind.  I've never been a huge Java fan, but the more I program in PHP the more I'm coming to appreciate some of Java's strengths.  On top of that the more I'm reading about PHP the less comfortable I'm feeling with it's security features and holes and more importantly the attitude of the PHP leadership towards that.

I don't know if Java will blossom, but I do think it will have a stronger foundation.

Here are a couple links that might be interesting to read:
Slashdot article: [**[COLOR="SeaGreen"]2007 Java Predictions[/COLOR]**]("http://developers.slashdot.org/article.pl?sid=06/12/17/0237234&from=rss")
heise Security news -  [**[COLOR="RoyalBlue"]Security specialist leaves PHP security team[/COLOR]**]("http://www.heise-security.co.uk/news/82500")

---

### Post by gh0st on 2006-12-18
Yeah I think you're right Java will have a stronger base under the GPL. I heard Sun's Open Source Manager on LUGRadio recently and he seemed fully commited to the GPL. He said they are working through the Sun product list Open Sourcing things and Java was just next on the list. Apparently he's been working there 2 years now so I dunno why it's taken so long :)

I like the fact that they are using the GPL rather than coming up with their own more restrictive license like some companes have with other things. We have enough different licenses knocking around already I think.

---

### Post by pmasiar on 2006-12-18
> **FyreBrand said:**
> Java wasn't developed as an answer to MS desktop dominance 

I never said java was **developed** that way. Sun developed it for own peculiar reasons. It was marketed and embraced by others as a way to break MS monopoly with "write once, run anywhere" promise. Remember thin PC clients 10 ears ago, promoted by Ellison, which even **looked** like a coffee-maker?

> The strength of Java is that it's a mature language.  Python and Ruby are great languages but still have a little growing to do. 

Python is mature enough: [ 1.2 released in 1995]("http://en.wikipedia.org/wiki/Python_%28programming_language%29"), .2 versions ahead of java :-) 

> It's a great time for Java to open and a great time for Linux to have it opened.  Since Linux is a popular server platform having Java opened will strengthen both platforms. 

Agree, with comments that Sun was more interested in opening jave than other way around. Opening java was also in part in response of free implementations of classpath and harmony. If Sun would wait little longer, IBM would push them through. Why do you think eclipse IDE was called as it is? To make Sun happy? To gain Sun's support? ;-)

> As far as your opinion on LAMP, I would ask that you keep an open mind.  

Not sure what you mean. **I prefer LAMP**. I actively hate Oracle, they are like MS: they don't care if they make developer's life miserable, if they save $0.25 on support costs, or can push some brain-dead marketing campaign. MySQL is more open to community and understand it better. Oracle is designed  as overcomplicated, so Oracle DBAs can require their 150K salaries. Oracle does not allow deep linking to it's oracle knowledgebase articles - you need "fast free login". Many forums have question in open, but you can access answer only if you register. Can you believe that?  MySQL allows user to comment on documentation pages, and some best explanations arre posted by users in docs pages. Tomcat web server is overcomplicated resource hog, apache is not easy but I can understand it. **I love LAMP.**

>  I've never been a huge Java fan, but the more I program in PHP the more I'm coming to appreciate some of Java's strengths.  

Try python. you have all modularity, order and OO goodness of java, with dynamic typing and flexibility of PHP.

---

### Post by FyreBrand on 2006-12-21
> **pmasiar said:**
> Not sure what you mean. **I prefer LAMP**. I actively hate Oracle, they are like MS: they don't care if they make developer's life miserable, if they save $0.25 on support costs, or can push some brain-dead marketing campaign. MySQL is more open to community and understand it better. Oracle is designed  as overcomplicated, so Oracle DBAs can require their 150K salaries. Oracle does not allow deep linking to it's oracle knowledgebase articles - you need "fast free login". Many forums have question in open, but you can access answer only if you register. Can you believe that?  MySQL allows user to comment on documentation pages, and some best explanations arre posted by users in docs pages. Tomcat web server is overcomplicated resource hog, apache is not easy but I can understand it. **I love LAMP.**
I'm saying that you can there are other good alternatives to PHP.  Apache and MySQL (or other decent db backends) can be used with other languages.

> **pmasiar said:**
> Try python. you have all modularity, order and OO goodness of java, with dynamic typing and flexibility of PHP.I do want to learn Python.  I like what I've read about it so far.

---

### Post by bieber on 2006-12-21
I've been having to use Sun's Java for Computer Science for a while, but I've been completely and utterly opposed to the idea of actually using it to create anything worthwhile, because there's no way I would ever develop software that would be tethered to a proprietary platform.  Now, once Java is thoroughly freed (I'm not going to be satisfied until it's *all* out there), I think I may very well go ahead and actually use it, since I know the language so well now.

So, yes, GPL'd Java is making a very large difference for me.

---

### Post by troach on 2006-12-22
> Not sure what you mean. **I prefer LAMP**. I actively hate Oracle, they are like MS: they don't care if they make developer's life miserable, if they save $0.25 on support costs, or can push some brain-dead marketing campaign. MySQL is more open to community and understand it better. Oracle is designed  as overcomplicated, so Oracle DBAs can require their 150K salaries. Oracle does not allow deep linking to it's oracle knowledgebase articles - you need "fast free login". Many forums have question in open, but you can access answer only if you register. Can you believe that?  MySQL allows user to comment on documentation pages, and some best explanations arre posted by users in docs pages. Tomcat web server is overcomplicated resource hog, apache is not easy but I can understand it. **I love LAMP.**



Try python. you have all modularity, order and OO goodness of java, with dynamic typing and flexibility of PHP.

Oracle is some expensive sh*t, but it has it's places. it's a proven platform that a company is willing to pay for to put their valuable data on. Yes, they will pay for it, but they are happy knowing they have a company (Oracle Support) that will stand behind it and resolve issues when they need to. Most featurs in an Oracle Database no one uses, but they have things like streams, advanced replication, advanced security, that not even DB2, SQL Server, or any other open source database offers. Try coding it all yourself.

Now if you want to know a nice open source alternative, I like PostgreSQL better than MySQL and check out EnterpriseDB for a slick open source DB that runs Oracle PL/SQL code. Sony Gaming / Entertainment Online just migrated all their Oracle DBs from Oracle to EnterpriseDB with minimal code modification.

I'll still use MySQL like a backend for an online bulletin forum such as this : ).

I will use the best tool for the job. Oracle has it's place, but I'm not the one paying for it.

---

