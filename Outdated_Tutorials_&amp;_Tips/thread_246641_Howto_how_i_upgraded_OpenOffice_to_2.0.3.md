---
title: "Howto how i upgraded OpenOffice to 2.0.3"
date: 2006-08-29
forum: Outdated Tutorials &amp; Tips
---

### Post by robert114 on 2006-08-29
I've found an article on the net

You can read it below

```

More than a month ago OpenOffice 2.0.3 was released, with a bunch of notable improvements. Dapper Drake, the latest release from the Ubuntu Linux distro still contains version 2.0.2. Since it contains new features it will probably have to wait for the next release to be included. Updated packages can be added to a distribution through the updates repositories, but only if they address bugfixes only.

A bug in the outline numbering was giving me headaches so I looked around for an update. Ubuntu set up a special repository called dapper-proposed that contains the new version. All packages in this repository seem to be OpenOffice related. If you prefer the vi /etc/apt-sources.list; apt-get update; apt-get install routine I don’t have to explain anything to you. For all the rest here’s a step by step guide on how to install it.

    * Go to the System menu and launch adept (packetmanager), enter your password
    * From the View menu choose Manage repositories

There should be a line somewhere at the top that looks like this :
deb http://be.archive.ubuntu.com/ubuntu/ dapper main restricted

It might look a bit different, especially the country code (be) might be different or absent. Make sure it contains ‘dapper’ and ‘main’.

    * Right click on it, choose ‘Clone’
    * On the newly created line, double click on ‘dapper’ and change it to ‘dapper-proposed’
    * At the bottom on the screen click on ‘Apply’
    * At the top click on ‘Fetch updates’
    * You return to the main Adept screen, type ‘openoffice’ in the search field
    * If all went right you should now see the package ‘OpenOffice.org’ in the list, with ‘upgradable’ next to it
    * Hit the little blue arrow next to it
    * Click on the ‘Request update’ button
    * Hit ‘Apply changes’ at the top of the screen

That’s all it takes! OOo 2.0.3 ready to serve you. 

```

thanx to arnebrasseur.net 
BTW, i used the belgian repo: (deb [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) dapper dapper-proposed main restricted)
The dutch Repo didn't contain the 2.0.2>2.03 upgrade!

I hope you'll enjoy it!
[COLOR="Red"][SIZE="4"]
Since there are some problems with the repositories you could/proberbly will break your system by using this how to... i'll update this message as soon as I notice it will work again![/SIZE][/COLOR]

---

### Post by Athanasius on 2006-08-29
I went to ect/apt/sources.list and inserted:
> deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-proposed main
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-proposed main
then sudo apt-get update
then sudo apt-get upgrade

---

### Post by Athanasius on 2006-09-04
This worked on one computer but broke something on my other one.  Use with caution

---

### Post by asplode on 2006-09-04
This breaks stuff for me.

This is what synaptic says:

E: /var/cache/apt/archives/openoffice.org-draw_2.0.3-6dapper1_i386.deb: trying to overwrite `/usr/lib/openoffice/share/registry/modules/org/openoffice/TypeDetection/Filter/fcfg_drawgraphics_filters.xcu', which is also in package openoffice.org-common
E: /var/cache/apt/archives/openoffice.org-impress_2.0.3-6dapper1_i386.deb: trying to overwrite `/usr/lib/openoffice/share/registry/modules/org/openoffice/TypeDetection/Filter/fcfg_impressgraphics_filters.xcu', which is also in package openoffice.org-common

---

### Post by RRS on 2006-09-04
> **asplode said:**
> This breaks stuff for me.

This is what synaptic says:

E: /var/cache/apt/archives/openoffice.org-draw_2.0.3-6dapper1_i386.deb: trying to overwrite `/usr/lib/openoffice/share/registry/modules/org/openoffice/TypeDetection/Filter/fcfg_drawgraphics_filters.xcu', which is also in package openoffice.org-common
E: /var/cache/apt/archives/openoffice.org-impress_2.0.3-6dapper1_i386.deb: trying to overwrite `/usr/lib/openoffice/share/registry/modules/org/openoffice/TypeDetection/Filter/fcfg_impressgraphics_filters.xcu', which is also in package openoffice.org-common

Same here. Tried different ways to repair the broken packages following prompts from Synaptic Package Manager and also; ```
sudo apt-get install -f
```
All with same end results.

Went back to the package manager and removed Open Office. Marked the new versions and reinstalled from package manager with no errors.

Probably not the cleanest method but since I don't really know why the overwrite errors occurred it's all I could think of @ the moment.

---

### Post by asplode on 2006-09-04
> **RRS said:**
> Same here. Tried different ways to repair the broken packages following prompts from Synaptic Package Manager and also; ```
sudo apt-get install -f
```
All with same end results.

Went back to the package manager and removed Open Office. Marked the new versions and reinstalled from package manager with no errors.

Probably not the cleanest method but since I don't really know why the overwrite errors occurred it's all I could think of @ the moment.

I removed the additional repo's, reloaded, in synaptic clicked Edit->Fix Broken Packages.

This removed the ubuntu-desktop metapackage, along with openoffice and something python related.

A quick reinstall of the ubuntu-desktop packaged returned it all back to normal.  Normal also being that annoying list/bullet bug in OO that was referred to by the OP

---

### Post by robert114 on 2006-09-05
That solved my problem as well just remove the dapper-proposed and remove openoffice... than update synaptic and reinstall openOffice...

To bad it breaks your system. I don't know why because it did work for me :-k

---

### Post by Athanasius on 2006-09-05
It worked once for me but not anymore.. maybe it's something with the repository itself

---

### Post by stalefries on 2006-09-05
I just tried this, and the error messages make me believe that his repo is gone. Bummer.

Also, can anyone link to the changes from 2.0.2 -> 2.0.3?

Edit: Looke here: [http://development.openoffice.org/releases/2.0.3.html](http://development.openoffice.org/releases/2.0.3.html)

It's complicated, but it's got good info. Check there if you've found bugs in Openoffice recently, it lists a whole bunch of stuff that was fixed.

---

### Post by eriksmith200 on 2006-09-08
> **asplode said:**
> I removed the additional repo's, reloaded, in synaptic clicked Edit->Fix Broken Packages.

This removed the ubuntu-desktop metapackage, along with openoffice and something python related.

A quick reinstall of the ubuntu-desktop packaged returned it all back to normal.  Normal also being that annoying list/bullet bug in OO that was referred to by the OP

i have the same problem and need to do the same fix, i have a n00b question: after removing openoffice + (k)ubuntu-desktop do i need to do a reinstall of the desktop from the command line or can i reinstall using synaptic without doing a reboot?

---

### Post by garybrlow on 2006-09-08
Using the dapper-proposed repository breaks openoffice. OOO 2.0.3 has dependency issues(office and GTK modules). This might be a backport in progress hence the propsed status but still has issues to resolve. Either wait for the backport or wait for Edgy.

---

### Post by SpEcIeS on 2006-09-21
If anyone is interested, you could just download the RPM tarball from OpenOffice.org and use alien to convert it. Remove the old OOo and install the new. I am currently using OOo 2.0.4 rc2 and it works well.:D 

For latest snapshots go here: **[http://download.openoffice.org/680/index.html](http://download.openoffice.org/680/index.html)**

Or download OOo 2.0.3 here: **[http://download.openoffice.org/2.0.3/contribute.html?product=OpenOffice.org&os=linuxintel&lang=en&version=2.0.3](http://download.openoffice.org/2.0.3/contribute.html?product=OpenOffice.org&os=linuxintel&lang=en&version=2.0.3)**

Unpack the tarball, enter the directory which contains the RPM's, and use **alien -k *.rpm** to convert the RPM's to DEB's. *(You must have alien installed "_sudo apt-get install alien_")*

Once the convertion is completed remove any packages that you do not want, such as *openoffice.org-kde-integration_2.0.4-4_i386.deb*, by renameing the extention *(eg . openoffice.org-kde-integration_2.0.4-4_i386.deb.no)*.

Next use **sudo dpkg -i *.deb** to install.

There you have it. :)

---

### Post by robert114 on 2006-09-21
SpEcIeS can you tell me what the improvements are of the 2.0.4 version
and did you're menu's work well?

---

### Post by SpEcIeS on 2006-09-21
Not sure about the improvements, but I am sure that they are listed at the OOo site. As far as the menus are concerned, everything works great. :cool:

---

### Post by yopnono on 2006-09-21
OO from 203 also have it's own update manager.

---

### Post by McDuff on 2006-09-22
i have done this various times now on different machines without any problem:

first remove current ooo packages, as they conflict with ooo203:
```
$ sudo apt-get remove openoffice.org*
```
this will also remove the meta-package ubuntu-desktop, but that doesn't do harm to the system.

then add the proposed repository to your sources.list
```
$ sudo gedit /etc/apt/sources.list
```

```
deb http://archive.ubuntu.com/ubuntu/ dapper-proposed main restricted universe multiverse
deb-src http://at.archive.ubuntu.com/ubuntu/ dapper-proposed main restricted universe multiverse
```
save the file
update apt
```
$ sudo apt-get update
```

re-install ubuntu-desktop, this will also install ooo203
```
$ sudo apt-get install ubuntu-desktop
```

re-install language-files in system -> settings -> language-settings

that's it

---

