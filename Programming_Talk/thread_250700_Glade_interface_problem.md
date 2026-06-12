---
title: "Glade interface problem"
date: 2006-09-04
forum: Programming Talk
---

### Post by dave_567 on 2006-09-04
I seem to have a path problem.  When I try making a project everything seems to work fine.  I can even save the project file.

When I try to build the file and get the output code I get the following error message.

*** Error running glade--to generate the C++ source code.
*** Check that you have glade-- installed and that it is in your PATH.
*** Then try running 'glade-- <project_fle.glade>>' in  termnal. 

My son and I will both be programing so I'll need to change the path for both of us.  How to do it is the problem.  Where is the setup file with the global path definition?  Or is there a better approach?

Thanks

---

### Post by ifokkema on 2006-09-06
Do you have glademm installed?

Please note that Glade is notoriously bad at producing C++ code.

---

### Post by dave_567 on 2006-09-06
Thanks for the answer.  I installed Glade from the Applications -> Add/Remove programs utility.  So I relly have no idea which individual packages were instlled.  I ran the package manager and you are right, I don't have that package installed.  I'll do it now.

I did not know about the problems with Glade.  How is the c code?  

I'm just starting to learn to code in Linux/Gnome.  I thought that the interface seemed to give me a good start.  Is there a better interface to go with or should I work without an interface at first.

---

### Post by ifokkema on 2006-09-07
> **dave_567 said:**
> I did not know about the problems with Glade.  How is the c code?
As far as I know, it's much better. When I tried working with Glade and C++, all I read on the net was all the problems people were having and how it would be removed from Glade as a whole. The C code creator seemed to work just fine, but I needed C++ and dropped Glade.

I would recommend [libglade]("http://www.jamesh.id.au/software/libglade/"), though. It parsed the glade XML file and works with that.

> **dave_567 said:**
> I'm just starting to learn to code in Linux/Gnome.  I thought that the interface seemed to give me a good start.  Is there a better interface to go with or should I work without an interface at first.
I guess it's a matter of preference. I've worked both directions. If you need a program that can be disconnected from the GUI, I would first write the code, then add the interface. If you need a program that only operates from the GUI, starting with the interface and then writing the program sounds good to me.

Have fun!

---

