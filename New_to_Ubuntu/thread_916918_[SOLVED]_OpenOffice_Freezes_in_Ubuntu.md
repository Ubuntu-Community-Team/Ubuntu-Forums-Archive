---
title: "[SOLVED] OpenOffice Freezes in Ubuntu"
date: 2008-09-11
forum: New to Ubuntu
---

### Post by linuxonyeije on 2008-09-11
Here's my problem as briefly as I can put it:

PROBLEM:
OpenOffice Freezes in Ubuntu in both original download and uploaded DEB format.

Background information:
[LIST=1]
[*]My Computer is a refurbished Dell Latitude D-600. 

[*]It was purchased used and I installed Ubuntu version 8.04 shortly after purchase. (I have included information regarding my hardware at the end of this post)

[*]	The computer was working and Ubuntu was functional, however, OpenOffice did not run.

[*]	When I opened OpenOffice it would show the logo screen and then it would freeze near the beginning of the  progress bar screen.

[*]	At this point I could not use the program and had to restart.

[*]	After doing some research online, I found the following solution online at: 
[*][http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68]("http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68")

[*]	The above solution requires removal of the Openoffice packages that came with Ubuntu 8.04 and reloading the DEB linux format.

[*]	After uploading the Debian version, OpenOffice still did not open properly. (It continued to freeze at startup).

[*]	I assume that there is a conflict with something else on my system but I cannot determine what it is.  

[*]	Any assistance would be greatly appreciated.

[*]Has anyone else had this problem?
[/LIST]

MY HARDWARE INFORMATION:
obtained by sudo lshw
          
    description: Portable Computer
    product: Latitude D600
    vendor: Dell Computer Corporation
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=portable uuid=44454C4C-0000-1000-8000-80C04F000000

---

### Post by SpenceMakesSense on 2008-09-11
try abiword 
```
sudo apt-get install abiword
```

---

### Post by linuxonyeije on 2008-09-11
> **SpenceMakesSense said:**
> try abiword 
```
sudo apt-get install abiword
```

Thanks for the timely response.

I am using abiword, and I LOVE it.  However, a great deal of what I will be doing with my laptop is Powerpoint presentations.  I use OpenOffice Impress now with my Windows laptop and it works great.

I tried KOffice's presentation program but it will not (or I cannot get it to) open *.ppt files.

thanks again.

linuxonyeije

---

### Post by SpenceMakesSense on 2008-09-11
i cant help much now because im at school but see if you can find the terminal command to boot it
(for instance to type firefox in the terminal and it would boot firefox.) because this way the terminal would say everything thats going on and it might be able to tell you if somethings wrong while booting.

---

### Post by linuxonyeije on 2008-09-11
> **SpenceMakesSense said:**
> i cant help much now because im at school but see if you can find the terminal command to boot it
(for instance to type firefox in the terminal and it would boot firefox.) because this way the terminal would say everything thats going on and it might be able to tell you if somethings wrong while booting.

Thanks for the tip. The error message I get indicates that:
 'openoffice is currently not installed.  You can install it by typing: sudo apt-get install openoffice.org-common

Looks like I've got some more homework.  I will get back after I give that a try.

Best wishes.

---

### Post by linuxonyeije on 2008-09-12
Life is Beautiful.

What worked was to go back into package manager (Synaptic) and delete all evidence of previous OpenOffice packages.  Then use the sudo apt-get command as described above.

OpenOffice now works perfectly and actually runs much faster than on my Windows Laptop.

A special word of thanks to SpenceMakesSense for his kind guidance.  

You have also been recognized in my latest [blog post]("http://linuxonyeije.wordpress.com/2008/09/12/my-openoffice-saga/"):

Kindest Regards !

---

