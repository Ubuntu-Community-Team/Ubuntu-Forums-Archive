---
title: "Graphic's and display is messing up"
date: 2012-08-19
forum: New to Ubuntu
---

### Post by amber95 on 2012-08-19
I am kinda new to ubuntu, I just had to reinstall it because i play a game online and it needs wine to run but it messed up so i had to reinstall ubuntu, Now if i try to install one of the driver's that is listed then it messed up i have picture's of everything, I can't change the resolution and if i try to install one of the driver's after i restart the computer it crashes Compiz i think it's called, I don't know what to do can anyone please help? :( [http://s1079.photobucket.com/albums/w513/Tonywlo0/Ubuntu/](http://s1079.photobucket.com/albums/w513/Tonywlo0/Ubuntu/)

---

### Post by LordEager on 2012-08-19
First: there was no reason to re-install the OS for a Wine issue.
Second: The nVidia drivers listed on proprietary drivers, were there by default, or you downloaded them from nvidia site?
Third: You should now give me some useful info on your system, to do this i'd like to have the inxi output, in order to do this, type this in terminal (copy&paste):

**sudo**[B] -s
      wget -O /etc/apt/sources.list.d/cathbard.list         [http://cathbard.com/files/cathbard.list](http://cathbard.com/files/cathbard.list)[/B]
[B]apt-get update && apt-get install inxi

[/B]When this is done, type please in terminal (log off from root session before):
[B]inxi -Gx
[/B]And post here the full output.```

```

---

### Post by amber95 on 2012-08-19
> Graphics:  Card: NVIDIA C61 [GeForce 6150SE nForce 430] bus-ID: 00:0d.0 
           X.Org: 1.11.3 drivers: nvidia (unloaded: nouveau,vesa,fbdev) Resolution: 640x480@50.0hz 
           GLX Renderer: GeForce 6150SE nForce 430/PCI/SSE2 GLX Version: 2.1.2 NVIDIA 173.14.35 Direct Rendering: Yes

Ok

---

### Post by LordEager on 2012-08-19
Ok drivers are loaded fine, now post the results of : **xrandr**

---

