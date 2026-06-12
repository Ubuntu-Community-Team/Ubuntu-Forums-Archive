---
title: "CrashPlan interface does not open (Ubuntu 12.04)"
date: 2012-11-25
forum: New to Ubuntu
---

### Post by Alb123 on 2012-11-25
Hello,

I have used [CrashPlan]("http://www.crashplan.com/") to back up data to another computer for a few months without problems. Since one or two weeks, when I try to open the UI (CrashPlanDesktop), I see the green splash screen for a few seconds, then it closes and nothing happens. This means that I cannot change my back up settings, restore files previously backed up, etc.

I am a newbie. My OS is Ubuntu 12.04 32-bit and it is up-to-date.

The following information may be useful:

The problem arises when I try to start the UI with a launcher and also when I enter the commands "CrashPlanDesktop" or "/usr/local/crashplan/bin/CrashPlanDesktop" in the terminal.

CrashPlanEngine is running, or so I am told when I enter "/usr/local/crashplan/bin/CrashPlanEngine status" in a terminal.

Messages on the computer I am backing up suggest that the engine is continuing to back up my data once a day as it used to. I cannot verify if this is the case as I am unable to open the CrashPlan interface on the other computer to restore files.

I tried to uninstall CrashPlan and reinstall it to see if this would fix the problem. At the end of the reinstall, a message on the terminal asked me if I wanted to start CrashPlanDesktop. I did, the UI started up, I logged onto my account, all my backup locations were showing up, and then I closed CrashPlanDesktop. But when I tried to open it again, the problem arose again: I saw the splash screen for a few seconds and then nothing.

I thought that there may be a problem with Java, but two other programs that run on Java (MuCommander and Tomighty) appear to work fine on my computer. By entering "update-java-alternatives -l" in a terminal, I found out that these are the versions of java that I have installed:

java-1.6.0-openjdk-i386 1061 /usr/lib/jvm/java-1.6.0-openjdk-i386
java-1.7.0-openjdk-i386 1051 /usr/lib/jvm/java-1.7.0-openjdk-i386

I am using the free version of CrashPlan, so I cannot use the company's technical support.

Many thanks in advance for your help.

---

### Post by ibjsb4 on 2012-11-25
I do not use CrashPlan, but did come across this.

[https://bugs.launchpad.net/ubuntu/+source/openjdk-6/+bug/712119](https://bugs.launchpad.net/ubuntu/+source/openjdk-6/+bug/712119)

That fix is dated and may not relate to your problem.  All the forum hits can be found here:

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=crashplan&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=crashplan&as_qdr=all&sa=Google+Search&lang=en)

That's all I have to offer, good luck.

---

### Post by Alb123 on 2012-11-25
Many thanks for the link.

The solution suggested in the linked post is to remove the package "libgail-common": "GNOME Accessibility Implementation Library -- common modules". I found out that it is needed by Orca reader and I use neither it, nor other accessibility programs/functions. However, the package description states that it contains core shared libraries and I am weary of uninstalling it for fear of breaking something (I am a newbie, cannot really fix things and have to use the Ubuntu computer for work). Can anyone confirm if uninstalling that package is safe/breaks anything?

Many thanks!

---

### Post by Alb123 on 2012-11-26
I did uninstall it. The CrashPlan UI now opens fine and my system appears to work fine without that package.

Thanks for the advice.

---

### Post by ibjsb4 on 2012-11-26
Welcome  :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

