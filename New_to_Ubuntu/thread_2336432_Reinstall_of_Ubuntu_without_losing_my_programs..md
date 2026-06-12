---
title: "Reinstall of Ubuntu without losing my programs."
date: 2016-09-08
forum: New to Ubuntu
---

### Post by jacko777 on 2016-09-08
Hello all again, I have solved my earlier problem with great help from the forum.
My next problem is:  How to load a fresh Ubuntu system without losing all my downloaded files and programs.

Is this possible?  If so, I would like to get the step by step instructions.  When I repaired the LOOOONG file name, I have fouled 
something up, and get various errors from first boot to actually using the O.S.
It is not too bad, I am able to mostly ignore the problems and keep on working.  I don't mind making an error or 3 as it helps with the learning curve.

I looked at the starting from a safe boot but can't get the hang of it.  I tried holding the shift at boot time but this didn't work for me, I am therefore asking again for help.

Thank you again,
Jacko777

---

### Post by ian-weisser on 2016-09-08
A proper reinstall erases all contents of the partition. No easy way around it.

The Debian/Ubuntu package system makes reinstalling applications very, very easy, and the LiveUSB can easily be used to back up data, so I'm not sure I understand your trepidation with 'losing' all your downloaded files and programs.

---

### Post by RobGoss on 2016-09-08
I would have to agree there's not really anyway to save your installed programs if you're doing a fresh installation at least I'm not aware of one

I usually can setup a fresh install in just a few minutes Ubuntu makes it quite easy because you can use **synaptic package manager **to grab what ever software program you want installed

It's good practice to just make a list of what's needed then all you have to do is begin installing them until you have everything you need for the system

You can always backup your files and important data you want to save then after the new installation is done just transfer your data over to the new system

---

### Post by bearlake on 2016-09-08
> **RobGoss said:**
> 

You can always backup your files and important data you want to save then after the new installation is done just transfer your data over to the new system

+1

When installing Ubuntu, select something else and create a separate /home partition for all your data.

Then next time you install a newer OS version, choose not to overwrite your /home and all data will remain.

---

### Post by oldos2er on 2016-09-08
You can create a list of all installed programs and use it to reinstall them after reinstalling the OS: ```
dpkg --get-selections > mypackages
``` creates a text file "mypackages" that you then use after your new OS is installed: ```
dpkg --set-selections < mypackages
``` Naturally you'll need to keep the file mypackages on a flash drive or somewhere else safe.

However I think trying to solve your current problems rather than reinstalling the OS would be easier to begin with? > When I repaired the LOOOONG file name, I have fouled 
something up, and get various errors from first boot to actually using the O.S. What exactly was the "repair"?

---

### Post by jacko777 on 2016-09-08
> **oldos2er said:**
> You can create a list of all installed programs and use it to reinstall them after reinstalling the OS: ```
dpkg --get-selections > mypackages
``` creates a text file "mypackages" that you then use after your new OS is installed: ```
dpkg --set-selections < mypackages
``` Naturally you'll need to keep the file mypackages on a flash drive or somewhere else safe.

However I think trying to solve your current problems rather than reinstalling the OS would be easier to begin with?  What exactly was the "repair"?

Hello, the 'repair' was getting rid of an extremely long prompt, it took up most of a line.  To overcome this I edited the BASHRC file.  It fixed the original problem but it seems I went too far and accidentally messed something else somewhere in the program.  
Being totally new to Linux I am bound to muck something up.  Still, having a complete neck full of Mr. Gates' virus, sometimes called an O.S. I made the effort to completely format all my drives and go to a better system where help is freely, and quite friendly given.

Hope this gives you some insight to what I have mucked up.

Jacko777

---

### Post by UltimateCat on 2016-09-08
Would clonezilla be an option?

---

### Post by TheMTtakeover on 2016-09-08
Is there anything particular you are worried about losing?

Out of all of the OSs I use Linux is probably the easiest one to get up and running from a fresh install. You can just apt-get most of what you need.

---

### Post by jacko777 on 2016-09-09
> **TheMTtakeover said:**
> Is there anything particular you are worried about losing?

Out of all of the OSs I use Linux is probably the easiest one to get up and running from a fresh install. You can just apt-get most of what you need.

I have installed quite a bit of software, including Eagle Schematic, the Linux version of office (forgotten its name), I have a large file in Calc that I use to log weather daily.  Also there are many contacts on the Thunderbird mail system that I use to send messages to the members of my volunteer fire brigade, Loads of spec. sheets for electronic components, among others.

I think I would go over the hill trying to remember just what other files I would lose.

I don't think a complete backup would work as it would only restore areas that I have fiddled with, this would only muck up a new installation if I restored it.
There was another suggestion, but I wonder if that would simply do a backup and restore without me being able to pick and choose which files I wanted to restore without getting the ones that I messed up.

regards,   Jacko777

---

### Post by howefield on 2016-09-09
> **jacko777 said:**
> When I repaired the LOOOONG file name, I have fouled something up, and get various errors from first boot to actually using the O.S.

If it is only the fouling up of the .bashrc file that is the root cause of the problem(s), you could revert to a default copy with the terminal command..

```
/bin/cp /etc/skel/.bashrc ~/
```

Now, this will destroy any modifications that you have made to the file, so may be better to take a copy of it first, eg

```
cp ~/.bashrc ~/Documents/
```

---

### Post by oldos2er on 2016-09-09
> **jacko777 said:**
> Hello, the 'repair' was getting rid of an extremely long prompt, it took up most of a line.  To overcome this I edited the BASHRC file. 

A reinstall of the OS is overkill to fixing your .bashrc. See howefield's latest post.

This: > it fixed the original problem but it seems I went too far and accidentally messed something else somewhere in the program concerns me a bit. Are you implying you did something more than edit your .bashrc? What is "the program"? Please remember we only know what you tell us; the more details you can give, the better the quality of help you will receive.

---

### Post by Geoffrey_Arndt on 2016-09-09
Good point by oldos2er . . what other system (non-/home files) were modified or even edited?    

The files mentioned jacko777 such as T-Bird address list and spreadsheet files can be _saved off to a v2 or v3 usb stick in a matter of minutes_.    If you use Gmail or similar web mail, that's not necessary either as that data is saved and available with new installs or even new PC's.   Plus, a normal install of any Linux installs a base of  user programs (such as LibreOffice, Firefox, etc.).   As mentioned already, Synaptic is a package manager that provides a way to install multiple programs in one instance (e.g, at the same time).   

Another solution (for files/data) is offline cloud storage, Dropbox, or SpiderOak or many others.   For many newbie types, offline storage is far safer than data on your local PC (harder to muck up).   And sensitive data can easily be encrypted with the compression program 7zip if nervous about your data (new users really should be more nervous if their data is only on a local hard drive imho).

---

### Post by jacko777 on 2016-09-10
> **howefield said:**
> If it is only the fouling up of the .bashrc file that is the root cause of the problem(s), you could revert to a default copy with the terminal command..

```
/bin/cp /etc/skel/.bashrc ~/
```

Now, this will destroy any modifications that you have made to the file, so may be better to take a copy of it first, eg

```
cp ~/.bashrc ~/Documents/
```

Thank you for that info. it helped, the next item is to overcome the error that comes up before the boot sequence finishes... /home/rod/ .profile: line 23: syntax error: unexpected end of file
I tried to change to this directory but :  " rod@rod-System-Product-Name-Invalid-entry-length-16-Fixed-up-to-11:/home$" ls
rod

take no notice of the long pathname, but when I try to list what is in home$  I get the next line that lists rod, but it is backgrounded with green and is inaccessible.  So I'm once again stuck.
This is indeed a learning curve, but every failure and advice given, I print and save for future reference.  Thank you all for your persistence with a noob. 

Regards,  Jacko777

---

### Post by howefield on 2016-09-10
> **jacko777 said:**
> .. the next item is to overcome the error that comes up before the boot sequence finishes... /home/rod/ .profile: line 23: syntax error: unexpected end of file....

Ok, I'd suggest changing the prompt via the method slickymaster posted [here]("https://ubuntuforums.org/showthread.php?t=2334867&p=13534852&viewfull=1#post13534852") in your previous thread, rather than directly editing the .bashrc file so as to avoid fouling it up once more.

Then to get the .profile file back to default, use

```
cp /etc/skel/.profile ~/.profile
```

but as before, might be best to take a copy of it beforehand with..

```
cp ~/.profile ~/Documents/profile
```

---

### Post by leunam12 on 2016-09-10
There is also a way to do it using synaptic (I have not tried this!)

================

Using Synaptic

Once Synaptic is running, select "Save Markings" from the drop-down File menu. You will be prompted for a location. Obviously, save to a USB stick (and make sure too that you check the box marked Save full state, not only changes otherwise you may create an empty file!).

Installing all that software is simply a matter of opening Synaptic in the other machine or fresh install and this time selecting "Read markings" from the File drop-down menu and selecting that backup and leave Synaptic to do its work. Of course, some of the packages may have been installed via a PPA and that means you'd be well advised to also backup your sources files, which contains a list of all enabled repositories including the PPAs. Synaptic does not have a facility for doing this, so just copy it (as root) with this simple command:

```
cp /etc/apt/sources.list.d ~/sources.list.d.backup
```

and drop the file onto a USB stick and copy it to the same location on the other machine(s). Run Synaptic again and hit the Reload button and the repositories will be read in. that's it!

---

### Post by gacb on 2016-10-28
There's a neat, dead easy to use app called Aptik which backs up all your apps and settings. The latest version of Ubuntu doesn't want to install it via the terminal, but you can get the .deb file on this page:

[http://www.teejeetech.in/2016/04/aptik-v1641.html](http://www.teejeetech.in/2016/04/aptik-v1641.html)

---

