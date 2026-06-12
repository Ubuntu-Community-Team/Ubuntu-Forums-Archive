---
title: "Where are my programs truely stored?"
date: 2008-11-26
forum: New to Ubuntu
---

### Post by icyest on 2008-11-26
I'm used to the convenience of Program Files from windows. In windows, when my computer runs into a file it's never seen before, like .gp5 I can go and select "GuitarPro" folder from the Program Files list, then select GuitarPro.exe

What is the Linux equivalent of browsing for files to select? You know that window that opens up when you download a file using firefox browser, and it says something like:

o  Open With: [Browse Button]
o  Save to Desktop:

I want to know where to that .exe file is in Linux so that I can make up new paths for when my computer runs into exotic files. "Program Files" from windows made it very easy to find where programs were installed.

How can linux compete?


(I'm  dealing with TuxGuitar by the way. It is not listed as one of the programs that my Ubuntu can open files with)

---

### Post by kostkon on 2008-11-26
> **icyest said:**
> I'm used to the convenience of Program Files from windows. In windows, when my computer runs into a file it's never seen before, like .gp5 I can go and select "GuitarPro" folder from the Program Files list, then select GuitarPro.exe

What is the Linux equivalent of browsing for files to select? You know that window that opens up when you download a file using firefox browser, and it says something like:

o  Open With: [Browse Button]
o  Save to Desktop:

I want to know where to that .exe file is in Linux so that I can make up new paths for when my computer runs into exotic files. "Program Files" from windows made it very easy to find where programs were installed.

(I'm  dealing with TuxGuitar by the way. It is not listed as one of the programs that my Ubuntu can open files with)
Program files are put in various places but most of the executables are stored in */usr/bin*

Hope that helps.
> **icyest said:**
> How can linux compete?
Compete?!

---

### Post by ndefontenay on 2008-11-26
Yep. It's not trying to compete. 

I think there's the choice to choose from a list when it's exotic.

---

### Post by gn2 on 2008-11-26
To view installed applications, you can select the Status button in Synaptic then select Installed and you will be presented with a list of all your packages.

Or in a terminal enter: ```
dpkg --get-selections > installed-software
```

this will generate a text file called installed-software in your home folder listing every package that is installed.

---

### Post by scottmac112 on 2008-11-26
Yeah. There's /bin, /usr/bin, and (these aren't used very often), /sbin, and /usr/sbin. All of the binaries are stored in those folders.

---

### Post by porchrat on 2008-11-26
And most of the configuration files are stored in /etc

---

### Post by wardrich on 2008-11-26
and if worst comes to worst, you can always use the "locate" command, and if that fails, you can always try "sudo updatedb" then locate.

---

### Post by peakshysteria on 2008-11-26
If you want to associate programs to files via Firefox you can find the program files in /usr/bin.

But often it is enough to just right click the file **--> properties --> open with** and mark the program you want associated with the filetype. If you have more than one program for that filetype you can choose witch one you want associated as default.

---

### Post by ilrudie on 2008-11-26
Also, most programs get installed into your a directory in your shell's path.  If you can run the program from a terminal (which is almost surely the case) then you can use `which <program>` to get the full path to the program.

ex:
```
>which firefox
/usr/bin/firefox

```

---

### Post by bruce89 on 2008-11-26
> **peakshysteria said:**
> If you want to associate programs to files via Firefox you can find the program files in /usr/bin.

That's more a design fault than a feature.

---

### Post by Paqman on 2008-11-26
> **peakshysteria said:**
> If you want to associate programs to files via Firefox you can find the program files in /usr/bin.

But often it is enough to just right click the filetype **--> properties --> open with** and mark the program you want associated with the filetype. If you have more than one program for that filetype you can choose witch one you want associated as default.

:lolflag:

I think you're the only person on this thread that actually *read* the OP and posted the right information.

The rest of you guys, try to read the whole post and understand what's being asked for before replying.



> **icyest said:**
> 
I want to know where to that .exe file is in Linux so that I can make up new paths for when my computer runs into exotic files.

In linux you don't need to know the full path. You can launch an app with just the name of the package, Linux is smart enough to figure the rest out.

For example: Firefox's executable is located at "/usr/bin/firefox", but to launch it you can just use "firefox".

Linux doesn't just compete, it whups Windows' butt. Having to figure out the whole path is just one of many annoying things Windows makes you do that Linux does automatically.

---

