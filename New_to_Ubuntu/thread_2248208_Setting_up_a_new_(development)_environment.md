---
title: "Setting up a new (development) environment"
date: 2014-10-13
forum: New to Ubuntu
---

### Post by Daniel_Minnaar on 2014-10-13
Right, so after a weekend long battle with BIOS settings and incorrect MD5 hashes, I finally got Ubuntu installed and working well! \\:D/

My inspiration for moving over to Linux from Windows is that I'm tired of it all. I'm tired of big, clunky, unresponsiveness. I'm tired of all these new technologies coming out, and then being ported to Windows as a slower alternative. I have 11 years of experience developing .NET applications, but in the last few years I've been working on other languages like JavaScript and Python etc. Moving over to Linux brings up a few questions regarding configuration and setup.

**TL;DR**: I'm moving to Linux from Windows, and I have some questions regarding the configuration and installation of the OS and development applications.

Firstly, I'm used to having a 'data' partition on Windows where I store all my source code, media, etc. If I wipe Windows, I just re-install the OS & apps and I'm in full swing again 3 months later. Can / Should I do this with Linux? I'm prepared to reinstall if I need to redo the partitioning. Of the 160gb I have, I use 10gb swap (4gb  RAM) and 150gb primary. 

Secondly, I stupidly googled 'best code editor' which resulted in me installing vim and emacs. I opened up vim and had *no *idea what I had to do next. I'm looking for a clean and fast text editor that can assist me with HTML, JavaScript, Python, or even bash scripts. Asking for intellisense may be contradicting the clean / fast aspect, but I honestly have no idea whats out there. 

Lastly, after I installed Ubuntu, everything seemed to work perfectly. My mouse, keyboard, sound, video and even wifi adapter ***just worked***. Thank god for that, because if it didn't, I have no idea what I'd do. Which begs the question, how do I know if it's not working as perfectly as I think? How can I find out if it installed generic drivers which don't support certain features, or didn't install the correct drivers etc? I used to work with the Device Manager in Windows, but I'm a little lost now.

Also on a side note, how do I install 'services' on Linux that start up automatically and run in the background? When I think of technologies like apache, node.js and mongodb, what's the general prcedure of making my box run as a server?

Any help or points in the right direction will be appreciated.

---

### Post by nerdtron on 2014-10-13
> 

Firstly, I'm used to having a 'data' partition on Windows where I store all my source code, media, etc. If I wipe Windows, I just re-install the OS & apps and I'm in full swing again 3 months later. Can / Should I do this with Linux? I'm prepared to reinstall if I need to redo the partitioning. Of the 160gb I have, I use 10gb swap (4gb  RAM) and 150gb primary. 

Yup. You should use the "Something Else" option in Ubuntu installation screen for this. Basically same as windows, create a C: partition for OS and D: partition for data. But in Ubuntu, requirements are different, you need at least 2 partitions for OS, / partition that will hold the OS (and programs) and swap partition. Then create a larger partition for your data. 

> 
Secondly, I stupidly googled 'best code editor' which resulted in me installing vim and emacs. I opened up vim and had *no *idea what I had to do next. I'm looking for a clean and fast text editor that can assist me with HTML, JavaScript, Python, or even bash scripts. Asking for intellisense may be contradicting the clean / fast aspect, but I honestly have no idea whats out there. 
You edit text files directly? Have a look at Geany or the default Gedit. They both have syntax highlighting by default.

> 
Lastly, after I installed Ubuntu, everything seemed to work perfectly. My mouse, keyboard, sound, video and even wifi adapter ***just worked***. Thank god for that, because if it didn't, I have no idea what I'd do. Which begs the question, how do I know if it's not working as perfectly as I think? How can I find out if it installed generic drivers which don't support certain features, or didn't install the correct drivers etc? I used to work with the Device Manager in Windows, but I'm a little lost now.

That's how linux works. Most of the generic drivers are built on the kernel itself. If you are having problems on hardware, you can also ask questions in the forums. As long as nothing is acting up, then you're good to go.

> 
Also on a side note, how do I install 'services' on Linux that start up automatically and run in the background? When I think of technologies like apache, node.js and mongodb, what's the general prcedure of making my box run as a server?


When you install apache and mongodb or mysql, they all start at bootup (by default). The Desktop version of Ubuntu can be a good test bed for since if it works on the desktop, then it should work with the server version. Just install the programs/services you need and do your testing.

---

### Post by Daniel_Minnaar on 2014-10-13
> **nerdtron said:**
> 
You edit text files directly? Have a look at Geany or the default Gedit.

Well, if I had a nice IDE for html then i would use it. 

Thanks for the answers.

---

### Post by ajgreeny on 2014-10-13
As a means of saerching for applications such as a good html IDE I suggest you install synaptic, the best package manager for Ubuntu that is available, in my opinion.

It lets you search packages by name, or name and description, and will allow you to search for other available options, eg. bluefish.

---

