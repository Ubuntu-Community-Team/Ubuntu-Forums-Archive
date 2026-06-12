---
title: "[SOLVED] Upgrade error"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by Troll_the_Great on 2008-06-13
When the system finds an upgrade I get this message from the update manager :"W: Duplicate sources.list entry [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-backports/main Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_hardy-backports_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-backports/restricted Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_hardy-backports_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-backports/universe Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_hardy-backports_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-backports/multiverse Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_hardy-backports_multiverse_binary-i386_Packages)
"
but then, after I click OK, the system updates without any problem.What does this mean I how can I fix it?

---

### Post by Joeb454 on 2008-06-13
Post your /etc/apt/sources.list :)

From a terminal you can ```
cat /etc/apt/sources.list
```

---

### Post by _sphinx_ on 2008-06-13
This is just a warning telling you that you have duplicate entry for repository servers in /etc/apt/source.list file. Just edit that file and get rid of that warning

---

### Post by Troll_the_Great on 2008-06-13
And how can I edit that?I'm new to linux so I need step by step guidance.:)

---

### Post by Joeb454 on 2008-06-13
OK run the following from a terminal (slightly different from the above)

Terminal is located at Applications &#8594; Accessories &#8594; Terminal :) ```
cat /etc/apt/sources.list > ~/Desktop/sources.txt
```

Then upload the "sources.txt" file from your Desktop in another post :)

---

### Post by _sphinx_ on 2008-06-13
OK sorry for that
Press> alt+f2
type> gnome-terminal
then type in the terminal```
sudo gedit /etc/apt/source.list
```
this will open the file for you to edit it. Just go through the file carefully. Lines beginning with # are just comments and you need not worry about that. So see the uncommented lines and if you find some lie duplicate then remove it.

---

### Post by _sphinx_ on 2008-06-13
Make sure you make the back up of that file as pointed by Joeb454. Sorry for that.

---

### Post by Joeb454 on 2008-06-13
Also @_sphinx_ I'd suggest ```
gksudo gedit
``` rather than ```
sudo gedit
``` [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by Sef on 2008-06-13
> sudo gedit /etc/apt/source.list

That is not quite correct. The correct code is

```
gksudo gedit /etc/apt/source.list
```

If you use sudo instead of gksudo, you run the risk of not being able to boot into Ubuntu.

---

### Post by drs305 on 2008-06-13
Well, actually it's:
```
gksudo gedit /etc/apt/source**s**.list
``` ;-)

---

### Post by Troll_the_Great on 2008-06-13
Can't I run a command to remove duplicate entries, rather to try to find them?

---

### Post by _sphinx_ on 2008-06-13
The file should not be having more than 20 line that are uncommented. I think you should see that file.

---

### Post by Joeb454 on 2008-06-13
> **Troll_the_Great said:**
> Can't I run a command to remove duplicate entries, rather to try to find them?

This is why I asked you to post the contents of the file, so other's can look at the file and edit it for you :)

---

### Post by _sphinx_ on 2008-06-13
> **Joeb454 said:**
> This is why I asked you to post the contents of the file, so other's can look at the file and edit it for you :)

I agree :p

---

### Post by Troll_the_Great on 2008-06-13
This is how it looks:

troll@My-precious:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) hardy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) hardy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main restricted #Added by software-properties
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-backports restricted main multiverse universe #Added by software-properties
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security main restricted #Added by software-properties
deb [http://security.debian.org/](http://security.debian.org/) etch/updates main contrib non-free

---

### Post by Troll_the_Great on 2008-06-13
Now what?:)

---

### Post by drs305 on 2008-06-13
Make a backup and open sources.list for editing:
```

sudo cp /etc/apt/sources.list /etc/apt/sources.list-bak
gksudo gedit /etc/apt/sources.list

```

Copy & Paste this to replace your current menu.lst after making a backup of the original:
```

**deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted**
deb-src http://archive.ubuntu.com/ubuntu/ hardy main restricted #Added by software-properties
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ro.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://ro.archive.ubuntu.com/ubuntu/ hardy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ro.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://ro.archive.ubuntu.com/ubuntu/ hardy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ro.archive.ubuntu.com/ubuntu/ hardy universe
deb http://ro.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ro.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://ro.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ro.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://ro.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted #Added by software-properties
deb http://gb.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-backports restricted main multiverse universe #Added by software-properties

deb http://archive.ubuntu.com/ubuntu/ hardy-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy-security main restricted #Added by software-properties
deb http://security.debian.org/ etch/updates main contrib non-free
```

I think I've caught the duplications. 

You may want to comment out the reference in bold type that mentions your cdrom. This will eliminate the request to insert your installation cd any time you wish to update your system. It would make that line look like this:
```
**# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted**
```

---

### Post by Troll_the_Great on 2008-06-13
Thank you all for your help.A question though:how can I put my answer in that...square, the one you all use?

---

### Post by Joeb454 on 2008-06-13
If you use the Advanced Reply method, it's the # symbol in the options :)

If you use quick reply (as I do) it's [ CODE][ /CODE] though obviously without the spaces ;)

---

### Post by Troll_the_Great on 2008-06-13
I'm not sure I understand.... :(. And, by the way, do you know another usefull repositories that I should ad?

---

### Post by Joeb454 on 2008-06-13
If I want to paste a lot of output from the command line etc. or a command I want somebody to enter, I type ```
[ code]<my command goes here>[ /code]
``` like so.

I had to put a space in, to stop the forum formatting it ;)

And I have the backports repository enabled as well, though there's not much in there :)

---

### Post by Troll_the_Great on 2008-06-13
```
<You mean like this?>
``` :)

And what are the backports repositorys?

---

### Post by drs305 on 2008-06-13
> **Troll_the_Great said:**
> . And, by the way, do you know another usefull repositories that I should ad?

The medibuntu repository is popular. It has multitmedia and entertainment packages. To install it, run these two commands.

To add medibuntu to your sources.list run this command. You don't have to open sources.list This command will enter it as the last line:
```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```

Import the medibuntu key and update packages:
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

---

### Post by Troll_the_Great on 2008-06-13
Thx alot for your time.I added the line, but I get this :
```
W: GPG error: http://security.debian.org etch/updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A70DAF536070D3A1
W: You may want to run apt-get update to correct these problems
```
What do this means?

---

### Post by drs305 on 2008-06-13
Here are the lines directly from the medibuntu site:

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

The lines have changed and I incorrectly posted the old ones. These should work and I'll go back and edit the old ones.

Added: :-(

You will have to go back and delete the last line that I had you enter automatically in sources.list
Remove this line:
```
deb http://packages.medibuntu.org/ hardy free non-free
```
The reason for this is that Medibuntu now places it's address in a separate *medibuntu.list* folder in /etc/apt/sources.list.d/ and you would have duplicate entries. Essentially medibuntu wants it's own folder and doesn't want any *medibuntu* listings in sources.list

---

### Post by Troll_the_Great on 2008-06-13
Thx again.I added medubuntu, my question was what do this means:
```
The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A70DAF536070D3A1
```

---

### Post by drs305 on 2008-06-13
You probably got that message before I updated the commands. Some repositories use a security key to verify that the files are coming from the appropriate source. The method of getting the key changed and that is probably why you got the message. 

Running the new commands should work. Don't forget to delete the last line in sources.list (see end of previous post).

---

