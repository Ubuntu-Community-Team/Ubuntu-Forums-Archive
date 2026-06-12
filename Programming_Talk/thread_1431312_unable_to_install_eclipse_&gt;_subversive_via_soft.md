---
title: "unable to install eclipse &gt; subversive via software updates"
date: 2010-03-16
forum: Programming Talk
---

### Post by badperson on 2010-03-16
Hi,

I tried help > sofware updates > add site:

[http://community.polarion.com/projects/subversive/download/eclipse/2.0/galileo-site/](http://community.polarion.com/projects/subversive/download/eclipse/2.0/galileo-site/) 

I'm able to view different install options, but when I select one or more and hit "install" nothing happens. No error message, and nothing installs

any ideas? 
bp

---

### Post by Monkeon on 2010-03-16
Can you install anything via software update?

If not, have you tried setting GDK_NATIVE_WINDOWS to true before running eclipse?

i.e. export GDK_NATIVE_WINDOWS=true

I've got this in a script along with a line to run eclipse itself.

---

### Post by badperson on 2010-03-16
I just type this in the console? 
> export GDK_NATIVE_WINDOWS=true

---

### Post by Queue29 on 2010-03-16
> **badperson said:**
> I just type this in the console?

But not before crossing your fingers.

---

### Post by Monkeon on 2010-03-16
You can do it through the console, but you might have to run eclipse from the same session...I doubt setting it in the console, then running eclipse from the GUI would work.  That's why I tend to just do it using a script..

---

### Post by badperson on 2010-03-16
I installed a new version of eclipse, not in the repositories, and was able to install subversion, but now I have a new problem...

I created a url for my svn repo...svn+ssh://jason@<ip.addr>/code/svnrepo

When it asks me for my user/pw authentication, it means on the server, correct? 

I think I need to set up an svn user and have that in the svnserve.conf file....

anyone have any guidance for that? 
bp

---

