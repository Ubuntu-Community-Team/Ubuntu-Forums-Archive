---
title: "Ant problems - ignores 'delete' task?"
date: 2008-05-08
forum: Programming Talk
---

### Post by Tomosaur on 2008-05-08
Hi guys - just doing some work for an exam tomorrow. I'm toying around with ant via the terminal (normally juse let the IDE do the work - but for this exam I have to be familiar with ant being used from the command line), and I'm running into one pretty annoying problem.

When I use the 'delete' built-in task, ant just seems to ignore it. It doesn't give me any error messages or anything, it's just as if I never put a delete command in at all. Can somebody test this and let me know what happens? Another problem is that ant doesn't seem to try and use build.xml if I just start ant by typing 'ant' at the command line. I have to give it an option (either by specifying build.xml manually, or by calling a target in the build file like this: 'ant init'). In fact I'm fairly sure that the issue is entirely that ant refuses to take any of my options. If I type, for example 'ant -version', it complains that there is no default build file. The issues with 'delete' may simply be that ant doesn't even bother trying to find the 'clean' target at all.

Anyway attached is a basic testing setup comprised of a src directory (with a Hello World Java file), and build.xml). The expected behaviour when you type 'ant' in this directory should be for the Java file to be compiled, a 'build' dir to be created and the .class file put into 'build'. If you type 'ant clean', the build directory should be deleted. I have no problems if I just let ant do the work (as the default target is 'compile' in the build file), so compiling the Java file and creating the build directory works fnie - I just can't get ant to run the 'clean' target.

If somebody can let me know whether it works for them I'd really appreciate it. I'm using Gutsy, and the ant I have is from the repos (tried using the build available from the apache website, but no difference in behaviour).

If I use ant through an IDE (say Eclipse, or NetBeans), there are no problems.

---

### Post by yaaarrrgg on 2008-05-09
This works fine for me,  One quick observation ... you probably don't need the 'depends="init"' in the clean target.

Running this should work though:

ant clean

ETA: I'm running hardy with netbeans 6 installed.

---

