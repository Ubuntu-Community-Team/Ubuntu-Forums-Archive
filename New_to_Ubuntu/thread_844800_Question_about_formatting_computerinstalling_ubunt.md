---
title: "Question about formatting computer/installing ubuntu"
date: 2008-06-29
forum: New to Ubuntu
---

### Post by le singe on 2008-06-29
Hello all.

So just today I found Ubuntu and it's variants and I'd like to install it.  Currently I'm using windows xp and I have recently acquired a few viruses (generic trojan horses... I don't know how harmful these may or may not be).  What I want to do is wipe my computer clean with a formatting (I'm prepared, and everything I'd like to keep is already backed up) but I have a few questions.

First, does a clean formatting typically get rid of most viruses, and in my case the type mentioned above?

And two, with the ubuntu or kubuntu installations (I haven't yet decided with which to go, if anyone would like to offer any suggestions...) are there options included that will let you format your hard drive clean before installing the new OS?  If formatting is something you have to do separately, well how would you go about it?  I have always asked my more computer-savvy friends to do this for me in the past.  Do you need a bootdisk, and then would you need to have the ubuntu installation installed onto a CD that you could load after formatting your computer?  Are there bootdisk programs downloadable online?

I'm basically just looking for a fairly simple way to do this.  I would very much appreciate any responses.  Thanks.

---

### Post by helixed on 2008-06-29
Hello,

First of all, just so you understand, formatting your computer erases the partition tables on your hard drive, which in essence deletes all of your data.  Anything, such as your documents, music, viruses, operating systems, on the disk which was there before, will be erased.  This can easily be done from the Ubuntu Live CD.  Simply boot from the CD and select Install on the boot menu.  When the installer asks you about how you want your disk formatted, simply select "Use entire disk".  You can download this disk at the Ubuntu website.

As for Ubuntu vs. Kubuntu, I personally prefer Ubuntu, but it all comes down to preference.  You could always download both live CDs and see which one you like better.

I hope this helps,

helixed

---

### Post by iaculallad on 2008-06-29
> **le singe said:**
> Hello all.
First, does a clean formatting typically get rid of most viruses, and in my case the type mentioned above?

Clean formatting will totally eliminate all traces of your windoze viruses and other malicious applications.

> **le singe said:**
> And two, with the ubuntu or kubuntu installations (I haven't yet decided with which to go, if anyone would like to offer any suggestions...) are there options included that will let you format your hard drive clean before installing the new OS?  If formatting is something you have to do separately, well how would you go about it?  I have always asked my more computer-savvy friends to do this for me in the past.  Do you need a bootdisk, and then would you need to have the ubuntu installation installed onto a CD that you could load after formatting your computer?  Are there bootdisk programs downloadable online?

All you need is the Ubuntu Desktop LiveCD, that acts as you're bootdisk and at the same time, a complete "Clone" of the real Ubuntu OS to be installed on your system. You can have both Ubuntu w/c uses GNOME as desktop and (k)Ubuntu w/c uses the KDE desktop environment on your system.

Formatting/Partitioning can be done by your LiveCD when you opt to install it on your Hard drive. Basically, you just need to create your /, /home, and swap directory. Or just use the automatic partitioning to let the LiveCD choose the best partition layout for you.

EDIT: You only need (1) Ubuntu LiveCD if you want to install the GNOME desktop or (k)Ubuntu's KDE desktop.

---

### Post by Matthewslf on 2008-06-29
And as for the viruses, even if they weren't erased, they wouldn't do anything. Linux is effectively virus-free. And windows would probably never inherit them from Linux either. Another note, if you still want to use windows (disadvised), it's easier to reinstall windows first. Lastly, you probably shouldn't use it, but once you learn a little more about formatting, GParted is a wonderful tool, and it comes on a live cd.

---

### Post by Victormd on 2008-06-29
> **le singe said:**
> Hello all.

So just today I found Ubuntu and it's variants and I'd like to install it.  Currently I'm using windows xp and I have recently acquired a few viruses (generic trojan horses... I don't know how harmful these may or may not be).  What I want to do is wipe my computer clean with a formatting (I'm prepared, and everything I'd like to keep is already backed up) but I have a few questions.

First, does a clean formatting typically get rid of most viruses, and in my case the type mentioned above?

And two, with the ubuntu or kubuntu installations (I haven't yet decided with which to go, if anyone would like to offer any suggestions...) are there options included that will let you format your hard drive clean before installing the new OS?  If formatting is something you have to do separately, well how would you go about it?  I have always asked my more computer-savvy friends to do this for me in the past.  Do you need a bootdisk, and then would you need to have the ubuntu installation installed onto a CD that you could load after formatting your computer?  Are there bootdisk programs downloadable online?

I'm basically just looking for a fairly simple way to do this.  I would very much appreciate any responses.  Thanks.

Seems like all your questions have been properly answered so I'd just like to welcome you to Ubuntu! :)

---

### Post by le singe on 2008-06-29
Hey, y'all replied quick!  Thank you!

So, about the live CD... do I have to actually have this on a burnt CD, or can I just download the installation "live CD" and it will know what to do, still giving me the option of using the entire disk drive to install the OS onto?

And I'm pretty set on never having to use windows again, so I'm not worried about installing both systems.  Just so long as GMU/linux is pretty compatible with most programs.

And about the suggestion of installing both ubuntu and kubuntu.... could I install one and at a later time install the other, saving a partition for the second OS?

---

### Post by iaculallad on 2008-06-29
> **le singe said:**
> Hey, y'all replied quick!  Thank you!

So, about the live CD... do I have to actually have this on a burnt CD, or can I just download the installation "live CD" and it will know what to do, still giving me the option of using the entire disk drive to install the OS onto?

You have to download the Ubuntu LiveCD ISO file. Try reading this [link]("https://wiki.ubuntu.com/BurningIsoHowto") on how to successfully burn it on a CD medium.

> **le singe said:**
> 
And about the suggestion of installing both ubuntu and kubuntu.... could I install one and at a later time install the other, saving a partition for the second OS?

Ubuntu by default is installed, (k)Ubuntu installation can be an option for you.

```
sudo apt-get install kubuntu-desktop
```

---

### Post by helixed on 2008-06-29
You never know about using windows again either.  Every once in a while I'll come across a program I can't find a Linux alternative to. For example, I occasionally use Photoshop CS3 to do design work.  While I stay in Linux 99% of the time, it's still nice to have a small Windows partition there just in case.  If you have the disk space available, you may want to consider creating a small partition and installing it on there.  Matthewslf is right, it really is a pain trying to install Windows after you've already installed Ubuntu.  You can always delete the Windows partition if you find you don't need it later, or resize it to make it bigger if you need more space.  

helixed

---

### Post by le singe on 2008-06-29
Ok, it looks like I'll have to wait until I can get to a CD burner before I can load the OS.

Thanks again for your input, everyone.  Bye!

---

### Post by glotz on 2008-06-29
> **le singe]And I'm pretty set on never having to use windows again, so I'm not worried about installing both systems.  Just so long as GMU/linux is pretty compatible with most programs.[/QUOTE]GNU/Linux won't run any of your old programs. You need to check if they offer versions for Ubuntu or Linux in general. Or then use Wine (practically a windoze emulator), which might or might not work with the programs. Or dual boot windoze or have it installed into a virtual machine. It's all very doable.

On the other hand Ubuntu for example comes with alot of programs so you probably won't need all of your old stuff.

Also I want to point out, as people stated, Linux is pretty much virus-free. But by no means is it trojan free. Once you open the gates and let the biiiiig wooden horse in, you will get infected. True on any platform. So no installing random stuff. As long as you stick with the official repositories, you'll have no worries. In Hardy (ver. 8.04) there are about 25 000 packages available.

Welcome to the land of the penguin!

EDIT: [QUOTE=le singe said:**
> Ok, it looks like I'll have to wait until I can get to a CD burner before I can load the OS.There are multiple ways of installing without a CD if you wish to pursue them. [https://help.ubuntu.com/community/Installation#Installation%20without%20a%20CD](https://help.ubuntu.com/community/Installation#Installation%20without%20a%20CD)

---

### Post by vikramaditya on 2008-06-30
> **le singe said:**
> Ok, it looks like I'll have to wait until I can get to a CD burner before I can load the OS.
Or, you can order the Live CD **free** from . . .
[https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)

---

### Post by Lupgaru on 2008-06-30
Instead of spending money on a CD Burner, you could go several routes to obtain one. First would be to go to Unbuntu homepage and request a free one(takes a while) Second buy one online for a few dollars(Amazon.com)for one, or get a friend to download the Live CD and burn it for you.
    After you obtain it, boot it, and let it work its magic. Once you give 8.04 a try you will probably never use Windows again as your primary system. Good Luck!

---

### Post by Papa-san on 2008-06-30
Since you are going to be waiting a minute, I have some useful suggestions for a new user. (I learned the hard way!)

I have a windoze partition used solely for offline applications that I use with it. The OS is configured to NOT go online. Anything I do online, I do through my Ubuntu installation. 

When you do set your partitions, set up a separate '/home' partition. This is where all of your stuff will get stored. The root partition '/' is where the Linux OS is. If something goes wrong, you can re-install Ubuntu, but you won't overwrite your stuff. (Documents, photos, music, etc...) Search for some 'How-To's' on setting that up... You will really appreciate it down the road!

---

