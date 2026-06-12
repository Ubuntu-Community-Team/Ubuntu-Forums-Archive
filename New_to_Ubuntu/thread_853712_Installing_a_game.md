---
title: "Installing a game"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by jimi_hendrix on 2008-07-08
:guitar:

so i found a bunch of cool games on this forum post

[http://ubuntuforums.org/showthread.php?t=427205]("http://ubuntuforums.org/showthread.php?t=427205")

most of them have installed perfectly except for the MMORPG PlaneShift

ive tried the command
```
sudo apt-get update
sudo apt-get install PlaneShift
```

yes this comes up when i enter the command to install it

```
vincent@vincent-laptop:~$ sudo apt-get install PlaneShift
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package PlaneShift

```

the file is not in synaptic either

what do i do?

(yes i downloaded the linux version not the macOS or vista one)

---

### Post by st33med on 2008-07-08
Packages in the repoes do not have caps...
Try:
```
sudo apt-get install planeshift
```

---

### Post by Car60n on 2008-07-08
> yes i downloaded the linux version not the macOS or vista one
by the looks of it you downloaded the .bin file..
now do this--
go to terminal and type
```
sudo ./filename.bin
```
replace filename with the name of your file..
hope it helps

---

### Post by tjwoosta on 2008-07-08
i think im going to install this game also


by the looks of it you just have to download the bianary from the link that says download

then follow the link that says install to install it


im going to go do it now so ill message back if i figure it out

---

### Post by jimi_hendrix on 2008-07-08
> **st33med said:**
> Packages in the repoes do not have caps...
Try:
```
sudo apt-get install planeshift
```

did that got this response

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package planeshift

```

---

### Post by jimi_hendrix on 2008-07-08
> **Car60n said:**
> by the looks of it you downloaded the .bin file..
now do this--
go to terminal and type
```
sudo ./filename.bin
```
replace filename with the name of your file..
hope it helps

got this response

```
sudo: ./planeshift.bin: command not found

```

---

### Post by jimi_hendrix on 2008-07-08
btw the install link on that page seems not to work...i get a page that doesnt stop loading

---

### Post by smo0th on 2008-07-08
there are packages/games not listed into the repos, you should try downloading your game from the official site and installing it using ./game.bin

---

### Post by tjwoosta on 2008-07-08
> btw the install link on that page seems not to work...i get a page that doesnt stop loading 

yea i just figured that out the hard way

but anyway the way to install a .bin never changes

change to the directory that you downloaded the file to
```
cd /wherever/the/file/is
```

then do 

```
sudo ./PlaneShift*
```

the reason it didnt work when you tried above is because you used all lowercase when the filename has caps in it

---

### Post by Car60n on 2008-07-08
here is how you do it from the start

1>go to this site--
[http://www.planeshift.it/download.html#linux](http://www.planeshift.it/download.html#linux)
find the linux binary 32-bit version and download from any of the mirrors..

2>note where the file is and then open the terminal and cd to where the file is saved..

3>after that type this--
```
sudo ./PlaneShift-v0.4.01-x86.bin
```

that should do it..

---

### Post by jimi_hendrix on 2008-07-08
ok now this is the real noob question

when i cd i type in

cd vincent/Desktop (where the file is)

its says "bash: cd: vincent/Desktop: No such file or directory"

what am i doing wrong

---

### Post by jerome1232 on 2008-07-08
needs to be one of the three
```
cd ~/Desktop
```
that changes to the /home/current-user/Desktop
```
cd /home/vincent/Desktop
```
changes to that pariticular users desktop
when you first open a terminal it's already in ~/ or the current users home, so you can just
```
cd Desktop
```

---

### Post by m_duck on 2008-07-08
> **jimi_hendrix said:**
> ok now this is the real noob question
when i cd i type in
cd vincent/Desktop (where the file is)
its says "bash: cd: vincent/Desktop: No such file or directory"
what am i doing wrong

Your user's folder is in /home/vincent so you will need to type
*cd /home/vincent/Desktop*
   or 
[I]cd ~/Desktop

[/I] [LEFT]*   ---*

[/LEFT]
 There is also a Ubuntu installation guide posted on a forum: [http://hydlaa.com/smf/index.php?topic=31776.0](http://hydlaa.com/smf/index.php?topic=31776.0)
 
Note that if you have already downloaded the .bin file, the wget command used in the tutorial will download it again. If you have already downloaded it, from the terminal type "*cd /folder/downloaded/to*" (without quotes) and follow the guide from the *chmod* line.
 
 Hope this helps!

---

### Post by Car60n on 2008-07-08
do this --
```
cd /home/vincent/Desktop
```

---

### Post by tjwoosta on 2008-07-08
ok i got planeshift installed over here

i will give you step by step instructions
when you download the file [B]do this before doing anything
[/B]
right click the file and choose properties

click the permissions tab

give yourself read/write access

also check the box that says "allow executing file as a program"

then back to the terminal
```
cd /wherever/the/file/is
``` (be careful of capitaizations and spelling and all should work)

then 

```
sudo ./Plane*
```

the installer will pop up  (read everything carefully)

save to /opt   (it should say /opt by default, mine did anyway)

it will ask what desktop you have (choose gnome if using Ubuntu, or kde if using kubuntu)

it will ask you "do you want to change permissions?" (or something) just choose **yes**

then it will ask the for you what user  (use this format **tj:users**)  (except substitute your name where it says tj)

then it will ask for a number for chmod   (just put 777)

it will also at some point ask if you want to make menu entries (choose yes)

then once instalation is done go to Applications-Games-PlaneShift Setup

after setup you can start playing the game   (applications-games-planeshift)

EDIT: if you can get connected to the server (i just tried connecting but every time it says server fragnetics failed)

---

### Post by jimi_hendrix on 2008-07-09
> **tjwoosta said:**
> ok i got planeshift installed over here

i will give you step by step instructions
when you download the file [B]do this before doing anything
[/B]
right click the file and choose properties

click the permissions tab

give yourself read/write access

also check the box that says "allow executing file as a program"

then back to the terminal
```
cd /wherever/the/file/is
``` (be careful of capitaizations and spelling and all should work)

then 

```
sudo ./Plane*
```

the installer will pop up  (read everything carefully)

save to /opt   (it should say /opt by default, mine did anyway)

it will ask what desktop you have (choose gnome if using Ubuntu, or kde if using kubuntu)

it will ask you "do you want to change permissions?" (or something) just choose **yes**

then it will ask the for you what user  (use this format **tj:users**)  (except substitute your name where it says tj)

then it will ask for a number for chmod   (just put 777)

it will also at some point ask if you want to make menu entries (choose yes)

then once instalation is done go to Applications-Games-PlaneShift Setup

after setup you can start playing the game   (applications-games-planeshift)

EDIT: if you can get connected to the server (i just tried connecting but every time it says server fragnetics failed)

when i typed in ```
vincent@vincent-laptop:~/Desktop$ sudo ./Plane*

```

```
Expected option but got "./PlaneShift-v0.4.01-x64(3).bin". Options start with a leading "--" prefix
Use --help to get a list of valid options
```

---

### Post by sharks on 2008-07-09
i think the * button indicates the version numbr. can u post the full name of the folder?

---

### Post by jimi_hendrix on 2008-07-09
PlaneShift-v0.4.01-x64(2).bin

---

### Post by sharks on 2008-07-09
then type sudo ./PlaneShift-v0.4.01-x64(2).bin in terminal

---

### Post by jimi_hendrix on 2008-07-09
ok...last thing...hopefully then ill go click on the shiney little thankyou buttons on u guys

it asks if i want a system wide install...what is that

---

### Post by sharks on 2008-07-09
dont know about it. may be this can help u:

[http://hydlaa.com/smf/index.php?topic=31776.0](http://hydlaa.com/smf/index.php?topic=31776.0)

---

### Post by jimi_hendrix on 2008-07-09
ok i need 1 last thing...how do i become root?

---

### Post by sharks on 2008-07-09
to become root :sudo the-command-u-want-to-type

sudo means SuperUserDo

---

### Post by jimi_hendrix on 2008-07-09
well i got the program installed but its "locked" and i need to be root to access/change its properties...how would i do that

---

### Post by sharks on 2008-07-09
go to system--administration---users and groups and select root and click properties and change root password by selecting set password by hand.

Then log out and log in using:
the root username and password.

---

### Post by jimi_hendrix on 2008-07-09
i log in with the root username and password and it says system administrator not allowed to be accesed from this screen...

this is driving me nuts

---

### Post by sharks on 2008-07-09
check this (not for root)

[http://www.planeshift.it/guide/en/index.html](http://www.planeshift.it/guide/en/index.html)

---

### Post by tjwoosta on 2008-07-09
YES!!

YOU DO WANT A SYSTEM WIDE INSTALL!!!


(i thought i mentioned that, sorry)

---

