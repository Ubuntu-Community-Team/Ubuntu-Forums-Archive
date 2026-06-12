---
title: "Problem with Eclipse and GWT"
date: 2010-01-31
forum: Programming Talk
---

### Post by utford on 2010-01-31
Hi all - first post, hopefully I'm putting this in the right place.  I have just upgraded to Ubuntu 9.10, and installed Eclipse via the "Ubuntu Software Center".  I also added some packages via the Synaptic Package Manager - so I have installed the following:

eclipse 3.5.1
eclipse-rcp
eclipse-platform
eclipse-platform-data
eclipse-pde
eclipse-plugin-cvs
eclipse-jdt


My problem is with trying to install the GWT plug-in.  I use the following site:

[http://dl.google.com/eclipse/plugin/3.5](http://dl.google.com/eclipse/plugin/3.5)

But get the following message once Eclipse checks all the dependencies:

Cannot complete the install because one or more required items could not be found.
  Software being installed: Google Plugin for Eclipse 3.5 1.2.0.v200912062003 (com.google.gdt.eclipse.suite.e35.feature.feature.group 1.2.0.v200912062003)
  Missing requirement: Google Plugin for Eclipse 3.5 1.2.0.v200912062003 (com.google.gdt.eclipse.suite.e35.feature.feature.group 1.2.0.v200912062003) requires 'org.eclipse.wst.css.ui 0.0.0' but it could not be found

Any help would be much appreciated.  I can get this working in Windows, but would much rather work under Linux.

Thanks.
utford

---

### Post by utford on 2010-02-01
Found my own answer in the Google Community forums.  I'll append it here in case others have the same problem.  Add the following site to the list of available sites:

[http://download.eclipse.org/releases/galileo](http://download.eclipse.org/releases/galileo)

And make sure that "Contact all available sites" is selected

---

### Post by MikeEvans on 2010-03-23
Thanks! =D>

---

