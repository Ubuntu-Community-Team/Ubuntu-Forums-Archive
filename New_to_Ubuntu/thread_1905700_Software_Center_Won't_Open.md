---
title: "Software Center Won't Open"
date: 2012-01-07
forum: New to Ubuntu
---

### Post by hockeykid1022 on 2012-01-07
On Ubuntu 11.10, I click Software Center on the dock and the icon starts to blink, but the program won't open. Does anyone know how to fix this?

---

### Post by jerrrys on 2012-01-07
Open a terminal and enter:

sudo apt-get update

and try the software center again.

if it still will not work; in terminal enter:

software-center

and post any errors you get

---

### Post by hockeykid1022 on 2012-01-07
> **jerrrys said:**
> Open a terminal and enter:

sudo apt-get update

and try the software center again.

if it still will not work; in terminal enter:

software-center

and post any errors you get
When I type in sudo apt-get update, I get this. I've had this error for awhile and it's causing me to not receive updates. Any fix?[IMG]http://i1209.photobucket.com/albums/cc381/hockeykid1022/Greenshot_2012-01-07_21-42-47.png[/IMG]

---

### Post by bluexrider on 2012-01-07
please post ```
cat /etc/apt/sources.list.d/a
```

---

### Post by wildmanne39 on 2012-01-07
Hi, these are the commands you are looking for:
```
cat /etc/apt/sources.list
ls /etc/apt/sources.list.d/
```

You may want to try:
```
sudo rm /var/lib/apt/lists/* -vf
```
The first command will remove the damaged list and when you run the second command it will replace it with a new list.
```
sudo apt-get update
```
First, Thanks

---

### Post by hockeykid1022 on 2012-01-07
> **wildmanne39 said:**
> Hi, these are the commands you are looking for:
```
cat /etc/apt/sources.list
ls /etc/apt/sources.list.d/
```

You may want to try:
```
sudo rm /var/lib/apt/lists/* -vf
```
The first command will remove the damaged list and when you run the second command it will replace it with a new list.
```
sudo apt-get update
```
First, Thanks
I ran the commands and then put in "sudo apt-get update" after that and this came up. It might be the same message from before.[IMG]http://i1209.photobucket.com/albums/cc381/hockeykid1022/Greenshot_2012-01-07_23-34-14.png[/IMG]

---

### Post by wildmanne39 on 2012-01-07
Hi, we need to see all the information from these two commands ```
cat /etc/apt/sources.list
ls /etc/apt/sources.list.d/
``` 
if the second set of commands did not fix it so you will need to post it here by copying and pasting the information using new reply and click # and paste the information between the brackets.
Thank you

---

### Post by hockeykid1022 on 2012-01-07
> **wildmanne39 said:**
> Hi, we need to see all the information from these two commands ```
cat /etc/apt/sources.list
ls /etc/apt/sources.list.d/
``` 
if the second set of commands did not fix it so you will need to post it here by copying and pasting the information using new reply and click # and paste the information between the brackets.
Thank you
Please excuse me, but I'm kind of confused by what you mean. Do you mean everything that pops up in the terminal after I enter the commands? If so, I will make a screencast of what happens when I enter them.

---

### Post by wildmanne39 on 2012-01-07
Hi, yes I do and I gave you directions for coping and pasting it here using code tags, please do not use screenshots they are hard to read and take up a lot of space.
Thanks

---

### Post by bluexrider on 2012-01-08
A screencast won't do it. We need to see the actual output. Copy and past into the message box.

---

### Post by hockeykid1022 on 2012-01-08
After "cat /etc/apt/sources.list":
deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110427.1)]/ natty main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main

After akirad.list
akirad.list.save
and471-kazam-daily-builds-oneiric.list
and471-kazam-daily-builds-oneiric.list.save
cinelerra-ppa-ppa-oneiric.list
cinelerra-ppa-ppa-oneiric.list.save
google-chrome.list
google-chrome.list.save

After "sudo rm /var/lib/apt/lists/* -vf":
rm: cannot remove `/var/lib/apt/lists/partial': Is a directory

After "sudo apt-get update":
E: Type '<html>' is not known on line 1 in source list /etc/apt/sources.list.d/akirad.list
E: The list of sources could not be read.

---

### Post by Old_Grey_Wolf on 2012-01-08
Use this command ```
sudo rm -rf /var/lib/apt/lists/*
``` instead of "sudo rm /var/lib/apt/lists/* -vf" in post #5.

---

### Post by bluexrider on 2012-01-08
> After "sudo apt-get update":
E: Type '<html>' is not known on line 1 in source list /etc/apt/sources.list.d/akirad.list
E: The list of sources could not be read.I would try to comment out the line by inserting "#" at the beginning of line 1 in source list /etc/apt/sources.list.d/akirad.list

then ```
sudo apt-get update && sudo apt-get upgrade
```
If that doesnt work then
```
sudo rm -rf /etc/apt/sources.lists.d/akirad.list
```and ```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by hockeykid1022 on 2012-01-08
I don't know guys, doesn't seem like anything is working. I'm still getting the error message after "sudo apt-get update" which I believe is causing the issues with the Software Center. If nothing else works, I'll probably just reinstall Ubuntu on my VirtualBox. If anyone has anymore suggestions, post them now. If those don't work, I'll reinstall and see if everything will work. I'll post any more problems here.

Thanks for all your help!

---

### Post by Old_Grey_Wolf on 2012-01-08
Are you saying that after doing ```
sudo rm -rf /var/lib/apt/lists/*
sudo rm -rf /etc/apt/sources.lists.d/akirad.list
sudo apt-get update && sudo apt-get upgrade
``` it still didn't work?

---

### Post by hockeykid1022 on 2012-01-08
> **Old_Gray_Wolf said:**
> Are you saying that after doing ```
sudo rm -rf /var/lib/apt/lists/*
sudo rm -rf /etc/apt/sources.lists.d/akirad.list
sudo apt-get update && sudo apt-get upgrade
``` it still didn't work?
No it still doesn't work. The reinstall didn't work either.

---

### Post by bluexrider on 2012-01-08
thats because the command was incorrect


```
sudo rm -rf /var/lib/apt/list/* 
sudo rm -rf /etc/apt/sources.list.d/akirad.list 
sudo apt-get update && sudo apt-get upgrade
```

it was stated **sources.lists** instead of **[COLOR=Red]sources.list[/COLOR]**

Try it again

---

### Post by hockeykid1022 on 2012-01-08
> **bluexrider said:**
> thats because the command was incorrect


```
sudo rm -rf /var/lib/apt/list/* 
sudo rm -rf /etc/apt/sources.list.d/akirad.list 
sudo apt-get update && sudo apt-get upgrade
```

it was stated **sources.lists** instead of **[COLOR=Red]sources.list[/COLOR]**

Try it again
It worked! Thank you so much! So that's it, right? I don't have to do anything else or enter it again?

---

### Post by bluexrider on 2012-01-08
Glad to help you out. Time for a cold one. Please mark this 
(SOLVED)

---

### Post by Geek4096 on 2012-03-04
Well...I was following this thread because I'm having the same problem and the "fix" didn't work for me.

This all happened after installing TreeSheets - don't know if that actually had anything to do with the problem or not.

From a terminal root prompt, software-center does launch, but clicking the Software Center icon on the toolbar only causes it to pulsate, then nothing happens.

Here's the dump from the command prompt:

# software-center
2012-03-04 12:56:50,157 - softwarecenter.ui.gtk3.em - INFO - EM's: 17 15 21
2012-03-04 12:56:50,740 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2012-03-04 12:56:50,799 - softwarecenter.ui.gtk3.utils - INFO - Softwarecenter style provider for radiance Gtk theme: /usr/share/software-center/ui/gtk3/css/softwarecenter.css
2012-03-04 12:56:54,332 - softwarecenter.ui.gtk3.app - INFO - software-center-agent finished with status 0

Any help is much appreciated.

---

### Post by Geek4096 on 2012-03-06
Ok....so I found the problem...and it was caused by installing TreeSheets.  That installation added the following:

In the /etc/apt/sources.list.d  directory, this was added:

private-ppa.launchpad.net_commercial-ppa-uploaders_treesheets_ubuntu.list


Removing this line restored my Software Center funtionality and Softare Updates now works, as well.

---

### Post by MaxxABillion on 2012-03-28
I am having a similar situation, my software store will not open and after entering the      

sudo apt-get update

 this is the error I received:

E:  Type '<!DOCTYPE' is not known on line 2 in source list /etc/apt/sources.list.d/medibuntu.list
E:  The list of sources could not be read.

Any help will be greatly appreciated.  I am an ubuntu newbie and all this is new to me

---

