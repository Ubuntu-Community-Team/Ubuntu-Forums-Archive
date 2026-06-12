---
title: "app development"
date: 2008-03-04
forum: Packaging and Compiling Programs
---

### Post by monoufo on 2008-03-04
Hey guys, I'm new at this.  I can't find any guides.  How do I release an application?  

I don't have anything good yet, I only started learning c++ the other day. I have a lot to learn along the way.  I would like some guides now though.  I am using Code Blocks to compile, but manually using g++ also works.  But how do I make a Makefile so that it is easy to compile without code blocks? How do I make a deb file?  How do I license it?

thank you.

---

### Post by irrdev on 2008-03-04
I use CodeBlocks myself, and I find that it is easier to simply use CodeBlocks projects to compile my programs. Nevertheless, if you wish to redistribute your source code, makefiles are probably the better option. A simple beginner tutorial can be [found here]("http://mrbook.org/tutorials/make/"). 
For creating deb files, [this tutorial]("http://www.linuxdevices.com/articles/AT8047723203.html") is quite good, although it doesn't cover including install/deinstall scripts. When it comes to licensing your application, you have many options. Assuming that you choose to go open-source, I would recommend either the GPL or the zlib license. The GPL asserts your rights to the software, and mandates that any changes made to the source code be released to the community. The zlib license is the complete opposite, allowing anybody to modify and sell the source code without notice. You can find a good comparison of open source licenses [here]("http://developer.kde.org/documentation/licensing/licenses_summary.html").
Hope that helps!;)

---

