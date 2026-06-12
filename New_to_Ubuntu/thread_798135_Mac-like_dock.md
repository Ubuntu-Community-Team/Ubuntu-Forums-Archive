---
title: "Mac-like dock"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by pikabuntu on 2008-05-17
I am having trouble trying to figure out how to get a Mac-like dock on ubuntu...

---

### Post by Vicfred on 2008-05-17
try kiba dock

---

### Post by barbedsaber on 2008-05-17
the easiest way would probably be to open a terminal, and type

```
sudo apt-get install awn-manager
```

there are a lot of other docks, but that is in the repos and easy to install.

---

### Post by Victormd on 2008-05-17
Try this [HOWTO]("http://ubuntuforums.org/showthread.php?t=762363")

---

### Post by pikabuntu on 2008-05-17
ok, so what do i do now that ive typed that in the terminal?
when i click on applications>accessories>avant window navigator, it does nothing...

---

### Post by barbedsaber on 2008-05-17
> **pikabuntu said:**
> ok, so what do i do now that ive typed that in the terminal?
when i click on applications>accessories>avant window navigator, it does nothing...

as far as I know (and I could be wrong) it is there, but you have no launchers, so you can't see it. have somthing open when you click on it in the applications menu. then you should be able to see it, and have a place to drag and drop launchers from the applicaions menu to.

for example, if you want a little calculator icon that will launch your calculator, you open application, acceroris, and drag calculator to your dock.

---

### Post by pikabuntu on 2008-05-17
where exactly would i drag it to?

---

### Post by barbedsaber on 2008-05-17
> **pikabuntu said:**
> where exactly would i drag it to?

so, you see nothing new at the bottom of your screen?

make sure you have no maximized windows that might block it from view.

---

### Post by pikabuntu on 2008-05-17
> **barbedsaber said:**
> so, you see nothing new at the bottom of your screen?

make sure you have no maximized windows that might block it from view.

yeah, there's nothing new there...
i just noticed that there is a little flicker in the upper left hand corner when i try to start it... if that helps any

---

### Post by Inxsible on 2008-05-17
KoolDock is another option which is most similar to the Mac OS like dock. It also gives you the fish eye effect like OS X

---

### Post by pikabuntu on 2008-05-17
how would i get it?

---

### Post by cardinals_fan on 2008-05-17
Try these tips: [http://www.linux.com/feature/128982](http://www.linux.com/feature/128982)

---

### Post by pikabuntu on 2008-05-17
ok ill check that out then

---

### Post by pikabuntu on 2008-05-17
i get this from the wbar

tar: wbar-1.3.3.tbz2.tar.bz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
zach@Ubuntu:~$

---

### Post by Inxsible on 2008-05-17
> **pikabuntu said:**
> i get this from the wbar

tar: wbar-1.3.3.tbz2.tar.bz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
zach@Ubuntu:~$Where did you download the file? Did you cd to that folder before trying out those commands?

---

### Post by pikabuntu on 2008-05-17
> **Inxsible said:**
> Where did you download the file? Did you cd to that folder before trying out those commands?

how do i do that?

---

### Post by Inxsible on 2008-05-17
> **pikabuntu said:**
> how do i do that?On the link that cardinals_fan gave you, just before the commands, you have a Get the latest version here link. You have to first download the tar file and put it on your machine -- on your desktop for example. Then in a terminal, you have to ```
cd ~/Desktop
``` After that in the same terminal, perform the commands that the link shows you.

---

### Post by Inxsible on 2008-05-17
If you want to install KoolDock, you can install it by ```
sudo aptitude install kooldock
``` You have to have the universe and multiverse repos enabled.

---

### Post by Victormd on 2008-05-17
> **pikabuntu said:**
> i get this from the wbar

tar: wbar-1.3.3.tbz2.tar.bz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
zach@Ubuntu:~$

You should try the HOW To link I posted earlier... it's very complete for AWN...

---

### Post by cardinals_fan on 2008-05-17
Here's a better idea:

Type the following command in a terminal: ```
sudo apt-get install wbar
```

Then follow the instructions on that link (after the yellow code box).

---

### Post by pikabuntu on 2008-05-17
ummm... that how to is kind of confusing to me

---

### Post by pikabuntu on 2008-05-17
> **Inxsible said:**
> On the link that cardinals_fan gave you, just before the commands, you have a Get the latest version here link. You have to first download the tar file and put it on your machine -- on your desktop for example. Then in a terminal, you have to ```
cd ~/Desktop
``` After that in the same terminal, perform the commands that the link shows you.

that is what i got:

zach@Ubuntu:~$ cd ~/Desktop
zach@Ubuntu:~/Desktop$ tar xjf wbar-1.3.3.tbz2.tar.bz
tar: wbar-1.3.3.tbz2.tar.bz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
zach@Ubuntu:~/Desktop$

---

### Post by pikabuntu on 2008-05-17
im going to get off for the night... thnx for all of the help so far

---

### Post by Victormd on 2008-05-18
> **pikabuntu said:**
> ummm... that how to is kind of confusing to me

Open a terminal window then copy and paste the following commands (one at a time - I'm assuming you're using Hardy):
```
echo 'deb http://ppa.launchpad.net/reacocard-awn/ubuntu hardy main'  |  sudo tee -a /etc/apt/sources.list

```
```
echo 'deb-src http://ppa.launchpad.net/reacocard-awn/ubuntu hardy main'  |  sudo tee -a /etc/apt/sources.list
```
```
sudo apt-get update
```
```
sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr awn-manager-bzr
```
[Source]("http://ubuntuforums.org/showthread.php?t=762363")

---

### Post by pikabuntu on 2008-05-18
I did that, but it still does the same thing
a friend told me he thinks my graphics card is not supported

---

### Post by moonbeam on 2008-05-18
> **pikabuntu said:**
> I did that, but it still does the same thing
a friend told me he thinks my graphics card is not supported

You need to have a compositor active.

If desktop-effects 

[http://www.neohide.com/ubuntu-desktop-effects-for-hardy-heron](http://www.neohide.com/ubuntu-desktop-effects-for-hardy-heron)

won't activate 

then the metacity composite support will probably work for you (assuming Hardy)

[http://tombuntu.com/index.php/2008/03/31/enable-metacity-compositing-in-gnome-222/](http://tombuntu.com/index.php/2008/03/31/enable-metacity-compositing-in-gnome-222/)

---

### Post by cardinals_fan on 2008-05-18
Type this in a terminal:
```
sudo apt-get install wbar
```
The click this link: [http://koti.kapsi.fi/~ighea/wbarconf/wbarconf-0.7.1.tar.gz](http://koti.kapsi.fi/~ighea/wbarconf/wbarconf-0.7.1.tar.gz)

Once that has finished downloading, open a terminal.  Type the following commands: 
```
cd Desktop/
tar zxf wbarconf-0.7.1.tar.gz
cd wbarconf/
python wbarconf.py
```

Set the shortcuts how you like them, then hit save.  Hit Alt-F2 and type:```
wbar &
```

---

### Post by pikabuntu on 2008-05-18
thanx oodles, moonbeam!!! awn is now working correctly!

---

