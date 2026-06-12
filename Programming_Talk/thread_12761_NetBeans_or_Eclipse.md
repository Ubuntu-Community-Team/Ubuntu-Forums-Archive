---
title: "NetBeans or Eclipse?"
date: 2005-01-26
forum: Programming Talk
---

### Post by gheorghe_pop on 2005-01-26
I like NetBeans because it's easy,easy to install and i love SUN

---

### Post by mendicant on 2005-01-26
I used Eclipse.  Netbeans was far too ugly when I initially started trying them out (fontwise, configuration wise)--I just didn't like the UI.  Don't know about the latest versions of netbeans--I last tried 6 months ago or so.

---

### Post by jerome bettis on 2005-01-27
good question.

they both have good and bad things going for them.  but i voted for eclipse, netbeans is a little bloated and clunky i think.

netbeans 4.0 has come a long way from 3.0.  give it a try, you might like it.  the worst thing about 3.0 in my opinion was getting started (that whole business of mounting file systems and such).  now that's gone and it's much simpler.

---

### Post by gheorghe_pop on 2005-01-27
[http://overholt.ca/wp/index.php?p=11](http://overholt.ca/wp/index.php?p=11)
I tried eclipse long a go.I didn't like it.It was to heavy and to slow.In the link that i posted it's a flash demo of Eclipse.In my opinion it's a lot of work for building such a simple project.

---

### Post by pitr on 2005-01-27
I must admit I haven't used netbeans much and it was a long time since I last used it but I consider Eclipse to be an excellent IDE. Altought it might be problems using it on low-/midlevel machines since it is a bit memory/cpu hungry. I recommand a minimum ram of 256MB but if you plan to use the Visual Editor for building GUIs then 512 is more likly.

---

### Post by fng on 2005-01-27
I just heared eclipse will be the official development platform for the new versions of Progress and Webspeed.

---

### Post by defkewl on 2005-02-12
I use Eclipse and NetBeans in production. But if you want me to choose, then I'd prefer Eclipse since it has good a wide variety of plugins. One plugin I really loved is Lomboz. NetBeans is suck when it comes to J2EE, since it's platform oriented: Sun AppServer. Daargh, the damn slow appserver. Btw, when it comes to speed, NetBeans is nothing compared to Eclipse. This is one of the biggest issue when comparing them both.

---

### Post by hantsy on 2005-03-02
[QUOTE=defkewl]I use Eclipse and NetBeans in production. But if you want me to choose, then I'd prefer Eclipse since it has good a wide variety of plugins. One plugin I really loved is Lomboz. NetBeans is suck when it comes to J2EE, since it's platform oriented: Sun AppServer. Daargh, the damn slow appserver. Btw, when it comes to speed, NetBeans is nothing compared to Eclipse. This is one of the biggest issue when comparing them both.[/QUOTE]
Yeah,eclipse have so many plugins , but most of them are gargage...expect some excellent such as ,jboss ide ,lomzo , phpeclispe...

---

### Post by Poldi on 2005-03-03
[QUOTE=defkewl]I use Eclipse and NetBeans in production. But if you want me to choose, then I'd prefer Eclipse since it has good a wide variety of plugins. One plugin I really loved is Lomboz. NetBeans is suck when it comes to J2EE, since it's platform oriented: Sun AppServer. Daargh, the damn slow appserver. Btw, when it comes to speed, NetBeans is nothing compared to Eclipse. This is one of the biggest issue when comparing them both.[/QUOTE]

I cannot agree. I use Eclipse since 1.0 and NetBeans since 2.0 (from the pre-Sun area). Eclipse (3.01) with Windows XP is what I use 8-12 hours a day for work and NetBeans (4.0) on Ubuntu is what I do all my private stuff with.

not only is Eclipse less responsive that NetBeans when I compare my Windows-desktop at work with my Ubuntu-Thinkpad at home (both nearly equal in terms of power) - in Linux the situation worsens because the Gtk-SWT port is way slower than the Win32 SWT. yes, I could use the plain X11 version but that's just too ugly.

NetBeans and Swing both have gotten much faster in recent releases. the only sad issue for me on the ui part is that the J2SE 5.0 Swing Gtk-LookAndFeel is so buggy / incomplete that Netbeans looks better with Synth than with Gtk lnf.

regarding J2EE: Eclipse is completely dependant on plugins for this while NetBeans comes with very good support for the web-tier in 4.0 (JSP-degugging anyone?) and 4.1 (the beta is out and rather stable) will have support for the whole J2EE stack including EJB.

you can get NetBeans with or without default-implementation for the container. I don't understand why you think it would work only/better with the Sun implementation - I use NetBeans with both Bea and JBoss containers and a friend of mine uses Jones AFAIK.

kind regards,
Carsten

---

### Post by JeffS on 2005-03-03
[QUOTE=Poldi]I cannot agree. I use Eclipse since 1.0 and NetBeans since 2.0 (from the pre-Sun area). Eclipse (3.01) with Windows XP is what I use 8-12 hours a day for work and NetBeans (4.0) on Ubuntu is what I do all my private stuff with.

not only is Eclipse less responsive that NetBeans when I compare my Windows-desktop at work with my Ubuntu-Thinkpad at home (both nearly equal in terms of power) - in Linux the situation worsens because the Gtk-SWT port is way slower than the Win32 SWT. yes, I could use the plain X11 version but that's just too ugly.

NetBeans and Swing both have gotten much faster in recent releases. the only sad issue for me on the ui part is that the J2SE 5.0 Swing Gtk-LookAndFeel is so buggy / incomplete that Netbeans looks better with Synth than with Gtk lnf.

regarding J2EE: Eclipse is completely dependant on plugins for this while NetBeans comes with very good support for the web-tier in 4.0 (JSP-degugging anyone?) and 4.1 (the beta is out and rather stable) will have support for the whole J2EE stack including EJB.

you can get NetBeans with or without default-implementation for the container. I don't understand why you think it would work only/better with the Sun implementation - I use NetBeans with both Bea and JBoss containers and a friend of mine uses Jones AFAIK.

kind regards,
Carsten[/QUOTE]


What are the minimum hardware requirements to run NetBeans with Ubuntu?  ie cpu and memory?

---

### Post by rom on 2005-03-03
Hi all,

few things very cool i like about eclipse are:
 - the cvs browser: you can browse modules, whereas is netbeans I had to know and therefore to remember it.
 - dynamic compilation of java classes: no need run ant, just save the file. You never end up saving and committing files into cvs that don't compile.
 - the .project file is very covenient. Just cvs' it and then anyone else committing in a project will get it to and therefore get the workspace configured the way it should.
 - cvs tools are excellent. please see point one, but it also concerns the diff viewer the management of head/sub branches, ...

However, 
 - JSP support is poor, even with Lomboz. Dont get me wrong, it does do a fantastic job but sometimes, with the Log4J lib for example, it just keeps outputing kilometers of s*** in the logs. I hear some of you saying I mis-configured it or something. Possible, but then Eclipse should have offered some sort of JSP support anyway, taht's the least you should expect for a Java IDE.
 - mirrors for updates are painfully slow, wherever I tried this feature from.
 - slow to start. I'm running it on an AMD64 2.4Ghz and a P4 2.8 with both 1Go of Ram: takes around 10 seconds, I really would not like to having to use it on slower hardware.


Just my two cents. Also, I'm not really trying to compare Netbeans and Eclipse. I'm merely explaining what I like and dislike about Eclipse, and most likely Netbeans shares a few of those points.
All considered, Eclipse does do a great job in a professional environment, which is where I use it the most.

Romain

---

### Post by brk3 on 2005-03-09
netbeans!!! It is the best by far

---

### Post by Viro on 2005-03-12
I'm actually torn between the two :). I've used Netbeans for a long time and am far more familiar with it. But I decided to move when Netbeans 4 was released as they dumped a simple project manager for something more complex (like Eclipse's). I figured, since that was the only thing that stopped me from using Eclipse before, now that I have no more reason to stick to Netbeans, I might as well go to Eclipse.

On the PPC platform, I needed to recompile somethings just to get Eclipse to work. Illustrates one of the failings of SWT. Write once, compile everywhere :(. But after getting it working, the UI looks great! It's not as responsive as Netbeans though, but I think the layout is better.

Netbeans has an advantage when designing GUI apps. It's got a very functional GUI editor, something that Eclipse's VE project doesn't match yet. Eclipse is way too slow here.

---

### Post by Viro on 2005-03-12
[QUOTE=JeffS]What are the minimum hardware requirements to run NetBeans with Ubuntu?  ie cpu and memory?[/QUOTE]
 512 MB minimum, or else you'll get bad performance. Same with Eclipse. CPU speed is variable. I'm running it on a 1.33 GHz G4 processor and I don't mind the performance.

EDIT: Under Gnome's System Monitor, Eclipse is reporting 650 MB memory usage, while Netbeans is using only 260 MB. That's a *lot* of RAM to be wasting. These IDEs are huge.

---

### Post by dcviana on 2005-11-24
I used both Eclipse and Netbeans. Netbeans is better in terms of J2EE, but now I use Eclipse with the Web Tools plugins, wich gives me excelent J2EE support. Only complain here is that it didn't came bundled.

Concerning the visual part, Eclipse + VE is better than Netbeans. In Eclipse I can get a class extending JFrame made with any other editor and it "learns" the way the class mount the form. Netbeans in the other hand totally screwed up when I tried to import a JFrame class from another editor.

And if any of you think VE is slow, then try [Jigloo]("http://cloudgarden.com/jigloo/"). Its a visual editor plugin MUCH faster than VE, and its capacity of learning how to mount a form class created somewhere else is better than both Eclipse VE and Netbeans. Only problem is that its not free for comercial use, only for home use.

---

### Post by amohanty on 2005-11-26
Not trying to flame or anything, but I have found that gvim (on cygwin compiled with athena widgets - gtk look sucks on cygwin - no less) with a properly setup exuberant ctags and the javabrowser plugin kicks everybody else's ass.  I do use eclipse a bit but only for debugging purposes. When it comes to UI development having done quite a bit of MFC dev, Swing coding is quite frankly a joke to handle, so I have never needed the GUI builder.

Just my $0.02

AM

---

### Post by viscount on 2005-12-25
[QUOTE=rom]Hi all,
 takes around 10 seconds, I really would not like to having to use it on slower hardware.
Romain[/QUOTE]

I have slower hardware than you, AMD 2500+ with 512mb ram, and Eclipse
is fully loaded in under 8 seconds for me.

I suggest you switch to the sun-jdk-1.5 if you havent already, you'll notice a good
speed improvement.

---

### Post by infinitybrain on 2009-10-14
hey guys ive dual booted with Ubuntu 9.04 and Windows Xp on my pc(1.3 cpu ,512 ram etc...) and  on ubuntu Eclipse is too heave to run and some times become too slow.sure its because pc but NetBeans is much better in Linux and i use Eclispe on Xp and its working well i think (i can use netbeans in xp too but maybe some day i need some Extra Eclipse need hehe ,who knows !!!)

---

### Post by TheBuzzSaw on 2009-10-14
You do realize this thread is almost **four years old**, right?

---

