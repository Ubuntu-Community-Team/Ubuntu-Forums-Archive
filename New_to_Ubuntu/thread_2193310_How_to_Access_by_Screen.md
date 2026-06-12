---
title: "How to Access by Screen"
date: 2013-12-12
forum: New to Ubuntu
---

### Post by alanbr00 on 2013-12-12
Hi, i have a dedicated with ubuntu 13.04 and i have access by SSH, but how do i access by screen? Can't find anywhere how to do, but, everywhere is by screen. Maybe what i'm saying is not compreensible, so, i wanna access ubuntu 13.04 at my dedicated server like remote desktop.

Thanks!

---

### Post by Lars Noodén on 2013-12-12
If you mean [screen](http://manpages.ubuntu.com/manpages/trusty/en/man1/screen.1.html) then the first time connecting, just run it and it will start a new session.

```

screen

```

Then you can detach (close the terminal window for example).  Later when you re-connect, you can tell it to reattach to an existing session.

```

screen -d -r

```

However, if you are just getting started with that and have not yet installed screen, I would recommend  installing [tmux](http://manpages.ubuntu.com/manpages/saucy/en/man1/tmux.1.html) and getting started with that instead.  It does the same things but with newer, cleaner code.

```

tmux

```

and 

```

tmux attach 

```

are the equivalents of the above screen commands.

If you are wanting to run graphical programs from the remote machine and have them displayed locally, then use the [-X](http://manpages.ubuntu.com/manpages/saucy/en/man1/ssh.1.html) option when starting ssh to enable X forwarding.  Then run your program.

```

ssh -X alanbr00@*xx.yy.zz.aa*
firefox

```

That only needs the program to be installed on the remote machine.  The remote machine does not need a full graphical desktop for that to work.

---

### Post by r-senior on 2013-12-12
Or, perhaps you meant VNC?

[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

---

### Post by alanbr00 on 2013-12-12
I'm new on linux, it seems the i only have ssh installed i i'm getting lots of error trying to install packages, can anyone help me, my skype is cap_oliveira1

when i try to install screen or tmux i get this
The program 'tmux' is currently not installed. You can install it by typing:
apt-get install tmux

and when i do apt-get install tmux or screen i get this
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package tmux

Please guys if someone could give me a close assistance i will thank you for life.

---

### Post by Lars Noodén on 2013-12-12
Be sure to refresh the local package database.  Most of the time it might not make a difference, but it does when the packages change. 

```

sudo apt-get update

```

Then try installing screen or tmux, I'd recommend tmux again.  But those are text based.  If you want a graphical use 'ssh -X'.  Or VNC if you have a desktop installed.

---

### Post by alanbr00 on 2013-12-12
Using sudo apt-get update i get this

```
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring Release.gpg
  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)
Err [http://archive.ubuntu.org](http://archive.ubuntu.org) raring-security Release.gpg
  Something wicked happened resolving 'archive.ubuntu.org:http' (-11 - System error)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates Release.gpg
  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)
Ign [http://archive.ubuntu.org](http://archive.ubuntu.org) raring-security Release
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports Release.gpg
  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports Release
Err [http://archive.ubuntu.org](http://archive.ubuntu.org) raring-security/main Sources
  Something wicked happened resolving 'archive.ubuntu.org:http' (-11 - System error)
Err [http://archive.ubuntu.org](http://archive.ubuntu.org) raring-security/restricted Sources
  Something wicked happened resolving 'archive.ubuntu.org:http' (-11 - System error)
Err [http://archive.ubuntu.org](http://archive.ubuntu.org) raring-security/universe Sources
  Something wicked happened resolving 'archive.ubuntu.org:http' (-11 - System error)
Err [http://archive.ubuntu.org](http://archive.ubuntu.org) raring-security/multiverse Sources
  Something wicked happened resolving 'archive.ubuntu.org:http' (-11 - System error)
Err [http://archive.ubuntu.org](http://archive.ubuntu.org) raring-security/main amd64 Packages
  Something wicked happened resolving 'archive.ubuntu.org:http' (-11 - System error)
Err [http://archive.ubuntu.org](http://archive.ubuntu.org) raring-security/restricted amd64 Packages
  Something wicked happened resolving 'archive.ubuntu.org:http' (-11 - System error)
Err [http://archive.ubuntu.org](http://archive.ubuntu.org) raring-security/universe amd64 Packages
  Something wicked happened resolving 'archive.ubuntu.org:http' (-11 - System error)
Err [http://archive.ubuntu.org](http://archive.ubuntu.org) raring-security/multiverse amd64 Packages
  Something wicked happened resolving 'archive.ubuntu.org:http' (-11 - System error)
Err [http://archive.ubuntu.org](http://archive.ubuntu.org) raring-security/main i386 Packages
  Something wicked happened resolving 'archive.ubuntu.org:http' (-11 - System error)
Err [http://archive.ubuntu.org](http://archive.ubuntu.org) raring-security/restricted i386 Packages
  Something wicked happened resolving 'archive.ubuntu.org:http' (-11 - System error)
Err [http://archive.ubuntu.org](http://archive.ubuntu.org) raring-security/universe i386 Packages
  Something wicked happened resolving 'archive.ubuntu.org:http' (-11 - System error)
Err [http://archive.ubuntu.org](http://archive.ubuntu.org) raring-security/multiverse i386 Packages
  Something wicked happened resolving 'archive.ubuntu.org:http' (-11 - System error)
Err [http://archive.ubuntu.org](http://archive.ubuntu.org) raring-security/main Translation-en_US
  Something wicked happened resolving 'archive.ubuntu.org:http' (-11 - System error)
Err [http://archive.ubuntu.org](http://archive.ubuntu.org) raring-security/main Translation-en
  Something wicked happened resolving 'archive.ubuntu.org:http' (-11 - System error)
Err [http://archive.ubuntu.org](http://archive.ubuntu.org) raring-security/multiverse Translation-en_US
  Something wicked happened resolving 'archive.ubuntu.org:http' (-11 - System error)
Err [http://archive.ubuntu.org](http://archive.ubuntu.org) raring-security/multiverse Translation-en
  Something wicked happened resolving 'archive.ubuntu.org:http' (-11 - System error)
Err [http://archive.ubuntu.org](http://archive.ubuntu.org) raring-security/restricted Translation-en_US
  Something wicked happened resolving 'archive.ubuntu.org:http' (-11 - System error)
Err [http://archive.ubuntu.org](http://archive.ubuntu.org) raring-security/restricted Translation-en
  Something wicked happened resolving 'archive.ubuntu.org:http' (-11 - System error)
Err [http://archive.ubuntu.org](http://archive.ubuntu.org) raring-security/universe Translation-en_US
  Something wicked happened resolving 'archive.ubuntu.org:http' (-11 - System error)
Err [http://archive.ubuntu.org](http://archive.ubuntu.org) raring-security/universe Translation-en
  Something wicked happened resolving 'archive.ubuntu.org:http' (-11 - System error)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/main Sources
  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/restricted Sources
  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/universe Sources
  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/multiverse Sources
  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/main amd64 Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/restricted amd64 Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/universe amd64 Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/multiverse amd64 Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/main i386 Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/restricted i386 Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/universe i386 Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/multiverse i386 Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/main Translation-en_US
  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/main Translation-en
  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/multiverse Translation-en_US
  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/multiverse Translation-en
  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/restricted Translation-en_US
  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/restricted Translation-en
  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/universe Translation-en_US
  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/universe Translation-en
  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/main Sources
  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/restricted Sources
  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/universe Sources
  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/multiverse Sources
  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/main amd64 Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/restricted amd64 Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/universe amd64 Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/multiverse amd64 Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/main i386 Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/restricted i386 Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/universe i386 Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/multiverse i386 Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/main Translation-en_US
  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/main Translation-en
  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/multiverse Translation-en_US
  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/multiverse Translation-en
  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/restricted Translation-en_US
  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/restricted Translation-en
  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/universe Translation-en_US
  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/universe Translation-en
  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/main Sources
  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/restricted Sources
  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/universe Sources
  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/multiverse Sources
  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/main amd64 Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/restricted amd64 Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/universe amd64 Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/multiverse amd64 Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/main i386 Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/restricted i386 Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/universe i386 Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/multiverse i386 Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/main Translation-en_US
  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/main Translation-en
  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/multiverse Translation-en_US
  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/multiverse Translation-en
  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/restricted Translation-en_US
  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/restricted Translation-en
  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/universe Translation-en_US
  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-backports/universe Translation-en
  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/raring/Release.gpg)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/raring-updates/Release.gpg)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring-backports/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/raring-backports/Release.gpg)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://archive.ubuntu.org/ubuntu/dists/raring-security/Release.gpg](http://archive.ubuntu.org/ubuntu/dists/raring-security/Release.gpg)  Something wicked happened resolving 'archive.ubuntu.org:http' (-11 - System error)

W: Failed to fetch [http://archive.ubuntu.org/ubuntu/dists/raring-security/main/source/Sources](http://archive.ubuntu.org/ubuntu/dists/raring-security/main/source/Sources)  Something wicked happened resolving 'archive.ubuntu.org:http' (-11 - System error)

W: Failed to fetch [http://archive.ubuntu.org/ubuntu/dists/raring-security/restricted/source/Sources](http://archive.ubuntu.org/ubuntu/dists/raring-security/restricted/source/Sources)  Something wicked happened resolving 'archive.ubuntu.org:http' (-11 - System error)

W: Failed to fetch [http://archive.ubuntu.org/ubuntu/dists/raring-security/universe/source/Sources](http://archive.ubuntu.org/ubuntu/dists/raring-security/universe/source/Sources)  Something wicked happened resolving 'archive.ubuntu.org:http' (-11 - System error)

W: Failed to fetch [http://archive.ubuntu.org/ubuntu/dists/raring-security/multiverse/source/Sources](http://archive.ubuntu.org/ubuntu/dists/raring-security/multiverse/source/Sources)  Something wicked happened resolving 'archive.ubuntu.org:http' (-11 - System error)

W: Failed to fetch [http://archive.ubuntu.org/ubuntu/dists/raring-security/main/binary-amd64/Packages](http://archive.ubuntu.org/ubuntu/dists/raring-security/main/binary-amd64/Packages)  Something wicked happened resolving 'archive.ubuntu.org:http' (-11 - System error)

W: Failed to fetch [http://archive.ubuntu.org/ubuntu/dists/raring-security/restricted/binary-amd64/Packages](http://archive.ubuntu.org/ubuntu/dists/raring-security/restricted/binary-amd64/Packages)  Something wicked happened resolving 'archive.ubuntu.org:http' (-11 - System error)

W: Failed to fetch [http://archive.ubuntu.org/ubuntu/dists/raring-security/universe/binary-amd64/Packages](http://archive.ubuntu.org/ubuntu/dists/raring-security/universe/binary-amd64/Packages)  Something wicked happened resolving 'archive.ubuntu.org:http' (-11 - System error)

W: Failed to fetch [http://archive.ubuntu.org/ubuntu/dists/raring-security/multiverse/binary-amd64/Packages](http://archive.ubuntu.org/ubuntu/dists/raring-security/multiverse/binary-amd64/Packages)  Something wicked happened resolving 'archive.ubuntu.org:http' (-11 - System error)

W: Failed to fetch [http://archive.ubuntu.org/ubuntu/dists/raring-security/main/binary-i386/Packages](http://archive.ubuntu.org/ubuntu/dists/raring-security/main/binary-i386/Packages)  Something wicked happened resolving 'archive.ubuntu.org:http' (-11 - System error)

W: Failed to fetch [http://archive.ubuntu.org/ubuntu/dists/raring-security/restricted/binary-i386/Packages](http://archive.ubuntu.org/ubuntu/dists/raring-security/restricted/binary-i386/Packages)  Something wicked happened resolving 'archive.ubuntu.org:http' (-11 - System error)

W: Failed to fetch [http://archive.ubuntu.org/ubuntu/dists/raring-security/universe/binary-i386/Packages](http://archive.ubuntu.org/ubuntu/dists/raring-security/universe/binary-i386/Packages)  Something wicked happened resolving 'archive.ubuntu.org:http' (-11 - System error)

W: Failed to fetch [http://archive.ubuntu.org/ubuntu/dists/raring-security/multiverse/binary-i386/Packages](http://archive.ubuntu.org/ubuntu/dists/raring-security/multiverse/binary-i386/Packages)  Something wicked happened resolving 'archive.ubuntu.org:http' (-11 - System error)

W: Failed to fetch [http://archive.ubuntu.org/ubuntu/dists/raring-security/main/i18n/Translation-en_US](http://archive.ubuntu.org/ubuntu/dists/raring-security/main/i18n/Translation-en_US)  Something wicked happened resolving 'archive.ubuntu.org:http' (-11 - System error)

W: Failed to fetch [http://archive.ubuntu.org/ubuntu/dists/raring-security/main/i18n/Translation-en](http://archive.ubuntu.org/ubuntu/dists/raring-security/main/i18n/Translation-en)  Something wicked happened resolving 'archive.ubuntu.org:http' (-11 - System error)

W: Failed to fetch [http://archive.ubuntu.org/ubuntu/dists/raring-security/multiverse/i18n/Translation-en_US](http://archive.ubuntu.org/ubuntu/dists/raring-security/multiverse/i18n/Translation-en_US)  Something wicked happened resolving 'archive.ubuntu.org:http' (-11 - System error)

W: Failed to fetch [http://archive.ubuntu.org/ubuntu/dists/raring-security/multiverse/i18n/Translation-en](http://archive.ubuntu.org/ubuntu/dists/raring-security/multiverse/i18n/Translation-en)  Something wicked happened resolving 'archive.ubuntu.org:http' (-11 - System error)

W: Failed to fetch [http://archive.ubuntu.org/ubuntu/dists/raring-security/restricted/i18n/Translation-en_US](http://archive.ubuntu.org/ubuntu/dists/raring-security/restricted/i18n/Translation-en_US)  Something wicked happened resolving 'archive.ubuntu.org:http' (-11 - System error)

W: Failed to fetch [http://archive.ubuntu.org/ubuntu/dists/raring-security/restricted/i18n/Translation-en](http://archive.ubuntu.org/ubuntu/dists/raring-security/restricted/i18n/Translation-en)  Something wicked happened resolving 'archive.ubuntu.org:http' (-11 - System error)

W: Failed to fetch [http://archive.ubuntu.org/ubuntu/dists/raring-security/universe/i18n/Translation-en_US](http://archive.ubuntu.org/ubuntu/dists/raring-security/universe/i18n/Translation-en_US)  Something wicked happened resolving 'archive.ubuntu.org:http' (-11 - System error)

W: Failed to fetch [http://archive.ubuntu.org/ubuntu/dists/raring-security/universe/i18n/Translation-en](http://archive.ubuntu.org/ubuntu/dists/raring-security/universe/i18n/Translation-en)  Something wicked happened resolving 'archive.ubuntu.org:http' (-11 - System error)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring/main/source/Sources](http://archive.ubuntu.com/ubuntu/dists/raring/main/source/Sources)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring/restricted/source/Sources](http://archive.ubuntu.com/ubuntu/dists/raring/restricted/source/Sources)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring/universe/source/Sources](http://archive.ubuntu.com/ubuntu/dists/raring/universe/source/Sources)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring/multiverse/source/Sources](http://archive.ubuntu.com/ubuntu/dists/raring/multiverse/source/Sources)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring/main/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/raring/main/binary-amd64/Packages)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring/restricted/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/raring/restricted/binary-amd64/Packages)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring/universe/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/raring/universe/binary-amd64/Packages)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring/multiverse/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/raring/multiverse/binary-amd64/Packages)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/raring/main/binary-i386/Packages)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring/restricted/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/raring/restricted/binary-i386/Packages)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/raring/universe/binary-i386/Packages)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring/multiverse/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/raring/multiverse/binary-i386/Packages)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring/main/i18n/Translation-en_US](http://archive.ubuntu.com/ubuntu/dists/raring/main/i18n/Translation-en_US)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring/main/i18n/Translation-en](http://archive.ubuntu.com/ubuntu/dists/raring/main/i18n/Translation-en)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring/multiverse/i18n/Translation-en_US](http://archive.ubuntu.com/ubuntu/dists/raring/multiverse/i18n/Translation-en_US)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring/multiverse/i18n/Translation-en](http://archive.ubuntu.com/ubuntu/dists/raring/multiverse/i18n/Translation-en)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring/restricted/i18n/Translation-en_US](http://archive.ubuntu.com/ubuntu/dists/raring/restricted/i18n/Translation-en_US)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring/restricted/i18n/Translation-en](http://archive.ubuntu.com/ubuntu/dists/raring/restricted/i18n/Translation-en)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring/universe/i18n/Translation-en_US](http://archive.ubuntu.com/ubuntu/dists/raring/universe/i18n/Translation-en_US)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring/universe/i18n/Translation-en](http://archive.ubuntu.com/ubuntu/dists/raring/universe/i18n/Translation-en)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring-updates/main/source/Sources](http://archive.ubuntu.com/ubuntu/dists/raring-updates/main/source/Sources)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring-updates/restricted/source/Sources](http://archive.ubuntu.com/ubuntu/dists/raring-updates/restricted/source/Sources)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring-updates/universe/source/Sources](http://archive.ubuntu.com/ubuntu/dists/raring-updates/universe/source/Sources)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring-updates/multiverse/source/Sources](http://archive.ubuntu.com/ubuntu/dists/raring-updates/multiverse/source/Sources)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring-updates/main/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/raring-updates/main/binary-amd64/Packages)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring-updates/restricted/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/raring-updates/restricted/binary-amd64/Packages)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring-updates/universe/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/raring-updates/universe/binary-amd64/Packages)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring-updates/multiverse/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/raring-updates/multiverse/binary-amd64/Packages)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring-updates/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/raring-updates/main/binary-i386/Packages)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring-updates/restricted/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/raring-updates/restricted/binary-i386/Packages)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring-updates/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/raring-updates/universe/binary-i386/Packages)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring-updates/multiverse/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/raring-updates/multiverse/binary-i386/Packages)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring-updates/main/i18n/Translation-en_US](http://archive.ubuntu.com/ubuntu/dists/raring-updates/main/i18n/Translation-en_US)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring-updates/main/i18n/Translation-en](http://archive.ubuntu.com/ubuntu/dists/raring-updates/main/i18n/Translation-en)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring-updates/multiverse/i18n/Translation-en_US](http://archive.ubuntu.com/ubuntu/dists/raring-updates/multiverse/i18n/Translation-en_US)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring-updates/multiverse/i18n/Translation-en](http://archive.ubuntu.com/ubuntu/dists/raring-updates/multiverse/i18n/Translation-en)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring-updates/restricted/i18n/Translation-en_US](http://archive.ubuntu.com/ubuntu/dists/raring-updates/restricted/i18n/Translation-en_US)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring-updates/restricted/i18n/Translation-en](http://archive.ubuntu.com/ubuntu/dists/raring-updates/restricted/i18n/Translation-en)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring-updates/universe/i18n/Translation-en_US](http://archive.ubuntu.com/ubuntu/dists/raring-updates/universe/i18n/Translation-en_US)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring-updates/universe/i18n/Translation-en](http://archive.ubuntu.com/ubuntu/dists/raring-updates/universe/i18n/Translation-en)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring-backports/main/source/Sources](http://archive.ubuntu.com/ubuntu/dists/raring-backports/main/source/Sources)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring-backports/restricted/source/Sources](http://archive.ubuntu.com/ubuntu/dists/raring-backports/restricted/source/Sources)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring-backports/universe/source/Sources](http://archive.ubuntu.com/ubuntu/dists/raring-backports/universe/source/Sources)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring-backports/multiverse/source/Sources](http://archive.ubuntu.com/ubuntu/dists/raring-backports/multiverse/source/Sources)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring-backports/main/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/raring-backports/main/binary-amd64/Packages)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring-backports/restricted/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/raring-backports/restricted/binary-amd64/Packages)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring-backports/universe/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/raring-backports/universe/binary-amd64/Packages)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring-backports/multiverse/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/raring-backports/multiverse/binary-amd64/Packages)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring-backports/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/raring-backports/main/binary-i386/Packages)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring-backports/restricted/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/raring-backports/restricted/binary-i386/Packages)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring-backports/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/raring-backports/universe/binary-i386/Packages)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring-backports/multiverse/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/raring-backports/multiverse/binary-i386/Packages)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring-backports/main/i18n/Translation-en_US](http://archive.ubuntu.com/ubuntu/dists/raring-backports/main/i18n/Translation-en_US)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring-backports/main/i18n/Translation-en](http://archive.ubuntu.com/ubuntu/dists/raring-backports/main/i18n/Translation-en)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring-backports/multiverse/i18n/Translation-en_US](http://archive.ubuntu.com/ubuntu/dists/raring-backports/multiverse/i18n/Translation-en_US)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring-backports/multiverse/i18n/Translation-en](http://archive.ubuntu.com/ubuntu/dists/raring-backports/multiverse/i18n/Translation-en)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring-backports/restricted/i18n/Translation-en_US](http://archive.ubuntu.com/ubuntu/dists/raring-backports/restricted/i18n/Translation-en_US)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring-backports/restricted/i18n/Translation-en](http://archive.ubuntu.com/ubuntu/dists/raring-backports/restricted/i18n/Translation-en)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring-backports/universe/i18n/Translation-en_US](http://archive.ubuntu.com/ubuntu/dists/raring-backports/universe/i18n/Translation-en_US)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring-backports/universe/i18n/Translation-en](http://archive.ubuntu.com/ubuntu/dists/raring-backports/universe/i18n/Translation-en)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)

E: Some index files failed to download. They have been ignored, or old ones used instead.


```

I have a ubuntu 13.04 64bit server

---

### Post by Lars Noodén on 2013-12-12
Did you set anything for the proxy when did the installation or is the connection straight-through?

Also are you able to do a DNS look up?

```

host archive.ubuntu.com

```

---

### Post by alanbr00 on 2013-12-12
I did not set the installation.

> root@ubuntu:~# host archive.ubuntu.com
archive.ubuntu.com has address 91.189.92.177
archive.ubuntu.com has address 91.189.92.200
archive.ubuntu.com has address 91.189.92.201
archive.ubuntu.com has address 91.189.92.202
archive.ubuntu.com has address 91.189.91.13
archive.ubuntu.com has address 91.189.91.14
archive.ubuntu.com has address 91.189.91.15
archive.ubuntu.com has address 91.189.92.156
archive.ubuntu.com has address 91.189.92.176
archive.ubuntu.com has IPv6 address 2001:67c:1360:8c01::1a
archive.ubuntu.com has IPv6 address 2001:67c:1360:8c01::22
archive.ubuntu.com has IPv6 address 2001:67c:1360:8c01::23
archive.ubuntu.com has IPv6 address 2001:67c:1360:8c01::15
archive.ubuntu.com has IPv6 address 2001:67c:1360:8c01::18
archive.ubuntu.com has IPv6 address 2001:67c:1360:8c01::19



---

### Post by Lars Noodén on 2013-12-12
Does the file "/etc/apt/apt.conf" exist?  If so, what is in it?

---

### Post by alanbr00 on 2013-12-12
how do i get to the file?

---

### Post by Lars Noodén on 2013-12-12
It may not exist.  That's ok.  But you can see if it is there using [less](http://manpages.ubuntu.com/manpages/saucy/en/man1/less.1.html)

```

less /etc/apt/apt.conf

```

---

