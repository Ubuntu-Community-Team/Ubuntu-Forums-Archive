---
title: "Sun Java in Firefox on Hardy Heron for Webtycho text editor"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by jd1ckson on 2008-05-28
Hello,

Let me start by saying I have learned more about Linux in the 12+ hours I've spent muddling with this problem than I thought was possible.  I'm sure in the future this will be a very positive thing, but at the moment, I'm just extremely frustrated/irritated.

I use webtycho's classroom platform.  I have solved the "javascript" error it gives with Ubuntu's mozilla as described in other forums...completely different issue, many hours to solve, but done! The remaining problem is with Java: I have GCJ with Iced Tea installed for my Java, running Hardy Heron, which works smoothly in Firefox for "Applet" tests but does not load for "object" tests.

Webtycho has a java-enabled text editor that I cannot use with Iced Tea, nor did it work with straight GCJ or blackdown on 7.10.  I have installed, uninstalled, and reinstalled 3 java clients over and over with no result. 

My problem is: I go through synaptics package manager.  I install Sun Java, no problem.  I install the plugin, no problem.  But I can't get Mozilla's about:plugins to recongize that the plugin is installed, and the java applet doesn't load when I use mozilla pages.  Everything else works ok, mostly, with Iced Tea, but I really want my classroom to function properly! :confused:

I have tried using the guide on Ubuntu's documentation site, I have tried using Sun Java's guide on their site, and I am about ready to toss my laptop through a window!  I have done this through the terminal and found it even more frustrating...doesn't matter how I install it, I can't link the plugin so that firefox can interact with Sun Java.  Right now I'm back to Iced Tea and fuming in the corner.

Any help would be incredibly, wholeheartedly, appreciated.  I never thought that kicking Windows in the gut would be so hard...but I am determined to stick it out!

Thanks,
~Jen

---

### Post by SunnyRabbiera on 2008-05-28
well did you try to enable the restricted extras repositories?
try sun java 5? 6?

---

### Post by doorknob60 on 2008-05-28
```
sudo update-java-alternatives -s java-6-sun
```
If that gives an error, post the output of this:
```
sudo update-java-alternatives -l
```

EDIT: First, try this just incase you missed something:
```
sudo apt-get install sun-java6-plugin
```

---

### Post by jd1ckson on 2008-05-29
Hi Sunny,

I am enabled out the wazoo :-) All of the happy checkboxes in Synaptic's package manager are checkmarked.

My problem isn't installing Sun Java- it installs fine.  My problem is that when I use firefox, firefox doesn't see that java is installed.  I get the "you need additional plugins to view this page" error.  If I check Sun Java, then 1 of 2 things will happen- either it will say it can't find Sun Java, or it will tell me the plugin is already installed- yet in about:plugins, and on websites using java, I get no joy!

:-(

---

### Post by jd1ckson on 2008-05-29
Hi DoorKnob,

I don't get anything that actually says "error" when I run that in terminal, but when I look at my plugin list in the firefox browser, it still shows GCJ w/ Iced Tea 1.0, and no sign of java's plugin anywhere...I have the idea that the java plugin installs itself somewhere that firefox can't find it, but I don't know how to fix that, or am I completely off-track?  Issue was the same in Firefox 2 as it is now in Firefox 3...that was part of the reason I upgraded to Hardy, some misguided hope that it would magically fix my problem.  Do like Hardy better, though, overall.

I get the following when I enter sudo update-java-alternatives -1

usage: update-java-alternatives [--jre-headless] [--jre] [--plugin] [ -t|--test|-v|--verbose]
           -l|--list [<jname>]
           -s|--set <jname>
           -a|--auto
           -h|-?|--help



Thanks for any help you can give!

---

### Post by jd1ckson on 2008-05-29
I solved my problem using this: [http://ubuntuforums.org/showthread.php?p=5071005#post5071005](http://ubuntuforums.org/showthread.php?p=5071005#post5071005)

redirected the plugin to find Java, just like I thought :0D  I am sooo glad to have this resolved, and thanks to everyone for their help!

Cheers,
~Jen

---

