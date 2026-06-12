---
title: "help with install on UBUNTU"
date: 2008-10-02
forum: New to Ubuntu
---

### Post by MRM0607 on 2008-10-02
Dear UBUNTU Forum group,

I am new to LINUX(UBUNTU).

I opened a thread before but tag expired so I am opening a new thread.

I am trying to install NAMD software on ubuntu machine.

I tried to do reading before I start installing software and followed this link

[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

I followed step one as is written in the document.

I gave commands listed below

sudo apt-get install build-essential checkinstall
sudo apt-get install cvs subversion

The directory location at the time of command execution was /home/mamta.

Then as suggested I created directory /usr/local/src

After this I gave following commands at the command line (still the directory location is /home/mamta)

sudo chown yourusername /usr/local/src
sudo chmod u+rwx /usr/local/src

I tried to move the tar file in from current directory location, the command worked. Output is listed below:

mamta@requiem:/usr/local/src$ mv /home/mamta/Desktop/NAMD_2.6_Linux-i686.tar.gz ~/usr/local/src/

I tried to list the files in the current directory to see if it is there, This is the output I got:

mamta@requiem:/usr/local/src$ ls
mamta@requiem:/usr/local/src$ ls -la
total 8
drwxr-xr-x  2 mamta root 4096 2007-10-15 20:53 .
drwxr-xr-x 10 root  root 4096 2007-10-15 20:53 ..

When I use the icons on desktop to navigate I can see the file in the directory but via command line if I change to directory mentioned above, I cannot see the file via ls command. I found this confusing.

Despite this I tried to uncompress the file using tar -xvzf filename.tar.gz, but command fails. The message I get is

mamta@requiem:/usr/local/src$ tar xvzf NAMD_2.6_Linux-i686.tar.gz
tar: NAMD_2.6_Linux-i686.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

I thought may be I made a mistake and tried to redo 'sudo' commands again while I am in the /usr/local/src directory. Commands got executed and the output I got is listed below:

mamta@requiem:/usr/local/src$ sudo chown mamta /usr/local/src
mamta@requiem:/usr/local/src$ ls
mamta@requiem:/usr/local/src$ dir
mamta@requiem:/usr/local/src$ sudo chmod u+rwx /usr/local/src

Then I tried to list the contents of the directory, I got this output

mamta@requiem:/usr/local/src$ ls -la
total 8
drwxr-xr-x  2 mamta root 4096 2007-10-15 20:53 .
drwxr-xr-x 10 root  root 4096 2007-10-15 20:53 ..

I know there is something I am missing but I do not know what. I would kindly appreciate if you can help me out.

Thank you.
Mamta Mohan

---

### Post by 3rdalbum on 2008-10-03
Firstly, welcome to Ubuntu and the Ubuntu Forums.

Rather than doing all this creeping around in the command line, you might feel more comfortable doing as much as possible through a GUI.

Double-click on the file that you downloaded, the .tar.gz file. It will open in Archive Manager. Click the Extract button and extract it to somewhere in your home directory.

Use the file manager to go into the new directory that came out of the archive. Now you can act on whatever is inside the directory. I believe from the description that you've got a binary (precompiled program), so you might be able to just double-click the program icon and it will run.

If not you will need to navigate to that directory in the terminal, and then type:

./*programname*

where *programname* is the name of the program you need to run.

---

### Post by MRM0607 on 2008-10-03
Dear Forum user,

Thank you for your help. I appreciate it.

I will try that and if I run into problems I will write again

Mamta

---

