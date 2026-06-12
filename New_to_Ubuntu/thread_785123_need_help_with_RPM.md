---
title: "need help with RPM"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by fmpfmpf on 2008-05-07
hello everyone. this is my 1st Linux experience....so pls dont laugh.
My question is, how do i install the RPM?
i am using Ubuntu 7.10

i typed this in the terminal:-
sudo apt-get install rpm

and this is what i got:-
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

then i type this again:-
sudo apt-get install rpm

and the reply is:-
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package rpm is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or is only available from another source
E: Package rpm has no installation candidate

i am installing drivers for a touch screen monitor.
[http://www.elotouch.com/Support/Down...dnld.asp#linux](http://www.elotouch.com/Support/Down...dnld.asp#linux)

i am using the Unified_Serial_Source.zip

What should i do?

thank you in advanced

---

### Post by Xiong Chiamiov on 2008-05-07
RPM is a file extension used by Red Hat for installation files.  Although it is possible to install software on Ubuntu that ends in .rpm, it is not recommended.  Rather, you should first look in Synaptic, then for a .deb, then compile from source.  There is an excellent guide you should take a look at [here]("http://monkeyblog.org/ubuntu/installing/").

EDIT: And that said, there is no need to apologize.  All of us were new at some time (January for me), and there are many things that are quite different than what we were used to...

---

### Post by seshomaru samma on 2008-05-07
What is RPM?

Do you mean Red Hat programmes ?
You can install Red Hat software (RPMs) with Alien
```
sudo apt-get install alien
```

---

### Post by mapes12 on 2008-05-07
RPM is the Redhat Package Manager protocol and is not supported in Ubuntu. Redhat based distros use RPM. Ubuntu is based on Debian and uses the Aptitude protocol. Call up a terminal window: "man apt-get" for the full command switches. Either way, from your desktop: System / Administration / Synaptic Package Manager should do the job. Make sure you have all the repositories you need configured into your system.

---

### Post by nebu on 2008-05-07
u can use alien to convert rpm files to deb files which work on your ubuntu system

first install alien....> 
$sudo apt-get update
$sudo apt-get install alienthen use alien to convert the rpm to a deb file> 
$sudo alien -k name-of-rpm-file.rpmthen install form the deb file...> 
$sudo dpkg -i name-of-deb-file.deb

---

### Post by kestrel1 on 2008-05-07
The only RPM I know of is an .rpm file, that are packages used to install programs on some Linux systems. Ubuntu is Debian based & uses .deb files, although you can convert .rpm's to .deb if you are unable to install the source files.
What are you actually trying to do?

---

### Post by warbread on 2008-05-07
In terminal, go to the directory with the .rpm file and type:

```
:-$ sudo apt-get install alien
:-$ alien -d FILE.rpm
```

This will turn the .rpm file into a .deb file, which Ubuntu uses.  It will appear in the same directory.  Double click on it, or type into the terminal:

```
:-$ sudo dpkg -i FILE.deb
```

---

### Post by Xiong Chiamiov on 2008-05-07
Ah no!  Alien bad!  Unless you have absolutely no other choice, building (preferably with checkinstall) is a much better option from what I've seen.  Alien always seems to have problems.

---

### Post by mapes12 on 2008-05-07
I agree with Xiong Chiamiov. Don't use alien. You will screw up your system. Stay with native .deb packages from the repositories. What are you trying to install??

---

### Post by fmpfmpf on 2008-05-07
ok, so how do i install this deb file?
should i tpye something like sudo apt-get install deb?

thank you

---

### Post by fmpfmpf on 2008-05-07
I am using Ubuntu 7.10
i want to install some drivers, and i have obtained the drivers from the company's website.
The problem is, Ubuntu runs with .deb, but the drivers provided are .rpm
what should i do?
i have tried searching for the .deb drivers in Synamptic Package Manager, but no result

thank you very much

---

### Post by pedro_orange on 2008-05-07
> **fmpfmpf said:**
> I am using Ubuntu 7.10
i want to install some drivers, and i have obtained the drivers from the company's website.
The problem is, Ubuntu runs with .deb, but the drivers provided are .rpm
what should i do?
i have tried searching for the .deb drivers in Synamptic Package Manager, but no result

thank you very much

What sort of drivers are we talking about here?
What hardware are we trying to install?

---

### Post by fmpfmpf on 2008-05-07
i am installing drivers for a touch screen monitor.
[http://www.elotouch.com/Support/Downloads/dnld.asp#linux](http://www.elotouch.com/Support/Downloads/dnld.asp#linux)

i am using the Unified_Serial_Source.zip

thank you

---

### Post by brettg on 2008-05-07
You need to convert rpm to deb;

sudo alien --to-deb filename.rpm --scripts

If alien is not installed (it's not by default) you need to enable the multiverse repo (or maybe universe) and do;

sudo apt-get install alien

---

### Post by MaindotC on 2008-05-07
If the drivers are in .rpm format you can convert them to .deb installers using a program called alien.  Alien is available in the repositories.  When it is installed, you should be able to extract and conver them using [this thread]("http://howtoforge.com/converting_rpm_to_deb_with_alien")

---

### Post by SupaSonic on 2008-05-07
I think you should use this (taken from the link you gave):
> 
Using the Linux Package Manager:

    * Log in on the e-services page, then click the Download Linux Driver link to assemble and download the driver package. 

It says
> 
Pre-built binaries for popular Linux distributions. 


So there's a good chance there is a deb for Ubuntu. It's definitely better than using alien.

---

### Post by Joeb454 on 2008-05-07
There's [another thread]("http://ubuntuforums.org/showthread.php?t=785123") on this - whereby people have already recommended AGAINST using Alien - it always results in issues :(

Oh and to the OP - it's against the Forum CoC (Codes of Conduct) to post duplicate threads - just a heads up)

---

### Post by MaindotC on 2008-05-07
Thank you for brining this to my attention.  I've never had any problems with alien.

---

### Post by MaindotC on 2008-05-07
Once you have created the .deb file you can view it in a file browser, right click it, and select "open with debian package manager".

From the command prompt, you can type:

[code]
dpkg -i <filename.deb>
[code]

---

### Post by mapes12 on 2008-05-07
If you mean the the Synaptic Package Manager then it's already on your system: System / Administration / Synaptic Package Manager.

If you mean a specific package which one are you trying to install??

---

### Post by fmpfmpf on 2008-05-07
> **SupaSonic said:**
> I think you should use this (taken from the link you gave):

It says


So there's a good chance there is a deb for Ubuntu. It's definitely better than using alien.

i dont seem to able to find "Pre-built binaries for popular Linux distributions."

thank you

---

### Post by jong2x on 2008-05-23
i need help with .rpm i'm using ubuntu this is my first time using linux o.s. ... i downloaded xmms but i can't change the file to .deb and i don't know what i'm doing wrong... help... thanks...

james@james-laptop:~$ sudo alien -d xmms-kde-3.1-2-redhat9.i386.rpm
[sudo] password for james: 
File "xmms-kde-3.1-2-redhat9.i386.rpm" not found.
james@james-laptop:~$ sudo alien -d xmms
File "xmms" not found.
james@james-laptop:~$ sudo alien -d xmms.rpm
File "xmms.rpm" not found.
james@james-laptop:~$ sudo alien -k xmms-kde-3.1-2-RedHat9.i386.rpm
File "xmms-kde-3.1-2-RedHat9.i386.rpm" not found.

haha... it's obvious that i don't know what i'm doing haha...

---

### Post by brettg on 2008-05-23
Is the rpm actually in the folder you are working in?

ls -al *rpm

If your alien command returns "File not found" then you are probably mistyping something, use wildcards to reduce this possibility

sudo alien --to-deb --scripts xmms*

Note: xmms has been undeveloped for quite some time now which is why it has been dropped from the reps. Audacious is a fork of xmms and uses many of the same skins and plugins.

sudo apt-get audacious

---

### Post by jong2x on 2008-05-24
i downloaded xmms to my desktop.
i tried what you said but it's still saying file "xmms" not found

i'll try to download audacious manually
i also tried,
james@james-laptop:~$ sudo apt-get audacious
E: Invalid operation audacious

---

### Post by brettg on 2008-05-24
Sorry, my bad,

sudo apt-get install audacious

That's what you get for posting late at night after imbibing a few sherberts I guess :-)

---

### Post by Raccoon1400 on 2008-05-24
> **fmpfmpf said:**
> ok, so how do i install this deb file?
should i tpye something like sudo apt-get install deb?

thank you

click on the deb file you downloaded, and then gdebi should open and let you install it. Is the package available in synaptic or add-remove programs?

to use apt-get, type
apt-get install, then the name of the program, not package format. Note: must be exact package name.

---

### Post by jong2x on 2008-05-24
thanks :)

i've already installed it and found a guide how to install things

---

