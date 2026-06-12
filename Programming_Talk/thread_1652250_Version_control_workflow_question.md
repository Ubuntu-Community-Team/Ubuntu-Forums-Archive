---
title: "Version control workflow question"
date: 2010-12-24
forum: Programming Talk
---

### Post by japhyr on 2010-12-24
Hello,

After years of saving filenames such as "Class.py", "Class_2_works.py", "Class_3_addedNewMethod.py", I finally installed Subversion and learned how to use it.  It is wonderful.

I am only using this for small projects on my own, but I have a question about proper workflow using version control software.  I understand that the basic approach is:[LIST]
[*]check out a current working copy;
[*]modify the code to add a specific piece of functionality;
[*]update the working copy and resolve any conflicts;
[*]commit changes to the repository, with a clear log message.
[/LIST]
I am wondering about how to save changes during the second step, modifying the code.  Say I am working on making an on-screen report printable.  When adding this functionality I end up changing a number of files and trying a number of approaches.  I end up wanting to save versions of this work before knowing that the whole functionality works.  Since I am working alone, I just make a series of commits with log messages such as "progress - started to generate pdf of report".  I know this would not work in a collaborative environment because I would be polluting the main repository with partially-functioning code.

What is the proper approach?  Do developers keep their own version control system on their local machine, to check in changes as they progress on their specific assignment, and then commit final changes to the main repository?

---

### Post by Arndt on 2010-12-24
> **japhyr said:**
> Hello,

After years of saving filenames such as "Class.py", "Class_2_works.py", "Class_3_addedNewMethod.py", I finally installed Subversion and learned how to use it.  It is wonderful.

I am only using this for small projects on my own, but I have a question about proper workflow using version control software.  I understand that the basic approach is:[LIST]
[*]check out a current working copy;
[*]modify the code to add a specific piece of functionality;
[*]update the working copy and resolve any conflicts;
[*]commit changes to the repository, with a clear log message.
[/LIST]
I am wondering about how to save changes during the second step, modifying the code.  Say I am working on making an on-screen report printable.  When adding this functionality I end up changing a number of files and trying a number of approaches.  I end up wanting to save versions of this work before knowing that the whole functionality works.  Since I am working alone, I just make a series of commits with log messages such as "progress - started to generate pdf of report".  I know this would not work in a collaborative environment because I would be polluting the main repository with partially-functioning code.

What is the proper approach?  Do developers keep their own version control system on their local machine, to check in changes as they progress on their specific assignment, and then commit final changes to the main repository?

One way is to use branches. Another way is when your work does not interfere with the others'. In practice, there's often a mix. Having a common test setup which runs tests each time something is checked in is often a good idea. If you don't have test cases yet for your new things, at least the test runs will tell you if you broke something already existing. Preferably you run the tests yourself before checking in things, but inevitable it happens that the tests grow to the point of being too time-consuming to run for every change, and then you make a judgement whether it's necessary and sometimes it's wrong. At least in small cooperative groups, this can work.

One school of thought stipulates that you can never check in a change without first making a test case for it. Maybe that works, I've never encountered the practice.

---

### Post by CptPicard on 2010-12-24
I would suggest that you ditch svn for git; it is in pretty much all ways superior. Not only is it far easier to keep your own local repository (actually, there is no specific "central repository) in git, but branching and small commits is very natural in git-world; it really works excellently in exactly the scenario you describe.

At work my workflow using git is "create branch for new feature, work in that branch making small commits, merge feature branch to master, push to origin server for others to pull".

---

