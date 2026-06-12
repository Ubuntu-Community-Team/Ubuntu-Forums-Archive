---
title: "Distributing program with shared libraries"
date: 2011-10-02
forum: Packaging and Compiling Programs
---

### Post by CrystalMV on 2011-10-02
I'm not sure if I'm writing in the right section.
I use SDL library in my programs and I want to make them easy for users to install. In my opinion, it would be easiest to simply click on the archive file and extract it. The question is, can .so file be included in the archive in the way that program will load it?

---

### Post by dodle on 2011-10-02
How are you packaging your program? A regular archive (tar.gz, zip), or a DEB package? I'm not sure if .so libraries are like .dll for Windows where you can simply place the .dll in the same folder as the executable. 

My recommendation is to just notify the users to install SDL from their package manager. A purpose of shared libraries is to save disk space and download bandwidth by allowing multiple executables utilize the same files. If the user already has SDL installed then there is no need for the extra files packaged with the program. 

If you are using a regular archive (.zip, tar.gz) I would place a README file in the top directory that specifies the need for SDL to be installed for the program to work. If you are using a DEB you need to list SDL in the dependencies so it will be installed when your program is.

If you're not familiar with DEB packaging you can try one of these tools:
[Debreate](http://debreate.sf.net)
[Packin](http://sourceforge.net/projects/packin)
[Deb Creator](http://debcreator.cmsoft.net)
[Ubucompilator](http://code.google.com/p/ubucompilator)
[DebianPackageMaker](http://code.google.com/p/debianpackagemaker)

Note: Use Debreate, I made it :D

---

### Post by CrystalMV on 2011-10-03
OK, thanks for the answer and information about .deb files. I could use them, but the first thing I want to try is a regular archive. I downloaded Blender and it has lib folder near the executable file. That lib folder contains .so files. So does that mean the library will be loaded from the lib folder (if available) which is in the same folder where executable file is? Because SDL takes only half a MB and is the only library which I'm going to include, that would be very useful.

---

