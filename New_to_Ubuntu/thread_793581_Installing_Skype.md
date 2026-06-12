---
title: "Installing Skype"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by bilbo.san on 2008-05-13
Hi,

Has anyone installed Skype on Ubuntu 8?... and how?
I looked on Add/Remove and on Synaptic and nothing comes up available... 
I am sure there should be a simple way... perhaps downloading the file from Skype for Ubuntu 7.04... but then what?

thanks
b.

---

### Post by Inxsible on 2008-05-13
Download Skype from this site. Choose Ubuntu as your distro and just double click on the file that you download. It will tell you if some dependencies are unmet.

[Download Skype for Ubuntu]("http://www.skype.com/download/skype/linux/choose/")

---

### Post by plucky on 2008-05-14
Skype is also in **Medibuntu** repository

See [this link](https://help.ubuntu.com/community/Medibuntu) for adding **Medibuntu** repository to your sources.list.


Good Luck

---

### Post by hyper_ch on 2008-05-14
Use Medibuntu repos.. that way it will also get auto-updated.

---

### Post by viswanathan on 2008-05-14
dude its really easy if u add Skype Repository or Medibuntu Repository to ur s/w sources and ```
sudo apt-get install skype 
```
would easily work 

well check this out dude this is one heck of document
that u cant miss  ```
https://help.ubuntu.com/community/Skype
```

and i added Medibuntu Repository coz it wold be really helpful if u want vlc or mplayer :lolflag:

---

### Post by viswanathan on 2008-05-14
> **hyper_ch said:**
> Use Medibuntu repos.. that way it will also get auto-updated.


dude thats really amazing feature :-)

---

### Post by Rowanmf on 2008-05-15
I have added all the medibuntu repos but i do get a error on one , i then go to adept manager to look for skype and w32 codec but they are not there , 
errors i get are :

rowan@rowan-laptop:~$ sudo apt-get update && sudo apt-get install medibuntu-keyr                                                                                                   ing && sudo apt-get update
Ign cdrom://Kubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy Release.g                                                                                                   pg
Ign cdrom://Kubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/main Tran                                                                                                   slation-en_ZW
Ign cdrom://Kubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/restricte                                                                                                   d Translation-en_ZW
Ign cdrom://Kubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy Release
Ign cdrom://Kubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/main Pack                                                                                                   ages
Ign cdrom://Kubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/restricte                                                                                                   d Packages
Err cdrom://Kubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/main Pack                                                                                                   ages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update can                                                                                                   not be used to add new CD-ROMs
Err cdrom://Kubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/restricte                                                                                                   d Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update can                                                                                                   not be used to add new CD-ROMs
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_ZW
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_ZW
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_ZW
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non Translation-en_ZW
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_ZW
Hit [http://zw.archive.ubuntu.com](http://zw.archive.ubuntu.com) hardy Release.gpg
Ign [http://zw.archive.ubuntu.com](http://zw.archive.ubuntu.com) hardy/main Translation-en_ZW
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_ZW
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_ZW
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_ZW
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release
Ign [http://zw.archive.ubuntu.com](http://zw.archive.ubuntu.com) hardy/restricted Translation-en_ZW
Ign [http://zw.archive.ubuntu.com](http://zw.archive.ubuntu.com) hardy/universe Translation-en_ZW
Ign [http://zw.archive.ubuntu.com](http://zw.archive.ubuntu.com) hardy/multiverse Translation-en_ZW
Hit [http://zw.archive.ubuntu.com](http://zw.archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://zw.archive.ubuntu.com](http://zw.archive.ubuntu.com) hardy-updates/main Translation-en_ZW
Ign [http://zw.archive.ubuntu.com](http://zw.archive.ubuntu.com) hardy-updates/restricted Translation-en_ZW
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages
Ign [http://zw.archive.ubuntu.com](http://zw.archive.ubuntu.com) hardy-updates/universe Translation-en_ZW
Ign [http://zw.archive.ubuntu.com](http://zw.archive.ubuntu.com) hardy-updates/multiverse Translation-en_ZW
Hit [http://zw.archive.ubuntu.com](http://zw.archive.ubuntu.com) hardy Release
Hit [http://zw.archive.ubuntu.com](http://zw.archive.ubuntu.com) hardy-updates Release
Hit [http://zw.archive.ubuntu.com](http://zw.archive.ubuntu.com) hardy/main Packages
Hit [http://zw.archive.ubuntu.com](http://zw.archive.ubuntu.com) hardy/restricted Packages
Hit [http://zw.archive.ubuntu.com](http://zw.archive.ubuntu.com) hardy/main Sources
Hit [http://zw.archive.ubuntu.com](http://zw.archive.ubuntu.com) hardy/restricted Sources
Hit [http://zw.archive.ubuntu.com](http://zw.archive.ubuntu.com) hardy/universe Packages
Hit [http://zw.archive.ubuntu.com](http://zw.archive.ubuntu.com) hardy/universe Sources
Hit [http://zw.archive.ubuntu.com](http://zw.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://zw.archive.ubuntu.com](http://zw.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources
Hit [http://zw.archive.ubuntu.com](http://zw.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://zw.archive.ubuntu.com](http://zw.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://zw.archive.ubuntu.com](http://zw.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://zw.archive.ubuntu.com](http://zw.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://zw.archive.ubuntu.com](http://zw.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://zw.archive.ubuntu.com](http://zw.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://zw.archive.ubuntu.com](http://zw.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://zw.archive.ubuntu.com](http://zw.archive.ubuntu.com) hardy-updates/multiverse Sources
W: Failed to fetch cdrom:[Kubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom:[Kubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch [http://packages.medibuntu.org/dists/hardy/Release](http://packages.medibuntu.org/dists/hardy/Release)  Unable to find expected entry  non/binary-i386/Packages in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
rowan@rowan-laptop:~$   

and then - 


rowan@rowan-laptop:~$ sudo apt-get install skype
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
rowan@rowan-laptop:~$


what have i done wrong ?? please help

---

### Post by hyper_ch on 2008-05-15
(1)you still have the cd drive in your sources list. Open Synaptic and disable it there in the options (also add universe, multiverse, partner repos... basically check all boxes except for the cd one)

(2) before running the medibuntu command with apt-get update aso... make sure you don't have synaptic, add/remove or adept open. Only one manager can run at a given time.

(3) the command you posted above is fault. It has a space in "[...]keyr ing[...]". Just copy'n'paste the one from the medibuntu repository howto :) No need to type if you can copy'n'paste

---

### Post by Rowanmf on 2008-05-15
thanks , i had added the cdrom repo just incase it might help , yah taken that off now , then closed the adept manager , then ran the command again , copy and paste caused the space btw ... error is now -

W: Failed to fetch [http://packages.medibuntu.org/dists/hardy/Release](http://packages.medibuntu.org/dists/hardy/Release)  Unable to find expected entry  non/binary-i386/Packages in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.

Please help -

---

### Post by plucky on 2008-05-15
> thanks , i had added the cdrom repo just incase it might help , yah taken that off now , then closed the adept manager , then ran the command again , copy and paste caused the space btw ... error is now -



Now that you have fixed the error,why not reinstall the Medibuntu repository
```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list

```

and the key

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

```


To see what happens.

---

### Post by Rowanmf on 2008-05-16
i have done that a couple of times now .. here is the report -

--08:47:52--  [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list)
           => `/etc/apt/sources.list.d/medibuntu.list'
Resolving [www.medibuntu.org](www.medibuntu.org)... 87.98.242.10
Connecting to [www.medibuntu.org|87.98.242.10|:80](www.medibuntu.org|87.98.242.10|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 226 [text/plain]

100%[==================================================================================================================>] 226           --.--K/s

08:48:10 (16.77 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [226/226]

then i run the next line , i wont post the whole report just the last few lines showing the error -

Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources
W: Failed to fetch [http://packages.medibuntu.org/dists/hardy/Release](http://packages.medibuntu.org/dists/hardy/Release)  Unable to find expected entry  non/binary-i386/Packages in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.


Thanks 

Rowan

---

### Post by plucky on 2008-05-16
I have deleted my Medibuntu repository sources list entry and tried to add it again.It failed to add the key after I reinstalled the sources list file using the entries in this [link](https://help.ubuntu.com/community/Medibuntu)


To add the key I used ```
 wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
``` which worked and I have Medibuntu repository back.

Instead of ```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
``` which is what is on the Ubuntu Medibuntu Community page.


Try that to see if it works for you.

Good Luck

---

### Post by Rowanmf on 2008-05-16
the answer is in the details - deleted -
Yup i should have thought of it <smacks head> 
yah i had removed my medibuntu repo's in adept , BUT i did not look in my home folder for the medibuntu list files , this time i deleted those , used your instructions - and ta daa - it worked ..

A million thanks .

Rowan

---

