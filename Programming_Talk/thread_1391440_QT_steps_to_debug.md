---
title: "QT: steps to debug?"
date: 2010-01-26
forum: Programming Talk
---

### Post by gnometorule on 2010-01-26
I installed QT Creator. First thing I tried was to check basic functions with the usual "hello world" toy program. When entering and saving this, everything looks fine. But switching to debugging allows me (hoorah) to set a breakpoint (not more); and I cannot build the file. 

I read that QT Creator is just a front end for gdb of at least version 6.8., which of course I have (running 7.0). I'd have thought that installation takes care of linking the resident debugger to the application? Here are my ideas what could be wrong. Anyone using Creator kindly help.

(1) I'm saving programs under <qt folder>/docs/<filename.cpp>. Do i need to add that path someplace? I checked tools etc.

(2) Do I need another module to link gdb?

(3) ...or ?

I installed this just from web page (not synaptic/apt-get), and realize that I will make myself a pariah by that mere fact to some...Willing to install older version via synaptic of course if that is the issue. But is it? Installation looks good, just see above. 

---------------------

I have worked with Visual Studio Express (free) and gdb, and both are either easy to use, or well-documented. QT is just a horror. Debugging help tells you 'need gdb 6.8' (which I have) - and that's it. 3rd tutorial (third!!) prefaces its topic "...assumes reader is familiar with (followed by 3 rather deeper topics)" That's a bit like Don Knuth have, in his reference section, a link from "Definition, self-referential" to "Self-referential Definition", and back. Really, I find this sobering. I'm new to C++ developing, but have coded in more than a dozen languages, since the early 80s. Patterson/Hennessy, the standard on comp architecture, has a nice quote by Whitehead in chapter 1: "We measure the progress of civilizations by the amount of tasks we can execute w/o thinking about them." As much as I want to like it, working under Linux feels more and more like stone age, based on that definition. I got a quantitative Ph.D., for what that's worth, and have worked almost around the clock getting up in Linux for 2 weeks now. And i can't even get this to start; nor do i know where to look except throwing up my hands and being embarrassed and thankful about possible kindness of strangers on forums like this. People are very friendly and helpful here, but I'm used to working things out myself. Here, and often here, I just don't even know where to look and start.

Down from my soapbox. :)

---

### Post by dwhitney67 on 2010-01-26
There is no library for gdb; thus there is nothing to link with your application.

Your application, however, will need to have symbolic information included within it to be able to successfully debug it.  Symbolic information is included during the compile stage using the -g option with g++.  So make sure that your CFLAGS, or CXXFLAGS, or whatever it is that qmake defines is set appropriately.  Then you should be able to use gdb, or perhaps you may prefer, ddd.

P.S.  ddd is a GUI front-end to gdb, and other debuggers.

---

### Post by gnometorule on 2010-01-26
I think i must have rambled too much; my bad. I know how to debug with gdb and think it's a very strong program. As you say, 

gcc -g <name>
gdb -q <name>

at its most basic. I wanted to learn QT which states that it is a mere front-end for gdb in its own documentation. However, after installing it (QT), I cannot debug form within the app; nor can I build. So my guess was that the 'link' (whatever would be the proper term) to gdb was not built when QT installed itself. But what do i know.

---

### Post by Vox754 on 2010-01-26
> **gnometorule said:**
> I installed QT Creator. First thing I tried was to check basic functions with the usual "hello world" toy program...

I read that QT Creator is just a front end for gdb...

I installed this just from web page (not synaptic/apt-get), and realize that I will make myself a pariah by that mere fact to some...Willing to install older version via synaptic of course if that is the issue. But is it? Installation looks good, just see above. 

---------------------

I have worked with Visual Studio Express (free) and gdb, and both are either easy to use, or well-documented. QT is just a horror. ... 3rd tutorial (third!!) prefaces its topic "...assumes reader is familiar with (followed by 3 rather deeper topics)" That's a bit like Don Knuth have, in his reference section, a link from "Definition, self-referential" to "Self-referential Definition", and back. Really, I find this sobering. I'm new to C++ developing, but have coded in more than a dozen languages, since the early 80s. ... I got a quantitative Ph.D., for what that's worth... And i can't even get this to start...

Down from my soapbox. :)
L.O.L. I just had a good laugh at this post.

I cannot comment on this because everything would sound rather sarcastic. But don't worry, I'm sure people will be nice and actually help you.

Hang in there. You seem like a dedicated guy, so you'll figure this out eventually, and next year you'll look back at this thread and have a good laugh too.

---

### Post by not_a_phd on 2010-01-26
I installed QtCreator from the website as you did in Karmic. Colleague of mine did so in CentOS. I don't think it is a Synaptic versus Web install issue. Fact is, it takes too long for IDE updates to make it into the standard repositories. I haven't yet come across a PPA that keeps the qtCreator packages up to date. (Anyone know of one?)

When you say the app doesn't build in the debug mode, what error messages is it returning. The bottom menu allows you to view "Build Issues", and with that sub-pane open, you can view the compiler console messages. Might help diagnose the problem.

Your save path looks non-standard to me. Did you start a new Qt Console Project, and create the source file within that project? Doesn't look like you did. You might try it.

It is certainly possible to add source files outside of the project directory using this IDE, but I don't think that is what you are intending to do with a hello-world app.

Take heart. Qt is a very capable framework for setting up GUI applications. It is certainly different than MSVC++, and standard Console apps using gnu-make. But, once you get over the initial learning speed bumps, I think you will find that it will allow you to be very productive.

---

### Post by gnometorule on 2010-01-26
Here is precisely what I did (actually did another try):

(1) New project
(2) C++ source file
(3) save, this time in suggested location (just my home folder)

It's not like I get debug errors. When i switch on the left to debug; then go to the debug option on top, everything is faded out - except...

- 'toggle breakpoint', 
- 'operate by instruction', and
- i can enter the 'start debugging' MENU (first entry under 'debugging' on top)...but in the sub menu all options are not faded out EXCEPT the 'start debugging' option proper, which is again faded out.

So i can't do anything. 

However, I do notice that when i switch to 'projects' on the left, i get a 'no project' feedback - although, see above, i started this using 'new projects.' 

--------------------

P.S.:

To test, I tried opening another random type of project. Couldn't even figure out where code is there. I want to use QT to go over C++ again, this time using Stroustrup. But my C++, as of today, isn't great. So i need just the option to write simple C++ code; and wanted to use QT to get used to it for later switch for more interesting apps.

P.P.S.:

This is the link I used:

[http://qt.nokia.com/downloads/sdk-linux-x11-32bit-cpp](http://qt.nokia.com/downloads/sdk-linux-x11-32bit-cpp)

---

### Post by dwhitney67 on 2010-01-27
> **gnometorule said:**
> I want to use QT to go over C++ again, this time using Stroustrup. But my C++, as of today, isn't great. So i need just the option to write simple C++ code; and wanted to use QT to get used to it for later switch for more interesting apps.

Don't use the Qt framework for this; just stick to the basics.  Either use a terminal, or sigh, an IDE such as code::blocks or eclipse.

Qt is supposedly great for developing GUI applications, however I personally dislike it because it offers constructs that warps the C++ language through the use of macros.

---

### Post by gnometorule on 2010-01-27
Having read more about it, it seems to an extremely extended version of C++, which I don't like that much either. I guess I just stick to gcc/gdb for now, which is kinda archaic but still extremely powerful. Thanks everyone for chipping in.

---

