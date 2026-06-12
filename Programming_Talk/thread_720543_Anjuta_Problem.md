---
title: "Anjuta Problem"
date: 2008-03-10
forum: Programming Talk
---

### Post by gos1 on 2008-03-10
Hi : 
  
     I switched from Windows to Kubuntu and was using the Zend Studio for php applications . Now When I was looking for an Editor like Zend . I found the most similar one Anjuta . Which At least completes the variables . 
 
     Now When I try to import my files in the Anjuta as a new project in KDE I am getting this error : 
 
     Could not find a valid project backend for the directory given (/home/cem/ivan/files). Please select a different directory, or try upgrading to a newer version of the Gnome Build Framework.
 
      And When I try to make a new project : 
 
    Could not find autogen version 5, please install the autogen package. You can get it from [http://autogen.sourceforge.net](http://autogen.sourceforge.net)
 
      The question is am I choosing the right Editor for PHP . Or does  anyone knows a better one . Which completes braces and variables at lest ? ANd allows me to seacrh in all the files in a directory .

---

### Post by S15_88 on 2008-03-10
as for your problems i'm not sure what the deal is.  But Eclipse is a good IDE it's used by many for c/c++ java and php.

Thanks, ALain

---

### Post by cdekter on 2008-03-12
I've been using Quanta Plus to do some PHP development and found it very good. It's more of a full-featured web development studio. Overall the editor part of it is really nice, and if you enable the right settings it will do full completion and hints for PHP. I find it does just the right amount without getting in my way. You'll find it in the Ubuntu repositories.

---

### Post by namaster on 2009-03-01
i am having also same problem. Any help on how to fix it ? Using hardy 8.0.4.

---

### Post by ebharv on 2009-03-19
To fix the autogen problem you can to a 
```
sudo apt-get install autogen
```or goto Synaptic and search for autogen and install the newest package.
Don't know how to fix the other problem though.

But if you just want a PHP IDE I you should try Eclipse or NetBeans with the PHP plugins. Both have available php debuggers, so if you have a lammp/xampp installed you can debug your php code by stepping through line for line. I've used both of them and they're pretty similar. I liked the NetBeans better though. It was also easier to install the NetBeans stuff. A word to the wise, DO NOT use the Eclipse or NetBeans (if there is one) from the default repositories. The Eclipse is out dated and installing the PDT (php package for Eclipse) will be hell.

Go here for [NetBeans ]("http://www.netbeans.org/")and [NetBeans PHP]("http://www.netbeans.org/features/php/index.html")
Go here for [Eclipse]("http://www.eclipse.org/") and [Eclispe PDT]("http://www.eclipse.org/pdt/")

---

### Post by cjsteele on 2009-10-20
I've been scouring the web looking for a good PHP IDE that isn't Zend Studio (which is what I would really like, but alas, I don't have $800.)  I've tried Anjuta, phpedit, vim (which is what I'm currently using), and am in process of downloading eclipse.  My big desires are a built-in file manager, class browser, syntax highlighting and project space.  WHile completion is nice, it isn't necessary for me.

Anywho, just was wondering what others have found?  I know this post is old.

Cheers,
-C

---

