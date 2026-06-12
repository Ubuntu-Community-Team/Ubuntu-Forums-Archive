---
title: "RIA with JavaFX, any good?"
date: 2008-11-29
forum: Programming Talk
---

### Post by tinny on 2008-11-29
Recently I have become very interested in RIA development. The main reason for this is that I am just sick and tired of HTML (and JSP, JSF).

Over the last couple of months I have been playing with Flex and GWT. I have really enjoyed using Flex, I believe it is a huge improvement over HTML (IMHO) and makes it so easy for me to make good looking UI's without much trouble at all.

So, what is JavaFX like? Who is developing or playing with it? Does it compete with Flex in the RIA space?

As you know time is limited and I am really trying to gauge if JavaFX is worth the time for investigation...?

One thing that I am hugely skeptical of is that according to what I have read so far JavaFX applications deployed on the web are just Java Applets or standard swing applications under the hood. Im sorry but Java applets just suck!!!

---

### Post by cl333r on 2008-11-29
Of course Flex is an improvement over HTML..
Since JavaFX 1.0 comes out Dec. 2nd I would suggest waiting a few days, then having a close look at it and make decisions.
Read more about what applets are starting with java 6 udpate 10. Just google.

---

### Post by tinny on 2008-12-02
Yep I will be checking it out on 4th Dec.

Heres my simplistic view of JavaFX right now.

**Advantages:**

A unified toolset and development ecosystem. I can use the same free tools I use for Java development now ([http://www.netbeans.org/features/javafx/index.html](http://www.netbeans.org/features/javafx/index.html)). I can also leverage off my existing Java platform knowledge.

Easier to interface into back end Java systems. Flex is ok at interfacing into Java back ends, however it is a little clumbersome.

**Disadvantages**  

Download of the JVM is required. The user requires version 6.?? of the JVM on there system. This means that at some point they will need to download it just to view your application. The JVM is a ~15MB download, Flash (used for flex) is 1.8MB and Silverlight is 4MB.

Java applets have given people a poor perception of client side Java. Because of this its going to be harder for me to sell and JavaFX solution than an Adobe Flex solution IMO.

So the only real advantages I can see right now are for the developer. When selecting a technology you should be looking at selecting one that adds value for the customer, right? After all the developer doesnt have to use the application, the user does.

---

### Post by tinny on 2008-12-04
It seems that the JVM size issue has been addressed in version 1.6.10. They have introduced a new concept they call the [Java kernel]("http://java.sun.com/developer/technicalArticles/javase/java6u10/index.html#kernel"). This means that when your application depends on the JVM you can direct the user to only have to download the specific components of the Java runtime that the application needs, minimizing the download size. Sounds quite cool, it will be interesting to see how and if it works for "real" applications.

[http://java.sun.com/developer/technicalArticles/javase/java6u10/index.html#kernel](http://java.sun.com/developer/technicalArticles/javase/java6u10/index.html#kernel)

Also heres some positive commentary on JavaFX.
[http://www.mindbug.org/2008/07/give-javafx-chance.html](http://www.mindbug.org/2008/07/give-javafx-chance.html)

---

### Post by cl333r on 2008-12-08
So far it looks horrible to me.
The JavaFX samples don't work on windows (with java 6 update 11) I get complains about certificates issues (looks like Sun can't make their own stuff handle well their own certificate technology).
Ironically they work on Ubuntu (at least a couple that I tried out) but they put a heavy load on the CPU, the buck bunny movie loads my 2 core cpu by almost 100%, this is horrible..

The "do you trust ...?" certificates I get is a clear indication that Sun didn't learn enough from the death of the applets. You either stop embarrassing developers and customers or you meet the dinosaurs once again. I'm really sorry, Adobe isn't even competing cause Sun it shooting itself in the foot..

---

### Post by druellan on 2008-12-08
Lots of devs are really upset about JavaFX. Samples don't show anything really useful from a UI standpoint and diggin on class tree shows nothing revolutionary. On Java, GWT (while not technically Java) looks as a better alternative, over that, Flex is one of the stars.

Check this opinion: [http://tinyurl.com/6j7h33](http://tinyurl.com/6j7h33)

---

### Post by stejas on 2008-12-16
I agree with the opinions posted on JavaFX. JavaFX is too slow to be even considered a competitor in the RIA space. 

I went to [http://java.sun.com/javafx/]("http://java.sun.com/javafx/") and tried to install the first app. After 5-7 mins and a lot of surfing, while JavaFX downloading and initializing the application, I thought I might see what it is. Alas, it was not to be. I couldn't see anything. Maybe I was doing something wrong. I tried again, and gave up. Finally after another 5-7 mins, the sample opened up by some magic and let me tell you, frustration and disappointment are small words. 

Next time I will be really carefully not to run a JavaFX application.

[Tejas]("http://www.neoquant.com/blog")

---

### Post by myrtle1908 on 2008-12-16
Nothing to do with Java FX but for RIAs you should definitely take a look at ExtJS and/or GXT.  Beautiful widgets and API, so easy to extend, awesome community, brilliant documentation.

No, I do not work for Ext.

[http://www.extjs.com](http://www.extjs.com)

---

### Post by jespdj on 2008-12-17
JavaFX is still really brand new (despite that Sun has been working on it for two years or so). I think people should not be so quick to dismiss it. It will take some time before there are really good tools available to work with JavaFX.

One advantage that JavaFX has over Adobe Flex and Microsoft Silverlight is that it, unlike the competition, run on desktops and laptops as well as on mobile devices.

---

### Post by tinny on 2008-12-17
> **jespdj said:**
> JavaFX is still really brand new (despite that Sun has been working on it for two years or so). I think people should not be so quick to dismiss it. It will take some time before there are really good tools available to work with JavaFX.

One advantage that JavaFX has over Adobe Flex and Microsoft Silverlight is that it, unlike the competition, run on desktops and laptops as well as on mobile devices.

So does Adobe's products.

[http://www.openscreenproject.org/](http://www.openscreenproject.org/)

---

