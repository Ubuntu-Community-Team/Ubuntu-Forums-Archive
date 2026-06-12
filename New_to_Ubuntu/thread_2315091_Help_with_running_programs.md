---
title: "Help with running programs"
date: 2016-02-26
forum: New to Ubuntu
---

### Post by SaPaul on 2016-02-26
Hi Guys. A couple of years ago I heard about Ubuntu. Now I am about 20 years BC (before computers) and understand very little. However I took a PC follwed the instructions and loaded Ubuntu.

brilliant does everything i need it to do except one thing.

[http://www.brokerchoice.net](http://www.brokerchoice.net)

The Cynergiser product available on this page is defying anything that I try. I have tried wine but am unable to get this right.

Please I need help. it is important to me to be able to run this software or i will end up going back to Windows, which i do not want to do.

If any one can help and assist i would be very grateful.

regards

Paul

---

### Post by QIII on 2016-02-26
If this is a Windows program, you have already discovered it will not run natively under Linux  and you have tried Wine.

Wine is hit-or-miss and there is no guarantee every Windows program will run using it.  You can check the database at winehq.com to see if a given Windows program has been tested and how well it rates.  I found no mention of this application, which means it has not been tested.  Since it is not working for you, I would take that to mean that it does not work.

If you really need this application, then using Windows is just fine.  You need to do what you need to do, right?  Who's to judge.

But you also have the option of dual booting so that you can choose to run Ubuntu or Windows at boot -- you don't have to cleave to one or the other as if it were a marriage.  You can also explore the use of a virtualization application to run Windows in a virtual machine without having to give up Ubuntu.

---

### Post by SaPaul on 2016-02-26
Thanks for the reply. Great pity though if I can't get it running.

---

### Post by QIII on 2016-02-26
That may be how it is if it was written for Windows.

Like I said, though:  You can have both Windows and Ubuntu.  :)

---

### Post by Bucky Ball on 2016-02-26
Install Windows as a virtual machine and you can have it all (or dual-boot).

For a virtual machine you need a good amount of RAM as it is shared between the host OS and the guest OS. 4Gb is ok. 2Gb for Win, 2Gb for Ubuntu. 

This link will give you an idea of what Virtualbox is, but you don't need to download it from that website as it is already in the repository (just search in Software Centre).

Good luck.

---

### Post by KenUBF on 2016-03-02
SaPaul,  I agree with Bucky Ball, that a virtual machine would work well if you absolutely don't want to install Windows. I would suggest Virtualbox. However, in my experience, downloading and installing the program from the manufacturer's website would be best: [https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)  The older version did not work well for me from the Software Center. If you have any difficulty installing it there is a .deb file installer I use to make things simpler for me (I am fairly new with Ubuntu myself). It can be found in the Software Center and it is called GDebi Package Installer. This will automate the install process and install all dependencies. It's pretty nice for beginners.   I hope you can get your VM working and make use of your program in short order. Good luck.

---

### Post by Bucky Ball on 2016-03-02
You only need to double click a .deb file and Software Centre will install it for you. You don't need to install Gdebi. :)

---

### Post by KenUBF on 2016-03-02
> You only need to double click a .deb file and Software Centre will install it for you. You don't need to install Gdebi.  True, but by using the Software Center doesn't that install the older version? I could've sworn when I tried that it installed the wrong version. Hmmm.... I'll have to test that out in my VM and try that again. Maybe I can get rid of that program then, save some space. Thanks for the tip!   :- )

---

### Post by Bucky Ball on 2016-03-02
If you have an older version installed, uninstall it first. You may create chaos. It will install whatever .deb you double click. Check the version numbers.

---

### Post by KenUBF on 2016-03-03
> **Bucky Ball said:**
> If you have an older version installed, uninstall it first. You may create chaos. It will install whatever .deb you double click. Check the version numbers.  I just used my Ubuntu VM to install Virtualbox via the Software Center. I remember what the issue was because it seems to have happened again. On the download page it displays a number of Terminal commands and when I tried to install it the first time there were no application icons, nothing. It appears to not have been installed at all. I think my error when doing this the first time was seeing the Terminal commands I was under the impression that this version used only  Terminal commands to control it only because I saw no regular UI to use. I didn't try to reinstall. But this time in the VM I went back to the Software Center and hit Reinstall and that time the icon showed up in the Applications list in the Dash. It was the most recent version too. Cool. You learn something every day! Thanks!    To the OP, you can forget most of my advice and just use the installer from the Virtualbox website to install it direct from the Software Center. It should do it by default when you download it. Once you click on the installer, the Software Center should open and it should begin installing for you. If you run into the same issue I did, just try hitting Reinstall in the Software Center and that should do it. Good luck. Working with virtual machines is very cool. I think you'll enjoy it.

---

