---
title: "Debugging in Kdevelop?"
date: 2006-08-24
forum: Programming Talk
---

### Post by g9mekopi on 2006-08-24
Hi,

I'm using Kdevelop for the first time (in Kubuntu) and want to run a C program in the debugger. Obviously I need to compile it with debugging information and all the documentation I can find says you turn this on by going to Project Options -> Compile Options.

Problem is, there is no "Compiler Options" under "Project Options" or anywhere else. There are "Build Options" and Debugger options, but they don't have anything about compiling with debugging information. Nor can I find anything under Settings -> Configure Kdevelop

Am I crazy or just blind? How do you turn on debugging in Kdevelop3?

Thanks

---

### Post by Roque on 2006-08-26
Just go to Project->Build Configuration->Debug

---

### Post by g9mekopi on 2006-08-26
Thanks, but under "Project," there is no "Build Configuration." There is "Project Options", if that's what you meant, and a "Build Options" under that , but nothing about debugging.

---

### Post by Roque on 2006-08-29
Strange...
What KDevelop version are you using? "Build Configuration" should be placed above "Project Options".

Clicking in "Build Configuration" should open a submenu with three choices: Debug, Optimized and Default.

---

### Post by mycelo on 2006-08-30
Some project options were moved to Automake Manager (I'm not sure about debugging though), so you can have different options for different subprojects. Open the Automake Manager tab and right-click your project's branch.

Also, the debug profile is usually the default. Are you sure that it isn't already enabled? As far as I remember, debugging worked right out of the box for me.

mycelo

---

