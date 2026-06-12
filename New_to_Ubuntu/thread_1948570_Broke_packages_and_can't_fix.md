---
title: "Broke packages and can't fix"
date: 2012-03-28
forum: New to Ubuntu
---

### Post by awe1 on 2012-03-28
This is my first post... I am too dumb but determined to use Ubuntu so I paid a  professional to install it for me (dualboot 11.10 with Win7). When I  came home I got a lot of things from the software center. Skype did not  have a download button so I googled it and Ubuntu help told me to do  this:
  ```
sudo add-apt-repository "deb http://archive.canonical.com/ $(lsb_release -sc) partner"
```   and then this:
  ```
sudo apt-get update && sudo apt-get install skype
```   The terminal told me "that this is potentially harmful..." but I thought it was Ubuntu language meaning "are you sure?"
  Now the computer is mute.
  Items cannot be installed or removed until the package catalog is  repaired, so I want to repair it but the package operation fails.
  "sudo aptitude -f install" -> command not found
  Synaptic package manager tells me that I have two broken packages, libc6 and libc6-dev 
  so I do this:
  ```
 sudo apt-get update && sudo apt-get upgrade 
```   which tells me to do this:
  ```
 sudo apt-get -f install 
```   that ends up like this:
  > Can't exec "locale": No such file or directory at /usr/share/perl5/Debconf/Encoding.pm line 16.  Use of uninitialized value $Debconf::Encoding::charmap in scalar chomp at /usr/share/perl5/Debconf/Encoding.pm line 17.  Preconfiguring packages ...  dpkg: warning: 'ldconfig' not found in PATH or not executable.  dpkg: error: 1 expected program not found in PATH or not executable.  Note: root's PATH should usually contain /usr/local/sbin, /usr/sbin and /sbin.  E: Sub-process /usr/bin/dpkg returned an error code (2)   When fixing broken packages in synaptic package manager I get this:
  > Preconfiguring packages ... dpkg: warning: 'ldconfig' not found in PATH or not executable. dpkg: error: 1 expected program not found in PATH or not executable. Note: root's PATH should usually contain /usr/local/sbin, /usr/sbin and /sbin. E: Sub-process /usr/bin/dpkg returned an error code (2) A package failed to install.  Trying to recover: dpkg: warning: 'ldconfig' not found in PATH or not executable. dpkg: error: 1 expected program not found in PATH or not executable. Note: root's PATH should usually contain /usr/local/sbin, /usr/sbin and /sbin.  I want to become a linux geek but it is harder than I thought. Please help!

---

### Post by NikTh on 2012-03-28
Hello and welcome to Ubuntu forums. Many specialists and professionals volunteer here (not me , i am not pro ) for FREE. 
For your problem now , my mind goes to mis-configure sudo . I am not sure for that  , but give the output of command
```
sudo cat /etc/sudoers
``` . Please just copy-paste the results . DO NOT change anything in that file. 
Thanks.

---

### Post by awe1 on 2012-03-28
```
#
# This file MUST be edited with the 'visudo' command as root.
#
# Please consider adding local content in /etc/sudoers.d/ instead of
# directly modifying this file.
#
# See the man page for details on how to write a sudoers file.
#
Defaults    env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL:ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# Allow members of group sudo to execute any command
%sudo    ALL=(ALL:ALL) ALL

#includedir /etc/sudoers.d
```

---

### Post by papibe on 2012-03-28
Hi awe1. Welcome to the forums.

I believe you missed one word in your command:
```
sudo add-apt-repository "deb http://archive.canonical.com/**[COLOR="Red"]ubuntu[/COLOR]**  $(lsb_release -sc) partner"
```

I would edit the sources list manually and add the word:
```
gksudo gedit /etc/apt/sources.list
```
Then:
```
sudo apt-get upgrade
```
Hope that helps, and tell us how it goes.
Regards.

---

### Post by awe1 on 2012-03-28
That was too complicated for the newbie:confused:
which repository?
This was under the "third party developers"
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner

---

### Post by NikTh on 2012-03-28
I cannot see anything wrong to sudoers file. So leave it that way . 
Now that @papible undertake , just follow his suggestions. :p

I missed that this word([COLOR=Red]ubuntu[/COLOR])....is missing . :(

---

### Post by papibe on 2012-03-28
Sorry about that.

Try this:
[LIST]
[*]Open the 'Software Center'.
[*]Then go to Edit -> Software Sources.
[*]Fill your password on the dialogue.
[*]A new window will open. Select the tab 'Other Software'
[*]Look for the line you just added and click edit.
[*]Add the word 'ubuntu' (no quotes) so that the URI looks like this:
```
http://archive.canonical.com/ubuntu
```
[*]Close all windows.
[*]Run in the terminal
```
sudo apt-get update
```
[*]And then:
```
sudo apt-get install skype
```
[/LIST]
I hope this time it is easier to understand. Tell us how it goes.
Regards.

---

### Post by awe1 on 2012-03-28
well this is getting embarrassing. 
> Look for the line you just added and click edit.did I add a line?
Well I added 'ubuntu' in the end of a URI that didn't have it but looked like the example above.
I still have broken packages.
Commands didn't work.
Unmet dependencies is one reason given.

---

### Post by raja.genupula on 2012-03-28
yes do as Papibe suggested and let us know what you got .

---

### Post by papibe on 2012-03-28
EDIT: these instructions were before you manually added the word 'ubuntu'


Don't worry.

The command add-apt-repository add a line to the sources list.

Now that I think about it, you don't really need it.

The last line on the 'Other Software' should be the one you added. It should look like this:
```
http://archive.canonical.com/
```
without the word ubuntu.

Remove that line.

Then Go to the top of the list and make sure 'Canonical Partners' is check.

Then again in a terminal:
```
sudo apt-get update

sudo apt-get install skype
```
Tell us how it goes.
REgards.

---

### Post by awe1 on 2012-03-28
The last one has ubuntu in the end so I didn't change anything.
I did the "add-apt" command with ubuntu in the end after your first answer.
the update command gave me:
"duplicate sources"
The install command ended with "unmet dependencies"

---

### Post by papibe on 2012-03-28
> **awe1 said:**
> 
the update command gave me:
"duplicate sources"
Yes.

The source you are trying to add it is already there and it is called 'Canonical Partners'. Remove yours, update, and try to install again.

Regards.

---

### Post by awe1 on 2012-03-28
This is not a joke, sorry.
Most lines in "other software"  are called "Canonical Partners"
which one should I remove.

---

### Post by papibe on 2012-03-28
> **awe1 said:**
> This is not a joke, sorry.
That's OK.

I see a couple of options:

1. Could you post a screenshot of the 'Other Software' tab?

2. If not, we can solve the problem by editing the sources file. We can give you specific instructions. You would have to post the content of this file: /etc/apt/sources.list. To do that:
[LIST]
[*]Open a terminal, and run:
```
gedit /etc/apt/sources.list
```
[*]The editor will open.
[*]Copy all the text of that file, and paste here in a new post.
[*]Close the editor.
[/LIST]
Regards.

---

### Post by awe1 on 2012-03-28
# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ dists/oneiric/main/binary-i386/

# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ oneiric main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://is.archive.ubuntu.com/ubuntu/](http://is.archive.ubuntu.com/ubuntu/) oneiric main restricted
deb-src [http://is.archive.ubuntu.com/ubuntu/](http://is.archive.ubuntu.com/ubuntu/) oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://is.archive.ubuntu.com/ubuntu/](http://is.archive.ubuntu.com/ubuntu/) oneiric-updates main restricted
deb-src [http://is.archive.ubuntu.com/ubuntu/](http://is.archive.ubuntu.com/ubuntu/) oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://is.archive.ubuntu.com/ubuntu/](http://is.archive.ubuntu.com/ubuntu/) oneiric universe
deb-src [http://is.archive.ubuntu.com/ubuntu/](http://is.archive.ubuntu.com/ubuntu/) oneiric universe
deb [http://is.archive.ubuntu.com/ubuntu/](http://is.archive.ubuntu.com/ubuntu/) oneiric-updates universe
deb-src [http://is.archive.ubuntu.com/ubuntu/](http://is.archive.ubuntu.com/ubuntu/) oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://is.archive.ubuntu.com/ubuntu/](http://is.archive.ubuntu.com/ubuntu/) oneiric multiverse
deb-src [http://is.archive.ubuntu.com/ubuntu/](http://is.archive.ubuntu.com/ubuntu/) oneiric multiverse
deb [http://is.archive.ubuntu.com/ubuntu/](http://is.archive.ubuntu.com/ubuntu/) oneiric-updates multiverse
deb-src [http://is.archive.ubuntu.com/ubuntu/](http://is.archive.ubuntu.com/ubuntu/) oneiric-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://is.archive.ubuntu.com/ubuntu/](http://is.archive.ubuntu.com/ubuntu/) oneiric-backports main restricted universe multiverse
deb-src [http://is.archive.ubuntu.com/ubuntu/](http://is.archive.ubuntu.com/ubuntu/) oneiric-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
deb [http://archive.canonical.com/](http://archive.canonical.com/) oneiric partner
deb-src [http://archive.canonical.com/](http://archive.canonical.com/) oneiric partner
deb [http://archive.canonical.com/](http://archive.canonical.com/) oneiric partner
deb-src [http://archive.canonical.com/](http://archive.canonical.com/) oneiric partner
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner

---

### Post by awe1 on 2012-03-28
the screenshot

---

### Post by papibe on 2012-03-28
It looks like we are on business.

Here are the instructions:
[LIST]
[*]Open a terminal, and run:
```
gksudo gedit /etc/apt/sources.list
```
[*]Your password will be asked, and then the editor will open.
[*]WARNING: now you have the power to edit the file, so be very careful.
[*]Go to the end of the file.
[*]Look for the last block of text that looks like this:
```
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
deb [http://archive.canonical.com/](http://archive.canonical.com/) oneiric partner
deb-src [http://archive.canonical.com/](http://archive.canonical.com/) oneiric partner
deb [http://archive.canonical.com/](http://archive.canonical.com/) oneiric partner
deb-src [http://archive.canonical.com/](http://archive.canonical.com/) oneiric partner
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
```
[*]Insert a line after the 4th line, so it looks just like this:
```
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main

deb [http://archive.canonical.com/](http://archive.canonical.com/) oneiric partner
deb-src [http://archive.canonical.com/](http://archive.canonical.com/) oneiric partner
deb [http://archive.canonical.com/](http://archive.canonical.com/) oneiric partner
deb-src [http://archive.canonical.com/](http://archive.canonical.com/) oneiric partner
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
```
[*]The ending 6 lines your are seeing, are the result of the 'apt-add-repository' command you run. Delete them so the end of the file looks exactly like this:
```
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
```
[*]Save the file, and close the editor.
[*]Open a terminal and run:
```
sudo apt-get update
```
It shouldn't be any error, but if there is, just run it again:
```
sudo apt-get update
```
Now it shouldn't be any error at all (cross fingers).
[*]If all OK, you should be able to install skype like this:
```
sudo apt-get install skype
```
Or even from the Software Center.
[/LIST]
Hope that helps, and tell us if you have any problem.
Regards.

---

### Post by awe1 on 2012-03-28
No problems the second time I wrote ...update but when writing the install command there were unmet dependencies. 
The software center says:
The package system is broken
Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f

---

### Post by papibe on 2012-03-28
Try this:
```
sudo rm -vf /var/lib/apt/lists/*

sudo apt-get update

```
Then try using the Software Center.

Regards.

---

### Post by awe1 on 2012-03-29
software center still gives me this:
Items cannot be installed or removed until the package catalog is repaired.
And if I choose repair:
The installation or removal of a software package failed

---

