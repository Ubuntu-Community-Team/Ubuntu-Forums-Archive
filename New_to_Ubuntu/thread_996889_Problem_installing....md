---
title: "Problem installing..."
date: 2008-11-29
forum: New to Ubuntu
---

### Post by kamitsukai on 2008-11-29
I'm trying to install a program called Lee's iplayer Client ([http://iplayer-client.sourceforge.net/](http://iplayer-client.sourceforge.net/)) but when I try installing it by following the instructions:

```
Lee's iPlayer Client v1.01

Thank you for downloading Lee's iPlayer Client v1.01.

Installation:

YOU MUST RUN THE INSTALL SCRIPT AS ROOT!

1. Open a terminal window.
2. Become root.
3. Run 
	chmod +x installer.sh
4. Run
	./installer.sh
5. Follow the instructions.

```

I'm presented with 3 options which I cant figure out how to select??? I've tried typing in the corresponding number alongside the options but with no luck:(

[IMG]http://img133.imageshack.us/img133/9613/screenshotcarlcarldesktek8.png[/IMG]

---

### Post by __Ryan__ on 2008-11-29
OK so sudo is somehow allowing the script to escape the root account.  You will need to become root temporarily for this to work correctly.

* MANDATORY DISCLAIMER ABOUT HOW ROOT IS BAD AND NOT SUPPORTED UNDER THE UBUNTU SECURITY POLICY *

```
$ sudo su -
```

Use this terminal to execute the scrip as root.

Close the terminal so you don't use it to run other commands unintentionally.

Good Luck

---

### Post by kamitsukai on 2008-11-29
still won't let me select any options or such...


```
carl@carl-desktop:~/Desktop/iPlayer$ sudo su -
[sudo] password for carl: 
root@carl-desktop:~# cd /home/carl/Desktop/iPlayer
root@carl-desktop:/home/carl/Desktop/iPlayer# ./installer.sh
: command not founde 2: 
: command not founde 4: clear
Welcome to Lee's iPlayer Installer v1.01

You MUST be root to continue!
chmod: cannot access `scripts/3/installer.sh\r': No such file or directory

Please select an option:

1. Install Lee's iPlayer Client 
2. View the README file
3. Quit
1
': not a valid identifierread: `SCR
: No such file or directoryscripts/.sh
: command not founde 17: 
root@carl-desktop:/home/carl/Desktop/iPlayer# 


```

---

### Post by __Ryan__ on 2008-11-29
Try:

```
$ file installer.sh
```

and

```
$ cat installer.sh
```

im curious if there isn't a windows carrage return in that file for some reason.

---

### Post by kamitsukai on 2008-11-29
didnt get anything from the first one but second one gave this:

```
root@carl-desktop:/home/carl/Desktop/iPlayer# cat installer.sh
#Lee's iPlayer Client Installer 1.01

#!/bin/bash
clear
echo "Welcome to Lee's iPlayer Installer v1.01"
echo ""
echo "You MUST be root to continue!"
chmod +x scripts/*.sh scripts/1/installer.sh scripts/2/installer.sh scripts/3/installer.sh
echo ""
echo "Please select an option:"
echo ""
echo "1. Install Lee's iPlayer Client" 
echo "2. View the README file"
echo "3. Quit"
read SCR
./scripts/$SCR.sh

```

---

### Post by __Ryan__ on 2008-11-29
try this, you don't have to be root for this:

```
sudo chmod -x scripts/3/installer.sh && sudo ./scripts/1.sh
```

---

### Post by kamitsukai on 2008-11-29
> **__Ryan__ said:**
> try this, you don't have to be root for this:

```
sudo chmod -x scripts/3/installer.sh && sudo ./scripts/1.sh
```

```
carl@carl-desktop:~/Desktop/iPlayer$ sudo chmod -x scripts/3/installer.sh && sudo ./scripts/1.sh
[sudo] password for carl:
: not found.sh: 2:
: not found.sh: 4: clear
Please select your Operating System

1. Linux
2. Mac OS X
3. iPhone OS
1
: bad variable name
: not found.sh: 11: clear
: not found.sh: 12: ./scripts//installer.sh
carl@carl-desktop:~/Desktop/iPlayer$
```

---

### Post by __Ryan__ on 2008-11-29
Could you print the results of this command:

```
$ ls -lR
```

---

### Post by kamitsukai on 2008-11-29
> **__Ryan__ said:**
> Could you print the results of this command:

```
$ ls -lR
```

Any specific part? as it's huge

---

### Post by __Ryan__ on 2008-11-29
Ok so I found the problem/problems.  The script was last edited in Windows and contains carrage retrun characters which are incompatable with Linux and have to be removed...no big deal.  I then tried to run the script and it doesn't even run correctly in BASH.

So long story short you can run these commands from the iPlayer directory to install the software.

```
sudo apt-get update
sudo apt-get install ruby
sudo ruby engine/setup.rb config
sudo ruby engine/setup.rb install
sudo cp bin/iplayer* /sbin
sudo chmod +x /sbin/iplayer /sbin/iplayer-sd
sudo chown $USER /sbin/iplayer /sbin/iplayer-sd
sudo mkdir ~/TV
```

I will caution that based on the quality of the install script you will most likely have even worse problems with the software.

Good Luck

---

### Post by lmitchell6 on 2008-12-29
Hi, I'm the developer of Lee's iPlayer Client and I would like to apologise for all the problems people are having. I'm new to the software development scene - this started out as a script to automate a process for my own use. I have taken all of your comments on board and will be releasing an updated version soon. Sorry about the carriage return characters - I was away from my Linux box for a while and forgot about the file incompatibilities. Feel free to PM me or email me: greenpacman [at] users.sourceforge.net. Just out of interest, kamitsukai, where did you hear about the app?

Lee :D

---

