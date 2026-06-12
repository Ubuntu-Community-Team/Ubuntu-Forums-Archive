---
title: "[SOLVED] Not sure how to compile this?"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by FOBoi1122 on 2008-06-05
Hi guys, i'm trying to get cpu scaling back, and here's the instructions:

"As far the ACPI battery wiki goes you have to do some cat >> . But i get a permisson denied all the time. However i found a fix for this. Download this script that patches the kernel, [WWW] [http://gaugusch.at/acpi-dsdt-initrd-patches/initrd-add-dsdt](http://gaugusch.at/acpi-dsdt-initrd-patches/initrd-add-dsdt), as well as the modified DSDT previously mentioned, if you haven't done so, i.e. [WWW] [http://ginkel2.boerde.de/Lifebook_4220/lt4220.tgz](http://ginkel2.boerde.de/Lifebook_4220/lt4220.tgz)

Run the script (after you have permission of both script and kernel, or you'll get "command not found"):

(where you saved "initrd-add-dsdt")/initrd-add-dsdt /boot/initrd.img-(version number)-acpi /(where you saved your file)/DSDT.aml "

but i'm not sure how to compile the files i got... initrd-add-dsdt and the modified DSDT lt4220. can someone give me some help on it?

---

### Post by Xiong Chiamiov on 2008-06-05
I don't know about the specifics of what you're talking about, but [here is how to install anything in Ubuntu]("http://monkeyblog.org/ubuntu/installing/").

---

### Post by FOBoi1122 on 2008-06-05
sorry, it wasn't very helpful since there's no configure file in the folder . the files are all .aml or .dsl formats? any help there?

---

### Post by Xiong Chiamiov on 2008-06-05
Those don't seem to be in the standard form for compiling.  It appears that shell script will do the work for you; have you tried running it?

---

### Post by FOBoi1122 on 2008-06-05
I'm not really sure how to open the files. but i got them from this site:
[https://help.ubuntu.com/community/T4220](https://help.ubuntu.com/community/T4220)

and on the very bottom of the page, it says "Putting your DSDT into initrd"

it told me to download a file and said this a little above that title:

 DSDT CPU Scaling

In response to the comment above about cpu scaling, a small how to. Download the file provided by the link [WWW] [http://ginkel2.boerde.de/Lifebook_4220/lt4220.tgz](http://ginkel2.boerde.de/Lifebook_4220/lt4220.tgz)

As far I can tell, you don't need iasl (intel compiler) The files provided are already enough

This wiki helped me: [WWW] [https://help.ubuntu.com/community/ACPIBattery](https://help.ubuntu.com/community/ACPIBattery) 

But i still dont really know how to compile that

---

### Post by RSingh on 2008-06-05
From what I see,

first you should save the "initrd-add-dsdt" file as a "initrd-add-dsdt.sh" file in your home folder and right click on the file >> properties >> permissions

make sure allow "executing as program" is ticked

extract the lt4220.tgz archive into a folder called "lt4220"

press alt+f2 and run "gksu nautilus" to run nautilus in super user mode so you can edit the "/boot" directory

Note: the "some number" in the command below depends on your system, check your /boot directory for the details.

browse to your /boot/initrd.img-(some number)

copy the "lt4220" folder here

run the "initrd-add-dsdt" script by 
```

sudo ./initrd-add-dsdt.sh /boot/initrd.img-(some number)/lt4220/DSDT.aml
```

Hopefully this should work

---

### Post by iaculallad on 2008-06-05
Try looking at this [page]("http://www.columbia.edu/~ariel/acpi/acpi_howto.txt"), it talks about ACPI and AML.

From the text:

> 
the definition of AML, an interpreted  language  for  describing  these various functions, and a description of how the OS calls these functions and in what context.

*I don't know how they compile this kind of format.

---

### Post by FOBoi1122 on 2008-06-05
Rsingh, I tried your method and I am currently stuck at trying to access a folder /boot/initrd.img-(some number), though the only folder i have after boot is /boot/Grub . I do have the the initrd-img file, however it's not a folder.

---

### Post by FOBoi1122 on 2008-06-05
bump? any takers?

---

### Post by RSingh on 2008-06-05
tell you what, even i while writing my last post, did have a feeling this issue might come up becuase your right, there is no such folder. Anyway,

Try this, create a folder with same name as the inird image file in the /boot directory and place the files in it and then try.

---

### Post by FOBoi1122 on 2008-06-06
hey, I figured out why it wasn't working. it wasn't a .sh file. So all i had to do was rename it without the ".sh" in the name, and when i compiled with the rest of the code, it worked. Thanks for your help

---

### Post by RSingh on 2008-06-06
oh sorry about that, should have noticed the code style. Anyway nice to know it worked out.

---

