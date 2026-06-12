---
title: "Help, I need a guide to the Basics"
date: 2010-01-21
forum: Packaging and Compiling Programs
---

### Post by Telescope_Nerd on 2010-01-21
I am currently developing my first complete software package. It contains three parts: a Java bit (gui) a c++ bit (does some maths) and a python bit (produces nice graphs).

It all runs fine but I have literally no idea how to package this for Linux. On windows I can create three .exe's for each part and then zip them up in self extracting installer, voila.

I have been googling around and reading about configure, make .deb etc but I am finding the learning curve very steep. Is there a simple guide out there for a dummy like me that can explain the basics to me so I can package this up?

---

### Post by SevenMachines on 2010-01-21
hi there, there are probably a few different sources i'd recommend to learn about packaging

1. [The Ubuntu Packaging Guide ]("https://wiki.ubuntu.com/PackagingGuide/Complete")
I'd probably say this is the best place to start, it's really good! The right amount of detail explained with a good deal of clarity

2. [The Debian New Maintainers Guide]("http://www.debian.org/doc/maint-guide/")
Much more comprehensive, a good read but also a good reference when you're looking for a specific explanation of something

3. Source Packages
With something in the region of 30,000 packages in ubuntu, if you want to package something theres more than likely going to be similar packages already in the repository. If you can find some then why not look at what others with similar programs have done,
$apt-get source someprogram
then rifle through their packaging, see if it suits your needs, and if so, use it as the basis for your own package

4. [Ubuntu Developer Week]("https://wiki.ubuntu.com/UbuntuDeveloperWeek/")
Why not learn from the experts! The next one starts next week (25th January), there will be classes to help get started with packaging (and lots of other things)
Previous developer weeks are archived so you can try them out when you have free time [here ]("https://wiki.ubuntu.com/UbuntuDeveloperWeek/Previous")

---

### Post by Telescope_Nerd on 2010-01-22
Wow, that's a good reply. I have got stuck right into this and already produced my first .deb. Thanks!

---

### Post by zubin71 on 2010-04-03
also there are sessions which are held on the IRC channel #ubuntu-classroom ; these classes rock!

sessions on (python)packaging are taken regularly! you might wanna try attending them; you also get to ask your doubts LIVE. so it helps a lot.

---

