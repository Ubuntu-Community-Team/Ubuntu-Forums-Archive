---
title: "How to safely remove hard drive"
date: 2013-05-31
forum: New to Ubuntu
---

### Post by achilles316 on 2013-05-31
So as the title says, how do i safely remove my hard drive? When i plug it in i don't get anything on taskbar or desktop showing that it is plugged in. If i go to prefrences than disks i do see it there. The thing is that it don't give me the option of removing it or ejecting it. Could it be because the entire drive is encrypted with truecrypt?
**UPDATE: Still need help with this.**

Any and all help on this would be appreciated! And yes i have been reading and researching about this for hours and there really don't seem to be any definitive answer.


Since i have your attention. How do i install just the codecs from ubuntu extras package? Chrome already has flash player so no need to install and i don't use java. Not sure what else comes in that package.
**UPDATE: Found how to install just the codecs. Thanks for the help.**

Why the heck does my clock keep freezing? Did i configure it wrong. Here is what i have %I:%m%p and the line below it, %A%x
**UPDATE: Found the problem to this. I just had to capitalize the M and the P.**

BTW: How do you mark a thread as solved? I would like to mark my other thread as solved but don't know how. Thank you for any help!
**Thanks for the help on this Bashing-om**

---

### Post by Bashing-om on 2013-05-31
[COLOR=#000000]achilles316; Hi !

I will take a stab at trying to answer your questions.

1. Not knowing what version or distro you are running the response is equally ambiguous. Look about for a "System Settings" and poke about some more for "removable media" insure the appropriate boxes are checked.
location varies depending on the version, the distribution and the desktop installed.
1a, Never ever never unplug an external device with out "safely removing" //else file system damage will result at some level, depending on what is going on, perhaps disastrous. Happy with your setting ? then -> plug in the device. My preference to see if the system is aware of the external device is -> from desk top: key combo ctl+alt+t yields a terminal; In this terminal type:
```
sudo fdisk -lu
``` if the device is recognized there is one other entry in that output than are internal hard disk(s) in the machine.  

2, extras //Software Center and search on [/COLOR]ubuntu-restricted-extras, else: terminal:
```
sudo apt-get install ubuntu-restricted-extras
```

3. clock:What desk top ya running ? LXDE ? Will have to get back with ya on that - I am booted into xfce presently.

and finally 4.
Interim method:> Go to the first post in your thread. Click on "Edit Post". Now click on the orange "Go Advanced" button. In the advanced editor change the prefix to "SOLVED". Now click on the orange "Save Changes" button.

[INDENT]
let us know how you get on and how else we can help

[/INDENT]

---

### Post by achilles316 on 2013-05-31
> **Bashing-om said:**
> [COLOR=#000000]achilles316; Hi !

I will take a stab at trying to answer your questions.

1. Not knowing what version or distro you are running the response is equally ambiguous. Look about for a "System Settings" and poke about some more for "removable media" insure the appropriate boxes are checked.
location varies depending on the version, the distribution and the desktop installed.
1a, Never ever never unplug an external device with out "safely removing" //else file system damage will result at some level, depending on what is going on, perhaps disastrous. Happy with your setting ? then -> plug in the device. My preference to see if the system is aware of the external device is -> from desk top: key combo ctl+alt+t yields a terminal; In this terminal type:
```
sudo fdisk -lu
``` if the device is recognized there is one other entry in that output than are internal hard disk(s) in the machine.[/COLOR][COLOR=#000000]  

OS:          Ubuntu 13.04
Kernal:     Linux 3.8.0-23-generic (i686)
Compiled:  #34-UbuntuSMP
Desktop Env: LXDE (Lubuntu)

Not sure what else you might need. Let me know and i will look for it.

UPDATE: I tried that [/COLOR]sudo fdisk -lu[COLOR=#000000] in terminal and 2 disks popped up. I take it the first one is the main drive where Lubuntu is installed. And i take it the second one is the external hard drive. So it seems it is recognized. Now just to find a way to safely remove it as i still can't find a way to do so.

>  2, extras //Software Center and search on [/COLOR]> ubuntu-restricted-extras, else: terminal:
sudo apt-get install ubuntu-restricted-extras
[COLOR=#000000] I already installed this. Was wondering how to install only what i need though. Like i said, flash already comes installed with chrome so no need to download again. Java i never use it so will only waste space.[/COLOR]

> 3. clock:What desk top ya running ? LXDE ? Will have to get back with ya on that - I am booted into xfce presently.[COLOR=#000000] Yes LXDE, and i think i found the solution. I just capitalized the M and the P and everything seems to be working fine. For now anyways lol.[/COLOR]

> and finally 4.
Interim method: Go to the first post in your thread. Click on "Edit Post". Now click on  the orange "Go Advanced" button. In the advanced editor change the  prefix to "SOLVED". Now click on the orange "Save Changes" button.[INDENT]
let us know how you get on and how else we can help

[/INDENT]


Thanks, will mark my other thread as solved now. And thank you for the help!

---

### Post by achilles316 on 2013-06-01
No one has an answer for this? Right now it seems the best way to go about it is to turn of the computer and wait for the external hard drive to power down and than unplug it. There has to be another way to do this. 

Anyone? Any ideas? Thoughts?

---

### Post by Rob Sayer on 2013-06-01
I can't directly answer your question.  LXDE is actually the only ubuntu desktop shell I haven't tried.

But google is your friend ... under "lubuntu unmount drive":

[http://askubuntu.com/questions/98784/safely-unmount-external-drive-on-lubuntu](http://askubuntu.com/questions/98784/safely-unmount-external-drive-on-lubuntu)

---

### Post by CatKiller on 2013-06-01
> **achilles316 said:**
> 
Since i have your attention. How do i install just the codecs from ubuntu extras package? Chrome already has flash player so no need to install and i don't use java. Not sure what else comes in that package.

ubuntu-restricted-extras is a metapackage. Its only function is to depend on other packages. If you don't want to install all the packages that it depends on simply install the ones that you do.

---

### Post by rsgangr on 2013-06-01
I have experienced problems with the standard LXDE file manager, PCManFM, when trying to remove external drives. My solution was to install Nautilus and use that instead. In the sidebar of Nautilus, Right-Click on the drive name and the on "Safely Remove Drive" - hope this helps.

---

### Post by achilles316 on 2013-06-01
Thanks guys, the thing is that i think i am doing something wrong as i can't seem to install either udisk or nautilus. Any help would be appreciated!

---

### Post by Bashing-om on 2013-06-01
[COLOR=#000000]achilles316; OK....

What method are you employing to install "udisk" and "nautilus" ?

Is your package manager in shape ?->
```
sudo apt-get update
sudo apt-get upgrade
``` looking to see if there are errors in the package management  acquisition process.
[/COLOR][INDENT=2][COLOR=#000000]
but 1 small step in a process

[/COLOR][/INDENT]

---

### Post by achilles316 on 2013-06-01
> **Bashing-om said:**
> [COLOR=#000000]achilles316; OK....

What method are you employing to install "udisk" and "nautilus" ?

Is your package manager in shape ?->
```
sudo apt-get update
sudo apt-get upgrade
``` looking to see if there are errors in the package management  acquisition process.
[/COLOR][INDENT=2][COLOR=#000000]
but 1 small step in a process

[/COLOR][/INDENT]

Here is what i got at the end after using the sudo apt-get update

  Something wicked happened resolving 'dl.google.com:http' (-11 - System error)

W: Failed to fetch [http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg](http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg)  Something wicked happened resolving 'dl.google.com:http' (-11 - System error)


E: Some index files failed to download. They have been ignored, or old ones used instead.



Here is what i get when i do the upgrade.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by cmcanulty on 2013-06-01
right click drive in file manager and pick unmount or eject

---

### Post by Bashing-om on 2013-06-01
[COLOR=#000000]achilles316 ; Well

Looks like it is a problem with google's updater (not ubuntu directly)...

How bout going into your GUI Software Sources and de-tick in "other"software" the google source.
Now try the updates ya want to do....
later (re)enable google's source and see if there  is still a problem, If so suggest to d/l google's install media once more.
[INDENT=2]
that be my thought

[/INDENT]

[/COLOR]

---

### Post by achilles316 on 2013-06-01
> **cmcanulty said:**
> right click drive in file manager and pick unmount or ejectWould be awesome if i could. Thing is that it don't give me that option or any option for that matter. 

> **Bashing-om said:**
> [COLOR=#000000]achilles316 ; Well

Looks like it is a problem with google's updater (not ubuntu directly)...

How bout going into your GUI Software Sources and de-tick in "other"software" the google source.
Now try the updates ya want to do....
later (re)enable google's source and see if there  is still a problem, If so suggest to d/l google's install media once more.[INDENT=2]
that be my thought

[/INDENT]

[/COLOR]Looks like i installed both udisk and nautilus now. Now though i can' seem to find it anywhere. Man this is so frustrating!!

---

### Post by Bashing-om on 2013-06-02
Hey [COLOR=#000000]achilles316 ;

It takes time to learn a different desktop environment -- why I like the CLI -- no matter what desk top I am on, the CLI remains a constant !

I have LXDE on another install and when I re-boot tonight I will check it out for the particulars as to where Nautilus and udisk launchers are located.[/COLOR][INDENT=2][COLOR=#000000]
yak at ya then

[/COLOR][/INDENT]

---

### Post by ShadowVegan on 2013-06-02
If right clicking the device doesn't give you the option to unmount, you can unmount it in the terminal. Note that you should be right clicking it on the side bar of the file manager (under 'places' or 'directory tree' or something like that), not the part of the window that shows all the folders. To unmount something via the terminal, use [umount](http://manpages.ubuntu.com/manpages/lucid/man8/umount.8.html).

---

### Post by achilles316 on 2013-06-03
> **Bashing-om said:**
> Hey [COLOR=#000000]achilles316 ;

It takes time to learn a different desktop environment -- why I like the CLI -- no matter what desk top I am on, the CLI remains a constant !

I have LXDE on another install and when I re-boot tonight I will check it out for the particulars as to where Nautilus and udisk launchers are located.[/COLOR][INDENT=2][COLOR=#000000]
yak at ya then

[/COLOR][/INDENT]
Okay i don' t know if i am doing something wrong or what but now i get a different error. Here is what i did today.

Did fresh Lubuntu install
Installed Gufw firewall and enabled it.
Downloaded chrome package
Removed chromium through terminal
Installed chrome

Than i ran the command "[COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get update" to see what happened. Everything turned out fine.
[/FONT][/COLOR]Than i installed recordmydesktop, openshot, K3b and libavformat-extras-53. 
Than i ran the command "[COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get update" again and this time i got the following errors.
[/FONT][/COLOR]
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) raring Release.gpg
  Something wicked happened resolving 'extras.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/raring/Release.gpg](http://extras.ubuntu.com/ubuntu/dists/raring/Release.gpg)  Something wicked happened resolving 'extras.ubuntu.com:http' (-11 - System error)


E: Some index files failed to download. They have been ignored, or old ones used instead.

Any ideas?


> **ShadowVegan said:**
> If right clicking the device doesn't give you the option to unmount, you can unmount it in the terminal. Note that you should be right clicking it on the side bar of the file manager (under 'places' or 'directory tree' or something like that), not the part of the window that shows all the folders. To unmount something via the terminal, use [umount]("http://manpages.ubuntu.com/manpages/lucid/man8/umount.8.html").
Could you break this down for me? Remember novice user here. Been using Lubuntu for about 3-4 days barely. I would appreciate it. Thanks!

---

