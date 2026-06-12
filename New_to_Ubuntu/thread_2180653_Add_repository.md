---
title: "Add repository??"
date: 2013-10-14
forum: New to Ubuntu
---

### Post by goblynn932 on 2013-10-14
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

This page has links to repositories that I think I need to add to my system but I have no idea how to do this... maybe I am just really stupid and its incredibly easy and obvious but I am at a total loss... I know how to add a repository in general but the links listed on the help page don't have any of the information I am used to for easy adding...

its really frustrating when the page says "available under these repositories" and has ZERO information (nor any link to any information) on how to use this!!

Thanks!

---

### Post by mastablasta on 2013-10-14
What links are you talking about ? The ones that connect to launchpad? There are instructions on how to add thes repositories at launchpad link.

---

### Post by moteprime on 2013-10-14
Do you want to install the Proprietary ATI drivers? There's an easier way.

---

### Post by goblynn932 on 2013-10-14
Well, yes... I would like to install the drivers...

An easier way??

The links are the links under #2 "Installation Via The Repositories". I don't see any explanation on the pages that they link to on how to add them...

---

### Post by moteprime on 2013-10-14
I think that the repoe driver mentioned are the one from, "additional hardware drivers". They are not the latest, but have somewhat been tested.
I'm on Intel graphics now, (had it with ATI), but i used to got to ATI supp[http://support.amd.com/en-us/download]("http://support.amd.com/en-us/download") and download the driver. Unzip it, and run it from command line "sudo ./amd-driver-installer-catalyst-13-4-x86.x86_64.run(Whatever)". punch the Tab key to auto complete the long command. It usually just installs fine. Enable tearfree in the ATI/AMD control center after installation.
Mind! If you want to uninstall the driver you must use the uninstall feature described in the readme, otherwise you system might get screwed up.
Once in a while you the just visit the support page to se if theres and update for the driver. Usually 2-3 months apart.

---

### Post by goblynn932 on 2013-10-14
I am on a laptop and ATI tries to send me to the HP website... The easiest way for me in the past has been through the repositories but I still don't get how to add these from these links...

---

### Post by goblynn932 on 2013-10-14
How do i add this to my Ubuntu??

[https://launchpad.net/ubuntu/+source/fglrx-installer](https://launchpad.net/ubuntu/+source/fglrx-installer)

The LaunchPad directions seem to all be directed at those who want to host their files, not those who want to connect and download/use them!!

LaunchPad says "*Adding this PPA to your system*[COLOR=#4E4D4D][FONT=UbuntuBeta]." and I don't see this information any where.

None of this makes any sense, I am totally lost.[/FONT][/COLOR]

---

### Post by moteprime on 2013-10-14
It does not appear to have a ppa. I would be nice if ATI would supply a PPA based driver, but to my experience ATI sucks when it comes to support linux.
What grapihcs chip do you have in your laptop?

---

### Post by mastablasta on 2013-10-14
mostly info on packages in default repositories i believe:
This projects is for marking bugs that have been communicated to AMD for their fglrx video driver

what GPU are you using? if it's supported it will offer to install drivers automaticly. otherwise you can go to additional drivers in software sources i believe.

---

