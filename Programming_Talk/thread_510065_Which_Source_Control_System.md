---
title: "Which Source Control System?"
date: 2007-07-26
forum: Programming Talk
---

### Post by gushy on 2007-07-26
Guys,

I need to implement a source control server for our java guys at work, I know nothing about source control and I'm getting confused as to which will be best for their needs; cvs, subversion, git, bazaar .... etc

Our Java devs are Windows guys, all using Eclipse; none of them will want to use a console to check things in and out so I need to be able to give them nice Windows guis, or at least nice gui plugins for Eclipse.

Any recommendations?

TIA

---

### Post by Limpan on 2007-07-26
I would say Subversion. There are two good plug ins for Eclipse; Subclipse and Subversive. I would say that the latter is slightly better but they essentially provide the same functionality.

[http://subclipse.tigris.org/]("http://subclipse.tigris.org/")
[http://www.polarion.org/index.php?page=overview&project=subversive]("http://www.polarion.org/index.php?page=overview&project=subversive")

---

### Post by gushy on 2007-07-26
excellent thanks, I'll check them out. :)

---

### Post by Limpan on 2007-07-26
Be wary that the Subversive plug in only works by default in Windows. This is because they use binaries of JavaHL to provide Subversion functionality. Make sure to follow [these]("http://www.polarion.org/index.php?page=installation&project=subversive#notes") instructions if you don't already have SVNKit and are using Ubuntu.

---

### Post by gushy on 2007-07-26
that's fine, they are windows users anyway.

---

### Post by oparnier on 2007-07-26
I have experienced CVS and Subversion in Eclipse.

And for me, CVS client is better stable than subversion client implementation (subversive or subeclipse)

CVS client is also included in original eclipse installation

---

### Post by pmasiar on 2007-07-26
Why stop at repository? get [TRAC](http://en.wikipedia.org/wiki/Trac), which integrates code repository, change viewer (in browser, with colors), bug tracking database, and wiki for docs. Special commit messages, like "fixed 1234" will on code commit go to bug database and close bug 1234 for you.

---

### Post by solarwind on 2008-02-28
I would say subversion and subclipse are the best and easiest tools to use and set up.

---

### Post by gushy on 2008-02-29
Catherine, thanks for posting information on your company's products, however a windows / sql server based solution is not for us as our servers are linux based.  

We went with Subversion in the end, easy to setup and it gives us a lot of flexibility.

I'm not sure what client the java guys have gone with in the end, I know they've tried a couple; I believe subclipse and a windows standalone client are their current favourite options (not sure on the standalone client, but I think it gives the the ability to have subversion commands on right-click in windows explorer).  On linux 'm currently sticking with a stand alone client (RapidSVN).

---

