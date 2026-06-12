---
title: "New project needs testing"
date: 2006-07-24
forum: Programming Talk
---

### Post by cro.smiley on 2006-07-24
Finally i have released first version of TimeSaver, application I'm developing for a while. It is a is simple time management application. It alows user to keep track of the time spent on different activities.

Project homepage: [http://timesaver.sourceforge.net]("http://timesaver.sourceforge.net")
Project summary: [http://sourceforge.net/projects/timesaver]("http://sourceforge.net/projects/timesaver")
Download: [http://sourceforge.net/project/showfiles.php?group_id=170378]("http://sourceforge.net/project/showfiles.php?group_id=170378")

Application is made using wxWidgets and C++ with Kdevelop.
I have published documentation, so feel free to sugest any better solutions.

I hope you will find something useful in my small piece of work. :)
Any kind of feedback is welcome.

---

### Post by xtacocorex on 2006-07-25
I haven't had a need for a program like this, but I figured I'd test because it sounded fun before I finished getting ready to work.

The program is nice, I did have to install the wxWidgets libraries because I didn't have them, but if you end up creating a .deb file, you can have it install them it they aren't already installed.

I haven't fully tested it, but I did create two tasks, started one, stopped it and then deleted it so that works.

I really like this and will now have to find a use for it. Maybe have it report on a day to day basis of what tasks a person has done. This way, if you use it at your job, you can show your supervisor what you've been doing all day. I know that if it had that feature, I could get some of my IT friends at work using it since they have to record their time. Have you tested this on other distros? I'm assuming it'll work, but have no means to try.

A suggestion, in order to keep closing consistant with other Linux programs, the key shortcut for close should be Ctrl+q or Shft+Ctrl+q.

Keep up the good work!

---

### Post by Engnome on 2006-07-25
> **cro.smiley said:**
> Finally i have released first version of TimeSaver, application I'm developing for a while. It is a is simple time management application. It alows user to keep track of the time spent on different activities.


And reports it to google for profiling;)

---

### Post by cro.smiley on 2006-07-25
> **xtacocorex said:**
> 
I really like this and will now have to find a use for it. Maybe have it report on a day to day basis of what tasks a person has done. This way, if you use it at your job, you can show your supervisor what you've been doing all day. 

Interesting idea. I've made a new release with a basic report option. It extracts all current tasks to html file that you can use as a report. In src directory is a template.html file that is used for creating report and you can change it as you wish.

> **xtacocorex said:**
> 
A suggestion, in order to keep closing consistant with other Linux programs, the key shortcut for close should be Ctrl+q or Shft+Ctrl+q.


Fixed :)

---

### Post by xtacocorex on 2006-07-25
Awesome!

I'll have to tell my friend at work to get the source and try it on his RHEL 4 machine.

I'm going to get the source tonight and recompile.

---

### Post by cro.smiley on 2006-07-29
I have improved report generation by adding xml support using TinyXml. Sessions can now be saved and loaded from xml file. That file can be opened in browser to see session report. This is handled using xsl style sheet, which formats xml file to look nice. Xsl file comes with application and can be edited if user wants to have his report look differently.

Here is example report: [sample report.xml]("http://timesaver.sourceforge.net/samples/sample%20report.xml") 
This is xsl file: [report.xsl]("http://timesaver.sourceforge.net/samples/report.xsl")

This all comes in beta 0.3 release, so feel free to [try it]("http://sourceforge.net/project/showfiles.php?group_id=170378") and send me your opinions.

---

### Post by xtacocorex on 2006-07-29
Forgot to add comments about version 0.2, so I'm back testing 0.3beta. The reporting is far superior now and a lot more stable. 0.2 crashed on me when I tried to view the report.

Keep up the good work!

---

### Post by cro.smiley on 2006-08-06
I've made first debian package thanx to [this thread]("http://www.ubuntuforums.org/showthread.php?t=51003"). Installation worked ok at me, but there could still be some dependencies problems.

You can check it [here]("http://sourceforge.net/project/showfiles.php?group_id=170378") and let me know if it works.
Also, does anyone know how to put files in Ubuntu repository?

---

### Post by ifokkema on 2006-08-07
> **cro.smiley said:**
> I've made first debian package thanx to this thread. Installation worked ok at me, but there could still be some dependencies problems.
Nice...!

> **cro.smiley said:**
> Also, does anyone know how to put files in Ubuntu repository?
Well, that's not as easy as following a tutorial step by step, I'm afraid. You need to be a maintainer to be able to upload stuff to the servers. But first off, you would need to get your package into the lists but I think you need to build quite official packages, not the 'hack' (sorry) you have right now...

But hey, you could always just start off with your own repository, can't you :)

---

### Post by cro.smiley on 2006-08-31
New beta release is out.

Check new features and news: [http://timesaver.sourceforge.net]("http://timesaver.sourceforge.net")
Wiki pages: [http://www.bluwiki.org/go/TimeSaver]("http://www.bluwiki.org/go/TimeSaver")
Download: [sources on sourceforge.net]("http://sourceforge.net/project/showfiles.php?group_id=170378&package_id=194451")

[IMG]http://img371.imageshack.us/img371/4481/tsaverbeta05jy9.jpg[/IMG]

I need testers to help me debug and improve application.
So if you have some free time feel free to try TimeSaver and send me your feedback.

NOTE: [wxWidgets]("http://www.wxwidgets.org/") are required.

---

