---
title: "Remove wine 1.5.8"
date: 2012-07-16
forum: New to Ubuntu
---

### Post by blueshead on 2012-07-16
I'd like to revert back to 1.4.1

---

### Post by raja.genupula on 2012-07-16
type as ```
sudo apt-get install wine=1.4.1
``` in your terminal . 

all the best ,:)

---

### Post by czgirb on 2012-07-16
> **blueshead said:**
> I'd like to revert back to 1.4.1

Yesterday I just do **sudo apt-get install wine** ... it installed **1.4.x version**. (A version, which installed through **USC**).
Not the new one. Since the new one is not **Wine's final stable version**.
And based on the information showed in Terminal, it said **1.5.8 version** is removed.
What is your opinion regarding to this?
**PS:**
Is it means that there will be no **1.5.8** file left in my system?
If not ... please tell me how to make my system cleaned.
Is the **sudo apt-get autoclean** command is enough?

---

### Post by raja.genupula on 2012-07-16
Actually autoclean for this 

> **autoclean**
Like clean, autoclean clears out the local repository of retrieved package files. The difference is that it only removes package files that can no longer be downloaded, and are largely useless. This allows a cache to be maintained over a long period without it growing out of control. The configuration option APT::Clean-Installed will prevent installed packages from being erased if it is set to off.

and whats the output 
```
wine --version

```

---

### Post by blueshead on 2012-07-16
> **raja.genupula said:**
> type as ```
sudo apt-get install wine=1.4.1
``` in your terminal . 

all the best ,:)

 Version '1.4.1' for 'wine' was not found

---

### Post by blueshead on 2012-07-16
> Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine : Depends: wine1.4 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.


I'm still stuck with wine 1.5.8

---

### Post by Elfy on 2012-07-16
Try 

```
sudo apt-get install wine1.4
```

apt-cache search <package> in a terminal will tell you what you have available


Also if you have errors please post the whole output, use code tags [noparse]```
[/noparse] and [noparse]
```[/noparse]

---

### Post by blueshead on 2012-07-16
> **Elfy said:**
> Try 

```
sudo apt-get install wine1.4
```

apt-cache search <package> in a terminal will tell you what you have available


Also if you have errors please post the whole output, use code tags [noparse]```
[/noparse] and [noparse]
```[/noparse]


```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine1.4 : Depends: wine1.4-amd64 (= 1.4-0ubuntu4)
E: Unable to correct problems, you have held broken packages.
blues@blues:~$ 

```

---

### Post by prshah on 2012-07-16
> **blueshead said:**
> I'd like to revert back to 1.4.1

Hello:

How did you install wine 1.5.8; I'm guessing that you added the WINE PPA.

In this case, please use apt-get to remove the current WINE (1.5.8). Then, remove the PPA (look in /etc/apt.sources.list.d/), apt-get update, and then install wine (this will install the repository version, not the PPA version).

Summary```
sudo apt-get remove wine # optionally, add --purge to remove all settings as well
sudo rm /etc/apt/sources.list.d/wineppa # example, REPLACE WITH YOUR OWN PPA NAME
sudo apt-get update
sudo apt-get install wine # installs wine (1.4-0ubuntu4 Ubuntu:12.04/precise

```

Please post back if you need more specific instructions, or in case of any problems.

Note: Deleting the wrong PPA may cause problems in your setup. Please ensure that you are removing the correct PPA. If in doubt, please post the output of the following commands before attempting anything:
```
cat /etc/apt/sources.list
ls -l /etc/apt/sources.list.d/

```

---

### Post by blueshead on 2012-07-16
> **prshah said:**
> Hello:

How did you install wine 1.5.8; I'm guessing that you added the WINE PPA.

In this case, please use apt-get to remove the current WINE (1.5.8). Then, remove the PPA (look in /etc/apt.sources.list.d/), apt-get update, and then install wine (this will install the repository version, not the PPA version).

Summary```
sudo apt-get remove wine # optionally, add --purge to remove all settings as well
sudo rm /etc/apt/sources.list.d/wineppa # example, REPLACE WITH YOUR OWN PPA NAME
sudo apt-get update
sudo apt-get install wine # installs wine (1.4-0ubuntu4 Ubuntu:12.04/precise

```

Please post back if you need more specific instructions, or in case of any problems.

Note: Deleting the wrong PPA may cause problems in your setup. Please ensure that you are removing the correct PPA. If in doubt, please post the output of the following commands before attempting anything:
```
cat /etc/apt/sources.list
ls -l /etc/apt/sources.list.d/

```

That seemed to work.. Unfortunately it also removed gnome desktop, krita and a few other things.. I'll spend the rest of the night getting things back in order.

Anyway thank you for your help..   I'll mark it as solved..

---

### Post by prshah on 2012-07-16
> **blueshead said:**
> That seemed to work.. Unfortunately it also removed gnome desktop, krita and a few other things.

Since WINE and Gnome have no dependencies on each other, this is a very mysterious result.

The only causes for this I can think of are:

a) Attempt to remove important lines from sources.list or files from sources.list.d
b) apt-get remove command that also removes dependencies may have been using potentially troublesome flags such as -f, -m, --force-yes, etc. Note that removing the meta package "gnome-desktop" will NOT remove GDM / lightdm; some other command or list of package names is required.

if you can post a list of your recent commands (history), it may help pinpoint what went wrong.

---

### Post by czgirb on 2012-07-16
> **raja.genupula said:**
> 
... and whats the output 
```
wine --version

```

***@***:~$ wine --version
wine-1.4
***@***:~$ 
**PS**:
It should be the latest & stable version, which installed via USC.
But never stable in my lappie. Most my beloved applications, **iTunes **(even the most stable one, 7version) & **FormatFactory** are stucked ... unable to closed. And forced me to restart the lappie.
So, my currently planing, I will not used Wine, except for **F2K** and **SketchUp**

---

### Post by blueshead on 2012-07-16
Why gnome desktop and krita were removed I have no idea. I now have wine 1.4 running which is fine with me. I only use it for 1 app, which is working great.

---

