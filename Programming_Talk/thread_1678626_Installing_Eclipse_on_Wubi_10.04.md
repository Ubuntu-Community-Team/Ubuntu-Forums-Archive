---
title: "Installing Eclipse on Wubi 10.04"
date: 2011-01-30
forum: Programming Talk
---

### Post by snarkozard on 2011-01-30
Hey,

I know one of the standard responses to questions is "google it", but trust me, I have. Eclipse is seeming to be the most annoying program to install and have run correctly.

I've already given up getting on windows, so I've turned to my wubi install as I need this working for my computer science class this semester.

The installation instructions on the eclipse site are very straightforward, and they work just fine for getting the program installed. The issue arises when I try and use it. It loads up fine, no errors or anything seeming wrong, but it is missing its key functionality, being a Java IDE. The default action for .java programs is currently to open them in gedit. If I force them open in eclipse it looks just like plain text. I can't compile and run the package I recieved for my class, and starting a new project/file includes none of the base Java syntax in it.

So, what's up with my eclipse?

TL;dr Eclipse loads fine, but has zero functionality as a Java IDE, even though supposedly it was defined as fun.

Thanks!

---

### Post by snarkozard on 2011-02-02
Bump, because it's still frustrating my every effort.

It loads java up now, but it won't compile and run any java programs, the only option in the run menu is some Ant Build program.

Any help would be appreciated.

---

### Post by forrestcupp on 2011-02-02
I actually just installed Eclipse for Windows and got it working. It really is a pain. I wish they would make an installer instead of just unzipping it to a folder.

Which version of eclipse did you download, and what java version? I only have experience with this in Windows. I would install the latest Java JDK, not just the runtime, and install the SDK version of the latest eclipse. Make sure the Java JDK is installed first. Also, I didn't have any luck using 64-bit for any of it. I had to use 32-bit Java JDK and the 32-bit version of eclipse SDK. I couldn't get 64-bit to work at all.

Another thing, if you are having to reinstall eclipse, make sure to delete the old eclipse directory and the workspace directory that it created so you can start from scratch.

Remember, all of this is from my experience with the Windows version. After wrestling with it, it really was worth it. IMO, eclipse is a lot better than netbeans, especially for Android development.

---

### Post by Jagot on 2011-02-02
Is there any reason you couldn't use the version from the repository?

---

