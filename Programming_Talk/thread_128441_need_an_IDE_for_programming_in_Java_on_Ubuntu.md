---
title: "need an IDE for programming in Java on Ubuntu"
date: 2006-02-11
forum: Programming Talk
---

### Post by kvorion on 2006-02-11
Hello all,

Like the subject says, I need an IDE which I can use for programming in Java. I already have the Java software development kit which I installed using automatix. Although I can write programs in a text editor and go ahead, I would very much like it if I can do it using an IDE. 

So please help me find and IDE for java.

---

### Post by Greg2 on 2006-02-11
You can install DrPython or Eric with the Synaptic package manager, or install SPE from here:
[http://pythonide.stani.be/](http://pythonide.stani.be/)
SPE has the most features of the three, but as to which one is best... that is up to the individual user.

Edit: I just reread the title, lol. Sorry, but I must have had Python on my mind yesterday. :)

---

### Post by Corvillus on 2006-02-11
You can also get Eclipse with the Java Development Tools from the Universe repositories. The package you want is eclipse-jdt.

---

### Post by WelterPelter on 2006-02-11
Go with Eclipse. It's really excellent for Java programming.

---

### Post by kvorion on 2006-02-11
Thanks for the replies guys.

---

### Post by steve.horsley on 2006-02-12
If you are a beginner, you really want an IDE that's not too big, or you will spend all your time learning the IDE, not the language. For beginning, I recommend that you look at BlueJ ([http://www.bluej.org)](http://www.bluej.org)). It was designed for teaching java at university. It has the basics - editor, debugger, class diagrams, but doesn't ever get in your way.

Steve

---

### Post by cstudent on 2006-02-12
Eclipse: [www.eclipse.org](www.eclipse.org)
NetBeans: [www.netbeans.org](www.netbeans.org)

---

### Post by healychan on 2006-02-12
> If you are a beginner, you really want an IDE that's not too big, or you will spend all your time learning the IDE, not the language.

He is right. I believe Eclipse is too much for beginner.

If you find that Eclipse and NetBean are too heavy, try a new IDE called "geany". Although it is still at beta test stage but I love it because it is easy to use.

---

### Post by ZylGadis on 2006-02-12
You should start with gedit / pico / (insert generic text editor here). At least for your first two or three classes. This is the only way you will prevent yourself from being spoiled by an IDE. Then you may move up the line to something like SciTE, or possibly one of the other basic IDEs people have mentioned (I have not used them). Finally, move to Netbeans or Eclipse (I prefer Netbeans), or IDEA if you can afford it.

---

### Post by jerome bettis on 2006-02-12
you should not ever use pico ever, it's not for computer people.  if you want to use an old school editor, vim or emacs.  pico is like the notepad of unix, don't use it.

but for an ide, eclipse is pretty money.  netbeans is a clunky pig.

---

### Post by ZylGadis on 2006-02-12
I don't want to turn this into a flamewar, but please refrain from labeling IDEs in that way. For some weird reason my opinion on Netbeans vs Eclipse is exactly the opposite of yours.
And the whole purpose of starting simple is to concentrate on learning the language instead of the IDE. Vim or emacs will get in the way of any sensible person who is not "old-school" (and yes, I know how to use both, and I prefer not to use them). Pico does the job marvellously - clean and simple.

---

### Post by jerome bettis on 2006-02-12
[quote=Alex.P]I don't want to turn this into a flamewar, but please refrain from labeling IDEs in that way. For some weird reason my opinion on Netbeans vs Eclipse is exactly the opposite of yours.
And the whole purpose of starting simple is to concentrate on learning the language instead of the IDE. Vim or emacs will get in the way of any sensible person who is not "old-school" (and yes, I know how to use both, and I prefer not to use them). Pico does the job marvellously - clean and simple.[/quote] 
sorry but pico is total shit for a programmer.  it has no features at all, it's just designed to type text.  vim or any other ide has features a programmer should want to take advantage of.

i do agree with you though, if you're just starting out it's best to concentrate on what you're typing, not the program in which you are typing it.  learning a language and vim at the same time would be a bit much.  so i guess if you want to use pico to _start_ with, fine.  but after a few weeks you have to stop and learn how to use a real programmer's tool.

you really think eclipse is more of a pig than netbeans huh?

---

### Post by ZylGadis on 2006-02-12
I am glad we reached an agreement on pico.

I don't mind Eclipse as an IDE - it does the job well. I do mind, however, its being based on SWT and what is more, encouraging the use of SWT in projects. In my opinion SWT breaks the spirit of Java, as you need OS-specific libraries outside of the JRE to run it. Moreover, I believe it is simply a glorified AWT, and we know where AWT got us.
It is true that SWT sparked massive innovations to Swing in exactly the same way Eclipse brought about NetBeans's reemergence. Competition is always good. However, both NetBeans and Swing have gone a very long way since 2003 when they were indeed good-for-nothing clunky pigs. You'd be amazed at the functionality of NB5.0, which was released a few days ago, not to mention the upcoming Mustang (J2SE1.6) that ought to bring Java massively to the desktop, not in the least because of Swing innovations.

---

### Post by jeffjj on 2006-02-12
I have been a Java developer for quite a few years. Trust me, you want to use Eclipse. If you do web development then get yourself a subscription to MyEclipse ($30 a year and worth it).

I used to agree with people that said learn the language, not the IDE. Not anymore because the IDE does not get in your way...it just works. Plus things like code completion will help you learn the language more, not the other way around. I wish such an IDE would have been around when I first started programming. The less typing I have to do the better! I know how to type, now I just want to build software.

---

### Post by awi on 2006-02-13
I believe that **Eclipse** is the best tool available (without considering the one you have to pay for). 
Even when you are not going to use all of its features (I don't think that anybody is using ALL of it anyway :)  ), you can't compare the advantages that even a newbie will have, with the code assistant and the quick fix feature, not to mention the syntax highlighting, automatic import lines generation, etc.
Using a simple editor, and getting through the simple examples of java tutorials, should not take you more than a couple of days, the same amount of time I consider is going to take you an eclipse or java+eclipse tutorial, and you will be learning a tool that will definitively help you way longer and better than a terminal and a editor.
I used **Netbeans** for 2 1/2 years, and then switched to Eclipse, for good.
Even the NetBeans 5.0, recently showed up (without the profiler and Mobile Edition that I have not tried yet), are almost the same as 4.x, and almost the same as 3.x), and I'm not just saying it because I read some review, I actually used for 2 1/2 years the Forte's Form Editor (SUN's old IDE, based on Net Beans), and after that with the NetBeans 3.x and 4.x. The so called "new form editor" **Matisse,** is the basically the same it used to be, with the diference that now it has a name and a marketing crew that is making noise. 
That's one of the areas where Eclipse, as an IDE and without having to install third party plugins, is lacking, a good GUIs editor, but VE is going to be, in the near future.
I will go with Eclipse if your intention is not to pay for a tool, and even if you are, I still will consider going with eclipse and some paid plugin for specific tasks.

---

### Post by LordHunter317 on 2006-02-13
[QUOTE=Alex.P]I don't want to turn this into a flamewar, but please refrain from labeling IDEs in that way. For some weird reason my opinion on Netbeans vs Eclipse is exactly the opposite of yours.[/quote]Simpler answer: They're both crap, in their own unique special ways.  However, Netbeans is fixing that, Eclipse is just piling the crap on.

> In my opinion SWT breaks the spirit of Java,No, it doesn't.

> as you need OS-specific libraries outside of the JRE to run it.Which breaks WORA anyway for any self-contained application.  You still cannot rely on the JRE being installed on any system, and Sun has ensured that forever.  So blaming SWT without blaming the need for a JRE first is unfair.  The correct answer is, "WORA is a myth--blame Sun."

>  Moreover, I believe it is simply a glorified AWT, and we know where AWT got us.It got us that steaming pile known as Swing.  Which is nice in a few select ways, and terrible, terrible in most of the others.  It's a generally good concept marred by a terrible implementation and total lack of forethought in planning how to implement everything.

It's not clear Mustang will actually fix Swing's fundamental problems.  I'm not sure they can be, at this point.

---

### Post by kvorion on 2006-02-13
Well, since I am a newbie in Java now, I dont mind which IDE I use. But when I tried to install Eclipse from my synaptic, it said that a couple of packages on my system including azureus will have to be removed. I wasnt sure of what to do, so I stopped. Anybody got a clue why it is conflicting with azureus?

---

### Post by tmahmood on 2006-02-13
I'll say BlueJ is great for start, its very simple and easy yo use.

NetBeans 5 is also pretty good. I am using it right now. I have used 4 too. I feel performance is better then 4. and GUI designing is also pretty cool. I have Installed Mobility pack and its good too.

---

### Post by cstudent on 2006-02-13
[QUOTE=kvorion]Well, since I am a newbie in Java now, I dont mind which IDE I use. But when I tried to install Eclipse from my synaptic, it said that a couple of packages on my system including azureus will have to be removed. I wasnt sure of what to do, so I stopped. Anybody got a clue why it is conflicting with azureus?[/QUOTE]

I prefer to download the tarball direct from Eclipse and unpack it into my /opt directory. Eclipse just recently released version 3.1.2 and Synaptic is 3.1.1, I think.

---

### Post by kvorion on 2006-02-14
One more question. I checked out BlueJ's site. The installation file for linux is a .jar file. I was wondering how does one uninstall something that has been installed using a .jar or a .bin file. 

Synaptic and .deb packages are fine, but what about the rest? I remember when I was totally new to linux and was using FC3....I had installed Real PLayer from a .bin file and I was never able to uninstall it from my system because I did not know how to

---

### Post by LordHunter317 on 2006-02-14
You don't.  Simply run thge application with:```
java -jar app.jar
```

---

### Post by kvorion on 2006-02-14
So I am stuck with an application whether I like it or not? Kindly pardon my ignorance here. And what about the .bin installations? Is it possible to remove the applications installed using a .bin?

---

### Post by LordHunter317 on 2006-02-14
'Oh **uninstall.**  I read that as install.  My bad.  A Java application in a .jar is self-contained, just remove the jar.  As for a .bin, some will uninstall if you rerun with -uninstall or similiar.

---

### Post by kvorion on 2006-02-14
[QUOTE=LordHunter317]'Oh **uninstall.**  I read that as install.  My bad.  A Java application in a .jar is self-contained, just remove the jar.  As for a .bin, some will uninstall if you rerun with -uninstall or similiar.[/QUOTE]

Thanks...I was expecting that for the .jar file

---

### Post by ZylGadis on 2006-02-15
LordHunter, you would sound a bit more convincing if you were to actually put constructive arguments around your curt "No, it doesn't," "that steaming pile," and other popular expressions of yours. It would be even better if you were so kind as to indulge us in some code written by your omniscient figure, as well as mention some of your undoubtedly grand accomplishments on the programming scene.

Honestly, I've been reading through some of the topics here, and you look like the nastiest troll if there ever was one. You know the answer to anything, you always criticize other opinions (most often without giving the causes for their perceived wrongness), and you generally ruin any attempts for a constructive argument. I believe there would be a collective sigh of relief if you were to either remove yourself from this part of the forum, or change your attitude.

I won't even begin to argue about Swing, Netbeans or whatever else, as at this point that would not make any sense - there is nothing I would be arguing against. And I won't waste my time replying to you if you do your favourite "comment on each line of the other person's post without actually saying anything" trick.

---

### Post by LordHunter317 on 2006-02-15
[QUOTE=Alex.P]LordHunter, you would sound a bit more convincing if you were to actually put constructive arguments around your curt "No, it doesn't," "that steaming pile," and other popular expressions of yours.[/quote]On what, specifically?

Eclipse?  Everything they've added is slowly but surely making the IDE worse, not better.  Specifically, they've pulled a lot of functionality that used to be plugin-accessible back inside the Eclipse internals.  One pratical and important example is that it used to be possible to add a new authentication protocol to the CVS plugin, for example for sserver support, which Eclipse doesn't provide (it's coming, last I checked).  However somewhere between 3.0 and 3.1 (I forget exactly, some 3.1 milestone) they pulled all the protocol classes back inside the Eclipse API, for no apparent reason whatsoever.

The net effect is that you can't add a new CVS authentication protocol *at all* without reimplementing the entire protocol.   And it's not like the protocol code was actually wired to the socket code or the authentication code, it was already seperated out for the stuff Eclipse supported.

Seemingly retarded UI decisions are abound.  Why can't I place my tabs at the top or bottom of a set?  Why do all  minimized (quick-action or whatever they call it) sidesbars minimze to the same place, instead of in a bar beside them?  This is one thing Visual Studio gets right: I can have tabs that are open in a sidebar drawer and switch between them, and then have tabs that are minimized in that drawer.  Clicking on the name of the tab expands it out momentarily, and then retracts it when I refocus on my document.  

Let's talk about the web development tools they're working on.  They have no support for building an actual WAR (or didn't when I tried them), nor did it appear any real support was planned.  You can deploy, or you can package it yourself, meaning you have to do your own build.

They use ant to invoke xdoclet instead of invoking xdoclet directly.  This would be fine if it wasn't automatically triggered whenever you save a file after changing xdoclet attributes.  It's slow, it's painful, and effectively locks the whole IDE up.

Also, god forbid you don't use their file structure.  There's no way to change the layout besides manually editing the configuration, and some of it is hardcoded anyway.  Oops.

Even the JBoss stuff to do similiar is lightyears ahead, and it can't even do half the stuff the web dev tools eventually will.

As for Swing?  Tell me how to get the list of selected cells in a JTable when you can select by cell (as opposed to by row or by column) and when multiselection is enabled.  Then explain to me why all that work is required.  I can think of several other examples, but it's an easy one, and the code to illustrate my point can be found on Google pretty quickly.

There's a whole continual list of things like that.  DND support is **broken** (the datatransfer stuff), and a regression from AWT DND, which it is based on for DND anyway.  But the irony is that AWT DND is broken as well in several ways, but it's no longer meant for public use.  This means that as of late, Sun just closes any bugs files against java.awt.dnd regardless of merit.  The Java bug tracker will bear me out on this.

So Swing has no working DND beyond some really simple stuff.  Even then, the whole API is designed wrong, carries redundant information, and doesn't provide sufficent information where it should.

As I said, Swing is a good *idea* (Model-View is a useful design for GUI components to be flexible in what they can display and how they display it, without unnecessary complication) but it's clear that the execution placed in to actually implementing this idea was poor.

I'll give you another example: Why can the application control what L&F it appears in at all?  At most, it should be user configurable through a properties file.

And don't get me started on Java event handling.  There's so many issues there (dating all the way back to the birth of the language, where they stripped closures) that it's not even funny.  And for Swing, event handling is the *most important* generic concept.  And one that Sun got wrong.

> It would be even better if you were so kind as to indulge us in some code written by your omniscient figure, as well as mention some of your undoubtedly grand accomplishments on the programming scene.Why?  They're irrelvant.  It's a logical fallacy to even ask.  You judge my statements based on their merit and logic alone, not based on the person who's asking them.


> Honestly, I've been reading through some of the topics here, and you look like the nastiest troll if there ever was one. You don't know many trolls then, seriously.  I'm a timid kitten compared to a lot of people, though maybe not here so much.

> you always criticize other opinions (most often without giving the causes for their perceived wrongness),Criticial of the claims made perhaps.  I'm not criticial of the person making them. I could really care less, as a rule.

And what?  Most of what people say (including me, quite frequently) is either totally wrong or not totally correct.  

> and you generally ruin any attempts for a constructive argument.No, I don't.  You want to respond, feel free.  There's no ill-will against you unless you decide to attack me.  I may strongly-state what I feel, both in terms of fact and my own personal opinions, but unless I'm on the fence on something, there's no real reason to sugar-coat on the Internet.  It just clouds the issues.

> I believe there would be a collective sigh of relief if you were to either remove yourself from this part of the forum, or change your attitude.There would be a sigh of relief if you didn't engage in personal attacks.

> there is nothing I would be arguing against.If you feel I've been too terse, ask without attacking me and I'll be glad to elaborate, at length, if necessary.

> And I won't waste my time replying to you if you do your favourite "comment on each line of the other person's post without actually saying anything" trick.I say plently.  Just because I don't initally defend my statements in detail doesn't invalidate my reply.  It's only invalidiated when I refuse to provide detail when asked, and I've done nothing of the sort.

---

### Post by steve.horsley on 2006-02-16
[QUOTE=kvorion]One more question. I checked out BlueJ's site. The installation file for linux is a .jar file. I was wondering how does one uninstall something that has been installed using a .jar or a .bin file. 

Synaptic and .deb packages are fine, but what about the rest? I remember when I was totally new to linux and was using FC3....I had installed Real PLayer from a .bin file and I was never able to uninstall it from my system because I did not know how to[/QUOTE]
The BlueJ installer creates one directory to install into. I think it asks you where to put itself. It also looks for all possible j2sdk installations, asks which one to use and configures the application accordingly.

All you have to do to uninstall BlueJ is to delete thae installation directory. The only real reason for the installer is to set the configuration to point to the JDK.

P.S. 
I just found this - might give you a flavour: [http://www.bluej.org/papers/1999-11-JOOP4-blue-env.pdf](http://www.bluej.org/papers/1999-11-JOOP4-blue-env.pdf)
It's not java but liiks similar to BlueJ.

---

### Post by kvorion on 2006-02-17
[QUOTE=steve.horsley]The BlueJ installer creates one directory to install into. I think it asks you where to put itself. It also looks for all possible j2sdk installations, asks which one to use and configures the application accordingly.

All you have to do to uninstall BlueJ is to delete thae installation directory. The only real reason for the installer is to set the configuration to point to the JDK.

P.S. 
I just found this - might give you a flavour: [http://www.bluej.org/papers/1999-11-JOOP4-blue-env.pdf](http://www.bluej.org/papers/1999-11-JOOP4-blue-env.pdf)
It's not java but liiks similar to BlueJ.[/QUOTE]

I installed BlueJ and have started using it. Looks pretty good. Thanks

---

### Post by Van_Gogh on 2006-02-18
I don't like to talk negatively about persons, but I agree with Alex P.: replying only "no, it's not.", "No, you're wrong.", "That really shows your lack of understanding of the topic." etc. is a very rude way to answer someones posts(even if what they're saying is wrong) and, more importantly, just empty information. I mean, noone cares if LordHunter or someone else thinks that argument X or opinion Y is wrong: what we care about if *why* argument X or opinion Y is wrong.

So, instead of "no, it's not." please use "no it's not because of...." followed by an argument and I do think LordHunter's posts then could become very informative and enjoyable. His argument in his last post for why he doesn't like Eclipse seem well thought out and is absolutely infinitely better than just "They're both crap, in their own unique special ways. However, Netbeans is fixing that, Eclipse is just piling the crap on."(no argumentation).

Ok, that was my share of person-bashing for this year. I'll stop now.

---

### Post by LordHunter317 on 2006-02-18
[QUOTE=Van_Gogh]So, instead of "no, it's not." please use "no it's not because of...." followed by an argument and I do think LordHunter's posts then could become very informative and enjoyable.[/quote]**Or you know, *like I've said multiple times,* when I'n terse on anything, *just ask me and I'll elaborate at length.***

Frankly, I didn't think I'd have to elaborate on either because the facts that Eclipse is a poor IDE and Swing is a poor GUI are widely held, and the reasons for those views are widely known.

Netbeans too, when I think about it.  And JDeveloper, which has it's own lenghty set of issues.  The only Java IDE I hear consistently positive praise for is IDEA.

And my reasons for disliking them aren't extra-ordinary, or unobvious if you just sit down and use or program with the tools.  None of it is rocket science.

Besides, half the time I get bitched at for being too terse; the other half, too verbose.  Since there seems to be no happy medium here, I'll continue with my current policy.  

If other posters can't be civilized enough to simply ask for further clarification,  then maybe they should take a course in English, or manners, or something.  I don't really know what to say to that since I've paid others that courtesy many times here.

---

