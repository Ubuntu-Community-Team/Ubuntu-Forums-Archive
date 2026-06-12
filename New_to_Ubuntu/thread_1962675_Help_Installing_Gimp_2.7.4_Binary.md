---
title: "Help Installing Gimp 2.7.4 Binary"
date: 2012-04-21
forum: New to Ubuntu
---

### Post by Sennaria on 2012-04-21
Background:

I am "new" to Ubuntu as it's been almost 15 years since messing in any way with a linux environment (back then it was tiptoeing into RedHat).  It is my hope to go from Ubuntu installed with Wubi to a complete Windowless environment once I have my feet on the ground.  I use my computer mainly for graphics programs, and 2 games (WoW and SL).

I installed 3 days ago.  I finally got 11.10 to recognize my Wacom Bamboo Tablet yesterday (it was a 2011 release of tablet).

I use GIMP, on Windows I am using the 2.7.5 release and prefer to not have to go back down to 2.6 until 2.8 is released, I have to many preferences I need in the newer releases.  I, as well am studying the Bash commands section of this website refreshing myself on command lines for the terminal.

So now my problem is (3 days into it) finding a binary of Gimp post 2.6.  And did so yesterday, so now I'll post the information I'm needing as I've exhausted thus far all the resources and my brain. :)

I downloaded the binary for Gimp 2.7.4 from [http://alcides-mp.com/software/gimp-2-7-4-binaries-for-ubuntu]("http://alcides-mp.com/software/gimp-2-7-4-binaries-for-ubuntu/") and the archive is on my desktop.

I finally as well figured out I needed 7 zip to get the 7z x command line to work (duh) so that is all straight.

The way he has the binary set up it needs to be extracted into /opt. He says to do 
$ cd /opt
$ sudo 7z x /where-you-downloaded-the-file/gimp-2.7.4-linux-amd64.7z (I of course changed the wydtf to Desktop.)

When I do that..I get
[I]7-Zip [64] 9.20 Copyright (c) 1999-2010 Igor Pavlov 2010-11-18
p7zip Version 9.20 (locale=en_US.UTF-8,Utf16=on,HugeFiles=on,4 CPUs)


Error:
there is no such archive[/I]


So I thought ok..what if I do this and run it from Desktop into /opt (which makes more sense to me) 
cd ~/Desktop
sudo 7z x /gimp-2.7.4-linux-amd64.7z/opt

and I get the same error message of no such archive.

I have extracted it straight onto the Desktop, but it just stares at me doing nothing (as if chiding me that it should duhhh be in /opt)....

Any ideas as to how to get it extracted there?

I thought about pulling it from Desktop into /opt already extracted but I can't due to permissions not allowing me to.

Thanks ahead of time for any insights!

Edit:

Ok so extracted to Desktop and did:
sudo cp Desktop/gimp-2.7.4 /opt

in hopes it would work but it didn't...I got cp: cannot stat `Desktop/gimp-2.7.4': No such file or directory

In time I want to learn to compile etc but that comes after I have the basic set up and can work within the ubuntu environment. I am wanting a version of Gimp that has the single window mode and as I am using 2.7.5 in Windows 7, I would like to get as closer to that version as possible as I utilize many of the changes within it.

*goes back to her finagling*

-jorden (who is quickly learning so much and enjoying myself immensely)

Edit:

Fixed it by

@ubuntu:~$ sudo cp ./Desktop/gimp-2.7.4 /opt
[sudo] password for xxx: 
cp: omitting directory `./Desktop/gimp-2.7.4'
xxx@ubuntu:~$ 

so I changed it to be recursive 
sudo cp -r ./Desktop/gimp-2.7.4 /opt

---

### Post by Favux on 2012-04-21
Hi Sennaria,

Welcome to Ubuntu forums!

Not sure I understand his instructions but this should be what he's asking:
```

cd ~/Desktop

wget http://alcides-mp.com/wp-content/uploads/2011/12/gimp-2.7.4-linux-amd64.7z

cd /opt

sudo 7z x ~/Desktop/gimp-2.7.4-linux-amd64.7z
```

Opt is already a directory of the file system or root /.  Not sure why he's working in there instead of /usr/share, but OK.

Basically you're a little rusty on directories.

~/ = /home/yourusername

cd = change directory

cd .. = go back down one directory

pwd = print working directory, good to find out where you are if you lose track

The stat problems and stuff is because your not where you think you are.

---

