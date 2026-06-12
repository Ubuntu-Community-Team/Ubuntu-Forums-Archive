---
title: "9600GT fan noise."
date: 2008-06-03
forum: New to Ubuntu
---

### Post by CLomax on 2008-06-03
Recently bought an nVidia 9600GT which was a silly move since I use Ubuntu a lot. I was trilled that it displayed 1440x900 straight away with Ubuntu (800x600 on Windows ~_~) but I'm getting quite a bit of noise from the fan of my GPU which I could shut up in Windows by installing a driver, is that the case with Ubuntu too? I *think* I have a driver installed; by *think* I mean that I have used Envy to install the 169.something driver which wasn't clear as to whether it actually installed or not and the next boot up resulted in an error with the X server.

I'm also having a little trouble with the 'Desktop effects could not be enabled' message >.<

Any help appreciated, thank you.

---

### Post by phidia on 2008-06-03
If you are not seeing the nvidia splash screen prior to the login window chances are the driver didn't install correctly. 
What driver is listed in your /etc/X11/xorg.conf file? I'm providing the Device section of my xorg.conf below so you can see what it should look like and what to look for.

> Section "Device"
	Identifier	"nVidia Corporation G70 [GeForce 7600 GS]"
	Boardname	"nv"
	Busid		"PCI:5:0:0"
	Driver		"nvidia"
	Screen	0
Hope that's helpful.

About the fan noise I don't know of anyway in linux to change the fan setting on your gpu.

---

### Post by CLomax on 2008-06-03
> Section "Device"
	Identifier	"Device0"
	Driver		"nv"
	Vendorname	"NVIDIA Corporation"

I've successfully installed the driver through manual means but I still get an error with the X server, the only way to bypass it is to boot into recovery mode and select 'fix X server'. I was also informed by the error details that the only problem was that I had 71.86.04 installed (by Envy) as well as 171.05. Just uninstalled the 71.86.04 so it should work OK now.

I guess I'll just have to put up with the noise.

Thanks for the help :)

---

### Post by Calash on 2008-06-03
I had a difficult time getting my 9600GT drivers working.  I ended up having to download the beta drivers (171 I think) and compile them.  Envy would not detect my card and the 169 drivers locked up or just did not display.

This thread has the link to the beta driver and some guidance on how to get it working.

[http://ubuntuforums.org/showthread.php?t=717978](http://ubuntuforums.org/showthread.php?t=717978)

---

### Post by CLomax on 2008-06-03
I have the 171.05 driver installed, I am aware of the 173.08 but I'm also aware of the problems it brings.

So now there are only two problems left, the fan noise (important) and the 'Desktop effects cannot be enabled' message (not so important).

---

### Post by Calash on 2008-06-03
The beta driver fixed both the problems for me.  I will have to check when I get home and see what exact version I have running...I am pretty sure it is the 173

---

