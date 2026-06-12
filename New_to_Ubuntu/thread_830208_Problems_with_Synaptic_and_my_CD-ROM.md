---
title: "Problems with Synaptic and my CD-ROM"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by pablote on 2008-06-15
Hello! I'm having some troubles installing packages from synaptic, and I could REALLY use some help. 
The thing is that i have to configure my usb modem (linksys WUSB54G v4) to have access to the internet, and a i read in the ubuntu documentation that i needed to install ndiswrapper. In order to do this i have to install build-essentials among other things, so i put my installation cd while in synaptic (as i dont have an internet connection) and i tried to install all the needed packages from there. The problem is that, after i choose the packages i want, and i click "apply", a message pops up asking me to mount the "Ubuntu 8.04 Hardy_Heron CDROM"... but the cd is already in!!!! i tried to burn another copy of the cd (although ubuntu *can read* the cd -i mean i can access the files) but still no luck. I really don't know what to do and it's driving me crazy, because i cant install any new software on my brand new ubuntu =(.

Well, thanks in advance for your help! and forgive my english, one more time =P

Pablo

---

### Post by RSingh on 2008-06-15
I'm not quite sure, I may be wrong but I think the CD doesn't have the build-essential packages. It should be available on the DvD version.

---

### Post by pablote on 2008-06-15
Thanks for the reply! No, the build-essential packaged are indeed on the CD. Synaptic lets me go through all the avaible packages but when it comes to installation i get the error message. Any other ideas?

---

### Post by forestpixie on 2008-06-15
Post your sources list please

```
cat /etc/apt/sources.list
```


Edit - sorry if you don't know how - open a terminal from accessories and paste the command in  then enter - paste the output you get here

---

### Post by pablote on 2008-06-15
here it is:

deb cdrom: [Ubuntu 6.06 _Drapper Drake_ - Release i386 (20060531)]/ dapper main restricted
deb cdrom: [Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted

The first one appears because I tried to use a CD from an earlier ubuntu version (6.06). I couldnt find the packages i needed there but i did install a few games succesfully. I should remark that the Drapper Drake cd is original and the HArdy Heron cd is a burned image of the .iso i downloaded from the ubuntu website.

---

### Post by drs305 on 2008-06-15
Go to synaptic, settings, repositories, and uncheck the dapper cd in the lower window.

If that doesn't work and you still have the dapper cd, insert that one first.

---

### Post by forestpixie on 2008-06-15
edit the file - open it with 

```
gksudo gedit /etc/apt/sources.list
```

delete the dapper line and save then run

```
sudo apt-get update
sudo apt-get install build-essential
```

hopefully it will install - if you've not used the terminal as sudo - it will want your password - enter it - but it will not appear - it is there though.

---

### Post by pablote on 2008-06-15
Did that, but i still have the same problem. When i try to install the packages, synaptic asks me to insert the cd with label: "Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)" on the unit /cdrom/ ... =(

any other ideas? (thanks a lot anyway)

EDIT: when i do the same thing on the terminal i get the exact same message. It appears as synaptic doesn't recognize the cd for some reason when it comes to installing, but before that everything runs smoothly. In fact, it tells me how many disk space i require to install the packages, etc.

---

### Post by forestpixie on 2008-06-15
try with the dapper cd as drs305 said then

---

### Post by pablote on 2008-06-15
I already tried with the Dapper cd, and i can install packages succesfully, but the built-essentials are not there =(

EDIT: apparently i'm now having another problem: i unchecked de hardy cd from the repositories list, and i want to add de dapper cd, an error window pops up telling me "FAILED TO MOUNT CD ROM". Maybe there is some conflict with the cd rom drive???

---

### Post by drs305 on 2008-06-15
I don't think your CDRom is working. But you say you can read the cd and the files. The "mount" command should show the cdrom0 mounted. The following assumes your CD is mounted and readable.

My only other guess is to make a backup of sources.list
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list-bak1
```

Open synaptic. Go to settings, repositories, third party software. For some reason, my old cd is listed there as well. If you cd is listed but not checked, check it and try again. But here is what might work: remove any third party cd and then select Add CDRom. Maybe it will recognize your CD this way. If not, you can restore your backed up copy of sources.list to continue troubleshooting.

---

### Post by cariboo on 2008-06-15
Have you tried in a terminl:

```
sudo mount /media/cdrom
```

Jim

---

### Post by forestpixie on 2008-06-15
If you can't get it to work through apt - open the cd in nautilus - navigate to the /pool/main folder and that is where the packages are - right click and open it with Gdebi - I think that should work.

These are the packages on which it depends so those will need to be installed, might not work but if you can't get it to add as an apt source might be worth the try

[http://packages.ubuntu.com/hardy/build-essential](http://packages.ubuntu.com/hardy/build-essential)

---

