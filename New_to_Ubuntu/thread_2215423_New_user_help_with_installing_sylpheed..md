---
title: "New user help with installing sylpheed."
date: 2014-04-06
forum: New to Ubuntu
---

### Post by hansindia on 2014-04-06
Here&#347; some one that just left XP for Lubuntu 13.10. , installed it yesterday and is already happy with the switch.

I have no knowledge whatsoever regarding installing etc. , and am looking for help with starting for example sylpheed, how to download software and when and how to switch to the 14.04 LTS version.

Could someone send me through?

Thanks.

---

### Post by bapoumba on 2014-04-06
Moved to its own thread in Absolute Beginners Section.

---

### Post by oldrocker99 on 2014-04-06
OK, first of all (since you likely don't have it installed). do this:

```
sudo apt-get install synaptic
```

Then you can run Synaptic. It's the premier package manager for Debian-type systems (of which Ubuntu is one), and has a quick search as well as a more thorough search.

```
sudo apt-get install {name of program}
``` will install practically any program you know the name of, and Synaptic has categories, making installation easy as can be.

---

### Post by DogMatix on 2014-04-06
I thought Sylpheed was installed by default nowadays with Lubuntu. I'm using it on a couple of Lubuntu machines (13.10 & 14.04). It definitely is available in the Lubuntu Software Centre (I just checked). You will be able to upgrade to 14.04 from 13.10 when it is officially released in a weeks time.

---

### Post by 3rdalbum on 2014-04-06
> **hansindia said:**
> Here&#347; some one that just left XP for Lubuntu 13.10. , installed it yesterday and is already happy with the switch.

I have no knowledge whatsoever regarding installing etc. , and am looking for help with starting for example sylpheed, how to download software and when and how to switch to the 14.04 LTS version.

Could someone send me through?

Thanks.

The Lubuntu Software Center program that comes with Lubuntu is the way to discover and install software on Lubuntu.

When Ubuntu / Lubuntu 14.04 comes out, the Lubuntu site will have instructions on upgrading.

---

### Post by buzzingrobot on 2014-04-07
To set up Sylpheed, you will need to know the names of the mail servers used by your mail provider, along with some other configuration information.  This information is typically provided somewhere at your mail provider's web site.  You will likely see only instructions for setting up a Windows machine, but the information itself applies to any mail application on any OS. 

For future reference, all supported Ubuntu software packages are located on servers known as the Ubuntu repositories.  When you use the Software Center program, it lists and categorizes the packages available in those repositories.  When you tell the Software Center to install a package, it downloads and installs that package, along with any other packages required to support it.  Other programs, like Synaptic, or the terminal program apt-get, access the same repositories, but provide a different interface.

---

### Post by m-dw on 2014-04-07
I learned something reading this thread.  I had thought that Sylpheed had morphed into Claws-Mail, but now know they are independent project (claws being forked from sylpheed-claws.

---

