---
title: "Netbeans vs Eclipse"
date: 2007-02-04
forum: Programming Talk
---

### Post by phossal on 2007-02-04
I had a free weekend to try out some new things. One of the things I had on my to-do list that I figured would take about two minutes was looking at the netbeans IDE. I happen to be an Eclipse fan, but I was *shocked* by how much I *like* netbeans. I used to be really turned off by Java's "applet"-like application appearance. Eclipse is *beautiful*, where netbeans is cartoon-like. But netbeans is *incredible*. I've been in a bit of rut with my Java programming lately (having already played with most of the API's that interest me), yet using netbeans for just a couple hours has opened my eyes to a whole world of possibilities.

Has anyone else experienced that recently? Have you changed from one language, IDE, or library just on a whim and found yourself *surprised* by how useful or intuitive or *fun* it was?

---

### Post by flossgeek on 2007-02-04
They are both great IDE's and Both Open Source.

---

### Post by phossal on 2007-02-04
> **flossgeek said:**
> They are both great IDE's and Both Open Source.
Yeah, I know it. It's amazing. I like Ubuntu, but I don't really use my computer for anything except to hang out at the forums and development. I don't use Open Office, or games or anything. My love for Ubuntu really comes from liking the ability to do what I want at the command line in two seconds. I can *hack* together whatever I want to do in a couple of steps. If I screw something up, I just trash it and move on. 

Eclipse and NetBeans though? Wow! Amazing applications. It's just shocking to be able to get such useful, relatively intuitive tools to make the life of the guy who makes the lives of other guys easier - easier. lol 

It makes me wonder how such a thing can possibly exist in this world. It violates the laws of the universe somehow. I kinda dig it though.

---

### Post by kinson on 2007-02-04
> **phossal said:**
> 
It makes me wonder how such a thing can possibly exist in this world. It violates the laws of the universe somehow. I kinda dig it though.

It probably violates the laws of the corporate universe :D In terms of community(Open source), its probably the norm.

share and share alike, thats what I say :)

Cheers,
Kinson

---

### Post by laxmanb on 2007-02-05
Yeah, they're both kinda cool... (I <heart> Netbeans, tho)

---

### Post by ZylGadis on 2007-02-05
Netbeans all the way - not because Eclipse is stupid, but because it is built on top of the abomination that is SWT.

Btw, have you tried running Netbeans with Swing's GTK plaf? It looks native in Gnome, and not at all cartoonish. Perhaps there is a KDE plaf, too, but I don't use KDE.

```
netbeans-5.5/bin/netbeans --laf com.sun.java.swing.plaf.gtk.GTKLookAndFeel
```

---

### Post by phossal on 2007-02-05
That's a useful tip! Thanks, I'm going to try it now.

---

### Post by Ramses de Norre on 2007-02-05
> **ZylGadis said:**
> Netbeans all the way - not because Eclipse is stupid, but because it is built on top of the abomination that is SWT.

Btw, have you tried running Netbeans with Swing's GTK plaf? It looks native in Gnome, and not at all cartoonish. Perhaps there is a KDE plaf, too, but I don't use KDE.

```
netbeans-5.5/bin/netbeans --laf com.sun.java.swing.plaf.gtk.GTKLookAndFeel
```

If you add ```
export _JAVA_OPTIONS="-Dswing.defaultlaf=com.sun.java.swing.plaf.gtk.GTKLookAndFeel"
```
to your ~/.bashrc this will be the default plaf for all apps.

---

### Post by phossal on 2007-02-05
Good tips, really. The truth is that I don't really *like* the GTK look and feel any more than the default. I'm neutral to them all, I guess. Thanks again, though, for the tip.

---

### Post by randomnumber on 2007-02-05
My vote is for eclipse, that is just because I use it. I have not used the other. I understand that they are almost the same.

I know that eclipse has some issues but it is still faster and easier to use it. Just do not expect to learn it in one night.

---

### Post by phossal on 2007-02-05
> **randomnumber said:**
> I understand that they are almost the same.
They really aren't *that* similar. In some area, like GUI development, *beans is so far ahead, so intuitive, and so different that it's like doing something totally different than programming. I would never build another GUI in eclipse as long as eclipse remains as it is.

But, in general, I prefer eclipse, too.

---

### Post by asimon on 2007-03-09
I don't do much Java development but a couple of days ago I also come to really like netbeans 6.0's nightly builds because of their great Ruby support. For Ruby (without Rails) it already looks better than the Eclipse-based RDT/Radrails.

---

### Post by laxmanb on 2007-03-09
They're both cool... among the best IDEs in the world ...

---

### Post by Cyril on 2007-03-09
My opinion after using netbeans for a j2EE project is that it is s...l...o...w.... and buggy. Have not used eclispe so I cannot comment.

---

### Post by laxmanb on 2007-03-09
Hmmm... do you have enough RAM? 256 MB is the bare minimum, 512 MB is recommended...

---

### Post by pmasiar on 2007-03-09
> **phossal said:**
> netbeans is *incredible*. 

Thanks for sharing, phossal. I assumed that Eclipse is open-sourced and netbeans is not, and that everyone uses Eclipse with Java, so I never looked at netbeans. My bad. :-( I guess it is marketing hype spell IBM casted on me :-( :-(

For me one of important deciding factors between Eclipse/netbeans would be strength of opensource and commercial plugin development community, but I am not sure how to compare them easy. My gut feeling is that Eclipse is ahead in comunity mindshare - maybe because netbeans opened only recently, like Java itself? Anyone has opinions/references/links to how plugin architectures of Eclipse/netbeans compare?

Phossal, you said that GUI development is much better in netbeans - good to know. But I am more interested in web application development in Struts. I overheard somewhere that netbeans is better than Eclipse for javascript debugging. Anybody has experience with AJAX and can compare AJAX for Eclipse/netbeans? And other issue for me would be Struts development. I tried commercial MyEclipse plugin, I consider MyEclipse plugin usefull (but  not spectacular and in parts annoying). My trial period is ending soon and i need to shell out $50 or find decent free replacement.. Is WTP (free eclipse plugin) comparable? Does netbeans has something like that?

I shifted focus slightly to web development - I do hope you will not consider this hijacking :-) if you do, my apologies.

---

### Post by laxmanb on 2007-03-09
Just download Netbeans from [www.netbeans.org](www.netbeans.org) and see if it meets your needs... it is more intuitive than Eclipse, so you can feel comfortable using it almost instantly...

Netbeans has been open since 2002. just got lost in the SWT/Eclipse hype...

---

### Post by phossal on 2007-03-09
I like netbeans a lot, but for *most* of what I do with Java during the day, I've headed back to eclipse.

---

### Post by laxmanb on 2007-03-09
Anyway... it's good to experiment. I'll still keep using Netbeans and will move to Netbeans 6.0 when that comes.... will try that JRuby integration everyone's talking about...

---

### Post by JoxBG on 2007-03-21
> **Cyril said:**
> My opinion after using netbeans for a j2EE project is that it is s...l...o...w.... and buggy. Have not used eclispe so I cannot comment.

Try Eclipse on Linux,  then you'll really know the meaning of s....l....o....w.  Netbeans 5.5 is way much faster then Eclipse..on Linux anyway. And the C/C++ plugin pack just works. :)

---

### Post by mnml on 2008-03-09
I have been using both, and... I prefer Netbeans, Faster, Easier, Reverse UML integrated..

---

### Post by glok_twen on 2008-03-09
if you want to build a j2se or java gui app netbeans seems much more intuitive than eclipse. and i really like the matisse project gui that's now standard in it.

however with c++ if you use the fall or winter 3.3 eclipse versions i have found it to be much more reliable in terms of being able to import a project, have it generate the make file just from reading the code, do auto compiles in the back ground when you save the code and a lot more. (i did need to upgrade to gdb 6.7.1 tho to overcome an issue in debugging, and this is not the version with gutsy afaik).

also if you mix in some python the again goes to eclipse with pydev.

---

### Post by jespdj on 2008-03-10
> **Cyril said:**
> My opinion after using netbeans for a j2EE project is that it is s...l...o...w.... and buggy. Have not used eclispe so I cannot comment.
> **JoxBG said:**
> Try Eclipse on Linux,  then you'll really know the meaning of s....l....o....w.  Netbeans 5.5 is way much faster then Eclipse..on Linux anyway. And the C/C++ plugin pack just works. :)
Are you sure you are running it on a **real** version of Java (Sun Java 5 or 6) and not on crappy GNU Java (gcj / gij)? Because GNU Java is slow and incomplete and will make any Java program run slowly. Sun Java 5 or newer is quite fast.

I am an Eclipse user, but NetBeans, especially NetBeans 6.0, is very good too. I'm not using NetBeans every day, but the last time I tried it out I immediately missed all the great refactoring tools that Eclipse has. Maybe they're there in NetBeans and I just couldn't find them.

The Matisse GUI builder in NetBeans is great, and better than Eclipse's GUI builder (Visual Editor); although you can get very good GUI builders for Eclipse too (such as [WindowBuilder Pro](http://www.instantiations.com/windowbuilderpro/default.htm) - it costs money).

---

### Post by imagecko on 2008-03-10
I'm an former Windows programmer. N'I have now switched to Linux, and I'm planing on learning Java.
What editor do you suggest for a java-newbie? Eclipse or netbeans?

---

### Post by themusicwave on 2008-03-10
I was using eclipse primarily, but then I suddenly needed a GUI.

I then realized that Eclipse has basically no swing support that I could find that was free.  I switched to Netbeans and haven't looked back for J2SE development.  The GUI editor in Netbeans is very nice and it spoiled me, no more coding GUIs by hand for me!

It reminds me of the JBuilder GUI Designer from JBuilder 2005 and it uses either AWT or Swing.  I have no knowledge of SWT and no desire to learn it right now.  Swing has always worked just fine for me.

I also like how Netbeans has UML with reverse engineer right out of the box.  I think that going to school for Software Engineering just drilled the need for UML into my head, I just won't write a lien of code till I have a UML diagram sorted out for most projects.  It also has a handy reverse engineer feature to turn code into UML.  Great for syncing UML and code or creating that UML you were too lazy to make.

However, I do like Eclipse for Python and PHP development.  Pydev is a nice package.  When I am editing something that is more than a few simple scripts I prefer Eclipse with Pydev to IDLE.

I don't write much PHP(prefer python), but when I do I use Eclipse with the PHP plugin.

Eclipse does have a lot of plugins going for it, which is a nice feature.

I can't comment on C/C++ development as I haven't used either for that.

I'm a firm believer in using the best tool for the job.  Find the tool that works best for you.  For J2SE that's Netbeans for me.

---

