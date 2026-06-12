---
title: "No nvidia drivers to install?"
date: 2008-11-22
forum: New to Ubuntu
---

### Post by kjacobs on 2008-11-22
Now that I know I have a GeForce4 ti4200 card, i figured i need to install the nvidia driver. So, i went to "hardware drivers" to enable the nvidia driver, but there are no drivers listed at all in the "hardware drivers" section to enable. How do i get those enabled?

---

### Post by jenkinbr on 2008-11-22
For your card, GeForce4 ti4200, I think you need the nvidia-glx-96 drivers.

```
sudo apt-get install nvidia-glx-96 
```
should do it.

Why they arn't listed, I don't know.

---

### Post by Lazy-buntu on 2008-11-22
If that doesn't work try going to the nvidia website, finding your graphics card, and they should supply you with the correct driver. Then it's just a matter of installing it yourself.

---

### Post by kjacobs on 2008-11-22
Rats....I ran the sudo apt-get and got back an a "couldn't find package" error. That machine does not have internet, yet. I'm still trying to solve a wireless problem on it.

---

### Post by jenkinbr on 2008-11-22
> **kjacobs said:**
> Rats....I ran the sudo apt-get and got back an a "couldn't find package" error. That machine does not have internet, yet. I'm still trying to solve a wireless problem on it.
That may be why they aren't displaying.

Put your original installation CD in the drive.  A message should pop up asking if you want to open the software volume in your package manager (synaptic)  Once synaptic opens, find the package 'nvidia-glx-96' and mark it for installation.  (btw, I am assuming you are using intrepid?  Correct me if I am wrong here...)

---

### Post by kjacobs on 2008-11-22
> **jenkinbr said:**
> That may be why they aren't displaying.

Put your original installation CD in the drive.  A message should pop up asking if you want to open the software volume in your package manager (synaptic)  Once synaptic opens, find the package 'nvidia-glx-96' and mark it for installation.  (btw, I am assuming you are using intrepid?  Correct me if I am wrong here...)


Arggghhhh....okay I put the cd in the drive and all it popped up was a message to autorun the cd. I tried clicking yes and got an error. So then I went to synaptic package manager and checked for nvidia drivers. All the nvidia-*-modaliases and the nvidia-common file are already installed. I tried to use the load cd option and no drivers came up. I tried to do a search for the nvidia-glx-96 on the cd and came up with nothing.

Funny, how one little thing can get so complicated....

---

### Post by jenkinbr on 2008-11-22
> **jenkinbr said:**
> ....(btw, I am assuming you are using intrepid?  Correct me if I am wrong here...)

Are you using intrepid, hardy, or a different distro?

run ```
uname
``` and let me know what the output is.

---

### Post by roger_1960 on 2008-11-22
Hi

The following is in the 8.10 release notes:

nVidia "legacy" video support

The 71 and 96 series of proprietary nVidia drivers, as provided by the nvidia-glx-legacy and nvidia-glx packages in Ubuntu 8.04 LTS, are not compatible with the X.Org included in Ubuntu 8.10. Users with the nVidia TNT, TNT2, TNT Ultra, GeForce, GeForce2, GeForce3, and GeForce4 chipsets are affected and will be transitioned on upgrade to the free nv driver instead. This driver does not support 3D acceleration. 

I think its not that simple.......Try searching the installation forum.  This link seems relevant:

[http://ubuntuforums.org/showthread.php?t=970237&highlight=GeForce4](http://ubuntuforums.org/showthread.php?t=970237&highlight=GeForce4)

---

### Post by kjacobs on 2008-11-22
Oops, sorry....I am using 8.10. I typed uname and all it said was "Linux". Ha, I kind of knew that....

---

### Post by kjacobs on 2008-11-22
> **roger_1960 said:**
> Hi

The following is in the 8.10 release notes:

nVidia "legacy" video support

The 71 and 96 series of proprietary nVidia drivers, as provided by the nvidia-glx-legacy and nvidia-glx packages in Ubuntu 8.04 LTS, are not compatible with the X.Org included in Ubuntu 8.10. Users with the nVidia TNT, TNT2, TNT Ultra, GeForce, GeForce2, GeForce3, and GeForce4 chipsets are affected and will be transitioned on upgrade to the free nv driver instead. This driver does not support 3D acceleration. 

I think its not that simple.......Try searching the installation forum.  This link seems relevant:

[http://ubuntuforums.org/showthread.php?t=970237&highlight=GeForce4](http://ubuntuforums.org/showthread.php?t=970237&highlight=GeForce4)

Wow!!! I guess I fall into that category. That stink....should I go back to 8.04? Would that bring back working drivers???

---

### Post by roger_1960 on 2008-11-22
Hi

Yes, back to 8.04 should work.  I think there is a solution for 8.10 in the link I posted as well.

Good luck!!

---

### Post by kjacobs on 2008-11-22
Thanks to all for the help...in the interest of simplicity, I'm moving back to 8.04 for the time being...until the nvidia thing is resolved. Hopefully, I'll get the wireless working on that.

---

