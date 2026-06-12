---
title: "Visual tcl and Perl for writing programs"
date: 2005-12-02
forum: Programming Talk
---

### Post by Fermanagh on 2005-12-02
I would like to install visual tcl to be able to write GUI's for perl scripts.

I can download the visual tcl debian package from the website: [http://vtcl.sourceforge.net/](http://vtcl.sourceforge.net/)  to my desktop, but not sure how to do the install of the package into my edubuntu 5.01 environment. 

Do I simply extract the package or ....

Is there any way to have the Synaptic Package Manager do the install of the visual tcl debian package? I would prefer to have a package manager do the install rather than trying to do the install manually.

I want to setup a programming environment where I can create perl scripts that work with GUI's written in visual tcl. All of the programming would be done in the terminal window. 

I have done this in the past working in a Sun Solaris Unix environment.

It's a great way to write simple perl programs with really nice GUI's. 

Ubuntu comes with tcl/tk and perl, but it does not come with visual tcl?

How can I get visual tcl onto my edubuntu machine?

---

### Post by buddhagui on 2005-12-03
I just installed it. What a great program. All you have to do is go to the directory that you downloaded the file, type sudo dpkg -i vtcl.number.deb replace number with exact filename, and that's it. It will install. Then at the terminal type in vtcl and bingo! Enjoy!

-buddhagui
[http://chrisandjune.com](http://chrisandjune.com)

---

### Post by Fermanagh on 2005-12-04
Buddhagui

Thanks for the help. I was able to get Synaptic to intall it also by adding universal repositories. 

When the program starts in my terminal window I get the following message:

jjm@edubuntu:~$ vtcl
can't find package Tix

but for my needs, I don't think that I will need the Tix package.

Thanks again..
Fermanagh

---

