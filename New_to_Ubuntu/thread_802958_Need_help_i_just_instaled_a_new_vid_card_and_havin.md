---
title: "Need help i just instaled a new vid card and having problem installing the driver"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by appoloin on 2008-05-21
i just purchased a Nvidia video card and downloaded the driver on the website [http://www.nvidia.com/object/nv_swlicense.html](http://www.nvidia.com/object/nv_swlicense.html) i followed the steps to install it bu i may have missed something. Can anyone help i am getting an error
ERROR: nvidia-installer must be run as root

Steps Taken:
To download and install the drivers, follow the steps below:

STEP 1: Review the NVIDIA Software License.

You will need to accept this license prior to downloading any files.

STEP 2: Download the Driver File

Download - NVIDIA-Linux-x86-169.12.pkg1.run

SuSE users: please read the SuSE NVIDIA Installer HOWTO before downloading the driver.

STEP 3: Install
Type "sh NVIDIA-Linux-x86-169.12-pkg1.run" to install the driver. NVIDIA now provides a utility to assist you with configuration of your X config file. Please see Chapter 3 of the README or run 'man nvidia-xconfig' for details on usage. Instructions for those wishing to edit their X config file by hand can also be found in the README. 

Terminal:

ed@ed-desktop:~$ ls
Desktop  Documents  Examples  Music  Pictures  Public  Templates  Videos
ed@ed-desktop:~$ cd desktop
bash: cd: desktop: No such file or directory
ed@ed-desktop:~$ cd
ed@ed-desktop:~$ ls
Desktop  Documents  Examples  Music  Pictures  Public  Templates  Videos
ed@ed-desktop:~$ cd Desktop
ed@ed-desktop:~/Desktop$ ls
NVIDIA-Linux-x86-169.12-pkg1.run
ed@ed-desktop:~/Desktop$ ./'/home/ed/Desktop/NVIDIA-Linux-x86-169.12-pkg1.run'
bash: .//home/ed/Desktop/NVIDIA-Linux-x86-169.12-pkg1.run: No such file or directory
ed@ed-desktop:~/Desktop$ '/home/ed/Desktop/NVIDIA-Linux-x86-169.12-pkg1.run' 
bash: /home/ed/Desktop/NVIDIA-Linux-x86-169.12-pkg1.run: Permission denied
ed@ed-desktop:~/Desktop$ "sh NVIDIA-Linux-x86-169.12-pkg1.run" 
bash: sh NVIDIA-Linux-x86-169.12-pkg1.run: command not found
ed@ed-desktop:~/Desktop$ sh NVIDIA-Linux-x86-169.12-pkg1.run
Verifying archive integrity... OK
Uncompressing NVIDIA Accelerated Graphics Driver for Linux-x86 169.12............................................................................................................................................................................................................................................................................................
nvidia-installer: Error opening log file '/var/log/nvidia-installer.log' for writing (Permission denied); disabling logging.
ed@ed-desktop:~/Desktop$ sh NVIDIA-Linux-x86-169.12-pkg1.run
Verifying archive integrity... OK
Uncompressing NVIDIA Accelerated Graphics Driver for Linux-x86 169.12............................................................................................................................................................................................................................................................................................
nvidia-installer: Error opening log file '/var/log/nvidia-installer.log' for writing (Permission denied); disabling logging.
ed@ed-desktop:~/Desktop$ cd
ed@ed-desktop:~$ cd
ed@ed-desktop:~$ sh NVIDIA-Linux-x86-169.12-pkg1.run
sh: Can't open NVIDIA-Linux-x86-169.12-pkg1.run
ed@ed-desktop:~$ 


CAn anyone help me and teach me how to install a driver please? i have downloaded it on my desktop

---

### Post by appoloin on 2008-05-21
i have this screenshot if it helps

---

### Post by littletinman on 2008-05-21
Try Envy

---

### Post by appoloin on 2008-05-21
i will but Nvidea have the driver i guess i just need to know how to instal the driver in root as specified

---

### Post by Maestro23 on 2008-05-21
Try:

> cd Desktop

sudo chmod +x NVIDIA-Linux-x86-169.12-pkg1.run

sudo ./NVIDIA-Linux-x86-169.12-pkg1.run


---

### Post by appoloin on 2008-05-21
thanx for that now i have a new problem its saying im running a X server and i need to turn it off how do i do that?

see screenshot

---

### Post by appoloin on 2008-05-21
I found this when googling
Reply With Quote
aje
View Public Profile
Send a private message to aje
Find More Posts by aje
Old 10-26-04, 06:58 PM 	  #2
LinuxManiac
Registered User
 
Join Date: Oct 2004
Posts: 4
	
Default Re: "You appear to be running an X server"
you have to reboot in the run level 3, 2 or 1 <=how do i do this?

edit the file /etc/inittab in the line

id:5:initdefault:

change it to:
id:3:initdefault:


reboot...
then you'll enter without the X server

after installing the driver change it back to :
id:5:initdefault:


and enter the command:
shutdown -h now

to reboot again

---

### Post by appoloin on 2008-05-21
woot i got it working!!!!
for other here is the rest of the instruction

How to kill X?
I've been curious about that as well. I've set my computer to boot to CLI first, and then I start the GUI when I need it. Most people advocate just typing "startx" to do this, but I find that when I do, I can't kill it. Usually I type:

sudo /etc/init.d/gdm start

(I use Gnome. for KDE or XFCE you would use kdm or xdm)

Then when I want to stop it I type:

sudo /etc/init.d/gdm stop

And I'm right back to just the shell. But if I just "startx" the gdm doesn't start, so you can't kill it this way. But I've not been able to find the kill command for X, so I don't use "startx".

---

### Post by Maestro23 on 2008-05-21
So the driver is working properly?  Good deal man.:)

---

