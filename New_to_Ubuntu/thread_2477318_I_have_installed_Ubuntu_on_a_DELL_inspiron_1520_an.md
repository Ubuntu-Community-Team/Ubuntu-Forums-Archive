---
title: "I have installed Ubuntu on a DELL inspiron 1520 and it is not working correctly?"
date: 2022-07-21
forum: New to Ubuntu
---

### Post by bob1042 on 2022-07-21
I have installed Ubuntu on a DELL inspiron 1520 and it boots ok but then when I log in, it loops back to the Lock Screen. How can I fix this?

---

### Post by guiverc on 2022-07-21
You've not provided any product or release details.

By Lock screen, I also assume you mean the login/greeter screen; as the lock screen can be a different program for some systems (eg. Lubuntu uses xscreensaver as it's lock screen, but sddm as the greeter).

The first thing I'd check is disk space; did you provide sufficient space for your system as a GUI login will fail if insufficient space exists in $HOME or your home directory, meaning a GUI login will fail & the user is returned to the greeter (ie. login loop). But terminal logins will work allowing you to explore space issues. But this may or may not apply, as you didn't say if you're asking about Ubuntu Desktop?  Ubuntu Server?  Ubuntu Core?  or a Ubuntu *flavor* (like Lubuntu I mention in example).  The minimum requirements differ for the various products (desktop needing more than a server etc).

---

### Post by bob1042 on 2022-07-21
I have installed Ubuntu desktop and the hdd in the laptop is 80GB

---

### Post by oldfred on 2022-07-21
As that old of a system Lubuntu or other light weight flavor would be better.
You never said what version of Ubuntu? 22.04?
What video card/chip? specs show several options.

Light weight flavors:
Lubuntu, xubuntu, Ubuntu MATE, Budgie
[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)
[https://wiki.ubuntu.com/UbuntuFlavors](https://wiki.ubuntu.com/UbuntuFlavors)

I was able to use Kubuntu on my old laptop, and it is a mid-weight flavor. Ubuntu would not even install on that system. But Ubuntu server would install.

---

### Post by grahammechanical on 2022-07-21
What happened when you tested Ubuntu using the Try Ubuntu option?

How much memory (RAM) does the machine have? How much video memory does the video card have? If your machine has the lower end of these specifications then I am not surprised that present day Ubuntu is not loading. Even with the upper limit of video memory (512K) I would not expect a great performance out of Ubuntu.

[https://www.itechguides.com/product-specs/dell-inspiron-1520-specs/](https://www.itechguides.com/product-specs/dell-inspiron-1520-specs/)

Regards

---

### Post by ActionParsnip on 2022-07-21
If you press CTRL + ALT + F1 then can you log in there. If so, make sure there is free drive space with
```

df -h

```

Free space as possible. You should at least run 
```
 
sudo apt clean

``` 

You should then also make sure you are the owner of your entire home folder by running the below (you don't need to change this. The BASH variables make this easier
```

sudo chown -R $USER:$USER $HOME

```
Watch the spaces here.

You can then run
```

sudo reboot

```
Then retry logging in as usual.

---

### Post by guiverc on 2022-07-21
I still have no release details; eg. are you asking about Ubuntu 18.04 LTS Desktop (ie. 2018-April release), Ubuntu 22.04 LTS Desktop (ie. 2022-April release) etc.

Did you check your system meets the minimum hardware requirements for Ubuntu Desktop?

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

You'll note that includes

[LIST]
[*]2 GHz dual core processor 
[*]4 GiB RAM (system memory) 
[*]25  GB (8.6 GB for minimal) of hard-drive space (or USB stick, memory card  or external drive but see LiveCD for an alternative approach) 
[*]VGA capable of 1024x768 screen resolution 
[*]Either a CD/DVD drive or a USB port for the installer media 
[/LIST]

Further if you explore it has minimum specs for the video card too.

I don't know the specs of your machine, a quick look showed it to be c2d which made me think of a machine I use in QA (*Quality Assurance*) where I'd not choose Ubuntu Desktop, but a *lighter* flavor.

> lenovo thinkpad sl510 (c2d-t6570, 2gb ram, i915)

2GB of RAM in the box & lack of required "*3D Acceleration Capable Videocard with at least 256 MB*" (*the lenovo sl510 has **no*** *dedicated RAM for video*) make Ubuntu Desktop a poor choice; so whilst I may use it to ensure the system boots [*Ubuntu Desktop*], its not used for anything else except with lighter *flavors*.

You gave no machine specs as to your device. Does it meet the minimum specs? (*the minimums in the document I provided link for apply to all releases of Ubuntu since 17.10 or the 2017-October release which was the return of GNOME Desktop*)

---

