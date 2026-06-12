---
title: "Quick Help"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by adobrakic on 2008-05-26
I'm new to ubuntu, i got 8.04, and i'm having a little bit of trouble. I've had it for two days now and i figured out a lot of problems i had (and trust me, i've had a lot of issues). There's one thing I can't find out how to do though. Sometimes when I download things from synaptic, it doesn't appear in the Applications folder. Then I try to search for it, and i usually don't find the file, and if i do its just a folder full of stuff that doesnt open the program.

My specific problem is that I wanted a sysmetrix alternative for linux. I stumbled upon a post that said any of the following programs work like sysmetrix: conky, gkrellm, superkaramba, gdesklets, adesklets
I tried conky, gkrellm, and superkaramba, and i could never find where they've been installed to. I've deleted conky and grellm, but superkaramba is somewhere on here.

Can some one please show me how to locate it, and open it. And also, if there's a better prog than superkaramba that's like sysmetrix that you guys recommend, i'd love to know.

---

### Post by NikoC on 2008-05-26
Deleting:
In a terminal type:
sudo updatedb --> this will update the list of all files installed on your pc
locate superkaramba --> this will display a list of files containing 'superkaramba'
To remove an installation you could also just use synaptic again...

Opening a program:
ALT + F2
And in the dialogue box type 'conky' or 'superkaramba' or 'gkrellm' etc.
I think it will also autocomplete the name of the application you are typing.
Good luck!

---

### Post by adobrakic on 2008-05-26
I did sudo updatedb, and then locate superkaramba, but a looonngg list showed up. Is there like a main extention that usually programs are in (such as .exe on windows), because then it'd be a lot easier for me to locate.

And sorry to anyone who gets annoyed at these kinds of topics. I'm still trying to find out how everyone even remembers what the codes you type in terminal mean.:/

---

### Post by dRock1286 on 2008-05-26
and if need be, you can create a new launcher in the section of your menu that you want with the code for the program you are trying to launch

---

### Post by adobrakic on 2008-05-26
ah, okay i got conky installed and running, thanks a lot :]
also, do i need to do 'sudo updatedb' everytime before doing alt+f2 and opening a program with that?

---

### Post by NikoC on 2008-05-26
> **adobrakic said:**
> I did sudo updatedb, and then locate superkaramba, but a looonngg list showed up. Is there like a main extention that usually programs are in (such as .exe on windows), because then it'd be a lot easier for me to locate.

And sorry to anyone who gets annoyed at these kinds of topics. I'm still trying to find out how everyone even remembers what the codes you type in terminal mean.:/

If you want to remove it, run synaptic again, search for superkaramba, right click the package and select removal. I only use the terminal for removing packages that weren't installed via synaptic.

The following link may give you some more general info on linux directory structure
[http://www.tuxfiles.org/linuxhelp/linuxdir.html]("http://www.tuxfiles.org/linuxhelp/linuxdir.html`")

Just as dRock1286 stated, you can always right click your applications menu and edit it to add applications that don't appear in there automatically.

When you use linux frequently, you 'll see that it's fairly easy to quickly pick up and learn these commands...

---

### Post by NikoC on 2008-05-26
> **adobrakic said:**
> ah, okay i got conky installed and running, thanks a lot :]
also, do i need to do 'sudo updatedb' everytime before doing alt+f2 and opening a program with that?


No, if you run it via ALT + F2, no need to udpatedb.

---

### Post by adobrakic on 2008-05-26
okay, thanks a lot guys.

---

