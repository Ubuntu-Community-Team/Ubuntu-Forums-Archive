---
title: "Screen Resolution Problem in 8.04"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by MichaelDobbs on 2008-04-25
I have just installed hardy inside windows. All went well accept on start up I get a message about only having low resolution available. I get the option to configure but when I try... no joy. I have a VIA/S3G UniChrome Pro IGP. On the S3 site it said to use the S3 Savage 4(generic) driver but the option box doesn't allow me to use that. In fact I can only choose from among the drivers direct it wont allow me to go to select from the Brand choices or should I say it allows me to make a selection but then defaults back to the driver direct option. So at the moment the best screen resolution I can get is 800 x 600 on my 19 inch LCD monitor. If you haven't already guessed I am a novice who had hardy beta installed on a second hdd until that died a few days ago.
Any help will be appreciated!

---

### Post by zvacet on 2008-04-25
Applications>accessories>terminal>type

```
sudo dpkg-reconfigure xserver-xorg
```

Select vesa driver and change resolution.After restart go to the sysem>preferences and see if you can choose your resolution.Of course it shoud work.

---

### Post by shuffer on 2008-04-25
Sorry to be a complete idiot here, but the above method merely takes me through a load of keyboard options, then returns me to the Terminal. Getting the screen res right on my system is vital to me as I'm using our old Soy 1280 x 768 TV and the current res is giving me a headache. Again, I don't want to moan too much about free software, but this faffing about is going to lose Linux some switchers due to the complexity.

---

### Post by MichaelDobbs on 2008-04-25
Sorry but I am getting the same result as our friend shuffer. After the restart nothing had changed at all. 
Any more ideas??

---

### Post by spacefreak86 on 2008-04-26
I am also having problems with screen resolution, both while Kubuntu is booting up, and in the login screen, and I suspect on the desktop too. How do you go about changing / viewing what the current screen resolution is?

---

### Post by akiratheoni on 2008-04-26
Yeah the sudo dpkg-reconfigure xserver-xorg doesn't give me the option of resolution. I'd like a fix for this. I was able to use my old xorg.conf from Gutsy but I'd rather be able to adjust the resolution without needing to do so. Also, my login screen is not the correct resolution. In Feisty it was the correct one but in Gutsy and Hardy it's not anymore.

---

### Post by alienexplorers on 2008-04-26
First do you have the correct drivers installed.  If so you can go to System/Preferences/Screen Resolution to change the resolution.

---

### Post by spacefreak86 on 2008-04-26
Do you know how to change the screen resolution in Kubuntu? I need this for both the desktop and the boot screen / logon screen, as I am having issues with those areas as well.

---

### Post by MichaelDobbs on 2008-04-26
When I was using Feisty and then Hardy-Beta on the seperate HDD they were ok (not quite as high resolution as I would have liked but ok). Now as mentioned above the best res on offer is 800x600.

---

### Post by MichaelDobbs on 2008-04-26
You mention drivers - Where do I get these drivers? As mentioned above I went to the S3 site and got a driver but haven't worked out how to install it. I have unzipped it and there is a .run file - I have never seen one of these before. How do I install it? If I do install it will the system let me choose it because as mentioned earlier when I go to the "configure" option it doesn't accept my selection??

---

### Post by kagashe on 2008-04-26
> **zvacet said:**
> Applications>accessories>terminal>type

```
sudo dpkg-reconfigure xserver-xorg
```

Select vesa driver and change resolution.After restart go to the sysem>preferences and see if you can choose your resolution.Of course it shoud work.
I don't think "sudo dpkg-reconfigure xserver-xorg" is going to work on Hardy Heron.

---

