---
title: "Which image to use and how?"
date: 2008-10-04
forum: New to Ubuntu
---

### Post by JAS510 on 2008-10-04
These are my specs.
Please let me know which image i should download and from what country.  

 Athlon 64 3500+ 2.2 GHz
2000 MT/s (Mega Transfers/second)
Socket 939
Chipset
ATI Radeon XPress 200
MOther board
Manufacturer: ASUS
Motherboard Name: A8AE-LE
HP/Compaq motherboard name: AmberineM-GL6E
Hard drive
200 GB
7200 rpm
Video graphics
Integrated graphics
Sound/audio
Controller: AC97 audio
Location: Integrated

Network (LAN)
Integrated 10/100 Base-T networking interface


Memory card reader

    * USB interface
    * Supports the following cards:
          o Compact Flash I
          o Compact Flash II
          o SmartMedia
          o Memory Stick
          o Memory Stick Pro
          o MultiMediaCard
          o Secure Digital (SD)
          o Micro Drive
          o XD Picture Card (xD = extreme digital)
Keyboard and mouse
Compaq PS/2 home professional keyboard
Compaq PS/2 scroller mouse


**Please help. I downloaded a couple of images but they dont seem to work.  I had a couple of errors. One being that it kept on looping.  I log into the system, (i hear the login music) i wait for a little bit then it automatically logs me out and goes back to the login screen.  My mouse was detected my keyboard was detected and my sound was detected.  I did a crt, alt backspace and it told me that the greeter was crashing and it was going to find a new one.  blah blah blah....!! I'M A ABSOLUTE BEGINNER, DONT KNOW ANYTHING ABOUT TERMINAL COMMANDS.  
:confused::confused::confused::confused::confused::confused::confused:

---

### Post by elmer_42 on 2008-10-04
Well, 32bit Ubuntu 8.04 is the most well-supported version, so I would go for that. As for which mirror/country to download from, that doesn't really matter. Just pick one from or near your country.

---

### Post by Sef on 2008-10-04
What os are you running now?

---

### Post by markbuntu on 2008-10-04
I have almost that exact same hardware, same mobo, 3800+ instead of 3500. It should have ATI 200M integrated graphics. It should run fine on 32 or 64, I have both. Mine is an HP though. You should be able to go to the HP or Compaq website and get more detailed info on your machine and check for bios updates.

I also had this problem with login. When you get to the login screen there is a little icon in the bottom left corner, click on it and find the gnome safe mode, it was a while ago, I don't remember exactly but you should be able to find it with no problem. continue your login and if you get to the desktop successfully then wait a little bit and you will be prompted that you have updates, get them. If that does not happen, use System/Administration/Update Manager. After getting the updates, reboot and see if you can login then.

---

### Post by 3rdalbum on 2008-10-04
Have you tried the safe graphics mode?

---

### Post by Paqman on 2008-10-04
You have an Athlon 64, which means you can use the 64-bit version of Ubuntu. Linux has excellent support for 64-bit these days, so there's no reason to throttle your chip down to 32-bit.

However, it's not likely that you have the wrong disk image. If you did, it just wouldn't boot. However, did you check the disk for errors after burning it? And did you burn it at a nice slow speed? Errors in the burning process are a very common cause of problems like what you're describing.

---

### Post by JoshuaRL on 2008-10-05
> **Paqman said:**
> You have an Athlon 64, which means you can use the 64-bit version of Ubuntu. Linux has excellent support for 64-bit these days, so there's no reason to throttle your chip down to 32-bit.

However, it's not likely that you have the wrong disk image. If you did, it just wouldn't boot. However, did you check the disk for errors after burning it? And did you burn it at a nice slow speed? Errors in the burning process are a very common cause of problems like what you're describing.

Agreed on both points.  Make sure you are burning on the slowest you can, it will minimize the probablility of burn errors.

And the earlier suggestion to boot into Gnome Safe Mode is a good one.  Look for that option on the Sessions button on the login screen.  After your system updates you should be able to log back in with the appropriate drivers installed correctly.

Let us know what happens.

---

### Post by JAS510 on 2008-10-05
thanks guy, 
I booted off gnome safe mode.  Selected updated manage and yes there were updates for the system.  I clicked ok and the following error occured.  I dont know if the system detected my linksys wireless card but the error message i got was:
:W: failed fetch [http://security.ubuntu.com/ubuntu/pool/main/s/sslcert/ssl-cert_1.0.14-0ubuntu2.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/s/sslcert/ssl-cert_1.0.14-0ubuntu2.1_all.deb)
could not resolve 'security.ubuntu.come

*but i did get farther then before..awesome**

-i burned the image in the slowest speed and it works.  (except for error above.  

this is awesome.

---

### Post by JAS510 on 2008-10-05
Ok, i just found out my wireless card is not working. 
I have a linksys model WMP54GS WIRELESS G. i believe the disk is formated for winxp.

---

### Post by k3lt01 on 2008-10-05
If you have WinXP drivers for your wireless you will most probably be able to get it working with ndiswrapper. ndiswrapper is a wrapper (thus the name) that makes Windows drivers fit into a Linux system.

---

### Post by JAS510 on 2008-10-05
Ok i went to add/remove program to load the windows wireless blah blah...problem is, i dont have ANY INTERNET CONNECTION my route is downstairs.  (major obsticle). I got my driver disk w/ me.  Is there any way i can load the driver by using a second computer and installing the program ndiswrapper to a usb drive and then loading it to the linux system.

---

### Post by JAS510 on 2008-10-05
> **markbuntu said:**
> I have almost that exact same hardware, same mobo, 3800+ instead of 3500. It should have ATI 200M integrated graphics. It should run fine on 32 or 64, I have both. Mine is an HP though. You should be able to go to the HP or Compaq website and get more detailed info on your machine and check for bios updates.

I also had this problem with login. When you get to the login screen there is a little icon in the bottom left corner, click on it and find the gnome safe mode, it was a while ago, I don't remember exactly but you should be able to find it with no problem. continue your login and if you get to the desktop successfully then wait a little bit and you will be prompted that you have updates, get them. If that does not happen, use System/Administration/Update Manager. After getting the updates, reboot and see if you can login then.

Did you have any problems w/ your usb drives not connecting/recognizing???

---

### Post by k3lt01 on 2008-10-05
> **JAS510 said:**
>  Is there any way i can load the driver by using a second computer and installing the program ndiswrapper to a usb drive and then loading it to the linux system.Ndiswrapper should be on your install disk. Put it in your drive and look for it in Pool>Main. You will need to install "ndiswrapper-common" and "ndiswrapper-utils-1.9". To install them just double click on them and follow the instructions. After you have done that copy your Windows drivers to your desktop.

Save this code box to a txt file and take it to your computer and open the txt file in gedit (or your txt editor). Open the terminal, cut and paste this in (do not copy what is in the brackets, it is just information for you). Do each line one at a time. Each line (cd, sudo, and echo) is a new command
```
cd Desktop
sudo ndiswrapper -i ********.inf (where the **** are, type in the name of your driver.inf file. It must be the .inf file)
sudo depmod -a
sudo ndiswrapper -m (this makes ndiswrapper your wireless wlan0 connection)
sudo ndiswrapper -l (this tells you if it all worked)
echo "ndiswrapper"|sudo tee -a /etc/modules (this loads the ndiswrapper module at boot)
sudo shutdown -r now (this will reboot your machine and load ndiswrapper and your driver at startup. You should now have a working wireless internet)
```

Let us know how you go.

---

### Post by JAS510 on 2008-10-05
i loaded the two ndiswrapper tool by using the install disk.
Yes i copied the driver directory over to my desktop.
I then went into add/remove, type wireless and installed the package.

I then went to system>administrator>windows wireless driver
i installed the .ini file.  but still no wireless connection.  I dont see anything. 

*i couldnt copy the script over because my usb drive was not detected*

also, be aware that i'm logged in as safe mode.  What do i do next or did i mess this up?:confused:

---

### Post by k3lt01 on 2008-10-05
If you have a printer print off the post with the script. Don't use anything else if you can help it. Just follow that script and you should be ok. There is no need to go to add/remove as you will only get ndisgtk anyway, and as it is also on the install disk going to add/remove is just wasting time, and you wont be able to load the modules into boot so you will still have to follow that script anyway.

Have you tried rebooting to see if you can get out of safe mode? If you are running off the LiveCD installing ndiswrapper is a waste of time as nothing is kept if on the other hand you have installed Ubuntu and you have to operate in safe mode then something else is wrong and you should concentrate on fixing that before trying to install ndiswrapper and Windows wireless drivers.

It's near midnight here so I will check back in the morning to see how you are going.

---

### Post by JAS510 on 2008-10-05
restarted the system and logged in normally.  The system keeps on looping.  I put in my username and pw.  It looks likes its going to go to my desktop and then it logs me out again.  I tried to login a couple of times and it did login finally but the only thing on my desktop was the drive folder.  Tool bar is gone.  the only way i can get the tool bar back is by logging in on safe mode.  

summarize
-no wireless signal even after the ndiswrapper install under safemode
-computer loops everytime I log in normally.  it keeps taking me back to the login screen
-wireless driver installed, i think.
-usb ports dont work


i spent the whole night trying to fix this issue.  its now 5am.  ANYONE PLEASE HELP!!!! :mad::mad::mad::mad::(

---

### Post by barbedsaber on 2008-10-05
Just a suggestion, try booting into a knoppix live cd, it has some of the best hardware detection, and can be really good for diagnosing hardware problems, (If it works in knoppix, it can be done with a bit of tweaking in ubuntu, if it doesn't work, all is not lost.
You may want to see if anyone else thinks this is a good idea, before you waste your time though, it may not be something that needs to be done.

---

### Post by k3lt01 on 2008-10-05
barbedsaber might be right, I don't really know,it could be worth a try.

One thing I do know is if you cannot get into Ubuntu normally you are wasting time trying to install anything. I suggest you start another thread and post about your logging in problem. Give it a descriptive name like "Can't log in normally, can only log in in Safe Mode" and explain what the logging in issue is.

One last thing before I get my breakfast, you haven't got any USB drives connected when you boot up have you? I know on my machine this will make it hang.

---

### Post by JAS510 on 2008-10-05
ok, tried the knoppix live cd. 
I press enter and i see it do something..
and then the screen goes black.  The cd is not engaging.  I dont hear it spin. 

I dont have any usb pluged in. 
I dont know what else to do.I redownloaded the image again.  Burned it using Roxio 7.0 burned it on 1x speed.

NOw i cant even get to the desktop using
faisafe mode. 

I have to get this thing running or i might just loose hope for this O.S on this machine.

---

### Post by k3lt01 on 2008-10-06
JAS510, I think you need to get back to basics and stop using thingsyou don't need to use. All that is happening is you are complicating your install.

A few questions.
What is the other OS you are using? Windows XP? Vista? Mac OSX?
If its XP or Vista just use the Windows CD burner by clicking on the iso image and click burn to disk.

Have you tried the Alternative Install CD? If not it migt be an idea t download it and burn it following a basic procedure without using any fancy software.

Has your PC got a wired connection for the modem? maybe its worth your while to take the PC down to the modem and use it to get your updates etc until you get the wireless working.

Remember, back to basics, follow instructions as they are given (otherwise it makes it hard for us to hep you), and last but not least don't stress.

---

