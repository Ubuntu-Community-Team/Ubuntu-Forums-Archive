---
title: "Python - IDLE unusable?"
date: 2008-03-20
forum: Programming Talk
---

### Post by Minguo on 2008-03-20
Hey, I've swtiched over to Ubuntu and installed IDLE from the ubuntu repos to continue python development.

However, the Ubuntu version of Python does not have a 'restart shell' option.  There isn't even a 'shell' drop down menu and ctrl-F6 does nothing.

It's very tedious working with the interpreter to close and restart the program everythime I want to try somethng new.   Is this how IDLE is supposed to work on Ubuntu or is there something greater wrong?

---

### Post by pmasiar on 2008-03-20
CTRL-C should break currently executing program in shell - does it not?

---

### Post by Minguo on 2008-03-20
It does, although that isn't what I'm frustrated by.

I don't want to just stop executing code, I want to return the interpreter back to the initial state of script execution.  If I open up a script in Windows, and do Run-> Run Module, play wiht some variables and type in some new commands, then do Run-> Run Module again, the Shell restarts, IDLE checks the source code,  and reruns the script and re-initilizes any variables I have played with in the interpreter.  

In Linux, Run -> Run Module, the shell does NOT re-start, It does not check my source for changes, and any variables I have modified retain their modified values.   (Even though the old source tries to re-execute. )  I can live with this if I could manually restart the shell, but as I said I can't, without closing all windows and restarting IDLE.

The way it operates in windows is very helpful as I'm still learning. It allows me to run code, play with the results, then modify the source and rerun the whole thing to see how it turns out  differently.   The way Linux is behaving, it ignores any modifications to the source and just runs, and reruns the original script ignoring any changes except those I type into the interpreter. (WHich I *don't* want.)   Am I simply using it wrong?

---

### Post by OmegaBLK on 2008-04-27
I have noticed this issue also.  When I used Debian a few years ago the Shell Menu was available in their version of IDLE--not sure if it is there in the current Debian release.  I just returned to using IDLE and I do not recall if the SHELL Menu was in the Ubuntu version.  It is a nice feature and would love to get it back.  I am going to search the bug reports to see if one has been issued for this particular issue.

---

### Post by stevescripts on 2008-04-27
hmm ... in the idle installed on my gutsy box, ctrl-F6 restarts the shell ...

Steve

---

### Post by OmegaBLK on 2008-04-29
> **stevescripts said:**
> hmm ... in the idle installed on my gutsy box, ctrl-F6 restarts the shell ...

Steve

Like **Minguo** above, that key combination does not work for me also.  Tried with Compiz off and no change.  No way to add the Shell Menu with the restart-shell option either.  It's not really a deal breaker for me--just more convenient then exiting and restarting idle.  I'm using 1.2.1 in Gutsy and I think Feisty package was missing this Shell menu also.

---

### Post by stevescripts on 2008-04-29
Also Idle 1.2.1 here, on gutsy ... seems kinda strange. Not running Compiz.

Anybody got a clue?

---

### Post by OmegaBLK on 2008-05-02
Ok, I have found the solution to the problem.  The launcher/shortcut for IDLE in the application menu runs with "-n" option which is "Run IDLE without a subprocess".  This option prevents the Shell menu from appearing.  So if someone starts IDLE and sees the message "==== No Subprocess ====" in the shell then that means IDLE is running with the "-n" option on.  Run IDLE without the -n option on the command line/Run Application to solve this.  You can also edit the IDLE application menu  launcher and remove the "-n".

---

### Post by sirgimp on 2009-06-01
Please tell me how to edit IDLE so restart is available.

Thanks,

Jason Gervich:popcorn:

---

