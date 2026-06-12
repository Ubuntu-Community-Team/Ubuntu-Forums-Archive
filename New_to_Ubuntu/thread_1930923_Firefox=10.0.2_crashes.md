---
title: "Firefox=10.0.2 crashes"
date: 2012-02-24
forum: New to Ubuntu
---

### Post by phil66 on 2012-02-24
Ubuntu-10.04 lts
Firefox-10.0.2
shockwave flash-11.1 r102 updated 2/13/2012

Firefox crashes when trying to open yahoo games

This started when I upgraded to Firefox-10.0.2 canonical-1.0 from update manager.

This happens in regular mode or safe mode with add-ons disabled

Any fix for the problem ???

---

### Post by JC24 on 2012-02-24
i am having the same exact problem. 
my wife uses the computer ONLY to play yahoo games and check her email. We dont install anything on it other than the updates provided through the ubuntu update manager. 
i believe her firefox version says 10.0, not 10.0.2.
It crashes every single time she tries to log into yahoo games. I have posted this question also over at the mozilla help forum to no avail.
 
(edit*: forgot to mention, yahoo games previously worked perfectly for her. i believe once FF was upgraded to 10.0 that is when the issues started.)

---

### Post by phil66 on 2012-02-24
JC

Would you please give me the url for your mozilla post 

I would like to bump it and see if we can get any answers

Thanks for the reply

P.S  Firefox 10.0.2 works in other distro's that is the reason I posted Here.

---

### Post by phil66 on 2012-02-25
Has anyone else experienced this problem after updating firefox

---

### Post by rburkartjo on 2012-02-25
phil do you have adblock plus installed. if so you might try disabling on that website only. i had to do that to get the games to play. i am using aurora(firefox) 12.0. did that and everything was fine. good luck

---

### Post by weezyrider on 2012-02-25
Adobe has announced it will partner with Google and not develop flash as we get it now anymore. It will be integrated into Chrome only.

Mozilla is trying to substitute HTML5, and since FF versions and updates are being released so fast, getting a weird error wouldn't surprise me.

---

### Post by rbowen1 on 2012-02-25
I was able to run the Yahoo game Yoda Farmer with no problem using FF 10.0.2 running on Ubuntu  11.04.  Not sure which version of shockwave I am running.   Did you upgrade shockwave via an update manager update or do a manual update?

---

### Post by rbowen1 on 2012-02-25
I did a little more research since this problem intrigued me.   I was able to log into Yahoo games and play the wheel of fortune with no issues.   I am running 11.04 Ubuntu with Fire Fox 10.0.2 (latest) and flash version 11.1.102.62 (latest).     You can check this yourself with this link:   [http://kb2.adobe.com/cps/155/tn_15507.html](http://kb2.adobe.com/cps/155/tn_15507.html)

You mentioned that you were running  "shockwave flash-11.1 r102 updated 2/13/2012"   Shockwave flash is only for windows.   Please see this link:  [https://help.ubuntu.com/community/Shockwave](https://help.ubuntu.com/community/Shockwave)

Are you running Wine to simulate a windows environment?

---

### Post by phil66 on 2012-02-25
Thanks for all the replies
I had removed all extensions and plugins left only default appearance and language
The results were the same. Firefox still crashing.
Went to Firefox irc channel and they looked at the crash reports and determined it was caused by a bug in icetea plugin
Currently no fix but the bug report is still active
Disabled icetea plugin and it advanced until java is needed.Firefox did not crash.
So now have to wait for ice tea to fix there plugin. Which is what Firefox suggested.

---

### Post by Bobhuber on 2012-02-25
> **phil66 said:**
> Thanks for all the replies
I had removed all extensions and plugins left only default appearance and language
The results were the same. Firefox still crashing.
Went to Firefox irc channel and they looked at the crash reports and determined it was caused by a bug in icetea plugin
Currently no fix but the bug report is still active
Disabled icetea plugin and it advanced until java is needed.Firefox did not crash.
So now have to wait for ice tea to fix there plugin. Which is what Firefox suggested.
Install Java manually using the instructions found here.
[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

---

### Post by d4m1r on 2012-02-25
Post a direct link to the Yahoo games page that makes it crash?

Maybe we can confirm if it crashes for us as well. Also, google "flash aid firefox plugin" and install it, it might help.

---

### Post by phil66 on 2012-02-26
P.s > **d4m1r said:**
> Post a direct link to the Yahoo games page that makes it crash?

Maybe we can confirm if it crashes for us as well. Also, google "flash aid firefox plugin" and install it, it might help.

This is the sequence of address's up to the crash:
yahoo.com
games.yahoo.com
games.yahoo.com/po
games.yahoo.com/games/login2?page=po&ss=1

When the last address enters Firefox goes to desktop and crash report

The java program installed manually but icetea plugin also has to be installed for java to work. Firefox 9.01 does not crash.

Firefox-10.02 in lupu-5.28 -lucid does not crash.

---

### Post by Krytarik on 2012-02-26
> **phil66 said:**
> This is the sequence of address's up to the crash:
yahoo.com
games.yahoo.com
games.yahoo.com/po
games.yahoo.com/games/login2?page=po&ss=1

When the last address enters Firefox goes to desktop and crash report

The java program installed manually but icetea plugin also has to be installed for java to work.
I can confirm this on my system, eventually, with exact the same versions of everything you have. So this is an issue with Java, not with Flash; you could try using the proprietary Oracle JDK instead of OpenJDK:

[http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html](http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html)

Regards.

---

### Post by JC24 on 2012-02-27
not sure if it still helps or not, but here is the link to my mozilla post:
 
[https://support.mozilla.org/en-US/questions/920507](https://support.mozilla.org/en-US/questions/920507)
 
Is there any way to "roll back" my firefox to version 9? sorry, i am a complete Ubuntu noob. we pretty much only use that computer for yahoo games / email / GIMP
 
edit* also, over the weekend via the update manager my FF updated from 10.0 to 10.0.2, and i still have the same exact issue as OP.
 
Would Chromium web browser work with Yahoo games (or any other web browser from the software center?)

---

### Post by maan81 on 2012-02-28
I am too having the same problem, at random times when I use javascript [jQuery] scripts. Chromium on the other hand runs flawlessly. It really seems FF 10 isn't ready enough.

---

### Post by pootan on 2012-02-28
I think anyone with problems here should look at installing the Sun Java oracle packages and plugin. 

AS far as I know the webup8te repositories install an alpha Sun Java 7 version. 

The page linked below will help install the latest stable Sun Java packages and solved my problems with playing online games that required Sun Java. 

For your own piece of mind you should do some googling when adding 3rd party repositories to satisfy yourself that it is indeed trustworthy. From my own investigation I found duinsoft to be run by a respected Ubuntu community member so I went ahead with the risk. 

[http://www.duinsoft.nl/packages.php?t=en](http://www.duinsoft.nl/packages.php?t=en)

---

### Post by Krytarik on 2012-02-28
> **pootan said:**
> AS far as I know the webup8te repositories install an alpha Sun Java 7 version.

The page linked below will help install the latest stable Sun Java packages
Actually, the WebUpd8 Java Installer PPA provides installing the very same version offered as "Latest Release" on Oracle's website, version 7u3:

[LIST]
[*]WebUpd8 Java Installer PPA: [https://launchpad.net/~webupd8team/+archive/java/+packages]("https://launchpad.net/%7Ewebupd8team/+archive/java/+packages")
[/LIST]

[LIST]
[*]Oracle: [http://www.oracle.com/technetwork/java/javase/downloads/index.html](http://www.oracle.com/technetwork/java/javase/downloads/index.html)
[/LIST]

---

### Post by pootan on 2012-02-28
> **Krytarik said:**
> Actually, the WebUpd8 Java Installer PPA provides installing the very same version offered as "Latest Release" on Oracle's website, version 7u3:

[LIST]
[*]WebUpd8 Java Installer PPA: [https://launchpad.net/~webupd8team/+archive/java/+packages]("https://launchpad.net/%7Ewebupd8team/+archive/java/+packages")
[/LIST]

[LIST]
[*]Oracle: [http://www.oracle.com/technetwork/java/javase/downloads/index.html](http://www.oracle.com/technetwork/java/javase/downloads/index.html)
[/LIST]

Yes it is the latest version but 7 is still not a public release. 

[https://www.java.com/en/download/faq/java7.xml](https://www.java.com/en/download/faq/java7.xml)

I'm sure it would work well in most cases but if you rely on Java to play those games then the current recommended version is better.

---

### Post by Krytarik on 2012-02-28
> **pootan said:**
> Yes it is the latest version but 7 is still not a public release. 

[https://www.java.com/en/download/faq/java7.xml](https://www.java.com/en/download/faq/java7.xml)

I'm sure it would work well in most cases but if you rely on Java to play those games then the current recommended version is better.
So, where is the "recommend version" offered for download then, public-wise!? For that matter, the "Downloads" link on the site you are linking to isn't working here, as of now. :P

---

### Post by pootan on 2012-02-28
The recommended page is here:

[https://www.java.com/en/download/linux_manual.jsp?locale=en](https://www.java.com/en/download/linux_manual.jsp?locale=en)

or simply got  to java.com and hit the download button there

That will give you jre-6u31-linux

Anyway, at least now the OP and others have some good choices and know some background for each.

---

### Post by Krytarik on 2012-02-28
> **pootan said:**
> ... or simply got  to java.com and hit the download button there
Yeah, that way, it works. :P

> **pootan said:**
> Anyway, at least now the OP and others have some good choices and know some background for each.
Yeah, right. :D

---

### Post by JC24 on 2012-03-01
so to update my java all i have to do is go to Java's website and click the download now button?
 
sorry, as i mentioned before i am a complete Ubuntu noob. I know in the past we have had issues getting java on ubuntu working properly and often times i had to read these forums and copy and paste lots of commands into the terminal to install java.
 
just clicking "download now" on java's website to update my java just seems .... too easy? :)
 
edit* through more searching i found a lot of people recommending this link:
[https://sites.google.com/site/easylinuxtipsproject/java](https://sites.google.com/site/easylinuxtipsproject/java)
Is this the same thing? can i jsut follow the steps outlined there? i am fairly certain my computer at home right now is using the icedtea plugin

---

### Post by pootan on 2012-03-01
If you want your games to work and want a noob friendly way then look at step 2.1 of the page you linked. The duinsoft repository will install the latest recommended version of sun java and also the firefox plugin and update them when a newer version is available. 


[http://www.duinsoft.nl/packages.php?t=en](http://www.duinsoft.nl/packages.php?t=en)

The few simple steps can be found there under the heading **Repository**.

Don't forget to restart your browser when done and happy gaming.

---

### Post by JC24 on 2012-03-01
> **pootan said:**
> If you want your games to work and want a noob friendly way then look at step 2.1 of the page you linked. The duinsoft repository will install the latest recommended version of sun java and also the firefox plugin and update them when a newer version is available. 
 
 
[http://www.duinsoft.nl/packages.php?t=en](http://www.duinsoft.nl/packages.php?t=en)
 
The few simple steps can be found there under the heading **Repository**.
 
Don't forget to restart your browser when done and happy gaming.
 
thanks.
Will the detailed steps in section 5 get me the same results? I like how the author listed it step-by-step, and i am more than willing to try and use (and learn more) about terminal commands. So i'd actually prefer to do it as listed in section 5, so long as you think that would work as well.

---

### Post by pootan on 2012-03-01
Yes, that will get you the latest version as well. :)

---

### Post by Gremlinzzz on 2012-03-01
> **pootan said:**
> The recommended page is here:

[https://www.java.com/en/download/linux_manual.jsp?locale=en](https://www.java.com/en/download/linux_manual.jsp?locale=en)

or simply got  to java.com and hit the download button there

That will give you jre-6u31-linux

Anyway, at least now the OP and others have some good choices and know some background for each.

and the easy way to install:popcorn:
[https://sites.google.com/site/easylinuxtipsproject/java](https://sites.google.com/site/easylinuxtipsproject/java)

---

### Post by JC24 on 2012-03-02
just wanted to say that the java write up in that link worked for me! (i did everything it said step by step. i had to remove the icedtea java plugin first like it said). 
now, with firefox 10.0.2 and updated java i can access yahoo games and play games such as spades or literati without ff crashing.
thank you to everyone who posted in this thread and also to the person who created that tutorial website.
OP, dont know if you still have the problem or not but if you do just try the steps outlined here:
 
[https://sites.google.com/site/easylinuxtipsproject/java](https://sites.google.com/site/easylinuxtipsproject/java)

---

