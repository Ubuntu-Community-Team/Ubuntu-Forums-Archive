---
title: "Documentation in Geany"
date: 2008-08-14
forum: Programming Talk
---

### Post by BioCleaner on 2008-08-14
Hy all! I started using Linux recenlty and I would like to try programming on it. I searched for an IDE for C/C++ and maybe Pascal and Geany seamed the most easy to use.
Now I have a question; is there a way to open the language documentations in Geany? I would like something compared to pressing F1 in Borland Pascal or in Borland C 3.1. I keep forgething the sintax for some C commands and I need it.
If you have another suggestion for an IDE for High School programming please tell me. :)

---

### Post by kknd on 2008-08-14
I think Geany its one of the best choices, because you will learn how the entire process works!

For documentation:

In the VTE widget (the embedded terminal), type "man function", like "man memcpy" and you should get a detailed manual.

---

### Post by BioCleaner on 2008-08-14
I am not sure i got in right. I typed "man memcpy" in the terminal bellow "Messages" and "Scribble" but i got the following error:
"No manual entry for memcpy"

---

### Post by arist0tle on 2008-08-14
You can actually download ( svn checkout ) the source from the website. I think I remember having to run a script to generate the docs. Try looking through the README files in the source. I believe it tells you how to it in there. Geany is good choice. I use it everyday.

---

### Post by arist0tle on 2008-08-14
Sorry...a bit vague I suppose if you are new to Linux..... 

1) Make sure you have subversion installed (If you are a CS student or are serious about a career in the field, definitley learn about subversion - and version control ). 
  Run: 
    sudo apt-get install svn

2) Go to  [http://geany.uvena.de/Download/SVN](http://geany.uvena.de/Download/SVN)
3) Open a terminal and cd Desktop
4) run: svn co [https://geany.svn.sourceforge.net/svnroot/geany/trunk](https://geany.svn.sourceforge.net/svnroot/geany/trunk) geany 
5) look at the file 'HACKING'. It will tell you how to generate the docs

---

### Post by BioCleaner on 2008-08-14
Thanks. I am looking at the HACKING file now. I did as you said with one exception. I first typed "sudo apt-get install subversion".With "svn" it didn't work.
If you could explain to me what I just did I would be very grateful.

---

### Post by arist0tle on 2008-08-15
Yeah sorry about that. The package is subversion - svn is short for subversion (typo). What you did was check out a copy of the source code from the repository that the developers use to develop geany. Repositories are great when developing, especially when development involves more than one person (but I use it on projects that I alone develop). Basically it stores all of the versions of the project that you are working on. You can look at things you did before, revert changes that you made to a previous version, and log all of your changes. A repo' allows developers to keep a synchronized copy of the code. For example, you and I are working on some code. We each have our local copy that we work on on our own computers. When I finish implementing some code ( a new feature, some new methods, or whatever...), I commit my changes to the repo(svn commit). Then you can retrieve those changes and have them merged into your copy by running svn update ( or svn up - same thing ). You can't commit to the geany repo (this is a configurable option to not let certain people commit - after all, very often you dont want to allow just anyone to make changes to your code in the repo), but you can checkout and change it 'til your heart's content on your own machine. Also, the geany project has a mailing list for the subversion repository. I subscribe to it. Whenever anyone commits to the repository, I get an email which contains their commit message ( a message they enter stating the changes they made ) and the files which were affected by the change(s). Its great. Whenever I see a feature or fix that is added that I really want, Ill just do another checkout and rebuild and reinstall. This is the kind of transparency that rocks in the open source community. Peace. Dave

---

