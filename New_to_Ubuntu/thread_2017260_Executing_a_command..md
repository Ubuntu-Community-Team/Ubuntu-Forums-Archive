---
title: "Executing a command."
date: 2012-07-05
forum: New to Ubuntu
---

### Post by Tuluppa on 2012-07-05
Hello!

So I have to run a command "echo 0 | sudo tee /proc/sys/kernel/yama/ptrace_scope" before I can login in diablo3 using wine.

My question is, is there anyway to make it into a double-clickable something so I dont have to actually type it everytime into terminal?

Thank you for reading

Tuluppa

---

### Post by prshah on 2012-07-05
> **Tuluppa said:**
> 
So I have to run a command "echo 0 | sudo tee /proc/sys/kernel/yama/ptrace_scope" before I can login in diablo3 using wine.

is there anyway to make it into a double-clickable something so I dont have to actually type it everytime into terminal?

Yes. You can create a text file, and put the line into it. Use gksudo instead of "sudo". Give the file execute permissions, and setup a link to it where convenient to you (Eg ~/Desktop). You can also add the commands to launch the game in the text file. This text file containing commands is called a "script file".

BUT

> 
Is there a better solution?

    A better solution which is more secure and does not require repetitively modifying ptrace_scope is to grant Wineserver ptrace capabilities.

        In a terminal:

        sudo setcap cap_sys_ptrace=eip /usr/bin/wineserver
        sudo setcap cap_sys_ptrace=eip /usr/bin/wine-preloader

        This exempts the wineserver and wine-preloader binaries from the non-child ptrace restriction, and allows them to ptrace any process.
        It only needs to be done once, and is safer because these binaries are usually from a trusted source - the official repositories or the official Wine PPA, so they aren't going to be malware.
 (From: [http://askubuntu.com/questions/146160/what-is-the-ptrace-scope-workaround-for-wine-programs-and-are-there-any-risks](http://askubuntu.com/questions/146160/what-is-the-ptrace-scope-workaround-for-wine-programs-and-are-there-any-risks) )

---

