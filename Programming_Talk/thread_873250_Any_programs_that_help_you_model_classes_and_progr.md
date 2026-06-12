---
title: "Any programs that help you model classes and programs?"
date: 2008-07-28
forum: Programming Talk
---

### Post by ogwilson on 2008-07-28
I know I could do it in an image editor but itd really be cool if i could do this in a dedicated application. One that specifically uses UML would be cool, and platform could be linux or windows.

---

### Post by jay019 on 2008-07-28
Have you had a look at Dia or ArgoUML?
Dia is in repositories, ArgoUML is Java and is at [http://argouml-downloads.tigris.org/](http://argouml-downloads.tigris.org/) and can even be run online via webstart.

Some IDE's like Netbeans and Eclipse have UML capabilities too, so there are a few options open for you.

---

### Post by imdano on 2008-07-28
One of the most popular tools for doing what you describe is [UML.](http://en.wikipedia.org/wiki/Unified_Modeling_Language)  I can't really help you with a program for creating the diagrams unfortunately, the only ones I've used are propriety and for Windows.  It looks like the poster above me mentioned a few possibilities though.

---

### Post by tinny on 2008-07-28
What language? (I know UML is meant to just be OO but the tools tend not to be)

Ive used the NetBeans UML tool. You can reverse engineer your code, this is very nice when you want to get the big picture idea of the code quickly.

[http://www.netbeans.org/features/uml/](http://www.netbeans.org/features/uml/)

This is the best free UML tool ive seen for Java development. The "good" eclipse tools are commercial.

[http://www.visual-paradigm.com/product/vpuml/](http://www.visual-paradigm.com/product/vpuml/)

---

### Post by Diabolis on 2008-07-28
You can also try eclipse, it has a plug in that generates uml diagrams. I like it better than the one in netbeans, but that is just a matter of preference.

I think that the one in eclipse can also generate the code from a uml diagram, not sure tho.

---

### Post by tinny on 2008-07-28
> **Diabolis said:**
> You can also try eclipse, it has a plug in that generates uml diagrams. I like it better than the one in netbeans, but that is just a matter of preference.

I think that the one in eclipse can also generate the code from a uml diagram, not sure tho.

What UML Eclipse plug-in is that? There are many. The best Eclipse UML plug-in is visual-paradigm

---

### Post by Diabolis on 2008-07-28
> **tinny said:**
> What UML Eclipse plug-in is that? There are many. The best Eclipse UML plug-in is visual-paradigm

I've used [topcased]("http://www.eclipseplugincentral.com/Web_Links-index-req-viewlink-cid-696.html").

Since you mentioned visual-paradigm, I'll give it a try the next time I work in eclipse.

---

### Post by tinny on 2008-07-28
> **Diabolis said:**
> I've used [topcased]("http://www.eclipseplugincentral.com/Web_Links-index-req-viewlink-cid-696.html").

Since you mentioned visual-paradigm, I'll give it a try the next time I work in eclipse.

Does topcased work well? Does it support full round trip engineering? update model > auto update code, update code > auto update model?

---

### Post by ogwilson on 2008-07-28
Thanks guys. I use both Netbeans and Eclipse in my everyday needs, and im surprised that i hadnt looked into programs for either of these. the only plugin i downloaded was the CDT. I program in Java mostly, C++ occasionally, and C# for my own fun.

---

### Post by Quikee on 2008-07-29
> **tinny said:**
> Does topcased work well? Does it support full round trip engineering? update model > auto update code, update code > auto update model?

Neh.. there is no advantage having a 1:1 class diagram to real class synchronization unless you want to have auto-updating of a model for architecture documentation. You might in such a case go fully MDA/MDSD (using something like [OAW]("http://www.openarchitectureware.org/")) with a domain specific model and a more useful code generation (and UML generation out of your model if you need it). UML should just be used for "picture drawing" as you have a standardized set of constructs so that everyone understand you when you describe your architecture - this is what UML was designed for.

---

### Post by tinny on 2008-07-29
> **Quikee said:**
> Neh.. there is no advantage having a 1:1 class diagram to real class synchronization unless you want to have auto-updating of a model for architecture documentation. You might in such a case go fully MDA/MDSD (using something like [OAW]("http://www.openarchitectureware.org/")) with a domain specific model and a more useful code generation (and UML generation out of your model if you need it). UML should just be used for "picture drawing" as you have a standardized set of constructs so that everyone understand you when you describe your architecture - this is what UML was designed for.

Yep, well said.

I just use UML to explain my ideas to others (on a white board usually) or I use the reverse engineering functions of the tools stated above to get a very quick "big picture" idea of a mass of code. UML really does seem to slowly be becoming less relevant due to the mass uptake of Agile methodologies.

---

### Post by ch0d3 on 2009-02-12
Sorry to bring up an older thread, but I am looking for some alternatives to Eclipse for creating UML diagrams. I would prefer open source, but many of these tools for linux seem to be closed. I am going to check out [Dia]("http://live.gnome.org/Dia") tonight. 

Maybe we could add some links to the programming tools sticky?

---

### Post by Quikee on 2009-02-13
> **ch0d3 said:**
> Sorry to bring up an older thread, but I am looking for some alternatives to Eclipse for creating UML diagrams. I would prefer open source, but many of these tools for linux seem to be closed. I am going to check out [Dia]("http://live.gnome.org/Dia") tonight. 

Maybe we could add some links to the programming tools sticky?

Also check out Umbrello. It is IMHO one of the best open source tools for UML modelling (or at least good for drawing diagrams). It is for KDE and it is available in the Ubuntu repository.

---

