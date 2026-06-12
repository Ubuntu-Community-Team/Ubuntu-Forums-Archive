---
title: "How do I use wine to install a program?"
date: 2012-07-08
forum: New to Ubuntu
---

### Post by bonedriven on 2012-07-08
Hi forum,

I'm using ubuntu 12.04. I have a portable program Lingoes (dictionary software under windows). 

I have the portable program in the ubuntu system now, but I don't know how to use wine (Playonlinux) to run it. I have tried clicking here and there but don't have a clue what's it all about and failed to run the program.

Thank you very much.

---

### Post by krustenBrot on 2012-07-08
Have you taken a look at [Lingoes on the wine hq website]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=6328")?
It says there that except for versions 2.7.1 and 2.8.1 it is garbage.

Using wine you can run programs either by clicking on the executable (*.exe) or throught he terminal by typing [B]wine (-> executable goes here).
[/B]Play on Linux provides an interface for diffferent application and sets the wine options accordingly.

---

### Post by bonedriven on 2012-07-08
> **krustenBrot said:**
> Have you taken a look at [Lingoes on the wine hq website]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=6328")?
It says there that except for versions 2.7.1 and 2.8.1 it is garbage.

Using wine you can run programs either by clicking on the executable (*.exe) or throught he terminal by typing [B]wine (-> executable goes here).
[/B]Play on Linux provides an interface for diffferent application and sets the wine options accordingly.
Hi krustenBrot,

Thank you for the reply and the link. I double clicked the lingoes.exe or right click "open with wine program loader, but nothing happened.

---

### Post by z3nhakr on 2012-07-08
> **bonedriven said:**
> Hi krustenBrot,

Thank you for the reply and the link. I double clicked the lingoes.exe or right click "open with wine program loader, but nothing happened.

do you get an error message? surely something happens when you try running it via the command line

---

### Post by krustenBrot on 2012-07-08
> **z3nhakr said:**
> do you get an error message? surely something happens when you try running it via the command line

To open it up with the command line open a terminal by clicking on the **Dash icon** in the left side panel (The one on top) or press **ctrl + alt + t**
in terminal type:

```
cd  /(your directory where your executable lies) for example /home/krustenbrot/Games/

then 

```
```
wine yourexecutable.exe
```

and paste the output here.

Do you know which version of Lingoes you are using?
Does it work according to WineHQ?

---

### Post by bonedriven on 2012-07-08
> **z3nhakr said:**
> do you get an error message? surely something happens when you try running it via the command line

Via command line it says "can't find C:\\windows\\system32\\lingoes.exe", which is no suprise to me. How do I put it under system32? Do I have a system32 folder in linux?

And I also don't know where is C in my linux system.

---

### Post by bonedriven on 2012-07-08
> **krustenBrot said:**
> To open it up with the command line open a terminal by clicking on the **Dash icon** in the left side panel (The one on top) or press **ctrl + alt + t**
in terminal type:

```
cd  /(your directory where your executable lies) for example /home/krustenbrot/Games/

then 

```
```
wine yourexecutable.exe
```

and paste the output here.

Do you know which version of Lingoes you are using?
Does it work according to WineHQ?
Lingoes 2.8.1
I installed playonlinux from software centre. Do I need to install wine and other stuff too?
err:module:import_dll Library MFC42u.DLL (which is needed by L"Z:\\home\\jacques\\Documents\\Lingoes\\LGui64u.dll") not found
err:module:import_dll Library LGui64u.dll (which is needed by L"Z:\\home\\jacques\\Documents\\Lingoes\\Lingoes.exe") not found
err:module:import_dll Library MFC42u.DLL (which is needed by L"Z:\\home\\jacques\\Documents\\Lingoes\\Lingoes.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\home\\jacques\\Documents\\Lingoes\\Lingoes.exe" failed, status c0000135

---

### Post by mastablasta on 2012-07-08
play on linux is a fornt end fo rwine. you migh tneed winetrick which i hitnk install soem additionaly DLL libraries.

also another option to install via terminal is to type in wine ad a space and then clik drag and drop the .exe file form nautilus to it.

---

### Post by bonedriven on 2012-07-08
> **mastablasta said:**
> play on linux is a fornt end fo rwine. you migh tneed winetrick which i hitnk install soem additionaly DLL libraries.

also another option to install via terminal is to type in wine ad a space and then clik drag and drop the .exe file form nautilus to it.

Hi, i find that winetrick is already installed. Thank you for the trick to use wine. But how do I add additional dll libraries?

---

### Post by krustenBrot on 2012-07-08
> **bonedriven said:**
> Lingoes 2.8.1
I installed playonlinux from software centre. Do I need to install wine and other stuff too?
err:module:import_dll Library MFC42u.DLL (which is needed by L"Z:\\home\\jacques\\Documents\\Lingoes\\LGui64u.dll") not found
err:module:import_dll Library LGui64u.dll (which is needed by L"Z:\\home\\jacques\\Documents\\Lingoes\\Lingoes.exe") not found
err:module:import_dll Library MFC42u.DLL (which is needed by L"Z:\\home\\jacques\\Documents\\Lingoes\\Lingoes.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\home\\jacques\\Documents\\Lingoes\\Lingoes.exe" failed, status c0000135

For the MCF42 dll error install mfc42 through winetricks described [here]("http://machine-cycle.blogspot.de/2009/10/wine-and-missing-mfc42dll.html") 

I don't know about the LGui64u.dll see if it works after the winetricks thing. Did you install Lingoes through PlayonLinux?

---

### Post by oldos2er on 2012-07-08
> **bonedriven said:**
> And I also don't know where is C in my linux system.

That would be /home/user/.wine/drive_c/ but as krustenBrot suggested, an app rated as 'garbage' won't work under wine. Might I suggest you look for a Linux dictionary app instead?

---

### Post by bonedriven on 2012-07-08
> **krustenBrot said:**
> For the MCF42 dll error install mfc42 through winetricks described [here]("http://machine-cycle.blogspot.de/2009/10/wine-and-missing-mfc42dll.html") 

I don't know about the LGui64u.dll see if it works after the winetricks thing. Did you install Lingoes through PlayonLinux?

Later I installed mfc42 package in the library. I don't know how to install Lingoes through Playonlinux. That's the problem. I tired to follow the wizard but couldn't understand it at all.

> **oldos2er said:**
> That would be /home/user/.wine/drive_c/ but as krustenBrot suggested, an app rated as 'garbage' won't work under wine. Might I suggest you look for a Linux dictionary app instead?
Version 2.8.1 is not garbage rated. It's silver.
Alternative is goldendict I guess? I couldn't find its dictionaries at all. It looks like a dead project. But that's another story.

I always heard how easy wine it is to use to run windows program. They even run Starcraft 2 there. How come I can't even run a dictionary program normally?

---

### Post by oldos2er on 2012-07-08
I would have thought most Windows programs *don't* work on wine, but I'm about as far from being a wine expert as it's possible to be.

I have Goldendict installed, but it seems to be buggy to the point of being unusable on 12.04. There's also stardict, but I have no experience with it. 

Check this old thread, [http://ubuntuforums.org/showthread.php?t=982326](http://ubuntuforums.org/showthread.php?t=982326)
Maybe there's something there that would help?

---

### Post by bonedriven on 2012-07-08
> **oldos2er said:**
> I would have thought most Windows programs *don't* work on wine, but I'm about as far from being a wine expert as it's possible to be.

I have Goldendict installed, but it seems to be buggy to the point of being unusable on 12.04. There's also stardict, but I have no experience with it. 

Check this old thread, [http://ubuntuforums.org/showthread.php?t=982326](http://ubuntuforums.org/showthread.php?t=982326)
Maybe there's something there that would help?

Thank you oldos2er.
Since Lingoes is listed in wine's webpage: [http://appdb.winehq.org/objectManager.php?sClass=application&iId=6328](http://appdb.winehq.org/objectManager.php?sClass=application&iId=6328)

I hope somebody can guide me through how to install it.

---

### Post by Cheesemill on 2012-07-08
Have you installed Internet Explorer 6 yet?
```
winetricks ie6
```

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=23256](http://appdb.winehq.org/objectManager.php?sClass=version&iId=23256)

---

### Post by bonedriven on 2012-07-08
> **Cheesemill said:**
> Have you installed Internet Explorer 6 yet?
```
winetricks ie6
```

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=23256](http://appdb.winehq.org/objectManager.php?sClass=version&iId=23256)
My version is 2.8.1 so I installed vcrun6
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=25579](http://appdb.winehq.org/objectManager.php?sClass=version&iId=25579)

Now I am able to run the program. The only problem now is the Asian characters can't be displayed normally. I have installed "all fonts" with winetricks though.

---

