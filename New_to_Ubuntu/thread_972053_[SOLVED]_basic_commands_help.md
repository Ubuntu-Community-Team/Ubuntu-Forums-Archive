---
title: "[SOLVED] basic commands help"
date: 2008-11-05
forum: New to Ubuntu
---

### Post by dizzy1kenobi on 2008-11-05
if I want to replace an installed program with a new one how do I do it?

like for instance: firefox for the latest version
or:
                   yasm 0.5.0 for 0.7.1

I don't quite understand the "make" and get commands

---

### Post by ./. on 2008-11-05
From the command line 'sudo aptitude install update' or 'sudo aptitude install safe-upgrade'

That should allow you to upgrade packages to whatever is the most recent version in the Repositories.

---

### Post by milosz.galazka on 2008-11-05
You can look at *aptitude* command.
It's great console tool, you can run it in terminal in Gnome/KDE and use mouse.

---

### Post by dizzy1kenobi on 2008-11-05
0

---

### Post by dizzy1kenobi on 2008-11-05
> **dizzy1kenobi said:**
> From the command line 'sudo aptitude install update' or 'sudo aptitude install safe-upgrade'

That should allow you to upgrade packages to whatever is the most recent version in the Repositories.



So would I also include the name of the program also  like 'sudo aptitude install safe-upgrade firefox'?

---

### Post by REDace0 on 2008-11-05
No, that's going to grab the latest versions of everything. 'update' gets the latest list of packages, 'safe-upgrade' installs the newer versions if there are any.

If you are trying to get the beta of firefox, you might try using Ubuntu Tweak.

---

### Post by LowSky on 2008-11-05
Also remember that Ubutnu only updates software up to it release date, For instance 8.10 has all the newest software up to October, anything that came out late or after that like the newer OpenOffice will not be including into Ubuntu until the next release.

So if you want the newer version between the 6 month windows, then you need to install by hand, the best way is to find the progrmas in a package format called DEB, DEBs are very simular to Setup.exe files for a program. If you cannot find a DEB then you need to compile by the source files, which really isn't that much harder, most website will give instruction on how to install. A thing to remember is that if the package is currently installed, you should remove it before installing a newer version by hand. If you are very new to linux may I suggest you stay with ubuntu version of software for a while. Most newer versions of Software offer very little over the older versions.

---

### Post by dizzy1kenobi on 2008-11-05
I updated everything when I installed two weeks ago.  If I don't have the latest version of these already then the only way for me to do it is manually and individually.  So what I need to know is what commands will I use (also so I can do these things for myself in the future) to remove something and replace it with another version?  I am in the middle of installing Handbrake and need yasm 0.6.0 or higher.  I have 0.5.0.

---

### Post by achase79 on 2008-11-05
To get a higher version from ubuntu you will probably have to upgrade your dist.  Intrepid has Yasm 0.7.1.

---

### Post by Idefix82 on 2008-11-05
I just googled a bit and it seems that for hardy there is actually a repository with binaries of Yasm 0.7.1
You need to add this repository to your list of repositories:
```
gksudo gedit /etc/apt/sources.list
```
and then paste these lines:
```
deb http://ppa.launchpad.net/hexmode/ubuntu hardy main
deb-src http://ppa.launchpad.net/hexmode/ubuntu hardy main
```
and save. Now do
```
sudo apt-get update
sudo apt-get install yasm
```

---

### Post by dizzy1kenobi on 2008-11-05
> **Idefix82 said:**
> I just googled a bit and it seems that for hardy there is actually a repository with binaries of Yasm 0.7.1
You need to add this repository to your list of repositories:
```
gksudo gedit /etc/apt/sources.list
```
and then paste these lines:
```
deb http://ppa.launchpad.net/hexmode/ubuntu hardy main
deb-src http://ppa.launchpad.net/hexmode/ubuntu hardy main
```
and save. Now do
```
sudo apt-get update
sudo apt-get install yasm
```

Should I uninstall yasm 0.5.0 first?

---

### Post by Idefix82 on 2008-11-05
The first command will open a text editor. That's where you save the file in after having included the two lines.
I forgot that Yasm 0.5 is already installed. You can either uninstall it, then do the procedure I have described to you, or you can leave it, do this procedure but instead of
```
sudo apt-get install yasm
```
you can just do
```
sudo apt-get upgrade
```
which will automatically replace all software you have by the newest version that is available in the repositories.

---

### Post by dizzy1kenobi on 2008-11-05
Now I am getting a message that the packages are not authenticated.  Any suggestions?

---

### Post by Idefix82 on 2008-11-05
Go ahead anyway.
I hope you understand that you are doing it at your own risk and I haven't tested this repository yet.

---

### Post by dizzy1kenobi on 2008-11-05
Exactly why I asked that question.  As someone who is just learning to install and uninstall I am sure that I cannot do damage control if something happens.  If it were your machine would you trust it?

---

