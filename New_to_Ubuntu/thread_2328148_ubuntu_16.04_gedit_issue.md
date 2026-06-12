---
title: "ubuntu 16.04 gedit issue"
date: 2016-06-17
forum: New to Ubuntu
---

### Post by briandennis16 on 2016-06-17
I am trying to get my Ubuntu 16.04 updated being that I just wiped windows out of my HDD yesterday and am now a Ubuntu only user, I am having trouble with gedit and I am not totally sure if this is the right forum to post in but here we go anyway. This is what I keep getting in response from trying to upload a compiler and test it out. Any advise would be greatly appreciated.

[ATTACH=CONFIG]269642[/ATTACH]

---

### Post by briandennis16 on 2016-06-17
trying to install some programming stuff and I keep getting this **ERROR** Message in return.. Any answers or insight would be awesome thanks in advance!!

[ATTACH=CONFIG]269643[/ATTACH]

---

### Post by grahammechanical on 2016-06-17
The first thing that I would like to say is that you should not be using "sudo" to load Gedit. This is a much safer command to use

```
sudo -H gedit
```

The second point is that it is usual to see various error messages when we load applications like Gedit from the terminal.

Third, it is possible to load Gedit and at the same time have it open a file to edit but we often need to include the path to the file. What is first.c? Is it a file that can be edited in a text editor?

Regards

---

### Post by Impavidus on 2016-06-18
+1 to the above.

I assume the .c file is C source code, so that would be editable in gedit. But with the file located in your home directory it should be owned by you, which means there should be no need to use sudo at all. Don't use sudo when you don't need it, it will cause trouble.

---

### Post by briandennis16 on 2016-06-18
Yes Impavidus it is a C code file, I have just started using linux as my only operating system, which is similar to windows but much different and as for using the cmd I never used it with windows. Is there a good resource that can be recommended for learning the cmd with ubuntu? I am trying to learn it but do not want to mess something up in the process. And would you say Ubuntu is the best to learn Linux Distro on? or Mint? I have only used ubuntu for 3 days? Thanks for the help fellas!

---

### Post by Topsiho on 2016-06-19
There is an excellent book on the Linux command line. See No Starch Press, or duckduckgo for The Linux Command Line.

I don't think that Ubuntu is the best distro for learning Linux, it is too easy. That is just the great thing for Ubuntu, it just works.
See Distrowatch for other Linuxes, which are more difficult to get and keep running :)

Topsiho

---

### Post by briandennis16 on 2016-06-19
Thanks Topsiho,
Yeah I have been using Windows for the longest time and I am finally sick and tired of the force feeding of upgrades and installs they put upon there users and all that stupid crap! I am trying to learn this all over again and I haven't used Linux sense college which was a few years ago, so hopefully using the cmd comes back easily without to much trouble.  And thanks again for the tips on where to find information on the command line for Linux, are there any good apps for smartphones also? I just really need to learn quick as I wiped my windows and took the full plunge and not just attempted it now I have no choice but to learn it! LOL, liking Ubuntu too with It's similarities but better functionality. Again thanks everyone!

---

### Post by Topsiho on 2016-06-20
Hello briandennis16,

The command line is similar to MS-DOS, only very much more powerful. And you need not know everything, depends om what you want to do.
As for force feeding of updates/upgrades, I hope you realize updating your system is very important to help keep it safe and sound. Updating Ubuntu means updating the system AND the installed applications, AND to update or install drivers for new hardware. Fortunately updating Ubuntu is not such a chore as I remember is the updating of Windows: there are very fast servers all over the globe that serve you the updates, so if you have a good internet connection the updates are downloaded in a jiffy, and after that installed. AND you can do that on the background, while you do your more productive things.
While updating sometimes you have to restart the computer, but that is only once in a while, e.g. when updating the linux image itself (the brains of your system). I remember updating Windows and having to restart it umpty times doing so. I hated that.

Don't forget to remove the update files from your hard disk, as if you don't the disk might get congested (full):

sudo apt-get clean
sudo apt-get autoremove

except of course you still need the files.

As for smart phones:I don't know, sorry for that. Might use duckduckgo for that.

Topsiho

---

### Post by vasa1 on 2016-06-20
> **Topsiho said:**
> ....
While updating sometimes you have to restart the computer, but that is only once in a while, e.g. when updating the linux image itself (the brains of your system). ...
More here: [http://askubuntu.com/questions/672223/when-is-it-necessary-to-reboot-an-ubuntu-system](http://askubuntu.com/questions/672223/when-is-it-necessary-to-reboot-an-ubuntu-system)

---

