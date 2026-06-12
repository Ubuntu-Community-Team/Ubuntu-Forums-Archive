---
title: "Eclipse errors"
date: 2007-01-16
forum: Programming Talk
---

### Post by Mirrorball on 2007-01-16
I'm getting this error message when I launch a C++ program from Eclipse. I've downloaded and installed Eclipse 3.2.1 and Sun JDK 6 myself, not from Ubuntu packages. Both are for amd64.

```
!ENTRY org.eclipse.core.jobs 4 2 2007-01-16 17:02:40.476
!MESSAGE An internal error occurred during: "Launching".
!STACK 0
java.lang.NullPointerException
    at org.eclipse.cdt.launch.internal.LocalCDILaunchDelegate.runLocalApplication(LocalCDILaunchDelegate.java:83)
    at org.eclipse.cdt.launch.internal.LocalCDILaunchDelegate.launch(LocalCDILaunchDelegate.java:62)
    at org.eclipse.debug.internal.core.LaunchConfiguration.launch(LaunchConfiguration.java:639)
    at org.eclipse.debug.internal.core.LaunchConfiguration.launch(LaunchConfiguration.java:565)
    at org.eclipse.debug.internal.ui.DebugUIPlugin.buildAndLaunch(DebugUIPlugin.java:754)
    at org.eclipse.debug.internal.ui.DebugUIPlugin$6.run(DebugUIPlugin.java:944)
    at org.eclipse.core.internal.jobs.Worker.run(Worker.java:58)
```

What could be wrong?

---

### Post by Mirrorball on 2007-01-16
It's going to be sad if I have to launch the program from a terminal every time from now on. Help?

---

### Post by Mirrorball on 2007-01-17
I'll be trying the x86 version today. Good luck to me!

---

### Post by Mirrorball on 2007-01-17
I'm getting very angry at Eclipse.

```

!ENTRY org.eclipse.core.jobs 4 2 2007-01-17 14:08:17.877
!MESSAGE An internal error occurred during: "Launching".
!STACK 0
java.lang.NullPointerException
    at org.eclipse.cdt.launch.internal.LocalCDILaunchDelegate.runLocalApplication(LocalCDILaunchDelegate.java:83)
    at org.eclipse.cdt.launch.internal.LocalCDILaunchDelegate.launch(LocalCDILaunchDelegate.java:62)
    at org.eclipse.debug.internal.core.LaunchConfiguration.launch(LaunchConfiguration.java:639)
    at org.eclipse.debug.internal.core.LaunchConfiguration.launch(LaunchConfiguration.java:565)
    at org.eclipse.debug.internal.ui.DebugUIPlugin.buildAndLaunch(DebugUIPlugin.java:754)
    at org.eclipse.debug.internal.ui.DebugUIPlugin$6.run(DebugUIPlugin.java:944)
    at org.eclipse.core.internal.jobs.Worker.run(Worker.java:58)

```

---

### Post by mrdean on 2007-01-17
Eclipse seems to have problems while trying to run GCC. Dumb question, have you configured path to Gcc? Have you googled your error message, that usually helps resolve the problem .

---

### Post by phossal on 2007-01-17
> **mrdean said:**
> Have you googled your error message, that usually helps resolve the problem .

Wow. I can't wait to see his reply to that. :p

---

### Post by Mirrorball on 2007-01-17
Yes, I have googled my error message and found nothing. The path to gcc is correct, the project compiles just fine. It just doesn't launch. But I can launch the program from a terminal myself.

**It works now.** I've created another C++ project and I can launch the program. I still don't know what was wrong with the other though.

---

### Post by phossal on 2007-01-18
How are you launching it from within eclipse? In other words, how *should* it work? What do you click, etc? How did you install CDT, and what package/versions did you install of eclipse/CDT?

---

### Post by phossal on 2007-01-18
I had never used the CDT plug-ins before. I only downloaded them because you seem to be so taken with them, and you're having problems. I'm *almost sure* I installed them incorrectly, because I never end up with anything the way it's *supposed to be*. But it all works for me.

Here's what I did: I reinstalled everything from scratch, including build-essential, etc. Downloaded the standard JDK 6 and eclipse per my [usual method]("http://ubuntuforums.org/showthread.php?t=332674") (32Bit version), and then downloaded this: [org.eclipse.cdt.sdk-3.1.1-linux.x86.tar.gz]("http://download.eclipse.org/tools/cdt/releases/callisto/dist/3.1.1/"). 

Because I leave my "eclipse" folder so-named on my desktop, I temporarily renamed it so that when I right-click/extract the CDT package, it doesn't error out. Extracting it produces a folder of the same name: eclipse. Then I opened it, copy and pasted the folders from the Features/Plugins folder of the (now named) eclipse folder into the corresponding folders of the (now-named) eclipse_core folder.

In other words, I'm taking all the folders out of the plugins folder of the CDT file, and putting them in the plugins folder of the eclipse (core) file. I do the same for features. Then I launch eclipse.

I really had no idea how to do anything, so I found a simple tutorial to make and launch a Hello World project (via eclipse). Worked like a charm. On save, it created a binary, and when I hit the green *run* button, it spit out some text to the eclipse console. Is that how it *should* work?

I did notice this: > One thing to note about the CDT is that, up to this point, we are very tied to specific versions of the Eclipse Platform release. So please be careful how you are matching these versions.

---

### Post by phossal on 2007-01-18
lol Ugh. I just realized you solved it *hours ago*. That's depressing. The downside is I spent an hour learning something new. The upside is I spent an hour learning something new. I might just ditch the text editors and do *everything* in eclipse. It just needs an order pizza plug-in. :D

---

### Post by Mirrorball on 2007-01-18
:D Sorry for the trouble. I should have posted a new message to say that I solved the problem instead of editing my last one.

---

### Post by chibisam on 2009-10-02
er...I just installed ubuntu 9.04 & Eclipse today, and  found that i had the same trouble with you....
also i solve the problem just by create a new project (with totally the same content) .. it's much too strange....&#22247;
 hah~``i'm a green hand ^^  it's the first time i install ubuntu~``

---

