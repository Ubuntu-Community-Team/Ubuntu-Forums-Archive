---
title: "sudo alsaconfig"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by dooftard on 2008-05-15
:lolflag:

Alright, obviously I'm brand new to ubuntu.  I'll skip most of the sap and get to the core problem.
I love ubuntu so far, but since I'm on a laptop a lot of things are....not working.


1)  I cannot disable my touchpad and use only my mouse(its sensative and I use the laptop keyboard
2)  the volume wheel doesn't work
3)  I don't even have any volume at all unless I use headphones
4)  I don't have volume in firefox even whilst using headphones


So I've recently just been told to go get the alsaconfiguration tool.
Ubuntu didn't come with it(alsamixer apparently isn't it...)

so I've gone to this website:  [link]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

and I got to this part:
```
sudo cp ~/downloads/alsa* .
```
but the outcome is this:
```
/usr/src/alsa$ sudo cp ~/Desktop/alsa*
cp: missing destination file operand after `/home/dooftard/Desktop/alsa'
Try `cp --help' for more information.
```

Since I placed a folder on my Desktop named alsa I don't quite see whats wrong with this...
It tells me to download it to /downloads and I tried to even go that route, but I'm unable to even make a directory in that folder.

I'm stumped so any help would be appreciated at this point in time.

---

### Post by ruzkie on 2008-05-15
Alsaconf i presume you are talking about, it was removed in 7.10 and is the only way i've could change my soundcards with so far. It works and nothing else have worked since 7.10... ARgh.

---

### Post by kpkeerthi on 2008-05-15
You missed the . (dot) at the end of that command.

---

### Post by dooftard on 2008-05-15
> **kpkeerthi said:**
> You missed the . (dot) at the end of that command.

I really ....really hope your joking......LOL

::edit::
wow...yeah that worked.

anyway
here is the outcome:
```
cp: omitting directory `/home/dooftard/Desktop/alsa'
```

hopefully that was what was supposed to happen -shrug-

::edit::
alright so now the second part....I know whats going on, but I'm not quite sure how to fix it.  

```
/usr/src/alsa$ sudo tar xjf alsa-driver*.bz2
tar: alsa-driver*.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

```

it doesn't know where its at...I guess im going to tinker around with it(looking for an easy way out on here!)

---

### Post by kpkeerthi on 2008-05-15
LOL!
. (dot) refers to current directory ( the directory from where you ran that 
command )

---

### Post by dooftard on 2008-05-15
> **kpkeerthi said:**
> LOL!
. (dot) refers to current directory ( the directory from where you ran that 
command )

really wouldn't have known that up until now.

whats your cure for my second problem( I can see it now; I'm probably going to have a problem per line/command.....)

---

### Post by spiderbatdad on 2008-05-15
> **dooftard said:**
> I really ....really hope your joking......LOL

::edit::
wow...yeah that worked.

anyway
here is the outcome:
```
cp: omitting directory `/home/dooftard/Desktop/alsa'
```

hopefully that was what was supposed to happen -shrug-

::edit::
alright so now the second part....I know whats going on, but I'm not quite sure how to fix it.  

```
/usr/src/alsa$ sudo tar xjf alsa-driver*.bz2
tar: alsa-driver*.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

```

it doesn't know where its at...I guess im going to tinker around with it(looking for an easy way out on here!)

tar package needs to be in the directory you are working from, ie. /usr/src/alsa in the example above.

---

### Post by kerry_s on 2008-05-15
before you go through building it try this->
[B]sudo apt-get install alsa-base alsa-oss alsa-utils
sudo alsaconfig
reboot
in terminal> alsamixer[/B]

---

### Post by dooftard on 2008-05-15
> **spiderbatdad said:**
> tar package needs to be in the directory you are working from, ie. /usr/src/alsa in the example above.

I'm unable to move the said file to where it needs to go..
not enough privlages and what not.(drag and drop technique)

I'm thinking this would be a lot easier to just go out and get 7.10.

Right now I'm on 8.04

---

### Post by linuxonbute on 2008-05-15
> **dooftard said:**
> :lolflag:

Alright, obviously I'm brand new to ubuntu.  I'll skip most of the sap and get to the core problem.
I love ubuntu so far, but since I'm on a laptop a lot of things are....not working.


1)  I cannot disable my touchpad and use only my mouse(its sensative and I use the laptop keyboard


To disable the touchpad do the following

from a terminal window edit the file /etc/rc.local

sudo gedit /etc/rc.local

put the following as the last line of the file:

rmmod psmouse

save and exit

then reboot.

When you want to use the touchpad on a temporary basis

do from a terminal window:

sudo modprobe psmouse

If you want to use it permanently remove the line you added to /etc/rc.local

best wishes

---

### Post by dooftard on 2008-05-15
> **kerry_s said:**
> before you go through building it try this->
[B]sudo apt-get install alsa-base alsa-oss alsa-utils
sudo alsaconfig
reboot
in terminal> alsamixer[/B]

alsamixer isn't it; that just gives me a bunch of volume bars to adjust.  The guy that explained it to me over irc(another community) he said its to change my soundcard as its not even "found" with the plug and play.  I have to point to it with a configurator.

I already ran 4hrs on google trying to find a solution for it and this is what it came to.

whereis alsaconf
sudo alsamixer(not the one)
sudo alsaconf(not even found)
sudo alsaconfig('')

even tried to do the easy route of  add/remove  but I guess its not even up on there.


I know I'm quite stupid, but this is just taking the cake right here...lol.

sucks to be raised on windows all your life...well..amiga then to windows 95.

---

### Post by spiderbatdad on 2008-05-15
To have graphical administrative privileges with root directories/folders/files run:```
gksu nautilus
```but be careful...you will be able to write changes to the root filesystem. It is just as easy to copy the folder from its current location to the destination directory with sudo cp, for example```
sudo cp -r home/user_name/Desktop/some_folder /usr/src/alsa
```Just an example you need to use correct file names and directories. ```
man cp
```can tell you more.

---

### Post by meltindar on 2008-05-15
> **dooftard said:**
> I really ....really hope your joking......LOL

::edit::
wow...yeah that worked.

anyway
here is the outcome:
```
cp: omitting directory `/home/dooftard/Desktop/alsa'
```

hopefully that was what was supposed to happen -shrug-

::edit::
alright so now the second part....I know whats going on, but I'm not quite sure how to fix it.  

```
/usr/src/alsa$ sudo tar xjf alsa-driver*.bz2
tar: alsa-driver*.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

```

it doesn't know where its at...I guess im going to tinker around with it(looking for an easy way out on here!)

You missed the -r option for cp command. You have to provide it in order to copy directories (which cp doesn't do by default). That's why your .bz2 file could not be found.
HTH

---

### Post by kerry_s on 2008-05-15
> **dooftard said:**
> alsamixer isn't it; that just gives me a bunch of volume bars to adjust.  The guy that explained it to me over irc(another community) he said its to change my soundcard as its not even "found" with the plug and play.  I have to point to it with a configurator.

I already ran 4hrs on google trying to find a solution for it and this is what it came to.

whereis alsaconf
sudo alsamixer(not the one)
sudo alsaconf(not even found)
sudo alsaconfig('')

even tried to do the easy route of  add/remove  but I guess its not even up on there.


I know I'm quite stupid, but this is just taking the cake right here...lol.

sucks to be raised on windows all your life...well..amiga then to windows 95.

alsaconfig is in "alsa-base" that's why the apt-get line to make sure you have everything. if your not even going to try, i'm not going to bother, go ahead and follow those other instructions and build it.

alsaconf looks like this->

---

### Post by dooftard on 2008-05-15
> **kerry_s said:**
> alsaconfig is in "alsa-base" that's why the apt-get line to make sure you have everything. if your not even going to try, i'm not going to bother, go ahead and follow those other instructions and build it.

alsaconf looks like this->


I hate to get shitty with you, but like I said....I went at it yesterday for 4hrs trying to figure it out on google.
those commands I posted above didn't just POPUP out of nowhere in my empty little noggin.
I'm trying, but being completely lost and not knowing the commands/what they do really isn't helping me out.

---

### Post by kerry_s on 2008-05-15
> **dooftard said:**
> I hate to get shitty with you, but like I said....I went at it yesterday for 4hrs trying to figure it out on google.
those commands I posted above didn't just POPUP out of nowhere in my empty little noggin.
I'm trying, but being completely lost and not knowing the commands/what they do really isn't helping me out.

this is the main command, if you don't have the stuff of course it's going to say "not found".

```
**sudo apt-get install alsa-base alsa-oss alsa-utils**
```

are you saying you did that already and it's still not found? :confused:

---

### Post by Bob535 on 2008-05-18
As another poster pointed out earlier, alsaconfig was removed from ubuntu. Even with the utils, base and oss you are unable to call the command in 8.04

---

### Post by kerry_s on 2008-05-18
> **Bob535 said:**
> As another poster pointed out earlier, alsaconfig was removed from ubuntu. Even with the utils, base and oss you are unable to call the command in 8.04

ohh, they butchered it. that's just wrong. file a bug.

---

### Post by markbuntu on 2008-05-18
Have you tried fooling around with the System/Preferences/Sound whatchamacallit?
That usually works for me eventually.

---

