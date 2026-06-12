---
title: "Eclipse: Java debugger is not stopping at breakpoints"
date: 2009-05-03
forum: Programming Talk
---

### Post by VotaVader on 2009-05-03
I have no idea why this happens, but suddenly the Eclipse debugger isn't stopping at the new breakpoints I've added (which are all of them). I've even tried stopping the program at the beginning of the main method, but Eclipse just skips them all, and builds to the end.

Does anyone know how to fix this, or had this problem before? Thanks for any help. I'm coding in Java, by the way.

---

### Post by myrtle1908 on 2009-05-04
> **VotaVader said:**
> I have no idea why this happens, but suddenly the Eclipse debugger isn't stopping at the new breakpoints I've added (which are all of them). I've even tried stopping the program at the beginning of the main method, but Eclipse just skips them all, and builds to the end.

Does anyone know how to fix this, or had this problem before? Thanks for any help. I'm coding in Java, by the way.

Are you sure that you ran your program in debug mode and that you are in the Debug perspective at run-time?

---

### Post by VotaVader on 2009-05-04
> **myrtle1908 said:**
> Are you sure that you ran your program in debug mode and that you are in the Debug perspective at run-time?

Yes, I usually use this method for debugging, and it works perfectly. It's just now that it's giving me this trouble.
I ended up toggling breakpoints in all of the methods and noticed that it only stopped in one (with no particular characteristics), and skips all the rest. Still haven't figured out why, so it's been a real hassle to debug (what with putting prints to console everywhere, and skipping between calls to that method...).
It's really starting to piss me off, so please a some help! :confused:

---

### Post by mkwinter on 2009-05-20
Hi VotaVoder -- did you ever resolve this?  

I'm seeing the same behavior with Eclipse 3.2 on Jaunty Jackal:

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.04
DISTRIB_CODENAME=jaunty
DISTRIB_DESCRIPTION="Ubuntu 9.04"

Any resolution?

---

### Post by VotaVader on 2009-05-20
> **mkwinter said:**
> Hi VotaVoder -- did you ever resolve this?  

I'm seeing the same behavior with Eclipse 3.2 on Jaunty Jackal:

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.04
DISTRIB_CODENAME=jaunty
DISTRIB_DESCRIPTION="Ubuntu 9.04"

Any resolution?

Nope, sorry. I have the same version of Eclipse on Intrepid, but haven't fixed the problem. I started a new project now, and the breakpoints seem to be working relatively fine. Some random breakpoints don't stop, but most do. I've noticed they tend to work more when set at function calls (instead of variable declarations, loops, etc). It's not really much help, but I suggest making a new project with the same java files and see if it works, because the truth is I have no idea where this problem comes from... sorry
Hope you get it working! I did have to debug a whole program using System.out.print XD ... it was a pain.

---

### Post by gojomo on 2009-07-24
It's a bug in Java 6u14; see (near the end -- the 7/20 and 7/21 updates):

[https://bugs.eclipse.org/bugs/show_bug.cgi?id=279137](https://bugs.eclipse.org/bugs/show_bug.cgi?id=279137)

Workarounds are apparently to either:

(1) revert to u13 for debugging

(2) use -XX:+UseParallelGC option on JVM launch

---

### Post by Rikko on 2009-07-31
Thanks gojomo - I can confirm this fixed it for me!

---

### Post by vishnujyothi on 2010-03-09
Hey..Its still in unresolved state.am using ubuntu 9.10,eclipse galileo with jdk 1.6.14 ..am also facing same situation..clear solution is not specified in [eclipse forum]("https://bugs.eclipse.org/bugs/show_bug.cgi?id=279137")

i tried to solve this by starting my tomcat server in debugging mode for instance i thought it had really solved my problem, it began to hit for sometime..then its gone..dont know what to do..:confused::confused:

My thread to tis problem :[http://ubuntuforums.org/showthread.php?t=1425670 ]("http://ubuntuforums.org/showthread.php?t=1425670")

---

### Post by =mike= on 2010-07-26
To everyone who is having this issue it is related to the JDK version "jdk 1.6.0_14" for some reason there is an issue with update 14 skipping breakpoints sometimes. This can be fixed for sure by going back to version 13, and I am told by some people I work with that all later versions work as well.

Edit: downgrading to 13 may cause some issues since it is an older version, so you are better off upgrading to the newest jdk

---

### Post by tlowery on 2010-09-10
I'm using 1.6.0_20-b02 and I'm still having the problem.  So it doesn't look like it was fixed in updates after 14.

---

### Post by tacun on 2010-10-22
i want to say "thanks" for your help. I had the same problem working on windows 2003, elcipse 3.5.0. and jdk 1.6.15  
After adding the JVM options, i can debug ok. (I think there is not a ubuntu problem)

---

### Post by wkhasintha on 2010-10-24
I use netbeans .. no hassle.

---

### Post by tzh2231 on 2011-06-23
Hi Tacun, where did you put in the JVM option? I cannot find a clue where to put it...

> **tacun said:**
> i want to say "thanks" for your help. I had the same problem working on windows 2003, elcipse 3.5.0. and jdk 1.6.15  
After adding the JVM options, i can debug ok. (I think there is not a ubuntu problem)

---

### Post by cgroza on 2011-06-23
> **tzh2231 said:**
> Hi Tacun, where did you put in the JVM option? I cannot find a clue where to put it...
That guy hasn't logged on since October 2010 ;).

---

### Post by tzh2231 on 2011-06-23
duh~~~ good observation... anyone got any idea?
shame on java for not fixing such an issue for so many years!!!

> **cgroza said:**
> That guy hasn't logged on since October 2010 ;).

---

### Post by series0 on 2011-07-07
I am also experiencing this same issue at random.

Eclipse/Tomcat debug that simply ignores the fact that I hit the debug button to start.  Its as if I had just hit run but it goes further than that for me.  

All of my code changes since my last working debug run are ignored.  Everything in the project is saved.  Sometimes I even change several files and save them just to make sure.  Then clear the Tomcat application relationship.  Then debug.  Runs just like nothing had been changed since last effective debug run stopping at no breakpoints.  Gee Thanks!

I have found 1 workaround.  Close Eclipse entirely and re-enter it.  Then you get 1 more good debug run.  Thrills.

---

### Post by Jenga201 on 2011-09-13
I had this problem not too long ago.  Project>Clean fixed it for me.

---

### Post by crackers8199 on 2012-01-02
i'm having this issue right now suddenly with an android app i'm writing...it's frustrating the hell out of me, as it has pretty much completely disrupted my development.

anyone know how to fix it?  project -> clean didn't do anything...

---

### Post by fluca1978 on 2012-01-02
My experience is that Eclipse and Ubuntu often get strange behavior, I suspect it is due to the choice of the JVM version and options from Ubuntu updates.

---

### Post by crackers8199 on 2012-01-02
awesome :/

it was working fine until yesterday...is there a way i can get debugging back?  i'd rather not have to wipe my entire machine and start over...

---

