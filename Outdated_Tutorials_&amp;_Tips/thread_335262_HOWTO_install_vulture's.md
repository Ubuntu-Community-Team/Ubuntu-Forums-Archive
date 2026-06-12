---
title: "HOWTO: install vulture's"
date: 2007-01-10
forum: Outdated Tutorials &amp; Tips
---

### Post by Tharquil on 2007-01-10
Okay, first of all i'm a total n00b to Ubuntu. I wished to install Vulture's to try NetHack the 21st century way but could not find it in the repositories. Neither could i find a satisfying installation procedure. Finding bits of informations here and there, i finally managed to install it. Thus, this post describes how to install Vulture's but i fear my (un)skills with Ubuntu won't allow me to give support in case of trouble.

[SIZE="3"]**Installing Vulture's**[/SIZE]

Note: This procedure has been tested on Ubuntu 6.10 (Edgy Eft).

1. Get the [game]("http://www.darkarts.co.za/projects/vultures/attachment/wiki/downloads/2.1.0/vultures-2.1.0-full_unix-1.bin.sh")'s latest Unix auto compiler/installer version from the [official site]("http://www.darkarts.co.za/projects/vultures") 
and save the file wherever you like.

2. Install the tools needed to compile the game.
```
sudo apt-get install byacc flex libsdl1.2-dev libsdl-image1.2-dev libsdl-mixer1.2-dev libsdl-ttf2.0-dev
```

3. Go to the file's directory and make it executable.
```
chmod +x vultures-2.1.0-full_unix-1.bin.sh
```

4. Execute the auto compiler/installer.
```
./vultures-2.1.0-full_unix-1.bin.sh
```

And voilà! A few compilation warnings later, the game is installed in the vulture directory in your home's. You can play either Vulture's Eye or Claw.

Have fun!

---

### Post by jpcrow on 2007-01-19
Sweet, I'm a total newbie to Linux and you saved my life! Thank you soo much! =)

---

### Post by Pnin on 2007-02-26
Thanks a bunch Tharquil, you finally solved a problem I couldn't since I first installed Ubuntu (Dapper) and wondered where the hell was Nethack-vultures.

For a summary of my last quandaries, check the ticket I opened in Vultures site:
[http://www.darkarts.co.za/projects/vultures/ticket/10](http://www.darkarts.co.za/projects/vultures/ticket/10)

Bookmarked.

---

### Post by dannystaple on 2007-06-11
Since the vultures site is down, and I can assume I am neither the first, nor will be the last to look for it, I found a vultures repo, with releases at [http://usrsrc.org/svn/vultures/](http://usrsrc.org/svn/vultures/) thanks to the vultures wikipedia page. 
I actually picked up the RPM nethack-vultures-2.1.0-1.fc5.i386.rpm, and ran it through alien.
Alien converts packages for use in different distro's:
> 
sudo alien -k nethack-vultures-2.1.0-1.fc5.i386.rpm
sudo gdebi nethack-vultures_2.1.0-1.fc5_i386.deb 

Suffice to say, this worked a treat.

---

### Post by Jeruleus on 2007-06-18
> **dannystaple said:**
> Since the vultures site is down, and I can assume I am neither the first, nor will be the last to look for it, I found a vultures repo, with releases at [http://usrsrc.org/svn/vultures/](http://usrsrc.org/svn/vultures/) thanks to the vultures wikipedia page. 
I actually picked up the RPM nethack-vultures-2.1.0-1.fc5.i386.rpm, and ran it through alien.
Alien converts packages for use in different distro's:

Suffice to say, this worked a treat.

Hey guys.  I'm really new to linux and the ubuntu distro especially.  I've followed these instructions and I think vultures is installed correctly - there were no error reports after running the sudo gedit, and there're icons in menu bar > applications > games - but when I try to run it, nothing happens.  Any suggestions?  Thanks in advance for your time.

UPDATE**:  OK, so I was able to find out how to "run" it.  But it crashes immediately.  I get a series of errors when I try to launch from a terminal.

```
ERROR: could not open log file vultures_log.txt for appending: Permission denied
[./vultureseye]: Program initialization has failed.
Program initialization has failed.
ERROR: could not open log file vultures_log.txt for appending: Permission denied
[./vultureseye]: Report error to "games".
Report error to "games".
ERROR: could not open log file vultures_log.txt for appending: Permission denied
[./vultureseye]: FATAL: Actual size of gametiles.bin does not match the expected size!
Are you sure you are using the gametiles.bin that was built together with this executable?

FATAL: Actual size of gametiles.bin does not match the expected size!
Are you sure you are using the gametiles.bin that was built together with this executable?
```

UPDATE**: Issue resolved.  Snagged the rpm from [here,]("http://rpmfind.net/linux/RPM/fedora/extras/5/i386/nethack-vultures-2.1.0-9.fc5.i386.html") and followed the above instructions.  Thank you much fellas.

---

### Post by HorstJENS on 2007-08-12
a thousand thanks, and may you ascend many times !

I was so unlucky that i could install both vultures only on windows box only and not on my ubuntu box. Your guide-posting made it clear to me... i was to stupid to figure out that all i needed was the full.sh file from the website instead of the full.tar.gz file. Now i feel a better (wisdom +1).

---

### Post by HorstJENS on 2007-08-15
Anyone know where to find the **.slashemrc** file ? according to the manual, that is the file where i can set permanent options for the game.
I want to have the variable showxp, showdmg and time always on.
All i found were some vultures-claw specific config files that allow to change thinks like wall-height.

---

### Post by zerothis on 2008-12-19
the .slashemrc file must be created from scratch and placed in your home directory.

---

