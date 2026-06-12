---
title: "CVS newbie - won't let me login"
date: 2007-03-02
forum: Programming Talk
---

### Post by andrew222 on 2007-03-02
Hello all,

Today is my first time using CVS.  I just had a project accepted by sourceforge and I am trying to login to the CVS.   I type in the same password that I use to login to my account on sourceforge.net's website. I am typing in 'cvs login' and getting this error message:

CVS password: 
cvs login: authorization failed: server algebraagent.cvs.sourceforge.net rejected access to /cvsroot/algebraagent for user andrewgonzales
andrew@Ubuntu-one:~/Desktop$ 


I also try to login as an anonymous user and get this:

andrew@Ubuntu-one:~/Desktop$  cvs -d:pserver:anonymous@algebraagent.cvs.sourceforge.net:/cvsroot/algebraagent login
Logging in to :pserver:anonymous@algebraagent.cvs.sourceforge.net:2401/cvsroot/algebraagent
CVS password: 
cvs login: authorization failed: server algebraagent.cvs.sourceforge.net rejected access to /cvsroot/algebraagent for user anonymous
 


  Am I doing anything wrong? Should I be doing something different? Hopesomeone can help me out

---

