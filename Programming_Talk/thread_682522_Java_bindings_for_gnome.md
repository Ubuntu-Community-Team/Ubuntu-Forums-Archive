---
title: "Java bindings for gnome"
date: 2008-01-30
forum: Programming Talk
---

### Post by Gurumaker on 2008-01-30
Hi all,

I'm developing with java and want to use the java gnome bindings but the libs I get from the ubuntu repository are all completely deprecated. I've fetched the lib packages libgnome-java, libgtk-java, libglib-java and so on with apt-get (Gutsy).

I've registered that there is a libgnome2-java but apt means thats no installation candidate can be found for the package. After I searched something around, I found out, that the bindings will be rewritten from the scratch. 

My question is, what shall I use for writing java applications for gnome?  Is there another lib I can use?

Regards
Gurumaker

---

### Post by LaRoza on 2008-01-30
> **Gurumaker said:**
> 
My question is, what shall I use for writing java applications for gnome?  Is there another lib I can use?


You might be better off using Swing. I am not expert though, especially in Java.

---

### Post by Gurumaker on 2008-01-30
Hi LaRoza, thakn you for your answer. I find Swing is really nice, but I can't create a gnome typical GUI with Swing. The desktop integration is also poor with Swing or SWT.

---

### Post by LaRoza on 2008-01-30
> **Gurumaker said:**
> Hi LaRoza, thakn you for your answer. I find Swing is really nice, but I can't create a gnome typical GUI with Swing. The desktop integration is also poor with Swing or SWT.

Not being a Java programming and not being a big fan of GUI programming (but I have to do one soon, for my System Restore program) I can't give much more.

Perhaps another Java programmer could help more.

[http://ubuntuforums.org/showthread.php?t=73294](http://ubuntuforums.org/showthread.php?t=73294) seems to address the Swing on GNOME as best it can.

---

### Post by xlinuks on 2008-01-30
By default Java uses the cross platform look and feel that's why it looks "foreign", if you wish your Swing application to use the system look and feel you gotta tell Java to do so. Google for this info or the following snippet might be enough:
```

public static void main(String[] args) {
    try {
	    // Set System L&F
        UIManager.setLookAndFeel(
            UIManager.getSystemLookAndFeelClassName());
    } 
    catch (UnsupportedLookAndFeelException e) {
       // should not happen
    }


    new SwingApplication(); //Create and show the GUI.
}


```

---

### Post by Gurumaker on 2008-01-30
HI, thanks for your reply, but the look and feel is not really the problem. What I need is a deeper desktop integration. For example, my application is't visible any time and needs to display a status icon in the notification area and it where usefull to use the org.gnome.gtk.StatusIcon class. 

A SwingUI can looks a little bit like a gnome application but there're some widgets and many features missing. This should be simple things like the default icons for buttons and so on. 

I think there no more options than compiling the java-gnome 4.0 binding and put them into my release.

---

### Post by LaRoza on 2008-01-30
Having found no adequate solution in my searches, it seems that Java's main focus isn't integration in Linux but being cross platform. Perhaps you could try a different language with more suitable libraries that are up to date.

I realize that suggesting a change in language can be considered flamebait, and I am not known as a Java fan, but I really do not see a way to get a better GNOME app than to use a language better suited for it. An open source language may be a better solution.

---

### Post by Lord Illidan on 2008-01-30
Or try this site : [http://java-gnome.sourceforge.net/](http://java-gnome.sourceforge.net/)

---

### Post by LaRoza on 2008-01-30
> **Lord Illidan said:**
> Or try this site : [http://java-gnome.sourceforge.net/](http://java-gnome.sourceforge.net/)

/me kicks LI Go study!

---

### Post by xlinuks on 2008-01-30
> **Gurumaker said:**
> HI, thanks for your reply, but the look and feel is not really the problem. What I need is a deeper desktop integration. For example, my application is't visible any time and needs to display a status icon in the notification area and it where usefull to use the org.gnome.gtk.StatusIcon class. 

A SwingUI can looks a little bit like a gnome application but there're some widgets and many features missing. This should be simple things like the default icons for buttons and so on. 

I think there no more options than compiling the java-gnome 4.0 binding and put them into my release.

The current latest version (6) does have the ability to use a system tray. If you ask me - I don't like the implementation for it doesn't allow to display icons in a drop down menu which tipically appears when clicking such a tray, but the tray itself can have icons. Check this:
[http://java.sun.com/javase/6/docs/api/java/awt/SystemTray.html](http://java.sun.com/javase/6/docs/api/java/awt/SystemTray.html)

PS: The following article about the new system tray functionality is a LIE, you can't create such a sys tray (on the pictures) using the standard libraries in JRE 6:
[http://java.sun.com/developer/technicalArticles/J2SE/Desktop/javase6/systemtray/](http://java.sun.com/developer/technicalArticles/J2SE/Desktop/javase6/systemtray/)

However you can use JDIC which has a decent sys stray implementation (but is not part of the Java standard libraries).

---

### Post by ZylGadis on 2008-01-30
> **LaRoza said:**
> An open source language may be a better solution.

Java is an open-source language. Do not spread FUD.

---

### Post by Lord Illidan on 2008-01-30
I too believe that python may be more useful for developing gtk apps.

---

### Post by Gurumaker on 2008-01-30
> **xlinuks said:**
> The current latest version (6) does have the ability to use a system tray. If you ask me - I don't like the implementation for it doesn't allow to display icons in a drop down menu which tipically appears when clicking such a tray, but the tray itself can have icons. Check this:
[http://java.sun.com/javase/6/docs/api/java/awt/SystemTray.html](http://java.sun.com/javase/6/docs/api/java/awt/SystemTray.html)

PS: The following article about the new system tray functionality is a LIE, you can't create such a sys tray (on the pictures) using the standard libraries in JRE 6:
[http://java.sun.com/developer/technicalArticles/J2SE/Desktop/javase6/systemtray/](http://java.sun.com/developer/technicalArticles/J2SE/Desktop/javase6/systemtray/)

However you can use JDIC which has a decent sys stray implementation (but is not part of the Java standard libraries).

JDIC is cool, i do not know that the project is already so sophisticated, thank you for the hint. JDIC or Java6 are both good solution. I'm a little bit disappointed about the deprecated bindings and the new ones which are not provided with a simple package, but the two suggestions you've made are much more platform independant. Thank you for your help, I tink I will make it.

> **LaRoza said:**
> Having found no adequate solution in my searches, it seems that Java's main focus isn't integration in Linux but being cross platform. Perhaps you could try a different language with more suitable libraries that are up to date.

I realize that suggesting a change in language can be considered flamebait, and I am not known as a Java fan, but I really do not see a way to get a better GNOME app than to use a language better suited for it. An open source language may be a better solution.

I think your really right. Java isn't a good language to develop for a special platform. I'm writing java code for some years and it's the easiest way for me to stay with java. By the way, the sun java implementation are also under GPL about one year. I think I will take a look at python. Thre're some plugins for developing python with eclipse. A new language in a familiar ide is much easier to learn ;-)

---

### Post by LaRoza on 2008-01-30
> **ZylGadis said:**
> Java is an open-source language. Do not spread FUD.

If my lack of experience in Java, which I states, means I am a bit behind in its development, it doesn't mean I am spreading FUD.

In fact, accusing someone of doing so is usually offensive. Last time I looked at it (a while ago) it was developed by Sun Microsystems. 

On the other hand, a language that was developed as open source from its start, would probably have a head start in having the stability and libraries to accomplish tasks.

---

### Post by Lord Illidan on 2008-01-30
> **LaRoza said:**
> If my lack of experience in Java, which I states, means I am a bit behind in its development, it doesn't mean I am spreading FUD.

In fact, accusing someone of doing so is usually offensive. Last time I looked at it (a while ago) it was developed by Sun Microsystems. 

On the other hand, a language that was developed as open source from its start, would probably have a head start in having the stability and libraries to accomplish tasks.

It has been opensourced recently, and there is also gcj. However, I don't think people use java that much for gnome development. Python, C/C++, and C# seem to be the languages everybody is using.

---

### Post by LaRoza on 2008-01-30
> **Gurumaker said:**
> 
I think your really right. Java isn't a good language to develop for a special platform. I'm writing java code for some years and it's the easiest way for me to stay with java. By the way, the sun java implementation are also under GPL about one year. I think I will take a look at python. Thre're some plugins for developing python with eclipse. A new language in a familiar ide is much easier to learn ;-)

Nothing against Java, but I haven't really studied it beyond the basics from two books I have (a Java and a Swing book), and I never got the latest developments on it when studying because those books were really good, and I bought them before I had the internet at home, and never used online resources in my study.

Python will be quick to learn too, most likely, as it is much simpler in design than Java and dynamic. It is a good choice with a long open source history, and probably the best standard library I have seen.

---

### Post by LaRoza on 2008-01-30
> **Lord Illidan said:**
> I too believe that python may be more useful for developing gtk apps.

If you are done studying, you should let us all know...

---

### Post by Lord Illidan on 2008-01-30
Taking a break from time to time, LaRoza. Not done yet.

---

### Post by LaRoza on 2008-01-30
> **Lord Illidan said:**
> Taking a break from time to time, LaRoza. Not done yet.

Good luck!

/me reserves kick...for now

---

### Post by Lord Illidan on 2008-01-30
> **LaRoza said:**
> Good luck!

/me reserves kick...for now

My bottom is sore...

---

### Post by LaRoza on 2008-01-30
> **Lord Illidan said:**
> My bottom is sore...

I am not going to comment....

---

### Post by pmasiar on 2008-01-31
> **Lord Illidan said:**
> It has been opensourced recently, and there is also gcj. However, I don't think people use java that much for gnome development. Python, C/C++, and C# seem to be the languages everybody is using.

Java was open source from the very beginning. Just before it was released under Sun specific license ("Java community something and else"), but recently almost all Java code was released under GPL, under pressure that IBM will manage to pull out BSD-licensed reimplementation.

Lord Illidan, I know that being admin does not mean automatically you know difference between "open source" and "Free software" (== GPL), but it would make sense to learn the difference, if you want to express opinion about it. :-)

It is not that hard: There are many "open source" licenses, GPL and BSD are most popular, but there are 50+ more licenses approved by Open Source Foundation, including two Microsoft licenses (beyond "Shared source", IIRC it is not OSF approved). GPL and BSD use different definition for "free": GPL is concerned about freedom of users (4 freedoms), BSD is concerned about freedom of developers (even allowing to make changes private).

And yes, if you want to use language with better chance to accepted by ubuntu, use Python. :-)

---

### Post by LaRoza on 2008-01-31
> **pmasiar said:**
> 
Lord Illidan, I know that being admin does not mean automatically you know difference between "open source" and "Free software" (== GPL), but it would make sense to learn the difference, if you want to express opinion about it. :-)


We are just lowly mods, admins are like Yog-Sothoth, we are just Cthulhu.

Lord Illidan also has to study, so try not to distract.

---

### Post by pmasiar on 2008-01-31
> **LaRoza said:**
> We are just lowly mods, admins are like Yog-Sothoth, we are just Cthulhu.

Lord Illidan also has to study, so try not to distract.

Everyone has a life outside of forums... or so I hope! :-)

Sorry if I was harsh, but really distinguishing between different kinds of open source is not that hard, and maybe because admins have high expectations on my behavior, I have higher expectation on validity of their comments :-)

---

### Post by Lord Illidan on 2008-01-31
My apologies.
But if I am not mistaken, Sun Java has always been propietary, or at least severely restrictive until 2007.

 [http://en.wikipedia.org/wiki/Sun_java](http://en.wikipedia.org/wiki/Sun_java)

---

### Post by LaRoza on 2008-01-31
> **pmasiar said:**
> 
Sorry if I was harsh, but really distinguishing between different kinds of open source is not that hard, and maybe because admins have high expectations on my behavior, I have higher expectation on validity of their comments :-)

In my personal view, I thought Java was a bit proprietary, but I really don't care enough to research it (a rare moment, I research everything usually)

Yes, admins should be held to the highest standard. But I only say that because LI and I are not admins :) We are mods, less powerful (in case you are not a fan of Cthulhu, he is less than Yog-Sothoth)

---

### Post by pmasiar on 2008-01-31
> **Lord Illidan said:**
> My apologies.

none needed. It's common misinterpretation, no worry. And you would not expect **me** to be a Java zealot, would you? :-)

> But if I am not mistaken, Sun Java has always been propietary, or at least severely restrictive until 2007.
[http://en.wikipedia.org/wiki/Sun_java](http://en.wikipedia.org/wiki/Sun_java)

Most (not all: Sun likely does not own all copyrights) was released under [http://en.wikipedia.org/wiki/Java_Community_Process](http://en.wikipedia.org/wiki/Java_Community_Process) which lets users access source code for free, but keeps control of enhancements firmly in Sun's hands. It was good enough for 1998 (at least in eyes of many  suits) to embrace Java instead of Microsoft, and give Java enough hype to become the weed it is now.

wikipedia: "On 13 November 2006, Sun Microsystems made the bulk of its implementation of Java available under the GNU General Public License, although there are still a few parts distributed as precompiled binaries due to intellectual property restrictions.[1]"

---

### Post by a9bejo on 2008-01-31
> **pmasiar said:**
> 
Most (not all: Sun likely does not own all copyrights) was released under [http://en.wikipedia.org/wiki/Java_Community_Process](http://en.wikipedia.org/wiki/Java_Community_Process) which lets users access source code for free, but keeps control of enhancements firmly in Sun's hands.


Which means that it was definitely not [open source](http://en.wikipedia.org/wiki/Open_Source_Definition). But you are right of course that the JCP always had a pretty open development process.   

Anyway it doesn't really matter.  It is open source now.  Which means that Java is the most popular and significant piece of FOSS that exists. ;)

---

### Post by LaRoza on 2008-01-31
> **LaRoza said:**
> Having found no adequate solution in my searches, it seems that Java's main focus isn't integration in Linux but being cross platform. Perhaps you could try a different language with more suitable libraries that are up to date.

I realize that suggesting a change in language can be considered flamebait, and I am not known as a Java fan, but I really do not see a way to get a better GNOME app than to use a language better suited for it. **An open source language may be a better solution.**

Thanks for the Java licenses. As you can see, I am the one that started the "open source" discussion. Perhaps I should have said "a language developed as open source". I am sure Sun's main focus wasn't GNOME, and the development for Java + GNOME is probably much behind other languages that are developed as open source. 

Regardless of the license now, I am sure another language would have better GNOME integration.

(You'll note I didn't point out what language I was thinking of when I stated my opinion to the OP, but everyone knows what language I was thinking of)

> **pmasiar said:**
> none needed. It's common misinterpretation, no worry. And you would not expect **me** to be a Java zealot, would you? :-)
[1]"

I thought you liked Java. I must have missed something when reading your posts.

---

### Post by a9bejo on 2008-01-31
> **LaRoza said:**
> I am sure another language would have better GNOME integration.

As you might already know, Java is not only the name of a programming language, but also of a software platform.  And I think that's is what every one really meant when writing about Java in this Thread (e.g., you cannot really open source a language).

You can write on Java in many languages, including Python, Ruby, Javascript, Scala or Scheme.  In fact, I spent quite some time at work  coding on Java in JRuby and Javascript.  And even if many of these languages also have other implementations, which also have very good libraries (and yes, many of these libraries are better that the ones in Java ), there is nothing that comes close to the huge pool of libraries, specifications and tools that exists for Java.  

So that's why I think that java-bindings for GTK (which seems to be what the [java-gnome](http://java-gnome.sourceforge.net/4.0/) project is about) are very important: Such bindings form a very powerful connection between the Linux Desktop and the Java Platform.  They allow Gnome developers to use the largest software platform on earth together with the GTK libraries.  That's awesome. \\:D/

I think Linux developers can and should make more use of Java in many places.  In the past, this was not possible because Java was not free.  Now that it is, we should embrace it with open arms.

---

### Post by LaRoza on 2008-01-31
> **a9bejo said:**
> 
So that's why I think that java-bindings for GTK (which seems to be what the [java-gnome](http://java-gnome.sourceforge.net/4.0/) project is about) are very important: Such bindings form a very powerful connection between the Linux Desktop and the Java Platform.  They allow Gnome developers to use the largest software platform on earth together with the GTK libraries.  That's awesome. \\:D/

I think Linux developers can and should make more use of Java in many places.  In the past, this was not possible because Java was not free.  Now that it is, we should embrace it with open arms.

I think they are important too. But the issue (when I was posting before) was an immediate solution, not future developments.

Also, Java and Python can be used together to great effect.

My personal opinion is that Java is a bit late. In my opinion, it has a lot to catch up with. With Python, Perl, Ruby, and even Tcl, Java has a lot to compete with. Competition is a good thing, it will drive language development. 

Never once did I think that I should use Java. Sometimes I think "hey, Forth would be good for this", or "Now I know why they have Perl", but I never once thought Java was a solution (even though I know it better than Forth and Perl).

---

### Post by pmasiar on 2008-01-31
> **a9bejo said:**
> Which means that it was definitely not [open source](http://en.wikipedia.org/wiki/Open_Source_Definition). But you are right of course that the JCP always had a pretty open development process.   

Anyway it doesn't really matter.  It is open source now.  Which means that Java is the most popular and significant piece of FOSS that exists. ;)

I am too lazy to check OSF website if JCP was OSF approved, but I would assume it was one of ~~ 50 OSF approved licences.

But I strongly disagree about Java being just "open source": Now Java is more than that - it is genuine GPL Free software! :-) There **is** difference, ask RMS. :-)

Sorry for hijacking the thread. :-)

---

### Post by LaRoza on 2008-01-31
> **pmasiar said:**
> 
Sorry for hijacking the thread. :-)

Like that never happens around here...

---

### Post by pmasiar on 2008-01-31
> **LaRoza said:**
> 
I thought you liked Java. 

NEVER! :-)

In my current project, I use Java, and almost daily I have new reasons to hate it -- and sometimes it is just recycled old reasons.

Once you tasted freedom of Perl and Python, there is no way back. That's why I want to subvert all beginners :-)

---

### Post by LaRoza on 2008-01-31
> **pmasiar said:**
> NEVER! :-)

In my current project, I use Java, and almost daily I have new reasons to hate it -- and sometimes it is just recycled old reasons.

Once you tasted freedom of Perl and Python, there is no way back. That's why I want to subvert all beginners :-)

My condolences, I don't think anyone could pay me to write in Java.

Ruby is looking good too. I am looking into it again. At least learning the language core, so I can be more helpful when Ruby comes up.

It looks like a good language, seems a bit obsessed with being OO, everything really is an object... It has a few idioms that I like. It can be written to look much like Python, as it doesn't use braces. The "end" seems a bit redundant, though. As if someone isn't going to indent.

---

### Post by pmasiar on 2008-01-31
> **LaRoza said:**
> My personal opinion is that Java is a bit late. In my opinion, it has a lot to catch up with. With Python, Perl, Ruby, and even Tcl, Java has a lot to compete with. Competition is a good thing, it will drive language development. 


Excuse me, "a bit late" after 10 years of becoming "mainstream language" and "enterprisey"? Java is not a newcomer: it is rather old and sclerotic dog, which has hard time to learn new tricks. It was hyped up fast, before it was ready for prime time, and now they cannot add new features because it would break backward compatibility. Java is new COBOL++.

---

### Post by pmasiar on 2008-01-31
[Open-Source Java: One Year Later](http://www.eweek.com/c/a/Application-Development/OpenSource-Java-One-Year-Later/1/)

"in May of this [2007] year, Sun had open sourced approximately 96 percent of the total code base of OpenJDK. Only about 4 percent of the code was encumbered, primarily some low-level routines... we're confident that with the communitys help, well have 100 percent free software OpenJDK code base."

---

### Post by LaRoza on 2008-01-31
> **pmasiar said:**
> Excuse me, "a bit late" after 10 years of becoming "mainstream language" and "enterprisey"? Java is not a newcomer: it is rather old and sclerotic dog, which has hard time to learn new tricks. It was hyped up fast, before it was ready for prime time, and now they cannot add new features because it would break backward compatibility. Java is new COBOL++.

[quote="Wikipedia"]
The original and reference implementation Java compilers, virtual machines, and class libraries were developed by Sun from 1995. As of May 2007, in compliance with the specifications of the Java Community Process, Sun made available most of their Java technologies as free software under the GNU General Public License. Others have also developed alternative implementations of these Sun technologies, such as the GNU Compiler for Java and GNU Classpath.
[/quote]

May 2007 is late to be a GNU language. When I said it is "late", I was refering to open source GPL'd development of Java, where it would be behind other languages.

---

### Post by ZylGadis on 2008-01-31
You should note that Java SE was the one of the first, if not the first, platforms with a VM. You should also note that Python itself, much like Java, was under a non-Free (but Open-Source) license for most of its life. They are really not that different from each other, come to think of it.

To address a previous comment, spreading FUD is inexcusable. If you are too lazy to do research, say nothing. FUD is the single most used weapon for human suffering throughout the ages (starting at the latest with the Council at Nicaea), and you should know better than use it (knowingly or not). If you do not know, say nothing. If you feel unsure, check your sources, and best say nothing. If you feel sure, but it turned out you were wrong, apologize and issue a correction. I understand this is a public forum and I cannot hold everyone to the standards I expect of myself, but still, it is a **programming** forum, and programmers are supposed to be smart.

Back to Java. I do not understand all the people foaming against it. It is the best tool for some jobs. It has a huge following in terms of libraries. It is being actively developed. It is as fast as C++. It has its own memory management. It interfaces with the OS level in the best possible way (epoll, anyone, and how many of you even know about it?) It brings together the best of the cathedral and the bazaar, with very few of their drawbacks. I would not even think of using something else for server-side development nowadays.

I would not even think of using Java for client-side or standalone development nowadays, either, for many reasons. Best tool for the job. You should really learn a few languages, so that you see for yourselves that if all you have is a hammer (Python, Ruby, C, Lisp), everything starts looking like a nail, and you prefer to believe somebody else (possibly another foamer) than see for yourselves that there might actually be a purpose behind that chisel over there.

Open your eyes and think for yourselves.

---

### Post by LaRoza on 2008-01-31
> **ZylGadis said:**
> You should note that Java SE was the one of the first, if not the first, platforms with a VM. You should also note that Python itself, much like Java, was under a non-Free (but Open-Source) license for most of its life. They are really not that different from each other, come to think of it.

To address a previous comment, spreading FUD is inexcusable. If you are too lazy to do research, say nothing. FUD is the single most used weapon for human suffering throughout the ages (starting at the latest with the Council at Nicaea), and you should know better than use it (knowingly or not). If you do not know, say nothing. If you feel unsure, check your sources, and best say nothing. If you feel sure, but it turned out you were wrong, apologize and issue a correction. I understand this is a public forum and I cannot hold everyone to the standards I expect of myself, but still, it is a **programming** forum, and programmers are supposed to be smart.

Back to Java. I do not understand all the people foaming against it. It is the best tool for some jobs. It has a huge following in terms of libraries. It is being actively developed. It is as fast as C++. It has its own memory management. It interfaces with the OS level in the best possible way (epoll, anyone, and how many of you even know about it?) It brings together the best of the cathedral and the bazaar, with very few of their drawbacks. I would not even think of using something else for server-side development nowadays.

Open your eyes and think for yourselves.

Java and Python not different from each other? Yes, the are both imperative languages, and OO, but they are different in many significant ways.

You are getting religious now, and there was no FUD. The issue was doing GNOME specific programming, and Java was found lacking in that department. I merely stated another language would have better GNOME support, and didn't state a language in particular. If you find a discussion of personal preferences (which followed), as being FUD, then you didn't get our intent. There are programmers on this forum who have preferences in many areas, including Java, Lisp, Perl and Python, and we usually know each others preferences.

No one is foaming against it, it just isn't our preference, and I know that pmasiar doesn't prefer it and probably doesn't like using it for the project.

Neither of us where giving advice to anyone.

As for learning more than one language, I fully agree that is the best thing to do. Have you seen my wiki? Also, I did state I know Java, and am looking into Ruby some more in an earlier post. Hardly the attitude of a "foaming" person.

---

### Post by a9bejo on 2008-01-31
I think my "language != platform" statement above did not get enough attention ;)

**There are really [b]not** more libraries for the Java Language than there are for Ruby.  Both languages share the same libraries. [/b] 

Even more: The JRuby team decided to not only write an implementation of the Ruby language for Java, they ported the whole CRuby Platform to the Java Platform.  This means that you can use all the great stuff from the ruby standard library together with the huge pool of java stuff.  You can take most ruby programs and simply use them on Java. The only exceptions are the libs that use C extensions, and most of them are already ported to Java.  

You can dynamically extend classes from the JDK at runtime.   You can install packages via ruby gems.  You can deply a Ruby on Rails application inside a J2EE Application Server. You can use ActiveRecord that talks with JDBC.

For the Java Language, I think there were a lot of decisions in the design of Language that later turned out to be not such good ideas.  I personally think it could be much worse ( Hello C++ :) ), but If I get a choice I prefer to use more abstract languages than Java.  

However, ** the future of the Java Language has nothing to do with the future of Java**.   Java is in no way a competition to Ruby or to Python.  It is instead a great enhancement to these languages.

---

### Post by pmasiar on 2008-01-31
Let's calm down, shall we?

calling anyone "foamer" is flamebait IMHO, a notch better than calling him a troll.

Of course everyone has different need and different background, but it becomes tedious to mention them in every post. 

But when I last time asked for a stickied thread where forum regular can mention openly their background, experience, and preferences, so people can see if it is a good fit, it earned me permanenet infraction, and I cannot afford to do it again, so I will not.

---

### Post by pmasiar on 2008-01-31
> **ZylGadis said:**
> You should also note that Python itself, much like Java, was under a non-Free (but Open-Source) license for most of its life. They are really not that different from each other, come to think of it.

IMHO Python is still under same Python/Artistic license, but I need to check details :-)

Difference is, Python **always** was open to discussion and patches from outside. Sun kept **much** stronger hold on Java.

---

### Post by LaRoza on 2008-01-31
> **pmasiar said:**
> Let's calm down, shall we?

calling anyone "foamer" is flamebait IMHO, a notch better than calling him a troll.

Of course everyone has different need and different background, but it becomes tedious to mention them in every post. 

But when I last time asked for a stickied thread where forum regular can mention openly their background, experience, and preferences, so people can see if it is a good fit, it earned me permanenet infraction, and I cannot afford to do it again, so I will not.

Also, dragging Catholics in was a bit much and uncalled for. 

My wiki, [http://ubuntuprogramming.wikidot.com](http://ubuntuprogramming.wikidot.com) has a place for UF members who wish to state their background and experiences.

That wiki is slow to grow, but hopefully some will take interest in it.

---

### Post by Lord Illidan on 2008-02-01
I don't think Java is that bad. I like python also, and c++, but java certainly isn't a bad language.

---

### Post by derkmerkin on 2008-02-01
What a waste of time reading this thread was. Some of you took this thread off topic and turned it into something ridiculous. I didn't realize i walked into a java bashing session.

I was actually interested in java and native gtk apps myself. Gives me second thoughts about asking anything myself on the Ubuntu forums if this is how people act towards a genuine outreach for information.  I hope the rest of the open source community doesn't act like this. 

And the "moderators" should be ashamed for their part in this thread, 5 pages of crap.:(

edit for spelling

---

### Post by a9bejo on 2008-02-01
calm down. The question for java-gtk bindings was answered in post #8,then we had a discussion.  After all, we are here in the community discussion section and not in a pure support forum. It is callled programming talk, and that's what we are doing - we talk.

---

### Post by pmasiar on 2008-02-01
> **derkmerkin said:**
> What a waste of time reading this thread was. Some of you took this thread off topic and turned it into something ridiculous. I didn't realize i walked into a java bashing session.

I was actually interested in java and native gtk apps myself. Gives me second thoughts about asking anything myself on the Ubuntu forums if this is how people act towards a genuine outreach for information.  I hope the rest of the open source community doesn't act like this. 

And the "moderators" should be ashamed for their part in this thread, 5 pages of crap.:(

Pray tell me, you know about forum where discussion never goes off topic? I would love to become member - but I guess it is invitation only, right? :-)

After answering direct question, we participated in discussion and learning. 

I learned about [http://en.wikipedia.org/wiki/First_Council_of_Nicaea](http://en.wikipedia.org/wiki/First_Council_of_Nicaea) (although have no clue why it is relevant to anything :-) ) and current JRuby status, other people learned there is difference between open source and free software, and what it is, and more stuff. Some people expressed surprise that I use Java in my day job, so when I say Java is not my favorite language, I may have a bit of clue. :-) Compared to many people who bash language which they do not use or know, because it is just a "scripting" language. Just a banter between friends who have fun while helping other people. Community of volunteers. 

BTW if you are concerned about my opinion about Java, let me tell you that I hate VB even more passionately. You may check some of my old threads, I am quite opinionated (and have infraction points to prove it :-) )

---

### Post by Lord Illidan on 2008-02-01
> **derkmerkin said:**
> What a waste of time reading this thread was. Some of you took this thread off topic and turned it into something ridiculous. I didn't realize i walked into a java bashing session.

I was actually interested in java and native gtk apps myself. Gives me second thoughts about asking anything myself on the Ubuntu forums if this is how people act towards a genuine outreach for information.  I hope the rest of the open source community doesn't act like this. 

And the "moderators" should be ashamed for their part in this thread, 5 pages of crap.:(

edit for spelling

Somebody seems to be having anger issues here. The question asked was answered, and so the thread turned into a discussion about the merits of java. I don't know what's so bad about it.

And no, I'm not ashamed of my part in this thread, and nor should anybody else.

---

### Post by LaRoza on 2008-02-01
> **derkmerkin said:**
> What a waste of time reading this thread was. Some of you took this thread off topic and turned it into something ridiculous. I didn't realize i walked into a java bashing session.

I was actually interested in java and native gtk apps myself. Gives me second thoughts about asking anything myself on the Ubuntu forums if this is how people act towards a genuine outreach for information.  I hope the rest of the open source community doesn't act like this. 

And the "moderators" should be ashamed for their part in this thread, 5 pages of crap.:(

edit for spelling

Sorry if it looked that way, here is a little background:

* The issue was addressed, so the OP wasn't mislead
* We mostly know each other, so it isn't a bunch of random people 
* Two of us happen to have preferences outside of Java, and made a few comments to each other
* The Java license issue was just a technicality that was discussed.

You will see that many threads on this forum (especially the programming talk) often have a lengthy OT discussion after the issue is addressed. 

And I am only acting as a moderator when I stated to so in [color="red']red[/color]. I am a member of this forum like everyone else, am I not allowed to have opinions? I do know Java, among other languages, and I don't prefer to use it.

---

