---
title: "Which wine program should I use?"
date: 2012-12-13
forum: New to Ubuntu
---

### Post by flyfishingphil on 2012-12-13
I had tried it before but was unimpressed with its workings. In honesty it may have been more of a problem with "user" abilities that program ability!

There are some things I would like to do, such as have the DirecTV Everywhere workable that require Win$ of some sort, so am considering using Wine again. 

In checking the software center I find wine, Q4wine, Wine windows program launcher, Play on Linux, Winetricks all listed. In reading the reviews it appears they all do the same thing so that's what brings up the questions.

1. Are they all basically the same in what they do?

2. What is the most workable and productive version?

3. Is it advisable to use more than 1 of the choices? (I.E. Should I use a combo like Wine Windows program loader and Play on Linux?)

Any suggestions/help would be greatly appreciated. (Word them for the brain problem viewer!)

Thanks,  Phil

---

### Post by ibjsb4 on 2012-12-13
I find play-on-linux the easiest and works for my simple needs.

---

### Post by Cheesemill on 2012-12-13
+1 for PlayOnLinux

It automatically downloads and configures the correct version of Wine for each of the Windows applications you install.

---

### Post by squakie on 2012-12-13
+1, but keep this in mind:  if any of your equipment is USB (except keyboard, mouse and some printers), and you want to access it in Wine - you can't.

---

### Post by NM5TF on 2012-12-13
> **squakie said:**
> +1, but keep this in mind:  if any of your equipment is USB (except keyboard, mouse and some printers), and you want to access it in Wine - you can't.

which is a good reason to consider running WIN inside a Virtual Machine...

I use Virtual Box to run WIN XP inside Ubuntu 12.04.1 LTS for my on-line
H & S training required by my employer ( it requires IE 8 to work )....

XP loads faster & runs better than a stand-alone install...and ALL my
USB stuff works great!!

for more info on VB, go here:

[https://www.virtualbox.org/manual/ch01.html#intro-installing](https://www.virtualbox.org/manual/ch01.html#intro-installing)


Tommy

---

### Post by Mr. Hibba on 2012-12-13
1.  Q4wine is a graphical user interface for Wine.  I don't usually use it, so I'm not sure how good it is.  Wine Windows Program Launcher should be the Wine program itself.  PlayOnLinux is a package deal that should make using Wine a bit easier.  And finally, winetricks is a little tool used to configure Wine and/or install certain Windows programs easily.

2.  Yeah... I think I'm going to agree with the others and say that PlayOnLinux is probably the least hassle of the ones listed; however, you may want to look into Crossover Linux ([http://www.codeweavers.com/](http://www.codeweavers.com/)), which is a commercial version of Wine, with real tech support, too.  

3. Hmm, it would probably be safe to have all four of the programs that you listed installed at one time, if you want to.  If you decide to go the PlayOnLinux route, though, I'm not sure that you'd really need the others (it might be a good idea to install winetricks, just in case you need it later).

---

### Post by squakie on 2012-12-13
Exactly why I've always used VM's except for a couple of things I used crossover for.  You are 100% correct - MUCH easier and MUCH simpler.  Have a good one! ;)

---

### Post by flyfishingphil on 2012-12-13
> **NM5TF said:**
> which is a good reason to consider running WIN inside a Virtual Machine...

I use Virtual Box to run WIN XP inside Ubuntu 12.04.1 LTS for my on-line
H & S training required by my employer ( it requires IE 8 to work )....

XP loads faster & runs better than a stand-alone install...and ALL my
USB stuff works great!!

for more info on VB, go here:

[https://www.virtualbox.org/manual/ch01.html#intro-installing](https://www.virtualbox.org/manual/ch01.html#intro-installing)


Tommy

Went to Oracle and see there is the new 4.24 version, checked the download and see that it is a .deb file. Don't recall, off the top of my head the steps for installing a .deb file. Where are those? Also, before I get into installing, does it require partitioning during installation, before I install, or what?

Thanks for the tip.

---

### Post by NM5TF on 2012-12-13
the link I referenced contains the info needed to install VB & get it running correctly....it was a no-brainer & worked straight away...
there is a link called "installing VB" on the page...no partition
manipulation involved....it will then show up in the dash if using
Unity....

you WILL need a licensed copy of WIN or you will have to register it after
a 30 day trial....or e-mail me for a "work around" if you have misplaced your key.....

once you have it installed & opened, there is a step-by-step walk thru
to get you going....

let us know how it goes....

Tommy

p.s. you should also install the "guest additions" for VB from the same site...

---

### Post by flyfishingphil on 2012-12-13
NM5TF

OK, went to Oracle and followed suggestions on installing from .deb and all I got from terminal was "not available". Currently doing download of 4.2.4 but was wondering, do I need to install the current version in Software center then do an update?

Thanks again.

EDIT: Never mind! Finished download and clicked "open" and it jumped right in to the Software Center with option to install as usual. Clicked there and it says it is now installed. Will now go look for the "guest additions" and see what I can do there. Once completed I'll need further help re the "Win$" I use. 

Had that in the Toshiba when purchased and don't think I wiped that out when I formatted and went full ubuntu. Might there be a way to get into the "storage" area where the original programming was kept and pull it from there? If not have an older version of XP on cd that I should be able to use, unless the key is no longer usable.

EDIT 2:

Found the "guest additions" in WinXP. Now to see if it recognizes the USB device>Not reading when using USB. "No USB device attached". Suggestions?

---

### Post by Mr. Hibba on 2012-12-13
Pardon me, but wouldn't it probably be easier to use the VirtualBox packages in the Ubuntu repositories rather than installing them manually?  

Also, either way you install it, repartitioning your hard drive shouldn't be needed.  VirtualBox will create a virtual hard drive for the guest Windows OS and it will be formatted from inside the virtual machine.  Your physical disks should be ok the way they are.

---

### Post by NM5TF on 2012-12-13
> **flyfishingphil said:**
> OK, went to Oracle and followed suggestions on installing from .deb and all I got from terminal was "not available". Currently doing download of 4.2.4 but was wondering, do I need to install the current version in Software center then do an update?

Thanks again.

now you've got me wondering....maybe best to install from software center
after all....wonder why it is saying not available???

pretty sure I got it from Oracle, but then I've slept since then;)

---

### Post by NM5TF on 2012-12-13
oh yeah, 1 more little tip...if you want to use your USB devices, which
you most likely want to do, you need to add yourself to the VB users group
by doing this:

```
sudo usermod -G vboxuser username
```

of course, you will substitute your OWN username in the above...

Tommy

---

### Post by flyfishingphil on 2012-12-13
> **NM5TF said:**
> oh yeah, 1 more little tip...if you want to use your USB devices, which
you most likely want to do, you need to add yourself to the VB users group
by doing this:

```
sudo usermod -G vboxuser username
```

of course, you will substitute your OWN username in the above...

Tommy

Forgot to write dow my username!!! It should be "flyfishingphil" but I get

 usermod: group 'vboxuser' does not exist

what did I mess up now?

---

### Post by Cheesemill on 2012-12-13
The group name should be vboxuser**s** not vboxuser.

---

### Post by flyfishingphil on 2012-12-13
> **Cheesemill said:**
> The group name should be vboxuser**s** not vboxuser.

Got the extension installed, did the terminal thing but still can't get "into" the usb. Get this message when clicking on USB


Result Code: 
NS_ERROR_FAILURE (0x00004005)
Component: 
Host
Interface: 
IHost {30678943-32df-4830-b413-931b25ac86a0}
Callee: 
IMachine {22781af3-1c96-4126-9edf-67a020e0e858}

Didn't do restart after installing will try that and see what it does. Still not connecting. Here's what I get on Terminal:

flyfishingphil@flyfishingphil-Satellite-L305:~$ sudo usermod -G vboxusers flyfishingphil
[sudo] password for flyfishingphil: 
flyfishingphil@flyfishingphil-Satellite-L305:~$

Could it be I need to use -C instead of -G? Will try that and see what happens.

Changed it from G to C and got a list of things done in terminal. Will check now and see what happens. Guess the C is not correct here's what showed up. Noticed the "C" invalid.

flyfishingphil@flyfishingphil-Satellite-L305:~$  sudo usermod -C vboxusers flyfishingphil
[sudo] password for flyfishingphil: 
usermod: invalid option -- 'C'
Usage: usermod [options] LOGIN

Options:
  -c, --comment COMMENT         new value of the GECOS field
  -d, --home HOME_DIR           new home directory for the user account
  -e, --expiredate EXPIRE_DATE  set account expiration date to EXPIRE_DATE
  -f, --inactive INACTIVE       set password inactive after expiration
                                to INACTIVE
  -g, --gid GROUP               force use GROUP as new primary group
  -G, --groups GROUPS           new list of supplementary GROUPS
  -a, --append                  append the user to the supplemental GROUPS
                                mentioned by the -G option without removing
                                him/her from other groups
  -h, --help                    display this help message and exit
  -l, --login NEW_LOGIN         new value of the login name
  -L, --lock                    lock the user account
  -m, --move-home               move contents of the home directory to the
                                new location (use only with -d)
  -o, --non-unique              allow using duplicate (non-unique) UID
  -p, --password PASSWORD       use encrypted password for the new password
  -s, --shell SHELL             new login shell for the user account
  -u, --uid UID                 new UID for the user account
  -U, --unlock                  unlock the user account
  -Z, --selinux-user            new SELinux user mapping for the user account

flyfishingphil@flyfishingphil-Satellite-L305:~$

Be back in a bit to check and see if any progress is made.

---

### Post by NM5TF on 2012-12-13
since you did NOT get an error message asssigning your
username to vboxusers, you should be good...

as for the USB error read below...

towards the bottom of this page is a section titled "USB Support"

you might have to play with it a bit, but it will work...go here:

[https://www.virtualbox.org/manual/ch03.html#settings-usb](https://www.virtualbox.org/manual/ch03.html#settings-usb)



Tommy

---

### Post by monkeybrain2012 on 2012-12-13
> **NM5TF said:**
> which is a good reason to consider running WIN inside a Virtual Machine...

I use Virtual Box to run WIN XP inside Ubuntu 12.04.1 LTS for my on-line
H & S training required by my employer ( it requires IE 8 to work )....

XP loads faster & runs better than a stand-alone install...and ALL my
USB stuff works great!!

for more info on VB, go here:

[https://www.virtualbox.org/manual/ch01.html#intro-installing](https://www.virtualbox.org/manual/ch01.html#intro-installing)


Tommy

Well that depends on what you do with wine. I only run a few simple Windows apps, all work perfectly in wine so I don't really care for using VM for them. For one thing vbox is much slower on my machine and many older machines don't even have the specs to run VM.

Also you do have to have a Windows disk to run it in VM.

---

### Post by monkeybrain2012 on 2012-12-13
> **Mr. Hibba said:**
> Pardon me, but wouldn't it probably be easier to use the VirtualBox packages in the Ubuntu repositories rather than installing them manually?  

Also, either way you install it, repartitioning your hard drive shouldn't be needed.  VirtualBox will create a virtual hard drive for the guest Windows OS and it will be formatted from inside the virtual machine.  Your physical disks should be ok the way they are.

You can add the virtualbox ppa following the instructions [http://tech.sixcolumns.com/2012/10/virtualbox-4-2-4-released-with-new-features-install-it-in-ubuntu-12-10/](http://tech.sixcolumns.com/2012/10/virtualbox-4-2-4-released-with-new-features-install-it-in-ubuntu-12-10/)

---

### Post by monkeybrain2012 on 2012-12-13
Just install gnome-system-tools from the Software Centre and then from the Dash (or the menu, depending on your DE) open user and groups, click advanced and add yourself to the vboxusers group. Sometimes command lines are more efficient, but typos can be frustrating if you don't know the exact names of things.

---

### Post by flyfishingphil on 2012-12-13
Thanks for the assists. Getting rummy from too many hours messing with this. Will take a break and get back into it tomorrow and see if I can find the answers. Just checked nm5tf's reference and need to do that I guess before it will accept the usb device.

---

### Post by NM5TF on 2012-12-13
looks like it is my bad Phil....

to add your name to vboxusers you should use this code...

```
sudo usermod -aG vboxusers "your username"
```
your username without the ""....

I forgot the -a switch in previous post...it will "append"
your username to the group....you will also need to log out
& then back in for the change to take place...

sorry for the confusion, but it's been a while since I did it

and then do this:

```
VBoxManage list extpacks
```

you should see something like this:

```
<username>@<hostname>:~$ VBoxManage list extpacks
Extension Packs: 1
Pack no. 0:   Oracle VM VirtualBox Extension Pack
Version:      4.1.14
Revision:     77440
Description:  USB 2.0 Host Controller, VirtualBox RDP, PXE ROM with E1000 support.
VRDE Module:  VBoxVRDP
Usable:       true
Why unusable:
```

 if the usable: = true you are good to go...

Tommy

p.s. I assume that you got my private e-mail earlier??

---

### Post by monkeybrain2012 on 2012-12-13
I think the problem is that you have not installed the extension pack

It says
"Support for USB 2.0 devices, VirtualBox RDP and PXE boot for Intel cards"
[https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)

---

### Post by flyfishingphil on 2012-12-14
> **NM5TF said:**
> looks like it is my bad Phil....

to add your name to vboxusers you should use this code...

```
sudo usermod -aG vboxusers "your username"
```
your username without the ""....

I forgot the -a switch in previous post...it will "append"
your username to the group....you will also need to log out
& then back in for the change to take place...

sorry for the confusion, but it's been a while since I did it

and then do this:

```
VBoxManage list extpacks
```


you should see something like this:

```
<username>@<hostname>:~$ VBoxManage list extpacks
Extension Packs: 1
Pack no. 0:   Oracle VM VirtualBox Extension Pack
Version:      4.1.14
Revision:     77440
Description:  USB 2.0 Host Controller, VirtualBox RDP, PXE ROM with E1000 support.
VRDE Module:  VBoxVRDP
Usable:       true
Why unusable:
```



 if the usable: = true you are good to go...

Tommy

p.s. I assume that you got my private e-mail earlier??

Got the email and answered.

Made the corrections. Did the code and got:

flyfishingphil@flyfishingphil-Satellite-L305:~$ VBoxManage list extpacks
Extension Packs: 1
Pack no. 0:   Oracle VM VirtualBox Extension Pack
Version:      4.2.4
Revision:     81684
Edition:      
Description:  USB 2.0 Host Controller, VirtualBox RDP, PXE ROM with E1000 support.
VRDE Module:  VBoxVRDP
Usable:       true 
Why unusable: 

Still not working but I went to Verbatim and got the impression that it is only usable for Win$ although I have used it in Ubuntu before. It also says that the VBoxUser stil is not operational. Some sort of glitch between point A and point B I guess. 

Giving up for the night.

---

### Post by flyfishingphil on 2012-12-14
It just keeps getting worse. Thought I'd just uninstall it and got nowhere.

sudo ./VirtualBox.run uninstall
[sudo] password for flyfishingphil: 
sudo: ./VirtualBox.run: command not found

Tried to reinstall from software center but it calls for Root password and doesn't accept what I thought was the right one.

Any suggestions on how to recover my Root password, or other methods to uninstall what is there?

Going crazy isn't a good idea but it sure makes life easier!

---

### Post by flyfishingphil on 2012-12-14
OK. Gave up and did a fresh installation of 12.04. Now just need to try and remember what all I had in there before and how to reset the desktop so it appears with the toolbar across the top with the choices of application, etc.

With that in mind I'll mark this one as solved but if you have any helpful suggestions on how to reset the desktop feel free to let me know.

Thanks for the assists.

---

### Post by Derek Karpinski on 2012-12-17
```
sudo usermod -G vboxusers "your username"
```
 
Is where you messed up.
 
if you don't use the -a flag like:
 
```
sudo usermod -aG vboxusers "your username"
```
 
You're removing yourself from all groups, like sudo, admin, "username", etc, and making your only group 'vboxusers'
 
You must use the -a to append.
 
I've been there before, and it's a mess.
 
Take it as a lesson not to copy and paste code into terminal without learning what you're doing.

---

### Post by flyfishingphil on 2012-12-17
I think what happened was the "a" was left off initially in the tip so it got all messed up from there.

Seriously considering trying it again but this time, despite several mentions that the Software Center version is outdated, I will install from the software center, write down every entry I make and read everything more closely, twice, before hitting next or continue.

Mistakes make for great teachers.

---

### Post by Buntu Bunny on 2012-12-17
> **ibjsb4 said:**
> I find play-on-linux the easiest and works for my simple needs.

I didn't know this existed. Thanks!

---

### Post by flyfishingphil on 2012-12-17
> **Buntu Bunny said:**
> I didn't know this existed. Thanks!

I've spent the last few days reading up on all of the choices and came to the conclusion that the only one that will do what I want is either VirtualBox or partiton my hard drive. WINE, PlayOnLinux, and the others allow you to install (some) of the programs you would usually use in Windows but not a full (Win$ 7) program.

I downloaded the VB users manual and will spend a few days reading that over before I make the final choice between that and partitioning. (Big questios is if I can partition easily after installing 12.04LTS or do I have to do it all over again.)

ffp

---

### Post by ibjsb4 on 2012-12-17
Here's a thought.  Spend a few days getting your game plan together and then post it here.

And welcome Buntu bunny  :)

---

### Post by flyfishingphil on 2012-12-18
> **ibjsb4 said:**
> Here's a thought.  Spend a few days getting your game plan together and then post it here.

And welcome Buntu bunny  :)

Will do. I'll try to write down everything I do then build a report on it in case it can help anyone else.

---

