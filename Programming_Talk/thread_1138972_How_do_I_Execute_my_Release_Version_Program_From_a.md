---
title: "How do I Execute my Release Version Program From a Menu?"
date: 2009-04-26
forum: Programming Talk
---

### Post by rich1939 on 2009-04-26
I just finished creating the release version of my program and now I want to add it to one of the "Applications" menu categories...but even when I create a Launcher for it either as an "Application" or "Application in Terminal", it doesn't run.

However, when I open a Terminal window and browse to the Release directory and type "./myProg", it executes fine (but the terminal window is still there, of course).

I'd really like to launch it directly from the Applications menu and have it run. How do I do that?

---

### Post by Sinkingships7 on 2009-04-27
What's the command you use in the properties of your launcher?

---

### Post by rich1939 on 2009-04-27
> **Sinkingships7 said:**
> What's the command you use in the properties of your launcher?

I browsed to the directory and the command and it appears as follows in the Launcher properties:

```

/home/richard/Documents/Development/CBsolotime/solotime/bin/Release/solotime

```

The program also needs to read files in the "Release" directory, so if I have to move the whole thing to somewhere else, all of those files need to be moved, too.

If I navigate to the "Release" directory using the Places menu and double-click the "solotime" program, it runs fine.

Any suggestions on how to setup the Launcher?

---

