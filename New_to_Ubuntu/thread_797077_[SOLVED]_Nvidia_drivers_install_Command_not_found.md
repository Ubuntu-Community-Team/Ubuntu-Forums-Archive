---
title: "[SOLVED] Nvidia drivers install Command not found"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by Lukky on 2008-05-16
Ok,
   This new install of Ubuntu is kicking my butt. I am trying to install the Nvidia drivers for my Nvidia 7150m on my hp laptop (dv6815nr) So I go to the login and hit "ctr alt f1" I disable the x Server then I try every command know to man And it wont work. The file from Nvidia is on my desktop. This is the last thing I tried after logging in droping the file in the promt and copying the code from there. It tries to work when I just drop the file in the promt but offcourse the X server is still running. 

Sudo /home/dustin/desktop/nvidia-linux-x86-169.12.pkg1.run

With that line of code I get Command not found?

Please Help

---

### Post by macaholic on 2008-05-16
Well the way you would run that would be ```
cd Desktop
``` then running ```
sudo ./nvidia-linux*
``` but why are you installing it like that? I'm not an nvidia user, but I didn't think that was the best way to install those drivers.
P.S.
It is always sudo, not Sudo, the capital makes all the difference.

---

### Post by Raccoon1400 on 2008-05-16
> **macaholic said:**
> Well the way you would run that would be ```
cd Desktop
``` then running ```
sudo ./nvidia-linux*
``` but why are you installing it like that? I'm not an nvidia user, but I didn't think that was the best way to install those drivers.
P.S.
It is always sudo, not Sudo, the capital makes all the difference.

cd shows the specified directory. Wouldn't it be
```
cd ./Desktop
```

Use restricted drivers manager.

---

### Post by PinkFloyd102489 on 2008-05-16
Best way for me has always been to download the drivers from the site and make a quick console run. I prefer it over the GUI frontends because I have a slow computer.

Fairly straight forward. Kill GDM, run script, correct errors, restart GDM.

---

### Post by macaholic on 2008-05-16
> **Raccoon1400 said:**
> cd shows the specified directory. Wouldn't it be
```
cd ./Desktop
```

No, the ./ is unnecessary. As long as his terminal defaults to his home directory, he would have to change it to something else, cd Desktop should work just fine.

---

### Post by Lukky on 2008-05-16
I am instlaling it like that because I am a ROOKIE and that is the only way I have found to install it. 
   Ok I got the cd Desktop to work. Then I tried this code
sudo ./nvidia-linux-x86-169.12.pkg1.run
   I still get command not found. There has to be a problem with my syntax or something. 
Does the all caps matter in the name "NVIDIA" ?

THanks Dusitn

---

### Post by macaholic on 2008-05-16
Try ```
sudo bash ./nvidia*
```

---

### Post by ad_267 on 2008-05-16
Why don't you just go System - Administration - Hardware Drivers and enable the nVidia drivers from there. If you're using Hardy they should be the latest drivers.

---

### Post by macaholic on 2008-05-16
> **ad_267 said:**
> Why don't you just go System - Administration - Hardware Drivers and enable the nVidia drivers from there. If you're using Hardy they should be the latest drivers.
yes, if they are the same drivers (I honestly don't know if they are) then that is the best way to install them.

---

### Post by Swatfoot on 2008-05-16
sorry

---

### Post by Lukky on 2008-05-17
From my understanding to install the NVIDIA drivers the X server has to be disabled. This leaves me with a command promt to install from. I am using UBU 8.04

Thanks Dustin

---

### Post by Lukky on 2008-05-17
When I go to Hardware drivers it show the nvidia_new and it is checked to be inabled but there is a red light and it says not in use.

---

### Post by Lukky on 2008-05-17
ok I found my Syntax error. It seems I didnt have the "L" in linux capitilized. So the command it working but know I get an No Matching Kernel interface was found. What does that mean. It wanted to connect to the internet and download it but offcourse I cant make my wireless work yet so that didnt work. Did I get the wrong driver or is this Kernel just too new?

Thanks Dustin

---

### Post by PmDematagoda on 2008-05-17
You didn't get the wrong driver, the fact is that the Nvidia installer needs to compile a kernel module and for that it could either compile one itself or download an existing one off the internet, in any case there usually isn't a proper pre-built module that matches the kernel to be downloaded so it will have to compile it, for that you will need to install the build-essential package with:-
```
sudo apt-get install build-essential
```

But can you connect to the internet to install it?

---

### Post by ad_267 on 2008-05-17
You should be able to use the method I said to install the drivers. Try unchecking the driver and then recheck it and restart. This is by far the easiest method to install them and should work.

---

### Post by Lukky on 2008-05-17
No I can not connect to the internet. I have not figured that out yet. Atheros 5007

Thanks Dustin

---

### Post by Lukky on 2008-05-17
I tried unchecking the driver closing the hardware manager and then reopening the manager rechecking the driver. I then restarted my computer. I still get the red dot with Not in use.

Thanks Dustin

---

### Post by PmDematagoda on 2008-05-17
> **Lukky said:**
> No I can not connect to the internet. I have not figured that out yet. Atheros 5007

Thanks Dustin

You can try and find a way to use your wireless by starting a thread on this issue in the [Networking & Wireless section]("http://ubuntuforums.org/forumdisplay.php?f=336").

After your wireless dilemma is solved then installing the Nvidia driver should be much easier.

---

### Post by macaholic on 2008-05-17
> **PmDematagoda said:**
> You can try and find a way to use your wireless by starting a thread on this issue in the [Networking & Wireless section]("http://ubuntuforums.org/forumdisplay.php?f=336").

After your wireless dilemma is solved then installing the Nvidia driver should be much easier.
Definitely ture, the first thing you always want to figure out is internet connectivity. Otherwise you have to deal with transporting packages and other files from other computer, which believe me, isn't fin.

---

### Post by Lukky on 2008-05-17
ok So I plugged my computer into the internet. Then I tried the code 
sudo apt-get install build-essential
It tried to do it then came back with an error 
E: couldnt find package build essential

What Now?

Thanks Dustin

---

### Post by Lukky on 2008-05-17
I finally got it installed. I Found some code somewhere on the forum that allowed me to build Essentials and after that it was childs play once I got all of my caps issues fixed. 

Thanks Everyone

Off now to figure out my wifi, Hope to see you there

---

