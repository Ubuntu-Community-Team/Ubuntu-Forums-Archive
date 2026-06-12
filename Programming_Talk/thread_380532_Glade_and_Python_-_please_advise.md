---
title: "Glade and Python - please advise"
date: 2007-03-09
forum: Programming Talk
---

### Post by mrwooster on 2007-03-09
Hi,

I want to start creating some small apps for linux systems.

I will be using the GTK+ libraries and am looking at using the PERL bindings.

Therefore:

I have installed Glade, and all the Perl stuff and can create a simple app to pop up a window.

I have managed to get glade working so that my Perl app can read in the XML data from the .glade file and produce a window accordingly.

However, I am a little confused:

Would it be better to use the .glade XML files or is it possible to get a code generator for glade so that it generates the source like it does for C.

Once I have written an app, will it be portable? Or will each person have to install all the GTK-perl and glade-perl libraries before they can run the program? If so how do you get round this? Can you include all the requires files in am installation package?

Also - Is it possible to get Glade-3 on Drapper or can you only get Glade-2?

Regards

Guy

---

### Post by j_g on 2007-03-10
Version 3 of Glade doesn't produce any C code. That feature was jettisoned because the authors ostensibly felt that it would be too difficult to synchronize changes to the XML layout (XML file) with any manual changes the programmer made to the generated C code. (Of course, the way around this is to design the framework, and the tools, to tightly integrate, like NET does. But that's not the approach Linux authors take). So, your best bet is to just adopt the policy that the Glade authors have endorsed. Just ship your XML file (as a separate file) along with your program.

Anyway, yes, a person who uses your Perl program will need to have installed GTK+, libglade, and any other packages you've used. One of the ways to handle this is to make either an RPM or DEB "install package" of your program. In addition to storing all of your program files inside one archived file, this will store the names of the other packages that your software "depends upon". When the enduser installs your DEB (or RPM) file with Synaptic Package Manager, or DEBI, then that install utility will try to download and also install the dependent packages, from some "repository" of packages (which are also in RPM or DEB files).

You can, and should, get glade3 right now from Ubuntu's repository. Run Synaptic Package Manager, and you'll see it there.

Perl scripts are supposed to be portable. So, if someone's distro has available all the packages you depend upon, then the script should run on his system (unless you did something in your script that is very platform specific).

---

### Post by mrwooster on 2007-03-10
Thanks for the help, I now understand how it works - I think using DEB packages would be the way forward.

I can't seem to find Glade3 in the Package Manager, I am running Dapper - is it available or do I have to use Glade 2?

Thanks

Guy

---

### Post by j_g on 2007-03-10
In Synaptic Manager, go to the "Edit -> Search" menu item.

Type in glade-3 and you should find it.

One word of warning: Creating a Debian package is really, really convoluted. It requires a half dozen files containing an unnecessarily complex syntax. I found it much easier to create an RPM file. That involves making just one text file (ie, a .spec file), and then using the utility rpmbuild to make an RPM file. Then you can use another utility called alien to convert this RPM file to a Debian file.

For that, you have to install the following packages: alien, rpm, and debianutils.

There's an online book about making an RPM at [http://www.rpm.org/max-rpm](http://www.rpm.org/max-rpm)

You can skip a lot of the beginning chapters, and read chapter 11. That tells you what you really need to know. One caveat. On ubuntu, the rpm directories are under /usr/src/rpm (not /usr/src/redhat like the online book says).

Basically, you bundle up all your source (and XML) files into one tar file. (Use "Applications -> Accessories -> Archive Manager"). Then you copy this tar file to the /usr/src/rpm/SOURCES directory. (Note, you'll have to open a "Root terminal" window and do a cp command to copy to this directory. Or do sudo cp from a user terminal window). Now write your .spec file and copy that to /usr/src/rpm/SPECS. Cd to that SPECS directory, and issue the rpmbuild command as so (assuming the name of your spec file is "mystuff.spec").

rpmbuild -ba mystuff.spec

If all goes well, this will create your RPM file in the /usr/src/rpm/RPMS/i386 directory. CD to that directory. Assuming it has created an RPM named mystuff-0.1-1.i386.rpm, now issue the command:

alien -k mystuff-0.1-1.i386.rpm

This will create a debian package with a .deb extension. There you go.

---

### Post by j_g on 2007-03-10
Oh yeah, one other thing. Tell your endusers to install the debi package. This way, when they get your .deb file, all they need do is double-click on it and it will pop open a window to let them install your program by just clicking on the Install button. Debi will also install all the other packages that yours depends upon.

---

### Post by mrwooster on 2007-03-10
Thanks j_g, thats exactly what I needed. I still can't find glade-3, even though I am using all the repos, are you sure it is available for Dapper?

Regards

Guy

---

### Post by pmasiar on 2007-03-10
> **mrwooster said:**
> I still can't find glade-3, even though I am using all the repos, are you sure it is available for Dapper?

Synaptic shows glade2 installed and used in most systems, with Glade3 available. Maybe you need to do more research how to run Glade3 alongside Glade2.

Let me tell you (and you already know that) that what you decided to accomplish is not easy or simple. It is great learning opportunity tho :-)

---

### Post by mrwooster on 2007-03-10
> **pmasiar said:**
> 
Let me tell you (and you already know that) that what you decided to accomplish is not easy or simple. It is great learning opportunity tho :-)

I realise that it is a challange but as you say - its really about the learning opportunity. I guess I wan't to learn more about the linux system.

---

### Post by WW on 2007-03-10
> **pmasiar said:**
> Synaptic shows glade2 installed and used in most systems, with Glade3 available. Maybe you need to do more research how to run Glade3 alongside Glade2.


Glade-3 is not available in dapper, at least not in the standard ubuntu repositories, so I'm not sure what you mean when you say "...with Glade3 available."  What repositories are you using?

---

### Post by pmasiar on 2007-03-10
> **WW said:**
> Glade-3 is not available in dapper, at least not in the standard ubuntu repositories, so I'm not sure what you mean when you say "...with Glade3 available."  What repositories are you using?

All Ubuntu including multiverse, but no 3rd party. I searched for "glade" in Synaptic. Synaptic shows entries like glade-3 installable - I don't have them installed, and neither glade2.

I don't use glade at all, I just wanted to suggest OP to check how (and if) glade3 (suggested by j_g) will coexist with glade2. Glade2 seens be preferred Ubuntu version - I am not expert, but ubuntu logo is there for something.

I have nothing more to say about glade3 or 2 or creating .DEBs (only that it seems really hard to do), don't look at me for more help. :-)

---

### Post by WW on 2007-03-10
You must be using edgy or feisty. Glade-3 is not in dapper.

---

### Post by pmasiar on 2007-03-10
> **WW said:**
> You must be using edgy or feisty. Glade-3 is not in dapper.

:blush: oh absolutely you are right. Edgy is it. My bad.

---

### Post by Daverz on 2007-03-11
Hmmm, the subject says Python, but we seem to be talking Perl...

Anyway, if you do work in Python, it's worth checking out gazpacho:

[http://directory.fsf.org/Gazpacho.html](http://directory.fsf.org/Gazpacho.html)

and also this "all in one" pygtk installer for win32:

[http://aruiz.typepad.com/siliconisland/2006/12/allinone_win32_.html](http://aruiz.typepad.com/siliconisland/2006/12/allinone_win32_.html)

---

### Post by psychicdragon on 2007-03-11
I wouldn't recommend using glade-3, especially if you have any glade files you created in glade-2. It will mangle them.

Glade-3 isn't exactly stable yet, and the version in edgy is quite outdated. There are silly bugs like pixbufs in menus being sized incorrectly, and it fails to parse notebooks with widgets other than a label in the tabs sometimes.

---

