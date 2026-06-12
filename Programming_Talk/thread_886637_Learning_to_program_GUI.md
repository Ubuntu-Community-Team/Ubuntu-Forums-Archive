---
title: "Learning to program GUI"
date: 2008-08-11
forum: Programming Talk
---

### Post by harisund on 2008-08-11
As a brief introduction, I used to program in VB6 (not the current VB.Net etc). GUI programming was basically dragging and dropping GUI elements (like buttons, forms, menus etc) and then writing some code to tell the program how to behave when it's clicked on, when the mouse hovers over it etc. 

It's been a while since I have done anything like that. Most of my code in recent times in college has been strictly terminal based, where the user enters some input, or in most cases read some input from a file, work on it using some genetic algorithm (sort, search etc) and print output. As you can imagine, college class work. 

Now I would like to try to create some GUIs. What I am looking for is basically - 
1. Something cross platform. I want to be able to code and run both on Windows and Linux (Ubuntu, eeeUbuntu)
2. Something with the ease of use of old school Visual Basic. I want to be able to create GUI elements by dragging / dropping and write event driven code for it. A debugger would help. Any good IDE suggestions? 
3. I don't care what programming language is used. I have used C++ in school, well C actually, but I am willing to learn anything new. 
4. Existence of good tutorials. I am no n00b to Linux or programming, but I am a big fan of tutorials as well. 

Any ideas anyone?

---

### Post by guilly on 2008-08-11
Java 

Eclipse for IDE

references : [http://java.sun.com/j2se/1.5.0/docs/api/](http://java.sun.com/j2se/1.5.0/docs/api/)

the java api's are a great source for learning various classes. You will most def. be reffering to this website if you choose to develop in java.

---

### Post by era86 on 2008-08-11
Have you looked into wxWidgets and Dialog Blocks?  This is a cross-platform GUI for C++ (also with many other programming languages).  I am using it now and I like it.

There is also QT.  You can get the QT Designer, which has a similar drag and drop interface to MSVS.

---

### Post by themusicwave on 2008-08-11
The Java Netbeans IDE has a nice GUI builder.  It is also cross platform, as is Java.


It might be worth a look.

---

### Post by WRDN on 2008-08-11
I would recommend using the GTK+ library. The fundamentals for creating a GUI aren't hard to grasp, and you can very quickly create a functional GUI based program. I followed [this]("http://zetcode.com/tutorials/gtktutorial") guide for GTK.

---

### Post by Bachstelze on 2008-08-11
+1 for Qt. I'm currently working on something in Python + Qt as my first serious GUI vork, and it's a real breeze.

---

### Post by OutOfReach on 2008-08-11
+1 for Qt here too, I'm learning the fundamentals of it right now, and I must say it is somewhat easier to learn than GTK (I tried to learn GTK in the past...)

---

### Post by MaxIBoy on 2008-08-11
Cross-platform GTK+ bindings are available for Python.

---

### Post by LaRoza on 2008-08-11
> **harisund said:**
> As a brief introduction, I used to program in VB6 (not the current VB.Net etc). GUI programming was basically dragging and dropping GUI elements (like buttons, forms, menus etc) and then writing some code to tell the program how to behave when it's clicked on, when the mouse hovers over it etc. 

You can do that in Linux also.


> 
Now I would like to try to create some GUIs. What I am looking for is basically - 
1. Something cross platform. I want to be able to code and run both on Windows and Linux (Ubuntu, eeeUbuntu)
2. Something with the ease of use of old school Visual Basic. I want to be able to create GUI elements by dragging / dropping and write event driven code for it. A debugger would help. Any good IDE suggestions? 
3. I don't care what programming language is used. I have used C++ in school, well C actually, but I am willing to learn anything new. 
4. Existence of good tutorials. I am no n00b to Linux or programming, but I am a big fan of tutorials as well. 


The sticky, the only sticky, called "Please Read This Before Posting" has a link in it about GUI's. Did you miss it?

It has everything people mentioned here, with more links and a more coherant form including links to GUI designers.

And for the IDE question, that same sticky has a link for it.

Tutorials? The sticky again has your answer.

The "Please Read This Before Posting" title was meant to drawn attention to it to help you. If something isn't answered by the sticky, giving feedback on the sticky (and the links therein) will improve it for others.

---

### Post by Shin_Gouki2501 on 2008-08-11
I highly recommend, Eclipse SWT, Jface and Finnaly Eclipse RCP.
If you really want to build "GUIs" those give you nice Abstraction levels from lowlevel (SWT) to JFace (Viewer Concepts and Dialogs e.g. READY TO USE Wizards etc..) to finally RCP which offers you Moduels via OSGi and an incredibly powerfull workbench.

Not to say something against QT or other  C++ stuff. But as far as i can tell from personal eperince Eclipse RCP helps you to be productive and don'T think too much about Platformdetails.

Check here for general Information:
[http://wiki.eclipse.org/index.php/Rich_Client_Platform](http://wiki.eclipse.org/index.php/Rich_Client_Platform)
 and here for Demo Application:
[http://www.eclipse.org/community/rcp.php](http://www.eclipse.org/community/rcp.php)


Ah and hi LaRoza :)
Remember over 90% of posters dotn read Sticky since they tend to ask things which google answers esily, but now guess what is even easier then google ( for the lazy ones).
:)

---

### Post by pmasiar on 2008-08-11
> **Shin_Gouki2501 said:**
> Remember over 90% of posters dotn read Sticky 

I suggest again:

1: add "did you read FAQ sticky" right next to submit button when creating new thread. I cannot imagine why this is a problem, because I am sure that all subforums have exactly this same problem: people not reading FAQ before first post. So every forum would be better with this trivial reminder.

2: to punish a question answerable by reading FAQ by 1 infraction point, expiring in 1 day, or even reverted. 

- it will sting poster a little, so next time will try to read FAQ first
- but not too much to really hurt
- if not, we will see that someone just ignores FAQ == prefers us to read FAQ for him. That is a leech, and this measure will detect it.

I am at loss why we have to ignore current situation, where 25% of my posts is "see the FAQ", competing with answers by random ppl with less and worse info than elaborate FAQ **we already created** but those random ppl ignore and possibly never read themselves.

All these posters would do better to add post to proper FAQ sticky thread (it that opinion is not mentioned yet), and link to it.

So current situation clearly prefers random half-information, hurting both posters and people who invest time to provide good answers, and benefits only random posters who gets to express opinion, even if less than optimal.

</rant>

---

### Post by LaRoza on 2008-08-11
> **Shin_Gouki2501 said:**
> 
Ah and hi LaRoza :)
Remember over 90% of posters dotn read Sticky since they tend to ask things which google answers esily, but now guess what is even easier then google ( for the lazy ones).
:)

When you see something that can answered by the sticky point it out instead of answering. That answer you gave was interesting, but it will be lost the next time. Why not give input on the GUI thread so everyone can benefit?

> **pmasiar said:**
> I suggest again:

1: add "did you read FAQ sticky" right next to submit button when creating new thread. I cannot imagine why this is a problem, because I am sure that all subforums have exactly this same problem: people not reading FAQ before first post. So every forum would be better with this trivial reminder.

Click on the report button under my name. Read the text under it. That text is wrong (the last time I looked) and the report feature can be used for more (see guide to forum features and link for it, but I don't think it doesn't say anything you don't know). We still get many reports asking for help, answering the post, or somehow indication complete ignorance of the fact that no one will read that (except staff, and we ignore them)

The reminder won't work any more than the text in the report feature, and the name of the sticky itself.

Frusterating, but read Dilbert and take heart in the fact we are extremely intelligent. (speaking of which, I am reading about Scientology at the moment...)

> 
2: to punish a question answerable by reading FAQ by 1 infraction point, expiring in 1 day, or even reverted. 

- it will sting poster a little, so next time will try to read FAQ first
- but not too much to really hurt
- if not, we will see that someone just ignores FAQ == prefers us to read FAQ for him. That is a leech, and this measure will detect it.

You know the answer to that (but if I were the owner of this forum, and it wasn't attached to UF, I would do something more than we do here)

> 
I am at loss why we have to ignore current situation, where 25% of my posts is "see the FAQ", competing with answers by random ppl with less and worse info than elaborate FAQ **we already created** but those random ppl ignore and possibly never read themselves.

I agree. I see so many "Use GTK+!", "I use PyQT", "Try Java with $DESIGNER" randomly scattered. Do they see how incomplete that is and how uninformative?

> 
So current situation clearly prefers random half-information, hurting both posters and people who invest time to provide good answers, and benefits only random posters who gets to express opinion, even if less than optimal.

</rant>

+1

</modrantapproval>

---

### Post by harisund on 2008-08-11
First off, thanks for the posts ! I will take a look into the options. 

Second, LaRoza how on earth do people like you become administrators? And I was told the Ubuntu community was the friendliest. 

Yes, I have read the stickies. I have been a member here and been using Ubuntu since 2k5, I fully know the rules. I just wanted the opinions of more users than that of a forum administrator listing out his bunch of options.

> **pmasiar said:**
> So current situation clearly prefers random half-information, hurting both posters and people who invest time to provide good answers, and benefits only random posters who gets to express opinion, even if less than optimal.

Oh em gee, are you so upset I decided to skip over your "good answer" to get a random posters' sub-optimal opinion? 

If you want to delete this thread, by all means go ahead and do so. I have got the information I wanted.

---

### Post by harisund on 2008-08-11
> **LaRoza said:**
> 

I agree. I see so many "Use GTK+!", "I use PyQT", "Try Java with $DESIGNER" randomly scattered. Do they see how incomplete that is and how uninformative?


Sorry, I find it neither incomplete nor uninformative.

---

### Post by LaRoza on 2008-08-11
> **harisund said:**
> 
Second, LaRoza how on earth do people like you become administrators? And I was told the Ubuntu community was the friendliest. 

Yes, I have read the stickies. I have been a member here and been using Ubuntu since 2k5, I fully know the rules. I just wanted the opinions of more users than that of a forum administrator listing out his bunch of options.

I see no admin doing such thing. I am a moderator (and it may not be "his" options either)

The stickies may look like mine, but they are the result of other people's input and work. If you read the sticky, there is a thread dedicated to feedback on improving it: [http://ubuntuforums.org/showthread.php?t=694551](http://ubuntuforums.org/showthread.php?t=694551)

Also, if you followed the links, particularly to the GUI section. you'd see that it is just me updating the original post based on other people's comments. 

Also, you knocked the sticky and the various FAQ's without telling how to improve them...

Also, as for being friendly, there is a difference between being friendly enough to try to make information easy to get (at the expense of my own time) and being "friendly" enough to not care if people ignore it.

> 
Oh em gee, are you so upset I decided to skip over your "good answer" to get a random posters' sub-optimal opinion? 


Considering most people like my efforts to make information easier to find, I do not care you skipped it.

> **harisund said:**
> Sorry, I find it neither incomplete nor uninformative.
It is complete? Wow. I must have missed something...

---

### Post by kknd on 2008-08-11
Everyone is casting their votes, so:

+1 to GTK.

---

### Post by tinny on 2008-08-11
> **themusicwave said:**
> The Java Netbeans IDE has a nice GUI builder.  It is also cross platform, as is Java.


It might be worth a look.

+1 And...

[MonoDevelop]("http://www.monodevelop.com/Main_Page") has a GUI builder and support for the VB programming language, not sure how well the two work together?

[http://www.monodevelop.com/Image:Stetic-in-monodevelop.png](http://www.monodevelop.com/Image:Stetic-in-monodevelop.png)

It may not be the "popular" choice here but I believe you will be most comfortable with NetBeans and its built in GUI builder.

If you're come from a VB background you are most likely a tools centric type developer and just want something that will deliver all these tools straight out of the box. NetBeans does this.

However if I where you id be looking at getting myself up to speed with a modern mainstream programming language before committing to a tool set.

As a guide:

Java, NetBeans
Python, (Not sure about this one maybe someone can fill in the gap.........)
C#, MonoDevelop

EDIT: As for the whole sticky conversation. Yes its always good to look at the sticky but there is nothing wrong with some semi human interaction right? otherwise we would get rid of forums all together and just use google.

---

### Post by LaRoza on 2008-08-11
> **tinny said:**
> otherwise we would get rid of forums all together and just use google.

Well, for things not answered yet, posting just helps google complete its index. Soon, google will be all, and the need for humans at all will vanish as google solves all the world problems (if Terminator is any indication, it will solve them by removing them, but whatever works)

---

### Post by HotCupOfJava on 2008-08-11
I'm gonna stay off the "sticky" fussing and answer the original question.

Another vote for Java and Netbeans for the IDE. Both are great choices for your needs.

---

### Post by LaRoza on 2008-08-11
> **HotCupOfJava said:**
> I'm gonna stay off the "sticky" fussing and answer the original question.

Another vote for Java and Netbeans for the IDE. Both are great choices for your needs.

```

1. Something cross platform. I want to be able to code and run both on Windows and Linux (Ubuntu, eeeUbuntu)

```
Yes, Java fulfils that.

> 
2. Something with the ease of use of old school Visual Basic. I want to be able to create GUI elements by dragging / dropping and write event driven code for it. A debugger would help. Any good IDE suggestions?
Java is not easy to use. Its code is the opposive of VB...

> 
3. I don't care what programming language is used. I have used C++ in school, well C actually, but I am willing to learn anything new.
All the toolkits (except Java) mentioned have GUI designers and ports to many langauges. But the sticky linked to those toolkits and their GUI designers with the drag and dropping, so I guess that wasn't what you wanted?

---

### Post by pmasiar on 2008-08-11
> **tinny said:**
> EDIT: As for the whole sticky conversation. Yes its always good to look at the sticky but there is nothing wrong with some semi human interaction right? otherwise we would get rid of forums all together and just use google.

Semi-human? I consider myself fully human, so it leaves you out? :-)

I have no problems with human-to-human interaction. My problem is that when ignoring stickies, random less- or mis-informed posts compete for attention with good answers, which discussed the topic in depth and context, but are ignored.

At least if OP mentioned that he read stickies, and which part he missed/misunderstand/needs better explanation, so we can skip "RTFS" and talk business.

Optimal way would be something like wikipedia, where  experts would collaborate on best wording, removing cruft and misunderstanding, without ego-trips and opinion-flashing. Just the facts.

Then discussion would be about collecting the facts for wiki, not trying to replace it.

---

### Post by pmasiar on 2008-08-12
> **harisund said:**
> Second, LaRoza how on earth do people like you become administrators? And I was told the Ubuntu community was the friendliest. 

Being friendly does not mean taking side of someone who does not follow suggestion of "how to ask questions" - we may be friendly and still try to stop the 'eternal september' tide. Education and acculturation makes discussion richer for all parties, including beginners.   

> Yes, I have read the stickies. I have been a member here and been using Ubuntu since 2k5, I fully know the rules. 

Forgive me I was not able to read in your mind words you never typed. If you read the stickies, did you skipped the part 'how to ask questions'?

> I just wanted the opinions of more users than that of a forum administrator listing out his bunch of options.

Many people contributed to stickies beyond admins - in fact, more than bothered to answer your question. If you read the stickies, you would know that.

And if you mentioned that you read stickies, and which part he missed/misunderstand/needs better explanation, so we could skip "RTFS" and talk business. Improving stickies.

> Oh em gee, are you so upset I decided to skip over your "good answer" to get a random posters' sub-optimal opinion? 

You are free to use gathered advice or ignore it as you wish. I do not care much about you personally. I care more about the forum - I want forum to become more informative, less noise, place for interesting discussions, not for competition to repeat same answers for same questions, already answered in FAQ.

I am fully aware that I am in minority, but I did not gave up the fight yet :-)

---

### Post by LaRoza on 2008-08-12
> **pmasiar said:**
> 
I am fully aware that I am in minority, but I did not gave up the fight yet :-)

Mod: When we joined the Forum, we took an oath! 
Members: According to our station! All without exception! 
Mod: On the blood of our fathers, on the blood of our daughters, we swore to uphold the Code of Conduct! 
Members: Even to our dying breath! 
Mod: Those who would break this oath are heretics! Worthy of neither pity nor mercy nor responses! 
Members: We shall grind them into dust! Wipe them as excrement from our boots! 
Mod: And continue our march to glorious October 1st!
 

pmasiar: You are the Mod. The will of the Admins. But these are my newbs. Their lives matter to me, yours does not. 
LaRoza: That makes two of us.

---

### Post by pmasiar on 2008-08-12
> **LaRoza said:**
> pmasiar: You are the Mod. The will of the Admins. But these are my newbs. Their lives matter to me, yours does not. 
LaRoza: That makes two of us.

Your life (as many regulars which became my e-friends) does matter to me, so I am missing something? Even when you became mod/admin, I still considered you a friend. So it is over now?

In my previous response, I (maybe clumsily) wanted to express that I do not lose any sleep if one particular poster I never heard before decides to ignore my suggestions. Advice is free to take or free to leave, I would just consider not wasting my time typing answer to that particular person next time, that's all. There are plenty of forum members who are looking for answers and appreciate them. 

But if you (or any other of me e-friends) bothered to send me a message/advice, I would definitely read it and considered it. Does it count as 'you matter'?

---

### Post by LaRoza on 2008-08-12
> **pmasiar said:**
> Your life (as many regulars which became my e-friends) does matter to me, so I am missing something? Even when you became mod/admin, I still considered you a friend. So it is over now?

In my previous response, I (maybe clumsily) wanted to express that I do not lose any sleep if one particular poster I never heard before decides to ignore my suggestions. Advice is free to take or free to leave, I would just consider not wasting my time typing answer to that particular person next time, that's all. There are plenty of forum members who are looking for answers and appreciate them. 

But if you (or any other of me e-friends) bothered to send me a message/advice, I would definitely read it and considered it. Does it count as 'you matter'?

Start at 4:02, I couldn't find this scene alone: [http://www.youtube.com/watch?v=GWLLh8Sr6mM&feature=related](http://www.youtube.com/watch?v=GWLLh8Sr6mM&feature=related)

---

### Post by tinny on 2008-08-12
> 
Semi-human? I consider myself fully human, so it leaves you out?


If this forum was full human interaction my hands would be sore from slapping! :)

GUI, stands for "Graphical User Interface"? Just thought id check. 

Doesnt this forum have a PM function? Maybe their could be a war of the roses sticky?

---

### Post by tinny on 2008-08-12
> 
All the toolkits (except Java) mentioned have GUI designers and ports to many langauges. But the sticky linked to those toolkits and their GUI designers with the drag and dropping, so I guess that wasn't what you wanted?


@LaRoza, "except Java"...? What are you saying here? Java doesn't have GUI designers? 

[http://www.netbeans.org/features/java/swing.html](http://www.netbeans.org/features/java/swing.html)
[http://www.jformdesigner.com/](http://www.jformdesigner.com/)
Etc, etc, etc...

You can build swing apps with Jython and JRuby.

[http://aspn.activestate.com/ASPN/Mail/Message/Jython-users/2239336](http://aspn.activestate.com/ASPN/Mail/Message/Jython-users/2239336) 
[http://s2s.org/code/jruby/TreeDemo.rb](http://s2s.org/code/jruby/TreeDemo.rb)

Maybe I misinterpreted your post?

---

### Post by LaRoza on 2008-08-12
> **tinny said:**
> @LaRoza, "except Java"...? What are you saying here? Java doesn't have GUI designers? 

[http://www.netbeans.org/features/java/swing.html](http://www.netbeans.org/features/java/swing.html)
[http://www.jformdesigner.com/](http://www.jformdesigner.com/)
Etc, etc, etc...

You can build swing apps with Jython and JRuby.

[http://aspn.activestate.com/ASPN/Mail/Message/Jython-users/2239336](http://aspn.activestate.com/ASPN/Mail/Message/Jython-users/2239336) 
[http://s2s.org/code/jruby/TreeDemo.rb](http://s2s.org/code/jruby/TreeDemo.rb)

Maybe I misinterpreted your post?

No, I meant the GUI toolkits mentioned were all ported to other language except Java's, not that Java doesn't have a GUI toolkit/designer.

---

### Post by tinny on 2008-08-12
> **LaRoza said:**
> No, I meant the GUI toolkits mentioned were all ported to other language except Java's, not that Java doesn't have a GUI toolkit/designer.

Check this out

[http://en.wikipedia.org/wiki/Java-gnome](http://en.wikipedia.org/wiki/Java-gnome)

---

### Post by LaRoza on 2008-08-12
> **tinny said:**
> Check this out

[http://en.wikipedia.org/wiki/Java-gnome](http://en.wikipedia.org/wiki/Java-gnome)

I meant, the GUI toolkits (QT, GTK, wxWidgets, etc) were ported to many languages except Java's (Swing) which is for Java only.

---

### Post by tinny on 2008-08-12
> **LaRoza said:**
> I meant, the GUI toolkits (QT, GTK, wxWidgets, etc) were ported to many languages except Java's (Swing) which is for Java only.

Well strictly speaking not ports, but..

Jython, JRuby (post #27) and maybe Pnuts (not sure about that one) can use Swing.

Edit: Yep Pnuts does too [http://www.ddj.com/windows/184403965#l2](http://www.ddj.com/windows/184403965#l2)

---

### Post by LaRoza on 2008-08-12
> **tinny said:**
> Well strictly speaking not ports, but..

Jython, JRuby (post #27) and maybe Pnuts (not sure about that one) can use Swing.

Edit: Yep Pnuts does too [http://www.ddj.com/windows/184403965#l2](http://www.ddj.com/windows/184403965#l2)

They are on Java ;)

---

### Post by tinny on 2008-08-12
> **LaRoza said:**
> They are on Java ;)

Yeah, I was cheating.

Right thats it! Im going to port swing to C just to annoy you. :lolflag:

---

### Post by LaRoza on 2008-08-12
> **tinny said:**
> Right thats it! Im going to port swing to C just to annoy you. 

That would be interesting. I don't think it is possible though. Perhaps port C to Java...

---

### Post by tinny on 2008-08-12
> 
Perhaps port C to Java...


And call it the most inefficient compiler ever created.

---

### Post by LaRoza on 2008-08-12
> **tinny said:**
> And call it the most inefficient compiler ever created.

Please do not put spaces in the compilers name! Use an acronym. "tmicec"

---

### Post by Shin_Gouki2501 on 2008-08-12
I think its important to point out the diffrent abstraction levels in GUI-Programming.
( I really like to use Eclipse API as an example here ;) )
SWT - Offers you a Java Widget Library which is fundamental for GUI -Programming

JFace
JFace Compontens allow you to programm according to the MVC(see wikipedia)
Apporach. If you do a bit "more" with GUI's you realizse SOON that its nice and necessary to keep a clean distinction between Model and View.
Viewers enable you to easily Display data. You have so many options to configurare your desired Look ( LabelProvider!).
On top of that you get ViewerSorter! Ever tried impelmenting a GUI Table and custom sorting options? Using Viewersorter it was just so easy for me.

There are tons of preconfigured ( easy to reconfigure for your needs) Dialogs. Examples: Input, Message, Progress- Dialog or even Wizards!
On my work i had to port an application and using a wizard as input concept was a very convenient way to do so.

And this is "just" Jface-Level.

On RCP you get access the Workbench and develop in OSGi Modules.( More incredibly stuff which enables you todo mroe with less code through an amazing API, there is a significant rise in RCP Applications in the Business ) If anyone cares i can elaborate this laters.

---

### Post by NathanB on 2008-08-12
> **LaRoza said:**
> That would be interesting. I don't think it is possible though. Perhaps port C to Java...

Already been done.  Since C is a small language, people write compilers for it almost as often as they write Basic interpreters.

[http://depth-first.com/articles/2006/10/16/compiling-c-to-java-bytecode](http://depth-first.com/articles/2006/10/16/compiling-c-to-java-bytecode)

Nathan.

---

### Post by nvteighen on 2008-08-12
> **LaRoza said:**
> Perhaps port C to Java...

In the name of the Sacred Cult of C, you're under arrest because of thinking and also daring to write such a blasphemous statement.

---

### Post by tinny on 2008-08-12
> **Shin_Gouki2501 said:**
> I think its important to point out the diffrent abstraction levels in GUI-Programming.
( I really like to use Eclipse API as an example here ;) )
SWT - Offers you a Java Widget Library which is fundamental for GUI -Programming

JFace
JFace Compontens allow you to programm according to the MVC(see wikipedia)
Apporach. If you do a bit "more" with GUI's you realizse SOON that its nice and necessary to keep a clean distinction between Model and View.
Viewers enable you to easily Display data. You have so many options to configurare your desired Look ( LabelProvider!).
On top of that you get ViewerSorter! Ever tried impelmenting a GUI Table and custom sorting options? Using Viewersorter it was just so easy for me.

There are tons of preconfigured ( easy to reconfigure for your needs) Dialogs. Examples: Input, Message, Progress- Dialog or even Wizards!
On my work i had to port an application and using a wizard as input concept was a very convenient way to do so.

And this is "just" Jface-Level.

On RCP you get access the Workbench and develop in OSGi Modules.( More incredibly stuff which enables you todo mroe with less code through an amazing API, there is a significant rise in RCP Applications in the Business ) If anyone cares i can elaborate this laters.

SWT JFace etc... Are all good, but remember the OP is just "Learning to program GUI".

---

### Post by Shin_Gouki2501 on 2008-08-12
so you think playing arround with "widgets" is the goal? Also i mention the "levels" of abstraction, if your happy with widegts stick with SWT or anythign else if you want to programm some "real" GUI-Applications you will fast see that writing every thing from scratch just is the WRONG way...

---

### Post by tinny on 2008-08-12
> **Shin_Gouki2501 said:**
> so you think playing arround with "widgets" is the goal? Also i mention the "levels" of abstraction, if your happy with widegts stick with SWT or anythign else if you want to programm some "real" GUI-Applications you will fast see that writing every thing from scratch just is the WRONG way...

Are you saying that learning to programming GUI's ("writing every thing from scratch") is the wrong way to  "Learning to program GUI"? The OP wants to learn, they are not concerned with productivity etc yet.

Dont get me wrong the approach you state is good, I just think it is a premature abstraction for someone that wants to learn. :)

---

### Post by Shin_Gouki2501 on 2008-08-12
To know the bascis is important since you build on up on that.

Its just important to know that "higher"-level APIs exist and when to use them.

---

### Post by Shin_Gouki2501 on 2008-08-14
To came back to topic i think that very important aspects of GUI - Programming are:
- Use Cases
This is hard to start off but its improtant to think about in detail what a application should/can do and what not!
- Object Model
If your programm is growing or you need to work in a team a clear object model becomes indispensable. It jsut makes everthing easier on the OO Level. Exchanging or transforming data within your application, persisting data to databases or other resources. 
- Lifecyle
If diffrent components interact it is important to keep in touch with the "flow" of data within your application. Sometimes UML Sequence diagrams do fine for that.

---

### Post by Ruhe on 2008-08-14
Let's think, what are the core technologies used today for GUI programing.
And what technology is the best to learn.
From my expirience, I can give this list:
**- MVC:** 
The most important part. Java swing made with this pattern in mind. Adobe Flex with it's mxml is awesome. It's like delayering web page. Model(text) in html, view in css, and controller in JavaScript.
**- Events:**
Event dispatching isn't so easy as it seems. Again, if compare Java and Flash, I give my choise to Flash(ActionScript 3.0).
It's very easy to build custom events, to listen, or to dispatch events. Everything is clean and clear. Java event dispatching system sucks.
**- DataBinding:**
If someone used databinding in Java or Adobe Flex, you know, what a pleasure it is. You must not to write tonns of getters and setters, just make a bean and bind it to some GUI components.
**- Threading:**
Java has a good support of threads. SwingWorker was the ray of light for Java1.5. And the brilliant of all the swing - [swing application framework]("https://appframework.dev.java.net/"), it shines like a gem. Read about it if you are Java programer.
Flash doesn't provide any threads or something like this. But it seems that flash coders do their job very well without threads.

This is from my own experience.
I guess you guys can write about GTK, QT, Mono and all other stuff from this point of view, not just writing "+1 for QT".
In gathering information here we can help each other. No one knows with what he had to face in the future. A basic knowledge obtained here will help overcome the problems;)

---

