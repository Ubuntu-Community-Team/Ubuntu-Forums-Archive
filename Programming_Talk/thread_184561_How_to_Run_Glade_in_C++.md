---
title: "How to Run Glade in C++ ?"
date: 2006-05-30
forum: Programming Talk
---

### Post by kolichina_s_s on 2006-05-30
Hi,

I am using Glade Interface Designer with anjuta. I am having a problem creating a Glade Project with C++ code. cause when i am trying to build from glade designer it shows following message.


> Error running glade-- to generate the C++ source code.
Check that you have glade-- installed and that it is in your PATH.
Then try running 'glade-- <project_file.glade>' in a terminal.


While i am able to create and Run a C project i'm not able to run a c++ project. also when i am trying it through anjuta i am getting only the main.cc file in the source directory.

I could not find anyother file as i am not able to design and Build through Glade first.

I am new to Linux Please Help

Thanks in advance

---

### Post by Engnome on 2006-05-30
I made a thread about it yesterday here: [http://ubuntuforums.org/showthread.php?t=183768](http://ubuntuforums.org/showthread.php?t=183768) 

Long story short: The preferred way is not to generate code with glade.

---

### Post by goodfella on 2006-07-23
I had the same problem, so I installed the glademm package from synaptic and was able to generate the c++ code; however, when I try to run autogen.sh I get the following error:

**Error**: You must have `glib' installed.
You can get it from: [ftp://ftp.gtk.org/pub/gtk](ftp://ftp.gtk.org/pub/gtk)

Hopefully this helps you at least build the c++ source and you don't have the same problem I do.

---

