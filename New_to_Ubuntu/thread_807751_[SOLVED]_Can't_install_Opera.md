---
title: "[SOLVED] Can't install Opera"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by special ed on 2008-05-26
I couldn't find Opera in the Package Manager so I went to Opera's website to download it.

I download it and open it but I keep getting an error: 
Wrong Architechture 'i386'

Am I missing something?

newbie

---

### Post by bumanie on 2008-05-26
You have either downloaded the windows version or trying to put a 64bit version on a 32bit operating system. Without the file name etc. it is hard to definitively know what is causing the problem. Can you post the name of the file. Also include your computer specs. and whether you are running ubuntu 32bit or 64bit and which version of ubuntu ie 7.10, 8.04 etc.

---

### Post by ardvark71 on 2008-05-26
> **special ed said:**
> I couldn't find Opera in the Package Manager so I went to Opera's website to download it.

I download it and open it but I keep getting an error: 
Wrong Architechture 'i386'

Am I missing something?

newbie

Hi...

Is your processor 32 bit or 64 bit? 

Best Regards...

---

### Post by ahmatti on 2008-05-26
> **special ed said:**
> I couldn't find Opera in the Package Manager so I went to Opera's website to download it.

I download it and open it but I keep getting an error: 
Wrong Architechture 'i386'
newbie

It seems to me that you are trying to install 32bit version on a 64 bit system. There is a 64 bit version of Opera 9.5b available at:
[ftp://ftp.opera.com/pub/opera/linux/950b2/final/en/x86_64/](ftp://ftp.opera.com/pub/opera/linux/950b2/final/en/x86_64/), you'll want to get the .deb package

---

### Post by sayakb on 2008-05-26
Post the output here of because most probably, you have a x86_64 architecture (64-bit):
```
uname -m
```Also, make sure your software sources (System->Administration->Software sources) are enabled. After enabling all the software sources:
```
sudo apt-get update
sudo apt-get install opera
```

---

### Post by special ed on 2008-05-26
I have a HP Laptop dv6000t with dual core processor, 2GB of RAM Nvidia 8400 video card. I installed Ubuntu 8.04 with Wubi.

I downloaded Opera from here:
[http://www.opera.com/download/index.dml?platform=linux](http://www.opera.com/download/index.dml?platform=linux)

I selected Ubuntu 8.04 and hit download. Then I open the installer and it starts to install then stops with the error

---

### Post by sayakb on 2008-05-26
That is all fine. Now what you have downloaded is a 32-bit version of Opera while you need is a 64-bit one. Either follow the last 2 commands I posted after enabling all software sources, or install the existing one with a force architecture constraint (which has some chances of screwing up your 64-bit packages)
** To install the one you've already downloaded:**
```
sudo dpkg -i packagename --force-architecture
```It's better if you download a 64-bit package rather than installing this one.

---

### Post by ahmatti on 2008-05-26
> **special ed said:**
> I have a HP Laptop dv6000t with dual core processor, 2GB of RAM Nvidia 8400 video card. I installed Ubuntu 8.04 with Wubi.

I downloaded Opera from here:
[http://www.opera.com/download/index.dml?platform=linux](http://www.opera.com/download/index.dml?platform=linux)

I selected Ubuntu 8.04 and hit download. Then I open the installer and it starts to install then stops with the error

You downloaded the 32bit version, get the 64bit version from the link I posted above and it should work for you.

---

### Post by ahmatti on 2008-05-26
> **LinuxIsInnovation said:**
> That is all fine. Now what you have downloaded is a 32-bit version of Opera while you need is a 64-bit one. Either follow the last 2 commands I posted after enabling all software sources, or install the existing one with a force architecture constraint (which has some chances of screwing up your 64-bit packages)


I don't think opera exist in the 64bit repos, even after enabling all sources? At least I couldn't find it and I should have all the repos enabled..

---

### Post by sayakb on 2008-05-26
Hmm.. it doesn't. 

@OP
Just download the 64-bit package as indicated by ahmatti

---

### Post by special ed on 2008-05-26
> **ahmatti said:**
> It seems to me that you are trying to install 32bit version on a 64 bit system. There is a 64 bit version of Opera 9.5b available at:
[ftp://ftp.opera.com/pub/opera/linux/950b2/final/en/x86_64/](ftp://ftp.opera.com/pub/opera/linux/950b2/final/en/x86_64/), you'll want to get the .deb package


I used your link and downloaded and installed. But now I can't find it.

It's not under Applications/Internet

Sorry, but I'm really new to this

---

### Post by ahmatti on 2008-05-26
Try running it from the terminal, the command is simply

opera

Strange that you don't have the launcher..  I installed it using the same deb and I have the launcher under applications\internet

---

### Post by special ed on 2008-05-26
> **ahmatti said:**
> Try running it from the terminal, the command is simply

opera

Strange that you don't have the launcher..  I installed it using the same deb and I have the launcher under applications\internet

I did this and it worked. but I have another problem. When I close Opera the only way I can open it again is by going to Terminal again

---

### Post by aysiu on 2008-05-26
Right-click the Applications menu and select Edit Menu

Then add a launcher under Internet and make sure the command is ```
opera
```

---

### Post by sayakb on 2008-05-26
> **special ed said:**
> I did this and it worked. but I have another problem. When I close Opera the only way I can open it again is by going to Terminal again

Create a Launcher for opera. Right click on Desktop and click "Create Launcher" and enter the name and command as opera

---

### Post by special ed on 2008-05-26
Got it. Thank you for all your help and patience.

---

### Post by ahmatti on 2008-05-26
You can create a launcher for it. Just right click on the Desktop and choose "Create launcher" -> the command again is simply opera.

EDIT: Wow you guys were fast, or then I'm really slow...

---

### Post by Sef on 2008-05-26
Check this:  Systems > Preferences > Main Menu > Internet > Click on box next to Opera.

---

