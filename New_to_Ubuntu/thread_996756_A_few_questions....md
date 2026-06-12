---
title: "A few questions..."
date: 2008-11-29
forum: New to Ubuntu
---

### Post by NicksterC on 2008-11-29
Hi everyone, I'm using Wubi, and I've never used any sort of Linux OS until today.

My first problem is that I want to run the internet via USB, i.e., through an ADSL modem. The internet won't work, even though it showed the correct name when I tested the Hardware. EDIT: "Won't work" as in "no connection".

Also, my screen is a bit off-centre, going towards the right. How do I set it right(lol)?

Another thing is that I can't run my exe files(which I compiled using Dev-cpp). I haven't actually compiled any of my cpp files on Ubuntu yet, but I'm talking about the ones compiled in Windows. 

One last thing, can you suggest a compiler(hopefully with GUI) for Ubuntu?

---

### Post by NicksterC on 2008-11-29
Anyone?
Please!
:(

---

### Post by Scarlath on 2008-11-29
> **NicksterC said:**
> Also, my screen is a bit off-centre, going towards the right. How do I set it right(lol)?
Mine does that too. All I have to do though is to just fix some settings on my screen (e.g pressing some buttons on the screen, not in the actual operating system). I have not yet installed the restricted drivers so I'm not sure if that will fix it. 

Can't really help you with your other questions, sorry :P

---

### Post by echo.whoami on 2008-11-29
What model is your modem???
See if you can install it with ubudsl. 

Exe files doesn't run on linux.

If you have your source code you can run in a terminal:
```
g++ <the source file name>.cpp -o <the compiled program name>.out
```

As for the screen you can get in the menu of your display and change horizontal settings.

The gui i am using is anjuta. If you google will find and other discussions about what gui for c++ to use.

---

### Post by kiran.tambe08 on 2008-11-29
heres the compiler----->[http://packages.ubuntu.com/dapper/c++-compiler](http://packages.ubuntu.com/dapper/c++-compiler) and about the screen u hav press the menu button on ur monitor and adjust it

---

### Post by davidbilla on 2008-11-29
Try

$ sudo pppoeconf

to configure your ADSL connection. You will have to enter your username and password and choose some other settings. Just choose defaults. This should just work fine. That's how I configure my connection.

And Eclipse CDT is supposedly a good IDE for C/C++ development. I've just started on it.

---

### Post by NicksterC on 2008-11-29
Thanks everyone, I managed to fix the screen, but apparently the display settings are different for XP and Ubuntu. I have to press the "Auto" button each time I boot into a different OS.

I'm afraid none of the other problems could be solved. There's some sort of linker error on trying to compile any source file, which I'll post in a bit. g++ wouldn't work anyway producing a whole para of errors or something. gcc only outputs that linker error.

As for the net bit, "sudo pppoeconf" can't find any compatible something-something.

Sorry for the lack of info, I'll post it up here in a bit.

---

### Post by NicksterC on 2008-11-29
Hmm... 
```
The program 'g++' can be found in the following packages:



 * g++
 * pentium-builder


Try: sudo apt-get install <selected package>


bash: g++: command not found



nick@ubuntu:~/Documents/cprogs$ gcc n2.cpp -o n2exe.out



gcc: error trying to exec 'cc1plus': execvp: No such file or 

directory
nick@ubuntu:~/Documents/cprogs$ 

```

Any ideas?

---

### Post by fballem on 2008-11-29
> **NicksterC said:**
> Hmm... 
```
The program 'g++' can be found in the following packages:



 * g++
 * pentium-builder


Try: sudo apt-get install <selected package>


bash: g++: command not found



nick@ubuntu:~/Documents/cprogs$ gcc n2.cpp -o n2exe.out



gcc: error trying to exec 'cc1plus': execvp: No such file or 

directory
nick@ubuntu:~/Documents/cprogs$ 

```

Any ideas?

Think of Windows and Ubuntu as two separate things. They are similar in many ways, but very different in others.

In ubuntu, the preferred way (especially for us newbies) to install a program is to use Synaptic. If you go to your ubuntu screen (I don't dual boot or use Wubi), then select System > Administration > Synaptic Package Manager, you will get a panel similar to the attached.

You can then search for g++. If it is not marked, then you can select it to be installed. (click and select the option). You can select more than one program, then select the Apply button.

Hope this helps solve one of your problems.

---

