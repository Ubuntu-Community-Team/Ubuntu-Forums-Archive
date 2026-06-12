---
title: "erratic repos behaviour"
date: 2006-02-20
forum: Repositories &amp; Backports
---

### Post by newblacknoise on 2006-02-20
i am having a very strange problem when trying to connect to the repositories.
i have just installed breezy, and have managed to get my internet connection working enough so that i can browse with firefox, and download enough packages through synaptic and/or apt-get to setup my wireless adaptor.

however, my ability to connect to the repos is not consistent. for the last few days since installing, i can sometimes connect to the repos and all is well, but more often i get this message when trying 'sudo apt-get update':

```
0% [Connecting to au.archive.ubuntu.com (1.0.0.0)] [Connecting to security.ubun
```

it sits there for so long i end up pressing CTRL+C to quit early. one thing which sometimes helps is if i ping the repo, ie. 'ping au.archive.ubuntu.com'. if i get a return 'pong', i can usually use synaptic or apt-get to connect, and this time it'll work. but it never lasts. i can connect one minute, then LITERALLY try to connect 30 seconds later, and it's all gone again. i'm quite stumped. has anyone experienced this kind of behaviour before? i can't tell if it's my internet setup, or the repo servers, or what.

below i will post my sources.list, just to pre-empt someone asking:

```

# Automatically generated sources.list
# http://www.ubuntulinux.nl/source-o-matic
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb http://au.archive.ubuntu.com/ubuntu breezy main restricted
deb http://au.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb http://security.ubuntu.com/ubuntu breezy-security main restricted

# Ubuntu supported packages (sources, GPG key: 437D05B5)
deb-src http://au.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://au.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb http://au.archive.ubuntu.com/ubuntu breezy universe multiverse
deb http://au.archive.ubuntu.com/ubuntu breezy-updates universe multiverse
deb http://security.ubuntu.com/ubuntu breezy-security universe multiverse

# Ubuntu community supported packages (sources, GPG key: 437D05B5)
deb-src http://au.archive.ubuntu.com/ubuntu breezy universe multiverse
deb-src http://au.archive.ubuntu.com/ubuntu breezy-updates universe multiverse
deb-src http://security.ubuntu.com/ubuntu breezy-security universe multiverse

```

i'm going to be away from my computer for a few hours now, so hopefully when i return someone will have some advice for me. please help, it's driving me slightly up the wall.

thanks very much.

---

### Post by anti_microsoft on 2006-02-20
I am having the same problem, although mine never works. I like Ubuntu, but without apt it serves me no point. I came here today to post about this problem and seen yours as a chance to voice my problems as well. The problem I have is not just with ubuntu but with any debian based distro I try. Does apt use a weird port or something? I would like to use ubuntu. Someone please help us.

---

### Post by anti_microsoft on 2006-02-20
Shortly after posting that message I figured it out. You have to go into admin and set up you network manually. that worked for me.

---

### Post by newblacknoise on 2006-02-20
can you be more specific about how you fixed the problem?
when i go into System -> Administration -> Networking, it seems like my network is set up just fine. like i've said, i can use all other internet services without any troubles, just not the repos. was there a specific action you took to fix your setup?

---

### Post by newblacknoise on 2006-02-22
just in case anyone DOES want to respond, i have some clarifications to make about my problem:

1. it's not just the repos in my sources.list, it's the others too. i've tried gb.archive.ubuntu.com as well, with no improved results (other than when one isn't working, sometimes the other one is.

2. i've also noticed that when i boot ubuntu, one of the lines that flashes by is something about 'synchronizing system clock with ntp.ubuntu.blahblah.....'. i was using an installation of hoary last week, and this 'passed' just fine, but now since i've installed breezy, it fails every time. i'm not sure what it's trying to do exactly, but the fact that it's trying to connect to an external server, and failing, seems relevant.

the above two points seem to indicate that there's some kind of kooky settings messing up my internet connection (no surprises there). anyone had this problem before, and maybe know how to fix it?

i should also reconfirm that firefox allows me to browse beautifully, and when i CAN connect to the repos, they do seem to operate at a nice healthy download speed.

me...stumped. really.

---

### Post by lerrup on 2006-02-22
Can't help I'm afraid - have you posted this elsewhere on the forum?

---

### Post by newblacknoise on 2006-02-22
i've also posted a message in the main Ubuntu 5.10 GNOME forum a few days ago, but this new thread is probably a bit clearer in explaining my problem. i just thought this was a more appropriate forum to place it in.

maybe an admin should move it to another area or something? i don't know. it feels like there must be a simple solution, but i just don't know what it is :-?

---

### Post by dbw on 2006-02-23
I have also seen ubuntu-security fail erraticly.  Apt-get says it cannot connect - for some reason this had happened more often when I used Synaptic than when I used apt-get from the command line.  Note that it often connected, as well, so I didn't simply have the bad sources.list which seems to be responsible for 45% of the problems on these forums.

I ended up just replacing the default ubuntu repos with mirrors I found somewhere.  I have had absolutely no problems since.  So, I guess, look around for those.  Maybe it was just a traffic issue, or my wireless card being impatient, I don't know.  Anyhow, good luck!

---

### Post by kartikeya_sri on 2006-02-27
I am having same kind of problem.
when I try to apt-get update I get the following message.

kartikeya@ubuntu:~$ sudo apt-get update
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy Release.gpg
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates Release.gpg
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg](http://au.archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg)  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg](http://au.archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg)  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/breezy-security/Release.gpg)  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Reading package lists... Done
W: Couldn't stat source package list [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates/universe Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_breezy-updates_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates/multiverse Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_breezy-updates_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
[PHP][/PHP]

I have tried almost all the repositories listed by others in [http://www.ubuntuforums.org/showthread.php?t=87946&page=4](http://www.ubuntuforums.org/showthread.php?t=87946&page=4) post.
My internet is working fine and I am able to download anything using my web-browser and also I can use bittorrent.

I am very new to Linux, and this is my first Linux installation.

---

