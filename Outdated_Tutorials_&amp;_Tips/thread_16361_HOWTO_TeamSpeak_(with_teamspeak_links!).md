---
title: "HOWTO: TeamSpeak (with teamspeak:// links!)"
date: 2005-02-21
forum: Outdated Tutorials &amp; Tips
---

### Post by JConnell on 2005-02-21
Download the linux client from the [TeamSpeak website](http://www.goteamspeak.com/downloads.php)

```

user@ubuntu:~ $ tar -jxf ts2_client_rc2_2032.tar.bz2
user@ubuntu:~ $ cd ts2_client_rc2_2032
user@ubuntu:~ $ sudo chmod 755 setup.sh
user@ubuntu:~ $ sudo sh setup.sh

```
Install to: /opt/TeamSpeak2RC2 (Should be the default)

```

user@ubuntu:~ $ sudo ln -s /opt/TeamSpeak2RC2/TeamSpeak /usr/bin/
user@ubuntu:~ $ TeamSpeak

```
Congratulations, TeamSpeak is now installed!



If you want to open "teamspeak://" links with firefox:

Launch firefox and type about:config in the address bar

Right-click and select New->String
Name: "network.protocol-handler.app.teamspeak"
Value: "TeamSpeak"

Right-click and select New->Boolean
Name: network.protocol-handler.external.teamspeak
Value: "true"

Now you can open teamspeak:// links, which will automaticly launch TeamSpeak and connect to the specified server when you click them! :D

---

### Post by KingArthur10 on 2005-04-23
Thanks for the help!  Finally got TeamSpeak working.  :-)  Thankee again!

---

### Post by sOnIc on 2005-07-01
Hi! 
I follow all steps but when i try to run TeamSpeak...

```
sonic@ubuntu:~$ TeamSpeak
Qt: Locales not supported on X server
```

What it means ?? (im absolutely new to linux) :roll:
Sorry about my bad english :-# 
Cheers sOnIc

---

### Post by scruffy on 2005-12-12
Works perfectly for me :D

Thanks

All the best..scruffy :D

---

### Post by Cogito on 2006-04-30
Getting an error on when I try and run the installer binary.  
Any suggestions?

```

user@ubuntu:~/ts2_client_rc2_2032$ sudo sh setup.sh
setup.sh: line 19: setup.data/installer/installer: cannot execute binary file

```

---

### Post by BlastXng on 2006-05-05
[QUOTE=Cogito]Getting an error on when I try and run the installer binary.  
Any suggestions?

```

user@ubuntu:~/ts2_client_rc2_2032$ sudo sh setup.sh
setup.sh: line 19: setup.data/installer/installer: cannot execute binary file

```[/QUOTE]

Try what was first shown above. I had problems with TeamSpeak after I used AutoMatix to install some software. I had to re-install TeamSpeak twice to get it to work. I followed the information at the begining of the post.

---

### Post by Neonsolid on 2006-05-06
*

---

### Post by Sakhaara on 2006-12-02
Thanks man :-D :-D :-D

---

### Post by stu_u2k on 2007-01-03
I have tried installing it multiple ways & i just cant get the Autoinstall to work or the manual install either, i am abit of a ubuntu n00b so maybe its something silly.

I going to paste what i have tried, i have also had a mate SSH in & look at it, thou he's much more Gentoo orientated than ubuntu & he was lost too.

First of all i will show you the Auto Installation problem...

"USER@COMPUTER:~/Desktop/teamspeak$ sudo sh setup.sh
setup.sh: 14: Syntax error: Bad substitution"

After trying loads of different things the *automated* way i gave up & thought i would install it the manual way, so i have copied the contents of "/image/" to "/opt/teamspeak" then edited the teamspeak file so it look like...

"#!/bin/sh
#
# This starup script will set the correct library path
# and then startup the teamspeak binary.
#

export LD_LIBRARY_PATH=/opt/teamspeak:$LD_LIBRARY_PATH
/opt/teamspeak/TeamSpeak.bin $*"

Then when i try to run it i get...


"USER@COMPUTER:~$ cd /opt/teamspeak
USER@COMPUTER:/opt/teamspeak$ ./TeamSpeak
./TeamSpeak: 8: /opt/teamspeak/TeamSpeak.bin: not found
USER@COMPUTER:/opt/teamspeak$ sudo ./TeamSpeak
./TeamSpeak: 8: /opt/teamspeak/TeamSpeak.bin: not found"

At this point i would forgive you for thinking i was abit useless and was in the wrong folder or something of the like so to prove otherwise...

"USER@COMPUTER:/opt/teamspeak$ ls
clicense.txt  libborqt-6.9-qt2.3.so  manual      TeamSpeak
client_sdk    libHVDI.so.0.8.0       Readme.txt  TeamSpeak~
icon.xpm      libspeex.so.1.0.0      sounds      TeamSpeak.bin"

I have all the correct permissions have tried all steps as "USER/ROOT/SUDO" all of which give me the same errors.
So i am completely lost, any advise would be appreciated.

---

### Post by ToeKing on 2007-01-04
remove the sh.  just do "sudo setup.sh"

---

### Post by Monkeysuit on 2007-02-10
Maybe i´m just blind, but I have tried a multiple of ways and get this error.

setup.data/installer/installer: No such file or directory

I have done all the path inclusions in the script files, but no joy at all. Any ideas?

---

### Post by hamil on 2007-03-11
Hello!

As the earlier poster, I am not getting there either...

Running sudo sh setup.sh gives:
```
setup.sh: 14: Syntax error: Bad substitution
```

Whereas sudo setup.sh gives:
```
sudo: setup.sh: command not found
```

Any guidance would be highly appreciated...

---

### Post by simplyw00x on 2007-03-11
```
carl@puzzlement:~$ apt-cache policy teamspeak-client
teamspeak-client:
  Installed: 2.0.32-2
  Candidate: 2.0.32-2
  Version table:
 *** 2.0.32-2 0
        500 http://gb.archive.ubuntu.com feisty/multiverse Packages
        100 /var/lib/dpkg/status
carl@puzzlement:~$ 
```
It's in fiesty

---

### Post by hamil on 2007-03-12
Good that it has found it's way into Feisty, but it would still be nice to know why this error occurs, and what one can do to get around that error.

Thanks for the tip, will see if I download it later.

Edit:
And for the ones who does not want to add the Feisty to their repos, this would the link for the deb file:
[http://gb.archive.ubuntu.com/ubuntu/pool/multiverse/t/teamspeak-client/teamspeak-client_2.0.32-2_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/multiverse/t/teamspeak-client/teamspeak-client_2.0.32-2_i386.deb)
And you do get an error for missing dependencies, if you do not run Feisty (libc6)

---

### Post by noenter1 on 2007-03-20
The correct code would be:
```
sudo ./setup.sh
```
Hope this works for you hamil it did for me.



EDIT: Official Howto is @ [https://help.ubuntu.com/community/TeamSpeak](https://help.ubuntu.com/community/TeamSpeak)

---

