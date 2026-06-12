---
title: "Dependency not Satisfiable"
date: 2013-03-13
forum: New to Ubuntu
---

### Post by Ediaan on 2013-03-13
I'm a complete newbie to Linux, and unfortunately, my internet at home has not been set up so I have been downloading applications manually and trying to install them on my system.

I have tried the sudo apt-get install and sudo apt-get update etc. in Terminal as well as opening the downloaded packages with Ubuntu Application Center but I keep on getting the error Dependency not Satisfiable <package name>.

What could I be doing wrong? I've managed to open another application ( also downloaded manually ) with the App Center and it says " Only install application if you trust it's source" ( or something along that line), displays the install button, but I'm unable to click on it.

Please help?

---

### Post by mellocode on 2013-03-13
What package specifically and what error specifically?

---

### Post by Ediaan on 2013-03-13
freecad_0.12.5284-dfsg-7ubuntu1_i386.deb, cannot remember what the error said, will have to check this afternoon when I get home.

I've downloaded all the additional libraries and packages seperately as well.

---

### Post by stinkeye on 2013-03-13
Place your freecad and dependencies debs into a folder in your home directory 
named **freecad_debs** [COLOR="#A9A9A9"](or whatever you care to name it)[/COLOR]
Open a terminal and change directory to ~/freecad_debs...
```
cd freecad_debs
```

Copy the .debs to /var/cache/apt/archives....
```
sudo cp *.deb /var/cache/apt/archives
```

Install freecad...
```
sudo apt-get install freecad
```

When you install a package the deb files are saved to /var/cache/apt/archives
and remain there even after uninstalling.
So when running **sudo apt-get install freecad** it will look there for
a freecad deb and dependencies.

If you had all the dependencies needed for freecad, not already installed on you computer,
in the ~/freecad_debs folder then it should install.

You can use synaptic for offline installs but synaptic is no longer included in a default install.
[**_[COLOR="#B22222"]Synaptic/PackageDownloadScript[/COLOR]_**]("https://help.ubuntu.com/community/Synaptic/PackageDownloadScript")

---

### Post by Ediaan on 2013-03-13
Thanks Stinkeye, will definitely try that, I take it that I'd need to use the same process for the installation of the other applications as well?

---

### Post by snowpine on 2013-03-13
The problem you may run into is that your dependencies might have dependencies of their own, and the dependencies' dependencies might have dependencies, and so forth.

Here is some information about "how to install packages on Ubuntu without an internet connection" that you might find helpful: [https://help.ubuntu.com/community/InstallingSoftware#Installing_packages_without_an_Internet_connection](https://help.ubuntu.com/community/InstallingSoftware#Installing_packages_without_an_Internet_connection)

---

### Post by Ediaan on 2013-03-13
Thanks snowpine, I suppose that's what is meant by Dependency not satisfiable: (dependency name).

---

### Post by stinkeye on 2013-03-13
> **Ediaan said:**
> Thanks Stinkeye, will definitely try that, I take it that I'd need to use the same process for the installation of the other applications as well?
Yep.
If you can install synaptic it makes it easier to get all dependencies.
eg 
If I wanted to install stardict I can use synaptic to create a download script 
which can be run on another linux machine
or 
copy the [COLOR="#FF0000"]links[/COLOR] in the script to download through the browser on a windows machine.

example script created by synaptic for stardict and dependencies....
```
#!/bin/sh
wget -c [COLOR="#FF0000"]http://au.archive.ubuntu.com/ubuntu/pool/universe/s/speech-tools/libestools2.1_2.1~release-5_amd64.deb[/COLOR]
wget -c http://au.archive.ubuntu.com/ubuntu/pool/universe/s/stardict/stardict-common_3.0.1-9.1_all.deb
wget -c http://au.archive.ubuntu.com/ubuntu/pool/universe/s/stardict/stardict-gnome_3.0.1-9.1_amd64.deb
wget -c http://au.archive.ubuntu.com/ubuntu/pool/universe/s/stardict/stardict_3.0.1-9.1_all.deb
wget -c http://au.archive.ubuntu.com/ubuntu/pool/universe/s/stardict/stardict-plugin_3.0.1-9.1_amd64.deb
wget -c http://au.archive.ubuntu.com/ubuntu/pool/universe/s/stardict/stardict-plugin-espeak_3.0.1-9.1_amd64.deb
wget -c http://au.archive.ubuntu.com/ubuntu/pool/universe/s/stardict/stardict-plugin-festival_3.0.1-9.1_amd64.deb
```

---

### Post by Ediaan on 2013-03-13
Makes sense, I've just downloaded synaptic, will install it and then try "the easier method". It's going to take a while for me to get used to terminal and its commands.

Thanks stinkeye, will definitely try it!

---

