---
title: "[SOLVED] terminal command for system hardware"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by linux.convert on 2008-08-09
this is a really stupid, yet needed question, there is a terminal command to display all the hardware. I've used it before, but I havent had Ubuntu for awhile so i forgot.

furthermore, need to set up graphics/drivers, again.

---

### Post by UltraMathMan on 2008-08-09
I think you might be looking for ```
lspci -v
```

-Hope this helps :)

---

### Post by hansdown on 2008-08-09
Hi linux. convert. Try this. Hope it helps.  [http://www.tech-recipes.com/rx/2771/ubuntu_generate_hardware_profile_system](http://www.tech-recipes.com/rx/2771/ubuntu_generate_hardware_profile_system)

---

### Post by prshah on 2008-08-09
> **linux.convert said:**
> there is a terminal command to display all the hardware. 

furthermore, need to set up graphics/drivers, again.

As suggested; lspci will work; you can also try it with "-v" for more information, and you can also use ```
lshw
``` (lIsT hARDwARE)

running a "man"(ual) on either command will give tons more information```
man lspci
man lshw
```

lspci is more compact (reports whatever info the devices give), but lshw is more comprehensive (reports what the OS makes of the hardware).

---

### Post by Blue_Lander on 2008-08-09
> **linux.convert said:**
> furthermore, need to set up graphics/drivers, again.

You can usually go to System>Administration>Hardware Drivers and enable the proprietary drivers for your card and it will download and install them automatically. This will require a restart to complete.

---

### Post by Vivaldi Gloria on 2008-08-09
There are a number of (terminal) commands that give general info about your hardware:

```
lshw
hwinfo
dmidecode
```

If any of these are not installed then search & install them using synaptic.

Preferably use these (and the ones at the end of this post) with sudo:

```
sudo lshw
```

etc. (Sudo gives administrative rights.)

These spit out so much info that it may be better to save the output into a text file:

```
sudo lshw > info1.txt
sudo hwinfo  > info2.txt
sudo dmidecode  > info3.txt
```

Start by using the short versions

```
sudo lshw -short
sudo hwinfo --short
```

They have flags to restrict the output to certain hardware. For example

```
sudo lshw -class system
```

gives a basic info and motherboard. To learn more about these flags see their man pages:

```
man lshw
```

etc.

Some other commands:

```
lspci (Lists PCI devices including Audio, VGA, Ethernet etc.)
aplay -l (sound info)
uname -a (kernel info)
lsusb (list USB devices)
ls /dev/disk/* -lah (disk info)
fdisk -l (disk info)
df -h (disk usage info)
free -m (memory info)
cat /proc/swaps (swap file/partition info)

```

and the list goes on and on.

---

### Post by linux.convert on 2008-08-09
many thanks guys, got my stuff working again.

---

### Post by kuckunniwi on 2011-01-17
Just for the record, for whoever else may stumble upon this post looking for info, add *-sanitize* to any of the aforementioned commands to remove potencially sensitive information from the output file.

Example:

```
 sudo lshw -sanitize 
```

To create a text file with the output of lshw, use:

 ```
 sudo lshw > hardwareprofile.txt  
```

It will create a file in your home folder called hardwareprofile.txt (you can change the filename to whatever you want).

To create an html file (in your home folder) with the output from lshw, use:

```
 sudo lshw -html > hardwareprofile.html 
```

You can also remove sensitive info from these file adding the *-sanitize* command, e.g.:

```


sudo lshw -sanitize > hardwareprofile_sanitized.txt 

sudo lshw -sanitize -html > hardwareprofile_sanitized.html


```



Also,

---

### Post by kuckunniwi on 2011-01-17
Just for the record, for whoever else may stumble upon this post looking for info, add *-sanitize* to any of the aforementioned commands to remove potencially sensitive information from the output file (such as serial numbers, etc.)

Example:

```
 sudo lshw -sanitize 
```

To create a text file with the output of lshw, use:

 ```
 sudo lshw > hardwareprofile.txt  
```

It will create a file in your home folder called *hardwareprofile.txt* (you can change the filename to whatever you want).

To create an html file (in your home folder) with the output from lshw, use:

```
 sudo lshw -html > hardwareprofile.html 
```

You can also remove sensitive info from these files adding the *-sanitize* command, e.g.:

```


sudo lshw -sanitize > hardwareprofile_sanitized.txt 

sudo lshw -sanitize -html > hardwareprofile_sanitized.html


```


Happy info-gathering!

---

