---
title: "NAMD installation on UBUNTU machine"
date: 2008-10-02
forum: New to Ubuntu
---

### Post by MRM0607 on 2008-10-02
Dear UBUNTU form Team,

I am new to Linux (UBUNTU). 

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

### Post by rajan on 2010-06-17
i understand this is a really late post, but i figure it can help someone who found this thread by a google search (like me), but is confused with the same problem.


when you say:

> I tried to move the tar file in from current directory location, the command worked. Output is listed below:

mamta@requiem:/usr/local/src$ mv /home/mamta/Desktop/NAMD_2.6_Linux-i686.tar.gz ~/usr/local/src/


you should have typed 

```
mamta@requiem:/usr/local/src$ mv /home/mamta/Desktop/NAMD_2.6_Linux-i686.tar.gz /usr/local/src/
```

Notice that there's no ~ before the /usr/local/src. The ~ means your home directory. 

In the future, try to use the "search for files" utility that you can find in the "places" menu at the top left of your screen.

---

