---
title: "Installing jdk system wide from binary"
date: 2008-11-16
forum: New to Ubuntu
---

### Post by kaustubh.bansal on 2008-11-16
Hello

I have a .bin file of jdk 6. I want to install it such that i can directly use "javac" and other commands from the terminal. In windows, i have to set PATH variable for this purpose. What is the parallel command in Ubuntu?
And which one is the recommended install directory?

---

### Post by fballem on 2008-11-16
Some questions, if I may:

[LIST=1]
[*]Where did you get the bin file that you are trying to install?
[*]Are you running a dual boot machine?
[*]Did you try the java that is available from the repositories?
[/LIST]

The reason that I'm asking is that a bin file meant for Windows will not work in Linux. As well, if you enable the Medibuntu repositories (instructions can be found at [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)), then there are Sun Java JRE (both 5 and 6) that are available and can easily be installed using Synaptic. An installation through Synaptic will ensure that the JRE is placed where it needs to be and that it is accessible from the terminal.

You will hear this often, but Linux is not Windows. It is a little different, and there is a learning curve.

I hope this helps,

---

### Post by kaustubh.bansal on 2008-11-17
I got it from netbeans dvd, i'm quite sure its meant for linux. Actually found a way round it. I need to export the jdk\bin directory of my installation to PATH each time I want to run java, though it is cumbersome but it still works. Is there any way i could make this command run at boot up? or better still, is there any way i can permanently add the jdk\bin to PATH variable?

---

### Post by bhatiasahil2009 on 2011-03-04
The solution would be to copy the line "export PATH=$PATH:/jdk_installtion_directory_path" in the .bashrc file which is located in home directory. Since it's a hidden file, it's name starts with a .(dot)

---

