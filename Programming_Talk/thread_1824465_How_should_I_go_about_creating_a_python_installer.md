---
title: "How should I go about creating a python installer?"
date: 2011-08-13
forum: Programming Talk
---

### Post by Ryland Taylor on 2011-08-13
I've been programming for a long time. It started as a hobby, and I eventually started getting jobs developing web applications. When I was programming as a hobby, I never really made anything serious that people would want to install on their computers, and I hardly ever finished my projects either. All my projects were more like learning experiences than actual projects. And all the jobs I've had were in web development, where the applications only had to run on the websites server and didn't have to be installed on other peoples computers. Now, I'm finally making something that people are taking interest in, and I need an installer. I don't  have much of an idea of how to make an installer. The program requires pygame and twisted. Pygame's easy to install on Windows, but twisted requires zope.interface, which requires setuptools, which requires you to edit your PATH variable, which I don't expect most Windows users to know how to do, or want to learn how to do. For now, I'll just make the installer in python, but I may want to make an msi later. Does anyone have any pointers on where I should start with this? Thanks.

---

### Post by Queue29 on 2011-08-14
Seems like you're looking to make an installer for Windows specifically? If so, try asking on a Windows (or perhaps Python) oriented forum.

---

### Post by lavinog on 2011-08-15
py2exe is what you are looking for.
[http://www.py2exe.org/](http://www.py2exe.org/)

---

