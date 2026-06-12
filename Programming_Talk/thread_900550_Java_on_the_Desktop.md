---
title: "Java on the Desktop"
date: 2008-08-25
forum: Programming Talk
---

### Post by Shin_Gouki2501 on 2008-08-25
Hello to everyone interested into java and java desktop applications(the rest may please ignore this , ty).

Swing all-in-one example implementation:
[https://substance.dev.java.net/webstart/test.jnlp](https://substance.dev.java.net/webstart/test.jnlp)

Really nice example build with netbeans platform:
[http://bluemarine.tidalwave.it/](http://bluemarine.tidalwave.it/)

Here is a really nice article which gievs you also a nice introduction:
[http://netbeans.dzone.com/news/from-pain-gain-swing-and-netbe?page=0%2C0](http://netbeans.dzone.com/news/from-pain-gain-swing-and-netbe?page=0%2C0)

Eclipse RCP(look eclipse rcp wiki side for more examples):
[http://www.rssowl.org/](http://www.rssowl.org/)


enjoy your java desktop programming :)

never forget there are incredible thigns you can do with java:
[http://www.pushing-pixels.org/?p=424](http://www.pushing-pixels.org/?p=424)

---

### Post by Ruhe on 2008-08-25
Sorry, but for me java desktop(swing) programming seems horrible.
I think that it's easier to to develop a spacecraft than build a java swing application.
Currently I'm working on very large program. The main window has about 70-80 different controls (comboboxes, inputs, buttons, tables...).
It's not our decision, we just got a sketch and task.
A lot of elements are tightly coupled(damned business logic). Lots of actionlisteners. We are encourage customer to allow refactoring (actually rewriting) this app.
Now I'm looking at Swing Application Framework, Matisse (NetBeans GUI builder).
I want to invite my collegues to use Swing Application Framework to handle the application (actions, menus, backround tasks and everything what this framework can do).
Split the interface in some independent panels, and bind a bean to each panel. This will be the VIEW part of MVC.
Controllers would listen to bean's properties. And get/set data on gui only through this beans. So I want to concentrate event processing in one place.

Is it good solution for large applications with complex and confusing business-logic?

If we'd use Adobe Flex, half of problems would go away because of good implemented databinding and event dispatching in flex.
But we have to work with java.

---

### Post by tinny on 2008-08-26
> **Shin_Gouki2501 said:**
> Hello to everyone interested into java and java desktop applications(the rest may please ignore this , ty).

Swing all-in-one example implementation:
[https://substance.dev.java.net/webstart/test.jnlp](https://substance.dev.java.net/webstart/test.jnlp)


I have used this lib a lot and its really good! 

> **Shin_Gouki2501 said:**
> 
Really nice example build with netbeans platform:
[http://bluemarine.tidalwave.it/](http://bluemarine.tidalwave.it/)


To justify the use of the NetBeans platform you need to be developing a very large application (Takes awhile to get up to speed on and its fat).

> **Shin_Gouki2501 said:**
> 
enjoy your java desktop programming :)

never forget there are incredible thigns you can do with java:
[http://www.pushing-pixels.org/?p=424](http://www.pushing-pixels.org/?p=424)

Yes, but generally not on the Desktop :( 

> **Ruhe said:**
> Sorry, but for me java desktop(swing) programming seems horrible.
I think that it's easier to to develop a spacecraft than build a java swing application.
Currently I'm working on very large program. The main window has about 70-80 different controls (comboboxes, inputs, buttons, tables...).
It's not our decision, we just got a sketch and task.
A lot of elements are tightly coupled(damned business logic). Lots of actionlisteners. We are encourage customer to allow refactoring (actually rewriting) this app.
Now I'm looking at Swing Application Framework, Matisse (NetBeans GUI builder).
I want to invite my collegues to use Swing Application Framework to handle the application (actions, menus, backround tasks and everything what this framework can do).
Split the interface in some independent panels, and bind a bean to each panel. This will be the VIEW part of MVC.
Controllers would listen to bean's properties. And get/set data on gui only through this beans. So I want to concentrate event processing in one place.

Is it good solution for large applications with complex and confusing business-logic?

If we'd use Adobe Flex, half of problems would go away because of good implemented databinding and event dispatching in flex.
But we have to work with java.

Sounds to me like your problem is bad architecture not Swing (Read over your post you have pretty much said that yourself).

Yes, MVC is the way to go :)

Have a look at [JFace]("http://en.wikipedia.org/wiki/JFace") + [SWT]("http://www.eclipse.org/swt/")

or 

[Scope]("http://scope.sourceforge.net/") (Can be used with Swing I think...)

Swing is not the problem, its the way that people use swing (its had massive performance improvements in Java 6).

BTW: I dont like GUI builders. They tend to produce bad code! (including Matisse) We write code in modern languages for the benefit of developers, so therefore the codes primary use should be to tell other developers what is going on. GUI builders code just confuses developers and is only maintainable to a point.

---

### Post by aloshbennett on 2008-08-26
Flex as a desktop programming tool? I wouldnt do that. Half of your problem related to UI can be solved. Thats pretty much it. For the other half of implementing business logic, you would be stuck making serverside calls to your localhost.

Think about database connectivity, threading, encoding, security or whatever your app is supposed to do.

Flex is a great tool for a rich internet client, not for desktop applications.

---

### Post by tinny on 2008-08-26
> **aloshbennett said:**
> Flex as a desktop programming tool? I wouldnt do that. Half of your problem related to UI can be solved. Thats pretty much it. For the other half of implementing business logic, you would be stuck making serverside calls to your localhost.

Think about database connectivity, threading, encoding, security or whatever your app is supposed to do.

Flex is a great tool for a rich internet client, not for desktop applications.

I know you can use Flex on top of J2EE, I wonder if you can call Java classes in J2SE?

We also have [JavaFX]("http://www.javafx.com/") (a Flex competitor). It seems to be targeted at multimedia type applications. (JavaFX can call J2SE classes)

---

### Post by aloshbennett on 2008-08-26
There's no native calling of java from flex. You have to make remote object calls.

---

### Post by Shin_Gouki2501 on 2008-08-26
> **Ruhe said:**
> Sorry, but for me java desktop(swing) programming seems horrible.
I think that it's easier to to develop a spacecraft than build a java swing application.
Currently I'm working on very large program. The main window has about 70-80 different controls (comboboxes, inputs, buttons, tables...).
It's not our decision, we just got a sketch and task.
A lot of elements are tightly coupled(damned business logic). Lots of actionlisteners. We are encourage customer to allow refactoring (actually rewriting) this app.
Now I'm looking at Swing Application Framework, Matisse (NetBeans GUI builder).
I want to invite my collegues to use Swing Application Framework to handle the application (actions, menus, backround tasks and everything what this framework can do).
Split the interface in some independent panels, and bind a bean to each panel. This will be the VIEW part of MVC.
Controllers would listen to bean's properties. And get/set data on gui only through this beans. So I want to concentrate event processing in one place.

Is it good solution for large applications with complex and confusing business-logic?

If we'd use Adobe Flex, half of problems would go away because of good implemented databinding and event dispatching in flex.
But we have to work with java.
wow that sounds nasty :D

but rest assure bad architecture is not  java related ;)
You can code ugly in every language. As for applciation frameworks and databinding. You can do those using the Swing Framework or Eclipse RCP btu however you need to think of good design and you Components interact in their lifecycle.

For me that works pretty well :D

wbr Shin Gouki

---

### Post by Ruhe on 2008-08-26
Ok, I had to be more accurate with my first post here.
I'm not a noob who just started to program in java.
That program on which we work now was made before us by other developers on jdk 1.5. We now add new features to this program and try to fight with it.

Imagine a form with 70-90 controls. Imagine how much java code goes to layout all this things.
One of the biggest lacks of swing (imo) is that it doesn't have declarative layou&#1077; ability. Today we see some new attempts on creating xml-based swing helpers. If compare this with mxml syntax in Flex I bet that java sucks in this apect. Flex lets developer to declaratively layout application controls (with nice gui builder, or by writing mxml by hands). If you need to dinamically create some gui parts than you can use action script.

Imagine how it's difficult to fight with that amount of controls. Some of them are date fields, some - comboboxes, some - edit fields, and most part - are JFormattedTextField. Now we don't have any databinding, and when user presses "save" button, a giant method gathers all the information from all fields and sends it as a bean to cluster - app server (that is what we did, before us application connected to db itself directly).
But if we have had a beans binded to every part of the gui, so half of problems would go away. So easy to gather all beans and send them to app server as a big bean.

And do you really like the event dispatching system in swing? Do you really think that it is good?
Read what writes Bruce Eckel about this. He has much more authority than me :)
[http://www.artima.com/weblogs/viewpost.jsp?thread=193593](http://www.artima.com/weblogs/viewpost.jsp?thread=193593)
[http://www.infoq.com/news/2007/01/eckel-flex](http://www.infoq.com/news/2007/01/eckel-flex)

---

### Post by Shin_Gouki2501 on 2008-08-26
bTW: no one said you are  a noob or such :)
the "gigantic" bean won't work so easy either. I'm currently working on a SWT/Jface PRoject there is also a form which ( only) has about 30 controls. Ofcourse layout and such can be a pain but once its doen it doesn'T change much ( at least here ;) )
Databinding or Bean binding is non trivial as if you look for JFace Databinding you will find quite uncomfortable exampel. You have to control all possible aspects of the beans lifecyle its kinda hart.
I don't use the "offical" one but a custom one which works nice for my stuff.

---

### Post by thomasaaron on 2008-08-26
Well, a lot of what has already been said here is above my head, as I'm not a professional programmer. But I find building swing apps with java and netbeans to be pretty straightforward. Most of my stuff is relatively small, but I can put together a nice java/swing app using netbeans *almost* as quickly as I can code the same thing up in Python/TK. 

I say this because laying out the GUI and creating the events is very fast with netbeans. All that's really left is the database calls (which I've built a nice class to handle - I've been able to re-use it on a number of apps) and processing the data to and from the various fields, etc...

Just a noob opinion, though.

---

### Post by tinny on 2008-08-26
BTW: Using Swing correctly not only means implementing a good MVC architecture but also knowing what Layout managers to use when. (and combinations of layout managers).

E.g. I try to stay away from GridBagLayout and instead use combinations of Grid and Box layout. But this is just one approach...

Also creating your own "helper" common layout panels helps

---

### Post by Reiger on 2008-08-27
Yeah that really is the hardest part; and is what makes Swing programming potentially very tedious work. Choosing the wrong layout and not realising it in time means often rewriting parts of code already covered by other layout managers which do what you want out of the box.

I think that's the only problem with Java's SWING: there is so much to choose from it can be hard to make the right choice.

---

### Post by Zugzwang on 2008-08-27
> **tinny said:**
> E.g. I try to stay away from GridBagLayout and instead use combinations of Grid and Box layout. But this is just one approach...


Oh, really? May I ask why? Whenever I make Java GUIs, GridBagLayout is the *only* Layout I am using. You can implement all of the GUIs I have seen so far this way.

---

### Post by thomasaaron on 2008-08-27
I've started using Absolute Layout. 

Since I'm programming on a Linux machine, I've found that Absolute Layout requires less adjusting when I do cross-platform testing on Windows and Mac.

Again, though, my apps are pretty small. I'd say most of them have twenty controls or less.

---

### Post by Ruhe on 2008-08-27
My opinion is that GUI builder - is the best approach.
Yes, it generates bad, ugly, unreadable code, but that code isn't supposed to be edited by hands. 
What if big team develops a big GUI java application. How much time should one developer spend to deal with hand written gui? And on other side, if all gui made by gui-builder, he can easily modify gui form, not spending time to find need control, not spending time to check if he did mistake in layout code.
I think that with time guys from sun will understand that and create some xml-based declarative layout syntax for swing. This will be a great step forward.
And last word - GridBagLayout was supposed to be used by gui-builders, not by human. It's very hard to read and understand code using gridbaglayout

---

### Post by tinny on 2008-08-27
> **Ruhe said:**
> My opinion is that GUI builder - is the best approach.
Yes, it generates bad, ugly, unreadable code, but that code isn't supposed to be edited by hands. 
What if big team develops a big GUI java application. How much time should one developer spend to deal with hand written gui? And on other side, if all gui made by gui-builder, he can easily modify gui form, not spending time to find need control, not spending time to check if he did mistake in layout code.
I think that with time guys from sun will understand that and create some xml-based declarative layout syntax for swing. This will be a great step forward.
And last word - GridBagLayout was supposed to be used by gui-builders, not by human. It's very hard to read and understand code using gridbaglayout

Bad code. :( (The value of a product in part is the quality of its code, not the tool it uses)

And you will locked into the same tool set forever. I believe that using a GUI builder is just avoiding actually learning Swing.

---

### Post by tinny on 2008-08-27
> **Zugzwang said:**
> Oh, really? May I ask why? Whenever I make Java GUIs, GridBagLayout is the *only* Layout I am using. You can implement all of the GUIs I have seen so far this way.

I just personally find it easier and that it gives me more control.

---

### Post by Ruhe on 2008-08-27
> **tinny said:**
> Bad code. :( (The value of a product in part is the quality of its code, not the tool it uses)

And you will locked into the same tool set forever. I believe that using a GUI builder is just avoiding actually learning Swing.

Yes, it's bad, I'm absolutely agree with you.

My hope is declarative xml-based language. Then gui-builder will generate good code, and developers will be happy. 
Take a look at mxml, used in Adobe Flex (example from wikipedia)
```

<?xml version="1.0" encoding="utf-8"?>
<mx:Application xmlns:mx="http://www.adobe.com/2006/mxml">
    <mx:Array id="sampleArray">
        <mx:String>Sample Label 1</mx:String>
        <mx:String>Sample Label 2</mx:String>
    </mx:Array>
    <mx:Panel title="Example Panel">
        <mx:ComboBox dataProvider="{sampleArray}"></mx:ComboBox>
    </mx:Panel>
</mx:Application>

```

Isn't it awesome?
That's what I would like to see in java. And it seems not so difficult to make such syntax and a gui-builder for such syntax.

---

### Post by mike_g on 2008-08-27
> Isn't it awesome?
That's what I would like to see in java. And it seems not so difficult to make such syntax and a gui-builder for such syntax.
Yeah I like it too :) gtk+ can build a ui from xml, which is pretty cool. As for a gui builder thats basically what glade does; outputs xml for gtk+. I'm pretty sure theres Java bindings for gtk.

---

### Post by tinny on 2008-08-27
> **Zugzwang said:**
> Oh, really? May I ask why? Whenever I make Java GUIs, GridBagLayout is the *only* Layout I am using. You can implement all of the GUIs I have seen so far this way.

> **Ruhe said:**
> Yes, it's bad, I'm absolutely agree with you.

My hope is declarative xml-based language. Then gui-builder will generate good code, and developers will be happy. 
Take a look at mxml, used in Adobe Flex (example from wikipedia)
```

<?xml version="1.0" encoding="utf-8"?>
<mx:Application xmlns:mx="http://www.adobe.com/2006/mxml">
    <mx:Array id="sampleArray">
        <mx:String>Sample Label 1</mx:String>
        <mx:String>Sample Label 2</mx:String>
    </mx:Array>
    <mx:Panel title="Example Panel">
        <mx:ComboBox dataProvider="{sampleArray}"></mx:ComboBox>
    </mx:Panel>
</mx:Application>

```

Isn't it awesome?
That's what I would like to see in java. And it seems not so difficult to make such syntax and a gui-builder for such syntax.

I dont like it.

All that XML is just noise.

.Net has this XML type language and pretty much no one uses it.

[http://en.wikipedia.org/wiki/XAML](http://en.wikipedia.org/wiki/XAML)

---

### Post by Reiger on 2008-08-27
XML isn't noise in case you app depends on context (which you can (and implicitly will) specify in the XML) it cannot adequately gauge beforehand.

And it's nice to be able to have an essentially extensible GUI. Especially if you want your end user to be able to influence the GUI of your app.

But from an efficiency P.O.V. it's not all that shocking. It requires quite a bit of expensive parsing; so if you can afford it you should use native language instead. Not to mention that XML code is just a lot of work: I mean now you have to code both Java *and *XML as a developer!

---

### Post by Sayers on 2008-08-27
You can always use SWT if you for some reason dislike java's swing. I personally do a lot of game development so I rarely deal with the desktop. I really love the java language though. It's easy to understand and very tied in with objects.

---

### Post by mike_g on 2008-08-28
> I dont like it.

All that XML is just noise.

.Net has this XML type language and pretty much no one uses it.

Why would you describe it as noise? I would say its the opposite; it seperates the interface from the code; which, IMO reduces noise. Not only that, it is more portable between different languages and programs. 

Minor alterations can also be made to the interface w/o having to dig through miles of code, then recompile it. I have made several changes to my XFCE UI by simply editing a couple of XML files.

Its not only .net that use languages derived from XML from what I have seen XML based languages are quite widely used just often not very visible. While I would never use XML for a database, to me, UI layout seems like a perfect application for it.

---

### Post by CptPicard on 2008-08-28
> **mike_g said:**
> Why would you describe it as noise? I would say its the opposite; it seperates the interface from the code; which, IMO reduces noise.

It breaks the "don't repeat yourself" principle. The idea that interface should be separate from the code can be argued against... if the code must conform to the interface and the interface describes the code, and they must be kept in sync, why not look at the code and see what its interface is? This is one of the reasons why Java got annotations for example -- people noticed that there are XML generators from code and vice versa, so if it's automatable... what's the point exactly?

> 
Minor alterations can also be made to the interface w/o having to dig through miles of code, then recompile it.

I'll grant that something like wiring components together and configuration may be an appropriate application...

> 
Its not only .net that use languages derived from XML from what I have seen XML based languages are quite widely used just often not very visible.

An interesting point is btw that XML is, by structure, essentially a kind of neutered Lisp...

---

### Post by mike_g on 2008-08-28
> It breaks the "don't repeat yourself" principle. The idea that interface should be separate from the code can be argued against... if the code must conform to the interface and the interface describes the code, and they must be kept in sync, why not look at the code and see what its interface is? This is one of the reasons why Java got annotations for example -- people noticed that there are XML generators from code and vice versa, so if it's automatable... what's the point exactly?
Yeah, they would need to be kept in sync, but I would still find it easier to keep track of what is what by having them seperated. I currently have a Java app thats around 7500 lines of code most of which is mindless Swing crap all mashed together. This is probably due to bad design as i started on the prog when I was new to java; I dont think I have used annotations yet (maybe I should read about them). Still, looking at the way a UI can be described in XML makes it seem more appealing to me.

> An interesting point is btw that XML is, by structure, essentially a kind of neutered Lisp... 
I cant answer that accurately because I dont really know Lisp, but yeah maybe. XML basically just lets you create your own markup language. Edit: Lol, misread that part o_0

Out of these [SVG](http://wiki.svg.org/Main_Page) seems like one of the more interesting things to me.

---

### Post by tinny on 2008-08-28
> 
It breaks the "don't repeat yourself" principle. The idea that interface should be separate from the code can be argued against... if the code must conform to the interface and the interface describes the code, and they must be kept in sync, why not look at the code and see what its interface is? This is one of the reasons why Java got annotations for example -- people noticed that there are XML generators from code and vice versa, so if it's automatable... what's the point exactly?


+1

We have enough languages as it is. Every time you define an XML schema you are basically creating a new internal domain specific language (DSL).

My feeling is that you should get the fundamental problem right first (J2EE 5 annotations has done wonders for EJBs) and not fix it by producing yet another layer (a XML DSL). 

Also this coupling of XML to your code is a big problem for me. I hate making a change in my code only to then find out that I then need to dive into hundreds of lines of XML to make it work.

XML is good, but I think is over used in software.

---

### Post by mike_g on 2008-08-29
Ok, you guys might be right, but I'm not going to agree until I have made a hideous mess with XML first :p

---

### Post by Ruhe on 2008-08-29
> 
It breaks the "don't repeat yourself" principle. The idea that interface should be separate from the code can be argued against... if the code must conform to the interface and the interface describes the code, and they must be kept in sync, why not look at the code and see what its interface is? This is one of the reasons why Java got annotations for example -- people noticed that there are XML generators from code and vice versa, so if it's automatable... what's the point exactly?

I can't understand how can xml break the DRY principle :(
xml has a tree structure, which best feats to GUI. swing gui is just a hierarhy of graphical components.
xml namespaces let easily decompose gui in several components, and then build the hole interface including different components.
Yes, mxml is a DSL. But why you say about annotations?
How can they solve problem of building gui?
This xml-based layou isn't supposed to be interpreted by running programm.
Flex compiles mxml to ActionScript, so java could compile such code to boring GridBagLayout.
Layout should be always separated from all other parts of application.


> Also this coupling of XML to your code is a big problem for me. I hate making a change in my code only to then find out that I then need to dive into hundreds of lines of XML to make it work.
And browsing hundreds line of java swing code makes you happy, and looking on that code, you can imagine what the layout should be? :)
Good IDE support whould throw away such problems. I've worked with Flex for a long time. And every line of mxml is just like a standart line of ActionScript, so I could browse all the code easily, the same way, when I ctrl+clicked on some java method in eclipse, and it brings me to the method declaration.

---

