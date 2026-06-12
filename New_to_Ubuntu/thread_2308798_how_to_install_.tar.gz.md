---
title: "how to install .tar.gz"
date: 2016-01-05
forum: New to Ubuntu
---

### Post by Qbi_Wan on 2016-01-05
I know the theory, but it doesn't work. That's the main problems:
./configure - terminal reads it as directory, therefor informs there are no such
Makefile (or so called) can't find

I try to install PolycodeLinux_0.8.4.tar.gz
PLS help

---

### Post by Herdo on 2016-01-05
.tar.gz files are just compressed files like .zip, 7zip, rar, etc.  You first need to extract the .tar.gz which you can do using the GUI and your mouse so try that first just to get use to the process.  Do this on your desktop, it will help simplify things.  Then check the unpacked package for a README or Installation Instructions file (or something similar). 

It will tell you exactly what to do.

The instructions will probably want you to "cd" into the directory, so in this case: 

```
/home/userName/Desktop/extractedFolder
```

Then finish the installation according to the instructions.

---

### Post by Qbi_Wan on 2016-01-05
1. thing did several times, 2. thing there is no any README nor INSTALL txt. file.  I saw it on YT, but I cant find it

---

### Post by Herdo on 2016-01-05
> **Qbi_Wan said:**
> 1. thing did several times, 2. thing there is no any README nor INSTALL txt. file.  I saw it on YT, but I cant find it


I just downloaded Polycode 0.8.4.zip source code from the Polycode website.  There is definitely a README, which instructs the user to open BUILD.md for full install instructions.


[http://polycode.org/download/](http://polycode.org/download/)

---

### Post by buzzingrobot on 2016-01-05
One of the most important reasons its best to get our software from trusted sources like Canonical's Ubuntu repositories is that we can be confident that someone is responsible for that software. We lose that confidence when we download from unknown sources. 

You are at the mercy of whoever put that tar archive on the net.  If it was expanded correctly, there will be a new directory, probably called "PolyCodeLinux", containing the extracted files.  Tar archives are most often used to distribute source files. It's traditional to include at least the standard boilerplate makefile and other info needed to compile the source.  But, that depends on the person who made the archive. They can put anything they want in one.

I've found more than a few tar archives with no makefile or other info on how to build the things, and plenty with incorrect info, and a lot that simply would not compile.

Unless you are a qualified software developer with the time to examine and audit the source files, or trust the source of a tar archive, how will you know if what's inside the archive is safe and trustworthy?

---

### Post by Qbi_Wan on 2016-01-05
Herdo => I really appreciate Your help & fast replies, but I don't have README [IMG]http://s29.postimg.org/s43ezkwef/Zrzut_ekranu_z_2016_01_05_21_52_32.png[/IMG]
[COLOR=#000000]buzzingrobot[/COLOR] => Of course if there is any similar program at [COLOR=#000000]Canonical's Ubuntu repository I'd be more than glad to use it, but I couldn't find it. Moreover, machine that holds Ubuntu is of not much matter to me so I don't care :P[/COLOR]

---

### Post by mastablasta on 2016-01-06
how about instructions here: [https://github.com/ivansafrin/Polycode/blob/master/BUILD.md](https://github.com/ivansafrin/Polycode/blob/master/BUILD.md)

---

### Post by leunam12 on 2016-01-06
If you extracted correctly all you have to do is go to IDE folder and doubleclick "Polycode". Nothing to compile and/or install.

---

### Post by buzzingrobot on 2016-01-06
The source code ZIP contains a README that refers to build.md.  The 32-bit tar archive that contains the executable system (no 64-bit version offered) has a DOC directory but I couldn't find a README file or anything similar. I don't see any setup scripts that would set it up appropriately on any Linux system.

---

### Post by kevdog on 2016-01-06
Usually here is the process for building:
(assuming you have the build-essential library installed)
tar -zxvf <tar.gz file>

Change into the directory where you just extracted:
(If there is no config file - try running ./make-config)
./configure
make
sudo make install

There are other ways, however that's the basic jist.  I don't know what kind of file you have in your directory.

---

### Post by Qbi_Wan on 2016-01-09
[COLOR=#DD4814]
[/COLOR]
**mastablasta**[COLOR=#DD4814][COLOR=#DD4814][COLOR=#000000] => I tried to follow instructions from your link, but i stuck on applying par2 file on PyPar2k - I don't know what it is.[/COLOR][/COLOR][COLOR=#000000]
[/COLOR][COLOR=#000000][URL="http://ubuntuforums.org/member.php?u=1449887"]
[/URL][/COLOR][/COLOR]**leunam12** [COLOR=#DD4814][COLOR=#000000]=> when I did as you said, blank txt file appeared:

[/COLOR][/COLOR][IMG]http://s10.postimg.org/5hflh1e55/wrong_koding.png[/IMG]
"nieprawid&#322;owe kodowanie" is something like wrong/incorrect coding

**kevdog** => when I typed that, console interprated it as folder so "couldn't find ./configure file nor folder", so make can't find Makefile

---

### Post by kevdog on 2016-01-09
So from your screenpost it doesn't look like you have to compile anything.  Polycode is listed as a program.  Can you post:

ls -la 

from within the directory where you unzipped everything.

---

### Post by Qbi_Wan on 2016-01-09
[IMG]http://s28.postimg.org/zdw0ph5zx/lsla_IDE.png[/IMG][IMG]http://s28.postimg.org/9h2ccv2cd/lsla_Fw.png[/IMG]

---

### Post by kevdog on 2016-01-09
So can you just within the directory (The first directory you listed) type

./Polycode

---

### Post by leunam12 on 2016-01-09
You double-clicked the Polycode file in the IDE directory and a blank text file appeared??? That's odd! I would download it again. But try the suggestion from kevdog first.

---

### Post by Qbi_Wan on 2016-01-11
kevdog => :~/Pobrane/PolycodeLinux_0.8.4/IDE$ ./Polycode
bash: ./Polycode: cannot execute binary file: [I]Incorrect executable file format [B&#322;&#281;dny format pliku wykonywalnego]

[/I]
[COLOR=#000000]leunam12 => did it 1 minute ago. Same thing :( Is it possible that my [/COLOR][COLOR=#000000]build-essential library is broken somehow?[/COLOR]

---

### Post by leunam12 on 2016-01-11
The file appears to be executable already but I would navigate to the IDE folder and try ```
chmod +x Polycode
./Polycode
```

---

### Post by Edward_Fish on 2016-01-11
Build instructions are available on GitHub.
[https://github.com/ivansafrin/Polycode/blob/master/BUILD.md](https://github.com/ivansafrin/Polycode/blob/master/BUILD.md)

---

### Post by Qbi_Wan on 2016-01-11
[[COLOR=#000000]leunam12[/COLOR]]("http://ubuntuforums.org/member.php?u=1449887")[COLOR=#000000] => nothing happened :( what command was that anyway?
[/COLOR][[COLOR=#000000]Edward_Fish[/COLOR]]("http://ubuntuforums.org/member.php?u=2016404")[COLOR=#000000]  => I know, but i'm stuck with installing that CMake [/COLOR][COLOR=#000000]on applying par2 file on PyPar2k - I don't know what it is.[/COLOR]

---

### Post by kevdog on 2016-01-13
I just downloaded the Polycode tarball and extracted it.  

From the terminal I entered the IDE directory and typed
./Polycode

WIndow opened and the program seemed to work as I would expect (DISCLAIMER:  I've never used this program before). Possibly you have a bad download

---

### Post by Qbi_Wan on 2016-01-15
But I downloaded it several times :( All right from original website... You have that CMake?

---

### Post by kevdog on 2016-01-16
I have no idea why yours isn't working.  I didn't need to compile anything.  Unsure why.

---

### Post by Edward_Fish on 2016-01-19
I downloaded it, extracted it with tar -xaf Polycode..... and CDed to the IDE directory and ran ./Polycode
[ATTACH=CONFIG]266830[/ATTACH]
And this happened
[ATTACH=CONFIG]266829[/ATTACH]
It appears to be working.

---

### Post by Qbi_Wan on 2016-01-20
1. I can't see your screens
2. My brother have the same Ubuntu (from the same CD) & same problem
3. Lets close this thread-to-nowhere.
Thanks for support to you all :)

Edit: Works. Check here:
[http://polycode.org/community/115-help-setting-up-on-linux/0](http://polycode.org/community/115-help-setting-up-on-linux/0)

---

