---
title: "[Java] Continuous Integration"
date: 2008-07-05
forum: Programming Talk
---

### Post by tinny on 2008-07-05
Hi

Im keen to learn of other peoples experiences in using continuous integration when working on a Java project.

Ive used [Hudson]("https://hudson.dev.java.net/") and found it to be great.

Id be interested to here about the relative build performances of these systems, reporting capabilities etc...

Also, can any of these continuous integration systems be installed from the standard Ubuntu repositories using APT?

---

### Post by jespdj on 2008-07-06
You can search Synaptic or [http://packages.ubuntu.com/](http://packages.ubuntu.com/) to see if the software you're looking for is in the Ubuntu repository.

I don't have much experience with continuous integration yet; at the moment we're looking at using [CruiseControl](http://cruisecontrol.sourceforge.net/).

---

### Post by halucard22 on 2008-07-06
> **jespdj said:**
> You can search Synaptic or [http://packages.ubuntu.com/](http://packages.ubuntu.com/) to see if the software you're looking for is in the Ubuntu repository.

I don't have much experience with continuous integration yet; at the moment we're looking at using [CruiseControl](http://cruisecontrol.sourceforge.net/).

You have also continuum, gump and the proprietary Bamboo from Atlassian. I don't have any experience in the continuous integration. So let's hope that it helps you in your choice.

---

### Post by Quikee on 2008-07-06
As I said in "original" thread - we are using [Continuum]("http://continuum.apache.org/") at work. the current version has some bugs (if you rename a class a error will occur and it won't do the build once) but beside of that it works OK.

> 
Id be interested to here about the relative build performances of these systems, reporting capabilities etc...

Well I don't know what kind of reporting you have in mind but the only reporting is the start/end time, duration, number of build, number of test passed/failed/error, ... .

---

### Post by tinny on 2008-07-06
> 
Well I don't know what kind of reporting you have in mind but the only reporting is the start/end time, duration, number of build, number of test passed/failed/error, ... .


Off the top of my head I believe Hudson has the above basic reports as well as PMD and open tasks (//TODO comments etc), it might have more not sure...?

> 
As I said in "original" thread - we are using Continuum at work. the current version has some bugs (if you rename a class a error will occur and it won't do the build once) but beside of that it works OK.


How do you fix this? Or does it just break your project?

---

### Post by Quikee on 2008-07-06
> **tinny said:**
> Off the top of my head I believe Hudson has the above basic reports as well as PMD and open tasks (//TODO comments etc), it might have more not sure...?

Well - this is not task of continuous integration tool, but maven plugins for "site-build" goal that generates a site with documentation, java-docs, code in html (so you can link to a specific code section in the documentation) and all the reports you mention (PDM, Checkstyle,...) - depends what plugins you enable.

> **tinny said:**
> How do you fix this? Or does it just break your project?

The problem is that it doesn't run only once it is scheduled - the next time it is scheduled it will run fine. It is a minor bug that is fixed in svn but not in the stable release yet. You usually don't even notice it in the quickly scheduled builds (we have it set to 10 min to look for changes and if it finds some it will run the usual build), but you notice it on the "nightly" builds (which we have for site-deploying and running tests on other databases).

---

### Post by tinny on 2008-07-06
> 
Well - this is not task of continuous integration tool, but maven plugins for "site-build" goal that generates a site with documentation, java-docs, code in html (so you can link to a specific code section in the documentation) and all the reports you mention (PDM, Checkstyle,...) - depends what plugins you enable.

Yes this is just basic Maven stuff.

I thought we were talking about continuous integration??? :)

(I guess im talking about stat's not reports)
See the attached jpg. My Hudson setup has "My Test Result Trend", "Open Tasks Trend", "checkstyle", "cpd" and "pmd" stat's.

Does Continuum have any basic stat's like this?

> 
The problem is that it doesn't run only once it is scheduled - the next time it is scheduled it will run fine. It is a minor bug that is fixed in svn but not in the stable release yet. You usually don't even notice it in the quickly scheduled builds (we have it set to 10 min to look for changes and if it finds some it will run the usual build), but you notice it on the "nightly" builds (which we have for site-deploying and running tests on other databases).


So its still usable, that's good to know thanks.

---

### Post by tinny on 2008-07-06
If you are interested you can see Hudson in action [here]("http://hudson.jboss.org/hudson/").

---

### Post by Quikee on 2008-07-06
> **tinny said:**
> Yes this is just basic Maven stuff.

I thought we were talking about continuous integration??? :)


Hehe.. yes this is all continuous integration however I think of Continuum only as a scheduler and build manager ("the one who triggers Maven automatically instead of me"). The other stuff are only plugins in Maven to do additional jobs for a particular goal. 

I have read a little more about Hudson and now I know that Hudson actually reads the data from the maven run of plugin. For example - when Maven runs checkstyle, Hudson can display the results checkstlye plugin has gathered which I think is really cool. ;)

> **tinny said:**
> 
(I guess im talking about stat's not reports)
See the attached jpg. My Hudson setup has "My Test Result Trend", "Open Tasks Trend", "checkstyle", "cpd" and "pmd" stat's.

Does Continuum have any basic stat's like this?


No. Not in such a way.

---

### Post by Quikee on 2008-07-06
> **tinny said:**
> If you are interested you can see Hudson in action [here]("http://hudson.jboss.org/hudson/").

Nice.. thanks

---

### Post by tinny on 2008-07-06
> **Quikee said:**
> Nice.. thanks

Hudson is really nice, give it a crack!

Also here is a nice [Hudson monitor]("https://sourceforge.net/project/platformdownload.php?group_id=229717&sel_platform=8772") for the desktop.

---

### Post by Quikee on 2008-07-06
> **tinny said:**
> Hudson is really nice, give it a crack!

Also here is a nice [Hudson monitor]("https://sourceforge.net/project/platformdownload.php?group_id=229717&sel_platform=8772") for the desktop.

Yes I will.. thanks. At least it has one advantage over Continuum judging from the link you provided - it is a faster. It also uses Tango icons that I like very much - but this is just a bonus. ;)

Do you have any experience with CruiseControl?

---

### Post by tinny on 2008-07-06
> **Quikee said:**
> Yes I will.. thanks. At least it has one advantage over Continuum judging from the link you provided - it is a faster. It also uses Tango icons that I like very much - but this is just a bonus. ;)

Do you have any experience with CruiseControl?

No I dont sorry. Or though here is a [live demo of CruiseControl]("http://cruisecontrolrb.thoughtworks.com/projects") for Ruby. The guys that I have talked to in my office prefer Hudson.

---

### Post by TonyGould on 2008-07-08
Bamboo is v good. I was skeptical at first, but it ticks all the boxes for a multi-platform multi-language multi-machine set up, and integrates v well w/ jira confluence as you'd expect. For plain old java continuum might be a good choice however, as it is by the same guys who did maven, plus it's fully open source, actively developed, and apache have other projects, like their repository of binaries (sorry forget the name).

This series of articles at IBM is v good background.
[http://www.ibm.com/developerworks/java/library/j-ap11297](http://www.ibm.com/developerworks/java/library/j-ap11297)

---

### Post by skeeterbug on 2008-07-08
I setup CruiseControl.NET (.NET port of CruiseControl) here at work. The time spent setting this up properly pays off extremely well.

When our external contributors commit code, it builds, archives that build, and outputs to an IIS virtual directory. The development of our new product can be seen and tested as soon as the build finishes. It also emails everyone when the build fails (sometimes files aren't committed, etc). Before this was all done manually by myself.

I am positive the Java version of CruiseControl has the same features, so it gets my vote.

---

### Post by tinny on 2008-07-08
> **skeeterbug said:**
> I setup CruiseControl.NET (.NET port of CruiseControl) here at work. The time spent setting this up properly pays off extremely well.

When our external contributors commit code, it builds, archives that build, and outputs to an IIS virtual directory. The development of our new product can be seen and tested as soon as the build finishes. It also emails everyone when the build fails (sometimes files aren't committed, etc). Before this was all done manually by myself.

I am positive the Java version of CruiseControl has the same features, so it gets my vote.

Yep, what you explain above is the definition of continuous integration. Hudson definitely does this and im pretty sure Continuum does too???

> 
Bamboo is v good. I was skeptical at first, but it ticks all the boxes for a multi-platform multi-language multi-machine set up, and integrates v well w/ jira confluence as you'd expect.


Sounds cool. I notice its a commercial product, right? :(

---

