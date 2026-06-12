---
title: "What software for development should I use?"
date: 2011-10-30
forum: Programming Talk
---

### Post by alexandros81 on 2011-10-30
Hi!
I have to do a University exercise that is I have to develop code in C. The code will have to handle processes, client server processes, socket descriptors & sockets, and creating new processes using fork().

What development environment do you suggest? I would prefer something that has step by step debugging, variables watch window etc.

Thanks
 
  Alex

---

### Post by Lars Noodén on 2011-10-30
In the beginning I would recommend staying with [geany](http://www.geany.org/), [kate](http://kate-editor.org/about-kate/), or emacs.  They might be much simpler than you are asking for, but they do the job.

Later, after you're familiar with the language, and are working on large projects you can look at kdevelop, netbeans or eclipse.

---

### Post by alexandros81 on 2011-10-30
I've been using XEmacs in the past. I am a bit familiar with C language.
I've used NetBeans for java development. Should I start using Netbeans for C ?
Where do I find and install kate , geany , emacs , netbeans, kdevelop? I would like to have go with all of these.

ta

---

### Post by The Cog on 2011-10-30
Moved to Programming Talk.

You'll probably get lots of answers here, each recommending a different IDE.

---

### Post by Bachstelze on 2011-10-30
A terminal and vim.

*EDIT:* and gdb.

---

### Post by alexandros81 on 2011-10-30
What is vim? Can you give me a link?

---

### Post by Lars Noodén on 2011-10-30
> **alexandros81 said:**
> What is vim? Can you give me a link?

He's just pulling your leg.  :)  The [vim](https://en.wikipedia.org/wiki/Vim_%28text_editor%29) vs emacs [editor war](http://en.wikipedia.org/wiki/Editor_war) is a classic.

---

### Post by Bachstelze on 2011-10-30
There should be a Recurring Discussions subforum in PT. :D

---

### Post by ofnuts on 2011-10-30
> **alexandros81 said:**
> I've been using XEmacs in the past. I am a bit familiar with C language.
I've used NetBeans for java development. Should I start using Netbeans for C ?
Where do I find and install kate , geany , emacs , netbeans, kdevelop? I would like to have go with all of these.

takate and kdevelop are in your usual repository. They integrate with the KDE desktop (which is a bit more oriented towards software development than Gnome or <smirk>Unity</smirk>

---

### Post by nvteighen on 2011-10-30
> **Bachstelze said:**
> There should be a Recurring Discussions subforum in PT. :D

Which should include itself as a subforum, recursively.

---

### Post by 11jmb on 2011-10-30
> **nvteighen said:**
> Which should include itself as a subforum, recursively.

:D lol

I think it may be to your benefit to use a text editor to edit your source/make files and the command line to compile and run. IDEs can be great if you are using a lot of developer's tools such as SVN, unit testing, autotools, etc, but if you are working on a smaller project as an individual, a simple text editor that does syntax highlighting will be simple and straightforward.

just my two cents

---

### Post by alexandros81 on 2011-10-30
I have downloaded and installed NetBeans 7.0.1
I have downloaded and installed both jdk and jre. Because I want to use NetBeans to write code in C I have to configure the NetBeans IDE for C/C++/Fortran. I am using this page: [http://netbeans.org/community/releases/70/cpp-setup-instructions.html#compilers_linux](http://netbeans.org/community/releases/70/cpp-setup-instructions.html#compilers_linux)

I have downloaded Oracle Solaris Studio 12.2 and in the section 'To download and install the Oracle Solaris Studio 12.2 compilers:'  I canot understand step 6: **Edit your PATH to add the path to the Oracle Solaris Studio software before starting the NetBeans IDE**
How do I do step 6?

Oh and last but not least I try to run NetBeans by issuing the command ```
./netbeans
``` in the Terminal and nothing happens. I also double click the netbeans icon on the desktop and still no luck

Ta

---

### Post by JDShu on 2011-10-31
Whether you choose vim or emacs, I recommend using cscope with it.

---

### Post by alexandros81 on 2011-10-31
Where do I find Emacs and cscope and how do i install them?

---

### Post by Lars Noodén on 2011-10-31
> **alexandros81 said:**
> Where do I find Emacs and cscope and how do i install them?

Both are in Ubuntu's software repositories.  You can install them from the Software Center or from Synaptic, whichever you are using.

---

### Post by phlancelot on 2011-10-31
I would recommend using Eclipse, I've used this in the past with Ubuntu to do Java, C++ and Android programming.

Its a very full featured editor and is cross platform and used at a lot of academic institutions.

I think your best bet for install would be go to eclipses site and follow the guide from there as the versions in the Ubuntu repos tend to be out of date

[http://www.eclipse.org/downloads/](http://www.eclipse.org/downloads/)

I think you'd be best getting the package for C++ or the classic one which I think may include c++ tools? or at least you should be able to add on stuff once its installed

---

