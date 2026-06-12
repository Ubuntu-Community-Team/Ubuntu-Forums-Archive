---
title: "Google Chrome OS Install Guide"
date: 2011-04-18
forum: Outdated Tutorials &amp; Tips
---

### Post by TheAJGman on 2011-04-18
Hi its me back from the dead. Wasn't here in so long because my Ubuntu laptop stopped working. Im going to show you how to build Google Chrome OS.

Here are some Beta scripts I made that does this automatically
[Install.sh]("http://www.box.net/shared/fpr21jb6sy")

**_[SIZE="4"][CENTER]Requirements[/CENTER][/SIZE]_**
[LIST]
[*]Ubuntu Linux (version 10.04 and up)
[*]A 64-bit system for performing the build
[*]An account with sudo access
[*]A fast machine with  2+ gigs RAM
[*]A fast Internet connection
[/LIST]



**_[SIZE="4"][CENTER]Building Chrome OS[/CENTER][/SIZE]_**

1. Retrieve depot_tools
```
sudo svn co http://src.chromium.org/svn/trunk/tools/depot_tools

```


2. Add depot_tools to your PATH
```
export PATH=`pwd`/depot_tools:"$PATH"
```
Enter this each time you reopen terminal to do some thing out side of /chromiumos

3. Install git
```
sudo apt-get install git-core gitk git-gui
```

4. Configure git
```
git config --global user.email "your email"
git config --global user.name "Your Name"
```

5. Make a home for the source
```
mkdir -p ${HOME}/chromiumos
```

6. Do you want Full(slow and huge) or Minn(fast and small)?
     a. Mini
     ```
cd ${HOME}/chromiumos
repo init -u http://git.chromium.org/chromiumos/manifest.git -m minilayout.xml
repo sync
```
     b. Full
     ```
cd ${HOME}/chromiumos
repo init -u http://git.chromium.org/chromiumos/manifest.git
repo sync
```
*repo sync takes for ever

7. Create croot
```
cros_sdk
```
Takes a while
8. Enter croot
```
cros_sdk --enter
```

9. Select the board
     a. ```
BOARD=x86-generic
```- a good place to get started if you're running Chromium OS on a computer with a x86-compatible CPU
     b. ```
BOARD=arm-generic
``` - a good place to get started if you're running Chromium OS on a computer with a ARM CPU

10. Initialize the build for a board
```
./setup_board --board=${BOARD}
```

11. Set the chronos password(chronos is the admin)
```
./set_shared_user_password.sh
```

12. Build the packages for your board
```
./build_packages --board=${BOARD}
```
*Takes 90+ minutes

13. Build a disk image for your board
```
./build_image --board=${BOARD} --withdev --noenable_rootfs_verification
```

14. Put your image on a USB disk
```
./image_to_usb.sh --board=${BOARD}
```
When it tells you that you must specify a file or device to write to then use this
```
./image_to_usb.sh --board=${BOARD} --to /dev/YOUR USB DEVICE HERE
```
*This erases the enter drive. You need a 2gig for Mini and a 4gig for Full layouts.


Set you bios to allow usb boot and set the usb device higher boot privilege than the hdd. your done if you have any questions please leave them below!

---

### Post by Spiritof76 on 2011-04-18
can this be built on a 32 bit OS?

---

### Post by TheAJGman on 2011-04-18
> **Spiritof76 said:**
> can this be built on a 32 bit OS?

No it's says at the top

---

### Post by TheAJGman on 2011-04-19
Bump bump buuuuuuuuuuuummmmmmppp

---

### Post by samurailink3 on 2011-04-20
Great tutorial! Perfect resource for anyone wanting to 'Get up and go' with Chrome OS.

---

### Post by uRock on 2011-04-20
> **TheAJGman said:**
> Bump bump buuuuuuuuuuuummmmmmppp

Please do not bump your tutorial to keep it at the top of the list.

---

### Post by TheAJGman on 2011-04-20
Ok

---

### Post by Fedil on 2011-04-24
Hi. I like this guide. I would like to try to install Chrome OS but i want first to try ChromeOS virtually. 

Could you explain the way for someone who wants to install ChromeOS on Virtual Box?

---

### Post by TheAJGman on 2011-04-24
I wouldn't know how but if you go to Hexxeh's site you can get a vanilla build it takes about an hour with torrent to download.

---

### Post by scott_g on 2011-05-14
> **Fedil said:**
> Hi. I like this guide. I would like to try to install Chrome OS but i want first to try ChromeOS virtually. 

Could you explain the way for someone who wants to install ChromeOS on Virtual Box?

[http://www.chromium.org/chromium-os/developer-guide]("http://www.chromium.org/chromium-os/developer-guide")

The above link gives more detailed information on the subject; instructions for installing to a virtual machine, or a USB flash drive are about 1/2 or 2/3 of the way down.

Hope it helps,
Scott

---

### Post by TheAJGman on 2011-05-21
Actually I adapted this guide from the official one because the official one isn't strait forward enough.

---

### Post by TheAJGman on 2011-05-26
if any one could help with my automated program go to
[http://ubuntuforums.org/showthread.php?p=10866038]("http://ubuntuforums.org/showthread.php?p=10866038") to help

---

