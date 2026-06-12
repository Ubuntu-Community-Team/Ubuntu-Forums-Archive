---
title: "How to program a shell application to create a journal file?"
date: 2021-05-16
forum: New to Ubuntu
---

### Post by bfromboston1 on 2021-05-16
Hello all,

My name is Brandon and I have very little experience with Linux. I've recently installed Ubuntu on an old laptop and am trying to understand an assignment that was given to me. **Basically I have to create a shell application to create a journal file and the shell script need to perform three functions (View, Modify, and append the journal file)**. Up until this point I have only ever used an SSH and never an OS like Ubuntu. So I guess my first question is how do I even create a shell application?

---

### Post by Holger_Gehrke on 2021-05-16
If you've used ssh to connect to a Unix or Linux machine, then the  commands you could execute in that ssh session were interpreted by a  shell.

The shell is a command line interpreter. There are multiple shells available for Ubuntu but the one that's installed and set as the default shell is bash - the 'Bourne Again SHell'. When you open a terminal and enter commands it's bash that's trying to read and execute your commands. A 'shell script' is a simple text file that contains commands for the shell. Just use any text editor you like, write commands into the file, save it, make it executable and run it from a terminal.

There are lot's of tutorials of varying quality on the web. A good book on the topic that's freely available for download is '[The Linux Command Line]("https://www.linuxcommand.org/tlcl.php")' by William Shotts.

Holger

---

### Post by grahammechanical on 2021-05-16
If I remember correctly, on this forum there is a policy not to do someone's school/college work for them. But, I think we can point people in the right direction. This is my offering.

Consider the application Software Updater. We open that application and it runs a few commands to update and upgrade/install the software of Ubuntu. In other words it is an application that runs a shell script in a shell/terminal.  We could do the same job with these commands in a terminal.

```
sudo apt update
sudo apt upgrade
sudo apt autoremove
```

Software Updater also updates the record (journal?) of what software packages have been upgraded. Everything depends upon the level of programming skill that you have been taught. Do you know how to craft a simple graphical user interface utility? 

I have no idea how to do that but I once modified the menu that Ubuntu shows when we choose Advanced Options>Kernel with Recovery mode. I added menu entries that allowed me to create, select & delete snapshots of the operating system. And it worked. In your case, what I did might have been called cheating. I call it using my initiative. I am just a private student of Linux/Ubuntu who is mainly self-taught.

Regards

---

### Post by bfromboston1 on 2021-05-16
Thanks for the help. I know I shouldn't be posting HW assignments but I just needed some help getting started. Which is what you guys did so thank you again.

---

### Post by ActionParsnip on 2021-05-16
Any command you can type in a terminal can be used in a script. A "journal file" just sounds like a text file but is ambiguous. Look into text redirection in Linux

---

### Post by grahammechanical on 2021-05-16
Use the file manager>properties will tell you if a file is a shell script and file manager will give an option to open the shell script in a text editor. Then you can study the syntax of the script.

Here is a tutorial on writing shell scripts 

[URL="https://linuxcommand.org/lc3_writing_shell_scripts.php"]https://linuxcommand.org/lc3_writing_shell_scripts.php

[/URL]Regards

---

