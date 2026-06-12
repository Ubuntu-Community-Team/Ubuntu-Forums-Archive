---
title: "Ubuntu freezes after clicking on &quot;Try or install Ubuntu&quot;"
date: 2022-11-29
forum: New to Ubuntu
---

### Post by adam-966 on 2022-11-29
[COLOR=#000000][FONT=Tahoma]Couple of months ago I got interested in linux operating system (I am a windows user and beginner android dev) and started trying it in the virtualbox. I have tried several linux distros and liked Pop os and Ubuntu.[/FONT][/COLOR]

[COLOR=#000000][FONT=Tahoma]After several weeks of trying these distros, I decided to fully switch to Pop os alongside Windows, and here the nightmare began. I made a bootable USB stick and tried to install Pop but was unsuccessful, the problem was that after clicking on "Try or install Pop" my laptop freezes with black screen, waiting for a long time doesn't help.[/FONT][/COLOR]

[COLOR=#000000][FONT=Tahoma]Then, I made a bootable USB stick with Ubuntu in it. Again, after clicking on "try or install Ubuntu" laptop freezes. [/FONT][/COLOR]

[COLOR=#000000][FONT=Tahoma]I have tried to install Ubuntu alongside Windows with safe graphics and I was successful but after finishing the installation I cannot log into the Ubuntu, the same issue, it freezes. The only way that I can get into the system is through recovery mode.[/FONT][/COLOR]

[COLOR=#000000][FONT=Tahoma]I am sure that the problem is related to my graphics card which is AMD Radeon(tm) vega VII. Because when I type "lshw -c video" command, the result is "*-display UNCLAIMED".

[/FONT][/COLOR]I have tried update all the drivers including propriatary ones, no result.

[COLOR=#000000][FONT=Tahoma]I have tried to download and install driver package for AMD Graphics from the official website, but I am getting the following error:[/FONT][/COLOR]

[COLOR=#000000][FONT=Tahoma]The following packages have unmet dependencies:[/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma]rocm-llvm: [/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma]Depends: python but it is not installable [/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma]Depends: libstdc++-5-dev but it is not installable or[/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma]libstdc++-7-dev but it is not installable or[/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma]Depends: libstdc-5-dev but it is not installable or[/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma]libstdc-7-dev but it is not installable[/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma]E: Unable to correct problems l, you have held broken packages.[/FONT][/COLOR]

[COLOR=#000000][FONT=Tahoma]I got stuck here and cannot proceed further, I would highly appreciate if you help resolve this issue.
[/FONT][/COLOR]

---

### Post by TenPlus1 on 2022-11-29
List the specs of your system, also have you tried the other ubuntu flavours to see if any of those work (Xubuntu, Lubuntu, Kubuntu) ?

---

### Post by yancek on 2022-11-29
Take a look at the last post in the link below.  Have you tried that process to correct the 'broken packages' error?  Make notes of the steps you take and results.  That is a fairly common problem and if the link below doesn't help, try an online search using that error.

[https://askubuntu.com/questions/1412571/cannot-install-packages-due-the-unmet-dependencies](https://askubuntu.com/questions/1412571/cannot-install-packages-due-the-unmet-dependencies)

When you start a thread here, it is always useful to post the release version you are using, the most recent LTS is 22.04, is that what you have?

---

### Post by adam-966 on 2022-11-29
System specs are:
Laptop: MSI Modern 14 B4MW
Processor: AMD Ryzen 7 4700U with Radeon Graphics 2.0 GHz
RAM: 16 GB

I haven't tried other Ubuntu flavors, but I have tried other distros like Pop os with and without Nvidia graphics, Linux Mint, Fedora. Should I try other Ubuntu flavors?

---

