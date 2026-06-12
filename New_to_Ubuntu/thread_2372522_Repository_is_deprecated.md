---
title: "Repository is deprecated"
date: 2017-09-26
forum: New to Ubuntu
---

### Post by ra.abbasi on 2017-09-26
Hi all,

I'm reading the book *Getting Started with Ubuntu 16.04 *and in a section it guides me to using this command:  
[B]sudo apt-add-repository ppa:ubuntuwine/ppa
[/B]install a repository from the terminal, but I get this message which seems more a warning: [B]
Please note that this repository is deprecated. 

[/B]What should I do please?
Thanks.

---

### Post by westie457 on 2017-09-26
Hello,
If you are looking to specifically add wine to your system go to this page and follow the instructions. [https://wiki.winehq.org/Ubuntu](https://wiki.winehq.org/Ubuntu)

---

### Post by ra.abbasi on 2017-09-27
Thank you. I did it. And is there any command or anything else to see if everything is done correctly?

---

### Post by howefield on 2017-09-27
> **ra.abbasi said:**
> Thank you. I did it. And is there any command or anything else to see if everything is done correctly?

If you haven't already done it you could try a 

```
sudo apt update
```

if in the output you see the wine repository being queried and the command completes without error then all should be well. Out of interest, which windows application is it that you want to install ?

---

### Post by ra.abbasi on 2017-09-30
I did and got this message:

```
abbasi@abbasi-HP:~$ sudo apt update
[sudo] password for abbasi: 
Hit:1 [http://ir.archive.ubuntu.com/ubuntu](http://ir.archive.ubuntu.com/ubuntu) xenial InRelease
Hit:2 [http://ir.archive.ubuntu.com/ubuntu](http://ir.archive.ubuntu.com/ubuntu) xenial-updates InRelease             
Hit:3 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease              
Hit:4 [http://ir.archive.ubuntu.com/ubuntu](http://ir.archive.ubuntu.com/ubuntu) xenial-backports InRelease           
Get:5 [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) xenial InRelease [17.5 kB]
Err:5 [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) xenial InRelease
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9A06AEF9CB8DB0
Hit:6 [https://dl.winehq.org/wine-builds/ubuntu](https://dl.winehq.org/wine-builds/ubuntu) xenial InRelease
Reading package lists... Done
W: GPG error: [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) xenial InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9A06AEF9CB8DB0
E: The repository 'http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu xenial InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
abbasi@abbasi-HP:~$
```

---

### Post by deadflowr on 2017-09-30
Simple.
You need to remove the ubuntu-wine ppa.
```
sudo apt-add-repository -r ppa:ubuntu-wine/ppa
```
the -r sets it to remove.
the rerun the apt-get update command.

---

### Post by ra.abbasi on 2017-10-01
Thanks.

I did the two and now at the bottom, it's written:
[I]325 packages can be upgraded. Run 'apt list --upgradable' to see them

[/I]By the way, it's not possible to see 325 packages! :)

Now what should I do?
Should I issue the command:
***sudo apt-add-repository ppa:ubuntu-wine/ppa***
?

---

### Post by mörgæs on 2017-10-01
What does ```
sudo apt dist-upgrade
``` yield?

---

### Post by deadflowr on 2017-10-01
> **ra.abbasi said:**
> Thanks.

I did the two and now at the bottom, it's written:
[I]325 packages can be upgraded. Run 'apt list --upgradable' to see them

[/I]By the way, it's not possible to see 325 packages! :)
? That's what the apt list --upgradable command does.
> Now what should I do?
Should I issue the command:
***sudo apt-add-repository ppa:ubuntu-wine/ppa***
?
No.
Then you would just be repeating history all over again.

---

### Post by Geoffrey_Arndt on 2017-10-02
If you want Wine . . . you might try installing "PlayOnLinux"

---

### Post by ra.abbasi on 2017-10-02
@[mörgæs]("https://ubuntuforums.org/member.php?u=939075")[COLOR=#000000] :
[/COLOR]
> sudo apt dist-upgrade
I took about 20 minutes and I think many packages were set. This is what written in the end of terminal:

```
Fetched 30.4 MB in 3min 21s (151 kB/s) 
W: Can't drop privileges for downloading as file '/var/lib/update-notifier/package-data-downloads/partial/adobe-flashplugin_20170912.1.orig.tar.gz' couldn't be accessed by user '_apt'. - pkgAcquire::Run (13: Permission denied)
Installing from local file /var/lib/update-notifier/package-data-downloads/partial/adobe-flashplugin_20170912.1.orig.tar.gz
Flash Plugin installed.
Setting up ubuntu-release-upgrader-gtk (1:16.04.22) ...
Setting up flashplugin-installer (27.0.0.130ubuntu0.16.04.1) ...
Setting up update-notifier (3.168.5) ...
Setting up update-manager (1:16.04.9) ...
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20160824-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for libc-bin (2.23-0ubuntu9) ...
Processing triggers for systemd (229-4ubuntu19) ...
Processing triggers for ureadahead (0.100.0-19) ...
Processing triggers for initramfs-tools (0.122ubuntu8.8) ...
update-initramfs: Generating /boot/initrd.img-4.10.0-35-generic
W: Possible missing firmware /lib/firmware/i915/kbl_dmc_ver1_01.bin for module i915
Processing triggers for resolvconf (1.78ubuntu4) ...
abbasi@abbasi-HP:~$
```

Now I don't know if I have Wine ver 1.8.2 app as the book says, installed on the machine or not! :(

And about connecting to this thread through my Windows 7 OS and Ubuntu:
When I come to this thread by windows (by Chrome), it takes about few seconds but when using Ubuntu on my laptop it takes 3 or 4 minutes using Mozilla!
It writes these at bottom:

*connecting to ubuntu. community...  *(I'm sure about this one but it's something like that)[I]
connecting to connect.facebook.net...

[/I]
What can the problem be please, the OS or the browser?

---

### Post by mörgæs on 2017-10-02
Let's wait a moment with Wine. First: You had 325 packages in need of upgrading. This translates to a big security hole. 

It it were my system I would begin with changing all passwords which have been entered and from now on run the two commands every day. 

Did you reboot after the update?

---

### Post by ra.abbasi on 2017-10-03
Linux is really terrible. Now I know why only few percent of people use it and the rest Windows.

---

### Post by mörgæs on 2017-10-03
Windows without the latest 325 security patches would be just as bad. 

Did you reboot?

---

### Post by ra.abbasi on 2017-10-04
I rebooted the machine and reissued the update command. It wrote the packages are up to date. 

I still don't know whether I have *Wine Version 1.8.2* installed or not.
I retried to install it this way:

```
abbasi@abbasi-HP:~$ sudo apt-add-repository ppa:ubuntu-wine/ppa
[sudo] password for abbasi: 
 !!! PLEASE NOTE THAT THIS REPOSITORY IS DEPRECATED !!!

In fact, it's double deprecated -- it was replaced by the Wine Builds PPA, which was then itself replaced.

For more information, please see:

    https://www.winehq.org/pipermail/wine-devel/2017-March/117104.html

The following commands can be used to add the new repository:

    wget https://dl.winehq.org/wine-builds/Release.key
    sudo apt-key add Release.key
    sudo apt-add-repository 'https://dl.winehq.org/wine-builds/ubuntu/'
 More info: https://launchpad.net/~ubuntu-wine/+archive/ubuntu/ppa
Press [ENTER] to continue or ctrl-c to cancel adding it
```

About the difficulty on using Ubuntu, I have problems with Firefox and Ubuntu Software programs. They are too slow. I created [this thread]("https://ubuntuforums.org/showthread.php?t=2372915") to solve it.

---

### Post by mörgæs on 2017-10-04
In post 9 you were advised not to install that package. 

Did you install it or press ctrl+c?

---

### Post by deadflowr on 2017-10-04
If the goal is a specific version of wine, I would not add or use any ppa, and instead follow 
Geoffrey_Arndt's suggestion and install playonlinux.
Playonlinux allows you to install multiple version of wine and they will stay that version for as long as you want.
(ppa's and other 3rd party repository tend to get frequent updates, so even if you install wine1.8.2 from some outside source chances are it'll get updated to another version sooner or later.)

---

### Post by mörgæs on 2017-10-04
Yes, there are many options. 
A fresh install of Buntu 17.04 will come with Wine 1.8.4 without the need for adding PPA's.

---

### Post by ra.abbasi on 2017-10-05
@[mörgæs]("https://ubuntuforums.org/member.php?u=939075")[COLOR=#000000] , @[/COLOR]
[COLOR=#000000][FONT=Ubuntubeta][[COLOR=#C61919]deadflowr[/COLOR]]("https://ubuntuforums.org/member.php?u=1276577") [/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntubeta][/FONT][/COLOR][IMG]https://ubuntuforums.org/images/ubuntu-VB4/statusicon/user-offline.png[/IMG]

> [COLOR=#000000]Did you install it or press ctrl+c?[/COLOR]
No I didn't install it. 


My goal to install *Wine* is just because the book said, other than that I have no goal.
If you disagree, OK, I won't install it as it itself too shows problems. (*Repository is deprecated*)

Instead of that *Wine* which of above do you suggest me. I'm very new on Ubuntu and few days ago I even didn't know what the Terminal is!!

Now I read that book, "*Getting Started with Ubuntu 16.04*" (141 pages) to be familiar with Ubuntu as a very newcomer. I don't know when I might install a windows program on Ubuntu using that tool but I want to have such a tool on my Ubuntu because I have program that sooner or later may want to install them on Ubuntu.


Now I install the app that you suggest me and continue reading the book too. but please also write the command how to install the suggested app as well.

Thanks.

---

### Post by deadflowr on 2017-10-05
> Now I install the app that you suggest me and continue reading the book too. but please also write the command how to install the suggested app as well.
huh?
Which app did you install and which app do you need help installing?

---

### Post by mörgæs on 2017-10-05
I suggest: 
Every day you run the **update** and **upgrade** command.
Have you changed all passwords which have been entered over time?
Only install stuff you need. Small is beautiful. 
When you need something, first search for a real GNU/Linux version. 
Windows programs are last resort
If you need Wine, do a fresh install of 17.04, else 16.04 will do.

---

### Post by ra.abbasi on 2017-10-07
Thanks to both of you.

I went for installing [COLOR=#000000]a fresh install of 17.04:

[/COLOR]```
abbasi@abbasi-HP:~$ sudo apt-add-repository Buntu 17.04
[sudo] password for abbasi: 
Error: need a single repository as argument
abbasi@abbasi-HP:~$ 

```

---

### Post by deadflowr on 2017-10-07
More lost now.
What was this suppose to do?
> sudo apt-add-repository Buntu 17.04
If it was an attempt to install Ubuntu 17.04 then it wasn't ever going to work.
To install 17.04, if not running 17.04 you need to either run a software upgrade.
(If you have the release upgrade option set correctly, then you would get an optional button in the software updater program for upgrading)
Or download 17.04 from Ubuntu.com (currently) and reinstall it like you installed the version you currently use.

---

### Post by ra.abbasi on 2017-10-08
What did Morgaes mean by "[COLOR=#000000]A fresh install of Buntu 17.04 will come with Wine 1.8.4 without the need for adding PPA's.[/COLOR]" in post #19?

Did he mean Ubuntu 17.04!? But the last version of Ubuntu is **16.04.3**


I thought that Buntu 17.04 is like Wine.
I'm confusing

For the fifth time please:
If Wine is deprecated or useless, what other program should I install on my Ubuntu 16.04 x64 to be able to install Windows apps on it too?

For installing that program, what command are needed to be typed on the terminal?

---

### Post by coffeecat on 2017-10-08
> **ra.abbasi said:**
> What did Morgaes mean by "[COLOR=#000000]A fresh install of Buntu 17.04 will come with Wine 1.8.4 without the need for adding PPA's.[/COLOR]" in post #19?

All the flavours of Ubuntu 17.04 - Ubuntu itself, Xubuntu, Lubuntu, Kubuntu, and so on - can install Wine 1.8.4 from the ordinary Ubuntu repositories without you having to add a PPA repository. Wine would be just a few clicks away in whichever package manager the particular flavour of Ubuntu uses.

There is no such thing as "Buntu" . Morgaes was using a shorthand to encompass all the varieties of Ubuntu - Ubuntu itself, and the so-called flavours, such as Xubuntu, Lubuntu, Kubuntu, etc.
> **ra.abbasi said:**
> Did he mean Ubuntu 17.04!? But the last version of Ubuntu is **16.04.3**

Yes, he did mean 17.04. That is currently the latest release, but it is only supported for 9 months from the release time of April 2017. Ubuntu 17.10 will be released in a couple of weeks but it too will only be supported for nine months. Ubuntu 16.04 (and the later point releases) is what is known as a LTS - long term support - and is supported for 5 years.

> **ra.abbasi said:**
> I thought that Buntu 17.04 is like Wine.

Again, there is no such thing as "Buntu". **U**buntu and its cousins, the other flavours such as Xubuntu and Lubuntu, are operating systems. Wine is simply an application which you can install in Ubuntu. It is a compatibility layer which allows you to run some Windows applications (with varying degrees of success) in Ubuntu.

> **ra.abbasi said:**
> I'm confusing

I'm not trying to be unkind here, but you are. It is very difficult to tell what your goals are, and you have frequently failed to answer questions other members have put to you. You seem to have got yourself saddled to a book which recommends installing a non-existent PPA, if I read correctly what you posted, or you have muddled the instructions in the book. At the very least you have become fixated on Wine which, frankly, should be one of the last things a beginner to Ubuntu should worry about - in my opinion.

> **ra.abbasi said:**
> If Wine is deprecated or useless, what other program should I install on my Ubuntu 16.04 x64 to be able to install Windows apps on it too?

Wine is **not** deprecated. You tried to activate a deprecated third-party repository, when it would have been simplicity itself to install Wine from an official Ubuntu repository already enabled on your system. In simple terms: what that book was telling you was unnecessary.  

As far as running Windows programs in Ubuntu, I suggest you don't even try. Use native apps in Ubuntu and native apps in Windows. If you find after running Ubuntu for a while and getting used to it, and you find there is one must-have Windows app you need, then you might need to think about Wine, but there are alternatives, such as running Windows in a virtual machine. If this is your situation, then come here for help. There are plenty of people who are willing to do so.

If, however, there are multiple Windows programs that you need to run, and there are no native Ubuntu apps that are a must for you, then use Windows. In such a situation Ubuntu would not be suited for you.

---

### Post by mörgæs on 2017-10-08
With 'Buntu' I mean any of the Ubuntu/Lubuntu/Xubuntu/Kubuntu... distros. 

The latest stable release of the Buntu family is 17.04, in which the number refers to 2017, 4. month. 

The version of Wine which is part of Buntu 16.04 is old. **IF** you need Wine then I recommend installing Buntu 17.04, erasing the old 16.04 system in the process.

---

### Post by ra.abbasi on 2017-10-08
> **coffeecat said:**
> There is no such thing as "Buntu" . Morgaes was using a shorthand to encompass all the varieties of Ubuntu - Ubuntu itself, and the so-called flavours, such as Xubuntu, Lubuntu, Kubuntu, etc.

It simply makes newcomers of Ubuntu bewildering. 

> I'm not trying to be unkind here, but you are. It is very difficult to tell what your goals are, 

I should try to improve my English. Probably I need to get used to using verbs, pronouns, determiners, adjuncts, complements, and also every primitive rule of English, because I'm not a native English speaker and make others confusing by my sentences. 
So I must have tried for the sixth time this way probably: "If the Wine app is not useful/appropriate/recommended, what other app is useful to be able to install a simple Windows app and using what commands?"


> and you have frequently failed to answer questions other members have put to you. You seem to have got yourself saddled to a book which recommends installing a non-existent PPA, if I read correctly what you posted, or you have muddled the instructions in the book. At the very least you have become fixated on Wine which, frankly, should be one of the last things a beginner to Ubuntu should worry about - in my opinion.

I have left answering no question deliberately. And you too seem to have got yourself saddled to a set of instructions that might not be very helpful for a beginner. My approach for learning computer stuff is reading books. After a good research for a beginner book on Ubuntu, that book was the one I culled.

> **mörgæs said:**
>  **IF** you need Wine then I recommend installing Buntu 17.04, erasing the old 16.04 system in the process.

No need, it's done.

---

### Post by mörgæs on 2017-10-08
Good, back to the questions:

> **mörgæs said:**
> I suggest: 
Every day you run the **update** and **upgrade** command.
Have you changed all passwords which have been entered over time?


The commands to which I referred are ```
sudo apt update
``` and ```
sudo apt dist-upgrade
```.

---

### Post by oldos2er on 2017-10-08
The problem with following books is they quickly become outdated--sometimes as soon as they're published. This is true for open source software in general as well as Ubuntu and its flavors in particular. 

Seeking information online is usually preferable, provided you double-check the date when the information was first written, the Ubuntu version it concerns, and whether it's been updated (or not) in the meantime.

Thank you ra.abbasi for your patience, and for the patience of all our forum members who've taken time to help you. Carry on.

---

### Post by ra.abbasi on 2017-10-09
Of course I appreciate the time folks dedicate to hep me. Thanks and it's done.

---

### Post by linuxissuperawesome on 2017-10-09
If You **Really **Want To Install Wine, Do The Following
```

wget -nc [https://dl.winehq.org/wine-builds/Release.key](https://dl.winehq.org/wine-builds/Release.key) #Wing GPG Key
sudo apt-key add Release.key #Adding The Key To APT
sudo apt-add-repository [https://dl.winehq.org/wine-builds/ubuntu/](https://dl.winehq.org/wine-builds/ubuntu/) #Adding The Repository
sudo apt-get install --install-recommends winehq-stable #Installing Wine

```
And Your System Is Stable. There Is No Need To Update Anything.Remember The Linux Saying
*If It Ain't Broke, Don't Fix It*
But If You Really Want To Update Try:-
```

sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by mörgæs on 2017-10-09
Like all operative system Buntu is broken and needs fixing on a daily basis. Read [here]("https://usn.ubuntu.com/usn/") for a few examples.

---

