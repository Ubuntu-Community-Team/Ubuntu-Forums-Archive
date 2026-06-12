---
title: "What to use to build a simple tool/gui to read/modify XML file?"
date: 2008-06-17
forum: Programming Talk
---

### Post by kernelhaxor on 2008-06-17
I have a XML file (with lots of elements) and I intend to write a simple tool which can parse through it and display all the different elements and values in a readable way .. the tool also should giv me the option to update any of the values ..
the xml and the tool should live on my local machine

php webpage? (but it would require a http server) 
java swing app?
anything else?

---

### Post by siouzi on 2008-06-18
Reinvent the wheel? If not, see e.g. [xmlstarlet](http://xmlstar.sourceforge.net/) - aptitude install available. Edit: aah a gui, maybe write a frontend for xmlstarlet :)

---

### Post by pmasiar on 2008-06-18
before creating a GUI, create commandline tool which parses XML and updates portions of it. Python/ElementTree would be my choice.

---

### Post by days_of_ruin on 2008-06-18
> **pmasiar said:**
> before creating a GUI, create commandline tool which parses XML and updates portions of it. Python/ElementTree would be my choice.
+1.
Check out this thread too.[http://ubuntuforums.org/showthread.php?t=594676&highlight=parsing+xml+python]("http://ubuntuforums.org/showthread.php?t=594676&highlight=parsing+xml+python")

---

### Post by Shin_Gouki2501 on 2008-06-18
> **siouzi said:**
> Reinvent the wheel? If not, see e.g. [xmlstarlet](http://xmlstar.sourceforge.net/) - aptitude install available. Edit: aah a gui, maybe write a frontend for xmlstarlet :)


If you dont have a timelime or really need to know this i would code somehtign myself. But believe me using an existing tool can be much nicer...

---

### Post by kernelhaxor on 2008-06-19
cool stuff .. I'll checkout xmlstarlet and elementtree

Thanks for the inputs guys!

---

