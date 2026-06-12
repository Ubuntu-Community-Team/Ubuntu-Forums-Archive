---
title: "Understanding how applications are installed in ubuntu?"
date: 2013-08-15
forum: New to Ubuntu
---

### Post by jonathanp2 on 2013-08-15
So after installing applications, where are they stored, and where are the program (the file to launch the program) usually stored? For example, if I download an application using apt-get, where do the files installed go, and in which folder do the launch file go to launch the program?

---

### Post by ibjsb4 on 2013-08-15
Not all programs come with launchers, but the one that do are located in:

/usr/share/applications

---

### Post by jonathanp2 on 2013-08-15
How about the ones that are used in Terminal Only? I have a few applications from Kali Linux that do install through synaptic s, but they are usually run through Terminal. so for the ones that might not have a launcher, where do they install?

---

### Post by ibjsb4 on 2013-08-15
Thats where [synaptic package manager]("http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+package+manager&sa=Search&cof=FORID:9") comes in handy.  It will show you all installed files.  example:

[ATTACH=CONFIG]245390[/ATTACH]

```
sudo apt-get install synaptic
```

---

### Post by jonathanp2 on 2013-08-15
Yeh I have it, I have to use it to get some Kali programs. The issue is that sometimes I have no idea where to find the launch file to run it. Does synaptic tell you what folder all the files are put into?

---

### Post by bab1 on 2013-08-15
> **jonathanp2 said:**
> How about the ones that are used in Terminal Only? I have a few applications from Kali Linux that do install through synaptic s, but they are usually run through Terminal. so for the ones that might not have a launcher, where do they install?

Usually these types of applications install under* /usr *.  But this isn't always true.  The terminal command *whereis *should find it however.  For example I have the terminal only application *iftop* installed and I can find it like this```

$ whereis iftop
iftop: /usr/sbin/iftop /usr/share/man/man8/iftop.8.gz

```...this shows the tool at /usr/sbin/

---

### Post by ibjsb4 on 2013-08-15
> **jonathanp2 said:**
> Yeh I have it, I have to use it to get some Kali programs. The issue is that sometimes I have no idea where to find the launch file to run it. Does synaptic tell you what folder all the files are put into?

You should be able to launch such programs by just entering the name of program in terminal.

You can also create a launcher with 'alacarte' (menu manager).

---

### Post by newb85 on 2013-08-16
alacarte isn't installed on a default Ubuntu system.  Also, it has gnome-panel as a dependency.  Did I miss where the OP said they aren't using Unity?

---

### Post by ibjsb4 on 2013-08-16
I thought alacarte worked in unity.  Am I wrong about that?

---

### Post by coldraven on 2013-08-16
+1 for Synaptic. Using it, you can sometimes discover documentation for a program in a place that you would not normally look.

---

### Post by 3rdalbum on 2013-08-16
> **ibjsb4 said:**
> I thought alacarte worked in unity.  Am I wrong about that?

On my 12.04 I've got "Main Menu" which I always thought was different to Alacarte. Main Menu works just fine in Unity, I use it to create Dash menu items that can be dragged to the Launcher. I've got a handy "Xkill" Launcher icon that I created in Main Menu.

---

### Post by ibjsb4 on 2013-08-16
Found this in 'NewDocs'  :D

[https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles](https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles)

---

### Post by SeijiSensei on 2013-08-16
A broader answer to the OP's question is that Ubuntu, like most mainstream distributions, conforms to the "[filesystem hierarchy standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)" which specifies the locations of files in Linux. 

Programs executable by ordinary users reside in /bin, /usr/bin, or /usr/local/bin.  The last of these is empty by default. 

Because /usr is not accessed until the system goes multi-user, programs like ls or chmod reside in /bin where they can be used even in single-user mode (what Ubuntu calls "recovery" mode).  The vast majority of programs are stored in /usr/bin.  

Linux is structured to use "shared libraries" which contain lots of common functionality used by many programs.  The libraries associated with a program reside in /lib or /usr/lib following the same logic as the division between /bin and /usr/bin.  Again most libraries are stored in the latter directory.

Programs that are used by the administrator ("root") have a special location, either in /sbin or /usr/sbin.  fdisk, for instance, is stored in /sbin, since it is a program that requires root privileges and can be run in single-user mode.  Most daemons that provide services like web and mail reside in /usr/sbin.

You can see all the files associated with a program by using the dpkg command.  For instance, "dpkg -S firefox" lists all files related to the firefox package, and any associated packages like firefox-locale-en.  Use "dpkg --help" for details.

---

### Post by oldrocker99 on 2013-08-16
In Synaptic, you can select an installed program, right-click and select Properties. On the third tab, you can see exactly where that package's files are installed. Just one of the many, many things I love about Sunaptic.

---

### Post by jonathanp2 on 2013-08-16
Thanks everyone. I will remember that command. I am using Unity, but I have the classic menu that i can use if I need it, plus I can always switch to Gnome Classic.

---

### Post by jonathanp2 on 2013-08-16
Thanks big help. I had to use that multiple times! lol.

---

### Post by oldos2er on 2013-08-16
> **oldrocker99 said:**
> In Synaptic, you can select an installed program, right-click and select Properties. On the third tab, you can see exactly where that package's files are installed. Just one of the many, many things I love about Sunaptic.

And just FYI, you can see the same thing in the terminal with ```
dpkg -L <package>
```

---

### Post by r_avital on 2013-08-16
One other thing, Jonathan,

If you know the name of the executable, but forgot where it is store, you can issue this at a terminal:

which <executable name>

For instance:

~$ which fdisk
/sbin/fdisk
~$ which gnome-tweak-tool
/usr/bin/gnome-tweak-tool

If it returns nothing, it means it is not installed, OR it is in a directory that is not covered by the which command, because they're not on the path.

for instance:

~$ which variety

returns nothing.  But:

~$ /opt/extras.ubuntu.com/variety/bin/variety

-- will execute the program "variety"

Have fun

---

### Post by oldrocker99 on 2013-08-16
oldos2er, thanks for the tip about dpkg, my other favorite package installer (I also like GDebi). This is Yet Another Example of why this forum has been my homepage since 8.04 (sadly ending its life; goodbye, old friend).

---

### Post by steamer360 on 2013-08-18
In some cases, you can find applications in ~/.local/share/applications, but there won't be many apps in there except for wine packages and chrome shortcuts

---

