---
title: "How Do I Get Java Working Online for Raring Ringtail?"
date: 2013-10-15
forum: New to Ubuntu
---

### Post by Frank_T._Morgan on 2013-10-15
Hi!

I've tried searching for another thread that addresses exactly what I'm trying to solve, and I don't think this has already been posted.  I'm not sure if it has, but I'll let the rest of you judge.  I'm still hopeful, however, that I can find some assistance.

I have an Intel Inspiron 2200 on which I installed Lubuntu/LXDE after I lost patience trying to nurse Windows into working outside of Safe Mode.  (After awhile, even starting up in Safe Mode took too long, as I waited for one line or another to stop hanging and to finish scrolling past.  That was it.)  My Inspiron has a Pentium M processor running at 1.60GHz, and it also appears to have 499MB of RAM.  After updates, my system presently has Lubuntu v13.04.  ("Raring Ringtail".  Yay! \\:D/ )

I have Chromium and Firefox installed (not Chrome.  Google's part in Chrome doesn't interest me after they changed their privacy policy).  I've tried to get Java working on both, though I've had a preference for Firefox for the keyboard shortcuts.  Chromium seems to test out fine on [http://www.java.com/en/download/testjava.jsp](http://www.java.com/en/download/testjava.jsp) , but it doesn't work consistently on other sites.  Firefox, however, just doesn't work.  The result I've been getting at Java.com is a picture of a sad-face block and the message, "The IcedTea-Web (using IcedTea-Web 1.3.2 (1.3.2-1ubuntu)) plugin has crashed. _Reload the page_ to try again."  Another message appears under that, stating "No report available."

Synaptic shows that I have gcj-4.7-jre, jcg-4.7-headless, and jcg-4.7-jre-lib installed, and all are v4.7.31unbuntu1.  (I'm not sure why these are there, but now that I'm looking for help in the forum, I'm don't want to try to figure it out.)  I also have jcg-jre and jcg-jre-headless, and both are v4:4.7.3-1ubuntu10.  Further down the list, I have icedtea-6-plugin, icedtea-7-plugin, icedtea-netx and icedtea-netx-common.  All of these are v1.3.2-1ubuntu1.1.  Below that, I have java-common, v0.43ubuntu4.

Below that, there's still more 8-[ (but I'll list it anyways).  I have libatk-wrapper-java and libatk-wrapper-java-jni, both v0.30.4-0ubuntu4.  I have libgcj-common, v1:4.7.3-1ubuntu10, and libgcj13, v4.7.3-1ubuntu1.  I have libjs-jquery, v1.7.2+debian-1ubuntu1.  I also have libwebkitgtk-1.0-0, libwebkitgtk-1.0-common, libwebkitgtk-3.0-0, libwebkitgtk-3.0-common.  All of these are v1.10.2-0ubuntu1.

As if that wasn't enough fun, here's the interesting part:  I made sure I had eight OpenJDK packages installed, thinking they would alleviate my Java concerns. :-({|=  As you may have guessed, *they did not.*  I have openjdk-6-jdk, openjdk-6-jre, openjdk-6-jre-headless, and openjdk-6-jre-lib.  All of these are v6b27-1.12.6-1ubuntu0.13.04.2.  I also have openjdk-7-jdk, openjdk-7-jre, openjdk-7-jre-headless and openjdk-7-jre-lib.  All of these are v7u25-2.3.10-1ubuntu0.13.04.2.

These aren't all the packages I have installed on my system that might pertain to Java, of course; they were just what I could find that casually *seemed* to be pertinent.  I have two questions, however:  1. How do I figure out why Java isn't working on my system?  2.  How do I get Java working?  Please let me know if there's any additional data that will be needed in order to solve the problem.  I would be grateful for any help that can be provided, besides which, I need to get some work done.  ](*,) :biggrin:
[HR][/HR]Update:  Upon further consideration, I've uninstalled all my OpenJDK packages in favor of installing Eclipse Juno 4.2, as shown at [http://thismagpie.blogspot.com/2012/07/installing-eclipse-juno-42-on-lubuntu.html](http://thismagpie.blogspot.com/2012/07/installing-eclipse-juno-42-on-lubuntu.html) .  Someone pointed this out to me in IRC, so I figured, why not.  (I've also downloaded jdk-7u45-linux-i586.tar.gz from [http://www.oracle.com/technetwork/java/javase/downloads/jdk7-downloads-1880260.html](http://www.oracle.com/technetwork/java/javase/downloads/jdk7-downloads-1880260.html), but I'm going to postpone trying to figure it for now.)  If anybody has any responses to this, either about it being a good plan or a bad plan, 8-[ I would still be happy to accept suggestions.  Any other advice is also welcome.  :-\" :biggrin:

---

### Post by QIII on 2013-10-16
Hello!

If you should choose to install Oracle Java 7, do yourself a huge favor and look [here]("http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html") for the easiest possible way to do it.

---

### Post by Frank_T._Morgan on 2013-10-21
Thank you very much.  I have some aptitude, but the easier it is to do this, the better.  :biggrin:\\:D/

[HR][/HR]
Update:  I ran through the steps they gave, and it's very straightforward!  Thanks.

[HR][/HR]
Update:  Recently I updated my system to Ubuntu 13.10 (Saucy Salamander), and this seems to change the context entirely.  However, I'm still proceeding with the same advice to see how well this works out.  I'm also cautiously optimistic that this will still solve everything I need that is pertinent to Java.  (We'll see.)

[HR][/HR]
Update:  *This appears to be [COLOR=#009900]_completely_** _solved,_**[/COLOR] according to the instructions you've provided for me:* At the [Java.com "Verify Java Version" page]("http://www.java.com/en/download/testjava.jsp"), I've received a message stating (with a green checkmark to the left), "Congratulations!  You have the recommended Java installed (Version 7 Update 45)."

*Thanks!!*  =D>\\:D/

---

