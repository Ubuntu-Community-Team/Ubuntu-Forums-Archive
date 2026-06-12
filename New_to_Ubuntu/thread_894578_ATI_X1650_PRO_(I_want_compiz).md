---
title: "ATI X1650 PRO (I want compiz)"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by Tom--d on 2008-08-19
Hello,
I have brought down my desktop from the loft. It has an ATI X1650 PRO graphics card. 
Here is the lspci | grep "ATI"
```
01:00.0 VGA compatible controller: ATI Technologies Inc RV530LE [Radeon X1600/X1650 PRO]
01:00.1 Display controller: ATI Technologies Inc RV530LE [Radeon X1650 PRO] (Secondary)
```
At the moment, I'm using the ati or radeon Open source driver. It has the right resolution, 1440x900 but no 3d support. (I know this, but in time.. there will be :))
but I would like to have 3D support. Which I know, fglrx. 
Used Hardware Drivers in system but it just left a blank picture when X was starting. No mouse. Nothing.
Removing the fglrx and reconfiguring X sorted that out and was back with 1400x900 with the open source drivers.

I tired EnvyNG. Didn't work.

I would like Compiz and maybe the odd game (Darkplaces (modification of Quake one))...

Thank you.
I hope someone can help me.
Tom

---

### Post by tangibleorange on 2008-08-19
reinstall the restricted drivers. then when X fails to start, press Ctrl+Alt+F1. then type:
```
sudo dpkg-reconfigure xserver-xorg
startx
```

hopefully that will work

---

### Post by Tom--d on 2008-08-19
> **tangibleorange said:**
> reinstall the restricted drivers. then when X fails to start, press Ctrl+Alt+F1. then type:
```
sudo dpkg-reconfigure xserver-xorg
startx
```

hopefully that will work

Thank you. 
Will try that in a min :)

---

### Post by Tom--d on 2008-08-19
No, it did not work.

What happens is when I logged out. I dont get a logging, well, i do. But its all fuzzed. Cann't see anything. The mouse is just lines of in a square. I can log in. and then my screen is just ****** really. CAnt see what im doing.
Then it just goes silver. The whole displayer is silver. :\
Fail safe gnome, I can get in. Just no Compiz.

---

### Post by nicedude on 2008-08-20
If envyng didn't work for you I would suggest you have a look at ATI's site as they have Linux based driver packages there for download. I don't use any ATI cards so I am not sure exactly how they do their install but if it is like Nvidia's then it isn't too hard but you will have to find some instructions on how to do it first. For example to install Nvidia you have to press Ctrl+Alt+F1 -> Login in non graphic environment -> then stop the X graphics server that is running in the background -> then type the name of the driver installer -> then restart the X server and your done. I would imagine an ATI install is similar.

ATI DRIVERS PAGE - SELECT LINUX AS OS 
[http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html)

Hope this helps

---

### Post by Tom--d on 2008-08-20
> **nicedude said:**
> If envyng didn't work for you I would suggest you have a look at ATI's site as they have Linux based driver packages there for download. I don't use any ATI cards so I am not sure exactly how they do their install but if it is like Nvidia's then it isn't too hard but you will have to find some instructions on how to do it first. For example to install Nvidia you have to press Ctrl+Alt+F1 -> Login in non graphic environment -> then stop the X graphics server that is running in the background -> then type the name of the driver installer -> then restart the X server and your done. I would imagine an ATI install is similar.

ATI DRIVERS PAGE - SELECT LINUX AS OS 
[http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html)

Hope this helps

Thanks, 
I will give it a try.

---

### Post by cjstuttle on 2008-08-20
can i ask where u got these initial driver from? i have a x1650 pro too, im new at Linux and would like a hand finding them and installing them. please

i found this on there web site 
[http://support.ati.com/ics/support/default.asp?deptID=894](http://support.ati.com/ics/support/default.asp?deptID=894)

but at the moment i dont understand what its all talking about and if it will help or hinder me

---

### Post by Tom--d on 2008-08-22
> **cjstuttle said:**
> can i ask where u got these initial driver from? i have a x1650 pro too, im new at Linux and would like a hand finding them and installing them. please

i found this on there web site 
[http://support.ati.com/ics/support/default.asp?deptID=894](http://support.ati.com/ics/support/default.asp?deptID=894)

but at the moment i dont understand what its all talking about and if it will help or hinder me

The Closed source Driver from Ati website does not work for me. Still get no X after installed and configured.

The open source driver, ati, which is in the installation of Ubuntu is used. It gives the right resolution for me but no 3D support yet.(will do in time). I want 3D support for compiz.

---

