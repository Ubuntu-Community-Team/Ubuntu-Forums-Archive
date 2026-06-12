---
title: "Transfferring Eclipse Projects"
date: 2009-03-08
forum: Programming Talk
---

### Post by nova47 on 2009-03-08
Does anyone know how to transfer Eclipse projects from one computer to another. (Specifically in Ganymede)

---

### Post by Gordon Bennett on 2009-03-08
Go into your Workspace directory - then package up your project's directory (into a .tar.gz for example) and then from the other machine import the project thus:

File->Import&#8230;->General->Existing Projects into Workspace

Then choose &#8216;Select archive file&#8217; and select the .tar.gz archive from the file dialog.  It will automatically select the project name for you.  Click on &#8216;Finish&#8217; and the project will be imported to the workspace.

---

### Post by nova47 on 2009-03-08
Thanks got it up and working.

---

