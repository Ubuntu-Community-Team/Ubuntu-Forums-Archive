---
title: "if/then statement issues"
date: 2009-06-19
forum: Programming Talk
---

### Post by dsell88 on 2009-06-19
Greetings. I am a network administrator on a Windows based domain, and I am trying create a script that configures an Ubuntu image when we first bring it up. Since I am used to the Windows environment and most scripting I do is in batch or VB, I have very little idea about what I am doing in the linux scripting shell. 

Anyways, I made up this script that installs packages we want, copies configuration files, and hooks up AD authentication. I've tested this script on the machine I wrote this on, and it worked. However, when I write it to a CD and try to run it off of that I get this error:
> Syntax error: end of file unexpected (expecting "then")The code is as follows:

```

#!bin/bash
###########

if [ "$USER" != "root" ]
then
    echo "You must be logged in as root to run this script!"
    exit
fi
    
echo "Installing System Packages."
    
apt-get update
apt-get install likewise-open
apt-get install samba4
apt-get install yum
apt-get install gawk
apt-get install filezilla
    
yum -y upgrade
echo "Finished with System Upgrades."
echo

echo "Setting up computer for domain Authentication."
echo

echo "** Updating System Configuration Files."
cp -rf system\ files/* /

echo "** Setting up hostname configuration."
echo
read -p "Enter the name of this computer (ex: COMP-L): " computername

echo "127.0.0.1 $computername    $computername.subdomain.domain
localhost.localdomain    localhost" >> /etc/hosts
hostname "$computername.subdomain.domain"
    
read -p "Enter domain admin username (ex: usr@DOMAIN for DOMAINALIAS or usr@SUBDOMAIN.DOMAIN for SUBDOMAINALIAS account): " username
    
domainjoin-cli join subdomain.domain $username
update-rc.d likewise-open defaults
/etc/init.d/likewise-open start

echo "Finished setting up domain authentication."
echo "You should be able to reboot Ubuntu now and log in with your company username using DOMAINALIAS\usr or usr@DOMAIN."
echo "End of Script."
echo

```I'm pretty sure I used the correct syntax for my if statement. I mean, if it was incorrect it shouldn't have worked in the first place. So why should it work if I run it from the desktop but not after I burn it to a disk?

BTW I'm running Ubuntu 9.04 on Microsoft Virtual PC 2007

Thanks,
DSell88

---

### Post by dwhitney67 on 2009-06-19
Your if-then-fi block of code looks ok, although I would've used "id -u" to obtain the user's ID.  The USER environment variable can be easily spoofed.

```

if [ `id -u` -ne 0 ]
then
    echo "You must be logged in as root to run this script!"
    exit
fi

```

As for the issue you are having, you indicated that you are running from a disk?  Can you verify that you have bash available at this point?  Perhaps you should consider using sh instead.

```

#!/bin/sh

...

```

---

### Post by dsell88 on 2009-06-19
Hmm, I made the changes, but it still gives the same error message. Not sure what's going on. I've gone through this several times. I will retype the same exact script into a new text file, and be able to run it, but once it gets put on a "CD" (It's actually an iso image that I have mounted to the Virtual machine I'm running ubuntu on), it gives the error again. I copy the script off of the "CD" and try to run it from there and I still get the message. Then when I retype it in a new text file, and it works. I've repeated this cycle a couple of times, and I can't figure out how or why it goes wrong when I put it on the ISO...

---

### Post by ghostdog74 on 2009-06-19
put set -x in your script at the top after the shebang and run your script again

---

### Post by croto on 2009-06-20
Man, you are missing a '/' in the first line. It should look like:

#!/bin/bash

---

