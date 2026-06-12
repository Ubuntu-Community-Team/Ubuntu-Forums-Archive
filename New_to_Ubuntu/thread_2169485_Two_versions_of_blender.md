---
title: "Two versions of blender?"
date: 2013-08-22
forum: New to Ubuntu
---

### Post by Halpm on 2013-08-22
I am trying to run two versions of blender side by side in ubuntu 13.04. I want 2.49, as it has an import script I need that isn't available for later versions, and 2.66, as I prefer it to work in.

I have installed 2.66 from the software centre, and downloaded 2.49b from the blender site as a tarball and unzipped to home. When I try to run 2.49 nothing happens. When I run it from the terminal I get this:
"Color management: using fallback mode for management
connect failed: No such file or directory

blender quits"
And then it opens blender 2.66.

Any ideas?

---

### Post by newb85 on 2013-08-22
Installing two versions with the same name doesn't work with apt-based package management. 

Simply unzipping a into your home directory does not usually install a package.

---

### Post by Halpm on 2013-08-22
Perhaps I wasn't clear - version 2.66 is installed from software centre. Version 2.49b was downloaded as a complete tarball, and unzipped to the home folder as per instructions enclosed in tarball.

---

### Post by monkeybrain20122 on 2013-08-22
You should be able to do it. Blender doesn't need installation, untar the tarball, go into the folder and click the file blender it should start (if you make it executable, right click Properties > Permission) 

There may be a problem if the two versions share the same configuration file. Try to delete it (look for .blender or .config/blender in your home, these are hidden directories so you need to get the file manager to show them first) and click blender again and see what happens.

---

### Post by Halpm on 2013-08-22
See, that's what I thought, and I deleted the .config/blender folder, and it still doesn't work. And I've rebooted. And I've checked that it's executable. It's very confusing.

---

### Post by azmyth on 2013-08-22
Run it in a terminal window and let us know what error it gives you.

---

### Post by Halpm on 2013-08-23
"error while loading shared libraries: libjpeg.so.62: cannot open shared object file: No such file or directory"
if I run ./blender.

---

### Post by Halpm on 2013-08-23
Hang on - a bit of judicious googleing told me that the library it couldn't find was part of [COLOR=#000000][FONT=Ubuntu Mono]libjpeg62. I installed that and now it runs :) All fixed :D[/FONT][/COLOR]

---

