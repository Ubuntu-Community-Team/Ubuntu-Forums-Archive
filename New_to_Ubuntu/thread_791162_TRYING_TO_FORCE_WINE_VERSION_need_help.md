---
title: "TRYING TO FORCE WINE VERSION need help"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by dtrot55 on 2008-05-11
I am trying to force WINE from the most recent version to version 46.  I go to my synaptic package manager and click on wine and go to package and force version is unselectable....can someone please help...seems that this version is better for running games that i am having issues with...my current wine version is only giving me 9-20 FPS in CSS which is horrible...any help would be much appreciated

---

### Post by RequinB4 on 2008-05-11
i386: [http://wine.budgetdedicated.com/archive/ubuntu/feisty/wine_0.9.46~winehq0~ubuntu~7.04-1_i386.deb](http://wine.budgetdedicated.com/archive/ubuntu/feisty/wine_0.9.46~winehq0~ubuntu~7.04-1_i386.deb)

amd64: [http://wine.budgetdedicated.com/archive/ubuntu/feisty/wine_0.9.46~winehq0~ubuntu~7.04-1_amd64.deb](http://wine.budgetdedicated.com/archive/ubuntu/feisty/wine_0.9.46~winehq0~ubuntu~7.04-1_amd64.deb)

Don't forget to uninstall beforehand!
```

sudo apt-get remove wine

```

---

### Post by dtrot55 on 2008-05-11
i tried that and i got this error:

Error: Dependency is not satisfiable: libldap2

---

### Post by RequinB4 on 2008-05-11
How did you install the version of wine you have now?

May just need the package:
```
sudo apt-get install libldap2
```

---

### Post by dtrot55 on 2008-05-11
Here's what i got from that:

dtrot@Ubuntu-Dtrot:~$ sudo apt-get install libldap2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libldap2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  slapd libldap-2.4-2
E: Package libldap2 has no installation candidate
dtrot@Ubuntu-Dtrot:~$ 

Still Erroring out.

---

### Post by RequinB4 on 2008-05-12
Install the slapd and libldap-2.4-2 packages (If it tells you that they are incompatible, just install the libldap-2.4-2 package).  Either use sudo apt-get install or system-admin-synaptic package manager.

You're going to have problems with outdated dependancies when installing software meant for feisty.  No big deal.

---

### Post by Gazneth on 2008-05-12
Try playonlinux to manage wine versions. I just installed 0.9.46 myself to test and it works perfectly. They have their own repository so you need to enable it then install playonlinux through synaptic. playonlinux.com You can even have different version assigned to different games.

---

### Post by dtrot55 on 2008-05-12
Thanks for stickin in with me on this...2.4-2 is already installed....still erroring...but i thoght you could just do the add/remove wine and then just go in to the synapic package manager and do a package force version.??

---

### Post by dtrot55 on 2008-05-12
> **Gazneth said:**
> Try playonlinux to manage wine versions. I just installed 0.9.46 myself to test and it works perfectly. They have their own repository so you need to enable it then install playonlinux through synaptic. playonlinux.com You can even have different version assigned to different games.

i got the file but when i try to put it in the repositories i get this:

dtrot@Ubuntu-Dtrot:~$ /etc/apt/sources.list
bash: /etc/apt/sources.list: Permission denied
dtrot@Ubuntu-Dtrot:~$ 

dtrot@Ubuntu-Dtrot:~$ deb [http://apt.wxwidgets.org/](http://apt.wxwidgets.org/) etch-wx main
bash: deb: command not found
dtrot@Ubuntu-Dtrot:~$ 

Forgive the noobness...im still learning

---

### Post by Gazneth on 2008-05-12
Ok don't install the .deb file. Copy and paste the following lines into a terminal window. These will install the repository first then the program using apt-get. For Gutsy version:
```
sudo wget http://playonlinux.botux.net/playonlinux_gutsy.list -O /etc/apt/sources.list.d/playonlinux.list
```then
```
wget -q http://playonlinux.botux.net/pol.gpg -O- | sudo apt-key add -

```
For Hardy version:
```
sudo wget http://playonlinux.botux.net/playonlinux_hardy.list -O /etc/apt/sources.list.d/playonlinux.list
``` then
```
wget -q http://playonlinux.botux.net/pol.gpg -O- | sudo apt-key add -
```
To install playonlinux then copy these:
```
sudo apt-get update
```
```
sudo apt-get install playonlinux
```
It is normally better to install programs through the repository system than by using .deb files.

---

### Post by dtrot55 on 2008-05-12
Ok got everything in...no errors with your code...ummmm now what? hehe  me<------noob

---

### Post by Gazneth on 2008-05-12
Ok start the playonlinux program, it usually shows up under games. Then menu >tools>manage wine versions. That is where the magic is, you can install other wine versions and assign them to different programs as needed. Install directx is also another menu option under tools if you need it.

I think you need to install your games under playonlinux for it to manage them properly, not positive though.

---

### Post by dtrot55 on 2008-05-12
K installed everything adn tried out CSS.  Im getting upwards to 35fps now but its still nowhere near what it should be and the 35fps isnt constant so there is choppyness....I even turned everything down to medium and all the way down to 1024x768 resolution and no real improvement there....any code or somthing i could show you???

---

### Post by Pap3r on 2008-05-12
> **dtrot55 said:**
> K installed everything adn tried out CSS.  Im getting upwards to 35fps now but its still nowhere near what it should be and the 35fps isnt constant so there is choppyness....I even turned everything down to medium and all the way down to 1024x768 resolution and no real improvement there....any code or somthing i could show you???

What GPU do you have?  Is anything overclocked?

---

### Post by brigux on 2008-05-12
Before going back to an old version I would try the v1.0RC1 (please post your experience if you do)

```
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list -O /etc/apt/sources.list.d/winehq.list
```

```
sudo apt-get update
```

```
sudo apt-get upgrade
```

```
wine --version
```
->wine-1.0-rc1

---

### Post by dtrot55 on 2008-05-12
> **Pap3r said:**
> What GPU do you have?  Is anything overclocked?

XFX 8600GT XXX...it is overclocked but it's factory oc'd i did nuthing to it

---

### Post by dtrot55 on 2008-05-12
installed 1.0 and got the same result...9-20fps and with all my setting on low i get 20-35fps...so 1.0 didnt help either.

---

