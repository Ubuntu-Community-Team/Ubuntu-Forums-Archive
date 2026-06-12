---
title: "Installation script for Celtx"
date: 2008-01-15
forum: Programming Talk
---

### Post by Barbatruk_tho on 2008-01-15
Hello,

First of all, please be nice with my english, i'm French ;)

I would like to create a script that would automatically download and install Celtx. It would create a new 'Celtx' directory in /usr/local/, download the archive inside, then uncompress it. Then, it would also download a script to run Celtx, into /usr/bin. By this means, Celtx could simply be run with a 'celtx' command.

This would simply be an automatic script for this manual method I wrote just before (and which works).

[http://doc.ubuntu-fr.org/celtx](http://doc.ubuntu-fr.org/celtx) (french...)

Sadly, I'm not very experimented in shell scripts programming, and my script doesn't work. I think it's because the script should first ask for root password, but I failed to understand how I could do that.

Well, this is the stuff (do not mock me, I'm a beginner ;))

```
#!/bin/sh

#Celtx automatic installation script for Ubuntu

#Information about the script
echo "This script will install Celtx 0.997 on your system"

#Root mode run
echo "Entrez votre mot de passe sudo"
sudo echo -n "" || error_exit "Le script n'a pas obtenu les droits root"

#creation of the Celtx local folder
sudo mkdir /usr/local/celtx
cd /usr/local/celtx
#Download from the official site
sudo wget http://www.celtx.com/download/Celtx-fr.tar.gz
#Uncompress the archive
sudo tar xvzf /usr/local/celtx/Celtx-fr.tar.gz
#User rights definition
sudo chmod 755 -R /usr/local/celtx/celtx
#Remove the archive
sudo rm /usr/local/celtx/Celtx-fr.tar.gz

#Celtx run script installation
cd /usr/bin
#Download the script
sudo wget http://www.aesplendaar.net/celtx
#User rights definition
sudo chmod 755 -R /usr/bin/celtx

echo "Celtx has been installed on your system. To run it, enter 'celtx' in a command line."
```

Error is 

```
/usr/bin/celtx: 5: ./celtx: Permission denied
```

Thanks a lot for your help ;)

---

