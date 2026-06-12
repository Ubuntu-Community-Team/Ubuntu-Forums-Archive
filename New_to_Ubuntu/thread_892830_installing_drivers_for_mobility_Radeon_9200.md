---
title: "installing drivers for mobility Radeon 9200"
date: 2008-08-17
forum: New to Ubuntu
---

### Post by torgas1 on 2008-08-17
I'm new to ubuntu.  Just installed it yesterday version 8.04 for a standard personal computer.  I have a hp pavilion zt3000 and I've been trying to update the graphics drivers.  The graphics card is a mobility radeon 9200.  I started to try EnvyNG but it doesn't support the 9200 series.  

So I found the driver I need on the ATI site.  The version I need is ATI-driver-installer-8.28.8.run.  I've tried to follow the sites instruction for installing this site but I have not succeeded.

Here's what I did.
I made sure the run as executable file was checked.
I opened the terminal
It is on my desktop so I typed:
cd ~/Desktop
sh ./ati-driver-installer-8.28.8.run

The file verify's integrity...All good.

Then it uncompressed the files.
it then said 
Detected configuration:
Architecture: i686 (32-bit)
X Server: unable to detect
Removing temporary directory: fglrx-install

and that was it... I could then enter another command.

Any help on how to get this to install would be greatly appreciated.

---

### Post by Ryadt on 2008-08-17
Try ```
sudo apt-get install xorg-driver-fglrx
```

---

### Post by torgas1 on 2008-08-17
Thanks for the fast response,
I tried it and it said the fglrx is already the newest version.

I think I need new drivers because for instance when I open up the chess program and try to view it in 3d mode I get an error saying 

You are unable to play in 3D mode due to the following problems:
No Python Open GL support
No Python GTKGLExt support.

---

### Post by Ryadt on 2008-08-17
Try installing your graphic card through envy. 

Install envy```
sudo apt-get install envyng-gtk
```

---

### Post by torgas1 on 2008-08-17
I tried Envy which seems to be a great program but it doesn't work on ATI models below 9500 and I have a 9200

---

### Post by Ryadt on 2008-08-17
> **torgas1 said:**
> I'm new to ubuntu.  Just installed it yesterday version 8.04 for a standard personal computer.  I have a hp pavilion zt3000 and I've been trying to update the graphics drivers.  The graphics card is a mobility radeon 9200.  I started to try EnvyNG but it doesn't support the 9200 series.  

So I found the driver I need on the ATI site.  The version I need is ATI-driver-installer-8.28.8.run.  I've tried to follow the sites instruction for installing this site but I have not succeeded.

Here's what I did.
I made sure the run as executable file was checked.
I opened the terminal
It is on my desktop so I typed:
cd ~/Desktop
sh ./ati-driver-installer-8.28.8.run

The file verify's integrity...All good.

Then it uncompressed the files.
it then said 
Detected configuration:
Architecture: i686 (32-bit)
X Server: unable to detect
Removing temporary directory: fglrx-install

and that was it... I could then enter another command.

Any help on how to get this to install would be greatly appreciated.

Can you try ```
sudo apt-get install xserver-xgl
```

---

### Post by torgas1 on 2008-08-17
Well I ran that code and it worked.  Not sure exactly what it did though.  Also I still can't run things in 3D mode.

---

### Post by Ryadt on 2008-08-17
> **torgas1 said:**
> Well I ran that code and it worked.  Not sure exactly what it did though.  Also I still can't run things in 3D mode.

Do ```
sudo apt-get install python-opengl python-gtkglext1
```

---

### Post by Mastoras12 on 2008-08-18
Hi!! I wonder if you solved the problem because I'm also trying to set my Ati card and I can't manage it 3 hours now... :)

---

### Post by torgas1 on 2008-08-19
Not yet, I'm working hard on it... check out the documentation on it... it may help[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

---

### Post by mcurran on 2008-10-29
You might want to try Envy and not EnvyNG.  Also, check your restricted drivers, someone else with this card was saying that it was automatically detected and installed, so I'm guessing there's a default driver in there you can use.

---

### Post by slccsoccer28 on 2009-06-11
For testing your 3D you may want to try to use another program besides the chess game that comes installed.  From what I have heard it seems to have a problem that it give you that message even if you have ur system configured well.

---

### Post by steward on 2009-12-09
Hi 
I m absolutely new to Ubuntu 9.10..
I d like to install My graphic card ([SIZE="4"]ATI Mobility Radeon 9200[/SIZE]) on UBUNTU 9.10. Would you please guide me step by step to install this critical driver because it really bothers my eye.

---

### Post by steward on 2009-12-21
No one wants to help me?

---

### Post by Mark Phelps on 2009-12-22
> **steward said:**
> Hi 
I m absolutely new to Ubuntu 9.10..
I d like to install My graphic card ([SIZE="4"]ATI Mobility Radeon 9200[/SIZE]) on UBUNTU 9.10. Would you please guide me step by step to install this critical driver because it really bothers my eye.

You can't -- there are no ATI restricted drivers that will work with your card and Ubuntu 9.10.

If you're seeing a desktop, that means you're running the open source drivers -- which are installed by default.

That's all that there is available for your card and Ubuntu 9.10.

---

