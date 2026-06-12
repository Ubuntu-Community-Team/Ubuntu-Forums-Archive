---
title: "some things i need to get in 11.10 xubuntu"
date: 2011-08-20
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by raja.genupula on 2011-08-20
1. actually i like terminal as  background of terminal should visual 
2. how to install themes for xubuntu 
3. am i  able to install unity in xubuntu .   


thanks in advance

---

### Post by cariboo on 2011-08-21
All the software you want is available via the Software Center or synaptic.

---

### Post by raja.genupula on 2011-08-21
i have installed gnome-terminal from software center. the transparent feature i am not getting .one more thing i am not getting sound also .

---

### Post by cariboo on 2011-08-21
Open a terminal and select Edit->Profile preferences to set colors and transparency, plus more.

We can't help with the sound problem, as you haven't given us any details.

---

### Post by raja.genupula on 2011-08-21
hey , i dont know what the details you want , could you please tell me what are those ?

---

### Post by cariboo on 2011-08-21
Could you paste the output of:

```
sudo lshw -C multimedia
```

in your next post.

---

### Post by raja.genupula on 2011-08-21
hey 
```
*-multimedia            
       description: Audio device
       product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 04
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:46 memory:fdff8000-fdffbfff

```

---

### Post by raja.genupula on 2011-08-21
> **cariboo907 said:**
> Open a terminal and select Edit->Profile preferences to set colors and transparency, plus more.

We can't help with the sound problem, as you haven't given us any details.

i have given the image , i have enabled transparent also. but i didn't get it . look at the image i have given in previous post .

---

### Post by cariboo on 2011-08-21
See the screenshot, to see he way I have my terminal preferences set.

As far as your sound problem goes, do you have the proper device set in sound preferences? If you have a fairly recent video card with a HDMI output, you may have that set as your sound device.

---

### Post by raja.genupula on 2011-08-21
no i am not getting . i have tried as you have given . if you want then i can able to provide the image . small doubt are you doing that in xubuntu or ubuntu . because i am trying to do in xubuntu , i already know how to do in ubuntu .

---

### Post by raja.genupula on 2011-08-21
i got solved with my sound problem by installing pulse audio volume controller from software center . now only one issue making my terminal as transparent .

---

### Post by madjr on 2011-08-21
why not install regular ubuntu where things work and it seems you want gnome, not xfce and if you want xubuntu later on, just install the package "*xubuntu-desktop*" (or viceversa and install "**ubuntu-desktop**"). Then log out and choose which one you want to log in.

---

### Post by raja.genupula on 2011-08-22
thats good idea . i like that . but small doubt , if i install ubuntu -desktop , was this install makes 11.10 ubuntu or 11.04 or any other else ubuntu desktop.

---

### Post by madjr on 2011-08-22
> **raja.genupula said:**
> thats good idea . i like that . but small doubt , if i install ubuntu -desktop , was this install makes 11.10 ubuntu or 11.04 or any other else ubuntu desktop.

the same version you are running

---

### Post by raja.genupula on 2011-08-22
thank you very much @cariboo907,@madjr for your great support . 
i got what i want . i am closing this .

---

