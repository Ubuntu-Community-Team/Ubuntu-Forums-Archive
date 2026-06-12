---
title: "Video Driver?"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by Codemastadink on 2008-05-23
So i just put ubuntu on my computer yesterday, and it didnt find a driver so it just used a generic one, not the screen resolution is off and everything is very big and i can not change it. how would i go and get the right driver for my video card?

---

### Post by FuturePilot on 2008-05-23
What graphics card do you have? And what driver did you install?

---

### Post by Codemastadink on 2008-05-23
> **FuturePilot said:**
> What graphics card do you have? And what driver did you install?

I dont know what card it is, i can find ot when i get home. Im at schol right not. I did not install a driver, i just selected to use a general driver when i installed ubuntu

---

### Post by Codemastadink on 2008-05-23
Well, i talked to a friend at school who knows a lot about Linux and ubuntu and he said to go to go into System-Administration-Hardware Drivers and that it would scan my system and install drivers that i need. So i tried this and when it got to that page it said "No proprietary drivers are in use on this system" Can anyone help from here? that would be awesome if you can. 

Thanks

---

### Post by subzero316 on 2008-05-23
Can you post the output of
```
lspci
```
it will list your graphics card

---

### Post by Codemastadink on 2008-05-23
> **subzero316 said:**
> Can you post the output of
```
lspci
```
it will list your graphics card

heres what it said

01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 86C326 5598/6326 (rev0b)

If u know what that means thats great cuz i dont


Edit: i downloaded what i believe to be the correct driver  and extracted it, but its just on the desktop and i dont know what folder to put it in.

Thanks for the help.

---

### Post by subzero316 on 2008-05-23
> 


Edit: i downloaded what i believe to be the correct driver  and extracted it, but its just on the desktop and i dont know what folder to put it in.

Thanks for the help.


well , if you downloaded the right one hoping its  SIS driver as we found out...you must have a readme file..else can u just paste the names of the files..listin it in command line using command```
ls
``` will be better

---

### Post by Codemastadink on 2008-05-23
> **subzero316 said:**
> well , if you downloaded the right one hoping its  SIS driver as we found out...you must have a readme file..else can u just paste the names of the files..listin it in command line using command```
ls
``` will be better




So, i go into the terminal and type in "1s" and then the file name? i did that and it said the "1s" command was not found. just to be sure it is "1" like the number "one" and then "s" correct?

---

### Post by Maestro23 on 2008-05-23
Goto your Desktop directory.

cd Desktop

Change directory to the extracted folder of the driver.

cd ....

then

ls (list contents of current directory)

---

### Post by Codemastadink on 2008-05-23
> **Maestro23 said:**
> Goto your Desktop directory.

cd Desktop

Change directory to the extracted folder of the driver.

cd ....

then

ls (list contents of current directory)

Hey.. so you think you could break that down into more simple terms, i understand most of it, but i dont understand what to do step by step so much. sorry for the trouble, new to Ubuntu

---

### Post by subzero316 on 2008-05-23
oh okay. all i wanted to know were the contents of the archive..so jus paste the contents.

---

### Post by Codemastadink on 2008-05-23
> **subzero316 said:**
> oh okay. all i wanted to know were the contents of the archive..so jus paste the contents.


I believe the contents are "XSiS_SVGA" that is waht was extracted, and when i open the file that i downloaded that is the only file in there to be extracted.

---

### Post by Codemastadink on 2008-05-24
bump

---

### Post by Codemastadink on 2008-05-25
Come on, somebody please hlep

---

### Post by Pedro52 on 2008-06-05
> **Codemastadink said:**
> Come on, somebody please hlep

Hia,

I found this thread that might help.
[http://ubuntuforums.org/showthread.php?t=686643](http://ubuntuforums.org/showthread.php?t=686643)

Sorry if it doesn't, I'm a bit new to all this myself :)

---

