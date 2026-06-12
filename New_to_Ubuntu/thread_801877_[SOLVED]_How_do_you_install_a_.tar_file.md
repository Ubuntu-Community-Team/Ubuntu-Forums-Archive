---
title: "[SOLVED] How do you install a .tar file?"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by Bigtime_Scrub on 2008-05-21
I downloaded a linux game because I wanted to check out what was available. I know how to extract a tar file, but I dont know how to install it.

---

### Post by Maestro23 on 2008-05-21
Is there a README/Installation file in the extracted folder?

---

### Post by iaculallad on 2008-05-21
Usually, game installers comes with the install script. To install it, open your terminal, then change directory to your "game" directory and issue the command

**./install**

on the terminal. (i.e: ian@gutsy-gibbon:~/GamesFolder$ ./install)

---

### Post by rockerphil on 2008-05-21
i generally prefer not to install from a tarball, there are really a lot of games for Ubuntu that you can install from Synaptic or the command line, but usually the tarball comes with the install script as stated above. but yea, try looking around for some games for Ubuntu, google it if need be.

---

### Post by Bigtime_Scrub on 2008-05-21
I made a directory for the game. 
 I had already extracted the tar, so I needed to put the game into the directory. I dont know how to this from terminal and when I tired I got permission denied.

---

### Post by sam_delta on 2008-05-21
extract the files into a folder called "game" in your desktop
then , open a terminal and type
```
cd Desktop/game
```

then, to install, try 
```
sudo ./install
```

type your password and tell us if it works

sam

---

### Post by Inxsible on 2008-05-21
> **sam_delta said:**
> extract the files into a folder called &quot;game&quot; in your desktop
then , open a terminal and type
```
cd Desktop/game
```then, to install, try 
```
sudo ./install
```type your password and tell us if it works

sam

You don't really need a sudo for the install since he is in his home folder. That way the game will be installed only for the current user.

---

### Post by Bigtime_Scrub on 2008-05-21
> **sam_delta said:**
> extract the files into a folder called "game" in your desktop
then , open a terminal and type
```
cd Desktop/game
```

then, to install, try 
```
sudo ./install
```

type your password and tell us if it works

sam

This is what I got.

gary@gary-desktop:~$ cd Desktop/game
gary@gary-desktop:~/Desktop/game$ sudo ./install
[sudo] password for gary: 
sudo: ./install: command not found
gary@gary-desktop:~/Desktop/game$

---

### Post by Inxsible on 2008-05-21
> **Bigtime_Scrub said:**
> I made a directory for the game. 
 I had already extracted the tar, so I needed to put the game into the directory. I dont know how to this from terminal and when I tired I got permission denied.

What files do you see when you extracted the tar ball? There must be a readme. Not all install files are named "install" Some games also come with "setup" as the installation script file. So you would have to see under the tar ball to know which file should be executed.

---

### Post by HotShotDJ on 2008-05-21
> **Bigtime_Scrub said:**
> I downloaded a linux game because I wanted to check out what was available.Have you confirmed that this game is not available in the repositories (System --> Administration --> Synaptic Package Manager)?  Have you used Google to search for a package for Ubuntu from a trusted third-part repository?

---

### Post by iaculallad on 2008-05-21
Post the result of this command:

ls

gary@gary-desktop:~/Desktop/game$ls

---

### Post by Bigtime_Scrub on 2008-05-21
I didnt see a set up menu and its not in the repositories. I did find a read me on the home site with install instructions though.

You need OpenGL and X libraries and header files installed.  As of version 0.5,
you also need libpng.

As the superuser, run `make install'.

The data files will be installed at /usr/local/share/vulcan, and the game
binary will be installed at /usr/local/bin/vulcan. If you wish to change this
configuration, edit the Makefile and change the variables PREFIX, BIN, and
DATA_DIR (at the beginning of the file).

---

### Post by Bigtime_Scrub on 2008-05-21
> **iaculallad said:**
> Post the result of this command:

ls

gary@gary-desktop:~/Desktop/game$ls


I got this 

gary@gary-desktop:~$ cd Desktop/game
gary@gary-desktop:~/Desktop/game$ ls
vulcan-0.7
gary@gary-desktop:~/Desktop/game$

---

### Post by Bigtime_Scrub on 2008-05-21
If I need to get some kind of compile program dont worry about it. I will research it a lot more later. I know those can get a little tricky.

---

### Post by ad_267 on 2008-05-21
How to install anything in Ubuntu:
[http://monkeyblog.org/ubuntu/installing.html#source](http://monkeyblog.org/ubuntu/installing.html#source)

---

### Post by Inxsible on 2008-05-21
> **Bigtime_Scrub said:**
> I got this 

gary@gary-desktop:~$ cd Desktop/game
gary@gary-desktop:~/Desktop/game$ ls
vulcan-0.7
gary@gary-desktop:~/Desktop/game$If that's the only file in there I don't think you have extracted the tar yet. or is vulcan-0.7 a folder?

try going into that folder(if it is one) and then post the output of ```
ls -la
``` l is lowercase L

---

### Post by iaculallad on 2008-05-21
On your terminal:

gary@gary-desktop:~/Desktop/game$

Change Directory to vulcan-0.7

cd vulcan-0.7

then issue the command: sudo ./install

---

### Post by Bigtime_Scrub on 2008-05-21
> **ad_267 said:**
> How to install anything in Ubuntu:
[http://monkeyblog.org/ubuntu/installing.html#source](http://monkeyblog.org/ubuntu/installing.html#source)

The tar section of that linked worked for me thank you.

I needed a build essential compiler tool.

---

### Post by iaculallad on 2008-05-21
This could do the trick:

**sudo apt-get install build-essential**

---

### Post by Bigtime_Scrub on 2008-05-21
> **iaculallad said:**
> This could do the trick:

**sudo apt-get install build-essential**

Yeah I did that with Synaptic. Thanks.

---

### Post by Xiong Chiamiov on 2008-05-21
> **ad_267 said:**
> How to install anything in Ubuntu:
[http://monkeyblog.org/ubuntu/installing.html#source](http://monkeyblog.org/ubuntu/installing.html#source)
I was wondering when someone was going to link to it.

Although I always thought compiling was scary, I had actually done it a few times before realizing that I had.  Now I'd prefer doing that (especially with checkinstall so I can uninstall it through apt) over the annoying next-next-next interface of Windows.  Granted, compiling takes more time than uncompressing a binary, but that's why I don't use Gentoo.

---

### Post by iaculallad on 2008-05-21
> **Xiong Chiamiov said:**
> I was wondering when someone was going to link to it.

Although I always thought compiling was scary, I had actually done it a few times before realizing that I had.  Now I'd prefer doing that (especially with checkinstall so I can uninstall it through apt) over the annoying next-next-next interface of Windows.  Granted, compiling takes more time than uncompressing a binary, but that's why I don't use Gentoo.

You're right in there Xiong Chiamiov, that's the reason too why I opted on using Ubuntu over Gentoo (But still I have a dual boot on Sabayon), the manual compilation of packages :-)

---

