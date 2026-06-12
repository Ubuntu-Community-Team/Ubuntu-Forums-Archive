---
title: "Installing g++ on 6.10"
date: 2006-11-28
forum: Programming Talk
---

### Post by Fafnr on 2006-11-28
Hiya :-)

I'm trying to learn a bit of c++ on my nice and shiny new ubuntu 6.10 :-)
Mainly because I thought it'd be fun, but also because I wanted a small program to make smb-mounting a bit easier for me.

But, when I apt-get g++ I get:
```

soren@soren-laptop:~$ sudo apt-get install g++
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
  g++: Depends: g++-4.1 (>= 4.1.1-2) but it is not going to be installed
E: Broken packages

```
So, I tried:
```

soren@soren-laptop:~$ sudo apt-get install g++-4.1
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
  g++-4.1: Depends: gcc-4.1-base (= 4.1.1-13ubuntu5) but 4.1.1-19 is to be installed
           Depends: gcc-4.1 (= 4.1.1-13ubuntu5) but 4.1.1-19 is to be installed
           Depends: libstdc++6-4.1-dev (= 4.1.1-13ubuntu5) but it is not going to be installed
E: Broken packages

```
o
As I traverse down this way, it basically boils down to the packages are already installed?!
(sudo apt-get install gcc-4.1 just says I already have the newest version), 

I've hit this sort of problem before, but what do I do?

I'm relatively new to the more advanced aspects of Linux, so please be gentle. :-)

Regards,

Søren

---

### Post by hod139 on 2006-11-28
Try installing the meta package build-essential, which will include g++ in addition to everything else you need to start building.

---

### Post by Fafnr on 2006-11-28
Thx for your suggestion hod139, but I get the same problem. :(

```

soren@soren-laptop:~$ sudo apt-get install build-essential
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
  build-essential: Depends: g++ (>= 4:4.1.1) but it is not going to be installed
E: Broken packages

```

:-(

---

### Post by hod139 on 2006-11-28
What happens if you update the repositories
```
sudo apt-get update
```

You can also use aptitude after updating to install (which we should all be using instead of apt, I don't know why I continue to use apt) the package:
```

sudo aptitude install build-essential

```

---

### Post by Fafnr on 2006-11-28
Brilliant, thank you!

aptitude allows me to downgrade a couple of packages, and seems to be able to resolve it all! Yay! :-)

Thanks a lot - I'll definetaly use aptitude from now on. :-)

BTW, is aptitude a strict upgrade from apt-get? 
I was thinking of binding aptitude to apt-get since that's where my mind goes automatically...

Regards,

Søren

---

### Post by hod139 on 2006-11-28
> **Fafnr said:**
> 
BTW, is aptitude a strict upgrade from apt-get? 
I was thinking of binding aptitude to apt-get since that's where my mind goes automatically...

aptitude is  a separate application from apt-get.  I don't think "binding" (linking?) will work.  We both will have to just remember to type aptitude instead of apt-get.   I'm just glad it worked for you.

---

### Post by mikito238 on 2007-06-27
awesome!!

---

