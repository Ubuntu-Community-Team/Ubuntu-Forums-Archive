---
title: "what i would like to do with ubuntu server - need pointers"
date: 2019-08-02
forum: New to Ubuntu
---

### Post by jwhiz56 on 2019-08-02
All,

absolute newbie here.  I have installed 19.04 server on an older desktop with the intention of using it as a file server for my windows computers.  win 10 is being a pain about networking and seeing attached computers on the network.  I have an 8 drive disk box attached via usb3.0 to a windows computer.  I want to take that 8 drive box and attach it to the ubuntu server desktop and have access to all disks/partitions via windows on all my other computers (only on my home network, not across the internet).  

I installed FTP and NFS on unbutu.  but I have no idea where to go from here.  if someone could point me to books, youtube tutorials or just provide direction, it would be appreciated.  

thanks
john w zerkel

---

### Post by TheFu on 2019-08-02
Lots of opinions follow.  Hopefully, some other people will chime in with theirs so you can pick and choose the different parts that make the most sense.

First, as someone new, you don't want 19.04. Support for that release ends in December.  You want 18.04, which has 5 yrs of standard support - 2023.  Stay with LTS releases for servers unless you have a very specific requirement.  Newer isn't always better.  18.04 and 16.04 are LTS releases.  Most of my systems are on 16.04, which has free standard support until April of 2021.

Second, Linux uses different file systems than Windows.  While it can read NTFS storage, there are multiple problems doing that since it doesn't natively support it. Performance will be less, standard Unix permissions aren't honored, and server-style storage management cannot be used.  So you have to decide how you will either migrate to a Linux storage solution software stack or live with all the issues that using NTFS forced onto the server.

USB3 doesn't implement the full ATA storage command set, so there are some things that USB (any sort) can cause.  Often, these USB storage boxes also support eSATA.  It would definitely be worth the effort to use eSATA over USB3.

To make Linux storage available to Windows, you'll likely want to use samba.  It is the least bad of the bad choices.  You can use sftp, scp, sshfs, NFSv3, NFSv4 and a number of other protocols if you like a little more challenge.  Samba is an SMB implementation, so it doesn't fully support Unix permissions. Samba/SMB is only useful on secured LAN networks.  If you want to access files securely over the internet, there are other methods, like sftp.  sftp support is built into almost every Linux file manager.  On Windows, WinSCP is a nice client.  There are sftp clients for every networked OS, like iOS, OSX, Android, Windows and all the different Unix/BSD flavors.

Please don't use plain FTP.  That protocol should have died in 1995. I'm 100% serious.  Use sftp instead.  ssh and ssh-based protocols are the way that Unix people communicate with Unix systems.  It is the swiss-army-knife of Unix connectivity.  Putty is the normal ssh client used by Windows.  Please uninstall/remove/purge whatever plain FTP server you installed.

To install sftp, just install and secure ssh.
```
sudo apt install openssh-server fail2ban
```
That's it. It will be enabled and running now.  You can connect using sftp, scp, ssh, rsync, and 50 other tools with that single line.  Learn about ssh.
What is that "fail2ban" thing?  It is a brute-force attack countermeasure, setup to automatically block brute force attacks against ssh, sftp, scp and all the ssh-based tools.  I don't remember the number of attempts allowed, but either 3 of 5 is the default before a firewall rule will block the attacking IP for 5 minutes.  Really, if you care about security, you won't allow passwords to be used. ssh-keys are much more secure AND 50,000x more convenient.

As for doing server things, google for "ubuntu server guide" and check out the results that have "ubuntu" in the name.  The problem with online resources is they say what to type, but do not provide "why" or "why not" to do those things.

A few more tips.  When googling for anything with your new Ubuntu Server - assuming you've moved to 18.04, then you should seek out solutions specific to 18.04.  Most server things don't change too rapidly, but there are many old how-to guides out there full of instructions that simply don't work for 18.04.  If you haven't figure this out, Linux servers don't have any GUI.  Generally, I manage my Unix servers through ssh, scripting, and automation tools.  For servers that are the same, I can manage 1, 5, 20, 200, 2000 servers with about the same level of effort.  That's why Unix/Linux servers are so much more popular than, other options.

But really, you need to get your storage and logical volume management design figured out carefully before going too far beyond ssh on the box.

If you will post a little about your system - **inxi -Fz** - would be good, we could suggest some other considerations for your new 18.04 server. Just install inxi since it isn't likely to be installed.  Getting the overview upfront will prevent misunderstandings.

---

### Post by jwhiz56 on 2019-08-02
thank you.  the storage box does offer eSATA but it only supports 6 of 8 drives on it.  That's why I chose USB3.0.  also, all drives/partitions are currently formatted as NTFS.  I will wipe and install 18.04 along with ssh and inxi.  I will post again upon completion with the output from inxi.  i'll also include specs on the drive box as well as the current drives installed.

thanks so very much.  
john

---

### Post by jwhiz56 on 2019-08-02
the 8-bay removable enclosure is StarTech.com's S358BU33ERM unit.  usb3.0/eSATA interfaces.  attached is the screen shot of the inxi display.

---

### Post by jwhiz56 on 2019-08-02
this is a picture of my StarTech drive configuration showing drives/partitions.

john

---

### Post by TheFu on 2019-08-02
Dude, no screen shots.  Copy/paste the text, please. Use code tags. See my signature for how - it redirects to a guide in these forums.

This isn't Windows and we always prefer text over images.  ALWAYS, especially for servers.  Many people here pay for bandwidth by the byte and I have terrible eyesight, so images just don't work for me.  I can't copy/paste a line from an image with corrections either ... so I'll just not help.

If you are running putty from Windows, the copy/paste is all mouse controlled and really easy. Left to select, right to paste.
If you are doing it on a Linux workstation, if there is a GUI, it is select/paste using the mouse (left to select, middle to paste) or you can redirect the program output into a file.  
```
inxi -Fz > /tmp/summary
```
and move the file to whatever machine has the web browser (using sftp?), then copy/paste.

[https://github.com/jlevy/the-art-of-command-line](https://github.com/jlevy/the-art-of-command-line) is an nice introduction to using bash that goes beyond the trivial stuff. Grab what you need and come back for most stuff later.  Mainly, if you are typing more than 2-3 characters at a time on any Unix machine, it is likely you are doing it the hard way. Learn about bash completion, also called "tab completion" since shells other than bash provide it too.

---

### Post by Morbius1 on 2019-08-03
As it turns out I just set up a Ubuntu server 2 days ago so I'll share what I did.

[1] Samba is the default file sharing mechanism on all desktop operating systems so I started with that:
```
sudo apt install samba
```
[2] I wanted the server to be "discoverable" through the file managers of all my Linux and MacOS clients so I installed avahi:
```
sudo apt install avahi-daemon
```
[COLOR=#0000cd][I]Note: Once avahi is installed samba will announce its presence automatically and will be seen by any Linux or MacOS desktop system.

[/I][/COLOR][COLOR=#000000][3] I wanted the server to be discoverable through Explorer on Win10.

As you may have discovered yourself Win10 has a problem "seeing" other hosts on the network. The normal NetBIOS mechanism which allowed host discovery no longer works in Win10 because it disabled SMBv1 on the client side ( as well as the server side ) and you can't browse the network without SMBv1. You can connect to by name ( maybe ) but you can't browse for it. 

You can still access the server through Explorer but it must be asked for explicitly by either:
[B]
ip address[/B]: \\192.168.0.100
OR
**mDNS name**: \\zerkelserver.local

**OR by NetBIOS name - if your're lucky**: \\zerkelserver

There is another way Win10 can discover the samba server. In my particular case and since the Win10 machines are somewhat transient in my universe I decided to implement WS-Discovery on the server using the steps in this feature request: [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1831441](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1831441)

Now the only thing left is to create a samba share. In my case I just created a Public guest accessible share to make sure everything works by editing /etc/samba/smb.conf and adding a share definition at the end on the file:

```
[Public]
path = /srv/Public
guest ok = yes
read only = no
force user = morbius
```
Then restarted smbd:
```
sudo service smbd restart
```

[/COLOR][COLOR=#0000cd]* Note: I had to create the /srv/Public path ( sudo mkdir -p /srv/Public ) and take possession of the folder ( sudo chown morbius /srv/Public )*[/COLOR][COLOR=#000000]

I think it would help people if you could describe your use case for this server. What is it going to be used for? Do you want everything to be accessible to everyone? etc.....

I suspect your biggest hurdle will be to mount these 8 USB "drives". Ubuntu server doesn't automount USB devices so you will have to define them.


[/COLOR]

---

### Post by jwhiz56 on 2019-08-03
Morbius1, Thank you for your very helpful post.  Can you please elaborate on your very last statement about my biggest hurdle?  please keep in mind that i'm a windows person JUST STARTING to look into Linux as a server for some storage.  I'm trying to get these disks available to all my win 10 machines via explorer WITHOUT having to map network drives explicitly.  my goal is to have all drives/partitions on the disk enclosure available to all my computers.  main use will be backup and file storage.  I have ordered 3 books on Ubuntu v18.04 covering server and workstation versions.  

TheFu, as noted in my first post, i'm a 3 day old user of ubuntu, coming from a windows world.  I don't know how to do the most basic things like copy/paste/transfer between the ubuntu machine and my windows machine (never heard of 'putty').  so i'm sorry to have offended you with the screen shots.  I will understand if you don't want to deal with an absolute beginner.

thanks
john

---

### Post by jwhiz56 on 2019-08-03
also, during the server installation, it asked if I wanted SSH installed and I said yes.  is that the same as openssh or do I need both or do I need to reinstall the server without ssh and add openssh?

thanks
john

---

### Post by Morbius1 on 2019-08-03
I'm going to answer the easy one first if that is OK.

When you installed SSH on the server you installed the client and server components so you should be good to go.

If your client is Win10 you already have an ssh client built into the system - in fact it's the same OpenSSH that Linux uses just a newer version. However unlike a Linux client that has it implemented in the file manager in Win10 it's only accessible via the terminal ... er ... CommandPrompt.

So the initial connection process would look something like this - my user on the server is tester and the hostname is ubsrv1804:
> Microsoft Windows [Version 10.0.18362.10005]
(c) 2019 Microsoft Corporation. All rights reserved.

C:\Users\morbius>ssh [EMAIL="tester@ubsrv1804.local"]tester@ubsrv1804.local[/EMAIL]
You will get a warning about accepting a key
> The authenticity of host 'ubsrv1804.local (2605:a601:a1a2:4e00:216:76ff:fea6:1745)' can't be established.
ECDSA key fingerprint is SHA256:VLwguAbPFc9BACFzqTEdBWiZL1BH637nY8j3yllat9E.
Are you sure you want to continue connecting (yes/no)? [COLOR=#0000cd]yes[/COLOR]
Warning: Permanently added 'ubsrv1804.local,2605:a601:a1a2:4e00:216:76ff:fea6:1745' (ECDSA) to the list of known hosts.
Then it will ask for the server users password:
> tester@ubsrv1804.local's password:
At that point you are remotely connecting to the server:
> Welcome to Ubuntu 18.04.2 LTS (GNU/Linux 4.15.0-55-generic x86_64)
...
...
...
tester@ubsrv1804:~$

This may not be the way you actually want to copy files around your network but you might consider using it to administer the server or when someone asks you to run some command and post the results you can do it from Win10 and copy and paste it to the forum.

Given the requirement to have everything in Explorer I'm not sure if there is an alternative to Samba and the WS-Discovery idea unless you want to enable SMBv1 on the client side of Win10. Microsoft has been trying to kill off SMB1 and the whole NetBIOS / Workgroup thing for 20 years and it really doesn't want anyone to use smb1.

---

### Post by TheFu on 2019-08-03
> **jwhiz56 said:**
>  TheFu, as noted in my first post, i'm a 3 day old user of ubuntu, coming from a windows world.  I don't know how to do the most basic things like copy/paste/transfer between the ubuntu machine and my windows machine (never heard of 'putty').  so i'm sorry to have offended you with the screen shots.  I will understand if you don't want to deal with an absolute beginner.

No offence taken and my statements about images were meant as a slight joke, but also serious.  These forums are a text-based medium, so using text is always preferred.

Putty (google for it) has been THE ssh client for Windows since the 1990s.  Only recently did MSFT add ssh to Win10. I've never seen it and definitely never used it.  If the Win10 ssh client runs inside any Windows cmd/powershell, that is a total pain to use for copy/paste.  Copy/paste in terminals is extremely handy.  Linux terminals and Putty make that really easy and highly efficient.

It isn't that I don't want to help.  The real issue is that since I haven't been a beginner in Unix in almost 30 yrs, I forget small steps that aren't issues for anyone except absolute beginners.  That means that sometimes my answers are confusing and frustrating in a medium like this.  People trying to run Ubuntu "server" tend to be much more technical and have a very strong desire to learn Linux.  If that isn't you, perhaps starting with a normal Linux desktop OS for the first 6 months would be a better choice?  The desktops have a nice GUI and don't prevent running all the server things.  With the GUI, desktop things are easier, while the server things are should still be handled in the "server way", that usually means via text configuration.
I've taught beginning Linux and and beginning systems administration with Linux at the local University.  [B]Every book I've seen is always out of date before printing. 
[/B][https://tutorials.ubuntu.com/](https://tutorials.ubuntu.com/)
[https://help.ubuntu.com/](https://help.ubuntu.com/) which leads to ... [https://help.ubuntu.com/lts/serverguide/](https://help.ubuntu.com/lts/serverguide/)
Before attempting to run a server, having an intermediate level of shell/CLI knowledge is very useful.  
[http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) is a nice, free, no-hassle, book that you can purchase, or just download the PDF. Multiple languages.
There's an Ubuntu help page that lists online Ubuntu and Debian guides. [https://help.ubuntu.com/community/ExternalGuides](https://help.ubuntu.com/community/ExternalGuides)
And because I've been asked how to Learn Linux hundreds of times, I wrote my own.
[https://blog.jdpfu.com/2014/12/28/learning-linux](https://blog.jdpfu.com/2014/12/28/learning-linux) which have links ordered so the most important things are learned first .... IMHO.  Everyone learns Unix/Linux in a slightly different way.  The most efficient way, isn't usually picked, because it is pretty boring after the first 2 hrs is done.  The problem with learning a skill as you need it, is that we skip over basic skills so doing the step-by-step stuff is much harder than it needs to be.  For example, everyone puts off learning about Unix file and directory permissions, but they are the cornerstone of all Unix security. The Unix model is used by every popular OS, but Windows uses it in a much more permissive way, so Windows users don't normally need to understand much.  Unix systems aren't as forgiving.

See how my writing can be confusing and frustrating?  ;)

Morbius1 knows Windows integration stuff far better than almost everyone else around here.
I think 1 step might have been missed in the samba setup, but perhaps it has been addressed in the newer samba releases.  I always have to create a samba userid using **smbpasswd** on the samba server before any connections work.  Perhaps the "guest" part of the configuration removes that need?

---

### Post by mastablasta on 2019-08-06
you didn't mention how you want users to connect to shared files. there is also the option of setting up your own cloud using owncloud, nextcloud or seafile.

auto mount partitions: [https://www.binarytides.com/ubuntu-automatically-mount-partition-startup/](https://www.binarytides.com/ubuntu-automatically-mount-partition-startup/)


you need to seriously think about NTFS file system on linux server. while it works, you might hit obstacles. for example if file system goes corrupt it is hard to get it back with linux tools. there is also the permissions issue already mentioned. it all depends what kind of server this is and who the users are (LAN - internet, few users - many).

you might also want to explore some server GUI's to make it easier for you. Zentyal is small business server with GUI and is based on Ubuntu, Ajenti is a nice webgui that works on Ubuntu, Open media vault is a Debian based distro aimed at storage servers. it comes with a nice webgui. Webgui is accessed via web browser. just have a look at them and explore a bit. maybe you see something you like. i find it easier to do things in user interface than in command line. not always the most efficient but it get's the job done.

---

### Post by jwhiz56 on 2019-08-09
All,

I didn't want you to think I disappeared.  real life has been hectic lately.  I also bought 3 books, 2 on server and 1 on workstation.  I using them to help myself.  I do have one question.  In several replies, I've been told to edit the file in \etc\&#8230;.   and I use nano to do that and I get a blank edit panel with a message I don't have authorization.  either ya'll are leaving out a step or i'm not doing it right.  any help?

thanks so much for all your help so far.

john

edited to add book titles:

Mastering Ubuntu server, 2nd edition - server v 18.04
Ubuntu 18.04 LS server admin & reference
Ubuntu unleashed 2019 edition v. 18.04, 18.10, 19.04 & 19.10

---

### Post by TheFu on 2019-08-09
Did those books cover file and directory permissions yet?   Unix systems are multi-user from the ground up.  Learning to handle different files based on which userid is the owner needs to be 2nd nature for an administrator.  In post #2 above, I mentioned Unix permissions.

So .... with that said, you will save yourself hours, days, weeks, months of frustration if you learn about Unix file and directory permissions ASAP.  Google "Ubuntu file permissions" to find the Ubuntu wiki page about those.  Working through it would be a first step, but to really "get it", the best way I know is to create 3 new userids, 2 new groupids, open 3 terminals, su into each new userid - 1 window for each one, then play for about 45 minutes mixing and matching every possible permission you thank think of for files and directories in a play area.   I struggled to really understand permissions for about a year before I finally sat down and figured them out.  Since then, I've only needed to look up funky permissions to solidify my understanding for the setgroupid, sticky-bit.  Pretty much all the other permissions are really easy to master and get used daily.

Ok ... the short answer is to use **sudoedit** when you need to edit system files.  System files are almost all of them under /etc/ and most places that are not in your HOME.
There are other ways to do it, without sudoedit, but IMHO, it is a good habit to start sooner than later.

A warning.  You'll see other places saying to use *sudo gedit /path/to/file*. Don't to that. Sometimes using sudo with GUI programs can break your ability to use those same programs normally.  sudo should only be used when necessary, not all the time and not whenever something doesn't work.  It is easiest to say only use sudo for non-GUI programs.  That is pretty safe and keeps most people out of trouble.  You can use *sudo -H gedit* fairly safely. Same for other GUI tools, but really it should be avoided. NEVER run a web browser or GUI email program with sudo.  

**sudo nano file** is safe to use, if you can stand nano. I can't. ;)  It is safe because nano doesn't write config files automatically or without your expressed request.  That's where most Gnome tools fail. They store settings without asking way too often.

Have you learned about tab completion yet?

One more thing. Every popular OS uses / for the directory separator, including Windows, OSX, Linux, BSD, Unix and variants of those.  Only MS-Windows works with \.  Your post above has a \etc\ ... which won't work.

---

### Post by Morbius1 on 2019-08-10
> **jwhiz56 said:**
> 
I also bought 3 books, 2 on server and 1 on workstation.  I using them to help myself. 
Oh dear. I fear that you are making this way more complicated than it needs to be - for a home network. These books are either geared to the enterprise or are way outdated. "Using Samba" is an example of such a book. It's several inches thick and represents how samba was configured 15 years ago. Even Samba itself tells you to stay away from this book: [https://www.samba.org/samba/docs/using_samba/toc.html](https://www.samba.org/samba/docs/using_samba/toc.html)

Anyhoo, I would like to offer the following suggestions that may be useful in your path of discovery:

[1] If you are following multiple sources for samba configuration you will likely end up with an incomprehensible mess. Luckily there is a factory fresh copy of the original smb.conf located here that you can use to restore yourself to the original setup: **/usr/share/samba/smb.conf**

[2] The following diagnostic command is your friend:
```
testparm -s
```
testparm will scan your smb.conf, compare it to the default settings ( which you do not have access to directly ) and display what affect it will have on how samba runs. It will catch many - but not all - errors you may have in your configuration.

>  In several replies, I've been told to edit the file in \etc\&#8230;.   and I  use nano to do that and I get a blank edit panel with a message I don't  have authorization.
You need to slap a sudo in front of nano - for example:
```
sudo nano /etc/samba/smb.conf
```

---

### Post by jwhiz56 on 2019-08-12
all,

based on all the pointers so far, I have created my server installation.  Ubuntu 18.04 is installed, updated, SMB installed, unzip installed, wsdd installed.  Hardware wise, usb 3.0 PCI card installed, 8 drive disk enclosure plugged in/functional.  I have attached a file showing the fstab entries I think I need and the smb.conf entries I think I need.  I have some questions.

1.  in regards to the following fstab entry, /STORAGE is the sub-directory where the drive is to be mounted (I think).  does the /585CEDA25CED7B60 (duplicating UUID per example) have to be the same as the UUID or can it be any (more descriptive) value?
#  1TB HD
UUID=585CEDA25CED7B60 /STORAGE/585CEDA25CED7B60 NTFS DEFAULTS 0 0

2.  do I need to make the directory /storage?  (pretty sure I do), do I also need to make the remainder as part of that directory structure?
3.  do I need to take ownership of these directories?
4.  any other things I should know/do?

here is the output of the blkid command:

jwhiz56@zerkelserver:~$ sudo blkid
/dev/sda2: UUID="53f4c033-fca8-4887-a544-a9e84b224e84" TYPE="ext4" PARTUUID="6840b843-bc52-45cf-8333-fb4a2885c922"
/dev/loop0: TYPE="squashfs"
/dev/loop1: TYPE="squashfs"
/dev/sda1: PARTUUID="377eca71-e5b2-4e9d-9e28-ad8f928c4165"
/dev/sdf1: LABEL="960gb spare ssd" UUID="3AF05EA8F05E6A61" TYPE="ntfs" PARTUUID="19a298c7-01"
/dev/sdg1: LABEL="Windows" UUID="2A7045C07045938B" TYPE="ntfs" PARTUUID="881c2b75-1369-412c-905a-b9df10269d6c"
/dev/sdh1: LABEL="DATA" UUID="585CEDA25CED7B60" TYPE="ntfs" PARTUUID="140b91dd-01"
/dev/sdj1: LABEL="500GB spare" UUID="E46AA01E6A9FEB94" TYPE="ntfs" PARTUUID="b91a0656-01"
/dev/sdi1: LABEL="1TB spare" UUID="F4D2F307D2F2CD3C" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="066813da-6360-40a6-a908-b74013eeb77d"
/dev/sdk1: LABEL="500GB spare" UUID="406668E36668DB64" TYPE="ntfs" PARTUUID="307ece58-01"
/dev/sdl1: LABEL="2tb sata" UUID="0C925C7D925C6CE8" TYPE="ntfs" PARTUUID="481c4239-01"
/dev/sdm1: LABEL="2tb sata" UUID="16884D7E884D5D7D" TYPE="ntfs" PARTUUID="7034c302-01"

---

### Post by jwhiz56 on 2019-08-12
I think i'm answering my own question, this is what I should do:  (did this and it works.  can see all 8 disks from my windows explorer)

sudo mkdir -p /storage/disk1
sudo mkdir -p /storage/disk2
sudo mkdir -p /storage/disk3
sudo mkdir -p /storage/disk4
sudo mkdir -p /storage/disk5
sudo mkdir -p /storage/disk6
sudo mkdir -p /storage/disk7
sudo mkdir -p /storage/disk8

sudo chown jwhiz56 /storage/disk1
sudo chown jwhiz56 /storage/disk2
sudo chown jwhiz56 /storage/disk3
sudo chown jwhiz56 /storage/disk4
sudo chown jwhiz56 /storage/disk5
sudo chown jwhiz56 /storage/disk6
sudo chown jwhiz56 /storage/disk7
sudo chown jwhiz56 /storage/disk8


corresponding fstab file:

#  1TB SSD
UUID=53f4c033-fca8-4887-a544-a9e84b224e84 / ext4 defaults 0 0
/swap.img       none    swap    sw      0       0
#   960GB SSD
UUID=3AF05EA8F05E6A61 /storage/disk1 ntfs defaults 0 0
#  500GB HD
UUID=2A7045C07045938B /storage/disk2 ntfs defaults 0 0
#  1TB HD
UUID=585CEDA25CED7B60 /storage/disk3 ntfs defaults 0 0
#  500GB HD
UUID=E46AA01E6A9FEB94 /storage/disk4 ntfs defaults 0 0
#  1TB HD
UUID=F4D2F307D2F2CD3C /storage/disk5 ntfs defaults 0 0
# 500GB HD
UUID=406668E36668DB64 /storage/disk6 ntfs defaults 0 0
#  2TB HD
UUID=0C925C7D925C6CE8 /storage/disk7 ntfs defaults 0 0
# 2TB HD
UUID=16884D7E884D5D7D /storage/disk8 ntfs defaults 0 0


/etc/samba/smb.conf file.  lines to be added at the end.
[disk1] 
path = /storage/disk1  
guest ok = yes 
read only = no 
force user = jwhiz56
[disk2]
path = /storage/disk2  
guest ok = yes 
read only = no 
force user = jwhiz56
[disk3]
path = /storage/disk3  
guest ok = yes 
read only = no 
force user = jwhiz56
[disk4]
path = /storage/disk4  
guest ok = yes 
read only = no 
force user = jwhiz56
[disk5]
path = /storage/disk5  
guest ok = yes 
read only = no 
force user = jwhiz56
[disk6]
path = /storage/disk6  
guest ok = yes 
read only = no 
force user = jwhiz56
[disk7]
path = /storage/disk7  
guest ok = yes 
read only = no
force user = jwhiz56
[disk8]
path = /storage/disk8  
guest ok = yes 
read only = no 
force user = jwhiz56

---

### Post by TheFu on 2019-08-12
chown doesn't work on NTFS.

---

### Post by mastablasta on 2019-08-13
NTFS uses is attrib

[https://docs.microsoft.com/en-us/windows-server/administration/windows-commands/attrib](https://docs.microsoft.com/en-us/windows-server/administration/windows-commands/attrib)

not sure how you would use it in linux.

---

### Post by Morbius1 on 2019-08-13
> based on all the pointers so far, I have created my server installation.   Ubuntu 18.04 is installed, updated, SMB installed, unzip installed,  wsdd installed.  Hardware wise, usb 3.0 PCI card installed, 8 drive disk  enclosure plugged in/functional.
...
...
> I think i'm answering my own question, this is what I should do:  (did  this and it works.  can see all 8 disks from my windows explorer)
A minor observation that does not need to be fixed: There is no need to chown a mount point before something is mounted to it. The mounted partition does not inherit the permissions of the mount point. In this case the fstab entry will make it owned by root but make it world writeable so there really isn't anything to fix.

I do have a request -- a plea really -- if you found the wsdd process works as advertised you might consider adding a "affects me too" to the list at launchpad ( [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1831441](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1831441) ). I don't know if they will do anything with just 2 votes and this really needs to be done by default at install time.

---

### Post by TheFu on 2019-08-13
> **mastablasta said:**
> NTFS uses is attrib

[https://docs.microsoft.com/en-us/windows-server/administration/windows-commands/attrib](https://docs.microsoft.com/en-us/windows-server/administration/windows-commands/attrib)

not sure how you would use it in linux.
chattr is the closest. I don't know if that works on NTFS file systems using the ntfs driver.  Depending on the type of data stored on these disks, ntfs could be ok, or a terrible choice, as already mentioned.  If there is any plan to store Linux backups there, then a number of Linux backup options will not work without a Linux file system. You'll need to be careful how you do it.  Whereas if Linux file systems are used, then any sort of backups or files can be stored there and disk performance will be noticeably better.

---

