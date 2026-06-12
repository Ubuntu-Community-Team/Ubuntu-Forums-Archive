---
title: "Removal of KDE (Kubuntu?) not working."
date: 2012-06-13
forum: New to Ubuntu
---

### Post by Skerps on 2012-06-13
Yesterday I tried to install KDE using [this]("http://www.psychocats.net/ubuntu/kde") tutorial.

My linux version was (is?) Ubuntu 12.04.

I wanted to use Gnome 3 instead of Unity but thought KDE might be good to.
 
Every thing went smooth but it looked quite different, the login screen is now different the startup splash screen show some kind of gray gear instead of the normal ubuntu logo and even GRUB is gray (was purple before).

I tried to remove KDE with all its apps using [this]("http://www.psychocats.net/ubuntu/pureubuntu") tutorial but got this message (and nothing is changed):

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package kubuntu-desktop is not installed, so not removed
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 default-jre : Depends: openjdk-6-jre (>= 6b23~pre11-1ubuntu1~) but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
```I would be glad if you guys could help me removing KDE and installing Gnome (I did read that you cant install both?)

ps: I'm rather new to Linux/Ubuntu

---

### Post by cortman on 2012-06-13
First run

```
sudo apt-get install -f
```

and then try removing KDE.

---

### Post by Skerps on 2012-06-13
> **cortman said:**
> First run

```
sudo apt-get install -f
```and then try removing KDE.

It sadly didn't change anything :(

---

### Post by cmcanulty on 2012-06-13
try this
[http://www.psychocats.net/ubuntu/pureubuntu]("http://www.psychocats.net/ubuntu/pureubuntu")

---

### Post by Skerps on 2012-06-13
> **cmcanulty said:**
> try this
[http://www.psychocats.net/ubuntu/pureubuntu](http://www.psychocats.net/ubuntu/pureubuntu)

Thats what I tried, it didn't work.  I know that thats the standard answer to this question...

---

### Post by cortman on 2012-06-13
> **Skerps said:**
> It sadly didn't change anything :(

Try running the giant apt-get remove command from the tutorial, only track down and exclude "kubuntu-desktop" from the list.

---

### Post by Skerps on 2012-06-13
> **cortman said:**
> Try running the giant apt-get remove command from the tutorial, only track down and exclude "kubuntu-desktop" from the list.

Still the same message...

---

### Post by Skerps on 2012-06-14
I just tried installing GNOME using [this]("http://www.filiwiese.com/installing-gnome-on-ubuntu-12-04-precise-pangolin/") tutorial but it didn't let me chose a GNOME option in the login screen (and the login screen is not the same as in the tut)...

Anybody know more about this?

---

### Post by cortman on 2012-06-14
Run

```
sudo apt-get -f install
sudo apt-get clean
sudo apt-get autoremove
sudo apt-get purge kubuntu-desktop
```

See if that will do it.

---

### Post by Skerps on 2012-06-14
> **cortman said:**
> Run

```
sudo apt-get -f install
sudo apt-get clean
sudo apt-get autoremove
sudo apt-get purge kubuntu-desktop
```See if that will do it.

This is what i'm getting now:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  libunity6
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 49 not upgraded.
tinus@tinus-linux:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  libunity6
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 49 not upgraded.
tinus@tinus-linux:~$ sudo apt-get clean
tinus@tinus-linux:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  libunity6
0 upgraded, 0 newly installed, 1 to remove and 49 not upgraded.
After this operation, 541 kB disk space will be freed.
Do you want to continue [Y/n]? Y
Abort.

```

No matter what I do its still "Aborts"...

---

### Post by cortman on 2012-06-14
Very odd- run

```
sudo apt-get purge libunity6
```

You mention you want to use Gnome shell- to install that run

```
sudo apt-get install gnome-shell
```

---

### Post by Skerps on 2012-06-15
> **cortman said:**
> Very odd- run

```
sudo apt-get purge libunity6
```You mention you want to use Gnome shell- to install that run

```
sudo apt-get install gnome-shell
```

The first command seems not to have done much, the second on the other hand did install GNOME which is weird because I tried it before but it didn't get installed then...

The KDE apps are still not removed...

---

### Post by cortman on 2012-06-15
> **Skerps said:**
> The first command seems not to have done much, the second on the other hand did install GNOME which is weird because I tried it before but it didn't get installed then...

The KDE apps are still not removed...

Did it actually remove libunity6?
If so, run the big remove command again.
If not, please post error output.

---

### Post by Skerps on 2012-06-15
> **cortman said:**
> Did it actually remove libunity6?
If so, run the big remove command again.
If not, please post error output.

I did remove something, if I try the big command to remove all of KDE the error stays the same.

A rerun of you command gave me this:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Virtual packages like 'libunity6' can't be removed
0 upgraded, 0 newly installed, 0 to remove and 49 not upgraded.
 
```

I don't know for sure if:

```
Virtual packages like 'libunity6' can't be removed
```

was said the first time I ran the command.

---

