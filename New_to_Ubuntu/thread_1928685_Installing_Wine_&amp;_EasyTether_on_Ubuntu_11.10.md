---
title: "Installing Wine &amp; EasyTether on Ubuntu 11.10"
date: 2012-02-20
forum: New to Ubuntu
---

### Post by alpacawon on 2012-02-20
Hey ya'll.

So I'm new to Ubuntu and trying to get my internet set up. I've decided to try EasyTether but I can't seem to figure out how to make it work. I downloaded the .deb file and got it extracted, but when it comes to "Open Terminal on your Linux computer, type easytether connect, press Enter" I'm lost. All I get is

```
 easytether: command not found 
```

Then I had the bright idea that maybe PdaNet might work through Wine, but I can't figure out how to get Wine working. I downloaded/extracted wine1.3_1.3.28-Oubuntu1_i386.deb and I can see the stupid program sitting on the desktop but the Terminal can't find it.

Help.ubuntu.com says I should do "winecfg" first and that's met with

```
The program 'winecfg' can be found in the following packages:
* wine1.2
* wine1.3
Try: sudo apt-get install <selected package>
```

And then when I do that, I get

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package wine1.3
E: Couldn't find any package by regex 'wine1.3'
```

I found on another forum someone recommended "sudo add-apt-repository ppa:ubuntu-wine/ppa; sudo apt-get update; sudo apt-get install wine1.3" but that seems to want an internet connection -- which I don't have at the moment. Any ideas?

Thanks in advance.

---

### Post by Cheesemill on 2012-02-20
> **alpacawon said:**
> I downloaded the .deb file and got it extracted

You have extracted the .deb file instead of installing it. Try doing:
```
sudo dpkg -i packagename.deb
```

The easytether command should then work in the terminal.

---

### Post by alpacawon on 2012-02-20
"sudo dpkg -i easytether_0.7.2-1_i386.deb" gives me

```
dpkg: error processing easytether_0.7.2-1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 easytether_0.7.2-1_i386.deb
```

And the same goes for Wine. Are they in the wrong place?

---

### Post by Cheesemill on 2012-02-20
Where did you download them to?

To make life easier you can type:
```
dpkg -i 
```
and then drag and drop the file onto the terminal, this will make sure you have the correct path.

---

### Post by alpacawon on 2012-02-20
I downloaded the .debs to the desktop so I wouldn't lose them. That's a neat trick, dragging and dropping, but now I get a new error

```
dpkg: error: requested operation requires superuser privilege
```

---

### Post by Cheesemill on 2012-02-20
> **alpacawon said:**
> I downloaded the .debs to the desktop so I wouldn't lose them. That's a neat trick, dragging and dropping, but now I get a new error

```
dpkg: error: requested operation requires superuser privilege
```

Sorry, it should be:
```
sudo dpkg -i
```

---

### Post by alpacawon on 2012-02-20
Yay thank you soooo much! I can get online now at least, but still having trouble with Wine.

```
rosemary@alpaca1:~$ sudo dpkg -i '/home/rosemary/Desktop/wine1.3_1.3.28-0ubuntu1_i386.deb' 
[sudo] password for rosemary: 
(Reading database ... 167062 files and directories currently installed.)
Preparing to replace wine1.3 1.3.28-0ubuntu1 (using .../wine1.3_1.3.28-0ubuntu1_i386.deb) ...
Unpacking replacement wine1.3 ...
dpkg: dependency problems prevent configuration of wine1.3:
 wine1.3 depends on libgettextpo0; however:
  Package libgettextpo0 is not installed.
 wine1.3 depends on libmpg123-0 (>= 1.6.2); however:
  Package libmpg123-0 is not installed.
dpkg: error processing wine1.3 (--install):
 dependency problems - leaving unconfigured
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for hicolor-icon-theme ...
Processing triggers for man-db ...
Errors were encountered while processing:
 wine1.3
rosemary@alpaca1:~$ 
```

---

### Post by Cheesemill on 2012-02-20
Now that you are online you can just do:
```
sudo add-apt-repository ppa:ubuntu-wine/ppa; sudo apt-get update; sudo apt-get install wine1.3
```
as you mentioned in your original post.

---

### Post by alpacawon on 2012-02-20
Okay, I must be doing something wrong... "sudo add-apt-repository ppa:ubuntu-wine/ppa" yields no results, it just times out after a few minutes. It updates successfully, but then the last command says I'm missing stuff.

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 wine1.3 : Depends: libgettextpo0
           Depends: libmpg123-0 (>= 1.6.2) but it is not going to be installed
           Recommends: gnome-exe-thumbnailer but it is not going to be installed or
                       kdebase-runtime but it is not going to be installed
           Recommends: ttf-droid but it is not going to be installed
           Recommends: ttf-mscorefonts-installer but it is not going to be installed
           Recommends: ttf-umefont
           Recommends: winbind but it is not going to be installed
           Recommends: wine1.3-gecko (>= 1.3) but it is not going to be installed
           Recommends: winetricks but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

Would you recommend I hunt down the recommendations and try to install those, or just try to install without packages? Thanks again.

---

### Post by Cheesemill on 2012-02-20
You're getting these errors because you tried to install software while offline. Simply doing what it recommends should fix any problems:
```
sudo apt-get f install
```

---

### Post by alpacawon on 2012-02-26
Thanks a million, I did eventually get this figured out and both programs are working great!

^^

---

