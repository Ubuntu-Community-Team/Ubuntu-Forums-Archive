---
title: "Why download and compile madwifi"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by pgte3 on 2008-07-17
Recently I got the wireless on my laptop working by downloading and compiling a wireless driver from madwifi (see link).

[http://ubuntuforums.org/showthread.php?t=861683](http://ubuntuforums.org/showthread.php?t=861683)

Why is this necessary? Why is the binary equivalent of what I compiled and created not in the ubuntu repositories somewhere.

---

### Post by Bachstelze on 2008-07-17
Madwifi is included with Ubuntu. Most likely, the one you compiled is a newer version.

---

### Post by pgte3 on 2008-07-17
I see a package called madwifi-tools within the universe repository. Does this package contain the drivers for the various wireless cards, or is this a collection of tools to work with wifi?

---

### Post by pgte3 on 2008-07-17
The description of the madwifi-tools package is:

This package provides userspace tools for the madwifi driver. The tools are required to use and manipulate the madwifi interfaces present in a system.

I do not think this is the drivers, it sounds like tools to work with madwifi drivers.

I am still wondering why the drivers themselves are not available through the repositories?

---

### Post by Bachstelze on 2008-07-17
They are, and they are even installed by default. Please don't make such strong statements when you have no clue, thanks.

[http://packages.ubuntu.com/search?searchon=contents&keywords=ath_pci.ko&mode=exactfilename&suite=hardy&arch=any](http://packages.ubuntu.com/search?searchon=contents&keywords=ath_pci.ko&mode=exactfilename&suite=hardy&arch=any)

---

### Post by pgte3 on 2008-07-17
I am sorry you interpreted my statements as strong, I am not sure what you meant by strong, but assume that it is not good. It is certainly not my intention to offend or be aggressive. I am simply trying to understand ubuntu.

I see the madwifi driver in the link you provided. When I was searching for madwifi packages the only hit I got was madwifi-tools, the reason for that appears to be the way I searched the repositories. I searched for package name only not description. When I search using description I found the packages you are referring too.

So I guess the answer to my orignal question is that the wireless card I have required a newer driver than what was available in the repositories.

---

### Post by Bachstelze on 2008-07-17
> **pgte3 said:**
> So I guess the answer to my orignal question is that the wireless card I have required a newer driver than what was available in the repositories.

Exactly.

---

