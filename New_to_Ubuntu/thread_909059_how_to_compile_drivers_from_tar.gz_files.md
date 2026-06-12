---
title: "how to compile drivers from tar.gz files"
date: 2008-09-03
forum: New to Ubuntu
---

### Post by hazman on 2008-09-03
total noob at these[are they source files] compiling and stuff never done it be for.

---

### Post by paul_mcl on 2008-09-03
$ su
# apt-get install build-essential
# cd /path_to_unarchived_directory
# ./configure
# make
# make install

Also try to read INSTALL file located in an unarchived directory for specific instructions.

---

### Post by Troll_the_Great on 2008-09-03
See this links, maybe will help.
[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)
[http://www.monkeyblog.org/ubuntu/installing/](http://www.monkeyblog.org/ubuntu/installing/)
Cheers!

---

### Post by Elfy on 2008-09-03
Install build-essential and checkinstall

```
sudo apt-get install build-essential checkinstall
```

It could be an idea to look at checkinstall as well, use that rather than install if possible

[https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)

[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

@Troll_the_Great - the monkeyblog has been a dead link for a while


Edit - you won't be able to follow paul_mcl as you haven't got su , use sudo instead.

---

### Post by eggdeng on 2008-09-03
Assming you have downloaded the tar.gz file to /home/myfolder, first move to this folder
```
cd ~/myfolder
```
Now extract the file
```
tar -xvzf mytarfile.tar.gz
```
This will create a new folder with the name of your tar file. You can see it by running
```
ls
```
Move into the new folder (copy and paste the filename from the ls command)
```
cd mytarfile.
``` Do
```
ls
```
again and look for any README files or similar which might contain specific instructions. Normally, you will just need to run
```
./configure
```
then
```
make
```
then
```
sudo make install
```

---

### Post by hazman on 2008-09-03
is this all done in terminal. told you a thicko when it comes to compiling programs

---

### Post by Elfy on 2008-09-03
Yep in the terminal :) and if you get errors post them, if it is a long list of stuff to post please use code tags - either use the # button on the reply box or you can do it manually with [noparse]```
[/noparse] at the beginning of the lines of text and [noparse]
```[/noparse]  at the end

---

### Post by WRDN on 2008-09-03
> **hazman said:**
> is this all done in terminal. told you a thicko when it comes to compiling programs

Yes, all commands should be run in the Terminal. Although some are saying run "make install", it is better now to run "checkinstall". This will add an entry for the program to the package manager, to allow for easy removal later.

---

### Post by hazman on 2008-09-03
i get this response
wayne@ubuntu:~$ cd ~/wayne
bash: cd: /home/wayne/wayne: No such file or directory
wayne@ubuntu:~$
and
when using sudo su
root@ubuntu:/home/wayne#  cd ~/wayne
bash: cd: /root/wayne: No such file or directory
root@ubuntu:/home/wayne#  cd ~/

---

### Post by paul_mcl on 2008-09-03
> bash: cd: /home/wayne/wayne: No such file or directory
lol, /home/wayne/wayne

Try this:
$ cd
$ ls
Find if your folder is present and then:
$ cd your_folder_name

---

### Post by hazman on 2008-09-03
no it came up with desktop so i tried navigating to cd desktop and got same response no file or directory

---

### Post by paul_mcl on 2008-09-03
Linux filesystems are case sensitive. "Desktop" and "desktop" are two different folders.

---

### Post by hazman on 2008-09-03
thanks getting some where now

---

### Post by hazman on 2008-09-03
no second command didn't work think am going to give up with this cos i don't know what am doing and might end up wrecking system

---

### Post by Elfy on 2008-09-03
So you know cd ~ will get you to your home from anywhere, so cd ~/Desktop would be your desktop.

Also be aware that if you install from source you will need the folder later if you want to uninstall, as WRDN has said try and use checkinstall, I gave a link earlier which will be of some use in using it.

---

### Post by Elfy on 2008-09-03
Which command didn't work?  make?

What exactly are you trying to install - links?

---

### Post by hazman on 2008-09-03
its a webcam driver but i been such a plank the second line i copied exactly instead of the file i wanted to use.i think i got my self confused abit cos i already extrarted files to desktop using archive manager

---

### Post by hazman on 2008-09-03
everything going fine until ./configure and got
oot@ubuntu:/home/wayne/Desktop/linux-2.6.22.15# ./configure
bash: ./configure: No such file or directory
root@ubuntu:/home/wayne/Desktop/linux-2.6.22.15#

---

### Post by Elfy on 2008-09-03
Why are you doing this as root? You should just use sudo to run commands as root.

Give the link to where the driver came from please..

IF you got No such file or directory you're eithere in the wrong directory or there is no ./compile to run

---

### Post by hazman on 2008-09-03
i hadn't compiled the kernel or something and had to run make oldconfig,make xconfig.when i had done that and ran make to started doing something

---

### Post by paul_mcl on 2008-09-03
> **hazman said:**
> 
oot@ubuntu:/home/wayne/Desktop/linux-2.6.22.15# ./configure
bash: ./configure: No such file or directory

You must execute ./configure command when you're inside extracted directory. For example, cd ~/Desktop/my-driver-4.01/ and only then try this command.

---

