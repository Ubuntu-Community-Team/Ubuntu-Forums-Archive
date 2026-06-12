---
title: "Synaptic Package Manager Error"
date: 2013-01-22
forum: New to Ubuntu
---

### Post by thegetman on 2013-01-22
I am using Lubuntu 12.10 and This is how it happened:

I was on the internet looking for an antivirus program I could download. I know linux doesnt really need an antivirus program but i need it to scan files before I plug them into my Win7 PC. 

Well I came up on this site

*********************.com/2012/09/30/to-do-list-after-installing-ubuntu-12-10-aka-quantal-quetzal/


Followed these directions:

```
sudo sh -c 'echo "deb http://download.bitdefender.com/repos/deb/ bitdefender non-free" >> /etc/apt/sources.list.d/bitdefender.list'
wget http://download.bitdefender.com/repos/deb/bd.key.asc
sudo apt-key add bd.key.asc
sudo apt-get update
sudo apt-get install bitdefender-scanner-gui
```


and now I get this error when opening up SPM:

> E: Type 'ree' is not known on line 2 in source list /etc/apt/sources.list.d/bitdefender.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.


Now I dont got any antivirus and a big red circle with a white line through it in the task bar. Any advice would be appreciated.

---

### Post by irv on 2013-01-22
Try running the command in a terminal
```
sudo gedit /etc/apt/sources.list.d/bitdefender.list
```
And see if you can see where the error is coming from on line 2.

---

### Post by ibjsb4 on 2013-01-22
deb [http://download.bitdefender.com/repos/deb/](http://download.bitdefender.com/repos/deb/) bitdefender non-free

Something is wrong with this line in your sources list.

You can remove it or uncheck it or edit it.

[https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories)

[https://help.ubuntu.com/community/Repositories/Ubuntu#Editing_Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu#Editing_Repositories)

If you need futher help with this, please open a terminal and enter and post the output:

```
cat /etc/apt/sources.list.d/*
```

---

### Post by thegetman on 2013-01-22
Software sources will not open. I click on it and nothing happens. No matter what path I take to Software Sources it does not stay open.

This is the error i get when I run the cat command from above in the terminal

```
deb http://download.bitdefender.com/repos/deb/ bitdefender non-f
ree
deb http://download.bitdefender.com/repos/deb/ bitdefender non-free
deb http://ppa.launchpad.net/ehoover/compholio/ubuntu quantal main
deb-src http://ppa.launchpad.net/ehoover/compholio/ubuntu quantal main
deb http://ppa.launchpad.net/ehoover/compholio/ubuntu quantal main
deb-src http://ppa.launchpad.net/ehoover/compholio/ubuntu quantal main

```

---

### Post by matt_symes on 2013-01-22
Hi

Press ALT + F2 and type

```
gedit /etc/apt/sources.list.d/bitdefender.list
```Post the output back here by copying and pasting the text from that file into your next post.

Kind regards

---

### Post by ibjsb4 on 2013-01-22
```
gksudo leafpad /etc/apt/sources.list.d/*
```And edit out that space in the first line non-f  ree to non-free.

---

### Post by thegetman on 2013-01-22
This is the message I got after running that command:


> Failed to execute child process "gedit" (No such file or directory)

---

### Post by ibjsb4 on 2013-01-22
Oops, this be lubuntu.  Need some help here, what editor does lubuntu come with??

---

### Post by ibjsb4 on 2013-01-22
Leafpad, I edited the above post.

---

### Post by matt_symes on 2013-01-22
Hi

For a bit of variety 

```
sudo sed -i '1N;s/\n//' /etc/apt/sources.list.d/bitdefender.list
```

should also fix it from the command line. (copy and paste into terminal)

Kind regards

---

### Post by thegetman on 2013-01-22
So I did your steps now in the file path:

/etc/apt/sources.list.d

there is a file named '*' with "deb [http://download.bitdefender.com/repos/deb/](http://download.bitdefender.com/repos/deb/) bitdefender non-free" in it.


Before we proceed any further I was thinking maybe BitDefender doesnt work with Lubuntu? 

Anyway my goal now is not to get BitDefender working but just to be able to open up my Synaptic Package Manager and make the Red/white error Circle in the task bar go away without having to reinstall Lubuntu. Also if you know of any easy to install antiviruses that would be great to.

---

### Post by ibjsb4 on 2013-01-22
If you no longer care about BitDefender then just uncheck it and that should fix your package manager.

[https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories)

And update after

```
sudo apt-get update
```

---

### Post by thegetman on 2013-01-22
Software Sources Does not open or respond

---

### Post by oldos2er on 2013-01-22
Bitdefender will work fine with any of the *buntus.

Open lxterminal and run ```
sudo rm /etc/apt/sources.list.d/bitdefender.list

sudo apt-get update
```

---

### Post by thegetman on 2013-01-22
Fixed...Everything is working now Synaptic and Software Sources... but what exactly did it do

---

### Post by ibjsb4 on 2013-01-22
> **thegetman said:**
> Software Sources Does not open or respond

My bad, for future reference.

```
gksudo software-properties-gtk
```

Will take you to software sources.

And the "rm" command stands for remove.  So you removed BitDefender from the sources list.

---

### Post by oldos2er on 2013-01-22
**rm** is "remove", which deleted the file causing your problem. **sudo apt-get update** refreshes your sources, which are lists of software repositories in /etc/apt/sources.list and /etc/apt/sources.list.d/

[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by ibjsb4 on 2013-01-23
One last thing :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

