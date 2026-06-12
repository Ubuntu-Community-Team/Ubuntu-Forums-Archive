---
title: "Building Monodevelop fails!!"
date: 2008-11-13
forum: Packaging and Compiling Programs
---

### Post by lakersforce on 2008-11-13
I have compiled all source code, in the order suggested [here]("http://monodevelop.com/Download_-_Unstable").

When I compile Monodevelop (1.9) I get this error:

> 
[COLOR="Red"]**./MonoDevelop.Components/GladeWidgetExtract.cs(79,39): error CS0030: Cannot convert type `Gtk.Widget' to `Gtk.Window'**[/COLOR]




EDIT: If I go into the source and change "Windows" to "Widget", I still get an error:

> 
[COLOR="Red"]**./MonoDevelop.Components/GladeWidgetExtract.cs(79,39): error CS0030: Cannot convert type `Gtk.Widget' to `Gtk.Widget'**[/COLOR]


---

### Post by iklein on 2008-11-30
So, did you solve the problem?
I got the same. And I've no idea.

---

### Post by lakersforce on 2008-12-02
No. I thought about sending a mail to the author (his e-mail is at the top of the source-file) but I never got to it. Instead I sat up a Windows XP install and installed VS2008.

---

### Post by iklein on 2008-12-02
Nice decision ;)

Thanks.

---

### Post by iklein on 2008-12-03
So, if you still need in.
There are some monodevelop deb-packages (wasn't try yet, i hope they'll run in Interpid):

monodevelop 2.0 Alpha 1 - [http://mirrors.dotsrc.org/getdeb/ubuntu/hardy/mo/monodevelop_1.9-1~getdeb1_all.deb](http://mirrors.dotsrc.org/getdeb/ubuntu/hardy/mo/monodevelop_1.9-1~getdeb1_all.deb)

monodevelop-nunit - [http://neacm.fe.up.pt/pub/getdeb/ubuntu/hardy/mo/monodevelop-nunit_1.9-1~getdeb1_all.deb](http://neacm.fe.up.pt/pub/getdeb/ubuntu/hardy/mo/monodevelop-nunit_1.9-1~getdeb1_all.deb)

monodevelop-versioncontrol - [http://cesium.di.uminho.pt/pub/getdeb/ubuntu/hardy/mo/monodevelop-versioncontrol_1.9-1~getdeb1_all.deb](http://cesium.di.uminho.pt/pub/getdeb/ubuntu/hardy/mo/monodevelop-versioncontrol_1.9-1~getdeb1_all.deb)



And the source is [http://www.getdeb.net/app/MonoDevelop](http://www.getdeb.net/app/MonoDevelop)

---

### Post by schmendrick on 2008-12-15
thanks for the link!

(the first one) works very nice on hardy! 
do you also happen to know where i can find a package for the debugger add-in? unfortunately i couldn't find any and when i try to build it myself it fails ....

---

### Post by ahitchman on 2009-01-15
I hit this problem. 

Getting [http://ftp.novell.com/pub/mono/sources/gtk-sharp212/gtk-sharp-2.12.7.tar.bz2](http://ftp.novell.com/pub/mono/sources/gtk-sharp212/gtk-sharp-2.12.7.tar.bz2) fixed it. I also needed [http://ftp.novell.com/pub/mono/sources/gnome-sharp220/gnome-sharp-2.20.1.tar.bz2](http://ftp.novell.com/pub/mono/sources/gnome-sharp220/gnome-sharp-2.20.1.tar.bz2).

I've managed to make and install, but running fails with missing Addins. Installing [http://ftp.novell.com/pub/mono/sources/mono-addins/mono-addins-0.4.zip](http://ftp.novell.com/pub/mono/sources/mono-addins/mono-addins-0.4.zip) got MD running.

---

