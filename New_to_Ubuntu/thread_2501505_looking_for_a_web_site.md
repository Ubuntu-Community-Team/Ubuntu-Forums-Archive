---
title: "looking for a web site"
date: 2024-10-10
forum: New to Ubuntu
---

### Post by cryofreeze666 on 2024-10-10
i evidently need to find a website that tells me the definitions of the scripts used in the command terminal, so far google has just lined me up with the definition of command terminal script.  so where would i go to find terms like sudo, apt, etc. with definitions and maybe examples of usage so i can learn instead of relying on copy and paste.

---

### Post by 1fallen on 2024-10-10
Man Pages would be a good place to start.
```
man sudo
man apt
```
It's a learning curve that can't be covered in a few short hours>>>Takes some time. :)
I applaud your bravery for more terminal skills. It makes a world of difference in your Linux experience.

---

### Post by davetheoldcoder on 2024-10-10
This looks helpful:
[https://ubuntu.com/tutorials/command-line-for-beginners](https://ubuntu.com/tutorials/command-line-for-beginners)

I recommend going through the whole tutorial in sequence.

As *1fallen2* suggested, you can use the *man* command to get detailed information about specific commands that you see there.

---

### Post by bobunderwood99 on 2024-10-10
[https://explainshell.com/](https://explainshell.com/)

---

### Post by ActionParsnip on 2024-10-11
man pages are your friend. If you want them, in a browser then duckduckgo has the bang syntax. Eg:
```

!man sudo

```
Will bring up the man page on the web. Very handy.

---

### Post by him610 on 2024-10-11
> where would i go to find terms like sudo, apt, etc. with definitions and maybe examples of usage
You might consider checking out the link under my signature. The open source book can also be freely downloaded.

---

### Post by duke.tim on 2024-10-15
If you would like to learn more about bash scripting (assuming you are using bash) I highly recommend this guide
[Advanced Bash-Scripting Guide (tldp.org)]("https://tldp.org/LDP/abs/html/index.html")

It's not designed with eye candy to look pretty, but it is the best scripting guide i've come across.

---

### Post by cryofreeze666 on 2024-10-15
i gotta do something, cutting and pasting terminal commands isn't working.  it's like every image burning program i've tried doesnt want to work in 20.04.  got unetbootin to install, but now i can't find it.  it gives me these directions on how to run it.  

To run these binaries, download them and run the command chmod +x ./unetbootin-linux, or go to Properties->Permissions and check "Execute"), then start the application by running ./unetbootin-linux

1) i have tried the terminal and got an error
a@a-GA-78LMT-USB3-6-0:~$ chmod +x ./unetbootin-linux
chmod: cannot access './unetbootin-linux': No such file or directory
a@a-GA-78LMT-USB3-6-0:~$ 

2) don't know what app to access to enter commands
3) properties, i assumed that would be in the home file under the user name, i now assume i'm wromg. can't access it (the home file hidden files) for some reason. i was in there a couple weeks ago deleting my unsuccessful attempt to install steam.

the videos i watched showed an installed gui for the program, i'm obviously going to have to create a shortcut after i find an .exe file (yes, i'm still thinking in windows terms) 

i'm also getting annoyed that proof reading seems to be a foreign concept to a lot of these "help pages" with the copy and paste script.

thanks 1fallen2 and davetheoldcoder

---

### Post by davetheoldcoder on 2024-10-15
Let's start with this:

> every image burning program i've tried doesnt want to work in  20.04.  got unetbootin to install, but now i can't find it.

You're running Ubuntu 20.04, and you want to make a bootable USB thumb drive from a downloaded .iso file?

And running an installed application on Linux can depend on how you installed it, which you didn't explain.

If you're new to Ubuntu, it's best to start with applications installed through the built-in package manager.

Ubuntu's  default application for flashing USB drives is Startup Disk Creator  (package name usb-creator-gtk or usb-creator-kde, depending on whether  you're using the Gnome desktop or the KDE desktop). Either of these will provide a GUI application that you can run by clicking a desktop launcher icon.

To check if usb-creator-gtk is already installed, use this command;
```
dpkg --status usb-creator-gtk
```

If it's installed, the output will include "Status: install ok installed" or something similar.

---

