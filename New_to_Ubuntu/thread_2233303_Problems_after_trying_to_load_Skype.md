---
title: "Problems after trying to load Skype"
date: 2014-07-07
forum: New to Ubuntu
---

### Post by paw2005 on 2014-07-07
Hi, I'm an absolute newby ( 2 months), after years of XP, & would be greatful for help with this.
I used these instructions found on the net to install Skype, (have since bookmarked the correct way off the forum for use once this is sorted .....  oh.. for a restore point: [IMG]http://ubuntuforums.org/images/icons/icon6.png[/IMG]

"Install Skype in Ubuntu 14.04"

"Open a terminal and use the following commands:
sudo sh -c 'echo "deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner" >> /etc/apt/sources.list.d/canonical_partner.list'
sudo apt-get update
sudo apt-get install skype
This will install Skye version 4.2.0.11. Once it is installed, you can run it by typing Skype in Unity Dash. Of course same trick should work on Xubuntu 14.04, Lubuntu 14.04, Kubuntu 14.04 and other Linux variants based on Ubuntu 14.04."

This didn't load Skype, & caused me to loose  access to Synaptic Manager, with this message:

"An error occurred
The following details are provided:

Software index is broken

Go to the repository dialog to correct the problem.
E: Malformed line 1 in source list /etc/apt/sources.list.d/canonical_partner.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report."

I also can't use Lubuntu Software Centre....
This message also appeared, I "think" to do with LSC :

"This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'."

I've tried looking for the info to repair but was unsuccessful....

I'd be happy for any help!
Thanks in advance....

Pete
N.B, Dual Booted with XP, Both were fine until I fiddled with Skype, XP still OK...

---

### Post by mooreted on 2014-07-07
I am not sure why you are going through all that. Skype is already in the Ubuntu repos.

Try this:

sudo rm /etc/apt/sources.list.d/canonical_partner.list

sudo apt-get update

sudo apt-get install skype

---

### Post by Rex Bouwense on 2014-07-07
The error told you what to do.  Go back to Synaptic Package Manager and run it for broken packages.  Anything that is broken, run the repair.

---

### Post by trag on 2014-07-08
Get "Time Shift" to create restore points.

---

### Post by Bucky Ball on 2014-07-08
Welcome. Always look in the repositories first. Skype is a couple of clicks away in the Software Centre or Synpatic Package Manager, whichever you use, or, as I think someone mentioned:

```
sudo apt-get install skype
```

That simple. It's rare the regular user needs to go through the Windows rigmarole to install an app. ;)

---

### Post by SeijiSensei on 2014-07-08
> **paw2005 said:**
> "Install Skype in Ubuntu 14.04"

That's a convoluted way to enable the partner repository.  Open a terminal and type "sudo nano /etc/apt/sources.list".  Then scroll down until you see 
```
#deb http://archive.canonical.com/ubuntu trusty partner
```
Remove the hash mark at the beginning of the line, save the file, then run
```

sudo apt-get update
sudo apt-get install skype

```

You can also use the GUI interfaces to enable the repository.  Find the "Software Sources" option and enable it there.

---

### Post by paw2005 on 2014-07-08
Hi all,
Thanks so much for the advice & tips.

Reg, 
When i try to open Synaptic Package Manager, I have to enter my Password, but then the page comes up blank, with just a block in the middle & the error message, (as below), ... with ***no*** way to access & use  it, .... only to close it down.[IMG]http://ubuntuforums.org/images/icons/icon9.png[/IMG]

[HR][/HR][HR][/HR]> [B][SIZE=2]An error occurred
[/SIZE]
The following details are provided:

E: Malformed line 1 in source list /etc/apt/sources.list.d/canonical_partner.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.
[/B]

[HR][/HR]Also, with: **... Go to the repository dialog to correct the problem.** Where would I find, & be able to access it? Are the repositories in the "SPM"?

Sorry to seem such a "dunce", but I am determined to resolve it, & am learning on the way[IMG]http://ubuntuforums.org/images/icons/icon11.png[/IMG]

Maybe, since it is a new install & not customised to my preferences yet, it might be an idea to uninstall it & do a reinstall from the disc? ... The Partitions have been already been rcreated, but how would I remove Lbuntu from them for reinstalation, ... in a step by step explanation?

Any guidance is greatly appreciated.

Regards Pete

---

### Post by plucky on 2014-07-08
> E: Malformed line 1 in source list /etc/apt/sources.list.d/canonical_partner.list (dist parse)

Open a terminal window and run ```
 sudo rm /etc/apt/sources.list.d/canonical_partner.list
``` and then run ```
sudo apt-get update
```

See if you can now open **Synaptic Package Manager**

If yes, The open the Software Repositories and make sure the "Partner" repository is enabled.

You should then be able to install skype as described above.

Good Luck

---

### Post by paw2005 on 2014-07-08
Thanks trag!;)

---

### Post by paw2005 on 2014-07-08
Hi plucky,
this came up after entry:

user@user:~$ sudo rm /etc/apt/sources.list.d/canonical_partner.list
sudo: unable to resolve host user
[sudo] password for user: 
user@user:~$ 

Any other ideas?
Thanks in advance,
pete

---

### Post by Bucky Ball on 2014-07-08
Just install over the top of what's there. If you choose 'Something Else' at the recovery section of the install, install the OS to the partition with the mountpoint '/'. Leave the rest alone, make sure they are marked 'Do not use' (except /swap and /home if you are running that way) and make sure they are not ticked to format. 

It appears from the errors you're getting something is odd with your install. 

This:

```
sudo: unable to resolve host user
```

... is not normal on a fresh install. Maybe the attempted Skype install has screwed things or a dodgy install.:-k

---

### Post by paw2005 on 2014-07-08
Yep Bucky,
But my problems appear to be solved when I did a Software Update!:p
Can now use SPM.
Will install TimeShift restore point app, so the next time I mess-up I can go back....
Is TimeShift OK for this pupose (simple to use), or any other suggestions?
Thanks Stax for your help...
Regards
pete

---

### Post by Bucky Ball on 2014-07-08
> **paw2005 said:**
> 
Is TimeShift OK for this pupose (simple to use), or any other suggestions?
Thanks Stax for your help...
Regards
pete

This is the stuff of a new support request on a new thread and off-topic on this one. A new thread will improve your chances. Please mark this one as solved.

Thanks and enjoy. ;)

---

### Post by paw2005 on 2014-07-08
Appreciated Bucky!
Cheers!
pete

[ 						 					]("http://ubuntuforums.org/member.php?u=698195") 				 				 					 						Thanks     [**[COLOR=#000000]SeijiSensei[/COLOR]**]("http://ubuntuforums.org/member.php?u=698195")  !

Thanks mooreted !!

Thanks Rex!

---

### Post by bbrannock on 2014-07-24
[[COLOR=#000000]mooreted[/COLOR]]("http://ubuntuforums.org/member.php?u=125614")

thank you thank you  
I installed skype off skypes website it worked but made software center stop working. I uninstalled skype and software center was not working.
my software center would open and close in seconds.

[COLOR=#000000]sudo rm /etc/apt/sources.list.d/canonical_partner.list
[/COLOR][COLOR=#000000]sudo apt-get update
fixed it 

thank you one more time

Bruce

btw do you all know a safe skype to run. I am running 14.04 LTS 64 bit[/COLOR]

---

### Post by Bucky Ball on 2014-07-24
This was stated at the beginning of this thread: install Skype from the Software Centre.

---

