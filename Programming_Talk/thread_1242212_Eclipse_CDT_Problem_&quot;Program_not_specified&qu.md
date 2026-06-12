---
title: "Eclipse CDT Problem: &quot;Program not specified&quot;"
date: 2009-08-16
forum: Programming Talk
---

### Post by RolandFlagg on 2009-08-16
I just installed eclipse and am trying to use the cdt extension to program in c++. I have g++ installed, but whenever I try to run anything, at the run box it says "Program not specified" and I can't run it. Any help would be greatly appreciated.

---

### Post by Can+~ on 2009-08-16
Compile it (click the hammer) and then go back to that menu and use "Search Project" and select the executable.

Also, I recommend you to install the Eclipse of the website, as the one on the repository is pretty old.

Oh, and if you're on Galileo, you just need to compile and running it is just clicking the run button.

---

### Post by RolandFlagg on 2009-08-17
Thanks so much, but I dont see a hammer anywhere, so I'm assuming that the hammer's only on the newer version of eclipse? I tried looking for "compile" under "project" but it's not there. So now I'm downloading the new eclipse. Why doesn't eclipse just like... compile automatically?

---

### Post by RolandFlagg on 2009-08-17
Also, the eclipse from the website is a tar file, which I dont know how to install...

---

### Post by colau on 2009-08-17
> **RolandFlagg said:**
> I just installed eclipse and am trying to use the cdt extension to program in c++. I have g++ installed, but whenever I try to run anything, at the run box it says "Program not specified" and I can't run it. Any help would be greatly appreciated.
The eclipse in the ubuntu repository is very older.
Eclipse-CDT is comparatively older.
Downloading from the [eclipse]("http://www.eclipse.org/downloads/download.php?file=/technology/epp/downloads/release/galileo/R/eclipse-cpp-galileo-linux-gtk.tar.gz") site would be better.

---

### Post by colau on 2009-08-17
> **RolandFlagg said:**
> Also, the eclipse from the website is a tar file, which I dont know how to install...
Extract the .tar.gz file with archive manager.(right click the file)
Or
```

tar vzxf <filename>.tar.gz
cd eclipse
./eclipse

```

---

### Post by Can+~ on 2009-08-17
> **RolandFlagg said:**
> Also, the eclipse from the website is a tar file, which I dont know how to install...

There's nothing special to it, just open the .tar.gz, throw it on a folder and run "eclipse".

In older versions of eclipse-cdt it would automatically compile when saving.

---

### Post by lboliveira on 2009-09-06
Hi there!

Same problem here. I click "Search Project..." and I olny see the 32bit binaries, the 64bit exists but the eclipse can't find them.

Can somebody help me?

---

### Post by jakehockey10 on 2010-03-08
I am having the same issue as presented at the beginning of this thread, but unfortunately all the suggested fixes are not working for me.  I have tried building my project which does not seem to work.  When I try to make a run configuration, I can select my project, but when I want to select a C/C++ Application by searching the project, no binaries are listed.  Up at the top of the window, the message, "Program not specified" is displayed.  Can someone help me?

---

### Post by SantoshLinux on 2010-11-24
> **jakehockey10 said:**
> I am having the same issue as presented at the beginning of this thread, but unfortunately all the suggested fixes are not working for me.  I have tried building my project which does not seem to work.  When I try to make a run configuration, I can select my project, but when I want to select a C/C++ Application by searching the project, no binaries are listed.  Up at the top of the window, the message, "Program not specified" is displayed.  Can someone help me?

Hi
I too had this problem, it was due to the g++ program missing from the system, hence eclipse could not generate any binaries. 

Go to System --> Administration --> "Synaptic Package Manager" --> "search for g++ and install it" 

Build your program again in eclipse and happy debugging :)

---

