---
title: "JavaFX for an Rich internet application"
date: 2007-08-05
forum: Programming Talk
---

### Post by triptoe on 2007-08-05
Hey, I am looking at making a pictionary like program. So far my choices are:

Flash, silverlight, and now javaFX.

i am kind of leery of using silverlight because it is microsoft. With flash i am leery because they have a poor track record of linux support... and their beta flash driver crashes my browser constantly.

I am looking at trying out javafx but what do you think? has anyone tried it? The downside I have seen is that the java runtime takes alot of background memory and is slow to load. However i just found this website : 

[http://www.theserverside.com/news/thread.tss?thread_id=45463](http://www.theserverside.com/news/thread.tss?thread_id=45463)

> Ethan Nicholas says that a lightweight, Consumer JRE is not a rumor. Sun is working on it and it will be available in the first half of 2008. Most people were so busy speculating about what JavaFX means (or doesn't) that they missed the actual announcement. The promise of JavaFX is likely tied to the Consumer JRE. Ethan says:

    The Consumer JRE is a release of Java 6 targeted at making the end-user experience better, meaning smaller downloads, faster installs, better graphics performance, smoother installation, faster startup, better reliability, and a bunch of other nice enhancements.

The Consumer JRE will allow execution of a typical Swing applications with a JVM installation of 3 to 4 MB as downloaded, and additional libraries and JVM elements will be installed on-demand, and in-place, when needed and without creating a myriad of JRE versions on the end-user's hard disk.

This seems to me like a good option... however i tried one of their demos on their site and the application would not load in the browser. It loaded in it's own window. So i am wondering will it ever be able to plug into the browser? Anyone know? thanks

---

### Post by pmasiar on 2007-08-05
First, full disclosure: I have no first-hand experience with neither technology. All suggestions are based on opinions I read, google for links if you want more details or don't believe me :-)

Bruce Eckel, well-known Java expert, used Flash for his training course, he is dissatisfied with Java - as missed promise. Maybe after 10 years they will do it right, but ... we all know that 80% of software projects fail, or miss schedule, or drop features. So until JavaFX is there, it is just vaporware. Will it also decrease divorce rate and stop global warming? Nobody knows.

Silverlight is very interesting technology, because looks like MSFT is sadly the only company that "gets it" - that right way is to have libarien in compiled statically typed language glued together by dynamic ("scripting") language, and they optimize CLR runtime to be good for dynamic languages. They hired former developer of Jython (to create IronPython), and now also Ruby (Ruby on Steel). I have no illusion MSFT will hurry to make this technology available for Linux (in fact, I don't believe they ever will, unless forced by a court decision), because for them it is important differentiating factor from free platform (GNU/Linux). 

Mono is not a solution, because as follower (forced to reimplement product of a competitor, feature by feature, bugs and warts) you can hardly be innovative, and product purchase price is only small part of total cost of ownership.

I am waiting what Google's response will be, because they don't want to be stuck following competitor, but also don't want to get stuck footing a bill for developing product for small niche market.

My bet would be: "neither of above", we need completely free implementation (MIT, Apache, BSD or GNU). many developers (including me) are reluctant to invest time learning proprietary technology - burned couple times, no more if I can avoid it.

So far we have AJAX. Yes it sucks, but it is open standard, with known implementation bugs, and is installed everywhere. Ubiquity is more important than featuritis.

What are rumors in Sun? Will JavaFX be GPLed?

---

### Post by triptoe on 2007-08-05
Here is a little charge that shows some of the differences between them. While flex is OSS, flash is closed. Javafx however is Open source... and seems like the most open solution there is which is why I am looking at it with a keen eye.

Javafx is clearly not vaporware either... you can see some of the demos on their site already.. and write some programs. The part that is rumor and vaporware is the newer JVM.

this part is a rumor: [http://www.theserverside.com/news/thread.tss?thread_id=45463](http://www.theserverside.com/news/thread.tss?thread_id=45463)

But then again My prog won't be done for a year or more anyway so it is of little consequence the wait . The question is will it come?

> Ethan Nicholas says that a lightweight, Consumer JRE is not a rumor. Sun is working on it and it will be available in the first half of 2008. Most people were so busy speculating about what JavaFX means (or doesn't) that they missed the actual announcement. The promise of JavaFX is likely tied to the Consumer JRE. Ethan says:

    The Consumer JRE is a release of Java 6 targeted at making the end-user experience better, meaning smaller downloads, faster installs, better graphics performance, smoother installation, faster startup, better reliability, and a bunch of other nice enhancements.

The Consumer JRE will allow execution of a typical Swing applications with a JVM installation of 3 to 4 MB as downloaded, and additional libraries and JVM elements will be installed on-demand, and in-place, when needed and without creating a myriad of JRE versions on the end-user's hard disk.

Is the Consumer JRE a good idea? Do you think it stands a fighting chance against Adobe's Flash or Microsoft's .Net? How does this environment stack up against proven, portable technologies like Qt that ISVs prefer for portable desktop applications?


---

### Post by triptoe on 2007-08-05
With my little knowledge of the different RIA's .. here is what I currently think about them:

Flash,

Cons: while flex is OSS, on the client side flash is closed source. This in the past has had trouble with linux. I want to support something truly cross platform. I don't like that flash is closed source.. although there is an open source implementation but it is impossible to keep up with the closed one.

Pro's installed on a very wide client base, is small and lightweight.. can do what i want it.. flex is OSS

silverlight

cons: it seems like anything microsoft touches is dangerous. Like mono, what are the patent implications? what are the chances that it will be truly cross platform? If they intended it to be crossplatform there would already be a linux client on their DL page along with the other choices. Supposedly mono will enable linux users to use silverlight... and i have heard various good and bad things about mono. I suspect that it is overblown.. and that using mono is actually safe but then I am not sure.

Pros: the pro seems to be that silverlight with the CLR is the most elegant solution as far as coding and performance. Look at this page here: [http://blogs.zdnet.com/Stewart/?p=459](http://blogs.zdnet.com/Stewart/?p=459)

The silverlight with CLR gets about 40% better performance than flash. Talk about nice.

Javafx

cons: It seems that the JVM is kind of large.. when i load the demos on their sites it takes alot of time to load. The benchmark from the site above shows javafx as being slowest by far, although it is a relatively new technology. So what are the chances that in the future it will get faster? Supposedly a small client install of a JVM is rumored to be in the works for early 2008 [http://www.theserverside.com/news/thread.tss?thread_id=45463](http://www.theserverside.com/news/thread.tss?thread_id=45463)

pros: the pro seems to be that javafx seems to be the most open choice and cross platform. According to this site it is the only one that is GPL'ed [http://ttlnews.blogspot.com/2007/05/test_22.html](http://ttlnews.blogspot.com/2007/05/test_22.html)
Will the smaller client JVM be as well though? Is the current JVM

---

### Post by laxmanb on 2007-08-06
Java FX isn't ready yet - It needs a compiler for example. Sun have also not released their content production tool for Java FX. (like Expression for Silverlight)

When it comes out, it might be a winner, The language seems cool, the Customer VM (definitely going to come out) sounds great.. try it if you want to!

PS: a pictionary program takes a year, really??

---

### Post by breaking on 2008-02-26
Sixth months had passed, and now it's a time to pull down our expectations.  Official mailing list has no worthy activity at all:
[https://openjfx.dev.java.net/servlets/ReadMsg?list=users&msgNo=2014](https://openjfx.dev.java.net/servlets/ReadMsg?list=users&msgNo=2014)

Also, google for "Consumer JRE" and try to get something hot out of the rotten swamp. Any good news out there?

---

### Post by lnostdal on 2008-02-26
.. RIAs ..

i doubt Mono or Moonlight will work out any good(#1) unless MS does what Sun does; release a full version of .NET with everything included for Linux then Open Source everything

meanwhile; Java and Sun is here already .. Applets and JWS is cool stuff .. the only thing needed now is:

* less download size
* less install time
* less startup time

..and, yes -- it seems these things are being worked on: [https://jdk6.dev.java.net/6uNea.html](https://jdk6.dev.java.net/6uNea.html)

..i'd say start building your back-ends right now :)


#1: or "good enough" .. (for me, to target as a developer)

---

### Post by breaking on 2008-02-27
Oh my :)
> 
Beta      March 08

What's about mobile applications?
Any way to start javafx applet on WM6.x PDA in nearest future? Or it's better to hook up with Android and let the JavaFX Mobile to overtake the market?

---

### Post by HuBaghdadi on 2008-02-27
JavaFX is still in its early stages, maybe it is not ready for the prime time yet.
I heard a lot of Adobe Flex but never tried it (and I will not).
If you are in a Java shop, I suggest you give GWT a shot, you will like it, take my word.
OpenLaszlo is also a powerful platform, you can export your application to Flash or Ajax.

---

### Post by woodenfox on 2009-04-16
JavaFX has come a long ways since February, deffinitly worth a second look.  I tried it again because of this game thats going on, PieTheory, it uses the SDK as part of it's challenges.  Worth checking out if your interested, you're going to need Virtualbox, SDK is still Mac/Win.

---

