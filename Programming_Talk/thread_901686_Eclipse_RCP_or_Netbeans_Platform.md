---
title: "Eclipse RCP or Netbeans Platform?"
date: 2008-08-26
forum: Programming Talk
---

### Post by CptPicard on 2008-08-26
Okay... time has come to bite the bullet and start considering writing a GUI for my "product" because I am starting to grow tired of pushing my data through a sequence of text files and command-line tools. The data manipulation workflow is also becoming so varied that a having a non-sequential GUI is warranted.

So we're essentially dealing with a Java "workbench" that allows spreadsheet-like views to sets of data that are then pushed through all sorts of operations, producing new spreadsheet-like views of data.

I have really never written proper desktop GUI apps before excluding some really simple Swing stuff, but am sort of drawn to the two dominant platforms for writing these kinds of "own the machine" applications, namely Eclipse and Netbeans. Would like to hear some opinions as to what the differences between the two are and which one is the more mature and/or easy to use...

---

### Post by mike_g on 2008-08-26
I cant comment on Eclipse as I have never used it but Netbeans is probably my favorite IDE ever. The code completion and error checking make creating all that verbose Swing (or whatever gui toolkit) code much faster.

I'm not so keen on the Netbeans form designer though as it locks you out of the code. If you need flexibility in your layout I'd recommend coding the UI by hand instead using layout managers. If you havent used them already the Table layout and Mig layout extensions are very handy.

IDK if you're planning on using Swing or not, but what I can say is that using netbeans with Swing can be very productive. I timed myself once: 500 lines of code in 3 hours. I think that must have been a personal record :D

---

### Post by CptPicard on 2008-08-26
Thanks, but I'm sort of more interested in the "platform" side of them -- I use both as IDEs in general already. As you probably know, both Eclipse and Netbeans themselves are built on top of reusable libraries :)

---

### Post by mike_g on 2008-08-26
Lol, yeah I guess you must have used netbeans before. I'm not really sure what the difference between the platform thing is, but I guess I'll find out :popcorn:

---

### Post by Shin_Gouki2501 on 2008-08-26
I have done some projects in SWT/JFace and a course in RCP.

I would suggest to start of with SWT and then take a look at JFace Viewer ( u love them) this combined with tabs and other JFace stuff "should" do the Job.
RCP is on a much higher level. The Workbench ofers you powerfull mechanisms like cross view selection provider/service. Using commands you can really plug things together ( comands, like CTRL+O) where they belong or you wish them to be. Context, Perspective and "View" Concetps ( not the Jface Viewer!) help to build flexible and customizables GUIs.  But as some things go easy some are difficult to achieave. So if you explorer JFace and need mroe then go RCP until then SWT + JFace is just fine. 

Good luck and hope to see soon something from your "product" ( funny that RCP calls its configured execuatble also : product ;)
:)

---

### Post by thomasaaron on 2008-08-26
I guess I'm not sure what you are asking either. I'll just register my opinion...

I've used Netbeans for Java/Swing programming now for about a year, and I'd NEVER give it up for Eclipse.

Eclipse is clever in its own right, but I find it to not be all that intuitive and it doesn't hold a candle to netbeans for designing swing guis.

---

### Post by jamesdcarroll on 2008-08-26
I've done Swing GUI programming in Eclipse and would never give it up for Netbeans (so there... :P  )

I'm currently learning RCP myself so the advice that I would give you is this: 
1. Eclipse uses SWT which is a thin layer that ultimately calls the underlying OSs GUI widgets. As such your app will look to your user like any other app that they run. Netbeans uses Swing (from what I've read) and therefore will have to carry its look and feel with it and will only be as good as the LnF. Both will ultimately suffers from Java's inherent 'least common denominator' problem.

2. I can't speak to Netbeans, but Eclipse (despite protestations to the contrary) has a particular perspective on what your app's overall design will be. Basically you will create panels that fall into two general categories: views that are dockable/movable about the edges of your app and editors which occupy the center of the screen. The classic "Explorer" style app: tree on the left, selected item on the right. Yes, you can work around that, but it will always feel like a fight. At least it does to me.

3. Eclipse has a plethora of apps built on it. The RCP book mentions that NASA uses it, IBM Lotus Expeditor (nee Workplace Client Technology) is built on it, and its the base for Apache's Directory Studio. Netbeans doesn't even have a 'Samples' page of fake apps that they taken the time to create. 'least not that I could find.

Bottomline, IMHO neither is perfect and neither is that horrible. My suggestion would to use Netbeans if you are comfortable with the IDE, Swing, and plan on reusing what you learn in other apps. I'm learning Eclipse RCP because I'm more comfortable in Eclipse and my company has forbade Netbeans.

---

### Post by tinny on 2008-08-27
I dont know a lot about either of these platforms expect this, your application has to be pretty big to justify the use of either of these. 

You dont need a platform to write a good Java desktop application.
..............................

I have followed the NetBeans learning trail and was quite impressed.

[http://www.netbeans.org/kb/trails/platform.html](http://www.netbeans.org/kb/trails/platform.html) (the NetBeans.org learning trails as you know CptPicard are pretty good)

Also there is a Maven archetype for a NetBeans Platform project ;) 

One of my first impressions was WOW this is going to force me to build one fat application! (not phat)

Then WOW the NetBeans IDE allows me to very quickly start developing with the NetBeans platform!

There where pretty much only three things that excited me about the NetBeans Platform.

1. The internal update system (Better than the Eclipse one IMO)
2. The internal persistence module (JavaDB)
3. Visual Library API for data visualization

At this point in my investigation I lost interest and just started writing a standard Swing application, with my own MVC implementation.

BTW, I have heard very good things about JFace. UI data binding.

My claim to fame Java desktop application used the following technologies.

Swing
[Substance]("https://substance.dev.java.net/")
[JFreeChart]("http://www.jfree.org/jfreechart/")
Toplink JPA (Yes thats right, J2EE 5 style annotations and all)
JavaDB (basically derby DB)
[JasperReports]("http://jasperforge.org/plugins/project/project_home.php?group_id=102")

This technology stack was great to work with and YES it did all work. :)

If you are interested in any of the above, just ask :)

So now to answer your question. I believe you should be using Visual studio 2008 to do your development.

---

### Post by jespdj on 2008-08-27
I have played a bit with Eclipse RCP, but never wrote a really serious application with it.

Nevertheless, my first impression of SWT and JFace was good, its design is much better than Java's AWT (and Swing). SWT is what AWT should have been (that's also the reason why IBM invented SWT years ago).

I don't know anything about the NetBeans platform besides that it's based on AWT and Swing.

---

### Post by dmartin on 2008-08-27
As a long time Java developer, I've done both.  But I'll throw you a twist.  My advice, should you choose to listen to it, is to use Java as your backend and Adobe Flex or Adobe Air as your front end.  Flex/Air is super easy for a Java developer, since ActionScript is fairly close (although, closer to JavaScript or C#).  And developing front-ends in Flex/Air is much, much, much easier to Swing or SWT.  The UI will look better, and gives you more opportunity to innovate.

The negatives:  Flex is open source, but the Flex Builder (pretty much a necessity) is not.  Also, you cannot create a native L&F if that's what you want.

---

### Post by mike_g on 2008-08-27
> The UI will look better, and gives you more opportunity to innovate.
I'd agree that Swing GUIs are very ugly, but from what I have heard SWT uses native widgets. If Flex does that too then thats good. Otherwise, as far as appearance goes, I'd definitely choose something that offers widgets that fit in with the environment.

---

### Post by tinny on 2008-08-27
> **dmartin said:**
> As a long time Java developer, I've done both.  But I'll throw you a twist.  My advice, should you choose to listen to it, is to use Java as your backend and Adobe Flex or Adobe Air as your front end.  Flex/Air is super easy for a Java developer, since ActionScript is fairly close (although, closer to JavaScript or C#).  And developing front-ends in Flex/Air is much, much, much easier to Swing or SWT.  The UI will look better, and gives you more opportunity to innovate.

The negatives:  Flex is open source, but the Flex Builder (pretty much a necessity) is not.  Also, you cannot create a native L&F if that's what you want.

Flex is very polished.

But, how do you call Java Objects/methods from Flex? My understanding is by using some sort of remoting system? (What a pain for a desktop application)

Also I dont believe CptPicard is after a multimedia type application, otherwise JavaFX would be worth a look.

---

### Post by CptPicard on 2008-08-27
Thanks guys... I'm being a bit partial to Netbeans atm as I really like the GUI designer and the persistence stuff looks interesting. I guess I'll use the platform as/if I need it. Anything that helps me use something out of the box is a huge plus though ofc :)

---

### Post by tinny on 2008-08-27
> **CptPicard said:**
> Thanks guys... I'm being a bit partial to Netbeans atm as I really like the GUI designer and the persistence stuff looks interesting. I guess I'll use the platform as/if I need it. Anything that helps me use something out of the box is a huge plus though ofc :)

GUI designer ](*,)

Please at least consider writing a raw Swing application or SWT + JFace application. Dont back yourself into a corner. ;)

---

### Post by CptPicard on 2008-08-27
> **tinny said:**
> GUI designer ](*,)

Hey, I at least admit to being a noob when I genuinely am.. ;)

---

### Post by tinny on 2008-08-27
> **CptPicard said:**
> Hey, I at least admit to being a noob when I genuinely am.. ;)

IMO you will invest as much time learning the Platform as you will learning Swing properly.

---

### Post by CptPicard on 2008-08-27
> **tinny said:**
> IMO you will invest as much time learning the Platform as you will learning Swing properly.

Okay. :)

---

### Post by Tomosaur on 2008-08-27
> **tinny said:**
> GUI designer ](*,)

Please at least consider writing a raw Swing application or SWT + JFace application. Dont back yourself into a corner. ;)

Writing a GUI by hand is incredibly boring and irritating - you don't have to think, you just have to go through the motions and do everything the way you are supposed to. There is nothing I hate more than writing GUI code, and I encourage people to use a GUI builder / designer whenever they can.

Sure, it's always best to understand the code that goes into a GUI, but if you want me to spend my whole time writing the same generic garbage every time I have to develop a GUI, then you've got another coming :P

On the other hand - the thing that really irritates me about using GUI builders is the action/event code, and for this I can't stand any automatic involvement on the part of the builder, preferring to do everything (even the basic method declarations!) by hand. For layouts and creating widgets and whatnot - the GUI builder is a god-send.

---

### Post by jamesdcarroll on 2008-08-27
Eclipse has a visual editor, its just that they've done such a horrible job supporting it that someone else has to step in (unofficially) and pick up the slack:

[http://www.ehecht.com/eclipse_ve/ve.html](http://www.ehecht.com/eclipse_ve/ve.html)

Its very functional and supports Swing and SWT. I've never had an issue with the code it generates, but then again ANY generator is gonna make assumptions about how you're gonna do things. As Tomosaur said, writing GUIs by hand is just plain annoying and tedious. And, for my money, forget about the layout managers, set it to *null*, plant your controls with *x, y, height, width,* and get on with your life.

If someone complains give them either the standard open source response ("Fix it yourself") or the standard closed source response ("We value your feedback and your concern has been forwarded to the development team for review")

:D

---

### Post by CptPicard on 2008-08-27
I personally have a strong dislike for writing GUI code as well, it is so... dumb and uninteresting. :) But alas, sometimes one has to have a GUI and if I've got a nice editor helping me do it, I'm all for it. So I guess plain JInternalFrame + my data grids in subwindows is going to be it... glad I wrote my toolkit in a reasonably modular manner.

---

### Post by tinny on 2008-08-27
> **jamesdcarroll said:**
> Eclipse has a visual editor, its just that they've done such a horrible job supporting it that someone else has to step in (unofficially) and pick up the slack:

[http://www.ehecht.com/eclipse_ve/ve.html](http://www.ehecht.com/eclipse_ve/ve.html)

Its very functional and supports Swing and SWT. I've never had an issue with the code it generates, but then again ANY generator is gonna make assumptions about how you're gonna do things. As Tomosaur said, writing GUIs by hand is just plain annoying and tedious. And, for my money, forget about the layout managers, set it to *null*, plant your controls with *x, y, height, width,* and get on with your life.

If someone complains give them either the standard open source response ("Fix it yourself") or the standard closed source response ("We value your feedback and your concern has been forwarded to the development team for review")

:D

Please tell me what projects you are involved in so that I can make sure I never use them :lolflag:

I hope the users never try and resize there window (x,y positioning)

---

### Post by Shin_Gouki2501 on 2008-10-04
Hey Captain!
How is your project going along? is there somethign you could show to the public, im kinda curious!

---

### Post by CptPicard on 2008-10-04
Actually, if I ever do write the GUI it will be just Swing, tinny is right.

And even if I did, this piece of code wouldn't really be meaningful to anyone outside our business -- unless of course you are doing similar sports betting as we are. And if you are, my boss would kill me for showing you what we've got :D

---

### Post by tinny on 2008-10-04
Yeah swing is fine. You have to write a mountain of boring code but IMO its quite easy once you have done the ground work and know how to use it.

I have attached a screen shot of a Swing application I play around with every now and then. Its a basic virus scanner.

It uses Swing and the substance L&F lib. If you need a Swing app to look good have a play with [Substance]("https://substance.dev.java.net/").

@CptPicard, is your application good enough to be Groovy? ;)

---

### Post by CptPicard on 2008-10-04
> 
@CptPicard, is your application good enough to be Groovy? ;)

Actually, I am reading on Groovy right now because I plan on doing GUI and other glue code in it in the future, and keep the number-crunching library internals as Java...

It really sucks that real, functional betting analysis tools by definition don't have a market, because selling these to a wide audience defeats their effectiveness. This would be cool stuff with a proper interface, but the business case just is not there right now :(

Then again, my boss plays my own money with these tools without taking his own cut, so I guess I should not be whining ;)

Are there any variable-odds games in New Zealand by any chance where the betting behaviour of the opposition is fully known? :)

---

### Post by tinny on 2008-10-04
> **CptPicard said:**
> 
Are there any variable-odds games in New Zealand by any chance where the betting behaviour of the opposition is fully known? :)

(I have no knowledge in this area)

If our all blacks rugby team are playing then all the New Zealand sheep will put a bet on them.

---

### Post by CptPicard on 2008-10-04
> **tinny said:**
> 
If our all blacks rugby team are playing then all the New Zealand sheep will put a bet on them.

This is a typical distortion that can be made good use of. You have no idea how much money we've made in ice hockey betting by playing against the Finnish national team whenever and whomever they play... patriotism can be expensive for the masses :)

Another typical fun money-maker is the fact that low match scores are always overplayed, people like playing safe so outcomes like 0-0, 0-1, 2-2... are absolutely never worth it in the long run.

---

### Post by tinny on 2008-10-04
> **CptPicard said:**
> This is a typical distortion that can be made good use of. You have no idea how much money we've made in ice hockey betting by playing against the Finnish national team whenever and whomever they play... patriotism can be expensive for the masses :)


Yeah New Zealand would be a text book example then. However we do have another distortion, your team is awesome! They are the best in the world except when it comes to the world cup :(

---

### Post by nvteighen on 2008-10-05
> **CptPicard said:**
> This is a typical distortion that can be made good use of. You have no idea how much money we've made in ice hockey betting by playing against the Finnish national team whenever and whomever they play... patriotism can be expensive for the masses :)


I prefer to stay patriot... (anyway, in Football/Soccer, Women Hockey, Basketball, Tennis and sometimes even Rugby, Argentina is a safe bet!)

---

### Post by tinny on 2008-10-05
> **nvteighen said:**
> sometimes even Rugby, Argentina is a safe bet!)

Not if you are taking the All Blacks on!

---

### Post by nvteighen on 2008-10-06
> **tinny said:**
> Not if you are taking the All Blacks on!
Yeah, you are the best, no doubt.

---

