---
title: "Drivers for Intel Pro 3945 wireless for Hardy"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by pvsdilhan on 2008-06-09
I have Intel Pro 3945bg wireless card. But it does not have drivers for Ubuntu hardy(8.04). Can any one help me to install that driver? It is convenient if you can explain it step by step. thanks.

---

### Post by Golem XIV on 2008-06-09
The driver for the 3945 is in the kernel, there is no need to install it.  It should work out-of-the-box.  Are you having problems with your wireless setup?

---

### Post by Nepherte on 2008-06-09
There is the closed source ipw3945 driver, which is a deprecated project. Instead Ubuntu uses the newer open source iwl3945 driver which is already included in the kernel.

---

### Post by ukripper on 2008-06-09
3945ABG is supported in hardy by default. It is using iwl3945

---

### Post by pvsdilhan on 2008-06-11
Thank you for your replies.
But I do not know how to configure that. Can you please explain me to configure that, step by step. Thanks.

---

### Post by ukripper on 2008-06-11
> **pvsdilhan said:**
> Thank you for your replies.
But I do not know how to configure that. Can you please explain me to configure that, step by step. Thanks.


Go to network manager, 

system-->administration-->Network manager 

enter your password

and then make sure Wireless is ticked--> go to properties of wireless  and then find your Access point in the dropped down list of ESSID. and then enter your key and thats it.

---

### Post by zzandeamos on 2008-06-11
UKRipper:

I have the same problem and I think everything is there I just don't know how to configure it.

|Go to network manager,
|
|system-->administration-->Network manager

(mine says 'network settings')

|enter your password
|
|and then make sure Wireless is ticked--> go to properties of |wireless and then find your Access point in the dropped down 
list |of ESSID. and then enter your key and thats it.

(the id of my wireless does not drop down, I have to put it in.)

I can get the wired eth working O.K. but the wireless is no go.
I can put in a live cd of Puppy Linux and get on wireless no problem.

When I first load 8.04 and bring up Firefox I go to the little vertical bars that indicate signal strength when online and click it and there is the wireless and the wired radio buttons. The wireless shows 70% or so. Then when I select wireless it wants the passphrase, I put that in and the little slider goes back and forth but never connects. After a bit it will ask for the passphrase again. Then no matter what I try it goes down hill until I can't see the wireless anymore and I have to reload the cd to get back to be able to see it.  The wired does not go away.  
I can keep working with it. 
Can you give me some ideas to try or if you could use some info let me know?
Thanks FDC

---

### Post by pvsdilhan on 2008-06-12
Thanks ukripper. I followed as you said. But there is nothing in ESSID.(I mean no item in the dropd down menu). So what do I have to do? Wirless network is working properly under Windows Vista.

---

### Post by p_quarles on 2008-06-12
Try this (in the command line):
```
sudo modprobe iwl3945
sudo /etc/init.d/networking force-reload
```
Now, try running the network manager again and trying to connect to a wireless router. If that works (it should!), then it will be easy to make this fix permanent.

---

### Post by Paqman on 2008-06-12
Is you access point broadcasting it's SSID? Check your router settings.

I'm using that same card on my laptop and confirm that it works without any setup required.

---

### Post by pvsdilhan on 2008-06-12
thank you p_quarles. But it did not work. Commands executed without a error. But I wa sunable to configure that.

---

### Post by ukripper on 2008-06-12
just to point out one thing about iwl3945, it doesn't like hidden ssid. Make sure your router has hidden ssid disabled. Or everytime you have to enter the ssid and key to get connected it won't show up in dropped down list

---

### Post by zzandeamos on 2008-06-12
> **p_quarles said:**
> Try this (in the command line):
```
sudo modprobe iwl3945
sudo /etc/init.d/networking force-reload
```
Now, try running the network manager again and trying to connect to a wireless router. If that works (it should!), then it will be easy to make this fix permanent.

Hey That looks good, so now I don't have to reinstall the 8.04 to get back to start.
fdc

---

### Post by DRSMURF on 2008-06-18
i think there is a problem with the driver itself because i ve tried the latest of many versions of Linux all have the same problem so the only way is to use Ubuntu 7.10 or to use ipw3945
thanks
by the way am very new in linux
so am not sure

---

### Post by Papi-KB7VGW on 2008-06-18
Follow this link.  It worked for me.  My light even works...

[http://ubuntuforums.org/showthread.php?t=808516](http://ubuntuforums.org/showthread.php?t=808516)

---

### Post by pvsdilhan on 2008-07-02
Thank you very much for all of you guys for your advices. I was finally solved my problem. I refer following link to solve it.

[[COLOR="Blue"]http://linuxexpert.wordpress.com/2008/04/28/fix-intel-wireless-driver-on-hardy/[/COLOR]]("http://linuxexpert.wordpress.com/2008/04/28/fix-intel-wireless-driver-on-hardy/")

---

### Post by ukripper on 2008-07-02
> **DRSMURF said:**
> i think there is a problem with the driver itself because i ve tried the latest of many versions of Linux all have the same problem so the only way is to use Ubuntu 7.10 or to use ipw3945
thanks
by the way am very new in linux
so am not sure

i am using 7.10 with iwl3945 with no problem. ipw3945 has been depreciated support wise. iwl should be used.

---

