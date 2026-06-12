---
title: "Switching from XP to Ubuntu for the first time"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by JimmyJim on 2008-05-25
Hello, as the title states I'm switching over for the first time. I am currently downloading Ubuntu 8.04 64 bit. I am going to completely format C:, which contains Windows, and use a smaller partition for document backup; I'm only going to be using Linux (Ubuntu distro to be specific). I have a few questions mainly regarding security:

1. My parent's computer is using Windows XP and we share a network. Although I try to make their computer as secure as possible and I always warn them, its hard to tell how secure it really is. Should I worry about any security issues? 

2. I'm not entirely sure if my current Windows installation is completely clean. I'll be backing up music, pdfs, documents, pictures etc. on a separate partition for my Linux install. Should I worry about anything bad compromising my fresh Ubuntu installation's security?

3. Will my Ubuntu installation be simple to install straight 'from the box'? Is there anything I need to know before I reformat and install? Note that I'm using a router; I'm not sure if that'll make a difference.

Thanks in advance!

---

### Post by maddot on 2008-05-25
for 1, linux or ubuntu, will not compromise your network, and since ubuntu works under linux, in theory the linux box will be immune to windows based viruses. However, if you later choose to dual boot as you're uncomfortable with ubuntu, then there is a chance, that a virus can cross over if you mount your linux partition in windows. It won't infect or anything, but essential files might be gone.

2. Nothing's bad as long as the files are not corrupted in the first place, that's all you need to worry about.

3. nope. nothing. it should work out of the box, if all your computer parts are supported. if you want to play mp3s and quicktime files, you'll need to activate the restricted codecs. besides that, my best answer is, just try it, don't worry, someone here will be able to solve your problem.....i hope.. XD

---

### Post by tamoneya on 2008-05-25
windows virii will not affect a linux system.  While I still recommend that you scan your files(I use clamAV) they wont compromise your linux system.  Linux is very (almost 100%) virus free.  The only thing you really have to worry about are rootkits.  Use rootkit hunter for this.

---

### Post by Paqman on 2008-05-25
> **JimmyJim said:**
> 
1. My parent's computer is using Windows XP and we share a network. Although I try to make their computer as secure as possible and I always warn them, its hard to tell how secure it really is. Should I worry about any security issues? 

Not nearly to the degree you would with Windows. You won't need antivirus, the software in the repos is 100% spyware and adware free, and the system has a firewall built in.

One security feature you might bump into to start with is the system of file permissions. It's pretty simple once you get used to it.

Check out the [security thread](http://ubuntuforums.org/showthread.php?t=765421) for a really in-depth explanation of the differences. 

> 
2. I'm not entirely sure if my current Windows installation is completely clean. I'll be backing up music, pdfs, documents, pictures etc. on a separate partition for my Linux install. Should I worry about anything bad compromising my fresh Ubuntu installation's security?

You'll be fine. Windows malware can't hurt a Linux system.

> 
3. Will my Ubuntu installation be simple to install straight 'from the box'? Is there anything I need to know before I reformat and install? Note that I'm using a router; I'm not sure if that'll make a difference.

Try out the LiveCD first. If you encounter any issues then come to this forum and see if there's a fix. If somebody hasn't posted the answer to your problem alread, then start a new thread and someone will be glad to help you.

---

### Post by JimmyJim on 2008-05-25
OK, I'm on Ubuntu as we speak and all seems to be well except one problem: I'm not sure how to get sound to work. I have an X-fi Xtrememusic soundcard. From what I've read, Linux support with this series hasn't been good. What should I do? 

Thanks again

---

### Post by JimmyJim on 2008-05-25
Although, less important, I should also mention that I tried to install Flash Player and I received a warning saying 64 bit isn't supported. :neutral: Do I have to do something special to install it? I didn't see a 64 bit version on the website.

---

### Post by wolfen69 on 2008-05-25
> **JimmyJim said:**
> Although, less important, I should also mention that I tried to install Flash Player and I received a warning saying 64 bit isn't supported. :neutral: Do I have to do something special to install it? I didn't see a 64 bit version on the website.

just do
```
sudo apt-get install flashplugin-nonfree
``` it should install nspluginwrapper automatically. did you enable your repos first? go to system>admin>software sources and check everything. then close and reload.

---

