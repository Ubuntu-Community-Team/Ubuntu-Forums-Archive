---
title: "Problem when trying to acess a folder shared with Samba on Windows7"
date: 2014-01-31
forum: New to Ubuntu
---

### Post by diniz-cpm on 2014-01-31
Hi everyone,
I'm trying to copy all the contents of my notebook (which runs Ubuntu 12.04 and Windows 8) into my parent's home computer, which runs Windows 7 (like a backup). I've installed Samba with Synaptic and I was able to acess and copy the Ubuntu files from the desk PC, but I couldn't acess the PC files from Ubuntu. But that didn't bothered me because I'm just trying to copy files from the notebook to the PC, and not the other way around.

But today I tried to do the same thing again but I when I tried to acess the folder from Win7 I received a "you don't have permission to acess this folder, contact the administrator to allow you" message, something like that. And I also got the following message when I tried to undo the sharing of the folder that I'm trying to share (which by the way is my whole home folder (/home/daniel):
```
'net usershare' returned error 255: net usershare add: share name daniel is already a valid system user name
```

I tried to google a solution for my problems and followed the instructions given [here]("http://askubuntu.com/questions/19361/cant-access-ubuntus-shared-folders-from-windows-7") and [here]("http://ubuntuforums.org/showthread.php?t=1982137&p=11949979#post11949979"). And now I have duplicated some files (smb.conf for example), change "encrypted password = no" to "encrypt password = yes" and created a folder named /home/daniel/sharedfolder but still I can't acess the folder from Win7!

To be pretty honest something that's been bothering me about Ubuntu is that sometimes things that worked fine yesterday don't work anymore and either a) you're some expert on coding that knows why the thing doesn't work anymore and hows to fix the problem; or b) you're just someone who doesn't have the time to learn coding skills and then you have to google solutions for hours, sometimes just to conclude that following all those instructions scattered across the web made things even worse. Another problem that appeared from nowhere is that when I boot Ubuntu it says that /tmp is missing! (??) Well that's just a personal comment, though, I just need help with Samba. Thank you very much!

(I apologize if this problem has already been adressed somewhere else on this forum, it's just that I believe that following so many tutorials on how to solve the Samba problem made my problem kinda of "unique").

---

### Post by tfrue on 2014-02-01
I only know how to set up Samba from the terminal, so I can try and help you that way.

what I would say you first need to do, is to make sure that we have Samba installed. Type:
```
sudo apt-get install samba
```

Let it install and once it's finished, we can configure the config file. Type:
```
sudo vim /etc/samba/smb.conf
```

Scroll all the way to the bottom with the arrorw key, and type an '*o*.' (Not a zero, but the letter o.)

Then add a share by typing:
```

[New Share]
comment= My New Samba Share
path= /path/to/directory
browseable= yes
guest ok= yes
read only= no
writeable= yes
```

That should give you an open share that you should be able to access from any machine on the LAN.

Good luck,
Chris

---

### Post by Morbius1 on 2014-02-02
You seem to have a number if issues but let me take a shot at a few:
> 'net usershare' returned error 255: net usershare add: share name daniel is already a valid system user name
Samba's usershare doesn't allow you to create a share name that matches an existing user ( and user is defined as anything listed in /etc/passwd ). You can get around this problem by naming it daniel-share in the Nautilus GUI.
> And now I have duplicated some files (smb.conf for example), change  "encrypted password = no" to "encrypt password = yes" and created a  folder named /home/daniel/sharedfolder but still I can't acess the  folder from Win7!

You may also have duplicated share definitions between smb.conf and usershares so the best thing I think it to post the output of the following commands:
```
testparm -s
```
```
net usershare info --long
```
It may very well be exactly what the error message on Windows suggested. A permissions problem - not a Samba permission - a Linux permission.

---

### Post by diniz-cpm on 2014-02-02
> **tfrue said:**
> I only know how to set up Samba from the terminal, so I can try and help you that way.

what I would say you first need to do, is to make sure that we have Samba installed. Type:
```
sudo apt-get install samba
```

Let it install and once it's finished, we can configure the config file. Type:
```
sudo vim /etc/samba/smb.conf
```

Scroll all the way to the bottom with the arrorw key, and type an '*o*.' (Not a zero, but the letter o.)

Then add a share by typing:
```

[New Share]
comment= My New Samba Share
path= /path/to/directory
browseable= yes
guest ok= yes
read only= no
writeable= yes
```

That should give you an open share that you should be able to access from any machine on the LAN.

Good luck,
Chris
I tried this but it didn't help and sudo vim etc/samba/samba.conf didn't work:
```
daniel@daniel-C14CU51:~$ sudo vim etc/samba/samba.conf[sudo] password for daniel: 
sudo: vim: command not found
daniel@daniel-C14CU51:~$ 
```

> **Morbius1 said:**
> You seem to have a number if issues but let me take a shot at a few:

Samba's usershare doesn't allow you to create a share name that matches an existing user ( and user is defined as anything listed in /etc/passwd ). You can get around this problem by naming it daniel-share in the Nautilus GUI.

You may also have duplicated share definitions between smb.conf and usershares so the best thing I think it to post the output of the following commands:
```
testparm -s
```
```
net usershare info --long
```
It may very well be exactly what the error message on Windows suggested. A permissions problem - not a Samba permission - a Linux permission.
At Nautilus GUI I canceled the sharing and then with root Nautilus (the gksudo nautilus thing) I found out another sharing (oh god), then I canceled it too and then I created another share. Then I set the permissions to "group sambashare create and reade files" and clicked on apply to enclosed files. Then I exit root nautilus.
Now I can acces this new share that I just created, but as I predicted the "apply to enclosed files" tool doesn't work very well so I had to set the permission subfolder by subfolder, but that's ok.

The outputs:
```
daniel@daniel-C14CU51:~$ testparm -sLoad smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
params.c:Parameter() - Ignoring badly formed line in configuration file: o
Processing section "[New Share]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	server string = %h server (Samba, Ubuntu)
	map to guest = Bad User
	obey pam restrictions = Yes
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d
	idmap config * : backend = tdb


[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	print ok = Yes
	browseable = No


[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers


[New Share]
	comment = My New Samba Share
	path = /home/daniel/sharedfolder
	read only = No
	guest ok = Yes

```
```
daniel@daniel-C14CU51:~$ net usershare info --long[teste2]
path=/home/daniel
comment=teste2
usershare_acl=Everyone:F,
guest_ok=y

```
*teste2 is the name of the share that I've just created with Nautilus as root.

---

### Post by Morbius1 on 2014-02-03
> Then I set the permissions to "group sambashare create and reade files"  and clicked on apply to enclosed files. Then I exit root nautilus.
Now I can acces this new share that I just created, but as I predicted  the "apply to enclosed files" tool doesn't work very well so I had to  set the permission subfolder by subfolder, but that's
I have no idea what folder you are setting to the sambashare group or why.

You have 2 problems:

[1] This share will not work unless you change permissions on the target folder:
> [New Share]
    comment = My New Samba Share
    path = /home/daniel/sharedfolder
    read only = No
    guest ok = Yes
[2] Your original problem remains however. The samba client user will add a file with permissions that will not allow daniel to write to the file. 

Since all your shares allow guest access you can fix both problems with this:

Edit smb.conf as root and add a line - under the workgroup line:
```
force user = daniel
```
Then restart samba:
```
sudo service smbd restart
```

When the samba client user connects to your shares his identity will be converted to user = daniel so every new file he adds will save with you being the owner.

---

### Post by mastablasta on 2014-02-03
if what you are trying to do is only create backup this is done in a different way (see clonezilla or redo backup on creting a disk image).

also vim is texteditor. i think default one is nano (in terminal) or gedit (in GUI- gui requires gksudo to edit files as root)

---

### Post by diniz-cpm on 2014-02-03
> **Morbius1 said:**
> I have no idea what folder you are setting to the sambashare group or why.

You have 2 problems:

[1] This share will not work unless you change permissions on the target folder:

[2] Your original problem remains however. The samba client user will add a file with permissions that will not allow daniel to write to the file. 

Since all your shares allow guest access you can fix both problems with this:

Edit smb.conf as root and add a line - under the workgroup line:
```
force user = daniel
```
Then restart samba:
```
sudo service smbd restart
```

When the samba client user connects to your shares his identity will be converted to user = daniel so every new file he adds will save with you being the owner.
Yes, I think that my attempt to explain what I did was pretty confusing. I found out that I had shared /home/daniel with nautilus and with nautilus root. So I cancelled both and as root I shared /home/daniel again. For some reason it worked, I managed to acess this folder from Win7 yesterday (and I hope I'm still able to do so).

Sorry for the silly question, but where is smb.conf (I guess there's one at /etc/samba/ and another one at /usr/share/samba)? Also, I can't find the right place to write this line on either of them (I searched for "workgroup" with ctrl-f but couldn't find a place that look appropriated).

> **mastablasta said:**
> if what you are trying to do is only create backup this is done in a different way (see clonezilla or redo backup on creting a disk image).

also vim is texteditor. i think default one is nano (in terminal) or gedit (in GUI- gui requires gksudo to edit files as root)
Well it's just that I think sharing folders is enough for the amount of files I'm transfering, I've actually already copied 90% of I intended to copy.

---

### Post by Morbius1 on 2014-02-03
The file is located here:
```
/etc/samba/smb.conf
```
You should put the force user line here:
> #
# Sample configuration file for the Samba suite for Debian GNU/Linux.
#
#
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options most of which 
# are not shown in this example.
#
# Some options that are often worth tuning have been included as
# commented-out examples in this file.
#  - When such options are commented with ";", the proposed setting
#    differs from the default Samba behaviour
#  - When commented with "#", the proposed setting is the default
#    behaviour of Samba but the option is considered important
#    enough to be mentioned here
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not made any basic syntactic 
# errors. 
# A well-established practice is to name the original file
# "smb.conf.master" and create the "real" config file with
# testparm -s smb.conf.master >smb.conf
# This minimizes the size of the really used smb.conf file
# which, according to the Samba Team, impacts performance
# However, use this with caution if your smb.conf file contains nested
# "include" statements. See Debian bug #483187 for a case
# where using a master file is not a good idea.
#

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
    workgroup = WORKGROUP
    [COLOR=#0000cd]**force user = daniel**[/COLOR]
If you have an abbreviated smb.conf file the important thing is that it's in the [global] section - in fact you can put it right under the [global] line.

---

### Post by diniz-cpm on 2014-02-04
That "force user = daniel" line seems to have fixed my problem! Thank you very much! Just another question: since I've duplicated the "smb.conf" file I think I should delete the copy now, right? So which smb.conf's must be maintained and which can I erase?

---

### Post by barryww1956 on 2014-02-04
Thanks, this post helped me with a problem I was having!

---

### Post by Morbius1 on 2014-02-05
> **diniz-cpm said:**
> That "force user = daniel" line seems to have fixed my problem! Thank you very much! Just another question: since I've duplicated the "smb.conf" file I think I should delete the copy now, right? So which smb.conf's must be maintained and which can I erase?
You really don't have to delete anything if you have it working. 

The only smb.conf that samba is looking at is /etc/samba/smb.conf.

The one at /usr/share/samba/smb.conf should be left alone as well since it's handy to have a default ready if something gets discombobulated later.

---

