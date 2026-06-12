---
title: "VMWare Tools installation, not going ahead"
date: 2012-02-15
forum: New to Ubuntu
---

### Post by bingoman on 2012-02-15
I need help installing VMWare Tools on the Ubuntu guest (host is Mac).  I have loaded the disk image and extracted the contents to the desktop.  So, it appears in the folder called vmware-tools-distrib.  Command line so far reads as follows:

user@ubuntu:~$ su
Password: 
root@ubuntu:/home/user# cd vmware-tools-distrib
bash: cd: vmware-tools-distrib: No such file or directory
root@ubuntu:/home/user# cd desktop
bash: cd: desktop: No such file or directory
root@ubuntu:/home/user# cd Desktop/ vmware-tools-distrib
root@ubuntu:/home/user/Desktop# sudo ./vmware-install.pl -d
sudo: ./vmware-install.pl: command not found
root@ubuntu:/home/user/Desktop# 
 
What am I doing wrong?  Also, how do I tell if it is already installed?

---

### Post by drmrgd on 2012-02-15
I think the problem is that you're not in the correct directory to run the file.  Just to be sure, you've put the vmware_tools_distrib folder on your Mac desktop (Host) or your Ubuntu desktop (Guest)?

If you've put it on your Ubuntu Desktop (which it does indeed need to be located in the Guest OS), then:

```
cd /home/user/Desktop/vmware-tools-distrib/
``` 

That should put you in the folder that contains the script.  Please let me know if you get an error and paste the exact terminal output here.  If no errors, then:

```
sudo ./vmware-install.pl
```

Then just follow the prompts to set it up as you like (usually the defaults are OK and I just hit yes to everything except for some of the experimental options).

---

### Post by bingoman on 2012-02-15
I can drag a file from host desktop to guest desktop.  I couldn't do that before.  That looks to me like evidence it works.   Thanks. 

Suffice to say, I took the default options to EVERYTHING and understood nothing.  Typical of newcomers, I guess.  Interestingly, Terminal seemed to think it was already installed so did some uninstalling first.

Does it matter that Virtual Machine>Install VMware Tools is clickable?  I heard it said elsewhere that that was one methed of telling whether it was installed.

---

### Post by drmrgd on 2012-02-15
> **bingoman said:**
> I can drag a file from host desktop to guest desktop.  I couldn't do that before.  That looks to me like evidence it works.   Thanks. 

Suffice to say, I took the default options to EVERYTHING and understood nothing.  Typical of newcomers, I guess.  Interestingly, Terminal seemed to think it was already installed so did some uninstalling first.

Does it matter that Virtual Machine>Install VMware Tools is clickable?  I heard it said elsewhere that that was one methed of telling whether it was installed.

Yep, that's usually a good sign that things are set up correctly.  I think you're good to go.  

When I first started using VMware Player, I didn't quite understand all of the settings either, and the person who showed me the software basically gave me the same advice I gave you: just say yes to everything.  Seems to be working well for me since :D

One other piece of advice:  if you ever lose the ability to drag and drop between host and guest and / or you lose the ability to copy and paste between guest and host, just reinstall the vmware player tools.  This will almost certainly happen anytime you upgrade the Linux kernel for Ubuntu.  I just keep a copy of the whole tools package in my /home directory so that I can run it easily when needed.

Not too sure about your last question.  It's that way on mine too, but I never messed with it.  Maybe it's a way of reinstalling via GUI rather than commandline?

---

### Post by bingoman on 2012-02-15
Like many Linux beginners, I'm PC literate and would be considered a geek by my contemporaries.  But at age 24, I lose patience with command lines and things which don't work out of the box.  I learned to use a Mac by myself, which is self-intuitive enough to do that. 

So I started with Virtual Machine>Install VMware Tools.  All it does is make the guest mount a disk image with the installer files on it.  

I got Adobe Flash installed on Firefox, after perhaps a full hour.  The first time I use a website without it, I'm redirected to Adobe, who give four different options for download of which none worked.  Ubuntu is going to take patience from me, but I appreciate the Linux corpus has come parsecs forward in this respect.

---

### Post by bingoman on 2012-02-15
OK - another thing.  I want to access files on host from the guest.  Ubuntu has a file browser; I can't find files.  I have shared them (and enabled it) in the VM settings.  

Is it supposed to be under Browse Network>Windows Network?

---

### Post by drmrgd on 2012-02-16
OK, this starts to drift outside of my realm of knowledge a bit (I really need to learn about sharing between different OSs, Samba, and whatnot).  Also, I on a Windows 7 host with Kubuntu as the guest here.  So, there could conceivably be differences.  

For me on this setup, I ran through the Shared Folders setup in Virtual Machine Settings -> Options tab -> Shared Folders.  Assuming you've done that already, I guess you could see the folder from Host.  On the Guest side, the folder is located in /mnt/hgfs/.  I think you can add the location to Nautilus so you don't have to follow the full path each time.  But, since I'm on Kubuntu, I don't know the exact steps to follow there (it may be just as easy as right clicking and choosing to add to Places or something).

Hope that at least points you in the right direction.

---

### Post by bingoman on 2012-02-17
Thanks for your efforts, but no luck.   I'll explain where I am:

I know about Virtual Machine>Settings>Sharing.  Mirroring folders is greyed out, so my only option is simple sharing (top of window).  I shared the host Downloads folder with guest, but I can't find it in the guest no matter where I look.  On Macs, the Downloads folder is created at installation and is used all the time. 

As for accessing guest files from host, I don't know where to start.

---

### Post by drmrgd on 2012-02-17
> **bingoman said:**
> Thanks for your efforts, but no luck.   I'll explain where I am:

I know about Virtual Machine>Settings>Sharing.  Mirroring folders is greyed out, so my only option is simple sharing (top of window).  I shared the host Downloads folder with guest, but I can't find it in the guest no matter where I look.  On Macs, the Downloads folder is created at installation and is used all the time. 

As for accessing guest files from host, I don't know where to start.

OK, just for the sake of clarity, did you say 'yes' to doing the file sharing when you installed vmware-tools?  If not, I'm thinking you may have to do that first; just re-run the vmware-tools setup again.  If so, then navigate (either terminal or Nautilus is OK) to /mnt/hgfs and see if the share folder you created it there.  That's where it is mounted for me, and hopefully there is no difference in your setup (not sure if the Mac filesystem throws a curve here).

---

### Post by bingoman on 2012-02-17
Oh dear.  Even attempting this has gone backwards.  

First off, cut & paste isn't working anymore (but drag & drop is); so I can't move the instructions from your first reply straight to ubuntu terminal.  

Second, when I type it in (cd /home/user/Desktop/vmware-tools-distrib/), the reply is 'no such file or directory'. It's in the same place it was last time.

My brief Linux experiment  may be shortlived, it seems.  There's still a lot of command line jiggery.  (Although now that I think about it, I did run the updates this morning which may not have helped…)

---

### Post by bingoman on 2012-02-17
Correction, terminal is case sensitive it seems.  

(So Desktop is capitalised, user and home aren't.  Bingoman finds his elementary English textbooks and revises spelling rules.)

---

### Post by bingoman on 2012-02-17
OK, the twit that I am may have missed this.  I know it looks like it is simple, but I'm not in a mood for trusting myself, so I will spell it out: basically there is another file I need to run and check for some things which may not be taking the default answer to all the options.  

Am I right?  I'll hit OK when I know I'm not insane. 

[I]The filesystem driver (vmhgfs module) is used only for the shared folder 
feature. The rest of the software provided by VMware Tools is designed to work 
independently of this feature.

If you wish to have the shared folders feature, you can install the driver by 
running vmware-config-tools.pl again after making sure that gcc, binutils, make
and the kernel sources for your running kernel are installed on your machine. 
These packages are available on your distribution's installation CD.
[ Press Enter key to continue ] [/I]

---

### Post by drmrgd on 2012-02-17
Hmmm...I've not seen that before.  It sort of suggests that you may be missing a few packages to complete the process, although I would have expected it to throw an error if it was missing things like 'gcc' and the kernel headers when you ran the script last time.  Perhaps I'm misinterpreting the error?  Did you remember any kind of warning or error when you tried to install the tools previously?

Let's start here and be sure he components you need are there (and if not install them):

```
sudo apt-get update
```
```
sudo apt-get install gcc linux-headers-generic build-essential
```

That will update your repository cache, and try to install the latest versions of the packages gcc, linux-headers-generic, and build-essential.  If you already have the newest verions, it'll say you do and won't try to download and install anything.

In response to your other comments, Linux is quite picky about capitalization and spacing.  So, it is very important to make sure you pay attention to the exact way something is written.  It does take a little getting used to, but once you know the rules, you will actually find it's quite quick and efficient to get around and do things you need to do the "Linux way"!  

A good trick is to use tab-completion.  If you start to type out a command or a location and then hit tab, assuming you've entered in something valid, the shell will fill the rest in for you.  That will assure that you don't make any typos and save some time.  So, for example:

```
cd /home/user/Des #then hit tab here right after the 's'
```

will fill in the work 'Desktop'.  However, if you try:

```
 cd /home/user/des #then hit tab as above 
```

you'll notice that nothing fills in because there is no directory or file that starts with 'des' where you're located.

---

### Post by bingoman on 2012-02-17
I have to use 'su, enter password: password, then the command' on three different lines.  This is because if I use 'sudo COMMAND' it rejects all passwords indiscriminately.  Ubuntu screen resolution has also reverted to narrowscreen (3x4) even though my Macbook is widescreen (~16x9).

I have let it go ahead with vmware config.

---

### Post by bingoman on 2012-02-17
Back to square one, I've attached the transcript.  The funny thing is before I'm told to make sure GCC is installed, it seems to have found it.

---

### Post by bingoman on 2012-02-19
no?

---

