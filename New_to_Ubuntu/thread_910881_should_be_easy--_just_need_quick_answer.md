---
title: "should be easy-- just need quick answer"
date: 2008-09-05
forum: New to Ubuntu
---

### Post by hyperhopper on 2008-09-05
I am trying to install unetbooting here [http://unetbootin.sourceforge.net/]("http://unetbootin.sourceforge.net/")

and how do I use the executable to run it---it wants me to select a program to run it with...

---

### Post by hyperhopper on 2008-09-05
its says 

"there is no application installed for this file"

---

### Post by Locutus_of_Borg on 2008-09-05
assuming you have already downloaded the source from sourceforge

enter the directory that contains the source code
type:
```
./configure && make && sudo make install
```
to install it, after that, it should be listed under your menu, or it can run by typing the name into the terminal, as long as it was installed into the usual path...

---

### Post by hyperhopper on 2008-09-05
how do you learn AND/OR remember these things????

---

### Post by hyperhopper on 2008-09-05
says no such file or directory

---

### Post by ad_267 on 2008-09-05
That file is a binary executable, it's not the source code (assuming you just clicked on Download for Linux). To run it you need to change its permissions so you can execute it as a program. Right click on it and select properties then Permissions then tick next to "Allow executing as a program" or something like that. Then you can just double click to run it.

Alternatively, you can run this in the same directory as the file:
```
chmod +x unetbootin-linux-274
./unetbootin-linux-274
```

---

### Post by Locutus_of_Borg on 2008-09-05
i learn and remember by having done them a lot

no directory to what?

you clicked the download button already i hope
after the download finished, if it is a compressed file (tar.gz etc) extract it to wherever you want, open a terminal and go to the directory that was created when you extracted, then type those commands to install

---

### Post by hyperhopper on 2008-09-05
> **Locutus_of_Borg said:**
> i learn and remember by having done them a lot

no directory to what?

you clicked the download button already i hope
after the download finished, if it is a compressed file (tar.gz etc) extract it to wherever you want, open a terminal and go to the directory that was created when you extracted, then type those commands to install
I did hit the button for linux, and will try changing permissions, but I have no clue what locust is talking about...

---

### Post by Crafty Kisses on 2008-09-05
You have to have build-essentials when building files. Make sure you have that.

---

### Post by Elfy on 2008-09-05
It doesn't need to be built it needs to be run as ad_267 has said.

---

### Post by hyperhopper on 2008-09-05
it returns this error message

```
7z not found. This is required for either install mode.
Install the "p7zip-full" package or your distribution's equivalent.
```

---

### Post by ad_267 on 2008-09-05
You can install p7zip-full by going to System - Administration - Synaptic Package Manager and searching for it, marking it for installation and clicking apply. Or you can run:

```
sudo apt-get install p7zip-full
```

---

### Post by hyperhopper on 2008-09-05
now I have to find the iso, which is on the usb, but when I try to copy it to the hard drive-it says not enough memory even though I should have plenty...

---

### Post by nothingspecial on 2008-09-05
Not enough memory on the usb stick?

---

### Post by hyperhopper on 2008-09-05
not enough on the computer to copy it from the usb to computer

my usb is 2 GB

---

### Post by Elfy on 2008-09-05
You have 675Mb left on your ubuntu installation, see your other thread :)

You can resize the virtual disk which wubi is using

[https://wiki.ubuntu.com/WubiGuide#How](https://wiki.ubuntu.com/WubiGuide#How) do I resize the virtual disks?

---

### Post by nothingspecial on 2008-09-05
Why are you copying it to the computer? To use unetbootin you need to select boot from usb in your bios.


(I know what you`re trying to do:wink: ssh, I wont tell them. You`d better be quick, remember they are in charge. Don`t let them find out!!!!!!!!)

---

### Post by hyperhopper on 2008-09-05
i need to copy the iso to my comp to use unetbootin to configure my usb so from there I can boot on the school comps when I get there in life 3 hours---lol---I REALLY should be sleeping for the first day back to school...

---

### Post by nothingspecial on 2008-09-05
Is unetbootin installed on your usb thing. Have you tried booting from it?

---

### Post by hyperhopper on 2008-09-05
on usb is  ubuntu live cd iso file


on computer is  unetbootin executable

---

### Post by nothingspecial on 2008-09-05
Can you copy the iso to a cd or dvd?

---

### Post by hyperhopper on 2008-09-05
I already have a live cd, I need a live usb-- I cannot fit a cd into my pocket...

---

### Post by nothingspecial on 2008-09-05
I mean instead of copying it onto your computer, or copy the unetbootin file onto the usb

---

### Post by Fevrin on 2008-09-19
> **ad_267 said:**
> That file is a binary executable, it's not the source code (assuming you just clicked on Download for Linux). To run it you need to change its permissions so you can execute it as a program. Right click on it and select properties then Permissions then tick next to "Allow executing as a program" or something like that. Then you can just double click to run it.

Alternatively, you can run this in the same directory as the file:
```
chmod +x unetbootin-linux-274
./unetbootin-linux-274
```

I already tried doing this, but I get an error: "bash: ./unetbootin-linux-281: Permission denied".  Using sudo doesn't help, either: "sudo: unable to execute ./unetbootin-linux-281: Permission denied".  And of course, using both sudo and bash produces yet another error: "./unetbootin-linux-281: ./unetbootin-linux-281: cannot execute binary file".  What am I doing wrong?  And yes, I gave the file executable permissions.

---

### Post by dirtylobster on 2009-04-10
This is so weird. I suddenly have the same "Permission denied" problem, after using unetbootin (v319) a bunch of times.

---

### Post by CodeNosher on 2009-04-20
Same problem.  Anyone get around it?

---

