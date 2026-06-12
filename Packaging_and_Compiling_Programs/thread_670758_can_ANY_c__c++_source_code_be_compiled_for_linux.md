---
title: "can ANY c / c++ source code be compiled for linux?"
date: 2008-01-17
forum: Packaging and Compiling Programs
---

### Post by Ralphie on 2008-01-17
This may or may not be a really dumb question, but I was just wondering if you have some C++ source code can it be compiled for use in any type of operating system without any change to the code?

the reason why I ask:
I need a program called VTFlib, for editing Valve Texture Files (half life 2 files).
The program is only compiled for windows, but they provide the source code here:
[http://nemesis.thewavelength.net/files/files/vtflib126.zip](http://nemesis.thewavelength.net/files/files/vtflib126.zip)

is it possible for me to compile this code for ubuntu?

Thank you for any help, and sorry if this is really basic and stupid. I have no clue about how code works

---

### Post by kostkon on 2008-01-17
I would recommend you to first try the easy solution: Check if you can run the program using Wine.

---

### Post by Ralphie on 2008-01-18
oops i should have mentioned that i have tried, and it doesnt work because it requires the ".net 2.0 runtime"

---

### Post by pedro_orange on 2008-01-18
To answer your question in the title of the post, no.

Why? Cause Windows and Linux will use different header files during compilation. You may be lucky if your package uses only standard libraries, but that is highly unlikely.

Also - .NET Framework 2 can be installed/used on Wine -> [http://appdb.winehq.org/objectManager.php?sClass=version&iId=3754](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3754)

---

### Post by Ralphie on 2008-01-18
thank you for the reply, the coding question is something i wondered about just in general, and now i know. 

Also id like to thank you for that link, i will use it when i get home. it will be nice not having to boot into my VM for the simple things i am trying to do

---

