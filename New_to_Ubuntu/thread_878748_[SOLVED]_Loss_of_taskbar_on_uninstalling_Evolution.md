---
title: "[SOLVED] Loss of taskbar on uninstalling Evolution"
date: 2008-08-03
forum: New to Ubuntu
---

### Post by Threlkeld on 2008-08-03
Ubuntu 8.04 on Dell Inspiron 6400. I was tidying-up and decided to uninstall Evolution using Synaptic, since I use Thunderbird for mail and have never touched Evolution. Alas, the next time I rebooted there was no taskbar of any sort, just a bare desktop, so I could not launch any applications graphically. 
I used another PC to search the forums and using what I found there was able to restore most of the important graphical functionality via Terminal. The reported problem I saw there was also caused by uninstalling Evolution.
My questions are these:
1. From terminal error messages and the fact that I now can't install new taskbar applets, I conclude that my Gnome (or something) is still a bit broken. How can I mend it fully?
2. Why does uninstalling Evolution trash Gnome? Does this need a bug report?

---

### Post by chuckyp on 2008-08-03
Try right clicking on the desktop and selecting add panel.  That will give you a bar you can begin rebuilding.  If you want to start over you can delete the .gconf folder in your home directory. This will remove all you settings in gnome. 

Also if what you are saying is true that the removal of evolution removes the gnome-panels that is definately a bug that needs to be looked at.

---

### Post by gerben1 on 2008-08-03
I have had this problem too. Apparently you have to uninstall evolution via apt-get if you want to, personally I would just leave it. It's not worth the potential trouble.

see this thread:
[http://ubuntuforums.org/showthread.php?t=784388](http://ubuntuforums.org/showthread.php?t=784388)

---

### Post by james_vanb on 2008-08-03
I've had similar experience.  Panels can be reinstalled with:

```
sudo apt-get install gnome-panel
```

For whatever reason, panels must be a dependency of some sort.  You might have gotten a pop up when you uninstalled Evolution saying the following applications will also be removed (Including panels).

---

### Post by Threlkeld on 2008-08-03
> **chuckyp said:**
> Try right clicking on the desktop and selecting add panel.  That will give you a bar you can begin rebuilding.  If you want to start over you can delete the .gconf folder in your home directory. This will remove all you settings in gnome. 

Also if what you are saying is true that the removal of evolution removes the gnome-panels that is definately a bug that needs to be looked at.

Alas, I don't see 'Add Panel' when I right-click on the desktop. There is 'Create Launcher' and 'Create Document', but no 'Add Panel'. Is this a further symptom of the damage I have inflicted by uninstalling Evolution?
I'm a bit reluctant to delete .gconf in case the bars disappear again, though I suppose I could just change the name.

---

### Post by Threlkeld on 2008-08-03
> **james_vanb said:**
> I've had similar experience.  Panels can be reinstalled with:

```
sudo apt-get install gnome-panel
```

For whatever reason, panels must be a dependency of some sort.  You might have gotten a pop up when you uninstalled Evolution saying the following applications will also be removed (Including panels).

I get:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gnome-panel is already the newest version.
The following packages were automatically installed and are no longer required:
  libggzmod4 libggz2 libgdata1.2-1 libgdata-google1.2-1
  linux-headers-2.6.24-18-generic libggzcore9 linux-headers-2.6.24-18
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

So, no change there. If I try to install an applet to the bar I get an error message saying "The Panel encountered a problem while installing [applet name] Do you want to delete the applet from your configuration  [Don't delete] [Delete]" It doesn't matter which you choose, it doesn't install.

---

### Post by james_vanb on 2008-08-03
Youcan try removing and reinstalling:

```
sudo apt-get remove gnome-panel
sudo apt-get install gnome-panel
```

---

### Post by gerben1 on 2008-08-03
To get things working again, I think you'd best try to get back to the situation where you were when you tried uninstalling evolution.

Run:
```

sudo apt-get install ubuntu-desktop

```
ubuntu-desktop is a so-called meta-package that depends on everything the gnome desktop needs, so if you install this all necessary packages will be installed (also evolution, for some strange reason...)

---

### Post by Threlkeld on 2008-08-03
OK, tried both of those. Thanks James_VanB and Gerben1. I eventually did the total desktop reinstall because just doing the bar didn't seem to work. (Though perhaps I should have tried a reboot, I now realise) I now have what looks like a fully-functioning desktop.
Except:
Just after I log-on at bootup, I get a window that says something like:
"Users HOME/.dmrc file is being ignored...  ... File should be owned by user and have 644 permissions..."
(There are no other users on this machine)
I click OK and the boot process seems to run normally. I have Evolution and all the unwanted games back. How odd to think that removing those could do so much damage. How I wish I hadn't touched them!
Do I delete the .dmrc file and hope that it will make a new one, or what? I'd rather not have to re-customise all my desktop settings as I've done quite a lot.
Thanks again for all this help. It's marvelous to be able to ask for and receive such support.

---

### Post by gerben1 on 2008-08-03
I would just try to change the permissions to 644, like this:
```
chmod 644 ~/.dmrc
```

and change onwer to yourself like this:
```
chown gerben:gerben ~/.dmrc 
```
obviously change "gerben" with your inlog name

---

### Post by CatKiller on 2008-08-03
> **Threlkeld said:**
> Just after I log-on at bootup, I get a window that says something like:
"Users HOME/.dmrc file is being ignored...  ... File should be owned by user and have 644 permissions..."

I think it's (probably) unrelated to your previous problem, but you could just change the permissions of the .dmrc file to match what it wants to make the message go away.

---

### Post by Threlkeld on 2008-08-03
> **gerben1 said:**
> I would just try to change the permissions to 644, like this:
```
chmod 644 ~/.dmrc
```

and change onwer to yourself like this:
```
chown gerben:gerben ~/.dmrc 
```
obviously change "gerben" with your inlog name

Hm, I'm having a problem here. It says it can't find the file to perform the chmod action. I see that I bungled the error message transcription. It reads in full:
"User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users"
$HOME means nothing to me, as I don't see a directory of that name. What does the dollar sign signify? Sorry to be so stupid.

---

### Post by CatKiller on 2008-08-03
$HOME is a variable that means your Home folder, /home/<*username*>, ~. You might need to change the permissions on that too, to make it so that other (imaginary, in your case :)) users don't have write access. And if the file does not exist, you can create it with ```
touch ~/.dmrc
``` Don't forget to give it the right permissions.

---

### Post by gerben1 on 2008-08-03
> **Threlkeld said:**
> Hm, I'm having a problem here. It says it can't find the file to perform the chmod action.


Okay so the file does not exist, you can just make one, as catKiller explained with:
```
touch ~/.dmrc
```


> **Threlkeld said:**
> I see that I bungled the error message transcription. It reads in full:
"User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users"
$HOME means nothing to me, as I don't see a directory of that name. What does the dollar sign signify? Sorry to be so stupid.

if you want to see which value $HOME has, just type this in the Terminal
```
cat $HOME
```
for example in my case:
```

gerben@gerben-laptop:~$ cat $HOME
cat: /home/gerben: Is a directory

```

there are more variables that have all kinds of handy uses, if you ever need to use one just "cat" it first so you can understand what it refers to.

-------------------
Anyways, running these commands will probably solve your problem:
```

touch ~/.dmrc
chmod 644 ~/.dmrc
chown gerben:gerben ~/.dmrc

```
in last command replace gerben with your username

---

### Post by Threlkeld on 2008-08-03
You guys are really being incredibly patient with me and my problem. 
I really do appreciate it.
Alas, I'm still getting the same error message on boot-up, and I may have to live with it. 
The .dmrc file does not show up in home/rw whatever I do. I've tried typing the directory as an explicit string, and I've tried using the $HOME variable, but whatever I do it stubbornly refuses to appear (yes, I have remembered to enable hidden files in View).
But if I try to save a dummy file in home/rw as .dmrc, sure enough it says it already exists and asks if I want to overwrite it. Yet it doesn't show in the file list in the 'save' dialog box, or anywhere else as far as I can see.
I have the feeling that I'm being really stupid about something. Boy, I hate that feeling!

SORRY! it does exist. I'd been looking at folders, not files. I'm an Idiot!
It contains

[Desktop]
Session=gnome

And I have full permissions

---

### Post by gerben1 on 2008-08-03
> **Threlkeld said:**
> You guys are really being incredibly patient with me and my problem. 
I really do appreciate it.
Alas, I'm still getting the same error message on boot-up, and I may have to live with it. 
The .dmrc file does not show up in home/rw whatever I do. I've tried typing the directory as an explicit string, and I've tried using the $HOME variable, but whatever I do it stubbornly refuses to appear (yes, I have remembered to enable hidden files in View).


this character: ~
called the tilde, means "the home directory of the user"

in my case:
```

gerben@gerben-laptop:~$ cat ~
cat: /home/gerben: Is a directory

```

To see whether you have a file called .dmrc in your home directory you can try to list the file and its details with the command: ls -l
So, go to a terminal and type:
```

ls -l ~/.dmrc

```

If it lists the file and its details, it is there and you can change its owner and its permissions.

This is what happens on my laptop:
```

gerben@gerben-laptop:/$ ls -l ~/.dmrc
-rw------- 1 gerben gerben 28 2008-08-03 13:48 /home/gerben/.dmrc

```



> **Threlkeld said:**
> 
But if I try to save a dummy file in home/rw as .dmrc, sure enough it says it already exists and asks if I want to overwrite it. Yet it doesn't show in the file list in the 'save' dialog box, or anywhere else as far as I can see.
I have the feeling that I'm being really stupid about something. Boy, I hate that feeling!

Okay, so the file does exist then.
If you are in a "save as" dialog, you usually do not see the hidden files, but if you hit Ctrl-h you will see them.

You probably type the command or directory wrong on earlier tries, just be care full with directories, I see you  using  "home/rw" above and this is NOT the same as "/home/rw".

The first (home/rw) is a relative path and the second (/home/rw) an absolute path. The relative path gives the path relative to the current directory, whereas the absolute path just gives the whole path.

Example:
say you are in directory: /data
if you then refer to home/rw, you refer to /data/home/rw
if you had referred to /home/rw, then that would be just that /home/rw

---

### Post by gerben1 on 2008-08-03
> **Threlkeld said:**
> 
SORRY! it does exist. I'd been looking at folders, not files. I'm an Idiot!
It contains

[Desktop]
Session=gnome

And I have full permissions

Okay well than just change it's permissions and the owner, to what the error message said it should be:

```

chmod 644 ~/.dmrc
chown rw:rw ~/.dmrc

```

---

### Post by Threlkeld on 2008-08-03
And SUCCESS !!

(I also looked at the /home/rw permissions and they were set read/write for all. Wonder how that happened? I reset them to 'no access' for anyone outside the rw group).

Thank you very much. And catkiller too.
From Liverpool, my gratitude for your patience.
I'm a little better educated, and very impressed with the Ubuntu community.

(I wonder if I should post a bug about Synaptic trashing Gnome if it is used to uninstall Evolution. Other folk are likely to try that in the future.)

---

### Post by BGFG on 2008-08-03
And don't totally uninstall evolution again. You can strip it down but, most of the gnome desktop is tied to evolution-dataserver-common for a reason known only by the gnome engineers. 
If it's a funding thing then i cannot be mad at them. GNOME rocks and they gave us it for free.

To see what i mean, open synaptic search for evolution and attempt to remove one of it's packages. pay close attention to the subsequent message. Some can be removed but some of the libraries are depended on by many other gnome packages and should be left alone.

It's not a bug :) it a design thing.

---

### Post by Threlkeld on 2008-08-03
Understood, and of course I agree. But I've been using Ubuntu for some months without hearing of this special status for Evolution, and is a bit of a trap for the unwary. 
I'd noticed that in moving from Feisty through Gutsy to Hardy the boot-up time was getting almost as long as that of another operating system associated with Redmond. Too long, in fact. So I thought I'd de-clutter my system by removing applications I never use. Doubt if I'll be the last...     :-)

---

### Post by BGFG on 2008-08-03
> **Threlkeld said:**
> Understood, and of course I agree. But I've been using Ubuntu for some months without hearing of this special status for Evolution, and is a bit of a trap for the unwary. 
I'd noticed that in moving from Feisty through Gutsy to Hardy the boot-up time was getting almost as long as that of another operating system associated with Redmond. Too long, in fact. So I thought I'd de-clutter my system by removing applications I never use. Doubt if I'll be the last...     :-)

I agree, I had a thread parallel to yours today about removing evolution too. even made the same 'redmond' comment. But such a comparison is really harsh on our guys if only because we didn't we didn't pay through the nose for something that works so great.. :)

and that is certainly not the only reason.
Good luck. If i ever figure it out i'll let the forums know.

---

