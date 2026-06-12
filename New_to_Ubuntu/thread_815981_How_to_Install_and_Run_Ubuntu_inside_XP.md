---
title: "How to Install and Run Ubuntu inside XP"
date: 2008-06-02
forum: New to Ubuntu
---

### Post by mac143_01 on 2008-06-02
This procedure do not require you to have a dual boot OS in 1 PC,  open the URL to see the full details with pictures so you can easily follow the instructions... It works for me!!!

[http://www.pcmech.com/article/how-to-install-and-run-ubuntu-linux-inside-windows/](http://www.pcmech.com/article/how-to-install-and-run-ubuntu-linux-inside-windows/)


How To Install and Run Ubuntu Linux Inside Windows
Requirements
While there are several methods and a variety of virtual machine software to choose from, I am going to install Ubuntu Linux using Microsoft Virtual PC 2007 for this walk through. The process should be very similar for any other virtual machine software if you want to use something different.
•	Windows XP or Vista. 
•	Respectable processor (at least ~1.5 Ghz or a dual core). 
•	At least 1 GB RAM. 
•	Microsoft Virtual PC 2007 (it’s free). The download page says it requires XP Pro, but there are numerous reports it works on XP Home just fine. 
•	Latest distro of Ubuntu (7.10 at the time of this writing). Once you have downloaded the ISO file, burn it to CD. 
Steps To Install Ubuntu Linux Inside Of Microsoft Virtual PC 2007

1.	Open Virtual PC and click New inside of the Virtual PC Console. The New Virtual Machine Wizard starts. Click Next. 

2.	Select the option to create a new virtual machine. Click Next. 

3.	Enter “Ubuntu Linux” for the name of the virtual machine. Click Next. 

4.	Select “Other” for the operating system. Click Next. 

5.	Select the option to adjust the amount of RAM and assign at least 256 MB, but I would recommend 512 or higher. The more RAM you assign the faster Ubuntu will run, but your “host” Windows install will have that much less RAM while the virtual machine is running. Click Next. 

6.	Select the option to use a new virtual disk. Click Next. 

7.	Select a location to save the virtual machine file and assign a size for the virtual machine. The size you specify will be the size of Ubuntu’s hard drive, so make sure you assign at least 10,000 MB (10 GB). Click Next. 

8.	Review the summary page and click Finish to create the new virtual machine. There should now be an entry called “Ubuntu Linux” in your Virtual PC Console. You can select this entry and click the Settings button to review or change the VM settings.  

9.	Insert your Ubuntu CD into your CD drive, select the Ubuntu Linux entry and press Start. 

10.	When your virtual machine (VM) starts for the first time, it will not have any devices assigned to boot from. As a result, you will probably get a screen which shows the VM trying to boot from the network (”spinning” cursor) or just simply a “No boot device found” error. 

11.	To fix this, you need to tell the VM to use the CD drive from your host OS. From the CD menu of Virtual PC, select “Use Physical Drive D:” (where D is the drive letter of your CD drive in Windows). This will bind the the D drive in Windows to be the CD drive in your VM. 

12.	From the Virtual PC menu, select Action > Reset to restart the VM. 

13.	Once the VM reboots, it will read the CD and give you the Ubuntu boot menu. As of the time of this writing, Ubuntu 7.10 has a bug in its kernel which does not communicate correctly with PS2 driver emulators used by VM software such as Virtual PC 2007. Here is how to work around this issue (thanks to the Ubuntu Forums and this bug report): 
1.	While on the boot menu, press F6 to view the boot command string at the bottom of the screen. 
2.	At the end of the command string, remove “splash” and enter “i8042.noloop” before the two dashes. 
3.	Select the option to Start Ubuntu in safe graphics mode. 
4.	Your screen should look like the screenshot below. If it does, press Enter to boot to Ubuntu.  

14.	The boot process may take some time to load. If you see a blank screen for a few minutes, this is fine. Eventually you will see Ubuntu loading all of its start up services and then the GUI will appear. You are now in the Ubuntu Live CD Environment. 

15.	Since the mouse and keyboard are shared between your VM and host Windows OS, once you click inside the VM it will “lock” the mouse and keyboard input. To transfer control back to your host Windows OS, press the Right Alt key. 

16.	You can feel free to play around with the applications, but since everything is running from the CD the response will be really slow. Let’s get down to business and install Ubuntu on the virtual machine. To start, simply double click the Install icon on the desktop. The installation program will then start (be patient).  

17.	Select your language. Click Forward. 

18.	Select your time zone. Click Forward. 

19.	Select your keyboard layout. Click Forward. 

20.	The Ubuntu partitioner will detect the amount of space you allocated to your VM. For this guide, I am going to use the default option which is to use the entire disk for the Ubuntu install, however you can certainly manually configure your partitions if you prefer, but I will not cover manually editing your partitions in this guide. Select the option for guided and click Forward. 

21.	Fill out the information about yourself. Make sure you note your user name and password. Click Forward.  

22.	Review the installation summary and click Install to load Ubuntu on your virtual machine. This may take some time, so be patient. 

23.	Once the install is complete you will get a notice to remove the installation CD. In the Virtual PC menu (remember, press the Right Alt key to transfer the mouse) select CD > Eject and remove your Ubuntu installation CD. Click Restart now to boot to your new Ubuntu installation on your virtual machine. 

24.	Before we go into Ubuntu for the first time, we need to apply the mouse fix to the completed installation to work around the kernel bug. This only needs to be done one time. When the VM is booting, you will see a message which says “Press ESC to load the GRUB config”. Press ESC to enter the GRUB configuration (if you didn’t press ESC in time, simply go to Action > Reset to reboot the VM). 

25.	In the GRUB configuration, make sure the first option which reads “Ubuntu [Version], kernel 2.6.x-x-generic” is selected and press E.  

26.	Select the kernel option (should be the second line) and press E.  

27.	Just like when installing Ubuntu, change “splash” at the end of the line to be “i8042.noloop”. Press Enter to apply the changes.  

28.	Back on the kernel option screen, press B to start Ubuntu. Once logged into Ubuntu, I will show you how to edit this permanently so you don’t have to make this change every time you boot. 

29.	Once the Ubuntu login screen appears, enter the user name and password you created during the installation. 

30.	Welcome to Ubuntu completely inside of Windows.  

31.	Now, here is how to apply the permanent fix for the kernel mouse bug. Once you do this you will not have to worry about the mouse problem anymore: 
1.	Go to Applications > Accessories > Terminal. 
2.	Enter: sudo gedit /boot/grub/menu.lst 
3.	When prompted, enter your login password.
 
4.	Locate the “kernel” line we edited in when first booting Ubuntu (line ~132) and once again, change “splash” to “i8042.noloop”.
 
5.	Save your changes. 

32.	You are done! Enjoy running Ubuntu from inside of Windows. 
Of course, remember you are running Ubuntu Linux entirely from inside of a virtual environment. This should have no effect on program functionality, however you will most likely not be able to play any open GL games. I’ve also found that sound does not work out of the box, but if you need it this fix should help (I have not tried this though, as I do not use sound in my VM).
That’s it. Get down to giving Ubuntu a real good look and you might want to make it your primary OS.

---

### Post by billgoldberg on 2008-06-02
Shouldn't this be in "tutorials & tips"?

Nice guide BTW.

---

### Post by ardvark71 on 2008-06-02
Sounds awot wike that wascally WUBI! huh huh huh huh huh huh :biggrin:

*ahem* seriously though, it might be interesting to try...

Best Regards...

---

### Post by bumanie on 2008-06-02
A number of people suggested you use a virtual machine of some type when you asked how to do this yesterday. Interesting guide, but many of us already have virtual machines operating. This should have been posted in tips and guides.

---

### Post by ardvark71 on 2008-06-05
Hi all...

UPDATE: I just tried out the instructions a little bit ago, pretty nice! :KS It even used my dial-up connection as the "network connection." :biggrin:

However, I missed one of the instructions initially and didn't choose the safe graphics mode. Let's just say it was an interesting experience. ;)

Best Regards...

---

### Post by D.Sync on 2008-06-05
Wow, that sure took you many efforts to do it. Great job!

For me, I just dual-boot. Thanks for the guide, should be useful for somebody!

---

