---
title: "How to start executables by doubleclick"
date: 2008-09-09
forum: New to Ubuntu
---

### Post by mahy on 2008-09-09
Okay, time for a newbie question:

I downloaded Google Earth. Right-clicked it, enabled "executing as program" in Properties/Permissions, but when i double-clicked it, the following error message appears:

```
Couldn't display "/home/user/Downloads/GoogleEarthLinux.bin".

There is no application installed for this file type

```

That's an obvious nonsense.

Please don't tell me I should open the terminal and type something like "chmod +x GoogleEarthLinux.bin && ./GoogleEarthLinux.bin" I know how it can be done in CLI! I just wanted to see if Ubuntu is beginner-friendly enough to make program installation possible for people who ale scared of CLI. Well, the experiment failed. Or am I wrong and there's something i'm missing? THX for any answer

---

### Post by Titan8990 on 2008-09-09
If there is not a package for it then it needs to be compiled from source. The Ubuntu repositories contains 95% of the programs you will need and use. Search the repositories for Google Earth (seriously doubt it is there). The reason that it is not there is because it is not open source software. Companies that hide their source code do not usually get packages.

---

### Post by bobnutfield on 2008-09-09
Once it is opened from the command line, it will create an icon on your desktop that CAN be clicked to open (at least it is on my desktop.)

---

### Post by Thingymebob on 2008-09-09
> **Titan8990 said:**
> If there is not a package for it then it needs to be compiled from source. The Ubuntu repositories contains 95% of the programs you will need and use. Search the repositories for Google Earth (seriously doubt it is there). The reason that it is not there is because it is not open source software. Companies that hide their source code do not usually get packages.

Its in the Medibuntu repos

---

### Post by LowSky on 2008-09-09
add the medibuntu repos and then you can install GE very easily
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by mahy on 2008-09-09
Guys, I'm afraid none of you answered my question.

Ok, i'll repeat it: Why can't I execute a file (namely a Google Earth installation file, but also any other program) by double-clicking it? Why to I have to execute it from the terminal by typing ./filename ??

---

### Post by bobnutfield on 2008-09-09
Any package you download with a .deb extension will automatically install when double clicked using the package manager.  If you were using Fedora, SuSe or Red Hat, then a double click on a .rpm file would automatically install with the Red Hat Package Manager.  Point is, if you are comparing this to the automatic installation by Windows of a .exe file, then I would point out that Windows also would not automatically install a .bin file.

---

