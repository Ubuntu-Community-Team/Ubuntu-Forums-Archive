---
title: "Computer/Ubuntu issues...So many problems."
date: 2012-02-04
forum: New to Ubuntu
---

### Post by GatesBarber on 2012-02-04
I'm new at Ubuntu...and I'm going to go ahead and apologize now. I am a NEWB. So don't read this if you get frustrated easily...Assume I don't know anything about computers at all.

So...I'm having troubles. Whenever I try to download something using sudo apt-get, it can't read the file or it reports it as not being there at all. I couldn't open the software center either, and so I uninstalled it and tried to reinstall it...but now if I look under downloads all I see is the cardboard box...and I'm a super newb, I apologize and I really don't know how to get the programs out. 
And I'm having a ton of problems unpacking tar.gz, and I followed the online instructions but nothing seems to work. I'm at my wits end and I have no where else to turn.
I have some rpm files I have no idea what to do with...and deb, and zip and 7zip. I really just need someone experienced to help me slowly and simply so I can understand what to do and never run into any of these problems again. 

Do you think my problems have anything to do with my laptop battery running out quickly?

---

### Post by rudihawk on 2012-02-04
Try running: 

```
sudo apt-get update
```

Then try installing a package. 

.rpm files are not for Ubuntu, .deb are Ubuntu's package files. 

I'm sure someone with more experience and knowledge will be on hand to help you soon!

---

### Post by MG&amp;TL on 2012-02-04
Laptop battery is probably part of a kernel bug, which is being fixed. 

Okay, I'll run through how to install software in ubuntu, then you can tell me what's going wrong with it. :)

1. apt-get install <packagename> Example:

```
sudo apt-get install software-center
```

..installs the ubuntu software centre.

2. A .deb file. You can install them with the software centre, or with dpkg, like this:

```
sudo dpkg -i mypackage.deb
```

3. an rpm file. You may have some luck converting these to debs, with an application called alien.

4. a source file (tar.gz, tar.bz2) often used for less popular or new applications, these oftentimes need compiling yourself, and removing them afterwards can be a pain.

The further up this list, the better.

---

### Post by GatesBarber on 2012-02-04
Okay...so when I tried sudo apt-get install this is what I got:

E: Type '“deb' is not known on line 57 in source list /etc/apt/sources.list
E: The list of sources could not be read.

And with the software center...I got this.

Package software-center is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'software-center' has no installation candidate

---

### Post by MG&amp;TL on 2012-02-04
Okay, you have somehow managed to muck up your apt installation. Not a disaster, just not good, either. :)

Can you post the output of:

```
cat /etc/apt/sources.list
``` 

please?

Wrap it in code tags, the # sign at the top toolbar.

---

### Post by GatesBarber on 2012-02-04
Okay...heh...thanks. 

```
cat: /ect/apt/sources.list: No such file or directory

```

That's what I got. :/ I think you expected something...different?

---

### Post by MG&amp;TL on 2012-02-04
"/etc/apt/sources.list"

You mis-spelled etc. :)

---

### Post by GatesBarber on 2012-02-04
:D Oops. Hehe. Here, I got something...better (?) this time.

```
#deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)]/ oneiric main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric universe
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric universe
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu oneiric-security main restricted
deb-src http://security.ubuntu.com/ubuntu oneiric-security main restricted
deb http://security.ubuntu.com/ubuntu oneiric-security universe
deb-src http://security.ubuntu.com/ubuntu oneiric-security universe
deb http://security.ubuntu.com/ubuntu oneiric-security multiverse
deb-src http://security.ubuntu.com/ubuntu oneiric-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu oneiric partner
# deb-src http://archive.canonical.com/ubuntu oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu oneiric main
deb-src http://extras.ubuntu.com/ubuntu oneiric main
“deb http://deb.torproject.org/torproject.org experimental-lucid main”
“deb http://deb.torproject.org/torproject.org experimental-lucid main”

```

---

### Post by MG&amp;TL on 2012-02-04
Be very careful, but to remove the problem, I think you have to remove the inverted commas around the torproject entries, right at the bottom, so that it looks like this instead:

```
#deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)]/ oneiric main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric universe
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric universe
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu oneiric-security main restricted
deb-src http://security.ubuntu.com/ubuntu oneiric-security main restricted
deb http://security.ubuntu.com/ubuntu oneiric-security universe
deb-src http://security.ubuntu.com/ubuntu oneiric-security universe
deb http://security.ubuntu.com/ubuntu oneiric-security multiverse
deb-src http://security.ubuntu.com/ubuntu oneiric-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu oneiric partner
# deb-src http://archive.canonical.com/ubuntu oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu oneiric main
deb-src http://extras.ubuntu.com/ubuntu oneiric main
deb http://deb.torproject.org/torproject.org experimental-lucid main
deb http://deb.torproject.org/torproject.org experimental-lucid main
```

You can do this by running:

```
gksu gedit /etc/apt/sources.list
```



How did you install torproject, anyway, you should probably have oneeiric rather than lucid re

---

### Post by GatesBarber on 2012-02-04
Okay. So I ran it, and then put in my password, deleted the quote things and saved it. 

:D I ran sudo apt-get update and its doing it!
Will this solve all of the being-able-to-download-stuff problem? 

:) Thanks so much. -sigh- I was really at a loss...

---

### Post by GatesBarber on 2012-02-04
I think I installed TOR before this whole thing happened. Or do you mean the site I got it from?
And I don't know what 'oneeiric' OR 'lucid re' are..

---

### Post by rudihawk on 2012-02-04
> **GatesBarber said:**
> Okay. So I ran it, and then put in my password, deleted the quote things and saved it. 

:D I ran sudo apt-get update and its doing it!
Will this solve all of the being-able-to-download-stuff problem? 

:) Thanks so much. -sigh- I was really at a loss...

Well now that your 

```
sudo apt-get update
```

is working, you should be able to install things just by using: 

```
sudo apt-get install <packagename>
```

If you aren't comfortbale using apt-get you may want to reinstall the ubuntu software center. 

```
sudo apt-get install software-center
```

---

### Post by MG&amp;TL on 2012-02-04
Well...every release of Ubuntu is named, recently we've had:

OLD
10.04 - Lucid Lynx
10.10 - Maveric Meerkat
11.04 - Natty Narwhal
11.10 - Oneiric Ocelot (you're running this)
12.04 - Precise Pangolin (unstable, in active devlopment, release in April)
NEW

So, you've got the Lucid (10.04) repositories for tor, I'm not entirely sure how this would affect the newness of the software.

Anyway, run the following command:

```
sudo apt-get update && sudo apt-get upgrade
```

to update all your packages and upgrade if they've got a new version out. (update manager basically does this).

Then, you should be able to install whatever software you like.

You should probably be able to install and use the software centre now. 

Btw, some helpful apt commands:

```
sudo apt-get install <package>
```

install a package

```
sudo apt-get remove <package>
```

remove a package

```
sudo apt-get remove --purge <package>
```

remove a package, and its configuration files

```
apt-cache search <search term>
```

search for packages matching the search term.

```
apt-cache show <package>
```

show description and dependencies of a package.

Hope you've got your problem sorted now. :)

---

