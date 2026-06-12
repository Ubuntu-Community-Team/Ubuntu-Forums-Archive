---
title: "Doxygen for commenting?"
date: 2007-01-17
forum: Programming Talk
---

### Post by jaboc83 on 2007-01-17
For School I had a Professor that always made us use Doxygen for creating design documents and UML diagrams. I would assume that you would never find this in industry, but It was actually fairly impressive for large scale projects. Anybody here have any experience with Doxygen? What did you think?

- Jake

---

### Post by pmasiar on 2007-01-17
Never tried doxygen. But I really like using a wiki for docs - pages are online, edit using plain browser. TRAC  - [http://trac.edgewall.org/](http://trac.edgewall.org/) integrates a wiki, bug tracker, subversion code repository, and code viewer. Pretty neat! YMMV

---

### Post by welshboy on 2007-01-17
This is probably a very very thick question, but what is Doxygen?

---

### Post by supirman on 2007-01-17
We use doxygen at my company, so saying you'd not find it in industry isn't accurate.

---

### Post by engineer on 2007-01-18
we also use it in enterprise. but i must say, i don't like the html output of doxygen.

but it's good to have source comments in a standard format, means people spend more time, writing these comments. for me as a programmer the source comments would be enough, don't need any html (or whatever) documentation.

---

### Post by lloyd mcclendon on 2007-01-18
we've been using javadoc, springs beandoc, jira, subversion, and confluence.  it would be nice to have something integrated.  jira is a very nice piece of work, confluence looks even cooler but i haven't messed with it too much yet. 

any links to some doxygen stuff?  samples, how it works etc.  i'd like to evaluate it so i have a legitmate excuse to put off a clusterfuck project that i don't want to touch.

---

### Post by amo-ej1 on 2007-01-18
i use it all the time for generation api documentation and for making the code browsable. This is also in the industry where all documentation is valuable.

---

### Post by jaboc83 on 2007-01-18
wow, I'm glad to hear it has seen some use outside of the academic setting. I personally like using the LaTeX to make a single .pdf. it makes it much more clean to look at. I have an example project [here]("http://studentweb.stcloudstate.edu/moja0401/referenceManual.pdf") for those who have no idea what it does. Please excuse the code and documentation quality. It was kind of a rush job.

-Jake

---

### Post by hod139 on 2007-01-19
If you like LaTeX you should check out [nuweb.]("http://nuweb.sourceforge.net/nuwebhtml/index.html")

Basically, you combine all your source code (language independent) inside a latex document containing all your documentation.  You can then do all sorts of crazy LaTeX style referencing to certain parts of code, etc.  I didn't really like it but some people do.

---

### Post by Verminox on 2007-01-19
I think Doxygen is just too good. I have used for two projects and it gives results that are exactly what you would have hard coded yourself in HTML. And you dont require to keep code, comments, and docs separate. Everything is done at once. Every change in the source can change the corresponding docs with a single command. Great stuff.

---

