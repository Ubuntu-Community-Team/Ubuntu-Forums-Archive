---
title: "Eclipse: Java IDE or C++ IDE?"
date: 2010-02-09
forum: Programming Talk
---

### Post by Kenny_Strawn on 2010-02-09
I posted a thread about Linux native C++ IDEs. I got a post about Eclipse in it.

I installed Eclipse, and want to know: How come I don't see the term "C++" anywhere in the Help? All I see is the option to create Java projects or text projects.

Do I need to install a C++ plugin or something?

---

### Post by gusnan on 2010-02-09
C++ support for Eclipse comes in the form of a plugin named CDT.

[http://www.eclipse.org/cdt/](http://www.eclipse.org/cdt/)

---

### Post by Kenny_Strawn on 2010-02-09
Great, now I downloaded this plugin and imported it.

The ultimate question: How do I take advantage of this plugin? How do I view C++ code or use C++ objects, for that matter?

---

### Post by Queue29 on 2010-02-09
> **Kenny_Strawn said:**
> Great, now I downloaded this plugin and imported it.

The ultimate question: How do I take advantage of this plugin? How do I view C++ code or use C++ objects, for that matter?

File -> Open

Select .cpp and .h files of interest.

---

### Post by Kenny_Strawn on 2010-02-10
> **Queue29 said:**
> File -> Open

Select .cpp and .h files of interest.

Yes, but how about creating _**new**_ C++ projects?

---

### Post by Reiger on 2010-02-10
As you would do Java projects; simply selecting a different project type from the Wizard?

---

### Post by akshayy on 2010-02-10
In my eclipse, i clearly have options for New->C++ Projects!

---

### Post by Kenny_Strawn on 2010-02-10
[ATTACH]146631[/ATTACH]

There is clearly no option for "C++" in here.

---

### Post by Simian Man on 2010-02-10
Did you install it from the repositories?  The last time I used Ubuntu, the version they shipped with was laughably old.  What version are you running?  And how did you install the cdt?

---

### Post by Kenny_Strawn on 2010-02-10
> **Simian Man said:**
> Did you install it from the repositories?  The last time I used Ubuntu, the version they shipped with was laughably old.  What version are you running?  And how did you install the cdt?

I installed it from the Lucid repo.

As for the CDT plugin, I imported it via the "Import Plugins and Fragments" dialog. Is it supposed to be installed this way?

---

### Post by eewoz on 2010-02-10
> **Kenny_Strawn said:**
> I installed it from the Lucid repo.

As for the CDT plugin, I imported it via the "Import Plugins and Fragments" dialog. Is it supposed to be installed this way?

I think the best way to 'install' Eclipse with the CDT plugin is to go to [http://www.eclipse.org/downloads/](http://www.eclipse.org/downloads/) and select "Eclipse IDE for C/C++ developers".  My understanding of Eclipse is that it is not really installed, it is just more of a program that you download and run.

---

### Post by Kenny_Strawn on 2010-02-11
> **eewoz said:**
> I think the best way to 'install' Eclipse with the CDT plugin is to go to [http://www.eclipse.org/downloads/](http://www.eclipse.org/downloads/) and select "Eclipse IDE for C/C++ developers".  My understanding of Eclipse is that it is not really installed, it is just more of a program that you download and run.

That was fine, except that when I tried to install the C++ version, it wouldn't load, saying that it REQUIRED Java in order to run.

I decided to use Geany instead, which knows C++ by heart.

---

### Post by CptPicard on 2010-02-11
Well, Eclipse is after all a Java application and originally a Java IDE, so no wonder a lot of the core editing and code management support is in the Java default... :)

---

