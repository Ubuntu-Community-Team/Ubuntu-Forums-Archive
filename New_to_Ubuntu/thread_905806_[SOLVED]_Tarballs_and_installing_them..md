---
title: "[SOLVED] Tarballs and installing them."
date: 2008-08-30
forum: New to Ubuntu
---

### Post by WastePotato on 2008-08-30
Hey guys,

As a Linux newbie, I ran into a problem when trying to install Adobe Flash player and PhotoRec. I downloaded the .tar.gz archives, but I have _no idea_ whatsoever on how to install them. Any help? :confused:

Please don't think I'm a dumbass after this. 	](*,)

And P.S: How do I install alternate desktop environments such as XFCE and KDE?

---

### Post by nothingspecial on 2008-08-30
> **WastePotato said:**
> Hey guys,

As a Linux newbie, I ran into a problem when trying to install Adobe Flash player and PhotoRec. I downloaded the .tar.gz archives, but I have _no idea_ whatsoever on how to install them. Any help? :confused:

I believe things have changed since gutsy so I`ll leave that to someone else, sorry.

> **WastePotato said:**
> And P.S: How do I install alternate desktop environments such as XFCE and KDE?

```
sudo apt-get install kubuntu-desktop
```

```
sudo apt-get install xubuntu-desktop
```

All these flavours on one pc is kind of fun at first, but it soon gets really annoying. But you wont know till you try.
:)

---

### Post by gorgon on 2008-08-30
photorec you can unpack where ever you want by clicking the file in the file browser, but the program you have to run from a terminal as root:

```
sudo your-directory/testdisk-6.10/linux$ ./photorec_static
```

also read this:
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)

hth,
gorgon

---

### Post by nothingspecial on 2008-08-30
Sorry, multiple posts.

What I meant by the first part of my reply was that
```
sudo apt-get install flashplugin-nonfree
```
used to work but I believe it dosen`t any more. Try it anyway.

You shouldn`t need to mess with tar.gz yet but this site explains how to install stuff very well. Read and bookmark -
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by mikewhatever on 2008-08-30
Adobe flash is in the repositories: <sudo apt-get install flashplugin-nonfree>.
As for photorec, it's in the repositories too: <sudo apt-get install testdisk>.
In case you really really have to install from source, check out the link below.
[http://www.monkeyblog.org/ubuntu/installing.html](http://www.monkeyblog.org/ubuntu/installing.html)

---

### Post by Darkade on 2008-08-30
The flash plugin you download from adobe has a installer

First open a terminal (now'll assume you have download the tarball on your desktop) and type this
```
tar -xf **flash***.tar.gz
``` change the bolds for the propper name of the tarball

This will extract the files and create a folder named intall_flash_something again in the terminal type
```
cd **install***
```

In that folder there's a file named flashplayer-installer  then just type

```
 ./flashplayer-installer 
```

More acurate instructions can be found in the adobe site here
[http://www.adobe.com/products/flashplayer/productinfo/instructions/#section-31](http://www.adobe.com/products/flashplayer/productinfo/instructions/#section-31)

---

### Post by jemate18 on 2008-08-30
> **WastePotato said:**
> Hey guys,

As a Linux newbie, I ran into a problem when trying to install Adobe Flash player and PhotoRec. I downloaded the .tar.gz archives, but I have _no idea_ whatsoever on how to install them. Any help? :confused:

Please don't think I'm a dumbass after this. 	](*,)

And P.S: How do I install alternate desktop environments such as XFCE and KDE?

These are the steps on how to install adobe flash player 9.
1. Applications -> Accessories -> Terminal
2. Assuming you have downloaded your adobe flash player on your desktop
 which is
```
/home/[name]/Desktop/install_flash_player_9_linux.tar.gz
```
type this on your terminal
```
cd ~/Desktop
```
then
```
tar -xf install_flash_player_9_linux.tar.gz
```
3. A new directory named install_flash_player_9_linux will be created that is
```
/home/[name]/Desktop/install_flash_player_9_linux
```
4. type
```
cd ~/Desktop/install_flash_player_9_linux
```
5. type
```
./flashplayer-installer
```
6. Then you will be prompted about the installation
7. Close any browser
8. Press Y for the question asked about the "proceed with the installation" question.
9.restart firefox, or just open it.
10. ENJOY

instructions for installing KDE and XFCE was given in one of the replies, if you miss them
```
sudo apt-get install kubuntu-desktop
```
```
sudo apt-get install xubuntu-desktop
```

jemate18

I hope this helps

---

### Post by WastePotato on 2008-08-30
> Last resorts: .rpm and .tar.gz
The preferred way to install software in Ubuntu is to use the package manager, which you can access through Add/Remove or Synaptic. As we've seen with Skype, sometimes you can also find a .deb for software not in the repositories. But what if you can't find a .deb?

.rpm
If you can't find a .deb, you can try a .rpm. These files are packaged for other Linux distributions (usually Fedora or Mandriva), but there is an application called alien (which you can install using Synaptic) that allows you (most of the time) to convert .rpm files to .deb. Read more about this process.

.tar.gz
As a last resort, you can download a .tar.gz file. The .tar.gz file extension indicates the file is a compressed set of files and folders (the compressed files you see in Windows usually have a .zip extension). If you see the .tar.gz, it could be compressed files that have a precompiled binary file, or it could be compressed files that have the source code allowing you to compile the application from source.

If you have trouble installing a .tar.gz file, you can ask for help on the Ubuntu Forums. 

Should this "alien" program be able to convert the .rpm archive to a .deb?

Adobe is offering a "YUM" download. What's that? Should I use it?

---

### Post by WastePotato on 2008-08-30
Thanks, I'll try it out when I boot into Ubuntu. :D

---

### Post by nicedude on 2008-08-30
Waste potatoe you should use a deb package for flash 10, someone has a thread here in the forums and if you can't find it I could email you one for Hardy. In general you should avoid trying to use source while new and especially when easy methods are available that work just as well like in this case a deb package is much easier.

Goodluck with flash

nicedude

---

### Post by nothingspecial on 2008-08-30
> **WastePotato said:**
> Should this "alien" program be able to convert the .rpm archive to a .deb?

Adobe is offering a "YUM" download. What's that? Should I use it? 

No, yums and rpms are for a different sort of linux. debs are for debian based distros like Ubuntu. 
Did you try installing flashplugin-nonfree yet?

---

### Post by jemate18 on 2008-08-30
> **WastePotato said:**
> Thanks, I'll try it out when I boot into Ubuntu. :D

DId you try the solution I have posted? Because I have just did it in my other PC freshly installed with Hardy I while ago. and it worked! tgz works. So please try my suggestion. If you want to install flash player 9.

You don't need alien to convert .rpm to .deb, tgz will work fine.

jemate18

---

### Post by WastePotato on 2008-08-30
nothingspecial, 

Thanks for the instructions! i'm now running XFCE on Ubuntu! Thanks! 

I didn't try KDE because all of the bad things I've heard about it. D:


Hey jemate18,

Thanks! It worked perfectly!


And mikewhatever, you where right, TestDisk was in the repositories. I didn't check flash, though. Thanks!

---

### Post by WastePotato on 2008-08-30
Sorry nicedude, I didn't see your post until after I got everything running. Thanks for the effort though.

BTW, you know when you where helping me yesterday with my wireless? The main thing that persuaded me to use your driver was the fact that you said it could crack encyption.

What sort of encryption are we talking about? WEP, WPA or WPA2? TKIP or AES?

I'm using I'd need something along the lines of Wireshark or Aircrack, right?

If its WEP, my school network uses WEP and when I try to tell the Network Admin that it's not secure he always waves me off and tells me that WEP is secure , which it's not. I'd like to show  him how quickly the wireless encryption can be cracked. 

:)

---

### Post by aysiu on 2008-08-30
You shouldn't have to use .tar.gz files or the terminal to get Flash or Photorec installed.

Here's a screenshot-laden guide on the normal way to install programs:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

As a matter of fact, installing Flash is as easy as visiting a site that requires Flash and then following Firefox's  (not YouTube's) prompts:
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

---

### Post by ibgeorgeb on 2008-08-30
In Synaptic Package Manager there is 'alien'. Install and give it a try using the 'sudo' command in terminal.

---

### Post by aysiu on 2008-08-30
> **ibgeorgeb said:**
> In Synaptic Package Manager there is 'alien'. Install and give it a try using the 'sudo' command in terminal.
Why?

You don't need .rpm files for Flash or TestDisk (the package that has Photorec).

---

### Post by jemate18 on 2008-08-31
> **WastePotato said:**
> nothingspecial, 

Thanks for the instructions! i'm now running XFCE on Ubuntu! Thanks! 

I didn't try KDE because all of the bad things I've heard about it. D:


Hey jemate18,

Thanks! It worked perfectly!


And mikewhatever, you where right, TestDisk was in the repositories. I didn't check flash, though. Thanks!

Mark this thread SOLVED if you are able to do what you intend to do and DONT FORGET to THANK the people who HELPED YOU by clicking the "thanks" button

jemate18

---

### Post by jemate18 on 2008-08-31
> **WastePotato said:**
> nothingspecial, 

Thanks for the instructions! i'm now running XFCE on Ubuntu! Thanks! 

I didn't try KDE because all of the bad things I've heard about it. D:


Hey jemate18,

Thanks! It worked perfectly!


And mikewhatever, you where right, TestDisk was in the repositories. I didn't check flash, though. Thanks!

Check this link this will show you how to mark the thread as SOLVED

```
https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads 
```

Marking a thread as SOLVED allows other user search to be more easy and finding answers to their problems. As for the "THANKS" it usually feels better for those who helped to have an incremental or more "THANKS" status.

Cheers! More power to Ubuntu users

jemate18

---

### Post by WastePotato on 2008-08-31
jenmate18,

Double Post?

I already thanked everyone on this thread. :mrgreen:

---

### Post by jemate18 on 2008-08-31
> **WastePotato said:**
> jenmate18,

Double Post?

I already thanked everyone on this thread. :mrgreen:

Oh Its now my footer for every post/reply i make.. :)

---

### Post by WastePotato on 2008-08-31
Hehe :lolflag:

---

### Post by ellalan on 2008-09-02
> **nicedude said:**
> Waste potatoe you should use a deb package for flash 10, someone has a thread here in the forums and if you can't find it I could email you one for Hardy. In general you should avoid trying to use source while new and especially when easy methods are available that work just as well like in this case a deb package is much easier.

Goodluck with flash

nicedude

Hi nicedude
Could you please give me the link to get flash 10 .deb files.

---

### Post by aysiu on 2008-09-02
> **ellalan said:**
> Hi nicedude
Could you please give me the link to get flash 10 .deb files.
At the bottom of the page;
[http://packages.ubuntu.com/hardy-backports/flashplugin-nonfree](http://packages.ubuntu.com/hardy-backports/flashplugin-nonfree)

Pick your architecture (64-bit or not) and then pick the download mirror closest to you.

---

