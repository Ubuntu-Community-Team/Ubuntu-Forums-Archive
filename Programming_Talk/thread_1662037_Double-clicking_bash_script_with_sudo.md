---
title: "Double-clicking bash script with sudo"
date: 2011-01-07
forum: Programming Talk
---

### Post by japhyr on 2011-01-07
Hello,

I am writing a bash script to automate the installation of packages when I configure a new computer.  The script is working, but since many of the commands need root privileges, I have to run the script from the terminal, ie "sudo /home/username/Desktop/script.sh".  If I double click the script icon on the Desktop, the program runs but fails quickly because it does not have root privileges.

Is there a way to gain root privileges after clicking the script icon?

---

### Post by PaulM1985 on 2011-01-07
I think if you use "gksudo" it will prompt a user interface so that you can type in the password.  You should only be prompted on the first occasion.

Paul

---

### Post by Hur Dur on 2011-01-07
chmod +x?

I'm pretty sure it only requires administrative privileges to make it executable, and after that you can just double click it.

---

### Post by japhyr on 2011-01-07
I have made some progress based on people's responses. The first possibility:```
#!/bin/bash
logFile="$HOME/logs/log_test.txt"
sudo apt-get update | tee "$logFile"
```
This solution works, if I double-click the script and select "run in terminal".  This is actually what I want, because the script will update the computer, install a bunch of packages, and then copy some configuration files.  So we want the output logged, but simultaneously displayed in a terminal to monitor progress.

I have a related question, though.  The core of the actual script has a loop that installs a series of programs:```
for package in "${packages[@]}";
  do
    sudo apt-get -y install package
  done
```When I run this, what will happen when the script takes longer than 15 minutes to run (which is very likely)?  Will it fail?  Will it prompt for a password again?  Is there a way for the script to keep root privileges until the script finishes running?

---

### Post by soltanis on 2011-01-08
> **japhyr said:**
> When I run this, what will happen when the script takes longer than 15 minutes to run (which is very likely)?  Will it fail?  Will it prompt for a password again?  Is there a way for the script to keep root privileges until the script finishes running?

No need to fear. Once you invoke the interpreter with root privileges, as it executes the shell script it will keep those privileges throughout the duration (and all child processes i.e. aptitude also inherit those privileges from the shell).

---

### Post by japhyr on 2011-01-08
Thank you, I will give that a try.

---

