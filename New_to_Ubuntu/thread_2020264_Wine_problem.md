---
title: "Wine problem"
date: 2012-07-08
forum: New to Ubuntu
---

### Post by czgirb on 2012-07-08
Previously, when I installed Ubuntu 12.04, the Wine was installed through Ubuntu Software Center (USC). It was Wine 1.4.
Yesterday, when I do a browsing, I found there is Wine 1.5.8 in the following URL:
* [http://www.noobslab.com/2012/07/install-wine-158-in-ubuntulinux-mint.html](http://www.noobslab.com/2012/07/install-wine-158-in-ubuntulinux-mint.html)
So, I wish for having my Wine was updated.

But after I follow the instructions, I found I unable to open:
[B]* Winetricks
* Configure Wine
* All Windows' applications, which installed via wine.[/B]

Any idea?
[U][B]
Note:[/B][/U]
It's never mean **the instructions given is wrong.**
But ... there was a problem with my **Ubuntu/Wine**.
So, I wish somebody able to give me a solution.

In Windows, there is a **system repair**. Is there any in Ubuntu?

---

### Post by ubudog on 2012-07-08
Hi!

According to [WineHQ]("http://www.winehq.org/"), Wine 1.5.8 is a development version, and as such may be buggy.  To downgrade your Wine installation, do the following.

Since you added the Wine PPA in the instructions, let's purge that, which should also downgrade your Wine install.

Run the following commands in a terminal:
```
sudo apt-get install ppa-purge
```

Then do:
```
sudo ppa-purge ppa:ubuntu-wine/ppa
```

Now you should be downgraded and reverted back to how it was before.

I'd suggest trying [this]("http://www.winehq.org/download/ubuntu") guide, if you want to run the development version, although you may encounter the same issue.

Best,
ubudog

---

### Post by czgirb on 2012-07-08
```

***@***:~$ sudo apt-get install ppa-purge
[sudo] password for ***: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ppa-purge is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
***@***:~$ sudo ppa-purge ppa:ubuntu-wine/ppa
Updating packages lists
PPA to be removed: ubuntu-wine ppa
Package revert list generated:
 gnome-exe-thumbnailer/precise wine1.5/precise wine1.5-i386/precise 
wine-gecko1.5/precise winetricks/precise

Disabling ubuntu-wine PPA from 
/etc/apt/sources.list.d/ubuntu-wine-ppa-precise.list
Updating packages lists
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Release 'precise' for 'wine1.5' was not found
E: Release 'precise' for 'wine1.5-i386' was not found
E: Release 'precise' for 'wine-gecko1.5' was not found
Unable to find an archive "precise" for the package "wine1.5"
Unable to find an archive "precise" for the package "wine1.5-i386"
Unable to find an archive "precise" for the package "wine-gecko1.5"
Unable to find an archive "precise" for the package "wine1.5"
Unable to find an archive "precise" for the package "wine1.5-i386"
Unable to find an archive "precise" for the package "wine-gecko1.5"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.
                                         
PPA purged successfully using aptitude fallback
***@***:~$ 
```

I really do the copy and it was informed to be installed.
How can it said:
> 
E: Release 'precise' for 'wine1.5' was not found
E: Release 'precise' for 'wine1.5-i386' was not found
E: Release 'precise' for 'wine-gecko1.5' was not found
Unable to find an archive "precise" for the package "wine1.5"
Unable to find an archive "precise" for the package "wine1.5-i386"
Unable to find an archive "precise" for the package "wine-gecko1.5"
Unable to find an archive "precise" for the package "wine1.5"
Unable to find an archive "precise" for the package "wine1.5-i386"
Unable to find an archive "precise" for the package "wine-gecko1.5"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.


Please do a favor for my by explaining, why ....
Please ....

---

### Post by czgirb on 2012-07-08
> **ubudog said:**
> 
... Run the following commands in a terminal:
```
sudo apt-get install ppa-purge
```
Then do:
```
sudo ppa-purge ppa:ubuntu-wine/ppa
```
Now you should be downgraded and reverted back to how it was before ...

 
According to what you said:
I think, the ppa to be purge is ppa:ubuntu-wine/ppa
Cos this the ppa used in URL given
Now, I think I able to do the same thing, GIMP, with the same mehod.
* [http://www.noobslab.com/2012/04/install-gimp-28-on-ubuntu-1204-precise.html](http://www.noobslab.com/2012/04/install-gimp-28-on-ubuntu-1204-precise.html)
so I sudo ppa-purge ppa:otto-kesselgulasch/gimp
but the result is:
[COLOR=red][FONT=monospace][/FONT][/COLOR]```

***@***b:~$ sudo ppa-purge ppa:otto-kesselgulasch/gimp
[sudo] password for ***: 
Updating packages lists
PPA to be removed: otto-kesselgulasch gimp
Warning:  Could not find package list for PPA: otto-kesselgulasch gimp
***@***:~$ 

```
Any idea? Please help ...

---

### Post by ubudog on 2012-07-08
Alternatively you can just remove Wine, and install the older version.

Let's make a backup of .wine before doing this:
```
cp -a ~/.wine ~/.winebak
```

Now, let's remove the current Wine installation:
```
sudo apt-get remove wine
```

And let's remove the PPA:
```
sudo add-apt-repository --remove ppa:ubuntu-wine/ppa
```

Now update your package lists:
```
sudo apt-get update
```

Then install the stable version of Wine:
```
sudo apt-get install wine1.4
```

Hope that helps,
ubudog

---

