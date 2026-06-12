---
title: "Looking to get to HKEY files."
date: 2008-07-21
forum: Packaging and Compiling Programs
---

### Post by Nectar on 2008-07-21
From [http://www.fsckin.com/2007/12/20/how-to-run-world-of-warcraft-wow-in-linux-using-wine/](http://www.fsckin.com/2007/12/20/how-to-run-world-of-warcraft-wow-in-linux-using-wine/)      #6.

[SIZE="1"]. Next, we create a registry key and value.
The following instructions to modify the registry are taken directly from the Ubuntu wiki page and is licensed under CC-BY-SA.

a. Find this key HKEY_CURRENT_USER\Software\Wine\
b. Highlight the wine folder in the left hand pane by clicking left on it. The icon should change to an open folder
c. Right-click on the wine folder and select [NEW] then [KEY]
d. Replace the text New Key #1 with OpenGL
e. Right-click in the right hand pane and select [NEW] then [String Value]
f. Replace New Value #1 with DisabledExtensions (Notice it&#8217;s case sensitive!)
g. Then double click anywhere on the line, a dialog box will open.
h. In the value field type GL_ARB_vertex_buffer_object

It should look like this:[/SIZE]
[http://www.fsckin.com/wp-content/uploads/2007/12/regedit.png](http://www.fsckin.com/wp-content/uploads/2007/12/regedit.png)

Every time I search for HKEY in file system, my system freezes up. I'm trying to do the things above but I'm not sure on how to get there.

---

### Post by Nectar on 2008-07-22
Still freezing whenever I try to search for this.

---

