---
title: "Updated Lucid this morning, now Java is broken."
date: 2012-09-05
forum: New to Ubuntu
---

### Post by ctdahle on 2012-09-05
I'm the only person using Ubuntu at my school and have been bragging about how great it is. I have colleagues and administrators who are watching this with increasing interest, but if I can't take attendance or record grades, the experiment ends really fast! Everything was working before Update manager ran this morning. We use a web based attendance and gradebook system (Pearson PowerTeacher and PowerSchool)

Trying to run my grade book program I get-

/tmp/launchGradeBook.jnlp could not be opened, because an unknown error occurred.
Try saving to disk first and then opening the file.


When I attempt to open the file from my download menu, the system just stalls.

Going to the website where the gradebook program lives and following their troubleshooting procedure, I get a "Java Not Detected" error.

At the Java website, I get an animated spinning wheel and a "please wait" that persists interminably.

Thinking that something was missed in the update, I re-ran update manager, I get

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 83FBA1751378B444

Help!

---

### Post by ctdahle on 2012-09-05
Also, Software Center does indicate that all the Java tools are installed.

---

### Post by QIII on 2012-09-05
Could you please post the results of
```
java -version
```

---

### Post by ctdahle on 2012-09-05
Certainly:

java version "1.6.0_24"
OpenJDK Runtime Environment (IcedTea6 1.11.4)  (6b24-1.11.4-1ubuntu0.10.04.1)
OpenJDK Client VM (build 20.0-b12, mixed mode, sharing)

---

### Post by QIII on 2012-09-05
I see a couple of potential issues here.
 
1. You are using OpenJDK. Although I prefer OpenJDK because it is open source, some web developers don't recognize it as Java. It may be that the site you are using has been updated to use Oracle Java 7.
 
2. You are using OpenJDK 6, which is about to reach end of life in November. It could be that the web developers at that site are transitioning away from OpenJDK 6 as valid. Both OpenJDK 6 and Oracle Java 6 are vulnerable to an array of security problems and should not be used.
 
3. Although OpenJDK 7 is the open source reference implementation for Oracle Java 7, some developers, as I said, do not recognize the relationship and some applications and applets will not run with it.
 
4. There have been two recent vulnerabilities in Java that have caused Oracle to put out Update 7. There have even been a couple of build updates. It could be that the web developers have changed the site so that it will not work with any earlier update.
 
In the wiki in my signature, in the Oracle Java 7 section, under "Command line methods", there is a link "Using webupd8.org's strikingly simple method". Oracle will no longer allow anyone to have Java 7 in repositories. The webupd8 method uses what is known as a PPA to contain an installer that goes to Oracle's website to download and then install Oracle Java 7 on Ubuntu. This is a great process, because the PPA is updated as Oracle puts out updates to Oracle Java 7 and those updates are automatically applied to your machine when you do your normal Ubuntu updates. You don't have to go back to Oracle every time there is an update and reinstall.
 
Alternatively, OpenJDK 7 should be in the Lucid repo. If you would rather use OpenJDK, uninstall OpenJDK 6 and install OpenJDK 7. But, as I said, OpenJDK is not universally recognized as Java, despite the relationship.
 
Let me know how it works out.

---

### Post by ctdahle on 2012-09-06
First QIII, thank you for your efforts to help. I really mean that. But I  am quite nervous about enabling the Oracle PPA until I feel more  informed. (I do understand what a PPA is and does) If you can allay my fears, I'd be grateful.

Your comments on the changes toward Java7 make complete sense, yet I am skeptical that the publisher of our grade book software would push out  an update that _requires_ an upgrade to Java at this point in the school  year. In June, yes, but not in September...School computers are updated  in June and July and an educational software publisher who breaks the software that maintains student records in September will ABSOLUTELY lose many, if not most of their customers.  Besides, Pearson DID roll out a major revision last spring. Requiring a  coincident Java update would have happened then, not as part of a  maintenance release  3 weeks into a new school year.

Enough about my worries...here's what I have done to further evaluate the problem from home, without access to the school computer.

When I  finally obtained permission to use Linux instead of Windows7, I set up a  matching machine, at home also running Lucid, and I keep the school and  home machines in sync using Ubuntu One. If I make changes, I make them  on the home machine first, resolve any issues, then apply them to the  school machine. The gradebook website runs fine on my home machine. I just checked.

I updated the home machine on September 1...what I usually do is run  update manager on the home machine first, make sure everything is still  working, correct any issues, then run it on the school machine the  following week.

Snooping around, I am convinced that what killed  Java on my school computer was something added to the update channel  between Saturday September 1 and Wednesday September 5.

I checked java -version on the home machine. Here are the results:
> java version "1.6.0_24"
OpenJDK Runtime Environment (IcedTea6 1.11.3)  (6b24-1.11.3-1ubuntu0.10.04.1)
OpenJDK Client VM (build 20.0-b12, mixed mode, sharing)For reference, here is the java -version check result from the "broken" school machine:
> java version "1.6.0_24"
OpenJDK Runtime Environment (IcedTea6 1.11.4)  (6b24-1.11.4-1ubuntu0.10.04.1)
OpenJDK Client VM (build 20.0-b12, mixed mode, sharing)As you can see, the "working" machine has a slightly OLDER ".3" version of OpenJDK.

Under these circumstances, I remain reluctant to enable the PPA. On my personal machine, I don't mind being out on the bleeding edge, but I have to treat the school machine very conservatively.

...and the error message I got from update manager is still really bugging me

> W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net)  lucid Release: The following signatures couldn't be verified because  the public key is not available: NO_PUBKEY 83FBA1751378B444

---

### Post by Zill on 2012-09-06
ctdahle:  I can't really help you with the java problem other than to say that I too am running a fully updated Lucid (10.04) with the following java version and I have had no problems with this version (so far!):
```
java version "1.6.0_24"
OpenJDK Runtime Environment (IcedTea6 1.11.4) (6b24-1.11.4-1ubuntu0.10.04.1)
OpenJDK Server VM (build 20.0-b12, mixed mode)
```

Regarding your GPG error, this key (83FBA1751378B444) seems to indicate that you have installed LibreOffice from a PPA.  As the default office suite in Lucid is actually OpenOffice, rather than LibreOffice, I suggest you could revert to this and disable the LibreOffice PPA.

However, if you wish to continue with using LibreOffice then I suggest you ensure the PPA key is updated.  [This link]("http://ubuntuforums.org/showthread.php?t=1736999") may help.

If you still have problems with this then I suggest you post the output of the following two commands:
```
sudo apt-get update
```
and
```
cat /etc/apt/sources.list
```

---

### Post by QIII on 2012-09-06
The software itself may not have changed* at all*.

What may have changed (since this is a web start application -- JNLP) is the xml that determines what version of Java is required to run it.

If, in response to the EOL of OpenJDK 6 and the recent serious security flaws found in Java 7, the website has changed that xml to look for a more updated runtime environment, the application may not launch.

Which sites have you been using to test if your Java environment is working properly?

What is conservative?  Leaving your computer in a cage with a pack of wolves because you don't want to change, or putting it into a cage with a newer lock?

Java 6 and Java 7 prior to Update 7 are lock boxes to which the highwaymen already have keys -- and those lock boxes contain the keys to the kingdom.  The exploitable vulnerabilities allow malicious code to escape the Java sandbox and run in the user context on your computer, delivering payloads that can do the bidding of any nefarious agent who wants in.  This is not a matter of "bleeding edge".  This is a matter of having good locks.

Since you have the computer at home to test with before doing anything with the computer at school, test.

If you can post the link to the website, we can have a look at the source.  (I'm pretty busy today, so I may not get to it.  But someone else may.)  That way we can see if it is looking for a more up-to-date version of Java -- or even unwisely requiring a vulnerable one.

---

### Post by ctdahle on 2012-09-06
Thank you Zill and QIII. You have lead me to a much better understanding of the problem and I have done some additional probing as well. 

I am going to set up the PPA.

I found out that the Pearson software site returns a "Java not detected" message on every computer I am able to use, regardless of whether the gradebook program actually runs.

The Pearson site is the only site I have found so far where Java based programs are not working for me.

Unfortunately I cannot give you a URL for the site because it is password protected.

I will not be able to look at this again until Saturday, but based on what you have told me, I believe I will be able to resolve the problem and I will report back.

---

### Post by ctdahle on 2012-09-06
OK, I had a bit of time and I set up the PPA. This has cleared up the issue with the grading program.

On to the Libre Office/Open Office issue.

I did remove Open Office and install Libre Office about a month ago based on a belief that Open Office was going to be orphaned, so I will tear into that PPA  issue as suggested by Zill. Probably not until tomorrow though.

Thank you both for your patience and counsel.

---

### Post by patpatu on 2012-09-11
Hi,

This had me running round in circles for a hour (mainly undoing 18mnts of java experimentation). Darn those updates!

I solved it but, as yet too busy to repeat the soln properly to confirm a proper resolution:

In firefox 

[FONT="Courier New"]**[Prefs]-->Applications-->JNLP-->**[/FONT]

then choose "other" and browse to and select
/usr/lib/jvm/java-6-openjdk/jre/bin/javaws

I THINK this gets me going again with openjdk and pulseaudio integration etc. Now I hope this workaround does the trick for you but, may be not as I have been a little lapse with controlling java on this production box.

Alternatively, it may have been this which got me going:
[FONT="Courier New"]**sudo ln -s /usr/lib/jvm/java-6-openjdk/jre/bin/javaws /usr/bin/**[/FONT]


[I][SIZE="2"]java version "1.6.0_24"
OpenJDK Runtime Environment (IcedTea6 1.11.4) (6b24-1.11.4-1ubuntu0.10.04.1)
OpenJDK 64-Bit Server VM (build 20.0-b12, mixed mode)[/SIZE][/I]

---

