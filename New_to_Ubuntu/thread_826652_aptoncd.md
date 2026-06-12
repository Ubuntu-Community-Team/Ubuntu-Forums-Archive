---
title: "aptoncd"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by fazillatheef on 2008-06-12
hi
I heard abt this software called aptoncd.... I want to create a installation disk using the packages in my system for my friend ..
Can he install from the cd without having the aptoncd package installed on his system ... he has done a fresh install of hardy..

also does it work like normal disks from ubuntu... what i meant by that is ,will the autorun work and ask the user to add it to repository...

this is because my friend is new to linux... 

Otherwise i will have to find a method to put a readme in that cd to help him manually add it to the software sources

---

### Post by komputes on 2008-06-12
I'm not sure if you pop in a CD and it shows as an add-on CD once you pop it in or if you need to add it to your sources.list or if you need to use aptoncd on your friends computer.

I did find an interesting blog post on the subject:
[http://linuxhelp.blogspot.com/2006/11/aptoncd-create-backup-of-all-packages.html](http://linuxhelp.blogspot.com/2006/11/aptoncd-create-backup-of-all-packages.html)

Please let me know how this works out for you, I will be trying this as well.

---

### Post by Lorry ZA on 2008-06-12
I tried that this morning, i ran aptoncd on my home PC lastnight and loaded it on a clean install on one of my office PC's this morning, All you do is add the cd/dvd as a repository in the aptoncd restore section.

Then use the Synaptic Package Manager and select repositories through the settings tab and make sure the installable from cd/dvd rom has the backup cd there and it is checked

Close and click on reload in the Synaptic Package Manager and select packages to install.

This worked for me not sure if it was luck or if it is the right way, let me know if it works for your mate.

Cheers,

Lorry

---

### Post by rraj.be on 2008-06-12
there is no need for any such configuration's.

When you create a  cd with apt-on-cd it will automatiocally configure every thi8ng in its data base stored in cd.

When you insert your disk it will pop up a widow like

```
a software package dc was found and did you want to start it with package manager.
```

If you clikck yes it will automatically open yur package manager.

---

### Post by bodhi.zazen on 2008-06-12
First, make the list. Open a terminal and enter these commands:

    ```
dpkg --get-selections | grep -v deinstall > ubuntu-files
```

Now you have got a list of all of your installed debs in a fairly small file. Transfer "ubuntu-files" to the insstallation you want to update (flash drive, email it to yourself, backup partition, etc).

Install Ubuntu on the new system.

Once Ubuntu is up and running, copy your ubuntu-files back into your home directory and do the following:

    sudo apt-get update

    sudo apt-get dist-upgrade

    dpkg --set-selections < ubuntu-files

These commands tell the fresh install of Ubuntu what it needs to be installed. To install the packages .

```
sudo dselect
```

This will open up a dselect session. Type "I" and allow dselect to install of the the packages listed in your ubuntu-files document. When finished, type "Q" and hit the ENTER key to exit dselect.

Alternate : [http://ubuntuforums.org/showthread.php?t=650518](http://ubuntuforums.org/showthread.php?t=650518)

# Create a text list of an existing installation of all apt-get installed packages
# in order to re-install on a newly installed distro

# make the list
[old distro] sudo dpkg --get-selections >packages

# Now put them back on the new distro
[new distro] sudo dpkg --set-selections <packages

[new distro] sudo apt-get dselect-upgrade

# that's it!

---

