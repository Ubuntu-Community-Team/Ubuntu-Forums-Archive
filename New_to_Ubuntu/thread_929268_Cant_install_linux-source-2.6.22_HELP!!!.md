---
title: "Cant install linux-source-2.6.22 HELP!!!"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by KuroYoma on 2008-09-24
I am running a full upgraded Gutsy Gibbon 7.10 Ubuntu laptop


when i type this into the terminal i get
sudo apt-get install linux-source-2.6.22 build-essential gawk

Reading package lists... Done
Building dependency tree       
Reading state information... Done
gawk is already the newest version.
gawk set to manual installed.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: g++ (>= 4:4.1.1) but it is not going to be installed
E: Broken packages

---

### Post by nowshining on 2008-09-24
try sudo apt-get install -f

---

### Post by Crafty Kisses on 2008-09-24
Try running the following commands:
```
sudo dpkg --configure -a
sudo apt-get clean
sudo apt-get update
sudo apt-get install build-essential
sudo apt-get install libc6-dev
```
Then try reinstalling the kernel sources:
```
sudo apt-get install linux-source-2.6.22
```
That should solve your issues.

---

### Post by KuroYoma on 2008-09-24
> **nowshining said:**
> try sudo apt-get install -f

sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

this is what I got.

Codename:  I can now get the source code to install but build essentials and libc6-dev still will not

for libc6-dev i get: 
apt-get install libc6-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libc6-dev: Depends: libc6 (= 2.6.1-1ubuntu10) but 2.7-10ubuntu3 is to be installed
E: Broken packages

---

### Post by Crafty Kisses on 2008-09-24
I guess you can try running this:
```
sudo dpkg -r --force-depends libc6-dev
sudo apt-get install -f
```
That should force install that dependency.

---

### Post by bruce89 on 2008-09-24
Have you got non-standard repositories, as the system is getting confused between different versions of stuff.

---

### Post by KuroYoma on 2008-09-24
when i use the code:
sudo dpkg -r --force-depends libc6-dev
I get:
sudo dpkg -r --force-depends libc6-devdpkg - warning: ignoring request to remove libc6-dev which isn't installed.

I am not sure what you mean by non-standard repositories but i have added the Wine, Virtualbox (non-free), and XBMC repositories to my third-party list.

---

### Post by nowshining on 2008-09-24
oepn up synaptic does a dialog box come up telling u have broken packages??

---

### Post by KuroYoma on 2008-09-24
> **nowshining said:**
> oepn up synaptic does a dialog box come up telling u have broken packages??

No it does not.

---

### Post by Crafty Kisses on 2008-09-24
The following command should fix the broken packages:
```
sudo dpkg --configure -a
```
Then try installing that dependency, I actually gave you the command to force remove the dependency, I'm sorry for that, try this command to force install the dependency instead:
```
sudo apt-get install -f libc6-dev
```

---

### Post by KuroYoma on 2008-09-24
> **Codename said:**
> The following command should fix the broken packages:
```
sudo dpkg --configure -a
```
Then try installing that dependency, I actually gave you the command to force remove the dependency, I'm sorry for that, try this command to force install the dependency instead:
```
sudo apt-get install -f libc6-dev
```

I ran both codes and got

```
sudo apt-get install -f libc6-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libc6-dev: Depends: libc6 (= 2.6.1-1ubuntu10) but 2.7-10ubuntu3 is to be installed
E: Broken packages

```

Ok so i am running libc6 2.7-10  but build-essential calls for version 2.6.1
is there any way to downgrade?

I appreciated all the help but i have to go. will be back on tomorrow

---

### Post by KuroYoma on 2008-09-25
does anyone have any suggestions on how to downgrade libc6 to the 2.6.1-1 version?

---

### Post by nowshining on 2008-09-25
synaptic - select the item - package menu - force version..

---

### Post by KuroYoma on 2008-09-25
WOOT!!!!!   it worked

Build essentials is now installing

THANK YOU SO MUCH

---

### Post by nowshining on 2008-09-25
> **KuroYoma said:**
> WOOT!!!!!   it worked

Build essentials is now installing

THANK YOU SO MUCH

remember as long as the ol' version is in catch/on the HD, the force version should always work... - also may i suggest locking the package if one can, same thing in synaptic but choose lock pakage.. :)

---

### Post by KuroYoma on 2008-09-25
OK thanks

---

