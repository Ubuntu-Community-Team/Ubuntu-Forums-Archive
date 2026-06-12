---
title: "Some noob questions."
date: 2019-05-29
forum: New to Ubuntu
---

### Post by sigurdsk on 2019-05-29
I have some questions so I can get started.
1. My graphics are not set up i think
 1.1 How do i set screen resolution?
 1.2 I have NVidia Gforce GTX 960, where are the correct drivers and how do I install them?
2. I need to see my partition table.
 2.1 How can I view the HardDrives and Partition Tables on this computer?
 2.2 How can I access what is Ubuntu "Device Manager"?
2.3 How can i shrink my Swap space, and how do i activate it?

Another think I was thinking about is that I have my own business. But it is fuzzy to me how
UBUNTU One handles things. Like applications. 
1. I see that it is a sign-on service so i wonder..
 1.1 The passwords in my FireFox browser are stored, is that on UBUNTU One or the Browser?
 1.2 I see an "applications" list, is this so that all my UBUNTU applications can log on if i somehow add the application here? And if so HOW do i add the application?
1.3 Really just general information about how the system works and not too technical, put it simple :D
2. I see there are an "Applications" list on the side of 
For now theese are my main issues, and I hope to get started as soon as possible :KS As i allready have an opinion
about weather or not to use it.. If there are no needs or desires in my CO i will just leave it as is.

I would also need to know (for practical reasons, so I do not have to boot into BIOS or change boot settings when
I boot my computer. I have no selection menu for choosing Windows even thou i selected the installation to go 
along side Windows 10.) How may i get the settings back? Either from Windows or UBUNTU. Thanks :KS

---

### Post by Bashing-om on 2019-05-29
sigurdsk; Hello
1)
```

sudo lshw -C display

```
look in the configuration line for the module that is loaded.
1,1)
The kernel sets the resolution - Dynamic Kernel Mode Setting (DKMS)
Additional drivers tool in software sources to install a different driver.
1,2)
nvidia recommends the 430 version driver:
[https://www.nvidia.com/Download/driverResults.aspx/147582/en-us](https://www.nvidia.com/Download/driverResults.aspx/147582/en-us)
what shows :
```

sudo ubuntu-drivers list

```
2.1) Partition table:
```

sudo fdisk -lu
sudo parted -l

```
2.2)
Sorry - can not relate to "Device Manager"
What info do you require ?
2,3)
partition management is best done with the tool 'gparted' in the GUI.
what shows:
```

swapon --summary

```

[INDENT][INDENT]my bit to try and help[/INDENT][/INDENT]

---

### Post by sigurdsk on 2019-05-29
Thank you so much for helping me getting started (I cannot see your name but you know who you are)!
I will keep this like a noob thread and be keeping it active while I learn ;)
I will read the last link you sent me after I install graphic drivers, I cannot allmost see anything and I guess
RefreshRate or what you call it is not at all good LOL.
:guitar:

---

### Post by sigurdsk on 2019-05-29
the sudo ubuntu-drivers list show me nvidia-driver-390, wierd that I cannot change resolution settings? But anyhow I 
will be installing those recommended drivers, as soon as FireFox lets me LOL. It is not easy with this BIG screen resolution.

---

### Post by sigurdsk on 2019-05-29
I am posting regarding the NVidia driver and UBUNTU.
How do UBUNTU handle .run files? Is this standard for UBUNTU or is it just an executable named .run?
How may I run it from a Terminal? You see.. I tried to do a .\NVI and press the TAB key but nothing happens.
Curious as to what .run files are, what standard UBUNTU packackes are and I NEED to know how to run this 
file :KS
UPDATE: I read that you could type sh <filename>, but why is not TAB-completion working in terminal? The graphics are messed thou.
UPDATE 2: It ran, but i had to rename the file i somehow got it to n.run and then i could do sudo sh n.run and trying to install drivers. I am not able to do the "make it so a new kernel will not need new installation" thing, trying without that!
UPDATE 3: CC Check failed (I can provide more information). I am not sure how much longer I can ignore theese messages before it causes a serious issue!! The second message is that it asks me if i want to sign the kernel driver. Do I want that? Ahm.. Further it generated a Key Pair and also a certificate needed to be added to the local database.. OMG this is so advanced I just wanna cancel this and re-install without any certificate!!

---

### Post by sigurdsk on 2019-05-29
Can you check my last thread please? TY for your answer btw! Helps me out a lot!:KS

---

### Post by sigurdsk on 2019-05-29
Hi!
I just installed UBUNTU and got some help for the "New to UBUNTU" so I downloaded NVidia drivers, and are now
installing them. This is what i wonder about, it asked me if i wanted to sign the kernel driver. I clicked yes, as thou i get
many questions like "gcc was older than the gcc for this module" etc. But I wonder, this is super geeky, but it say that it has Signed the module, generated a key pair and then a certificate. But I am scratching my head when it say to add the key to a database in order for the Kernel to be able to verify the module signature. Now, I could just say, wait.. This is too advanced I am canceling this and reinstalling without signature. But you know what.. I am curious by nature.. So if it is anyone who can help me "add this key to the database" and explain to me how it works, like generally I know about the Windows side of things like the GPO (I am guessing it is kinda the same).. But if anyone thinks I can to this, please enlighten me :KS Nice to be here on the forum!
 - I guess some of the fun with linux is learn by typing. I could search up and learn about X.509 certificates, the learn about the SHA1 fingerprint and then learn what the kernel database really is.. That is what i loved about Linux in the old days, figuring things out :popcorn: Sitting here and no sound on speakers, so i will be just reading..

Got the basic understanding of what X.509 is and what SHA1 is and what the kernel database is, well adding a driver to the kernel database seems really too complicated. 
QUESTION: Should i just restart the installer and run it unsigned?? OFFCOURSE when I think in terms of Windows, i didnt bother to sign drivers I trusted?!?! DAH!

---

### Post by sigurdsk on 2019-05-30
Hi!
I have updated the drivers now, I hope everything went well.
My screen has this BIG resolution and slow response time..
Seems like something is wrong, but it could be the settings. So, here is another noob question.
How do I access the display settings? Like, all of them, for the adapter?

---

### Post by wildmanne39 on 2019-05-30
We allow one topic per thread so please start a new thread for each question but only one thread for each question and not multiple threads on the same topic, by that I mean if you have a question about installing the nvidia driver and it concerns secure boot, you do not need to ask one question for signing the module and then start a new thread to ask if secure boot needs to be enabled both questions would be okay in the same thread as they are related if it is a completely different then you need to start a new thread, in fact it would be best to edit the thread that talks about the module needing signed and add does secure boot really need to be enabled.

If you do not receive a reply to your thread in 12 hours you can bump it by just posting bump to keep it in view of the volunteers answering questions. Also please use a descriptive title when you start your thread so the volunteers and the people searching the internet for solutions will know what the thread is about.

Please read the posting guidelines in my signature.

Thanks

---

### Post by CatKiller on 2019-05-30
> **sigurdsk said:**
> I have some questions so I can get started.
1. My graphics are not set up i think
 1.1 How do i set screen resolution?
The Display part of the Settings.
> 1.2 I have NVidia Gforce GTX 960, where are the correct drivers and how do I install them?
The Additional Drivers tool will download the proprietary driver from the repository. You may also add the graphics-drivers PPA if you would like to use a newer version than the one in the repository.
> 2. I need to see my partition table.
You probably don't.
>   2.1 How can I view the HardDrives and Partition Tables on this computer?
Already answered by Bashing-om.
>   2.2 How can I access what is Ubuntu "Device Manager"?
There isn't one.
>  2.3 How can i shrink my Swap space, and how do i activate it?
You don't. The defaults are much more sensible than the intuitions of a Windows user. Things that you've been conditioned to believe, from using Windows, about how to use a computer are entirely wrong. You will only cause yourself problems by not realising that.

> I would also need to know (for practical reasons, so I do not have to boot into BIOS or change boot settings when
I boot my computer. I have no selection menu for choosing Windows even thou i selected the installation to go 
along side Windows 10.) How may i get the settings back? Either from Windows or UBUNTU. Thanks :KS

There is every chance that you've nuked your Windows install. Installed correctly, you would already have that menu at boot. Windows' settings default to *destroy Windows if Linux is installed* and, if you change them, revert to that on Windows updates.

> **sigurdsk said:**
> I am posting regarding the NVidia driver and UBUNTU.
How do UBUNTU handle .run files?
Perfectly well.
>  Is this standard for UBUNTU or is it just an executable named .run?
It's just a file named .run. Whether it's executable or not depends on the permissions that are set for it.

>  How may I run it from a Terminal?
You don't. Thinking that you need to download an executable from some random website is **exactly** the kind of false intuition that will cause you problems.

>  You see.. I tried to do a .\NVI and press the TAB key but nothing happens.
Filenames are case-sensitive.

>  Curious as to what .run files are, what standard UBUNTU packackes are and I NEED to know how to run this 
file :KS
No, you don't. Packages are installed through a package manager. Installing random stuff that you found on a website is **A Bad Plan**.

> UPDATE: I read that you could type sh <filename>, 
Don't do that, either

> but why is not TAB-completion working in terminal?
It is.

> The second message is that it asks me if i want to sign the kernel driver. Do I want that? Ahm.. Further it generated a Key Pair and also a certificate needed to be added to the local database.. OMG this is so advanced I just wanna cancel this and re-install without any certificate!!
[Secure Boot]("https://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface#SECURE-BOOT"). Installing the driver from the repository will automatically sign the kernel module if you're using Secure Boot. The driver from the PPA will not sign the kernel module; you'll need to sign it yourself if you need it signed. Installing random stuff that you found on a website is **A Bad Plan**.

---

### Post by mastablasta on 2019-05-30
to install nvidia drivers, you open additional drivers application, select the recommended ones and install them. for example: [https://itsfoss.com/install-additional-drivers-ubuntu/](https://itsfoss.com/install-additional-drivers-ubuntu/)

you can also add PPA if you wish and if you need some newer version. for example: [https://www.mvps.net/docs/install-nvidia-drivers-ubuntu-18-04-lts-bionic-beaver-linux/](https://www.mvps.net/docs/install-nvidia-drivers-ubuntu-18-04-lts-bionic-beaver-linux/)

just remember - new doesn't always mean better.

---

### Post by Autodave on 2019-05-30
You are definitely going about this the hard way.  Can you give us some specs on the machine that you are trying to install the drivers on?

---

### Post by CatKiller on 2019-05-30
> **Autodave said:**
> You are definitely going about this the hard way.  Can you give us some specs on the machine that you are trying to install the drivers on?

It's all the same stuff as their other thread.

---

### Post by oldos2er on 2019-05-30
Threads merged. Please don't create more than one thread for your question, it creates confusion for those trying to help.

---

### Post by DuckHook on 2019-05-30
This is a technical help forum. Here, we deal with specific technical problems.

What you are asking for is the equivalent of a course in Ubuntu. Even were the members here willing, the specific medium on which the forum is based is not conducive to such exchange.

I recommend that you start with [this website]("https://ubuntu-manual.org/"). [The Ubuntu Manual Project]("https://ubuntu-manual.org/") is based on Xenial (16.04), but 95% of it is still relevant to Bionic. The book is licensed under a Creative Commons license, so is free to download and peruse at your leisure.

After you finish with that, there are a ton of resources within the link in my sig: ***Resources for Newcomers***.
> **sigurdsk said:**
> …Really just general information about how the system works and not too technical, put it simple…
This is the reason for my reply. It is not possible to fulfill this request. It is like asking for "general information about how a nuclear power plant works…" There is no possible way for anyone to fill you in on a topic so vast. You must be prepared to do your own research. The links mentioned will get you started, but it is not reasonable to expect others to read your mind, figure out where the knowledge gaps are, then fill them in for you.

Good Luck and Happy Ubuntu-ing!

---

### Post by Bashing-om on 2019-05-30
sigurdsk; Hello Again :)

In addition to the most excellent advises given, May I re-direct your thought processes. This is open source where "you" have complete control over the operating system.
Let's reset your thinking:
[https://ubuntuforums.org/showthread.php?t=2380629](https://ubuntuforums.org/showthread.php?t=2380629)
[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)
[http://ubuntuforums.org/showthread.php?t=2125370](http://ubuntuforums.org/showthread.php?t=2125370)
[http://ubuntuforums.org/showthread.php?t=2200144](http://ubuntuforums.org/showthread.php?t=2200144)
[http://ubuntuforums.org/showthread.php?t=2201432](http://ubuntuforums.org/showthread.php?t=2201432)
[http://ubuntuforums.org/showthread.php?t=2241160](http://ubuntuforums.org/showthread.php?t=2241160)
[http://www.itworld.com/operating-systems/347533/ubuntu-guide-displaced-windows-users](http://www.itworld.com/operating-systems/347533/ubuntu-guide-displaced-windows-users)

Yep - correct - there is a learning curve -when you get beyond point-and-click-  as "this ain't Windows". All of us have been there and we do understand the bewilderment and frustration. Give it some time and effort and you will begin to understand.

We are here to help. As you have a question, open up a new thread on each separate issue that you encounter.

[INDENT]open source !
[INDENT][INDENT][INDENT]we are all in this together
[/INDENT][/INDENT][/INDENT][/INDENT]

---

