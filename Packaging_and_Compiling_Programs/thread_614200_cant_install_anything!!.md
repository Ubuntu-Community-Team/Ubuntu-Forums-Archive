---
title: "cant install anything!!"
date: 2007-11-15
forum: Packaging and Compiling Programs
---

### Post by benniebrown07 on 2007-11-15
When i try to install anything with the terminal and type su it asks for the password and then when i type nothing ever goes in, its just blank. when i open .deb it says: Failed to run gdebi-gtk '--non-interactive' '/home/benniebrown/Desktop/frostwire-4.13.3.i586.deb' as user root.

The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator. Thats if I get past it saying im missing depenecies or something. Im the administrator and i use the password I logon to ubuntu with and it never works. i cant even go to users and groups to try and fix it their cant go to add/remove applications either I cant download anything any one have a clue why and how to fix this? Thanks in advance.

---

### Post by rsambuca on 2007-11-15
You don't need sudo to install a .deb file.  Just double click on the frostwire deb and the gdebi package manager will install it for you.  You might want to note that for frostwire, you will also have to install java first.

---

### Post by dfreer on 2007-11-15
Can you post the output of these commands, please?:
```
whoami
cat /etc/apt/sources.list
sudo apt-get update
```

@rsambuca - technically, you do need root permissions to install a debian package. Perhaps you meant to say "You don't need *to use the terminal* to install a .deb file"?

---

### Post by benniebrown07 on 2007-11-15
whoami
benniebrown
benniebrown@bennie-desktop:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
benniebrown@bennie-desktop:~$ sudo apt-get update

---

### Post by rsambuca on 2007-11-15
> **dfreer said:**
> Can you post the output of these commands, please?:
```
whoami
cat /etc/apt/sources.list
sudo apt-get update
```

@rsambuca - technically, you do need root permissions to install a debian package. Perhaps you meant to say "You don't need *to use the terminal* to install a .deb file"?

I don't recall ever having to enter a password when using gdebi.  Are you positive about that?

In any case, whether I was incorrect or not, what I meant to say was exactly what I said.  Please do not be so presumptuous as to tell me what I meant to say.

---

### Post by rsambuca on 2007-11-15
> **benniebrown07 said:**
> whoami
benniebrown
benniebrown@bennie-desktop:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
benniebrown@bennie-desktop:~$ sudo apt-get update

I am afraid all of your repositories are messed up.  Go to System -> Administration -> Software Sources.  On the first tab, make sure all of the boxes are checked and then press the "Download from" button.  Select "Other".  Then press the "Select Best Server" button.

---

### Post by benniebrown07 on 2007-11-15
i cant Go to System -> Administration -> Software Sources because software sources is not there and when i go to edit that menu and i check next to software sources or user groups .etc it will check then uncheck after a second and it always does that

---

### Post by dfreer on 2007-11-15
@rsambuca:
> **rsambuca said:**
> I don't recall ever having to enter a password when using gdebi.  Are you positive about that?

In any case, whether I was incorrect or not, what I meant to say was exactly what I said.  Please do not be so presumptuous as to tell me what I meant to say.

I'm very positive about needing a password to install most packages, if not all of them. Since in most cases the files in these packages are installed in locations like /usr/bin/, /usr/lib/, which can only be wrote in by root, you would need to have permission to install them.
If you are not convinced by words alone, here's a small screencast of the gksu dialog launching, requiring the user to enter their password:
[http://www.dfreer.org/dfreer/screencast2.ogg](http://www.dfreer.org/dfreer/screencast2.ogg)

Since you are clearly an active member of the community, instead of saying flat out "You are wrong", I tried to politely correct you, giving you the benefit of the doubt, so to speak, that I just misunderstood what you meant. Please note the difference between the phrase:
> **Perhaps** you meant to say "You don't need to use the terminal to install a .deb file"**?**
and:
> rsambuca, what you meant to say is "You don't need to use the terminal to install a .deb"!

The latter is "telling you what you meant". The former is a question. Please do not presume that I was being presumptuous and don't take offense where none was intended. In the future I will try to remember not to phrase my questions in that manner.

EDIT:
@benniebrown07 - You can edit the /etc/apt/sources.list file yourself, if you want to. You'll need to have root permissions to be able to save the file, one way to open and edit the file is like this:
```
gksu gedit /etc/apt/sources.list
```
You can delete the lines that begin like this:
# Line commented out by installer because it failed to verify:
And delete the "#" sign in front of the lines you need. If you are not sure as to which ones you need, there is probably no harm in removing the comment from all the lines that begin with "# deb http://" and "# deb-src http://"

The most likely reason for the above lines being commented is that you did not have an active internet connection when you installed ubuntu,

---

### Post by benniebrown07 on 2007-11-15
Failed to run gedit '/etc/apt/sources.list' as user root.

The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator.
this is what i got again

---

### Post by rsambuca on 2007-11-15
> **dfreer said:**
> @rsambuca:


I'm very positive about needing a password to install most packages, if not all of them. Since in most cases the files in these packages are installed in locations like /usr/bin/, /usr/lib/, which can only be wrote in by root, you would need to have permission to install them.
If you are not convinced by words alone, here's a small screencast of the gksu dialog launching, requiring the user to enter their password:
[http://www.dfreer.org/dfreer/screencast2.ogg](http://www.dfreer.org/dfreer/screencast2.ogg)

Since you are clearly an active member of the community, instead of saying flat out "You are wrong", I tried to politely correct you, giving you the benefit of the doubt, so to speak, that I just misunderstood what you meant...


I guess I would rather you just told me I was incorrect.  I can take it.  I have been wrong many times in the past, and I will without question be wrong again.  It is better to get rid of the incorrect advice on these forums, as there is far too much of it.  It was probably just semantics of your writing, anyways.  Instead of "Perhaps...", you could have just asked "Did you mean...".

Anyways,  peace and love!

---

### Post by benniebrown07 on 2007-11-15
what do you think i should do know that that didnt work?

---

### Post by rsambuca on 2007-11-15
Hmmm... seems to be something messed up here.  Hopefully we will be able to fix it though.

What I propose is to replace your entire sources.list, and see if we can fix your installation.  To do this, we will first open a text editor to change your sources:```
gksudo gedit /etc/apt/sources.list
```
To make things easier, just delete the entire contents, and paste this into it:```
# Automatically generated sources.list
# http://www.ubuntu-nl.org/source-o-matic/
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -
#
# If you don't know what to do with this file, read
# https://help.ubuntu.com/community/Repositories/CommandLine

# Ubuntu supported packages
# GPG key: 437D05B5
deb http://us.archive.ubuntu.com/ubuntu gutsy main restricted 
deb http://us.archive.ubuntu.com/ubuntu gutsy-updates main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb http://us.archive.ubuntu.com/ubuntu gutsy universe multiverse 
deb http://us.archive.ubuntu.com/ubuntu gutsy-updates universe multiverse
deb http://security.ubuntu.com/ubuntu gutsy-security universe multiverse
```
Then save the file.

Then```
sudo apt-get update
```
Then cross your fingers!

---

### Post by benniebrown07 on 2007-11-15
gksudo gedit /etc/apt/sources.list I cant do this because when i type it in it asks for the password (which wont go in). Im supposed to type that in the terminal right?

---

### Post by rsambuca on 2007-11-15
Try a reboot.  Something is amiss here.

---

### Post by dfreer on 2007-11-15
**EDIT:** Whoops. I took too long to post, and now there is new information in this thread. I'll catch up to what I have missed so far.

**EDIT: A few minutes later.** Hmmm... Not sure if what I posted below will be of any help, as I am not quite sure what is wrong here. I'll step back and let the thread progress further, and add anything I think might help out as needed.



@rsambuca - I can see where "Did you mean..." would be less likely to be interpreted wrong, thanks for the advice! Peace and love to you too! :D

@benniebrown07:
> **benniebrown07 said:**
> Failed to run gedit '/etc/apt/sources.list' as user root.

The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator.
this is what i got again

Hmmm... not sure exactly what would cause this particular error message, My guess would be that your user account does not have permission to use sudo. If this is the case, I think it might be resolved if you can reboot into single-user mode, and from there add your username to the 'admin' group. Also, it would be a good idea to check your sudoers file to make sure that users in the 'admin' group have root privileges.

If this is not the problem, then the below should still be safe to run, as it is the default behavior of Ubuntu.

To get into single-user mode (Also known as "Recovery Mode"), please reboot your machine. When it starts, after it goes through POST it should bring up the GRUB boot menu (if you are currently dual-booting), or it should bring up some text in the upper-left corner of your screen saying something similiar to "Press 'Esc' to enter the GRUB menu". The GRUB boot menu will look something like the image at the bottom of this post.

Select the (recovery mode) option. It should boot, and upon booting it should leave you at a bash prompt as root, should look something like this:
```
root@bennie-desktop:~#
```
From here, you can add your username to the admin group:
```
adduser benniebrown admin
```
Now, to check your sudoers file:
```
visudo
```

It should look something like mine:
```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
**%admin ALL=(ALL) ALL**

```

If you need to edit that last line, go ahead and do so. You can save the file by hitting <Ctrl>+<X>, then <y>, then <Enter>.
Reboot with this command:
```
shutdown -r now
```
And hopefully this will take care of your sudo problems. Make sure to test it, perhaps by running:
```
sudo apt-get update
```

---

### Post by benniebrown07 on 2007-11-15
thanks for the help so far ima test this can you stay online to help me if this doesnt work or something?

---

### Post by benniebrown07 on 2007-11-15
thank you so much everything seems to be in order now now i have one more qeustion how do i instal .bin files

---

### Post by dfreer on 2007-11-15
@benniebrown07 - For future followers of the thread, what did you have do to solve the problem?

.bin files should be marked with the executable bit, and then executed. This is one way to do so:
```
sudo chmod a+x *yourfilename*.bin
./*yourfilename*.bin
```

---

### Post by benniebrown07 on 2007-11-15
Hmmm... not sure exactly what would cause this particular error message, My guess would be that your user account does not have permission to use sudo. If this is the case, I think it might be resolved if you can reboot into single-user mode, and from there add your username to the 'admin' group. Also, it would be a good idea to check your sudoers file to make sure that users in the 'admin' group have root privileges.

If this is not the problem, then the below should still be safe to run, as it is the default behavior of Ubuntu.

To get into single-user mode (Also known as "Recovery Mode"), please reboot your machine. When it starts, after it goes through POST it should bring up the GRUB boot menu (if you are currently dual-booting), or it should bring up some text in the upper-left corner of your screen saying something similiar to "Press 'Esc' to enter the GRUB menu". The GRUB boot menu will look something like the image at the bottom of this post.

Select the (recovery mode) option. It should boot, and upon booting it should leave you at a bash prompt as root, should look something like this:
Code:

root@bennie-desktop:~#

From here, you can add your username to the admin group:
Code:

adduser benniebrown admin

Now, to check your sudoers file:
Code:

visudo

It should look something like mine:
Code:

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

If you need to edit that last line, go ahead and do so. You can save the file by hitting <Ctrl>+<X>, then <y>, then <Enter>.
Reboot with this command:
Code:

shutdown -r now

And hopefully this will take care of your sudo problems. Make sure to test it, perhaps by running:
Code:

sudo apt-get update

Attached Thumbnails
Click image for larger version Name: grub.png Views: 2 Size: 5.4 KB ID: 50336  

Ijust followed these intructions and it works now,
but about the .bin files how'd you say do that again simple for me plese? I tried to sudo chmod a+x filename but the same thing saying
 Could not open the file /home/benniebrown/Deskto&#8230;6u3-linux-i586-rpm(2).bin.
gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again

---

### Post by dfreer on 2007-11-16
Can you run this command:
```
ls -l ~/Desktop/
```
And also, what software are you trying to install?

---

### Post by benniebrown07 on 2007-11-16
im trying to install java so i can install limewire and i ran the command heres what happened:
benniebrown@bennie-desktop:~$ ls -l ~/Desktop/
total 104456
-rw-r--r-- 1 benniebrown benniebrown 27617732 2007-11-15 07:26 [AH]_Naruto_Movie_Trailer_[6498D765].avi
-rw-r--r-- 1 benniebrown benniebrown 11446665 2007-11-14 10:32 avast4workstation-1.0.8.tar.gz
-rw-r--r-- 1 benniebrown benniebrown        0 2007-11-15 01:09 Cricketers.rar (2)
-rw-r--r-- 1 benniebrown benniebrown  7895892 2007-11-14 22:55 data.tar.gz
-rw-r--r-- 1 benniebrown benniebrown        4 2007-11-14 22:55 debian-binary
-rw-r--r-- 1 benniebrown benniebrown   153864 2007-11-14 10:47 easyubuntu_latest.deb
-rwxr-xr-x 1 benniebrown benniebrown  7896626 2007-11-14 21:56 frostwire-4.13.3.i586.deb
-rw-r--r-- 1 benniebrown benniebrown     5196 2007-09-18 06:28 gnome-terminal.desktop
-rw-r--r-- 1 benniebrown benniebrown 19119599 2007-11-13 23:57 jre-6u3-linux-i586.bin
-rw-r--r-- 1 benniebrown benniebrown 18598258 2007-11-13 23:33 jre-6u3-linux-i586-rpm.bin
-rw-r--r-- 1 benniebrown benniebrown  3842249 2007-11-14 22:22 ktorrent-2.2.3.tar.gz
drwx------ 2 benniebrown benniebrown     4096 2007-11-15 23:00 LimeWireLinux
-rw-r--r-- 1 benniebrown benniebrown  7265664 2007-11-15 22:53 LimeWireLinux.deb
-rw-r--r-- 1 benniebrown benniebrown  2947796 2007-11-14 23:59 Macgyver How-To Handbook - Very Interesting.rar

---

### Post by ubuntu27 on 2007-11-16
You are trying to install Java?

do this.

Open the Terminal and type

```
sudo apt-get install ubuntu-restricted-extras
```

that will install Sun Java, and some codecs such as mp3

---

