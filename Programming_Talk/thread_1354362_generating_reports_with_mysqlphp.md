---
title: "generating reports with mysql/php"
date: 2009-12-13
forum: Programming Talk
---

### Post by TheShabz on 2009-12-13
Hey all, I'm looking for something that will mimic the report creating capability that MS Access has. Can anyone recommend software (freeware) that will generate a report and spit it out in php for me? hopefully something that has an intuitive GUI.

the goal is to take values from tables, do some math, and output as a chart and summarized information.

thank you

---

### Post by tgalati4 on 2009-12-13
sugarcrm.com  is licensed under the gplv3.  Lot's of php code to look at.  There's a studio designer that allows you to modify the existing behavior of the default modules and you can write your own modules.  There is also an active developer community with add-on php modules.

---

### Post by TheShabz on 2009-12-13
I took a look through demos and it seems wayy too advanced for my needs. This isnt for a business setting. What I'm looking to do is run some very basic statisitcs like how often was option A selected while optionB=true. stuff like that. im just looking for something that will turn the numbers into something graphical then give me the option to export.

---

### Post by myrtle1908 on 2009-12-13
If you just want to create charts etc then you can use GD.  Google it.  Here's one [http://devzone.zend.com/article/3774](http://devzone.zend.com/article/3774)

---

### Post by Hellkeepa on 2009-12-13
HELLo!

Here are some tutorials and scripts that might help you:
[http://www.tutorialtoday.com/read_tutorial/7/](http://www.tutorialtoday.com/read_tutorial/7/)
[http://davidwalsh.name/milkchart](http://davidwalsh.name/milkchart)
[http://www.aditus.nu/jpgraph/](http://www.aditus.nu/jpgraph/)
[http://www.hotscripts.com/category/php/scripts-programs/graphs-charts/](http://www.hotscripts.com/category/php/scripts-programs/graphs-charts/)

Just be aware over the fact that the security of these scripts are often non-existing, or seriously flawed. Like most tutorials, really. :-\

Here's the search I used to find these:
[http://www.google.no/search?hl=no&client=opera&rls=en-GB&hs=SK2&q=how+to+create+charts+php+statistics&btnG=S%C3%B8k&meta=&aq=f&oq=](http://www.google.no/search?hl=no&client=opera&rls=en-GB&hs=SK2&q=how+to+create+charts+php+statistics&btnG=S%C3%B8k&meta=&aq=f&oq=)

Happy codin'!

---

### Post by WitchCraft on 2011-09-10
BTW, you don't need to create reports manually.

Use Eclipse BIRT, it's a FOSS equivalent of MS-Reporting Service, 
and compared to SSRS, it's graphing capabilities are remarkable.

The drawback is that the BIRT runtime uses Java (Java fans will rejoice).

However, it uses GTK for the GUI, and the runtime is only server-side, so the user needn't to have java, which means it's bearable.

I still don't like the thought of having a Java application on my server, because (unlike .NET) they usually are memory hogs, which is fine for them because it speeds them up, but not for the rest of the programs on the server (e.g. database), because they don't have much memory left after some time.

---

