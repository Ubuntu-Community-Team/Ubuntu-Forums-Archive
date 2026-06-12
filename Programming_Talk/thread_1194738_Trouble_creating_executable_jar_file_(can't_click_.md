---
title: "Trouble creating executable jar file (can't click and run)"
date: 2009-06-23
forum: Programming Talk
---

### Post by MR.UNOWEN on 2009-06-23
Hello,

I'm trying to create an executable jar file. The good news is that it executes, but only through terminal "./editor.jar". If I double click on it, it doesn't execute. I also tested it on windows, same problem.

jar cvmfe mainClass editor.jar *


What am I doing wrong?

---

### Post by pbrockway2 on 2009-06-23
Check that the jar's manifest specifies the main class properly.

The jar command you gave looks like it should include a file to use as the manifest, but it's not doing that.  I would expect something like

jar cvmfe manifest.txt editor.jar package.MainClass *

To quote from the man page "The -e option and entrypoint are a pair  --  if  either  is present, they must both appear. The letters m, f and e must appear in the same order that manifest, jarfile, entrypoint appear"

It might pay to consult [Setting An Application's Entry Point]("http://java.sun.com/docs/books/tutorial/deployment/jar/appman.html") in Sun's online Tutorial.

edit: also note that you expect something like the following command to be effective

java -jar editor.jar

What the behaviour of double clicking is will depend ultimately on how the environment is set up.  On my desktop jar files don't run when they're double clicked, instead they open up in an archive manager.

---

### Post by geirha on 2009-06-23
Right click a .jar file, select Properties, then on the Open with tab, add a custom command "java -jar" and set it as default.

---

### Post by Chicanob12 on 2010-05-03
> **geirha said:**
> Right click a .jar file, select Properties, then on the Open with tab, add a custom command "java -jar" and set it as default.


thanks man that worked perfectly for me!!

---

